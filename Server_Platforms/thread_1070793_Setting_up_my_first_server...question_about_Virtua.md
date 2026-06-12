---
title: "Setting up my first server...question about VirtualBox"
date: 2009-02-15
forum: Server Platforms
---

### Post by robmypro on 2009-02-15
I just installed my first Ubuntu Server (64 bit) and things seemed to go pretty smoothly. My goal of this machine is to have almost nothing on the base server except for running VirtualBox (and securing it). 

In essence I am setting up something similar to VMware ESXi, in that I really will do all of the work in the guest VM's. I would actually use ESXi but I do not have compatible hardware to run it.

So here are my questions. 

1. How I am going to administer the guest VM's (including installing them) without having a GUI on this box? Will I need to install a GUI on the server?

2. I would prefer to do it all remotely. Would SSH work? 

If anyone can point me to documents I can read regarding this I would appreciate it!

Thanks.

---

### Post by Thirtysixway on 2009-02-16
With virtualbox I'm pretty sure you can use ssh to manage all your virtual machines

[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)

---

### Post by Phlee on 2009-02-16
> **Thirtysixway said:**
> With virtualbox I'm pretty sure you can use ssh to manage all your virtual machines

[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)

That's a really good artical.  Should get you everything you need!

---

### Post by fang0654 on 2009-02-18
I currently have a few servers deployed running several VMs each, using VirtualBox.  A couple of extra things I had to do:

1.  Use VBoxManage to start the VMs, instead of VBoxHeadless.  VBoxHeadless will send all of the logging to stdout, and in order to keep the session running, you need to stay logged in (or use screen).  If you use VBoxManage startvm "VMName" -type vrdp then it is session independent.

2.  The VMs need to run under the user you create them as.  You can make a vbox user, set up the VMs under that user, and set up a script to run from rc.local to start the VMs when the machine boots up.  As an example, I have the following in my rc.local:

```
su - vbox -c "/usr/bin/start_machines.pl"
```

and in the start_machines.pl is:

```
#!/usr/bin/perl -w

use strict;

my $startcmd = "/usr/bin/VBoxManage startvm  ";

my @machines = ("New York DC", "CTI DC", "Miami DC", "San Diego DC", "Santa Ana DC", "Arizona DC");

foreach ( @machines )
{
     system("$startcmd \"$_\" -type vrdp ");
}
```


Hope this helps.

---

### Post by windependence on 2009-02-18
> **robmypro said:**
> I just installed my first Ubuntu Server (64 bit) and things seemed to go pretty smoothly. My goal of this machine is to have almost nothing on the base server except for running VirtualBox (and securing it). 

In essence I am setting up something similar to VMware ESXi, in that I really will do all of the work in the guest VM's. I would actually use ESXi but I do not have compatible hardware to run it.

So here are my questions. 

1. How I am going to administer the guest VM's (including installing them) without having a GUI on this box? Will I need to install a GUI on the server?

2. I would prefer to do it all remotely. Would SSH work? 

If anyone can point me to documents I can read regarding this I would appreciate it!

Thanks.

When you try to install ESXi, what error do you get? If it tells you it can't find any compatible disks to store VMs, I may have a solution for you.

-Tim

Linux Systems 4 You
VMware Partner

---

