# Juju Box

Juju Box a docker container project that provides a configured Juju
environment with all the tools you need to work with Juju.

Juju provisions machines, deploy services and orchestrates them into
systems.

This container comes with the basic tools you need to get started w/
juju.

 - juju
 - juju quickstart
 - [juju plugins](https://github.com/juju/plugins)

Note: jujubox does not currently install juju local provider.  We hope
to roll something that works like local provider in a container
solution soon.

# Install

### Linux
Install Docker using the package manager for your distro, or
[get.docker.com](https://get.docker.com/).

Docker >= 1.4.1 recommended.

### OS X

Docker does not run natively in OS X, so we'll need to use VirtualBox
and boot2docker. This is relatively easy for users of brew:

```
brew install cask
brew cask install virtualbox
brew install docker
brew install boot2docker

boot2docker init
boot2docker up
```

When boot2docker finishes, it will prompt you to export Docker
environment variables. With that done, you're ready to use docker.
You do not need to run the docker commands using sudo because
boot2docker runs as root.

    docker run  -ti whitmo/jujubox

# Download

Download the Juju Box source from github or the container from
[hub.docker.io](https://registry.hub.docker.com/u/whitmo/jujubox/):

### Linux
You can clone the repository from github.

```
git clone https://github.com/whitmo/jujubox.git && cd jujubox

```

Or download and install the container directly from hub.docker.io:

```
sudo docker run  -ti whitmo/jujubox
```


# To Run

There are two ways to run the docker container, from the github
repository (build from source) or from the container directly from the
hub.docker.io.


### Linux

#### From source:
```
sudo docker build -t jujubox ./
sudo docker run -i -t jujubox:latest
```

#### Use hub.docker.io:
```
sudo docker run  -ti whitmo/jujubox
```

If you already have juju installed, run the container using your
existing ${JUJU_HOME} directory (~/.juju):

```
sudo docker run --rm -v ${JUJU_HOME}:/home/ubuntu/.juju -it whitmo/jujubox
```

### OS X
Remember that boot2docker runs as root, so don't use `sudo` for the docker
commands:
```
docker run -ti whitmo/jujubox
```

# Once it's up

All your usual juju commands should work. You can use Quickstart if
you need to set up your cloud credentials:

    juju quickstart -i


# Other goodies

 - Charmbox: The charmers dockerfile is for developing and reviewing charms:
   *see
   [charmbox instructions](charmbox.md)*.


# Future Direction

We plan to build some containers that support juju local provider to
allow juju to orchestrate lxc containers locally for inception style
disposable architectures.
