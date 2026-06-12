---
title: "Issue installing Openstack"
date: 2023-12-12
forum: Ubuntu Cloud and Juju
---

### Post by nevers97 on 2023-12-12
Hi everybody,

Currently i'm experiencing an issue with installing openstack on a personal server. I've tried to install openstack but got an error on ubuntu server 22.04.3 LTS. I've tried many solutions on the internet without any success. Also tried upgrading the OS to Ubuntu 23.10, but again no sucess/ 

This is the current error I'm running into (I have replaced my username and ip with username@host):

```
sunbeam cluster bootstrap --accept-defaults&#10279; Bootstrapping Juju onto machine ... 
&#10297; Bootstrapping Juju onto machine ... 
&#10300; Bootstrapping Juju onto machine ... 
&#10292; Bootstrapping Juju onto machine ... Error bootstrapping Juju
Traceback (most recent call last):
  File "/snap/openstack/324/lib/python3.10/site-packages/sunbeam/commands/juju.py", line 290, in run
    process = subprocess.run(cmd, capture_output=True, text=True, check=True)
  File "/usr/lib/python3.10/subprocess.py", line 526, in run
    raise CalledProcessError(retcode, process.args,
subprocess.CalledProcessError: Command '['/snap/openstack/324/juju/bin/juju', 'bootstrap', 'sunbeam', 'sunbeam-controller', '--agent-version=3.2.0']' returned non-zero exit status 1.
ERROR initializing ubuntu user: subprocess encountered error code 255 (Permission denied, please try again.
Permission denied, please try again.
username@host: Permission denied (publickey,password,hostbased).)
ERROR subprocess encountered error code 255 (Permission denied, please try again.
Permission denied, please try again.
username@host: Permission denied (publickey,password,hostbased).)


Error: Command '['/snap/openstack/324/juju/bin/juju', 'bootstrap', 'sunbeam', 'sunbeam-controller', '--agent-version=3.2.0']' returned non-zero exit status 1.
```


I hope somebody knows a solution, I'm all out of options :(

---

### Post by scttstrck on 2024-01-22
Howdy, did you get this working?

I did this recently without problems on 22.04.3 LTS by following the tutorial.
The only thing I did beforehand was to ensure that the IP with the full name was in the /etc/hosts file.

I did the following steps, maybe you forgot to run the prepare node script:
[FONT=Consolas]sudo snap install openstack --channel 2023.2
[/FONT][FONT=Consolas]sunbeam prepare-node-script | bash -x && newgrp snap_daemon
[/FONT][FONT=Consolas]sunbeam cluster bootstrap -a

[/FONT]

---

### Post by bran-castillo on 2024-04-04
Hello, I recently ran into this similar issue and the following commands fixed this issue in my case.

Manually run the juju bootstrap command:
```
juju bootstrap sunbeam sunbeam-controller
```
Wait for the juju bootstrap to complete then run:[COLOR=#181818][FONT=-apple-system]
[/FONT][/COLOR]```
sunbeam cluster bootstrap --accept-defaults
```

Looks like there's a bug in launchpad: [https://bugs.launchpad.net/snap-openstack/+bug/2025316](https://bugs.launchpad.net/snap-openstack/+bug/2025316)

---

