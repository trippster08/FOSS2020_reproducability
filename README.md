# FOSS2020_reproducability
# FOSS2020 reproducibility tutorial
```
# connect to my atmosphere instance using ssh. The ip will probably change each time it connect. IP is copied from atmosphere instance page
ssh trippster08@/128.196.142.74
# move to /scratch, it has more space than other folders
cd /scratch
# clone my github reproducability repository
git clone https://github.com/trippster08/FOSS2020_reproducability.git
# change the name to the recommended name, reproducibility-tutorial
mv FOSS2020_reproducability reproducibility-tutorial
# download miniconda installer
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
# install miniconda
bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda
# make sure conda packages will be in path linked to /bin
ln -s /opt/conda/pkgs/*/bin/* /bin
ln -s /opt/conda/pkgs/*/lib/* /usr/lib
# install Jupyterlab version 1.2.3
/opt/conda/bin/conda install -c conda-forge -y jupyterlab=1.2.3
/opt/conda/bin/conda install -c conda-forge -y nodejs=10.13.0
/opt/conda/bin/pip install bash_kernel
/opt/conda/bin/pip install ipykernel
/opt/conda/bin/python3 -m bash_kernel.install
# start jupyterlab
/opt/conda/bin/jupyter lab --no-browser --allow-root --ip=0.0.0.0 --NotebookApp.token='' --NotebookApp.password='' --notebook-dir='/scratch/reproducibility-tutorial/'
# search for an find snakemake to see what versions are available
/opt/conda/bin/conda search -c bioconda snakemake
# install snakemake version 5.8.1
/opt/conda/bin/conda install -c bioconda -c conda-forge -y snakemake=5.8.1
# make sure packages are lined to /bin again
ln -s /opt/conda/bin/* /bin
ln -s /opt/conda/lib/* /usr/lib
# check verison of snakemake
snakemake --version
# update ubutu apt-get package manager
sudo apt-get update
# install packages for apt-get
sudo apt-get install -y \
apt-transport-https \
ca-certificates \
curl \
gnupg-agent \
software-properties-common
# add docker key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# add repository
sudo add-apt-repository \
 "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) \
 stable"
# update apt-get with new repository information
sudo apt-get update
# install docker
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
# test docker
docker run hello-world
# move to folder reproducibility-tutorial
cd reproducibility-tutorial/
# save all commands to README.md
history >> README.md
```
