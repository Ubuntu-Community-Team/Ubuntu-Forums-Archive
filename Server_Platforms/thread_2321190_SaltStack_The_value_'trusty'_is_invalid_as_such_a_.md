---
title: "SaltStack: The value 'trusty' is invalid as such a release is not available"
date: 2016-04-21
forum: Server Platforms
---

### Post by george@reilly.org on 2016-04-21
I'm building a Docker image based on Ubuntu 14.04.3 LTS (actually phusion/baseimage:0.9.18). I apt-get install a few packages including salt-minion. Then I use SaltStack to install more. This has worked for months. Tonight it started failing. Perhaps due to the imminent release of the 16.04 LTS?

Dockerfile:
```
# CookBrite base image - phusion/baseimage + SaltStack
# Note: never use :latest, always use a numbered release tag.
FROM phusion/baseimage:0.9.18
MAINTAINER Cookbrite, Inc.

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

# After the image is built, we will use salt, mounted via docker run.
# Update the sources list
RUN apt-get update

# Install basic applications
RUN apt-get install -y tar git vim nano wget net-tools build-essential salt-minion

# SaltStack fail hard if any state fails
RUN echo "failhard: True" >> /etc/salt/minion

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

```

$ docker build .
$ docker run -d -P --name test -v $(pwd)/salt/base:/srv/salt 1b12b6e7697b
root@c4969642c843:/# salt-call --local state.highstate
```
[INFO    ] The `lspci` binary is not available on the system. GPU grains will not be available.
[WARNING ] Although 'dmidecode' was found in path, the current user cannot execute it. Grains output might not be accurate.
[INFO    ] The `lspci` binary is not available on the system. GPU grains will not be available.
[WARNING ] Although 'dmidecode' was found in path, the current user cannot execute it. Grains output might not be accurate.
[INFO    ] Loading fresh modules for state activity
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/modules'
[INFO    ] Syncing modules for environment 'base'
[INFO    ] Loading cache from salt://_modules, for base)
[INFO    ] Caching directory '_modules/' for environment 'base'
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/states'
[INFO    ] Syncing states for environment 'base'
[INFO    ] Loading cache from salt://_states, for base)
[INFO    ] Caching directory '_states/' for environment 'base'
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/grains'
[INFO    ] Syncing grains for environment 'base'
[INFO    ] Loading cache from salt://_grains, for base)
[INFO    ] Caching directory '_grains/' for environment 'base'
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/renderers'
[INFO    ] Syncing renderers for environment 'base'
[INFO    ] Loading cache from salt://_renderers, for base)
[INFO    ] Caching directory '_renderers/' for environment 'base'
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/returners'
[INFO    ] Syncing returners for environment 'base'
[INFO    ] Loading cache from salt://_returners, for base)
[INFO    ] Caching directory '_returners/' for environment 'base'
[INFO    ] Creating module dir '/var/cache/salt/minion/extmods/outputters'
[INFO    ] Syncing outputters for environment 'base'
[INFO    ] Loading cache from salt://_outputters, for base)
[INFO    ] Caching directory '_outputters/' for environment 'base'
[INFO    ] Loading fresh modules for state activity
[INFO    ] Executing state pkg.installed for python-software-properties
[INFO    ] Executing command 'apt-get -q update' in directory '/root'
[INFO    ] Executing command "dpkg-query --showformat='${Status} ${Package} ${Version} ${Architecture}\n' -W" in directory '/root'
[INFO    ] Executing command 'grep-available -F Provides -s Package,Provides -e "^.+$"' in directory '/root'
[INFO    ] Targeting repo 'trusty'
[INFO    ] Executing command ['apt-get', '-q', '-y', '-o', 'DPkg::Options::=--force-confold', '-o', 'DPkg::Options::=--force-confdef', '-t', 'trusty', 'install', 'python-software-properties'] in directory '/root'
[ERROR   ] Command '['apt-get', '-q', '-y', '-o', 'DPkg::Options::=--force-confold', '-o', 'DPkg::Options::=--force-confdef', '-t', 'trusty', 'install', 'python-software-properties']' failed with return code: 100
[ERROR   ] stdout: Reading package lists...
[ERROR   ] stderr: E: The value 'trusty' is invalid for APT::Default-Release as such a release is not available in the sources
[INFO    ] Executing command "dpkg-query --showformat='${Status} ${Package} ${Version} ${Architecture}\n' -W" in directory '/root'
[ERROR   ] The following packages failed to install/update: python-software-properties.
local:
----------
    State: - pkg
    Name:      python-software-properties
    Function:  installed
        Result:    False
        Comment:   The following packages failed to install/update: python-software-properties.
        Changes:

Summary
------------
Succeeded: 0
Failed:    1
------------
Total:     1
```

The failing SaltState looks like:
```

python-software-properties:
  pkg.installed:
    - fromrepo: trusty
    - pkgs:
      - python-software-properties

# https://launchpad.net/~fkrull/+archive/ubuntu/deadsnakes-python2.7
python2.7-ppa:
  pkgrepo.managed:
    - humanname: Python 2.7 updates PPA
    - name: deb http://ppa.launchpad.net/fkrull/deadsnakes-python2.7/ubuntu trusty main
    - dist: trusty
    - file: /etc/apt/sources.list.d/python27-updates.list
    - keyid: FF3997E83CD969B409FB24BC5BB92C09DB82666C
    - keyserver: keyserver.ubuntu.com
    - require_in: python2.7-update

python2.7-update:
  pkg.latest:
    - fromrepo: trusty
    - pkgs:
      - python2.7
      - python2.7-dev
```

---

### Post by george@reilly.org on 2016-04-21
This repro'd several times last night, but it no longer does. The code has started working again.

---

