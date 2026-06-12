---
title: "Unable to bootstrap Juju controller"
date: 2018-07-26
forum: Ubuntu Cloud and Juju
---

### Post by quartzeye on 2018-07-26
Going through my build script that has worked many times before, I now can no longer bootstrap the Juju controller.  Running the latest up to date 18.04, lxd at 3.0.1, juju at  2.4.1-bionic-amd64.

Also created container after "lxd init" was done and tested.  Container ran with out issue and was able to ping the internet from inside of container.

```
udeadmin@ude:~/openstack-on-lxd$ juju bootstrap --config config.yaml localhost lxd
Since Juju 2 is being run for the first time, downloading latest cloud information.
Fetching latest public cloud list...
Your list of public clouds is up to date, see `juju clouds`.
Creating Juju controller "lxd" on localhost/localhost
Looking for packaged Juju agent version 2.4.1 for amd64
To configure your system to better support LXD containers, please see: [https://github.com/lxc/lxd/blob/master/doc/production-setup.md](https://github.com/lxc/lxd/blob/master/doc/production-setup.md)
Launching controller instance(s) on localhost/localhost...
 - juju-0ea207-0 (arch=amd64 mem=3.5G)
Installing Juju agent on bootstrap instance
Fetching Juju GUI 2.12.3
Waiting for address
Attempting to connect to 172.27.1.67:22
Connected to 172.27.1.67
Running machine configuration script...
```

_config.yaml_
```
default-series: bionic  <--- tried with xenial too
apt-http-proxy: [http://172.27.1.1:8000](http://172.27.1.1:8000)
``` 


Been this way all week.  I have done everything I can think of.  I used a snapshot from a VM that had worked many times a few weeks ago that now does not work.  I updated the VM with out success.  I even rebuilt a brand new VM with the same results.

_Something has changed on the Ubuntu side in the last week or so with either the default Juju agent, configuration script, or the hosted services. _

---

