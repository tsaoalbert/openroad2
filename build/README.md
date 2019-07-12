# Builds

## Creating Builds
The build framework has a dependency on docker. You will need docker Docker 18.09 (or later) installed. It is also necessary to setup an ssh-agent. You can run `ssh-add -L` to check if the agent is setup or `eval $(ssh-agent -s)` to start the agent

Run the following commands to build an export
```bash
git clone git@github.com:The-OpenROAD-Project/CI.git
cd build
make build-tools
make export-tools
```

Once the export is built (in the exports directory), it can be uploaded to the github [releases](https://github.com/The-OpenROAD-Project/CI/releases).

Other interesting make targets

- `make build-%` This will build the specified tool (e.g. yosys, utd, replace, etc)
- `make run-%` This will run the specified tool image with a `$USER` session inside the image
- `make runasroot-%` This will run the specified tool image with a root session inside the image
- `make export-tools` This will create a tar.gz export of all tools

## Installing Builds
The builds can be installed to any Redhat 6/7 based machine using the [modules installation system](https://modules.readthedocs.io/en/latest/). Download a build from the [releases](https://github.com/The-OpenROAD-Project/CI/releases) and perform the following steps to install

### Prerequisites on run system
1. environment-modules - all
1. Python3 - TritonCTS
1. tcl8.5 & tk8.5 - many

### Install procedure
```
tar -xzf Openroad{version}.tar.gz
module use modules
module load openroad
```
Once installed, all OpenROAD binaries should now be in your path.