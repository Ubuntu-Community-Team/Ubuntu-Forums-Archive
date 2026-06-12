---
title: "Changing default version of python in Lucid 10.04"
date: 2010-09-17
forum: Server Platforms
---

### Post by Imma_Beast on 2010-09-17
Here's how you change the default version of python in Lucid. Lucid comes packaged with 2.6 but we use 2.5 where I work. I didn't see much of anything on the web for this topic so figured I'd post something. 

If you are installing python2.5 on Lucid version 10.04 (comes package with 2.6 only)

[LIST]
[*]Edit /etc/apt/source.list
[*]add these additions to the bottom of list
[LIST]
[*]deb [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main deb-src [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main
[/LIST]
 
[*]sudo apt-get update
[*]sudo apt-get install python2.5 pythong2.5-minimal python2.5-dev
[/LIST]

[LIST]
[*]Next you need to change the default version of python
[LIST]
[*] vim /usr/share/python/debian_defaults - change the default version to python2.5
[*]Now you need to remove all the symlinks of python2.6 and related files to python then relink them to python2.5
[LIST]
[*]unlink /usr/bin/pydoc
[*] ln -s /usr/bin/pydoc2.5 /usr/bin/python
[*]unlink /usr/bin/pygettext
[*]ln -s /usr/bin/pygettext2.5 /usr/bin/pygettext
[*]unlink /usr/bin/python
[*]ln -s /usr/bin/python2.5 /usr/bin/python
[*]unlink /usr/bin/python2
[*]ln -s /usr/bin/python2.5 /usr/bin/python2
[*]unlink /usr/bin/python-config
[*]ln -s /usr/bin/python-config2.5 /usr/bin/python-config
[/LIST]
 
[*]Now log into python shell, it should show the version as 2.5: Python 2.5.5 (r255:77872, Sep 14 2010, 17:19:13)
[/LIST]
 
[/LIST]

---

### Post by LightningCrash on 2010-09-19
update-alternatives --install /usr/bin/python python /usr/lib/python2.6 1
update-alternatives --install /usr/bin/python python /usr/lib/python2.5 10

---

