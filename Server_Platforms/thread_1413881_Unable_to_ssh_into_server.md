---
title: "Unable to ssh into server"
date: 2010-02-23
forum: Server Platforms
---

### Post by F13 on 2010-02-23
Hello all,

I'm having a problem connecting to my server with ssh.

I'm running the latest Ubuntu 9.10 32-bit server, inside a virtual machine on a Mac (VMware Fusion 3, running on OS X 10.6.2 with 64-bit kernel).
I've set up a network interface (eth2) to act as a host-only network between the virtual machine and the host.

I can ssh into the server from my Mac when I type in its IP address
ssh root@[IP address]

BUT, I can not connect to the server when I type in it's hostname
ssh [email]root@myserver.local[/email]

do I need to open a port with ufw? or configure something else in the ssh settings?

Thanks in advance,

---

### Post by bhaverkamp on 2010-02-23
I have found that the vmware network drivers are interfering with bonjour to prevent using host names from the command line. You can test this by shutting down the vmware drivers (only needed when running VMs). If you only run vmware infrequently this is a reasonable solution. If you run it a lot and cannot shut it down you are @#$% out of luck. Try filing a bug.

---

