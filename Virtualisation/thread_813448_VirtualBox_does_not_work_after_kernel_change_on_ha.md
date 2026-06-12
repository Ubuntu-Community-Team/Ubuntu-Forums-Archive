---
title: "VirtualBox does not work after kernel change on hardy"
date: 2008-05-30
forum: Virtualisation
---

### Post by Valir on 2008-05-30
Hi, 

I have VirtualBox running a guest xp on my Ubuntu Hardy machine. Everything worked fine until an update the other day that changed somehow the kernel. Now I get this errormessage:

"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root"

the sudo /etc/init.d/vboxdrv setup

gave me this: "Look at /var/log/vbox-install.log"

"Makefile:127: *** Error: Unable to find the sources of your current linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop."

what is going on and how do I fix this?

---

### Post by quelx on 2008-05-30
you need to install the kernel header package for you new kernel

```
sudo apt-get install linux-headers-`uname -r`
```

then rerun **sudo /etc/init.d/vboxdrv setup**

---

### Post by InfinityCircuit on 2008-05-30
Beat me to it.

---

### Post by Valir on 2008-06-01
Worked like a charm. Solved.

Thanks

---

### Post by mikeivanov on 2008-06-04
> **quelx said:**
> then rerun **sudo /etc/init.d/vboxdrv setup**
```

$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

```

But what could *this* mean? :confused:

---

### Post by Valir on 2008-06-07
try sudo /etc/init.d/vboxdrv start

---

### Post by sam_delta on 2008-06-07
> **mikeivanov said:**
> ```

$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

```

But what could *this* mean? :confused:
that means that you can only type the following commands```
sudo /etc/init.d/vboxdrv start
sudo /etc/init.d/vboxdrv stop
sudo /etc/init.d/vboxdrv restart
or 
sudo /etc/init.d/vboxdrv status
```
sam

---

### Post by mikeivanov on 2008-06-07
Hi Sam,

> **sam_delta said:**
> that means that you can only type the following commands...
sam

Well, that's exactly what the message says. I was asking *why* :-)

I've found the answer. The opensource edition of VirtualBox does not support driver recompilation, only the non-free version does. The documentation says 'wait until we release an updated driver'. 

So here is how I solved the problem: I downloaded and installed Sun xVM VirtualBox - a closed-source variant of VB. 

What I really don't understand is why they are preventing driver recompilation in OSE since the both editions are FREE.

---

### Post by sam_delta on 2008-06-07
ah alright mike, thanks for the info about the driver recompilation anyways, i dont know why such a thing if both are free

sam

---

### Post by Oldsoldier2003 on 2008-06-07
> **mikeivanov said:**
> Hi Sam,



Well, that's exactly what the message says. I was asking *why* :-)

I've found the answer. The opensource edition of VirtualBox does not support driver recompilation, only the non-free version does. The documentation says 'wait until we release an updated driver'. 

So here is how I solved the problem: I downloaded and installed Sun xVM VirtualBox - a closed-source variant of VB. 

What I really don't understand is why they are preventing driver recompilation in OSE since the both editions are FREE.

Because the puel version isn't free in the strict sense of the word. its an evaluation version of a commercial product for "personal use and evaluation". Its closed source where as the ose is the "open source edition".

---

### Post by xItachi on 2008-07-19
> **quelx said:**
> you need to install the kernel header package for you new kernel

```
sudo apt-get install linux-headers-`uname -r`
```

then rerun **sudo /etc/init.d/vboxdrv setup**


I did that, but it said:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-14-generic has no installation candidate

```

Any ideas?

---

### Post by camarriott on 2008-10-16
I'm also getting that error when I run "sudo /etc/init.d/vboxdrv setup"

I went ahead and ran  "sudo apt-get install linux-headers-`uname -r`" and I got this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I assume that means I'm up to date.. Any other suggestions to get virtualbox working?

---

### Post by tiredofguessingusernames on 2008-10-25
Hi

I also had it working until recently,and then I got the same error. What worked for me was installing the following package from the repo's:

virtualbox-ose-modules-generic

I think this downloads the relevant headers for your kernel. Heaven alone knows how it managed to work before this.

---

### Post by Jim D v2.0 on 2008-10-25
I had the same problem with my wife's computer but not mine. The only difference was that I had the repository listed in the third-party software for synaptic. In the case of my wife's computer we needed to add the line 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

 to the third-party software in the repositories, and then everything has worked just fine since.

The following page has the needed information, along with the public key and fingerprint.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

