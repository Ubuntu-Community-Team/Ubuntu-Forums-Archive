---
title: "[SOLVED] 2.6.24-22 kernel update &amp;amp; Virtualbox problem"
date: 2008-11-29
forum: Virtualisation
---

### Post by Old_Grey_Wolf on 2008-11-29
I can not find modules in the repository for kernel 2.6.24-22. Should I wait a few days for them to appear or do I need to compile my own using the Virtualbox source?

---

### Post by HotShotDJ on 2008-11-29
What happens when you run the following in a terminal?```
sudo /etc/init.d/vboxdrv setup
```(You may need to install build-essential first if it isn't already installed)

---

### Post by Old_Grey_Wolf on 2008-11-30
When I tried to install build-essential it asked for a CD of an OS I had run in a VM. I haven't burned it to a CD.

---

### Post by HotShotDJ on 2008-11-30
> **Old_Gray_Wolf said:**
> When I tried to install build-essential it asked for a CD of an OS I had run in a VM. I haven't burned it to a CD.
:confused:

You need to install build-essential on the HOST operating system, not in the VM.```
sudo apt-get install build-essential
```

---

### Post by Old_Grey_Wolf on 2008-11-30
It is fixed.

I made up my mind and finally upgraded to 8.10 and everything is working great. Everything I have tried just works. 
:guitar:

---

### Post by Calmor on 2008-12-02
> **HotShotDJ said:**
> What happens when you run the following in a terminal?```
sudo /etc/init.d/vboxdrv setup
```(You may need to install build-essential first if it isn't already installed)

I get:

```
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

Build-essential is installed and up to date.

Any other suggestions?  So far, I have been booting into the -21 kernel to keep everything functioning.

I'm running 8.04.1 x64, and VirtualBox OSE from the repositories.

Thanks!

---

### Post by Stunts on 2008-12-02
I have the exact same issue, and I'm using the same workaround than Calmor. Any ideas on how long it will take to get those modules downstream?
It usually comes at the same time the main kernel modules, so I'm a bit apprehensive...
Hope it gets solved soon.

---

### Post by HotShotDJ on 2008-12-02
> **Calmor said:**
> I get:

```
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

Build-essential is installed and up to date.Drat!  This must have something to do with the differences between the "official" version from SUN (that I use) and the OSE version from the Ubuntu repositories.

One way to solve the issue is to switch to the official SUN version (see [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  -- I recommend adding the proper repository as instructed toward the bottom of that page)

Other than that, I guess its just a matter of waiting for the proper modules to be added to the ubuntu repository.

---

### Post by Calmor on 2008-12-02
> **HotShotDJ said:**
> Drat!  This must have something to do with the differences between the "official" version from SUN (that I use) and the OSE version from the Ubuntu repositories.

I've contemplated installing the full version.  I like the free (as in speech) theory, and try to stick with it whenever feasible... not that I'm tweaking the source of anything.  

One thing that I sometimes miss in the OSE version is the USB support.  Does the full version support full USB passthrough (so, for instance, I could tether a BlackBerry and have internet in at least the VM, if not both with bridged networking mode?)  Does the host OS need to recognize and support the device, or just need to recognize that it exists?

>  One way to solve the issue is to switch to the official SUN version (see [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  -- I recommend adding the proper repository as instructed toward the bottom of that page)

Other than that, I guess its just a matter of waiting for the proper modules to be added to the ubuntu repository.

I've contemplated learning to build the kernel module myself, but I just don't have the time right now.  So, at least until I decide if the full version is worth it, I'll keep booting into the -21 kernel if I need the VM.

Thanks for your help!

---

### Post by HotShotDJ on 2008-12-02
> **Calmor said:**
> One thing that I sometimes miss in the OSE version is the USB support.  Does the full version support full USB passthrough (so, for instance, I could tether a BlackBerry and have internet in at least the VM, if not both with bridged networking mode?)  Does the host OS need to recognize and support the device, or just need to recognize that it exists?So far, I've had no trouble with USB.  VirtualBox will grab control of a particular device based on the Vendor & Product ID if you 1) set up a device filter (easy as falling off a log) and 2) plug it in while your virtualized OS is running.  The example you give with your BlackBerry should work swimmingly (the operative word being "should").
> **Calmor said:**
> I've contemplated learning to build the kernel module myself, but I just don't have the time right now.This is another thing that is as easy as falling off a log with the official SUN version.  As I noted above, if you need to build the virtualbox kernel module, you simply make sure that build-essential is installed and then run:```
sudo /etc/init.d/vboxdrv setup
```Its so easy that I walked my mother (70 years old!) through it by phone just this afternoon (she runs Hardy, which I'll keep her using until the next Long Term Release).

As far as wondering if it is worth moving to the more restrictive PUEL from the "free as in beer" version... for me, it is.  Having the USB support is important to me.  And remember, if you are using the guest additions, you already are using the more restrictive PUEL anyway.

---

### Post by Old_Grey_Wolf on 2008-12-02
> **HotShotDJ said:**
> :confused:

You need to install build-essential on the HOST operating system, not in the VM.```
sudo apt-get install build-essential
```

I was installing build-essential on the HOST machine. However, my problems were Solved (thread marked solved) when I upgrades from 8.04.1 to 8.10.:p

---

### Post by HotShotDJ on 2008-12-02
> **Old_Gray_Wolf said:**
> I was installing build-essential on the HOST machine.Ok.  In that case, then I think I know what the problem was... but since you've upgraded to 8.10 and that fixed the issue, then it really is a moot point.
> **Old_Gray_Wolf said:**
> However, my problems were Solved (thread marked solved) when I upgrades from 8.04.1 to 8.10.:p:)  Yeah, we kind of hijacked your thread... but you were done with it anyway... LOL.

---

### Post by Old_Grey_Wolf on 2008-12-02
> **HotShotDJ said:**
> Ok.  In that case, then I think I know what the problem was... but since you've upgraded to 8.10 and that fixed the issue, then it really is a moot point.
:)

I am curious what the problem was. I may run into it again. 

> Yeah, we kind of hijacked your thread... but you were done with it anyway... LOL.

I don't care about the thread being hijacked. That is what old threads are for. I just wanted people to know that upgrading to 8.10 could solve their problem. That is if upgrading to 8.10 doesn't introduce other problems. I did a full backup before I tried the upgrade.:p

---

### Post by HotShotDJ on 2008-12-02
> **Old_Gray_Wolf said:**
> I am curious what the problem was. I may run into it again.If you look at the Software Sources (from Synaptic, click on "Settings" then select Repositories -- in 8.10, you can just open Software Sources from System --> Administration... I can't remember if 8.04 has that menu option)

Then, make sure that CD-ROM/DVD  is NOT checked off in the Ubuntu Software tab.  Also, make sure there is nothing referencing the CD-ROM/DVD on the Third Party Software tab.  If there is, make sure it is also not checked off.

---

### Post by Calmor on 2008-12-03
> **HotShotDJ said:**
> So far, I've had no trouble with USB.  VirtualBox will grab control of a particular device based on the Vendor & Product ID if you 1) set up a device filter (easy as falling off a log) and 2) plug it in while your virtualized OS is running.  The example you give with your BlackBerry should work swimmingly (the operative word being "should").

It may be worth giving a shot then.  I do occasionally use a few Windows-only USB devices (Sony Reader, and the aforementioned BlackBerry), and it might be nice to have those working again.  I've tried some of the BB linux ideas, but running x64 also makes things more complicated than I'm willing to deal with.  In fact, I find that with several things... but that's a whole different topic.  I wouldn't say I'm a linux expert, but I successfully set up a Verizon Wireless card on Gutsy, so I have a little experience with Vendor & Product ID research... so the USB in Virtualbox sounds easy.

> This is another thing that is as easy as falling off a log with the official SUN version.  As I noted above, if you need to build the virtualbox kernel module, you simply make sure that build-essential is installed and then run:```
sudo /etc/init.d/vboxdrv setup
```Its so easy that I walked my mother (70 years old!) through it by phone just this afternoon (she runs Hardy, which I'll keep her using until the next Long Term Release).

I've stayed with Hardy too.  I installed OOo 3.0 on the machine I use every day, and really haven't found the need to go to Intrepid.  I will when there are some functions I need that Hardy won't give.

Quick question - can I keep my .virtualbox forumla and uninstall/reinstall without having to set up my virtual machines again?  I deleted one once by accident... pain to set back up.

To the OP, I think the kernel in 8.10 is even newer than the newest Hardy kernel, since Hardy will only get bugfixes and security patches now.  Virtualbox modules apparently were forgotten about when the new kernel was released for 8.04, or something is causing an incompatibility... but that's why upgrading to 8.10 works.

[QUOTE]As far as wondering if it is worth moving to the more restrictive PUEL from the "free as in beer" version... for me, it is.  Having the USB support is important to me.  And remember, if you are using the guest additions, you already are using the more restrictive PUEL anyway.

Hmm.. interesting, didn't realize the guest additions were covered under PUEL.  I'm using them in my WindowsXP VM.  Maybe I'll give the full SUN version a try.

---

### Post by HotShotDJ on 2008-12-03
> **Calmor said:**
> Quick question - can I keep my .virtualbox forumla and uninstall/reinstall without having to set up my virtual machines again?  I deleted one once by accident... pain to set back up.Yes. I've moved between PUEL and OSE versions using the same virtual machine.  Any minor difficulties are usually easy to diagnose and fix simply by altering a few VirtualBox settings and then installing the proper guest additions.

---

### Post by bthoward on 2008-12-18
So I've gotten here via a google search and have done a bit of searching and I'm having a hard time turning up what I need to get a Blackberry working.....

I've added filters for the two devices that come up when I plug my Blackberry in.  These include everything right down to the serial number and all.  Essentially everything but the port.  

I then recompiled the driver too (just incase since it was mentioned here and its pretty cake).  No change...

When I plug the device in (after the VM is up).  I just get the host connecting to the thing...

This is what is shown in dmesg upon a plug while the VM is open:
```
[118796.604063] usb 5-7: new high speed USB device using ehci_hcd and address 15
[118796.766790] usb 5-7: configuration #1 chosen from 1 choice
[118796.800167] scsi13 : SCSI emulation for USB Mass Storage devices
[118796.805271] usb-storage: device found at 15
[118796.805276] usb-storage: waiting for device to settle before scanning
[118801.804777] usb-storage: device scan complete
[118801.806135] scsi 13:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS
[118801.807375] scsi 13:0:0:1: Direct-Access     RIM      BlackBerry       1003 PQ: 0 ANSI: 4 CCS
[118801.829910] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[118801.830577] sd 13:0:0:0: Attached scsi generic sg2 type 0
[118801.835127] sd 13:0:0:1: [sdc] Attached SCSI removable disk
[118801.837140] sd 13:0:0:1: Attached scsi generic sg3 type 0
```


Any tips?

EDIT:  I should state I'm running Intrepid (8.10) and running VirtualBox full version 2.1.0

---

### Post by mikeytdy on 2008-12-22
This worked for me:

[https://bugs.edge.launchpad.net/ubuntu/hardy/+source/virtualbox-ose-modules/+bug/303199/comments/19](https://bugs.edge.launchpad.net/ubuntu/hardy/+source/virtualbox-ose-modules/+bug/303199/comments/19)

It's even simpler than that:

sudo apt-get install virtualbox-ose-source
sudo module-assistant auto-install virtualbox-ose-source
sudo /etc/init.d/vboxdrv start

(the last step basically just loads the module with modprobe, but it also does a little bit of house keeping)

And you might only need to run the last two steps from above; according the the module-assistant man page:

"auto-install is followed by one or more packages desired for installation. It will run prepare to configure your system to build packages, get the package source, try to build it for the current kernel and install it."

---

### Post by teknotuck on 2008-12-23
Thanks mikeytdy, That broke last month and while i never ever use windows wouldnt you know it, it would have been helpful probably about 10 times so far in the last month to have this working again.  

Thanks again.
Tnt  :KS

---

### Post by Stunts on 2008-12-25
> This worked for me:

[https://bugs.edge.launchpad.net/ubun...99/comments/19]("https://bugs.edge.launchpad.net/ubuntu/hardy/+source/virtualbox-ose-modules/+bug/303199/comments/19")

It's even simpler than that:

sudo apt-get install virtualbox-ose-source
sudo module-assistant auto-install virtualbox-ose-source
sudo /etc/init.d/vboxdrv start

(the last step basically just loads the module with modprobe, but it also does a little bit of house keeping)

And you might only need to run the last two steps from above; according the the module-assistant man page:

"auto-install is followed by one or more packages desired for installation. It will run prepare to configure your system to build packages, get the package source, try to build it for the current kernel and install it."

Darn! Didn't work for me. Module assistant gives an error about "nothing to make for...."

---

### Post by xoros on 2009-01-07
There is a bug for the latest kernel and module-assistant. 

See this thread:
[http://ubuntuforums.org/showthread.php?t=1033758](http://ubuntuforums.org/showthread.php?t=1033758)

```
:/# module-assistant auto-install virtualbox-ose-source

Updated infos about 1 packages
Getting source for kernel version: 2.6.27-9-generic
Kernel headers available in /usr/src/linux-headers-2.6.27-9-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  debootstrap kpartx python-cheetah
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
The source tarball could not be found!
Package virtualbox-ose-source not installed?
Running "m-a -f get virtualbox-ose-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.27-9-generic KSRC=/usr/src/linux KDREV=2.6.27-9.19 kdist_image
find: `/usr/src/modules/virtualbox*': No such file or directory
:/#
 
```

---

### Post by annaa on 2009-01-11
OK, newbie here.  I've been running XP on Vbox very successfully for over a week (many thanks to HotShotDJ!!), until a software update last Friday. Presumably Ubuntu, although About only gives me the version of the Help file). Anyway, now the VBox machine fails with the following message:

"Virtual machine 'XP' has terminated unexpectedly during startup.
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}"

and then:
VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

So I opened terminal and ran "/etc/init.d/vboxdrv setup", which in turn gave me error:
annaa@ubuntu-desktop:~$ '/etc/init.d/vboxdrv setup'
bash: /etc/init.d/vboxdrv setup: No such file or directory
annaa@ubuntu-desktop:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module                                            open: Permission denied
 *  done.
open: Permission denied
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 337: cannot create /var/log/vbox-install.log: Permission denied

open: Permission denied
 * Look at /var/log/vbox-install.log to find out what went wrong
annaa@ubuntu-desktop:~$ 
annaa@ubuntu-desktop:~$ 
annaa@ubuntu-desktop:~$ 


Sure enough, there is no vbox-install.log, but that hardly helps me.  I'm a MS refugee, am trying Ubuntu because I'm really poor at all this command-line hacking stuff.

Can anyone please help? Do I create a blank vbox-install.log file, or populate it with my password, or what?

Thanks for any help!

---

### Post by HotShotDJ on 2009-01-11
> **annaa said:**
> So I opened terminal and ran "/etc/init.d/vboxdrv setup"AH!!  So close but yet.... you know the rest. :)  The proper way to do that is to open a terminal and run```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by annaa on 2009-01-11
DJ, you totally rock! A gazillion blessings upon you from the god(s)/powers of your choice!  After the following message, I could open the Vb XP:

annaa@ubuntu-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for annaa: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.
annaa@ubuntu-desktop:~$ 

So, seriously, is it better *not* to run the updates when they arrive, and just stick with the version that works?  Good things to all the volunteers who make Ubuntu, bless 'em all too, but maybe it isn't quite ready for us M$ bozos to use out of the box yet?

Thanks, thanks again!

---

### Post by HotShotDJ on 2009-01-11
> **annaa said:**
> So, seriously, is it better *not* to run the updates when they arrive, and just stick with the version that works?No, no... go ahead and run the updates.  Believe it or not, this one wasn't Microsoft's fault.  Most likely, you updated a the kernel or something with the kernel modules, which is what caused your problem.  Now that you know what to do when it happens, you don't really have to worry about it.  If you ever again run into an error message from Virtualbox that has something to do with the Driver, just run that code again.  Since the type of updates that may cause these errors tend to be kernel-level security issues, it is better to run the updates and fix any problems after.

---

### Post by annaa on 2009-01-11
Well, OK, if you say so (and you're going to be around for a couple more decades ;).  
Thanks again, I appreciate your time, expertise, and willingness to share them more than words can express!

---

### Post by Stunts on 2009-01-12
Good news!

After Friday's kernel updates Vbox is up and running back again!
All is well now.

---

