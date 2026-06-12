---
title: "Ubuntu Enterprise Cloud Install problem - specific IP?"
date: 2010-04-17
forum: Server Platforms
---

### Post by alexmc on 2010-04-17
Firstly: is this the best place to discuss Ubuntu Enterprise Cloud? I'm supposed to enter a "prefix" but there isn't one for UEC.

I have a number of problems with my UEC install which doesn't seem to be covered by the documentation. I'm using 9.10 server (64bit version on the Cluster Controller, 32bit on the nodes). 

The cluster controller is supposed to be doing everything other than running compute nodes but I have the following issues.

I am instructed to start the following services:



alex@hamilton:~$ sudo start eucalyptus-walrus-publication
start: Unknown job: eucalyptus-walrus-publication
alex@hamilton:~$  sudo start eucalyptus-cc-publication
start: Job is already running: eucalyptus-cc-publication
alex@hamilton:~$  sudo start eucalyptus-nc-publication
start: Unknown job: eucalyptus-nc-publication

But two of them don't exist

alex@hamilton:~$ pushd /etc/init.d/
/etc/init.d ~
alex@hamilton:/etc/init.d$ ls eucalyptus*
eucalyptus                  eucalyptus-sc
eucalyptus-cc               eucalyptus-sc-registration
eucalyptus-cc-publication   eucalyptus-walrus
eucalyptus-cc-registration  eucalyptus-walrus-registration
eucalyptus-cloud

What is the difference between these "service", "service-publication" and "service-registration" jobs?

By default there are no "nc" jobs on the cluster controller. So am I running it on the wrong machine? Should there be nc jobs there? I don't mind if there are.

Thanks for any pointers

---

### Post by rubensmatos on 2010-04-30
Looking in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  I noticed that services 
eucalyptus-walrus-publication
eucalyptus-sc-publication
eucalyptus-nc-publication

just does not exist in karmic koala (9.10) packages, 
but they belong to lucid lynx (10.04) packages.

Probably an update to lucid is needed, or the tutorial in ubuntu site can't be followed.

---

