---
title: "CLC not running"
date: 2011-06-02
forum: Ubuntu Cloud and Juju
---

### Post by yskhatib on 2011-06-02
Hello,

It seems that I am not starting CLC properly, as the Web interface is never up and the CC log keeps throwing:
 FATAL 86 tCredentialBootstrapper| Waiting for system credentials before proceeding with startup...

My setup has 2 machines. CLC (installed from package) is on Ubuntu Desktop 10.10, while CC and NC (installed from CD) are on another machine running Ubuntu Server 10.10. Eucalyptus version is 2.0.

The interfaces on the CLC are:
 auto lo
 iface lo inet loopback

auto br0
 iface br0 inet dhcp
 bridge_ports eth0
 bridge_fd 9
 bridge_hello 2
 bridge_maxage 12
 bridge_stp off

...while on the CC/NC it is:
 auto lo
 iface lo inet loopback

auto eth0
 iface eth0 inet manual

auto br0
 iface br0 inet dhcp
 bridge_ports eth0
 bridge_fd 9
 bridge_hello 2
 bridge_maxage 12
 bridge_stp off

If I try "euca_conf --list-nodes" on the CLC I get:
 grep: //var/lib/eucalyptus/db//*auth*: No such file or directory
 ERROR: cannot locate entry in eucalyptus database, try logging in through the admin web interface
 ERROR: cannot get credentials

It is apparent that the CLC is not set up properly, but I can't find the problem. Does any one have an idea? Let me know if more details are needed.

Cheers.

---

### Post by kim0 on 2011-06-04
Hi, 
It seems UEC is not set up correctly for you, the best advice I can say is to install from the CD integrated installer. Here are the instructions for that
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by Rusty au Lait on 2011-06-07
Well I have two questions.
Why are you using a desktop installation as you CLC server? There are a few things I can think of concerning this. Your Credentials and subdirectories for starters.
Why is the CL on the same machine as the NC? I believe the CL is trying to communicate with itself (NIC hardware wise) when it communicates with its NC.

just my 2¢

---

### Post by yskhatib on 2011-06-07
Thanks for your replies.

I was just trying to get a 2-machine 'cloud' up and running for me to explore Eucalyptus. I'll reconfigure using Ubuntu server, but what is the best setup with 2 machines?

CLC+CC  //  NC??

---

### Post by Sum Guy on 2011-06-15
The recommended setup is everything but the NC on one server, and the NC on the other. Obviously you can use more exotic layouts with more systems. Have you tried running euca_conf using sudo? I get an error like that when I run euca_conf without sudo, even though it works fine with sudo.

EDIT: the recommended setup is the default on a CD install.

---

