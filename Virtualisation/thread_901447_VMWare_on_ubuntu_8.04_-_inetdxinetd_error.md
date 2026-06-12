---
title: "VMWare on ubuntu 8.04 - inetd/xinetd error"
date: 2008-08-26
forum: Virtualisation
---

### Post by 3strandchords on 2008-08-26
Hi all.

I'm trying to install vmware on my ubuntu laptop in order to test whether or not virtualization would be the way to go for our network.  So, once I have VMWare running, I'll be installing between 3 and 5 ubuntu server virtual machines.

I've downloaded VMWare Server 1.0.6 from the web and attempted to follow the guide found on [this thread]("http://ubuntuforums.org/showthread.php?t=779934") in order to get everything working.

At the end of the SERVER install, I get the following text displayed:```
Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.
```

There is an /etc/inet.d folder out there, but (as the error states) no inetd.conf.

How do I move forward?  Can I create an empty inetd.conf file and allow the installing perl script to update it appropriately?

Thanks.....

---

### Post by seanc7 on 2008-08-26
Can you install xinetd onto the laptop? That would solve the problem. VMWare requires xinetd or inetd to run the daemon which listens for client connections from remote systems.

---

### Post by y@w on 2008-08-26
```
sudo apt-get install xinetd
```

..should do it. Then just run the config script again.

Also, once you're done, you'll need to run this to make the console work:

```
sudo ln -s /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
```

---

### Post by 3strandchords on 2008-08-26
Thanks all for the replies... One follow-up:

I've installed xinetd and completed the server install... However, something doesn't seem to have taken.  

After restarting (yeah, I know), I opened a terminal and tried to install the management tools (vmware-mui-distrib) but the install fails...
```
Installing the content of the package.

VMware Server must be installed on this machine for the VMware Management 
Interface to work

Execution aborted.
```

But everything *should* be working... I also have the development/scripting and console tars that I intend to install.

Thanks, again for the help.

---

