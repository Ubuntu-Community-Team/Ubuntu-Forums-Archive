---
title: "Virtual box after gutsy -- Problems with module"
date: 2007-10-23
forum: Virtualisation
---

### Post by mohnkern on 2007-10-23
I've recently upgrade to Gutsy, and I'm having problem with virtualbox.  

When I attempt to run the application (virtualbox) I get the following error:

WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-modules package for your kernel.

         You will not be able to start VMs until this problem is fixed.


When I type sudo apt-get install virtualbox-ose-modules  I get

Package virtualbox-ose-modules is a virtual package provided by:
  virtualbox-ose-modules-2.6.22-14-server 6
  virtualbox-ose-modules-2.6.22-14-generic 6


So I type

sudo apt-get install  virtualbox-ose-modules-2.6.22-14-server

and sudo apt-get install  virtualbox-ose-modules-2.6.22-14-generic


At the end of the install I get:

* Modprobe vboxdrv failed. Please use 'dmesg' to find out why.


but dmesg | grep vbox or dmesg | grep virtual gives me nothing.


It looks like there's a module that's not installing, but apt-get isn't installing it properly.



Any ideas?

---

### Post by mjwood0 on 2007-10-23
One thought is that you installed both the server and the workstation version of the file.

While I really don't see why this would be a problem I'm just not sure what exactly is different between the kernels.  

In the end, Virtualbox needs the correct kernel module for the kernel you're running.

Can you do the following and post the results:
```
uname -r
```

---

### Post by mohnkern on 2007-10-23
WHen I did the Gutsy upgrade, it did install the most recent kernel



2.6.22-14-386

---

### Post by mjwood0 on 2007-10-23
Correct.  Therefore, the new kernel modules were necessary.

I'm guessing you should uninstall both ose packages and just re-install the generic one.  The server one is for the server kernel, not the generic kernel.

I'm going to be attempting this exact thing tonight so if it works for me, I'll post my info.  Otherwise, I'm sure you'll see questions!

---

### Post by mohnkern on 2007-10-23
Let me know what you find out.  I'll try the same thing as well.

---

### Post by mohnkern on 2007-10-23
Now this is interesting:

$ sudo apt-get remove virtualbox-ose-modules-2.6.22-14-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose-modules-2.6.22-14-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ 

$ sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Looks like I'm running what I'm supposed to be running.



> **mjwood0 said:**
> Correct.  Therefore, the new kernel modules were necessary.

I'm guessing you should uninstall both ose packages and just re-install the generic one.  The server one is for the server kernel, not the generic kernel.

I'm going to be attempting this exact thing tonight so if it works for me, I'll post my info.  Otherwise, I'm sure you'll see questions!

---

### Post by mohnkern on 2007-10-23
Just to make sure I did an apt-get purge of virtualbox-ose and virtualbox-ose-modules-2.6.22-14-server and virtualbox-ose-modules-2.6.22-14-generic

Then I did a apt-get install virtualbox-ose virtualbox-ose-modules-2.6.22-14-generic

In the middle I get the following error:

Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...


That's not amusing.





> **mohnkern said:**
> Now this is interesting:

$ sudo apt-get remove virtualbox-ose-modules-2.6.22-14-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose-modules-2.6.22-14-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ 

$ sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Looks like I'm running what I'm supposed to be running.

---

### Post by j0sh78 on 2007-10-23
in terminal type:
sudo /etc/init.d/vboxdrv setup

enjoy ;-)

---

### Post by mohnkern on 2007-10-23
Well
$ sudo /etc/init.d/vboxdrv setup
[sudo] password for mohnkern:
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
$

and

$ sudo /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.


$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                                                            FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
$ 



> **j0sh78 said:**
> in terminal type:
sudo /etc/init.d/vboxdrv setup

enjoy ;-)

---

### Post by j0sh78 on 2007-10-23
have you installed virtualbox-ose-modules-2.6.22-14-generic?

i not and launching 
$ sudo /etc/init.d/vboxdrv setup
i solved my problem (the same)...

---

### Post by DarkDancer on 2007-10-23
I had that problem, I uninstalled it, then went to the actual virtualbox website, downloded the deb and installed it from that....

---

### Post by mohnkern on 2007-10-23
I believe so:

 sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-2.6.22-14-generic is already the newest version.
virtualbox-ose-modules-2.6.22-14-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm not quite sure what the "set to manual installed" means, but it's telling me it's installed.


> **j0sh78 said:**
> have you installed virtualbox-ose-modules-2.6.22-14-generic?

i not and launching 
$ sudo /etc/init.d/vboxdrv setup
i solved my problem (the same)...

---

### Post by mohnkern on 2007-10-23
I tried that as well, with the same results Didn't work).  Very strange.  



> **DarkDancer said:**
> I had that problem, I uninstalled it, then went to the actual virtualbox website, downloded the deb and installed it from that....

---

### Post by Jose Catre-Vandis on 2007-10-23
Looks like a similar problem i had when installing virtualbox onto a command line server. The default server installation has a whole pile of packages not found on the desktop install, and these were needed in order to getVbox to build it's driver (vboxdrv) properly, including linux sources.

Have a look at my howto on what I did, and it may help?

[http://ubuntuforums.org/showthread.php?t=555996](http://ubuntuforums.org/showthread.php?t=555996)

remember that you have a desktop install so you may need to change some items to reflect this.

---

### Post by mohnkern on 2007-10-23
100 points for this howto/faq.  Three seconds in (literally) and I had the problem solved.  Simply de installed everything, added the virtualbox deb, and ran the install, and was up and running.  I'm creating a "virgin" Gutsy install on a vm in virtualbox now.  (I want to compare my upgrade vs. a virgin install)

Thanks so much!

> **Jose Catre-Vandis said:**
> Looks like a similar problem i had when installing virtualbox onto a command line server. The default server installation has a whole pile of packages not found on the desktop install, and these were needed in order to getVbox to build it's driver (vboxdrv) properly, including linux sources.

Have a look at my howto on what I did, and it may help?

[http://ubuntuforums.org/showthread.php?t=555996](http://ubuntuforums.org/showthread.php?t=555996)

remember that you have a desktop install so you may need to change some items to reflect this.

---

### Post by Jose Catre-Vandis on 2007-10-24
> **mohnkern said:**
> 100 points for this howto/faq.  Three seconds in (literally) and I had the problem solved.  Simply de installed everything, added the virtualbox deb, and ran the install, and was up and running.  I'm creating a "virgin" Gutsy install on a vm in virtualbox now.  (I want to compare my upgrade vs. a virgin install)

Thanks so much!

:) :) :)

---

### Post by Bigdeath on 2007-10-30
What commands did you run?

---

### Post by GERGE on 2007-12-11
Using the closed-source versiyon solved the problem for me. Look here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by hotdoog on 2007-12-11
I had the same error when I was installing the deb (from the repo for dapper on the  innotek)

I also came across [http://www.virtualbox.org/ticket/794](http://www.virtualbox.org/ticket/794) and tried the thing at the end. I had to

```
locate vboxdrv.ko
```

(may need to locate -u first)

then I did

```
insmod /path/to/exact-same-kernel.../vboxdrv.ko
```

which seems to have worked so far. I'll post any further problems I have with that.

---

### Post by Bigdeath on 2007-12-12
for some reason i get the gray screen when I try to change my cd rom settings. Which I obviously need for my xp disk.

---

### Post by Bigdeath on 2007-12-12
nvm works now

---

### Post by dfm21 on 2009-03-29
> **hotdoog said:**
> 
```
locate vboxdrv.ko
```

(may need to locate -u first)
[...]
```
insmod /path/to/exact-same-kernel.../vboxdrv.ko
```


worked for me too. thanks, hotdoog!

---

