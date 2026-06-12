---
title: "Judgment Day - Hardy with VMware or VirtualBox vs. Vista"
date: 2009-03-17
forum: Virtualisation
---

### Post by JerryI on 2009-03-17
First, an apology for not being brief.  I don't know how to say this briefly.  I hope that someone will at least skim this and offer me some constructive advice.

I have been trying for days to achieve a successful install of VMware under Hardy.  

The following dialog tells somebody something about my kernel/system, but I don't have any idea what a kernel is or how to interpret the info.

jerry@downstairs:~$ uname --all
Linux downstairs 2.6.24-23-generic #1 SMP Thu Nov 27 18:13:46 UTC 2008 x86_64 GNU/Linux
jerry@downstairs:~$ 

When I boot, I click the following choice:
ubuntu 8.04.2, kernel 2.6.24-23-generic

I don't know what that means either.

When I went through my VMware installation/configuration last night I thought I had made some progress, i.e., that I had finally managed to install and configure some version of VMware Server, it 'congratulated' me with the following MISSION ACCOMPLISHED message:

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running kernel completed successfully.

But my elation was short-lived.  An attempt to run the app by typing vmware at the command line resulted in:

--------------------------------------------
jerry@downstairs:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
---------------------------------------------

So I attempted to configure Vmware with that command.  Thereafter, my Firefox web browser wouldn't run, and I had to reboot my system to make it functional.  (This has happened twice now, so I have learned that it is fruitless to try to run vmware.config.pl.)

Someone told me that I should probably use the 32-bit version of VMware on my AMD64 dual-core system instead of the 64-bit version that I apparently picked (in ignorance, admittedly.  I figured I needed the 64-bit version because I have an AMD64 processor, and I had already gone through about three days of grief in the first place trying to find any version of Ubuntu that would install.  It turned out to be an AMD64 version, but I still don't know if it's 32 or 64-bit Hardy).  I don't know what I have at this point (for Ubuntu or for VMware), but the first couple paragraphs above might enlighten someone in that regard.  Then if he/she would enlighten me I might be able to respond to such questions as, "What kernel are you using? Is it 32 or 64 bit? Is it 32 or 64 bit VMware? Is your Hardy or your VMware AMD64 or Intel?

Someone else told me that I should forget about VMware and use VirtualBox instead.  At this point, about one week into this whole Ubuntu adventure I am pretty weary of turning over rocks and finding stuff I can't use, especially since it takes a day or more to turn over each rock and explore what's underneath. 

I have learned that I should not have used Ubuntu 8.10 because it is too buggy (so I wiped out Intrepid and put in Hardy) and not to use VMware 2.0 because it is flaky (so I ripped out the 2.0 that wouldn't install and put in the 1.0.6 that won't configure) and now maybe not to use VMware at all or at least not to use the 64-bit version (of Ubuntu, VMware, or both).  It's kind of like converting fahrenheit to centigrade by adding or subtracting 32 before or after multiplying or dividing by 5/9ths or 9/5ths.

I have learned that the Ubuntu installation disk will destroy your other operating system (Vista) without warning and that you might have to start all over and repartition your hard disk from scratch to make sure that Ubuntu does not stomp on Vista and make it unrecoverable.

I have also learned that a a mere mortal being cannot make a 2wire usb network adaptor work.  And I am not sure whether my usb soundblaster card can ever achieve functionality.  And maybe I will not be able to use my nvidia card in twinview mode with Hardy (but it worked OK with Intrepid, which was supposedly more temperamental than Hardy) before I removed Intrepid on advice that it was too unreliable or too unstable or too buggy or too something.

Do I really have to just forget about linux and resign to going back and fighting flaky Vista (the devil I don't know too well, but which I learned enough about to dislike), or is it possible to cobble enough flaky linux software together to get a linux system to run? My original motivation to gve VMware a spin was to put XP inside Ubuntu and then shun Vista forever. (I tried for about a week to wipe out Vista and put XP on my machine in its place, but XP doesn't support SATA drives and I was never able to slipstream the SATA drivers into an XP installation disk.

Anyway, I am willing to push this project a little bit further.  At this point I do have a dual-boot Vista/Hardy system in place (Just in case I finally decide I can't make the final jump away from Mr. Gates, I can retreat forever to the Vista side of my system.).  But I haven't managed to accomplish the following goals (which I consider to be modest and necessary):

1. Get dual monitors running on the invidia card.
2. Get USB SoundBlaster audio card to function.
3. Get a virtualization program installed inside Hardy to install XP in.
4. Get Adobe Flashplayer to play Youtube videos.

Am I aiming too high?  If so, then I guess I should immediately go back to Vista  and start reinstalling the ms apps that I wiped out in my earlier attempt to share Hardy and Vista.  (Hardy and Vista now peacefully share a dual-boot system (60 Hardy - 40 Vista, BTW), but I have not re-installed any of my MS apps in Vista.)

If my goals ARE reasonable, can someone tell me specifically what package I should use for virtualization.  All I want is an XP virtual box.  So far I have given up on VMware 2.0 and I have a nonfunctional VMware 1.0.6 in my Hardy OS (created from ubuntu 8.04.2-desktop-amd64.iso).

Following is a regurgitation of my latest vmware install effort.  Should I continue with this vm-install attempt, or should I look under another virtualization rock?  But, don't just tell me to keep trying to get the 'installation' to work.  I'm not yet linux-savvy enough to figure out what I have to do next to correct the deficiency that the log apparently indicates to be the problem.

How do I find pre-built vmmon modules that ARE suitable for my kernel?

What's the mumbo-jumbo about: This program previously created the file /dev/vmmon, and was about to remove it.  Somebody else apparently did it already?

If the following statement is true:
The configuration of VMware Server 1.0.6 build-91891 for Linux for this running kernel completed successfully.

Then why do I later get the statment:

vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command: /usr/bin/vmware-config.pl.

And when I issue the above (re-)configure command, why does it congratulate me again for a successful configuration and then lock up my web browser so that I have to reboot?

----------------------------------------------------
Unsuccessful Installation Log Follows
----------------------------------------------------
jerry@downstairs:~$ sudo /usr/bin/vmware-config.pl
[sudo] password for jerry: 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-23-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport0, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet1, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x86_64.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

Do you want to enter a serial number now? (yes/no/help) [no] yes

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  AAHAE-FF6FJ-U3H0M-405CN

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running kernel completed successfully.
----------------------------------------------

---

### Post by AllanM on 2009-03-17
Firstly, don't be silly - Vista has failed hence Windoze7. On your points :

1. Get dual monitors running on the invidia card - install the (non-free) Nvidia accelerated graphics driver and select using "system/admin/hardware drivers" then use "system/prefs/nvidia x server settings" to get the 2nd monitor working. Have used this and it works fine.
2. Get USB SoundBlaster audio card to function - no idea never tried.
3. Get a virtualization program installed inside Hardy to install XP in - install Sun xVM Virtualbox 2.x using synaptic. Have used this on Hardy and works great with XP (if you really have to access SIMS in a UK school environment like I do).
4. Get Adobe Flashplayer to play Youtube videos - use synaptic to install flash-plugin 10.x. Works fine in FF with all I've tried so far inc. youtube.

Good luck.

---

### Post by JerryI on 2009-03-17
Thanks:

I uninstalled the vmware app that doesn't work and successfully installed VirtualBox (which I haven't used yet). My Hardy installation is 64-bit, which may not be the best choice, but right now I will let sleeping dogs lie.  I have managed to get my dual monitors working.  So two successes in one day is already a record breaker.

---

