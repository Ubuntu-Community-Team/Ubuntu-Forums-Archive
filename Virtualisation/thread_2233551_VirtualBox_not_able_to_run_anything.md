---
title: "VirtualBox not able to run anything"
date: 2014-07-09
forum: Virtualisation
---

### Post by cogitans on 2014-07-09
I've been using VirtualBox for several years now but have never experinced anything like this.

I'm trying to create a 64bit virtual mashine on my 64bit system (Linux Mint 17). That is a task in itself which I think I figured out how to do.
But I can't even get to test any of the settings as any of my virtual mashines wont boot up.

I tried all these attempts:

Initial message:
> Virtualbox Linux kerneldriver (vboxdrv) is either not loaded or there is a permissionproblem

So I did a "**sudo /etc/init.d/vboxdrv setup**"

Which resulted in this:
> Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

So I went to "**vbox-install.log**":
which states: > /etc/init.d/vboxdrv: 334: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/build_in_tmp: not found
that's didn't give me much usable information so I did a little more testing.

Checked for services:
"**sudo service vboxdrv status**":
->> VirtualBox kernelmodule is not loaded

I made sure that I had the dkms installed:
"**sudo apt-get install virtualbox-dkms**"

which resulted in this messages:
> Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Sætter virtualbox (4.2.16-dfsg-3ubuntu0.1) op...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for ureadahead (0.100.0-16) ...
Setting virtualbox-dkms (4.2.16-dfsg-3ubuntu0.1) up...
Loading new virtualbox-4.2.16 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-24-generic
/usr/sbin/dkms: line 1902: cannot create temp file for here-document: Access denied
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.

Another post online gave me this idea:
"**sudo modprobe vboxdrv**"

but the result was:
> modprobe: FATAL: Module vboxdrv not found

Does anybody have any idea of how I get closer to a solution?

---

### Post by cogitans on 2014-07-09
I tried installing "linux-generic-pae", too, but Synaptic states that I have broken packages.

I fixed some packedes through:
> sudo aptitude -f

but it didn't fix the problem.

And the same from:
                        > sudo apt-get check

 sudo apt-get autoremove

 sudo apt-get install -f
 sudo dpkg --configure -a


I did "uname -r"
which gave this:
> 3.13.0-24-generic


Then I did this: "sudo dpkg-reconfigure virtualbox-dkms"
which gave this:
> /usr/sbin/dkms: line 1902: cannot create temp file for here-document: access denied

------------------------------
Deleting module version: 4.2.16
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-4.2.16 DKMS files...
Building only for 3.13.0-24-generic
/usr/sbin/dkms: line 1902: cannot create temp file for here-document: Access denied
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.

---

### Post by TheFu on 2014-07-09
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

You need to install the dependencies. In this case, the kernel source. There are different sources based on the architecture and installed version on your machine. Whatever you do, don't just install the exact version of the sources - get a metapackage so that when a new kernel gets installed, all this stuff is automatically handled for you.  Otherwise, you'll be without the correct kernel source and vbox drivers won't be built and .... 

It will be bad.

Installing linux-generic-pae probably isn't the correct version on a 64-bit architecture. 
 [http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies](http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies) explains.

---

### Post by cogitans on 2014-07-09
Well, I followed
[http://austinmarton.wordpress.com/2013/02/10/virtualbox-driver-vboxdrv-missing-after-ubuntu-12-04-upgrade/](http://austinmarton.wordpress.com/2013/02/10/virtualbox-driver-vboxdrv-missing-after-ubuntu-12-04-upgrade/)

which states something similiar to what I did previously. But my system kept on telling me that the header for my system didn't excist.
So I went into softwaresources and chose another server. NOW there was a header for my kernel (???) which I downloaded (sudo apt-get install linux-headers-3.13.0-24-generic) and followed the rest of the setup on the link.
But 
> sudo /etc/init.d/vboxdrv setup
still gives this output:
> Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Removing old VirtualBox pci kernel module ...done.
Removing old VirtualBox netadp kernel module ...done.
Removing old VirtualBox netflt kernel module ...done.
Removing old VirtualBox kernel module ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)


Suddenly when I modified the sourcelist some updates are available. After I install those one upgrade is still missing.
> The following packages are hold back:
lib32nss-mdns

Could this have anything to do with the fact that mdns isn't able to compile the virtualbox-files?

---

### Post by TheFu on 2014-07-09
I would start over.  Purge everything virtualbox and begin again following **reputable instructions** for your EXACT hostOS (architecture, 32/64-bit, release, etc).  Be certain to remove any added PPAs, if you added any too.

Begin with the dependencies - build-essential and the correct kernel headers FOR YOUR SYSTEM.
Don't forget that adding your userid to the correct group is likely necessary too. Don't know the group - ... 

Wish I could help more - stopped using vbox in any serious way a few years ago - KVM rocks for server on server virtualization and I'm looking into Docker for single-app virtualization.

---

### Post by SeijiSensei on 2014-07-09
By far the easiest and most reliable method for installing VirtualBox is to [use Oracle's repository]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian_based_Linux_distributions") as described on the VB site.  It will bring in the required dependencies to build the kernel module and will update them as the kernel updates.

---

### Post by cogitans on 2014-07-09
I think I figured out what the problem is now. But I still don't have the solution to it.
All the errors is due to the fact that VirtualBox does NOT recognize that my system is 64bit. THe acceleration-tab on the "System"-page is all geyet out.
I've checked my BIOS for anything like "hardware virtualization" and "VT-X". The BIOS states that VT-X is supported. I can't find anywhere to set hardware virtualization or any other checks regarding VT-X (my motherboard is Asus H81M-D). Linux DOES recognize the 64bit system.
Another hint to the fact that VirtualBox isn't setup correctly is the fact that if I create any virtual mashine then I am NOT able to choose any 64bit system as shown in the pictures here: [https://forums.virtualbox.org/viewtopic.php?f=6&t=57871](https://forums.virtualbox.org/viewtopic.php?f=6&t=57871). That post is about windows and I don't know how to fix a linux-situation.

So if anybody is able to point me in the right direction I would be very pleased....

---

### Post by QIII on 2014-07-09
Hello!

I might have missed it,  but what exactly are your hardware specs?

Your BIOS may call it "Intel Virtualization Technology" or similar.

Edit:  I just checked.  That is exactly what it is called under the Advanced Menu.  It is disabled by default.  Enable it and you should be golden - if your processor supports it.

Also:

I want to echo SeijiSensei:  use Oracle's repo.

---

### Post by cogitans on 2014-07-09
Ah, I solved it now.
I followed these setups
[http://www.youtube.com/watch?v=UVqbdrDB7aU](http://www.youtube.com/watch?v=UVqbdrDB7aU)
and
[http://www.youtube.com/watch?v=2mknx7_5-qY](http://www.youtube.com/watch?v=2mknx7_5-qY)
which shows where to modify the BIOS so that VT-X is enabled. Now I'm able to create virtual images that's 64 bit and now the installation is running :-)

(UPDATE: which is what [**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170") also stated just before [as I notice now])

---

### Post by arneolaf2 on 2015-02-04
For me, this solved it:
```
sudo apt-get --reinstall install virtualbox-dkms
```

---

### Post by frytek on 2015-02-15
> **arneolaf2 said:**
> For me, this solved it:
```
sudo apt-get --reinstall install virtualbox-dkms
```

confirmed. It worked for me, too.

---

