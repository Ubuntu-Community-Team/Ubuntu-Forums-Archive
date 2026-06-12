---
title: "Installation Experience on Sparc"
date: 2010-03-24
forum: Server Platforms
---

### Post by lnelson on 2010-03-24
I have spent the last couple weeks playing with Ubuntu on some old Sparc Netras our company had laying around.  I was trying to install 9.10 (Karmic).  The process was frustrating for me so I thought I could share my experiences and possibly lessen the frustrations of others.  I have a sort of howto posted on my company's Wiki:

[http://ops.3rivers.net/wiki/index.php/Ubuntu_on_Sparc](http://ops.3rivers.net/wiki/index.php/Ubuntu_on_Sparc)

I was also a newbie to Sparc hardware, so some of my frustration came from the platform rather than from the installation.

Here are some highlights (that weren't high points in my life):

[LIST]
[*]Learning how to boot from CD
[*]The install CD died during the boot at SILO with the error "fast data access mmu miss"
[*]The installation process died during the SILO install.
[*]Kernel panic in 9.10 (Karmic)
[/LIST]
Here are the lessons learned from the above points of frustration:

[LIST]
[*]Booting from CD-ROM
[LIST]
[*]from the openboot "ok" prompt, "boot cdrom" almost always works.  The Wiki entry referenced above gives some suggestions
[/LIST]
 
[*]"fast data access mmu miss"
[LIST]
[*]From my experience, this occurs with all boot CD's for Ubuntu versions higher than 8.04 (Hardy).  It seems that the initrd file is too large.  The best method to get to a newer version of Ubuntu is to start with Hardy and then upgrade through each version from there.
[/LIST]
 
[*]SILO Installation
[LIST]
[*]The install process stalls during the SILO installation in Hardy.  My experience was seeing a blue or black screen (depending on the intelligence of my terminal emulator) with a blinking cursor in the lower left.  What is happening is that SILO is prompting for user input in the background but there is no way to interact with it.  Pressing ctrl-C aborts the SILO installation and continues with the install process.  It will complain a couple times about SILO or the boot loader not being installed.  The easiest work around is to choose the menu option to execute and shell and run "/target/sbin/silo -r /target" at the command prompt.  After this you can finish the installation normally.
[/LIST]
 
[*]Kernel Panic in Karmic
[LIST]
[*]There is a problem with the version of "upstart" in Karmic that causes a kernel panic in Karmic.  The best solution seems to be to stay at 9.04.  Perhaps future releases will have this fixed.  There is a bug posted at: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/436758](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/436758)
[/LIST]
 
[/LIST]
At this point I have 9.04 (Jaunty) running on a Netra 120 and a Netra 210.

---

### Post by lnelson on 2010-03-24
Here is the text of the Wiki article I mentioned in the original post:

**Booting from CDROM**

 If the system is already booting into SILO, you will need to either send a "[break]("http://ops.3rivers.net/wiki/index.php/Break_on_Sparc")" during the boot (I never got that to work on a Netra 120 but it did work on a 210) or enter "halt" from the SILO prompt to get to OpenBoot. Once at the OpenBoot "ok" prompt, you should be able to enter "boot cdrom". If this fails, then you will have to specify the cdrom device. This can be found by doing a "show-devs" and scanning the list for a device (or devices) that say "cdrom". You will then need to enter the full, cryptic-looking device name at the boot prompt, such as: 
 ok boot /pci@1f,0/pci@1,1/ide@d/cdrom
[B]
Picking a Version[/B]

 **Netra 120 and 210**

 Anything higher than 8.04.1 (Hardy Heron) fails to initiate the install with a "fast data access mmu miss" error (see [http://www.backports.ubuntuforums.org/showthread.php?t=1409144](http://www.backports.ubuntuforums.org/showthread.php?t=1409144)).  The failure seems to be because the initrd file is too large. 
 [B]
Other[/B]

 No other Sparc hardware has been tested yet. 
 [B]
Installing 8.04.1 (Hardy Heron)[/B]

 8.04.1 installs from CD, but fails during the SILO boot loader installation, which is nearly the last step of the install ([https://bugs.launchpad.net/ubuntu/+source/silo-installer/+bug/194032](https://bugs.launchpad.net/ubuntu/+source/silo-installer/+bug/194032)). After installing and configuring the optional packages (OpenSSH, LAMP, Mail Server, etc), the system will seem to hang on a blank screen with flashing cursor. Type ctrl-C to abort the silo installation script. (What is happening is that silo is prompting for user input but there is no way to interact with it.) The install process will ask you a couple times if you really want to skip the silo install, then it will dump you into a menu of what to do next. 
At this point, there are two options: 
 [B]
Execute a shell to install silo[/B]

 One of the menu options is to execute a shell. This is the quickest way to run silo manually. Once in the shell, the installed filesystem is mounted under "/target". Passing the argument "-r /target" to silo causes it to chroot to "/target" where it will find all files in their expected locations: 
 /target/sbin/silo -r /target
Enter "exit" to return to the isntallation menu. At this point, select "Finish the installation" and once again convince the installation process that you truly do want to continue without installing the boot loader (it doesn't know that you already did). 
 [B]
Install silo from rescue mode[/B]

 You need to select "Finish the installation" to continue. 
A (not so) nice "feature" of the Ubuntu install is that it ejects the CD after before rebooting after the install process. Since we need to boot from the same CD into rescue mode, you have to push the CD tray back in. 
To boot into rescue mode, boot from the CD, and from the SILO screen, enter "rescue". Go through all the options, just like during an install. If you used the default partition layout during the install, then tell rescue to mount /dev/sda2 on /. Then select the option to execute a shell in / (/dev/sda2). /etc/silo.conf is a symlink to /boot/silo.conf, so we need to mount the boot partition then execute silo: 
 rescue# mount /dev/sda1 /boot
rescue# silo -f
/etc/silo.conf appears to be valid
Type "exit" to leave the shell and go back into the rescue menus.  From the menu reboot the system. 
 [B]
Update 8.04.1 (Hardy Heron)[/B]

 Before upgrading to new releases, the system must have the latest packages for 8.04.1. 
 user@server:~$ sudo apt-get update
.
.
.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct 
user@server:~$ sudo dpkg --configure -a                                        
Setting up silo (1.4.13a+git20070930-1ubuntu1) ...                              
SILO, the Sparc Improved LOader, sets up your system to boot Linux              
directly from your hard disk, without the need for a boot floppy or a net       
boot.                                                                           
                                                                                
You already have a SILO configuration in the file /boot/silo.conf               
Install a boot block using your current SILO configuration? [Yes] n             
                                                                                
Wipe out your old SILO configuration and make a new one? [No]                   
No changes made.                                                                
                                                                                
user@server:~$ sudo apt-get update
.
.
.
Reading package lists... Done
user@server:~$ sudo apt-get dist-upgrade
.
.
.
Need to get 118MB of archives.                                                  
After this operation, 66.4MB of additional disk space will be used.             
Do you want to continue [Y/n]? y
.
.
.
Reboot the system. 
 [B]
Upgrading[/B]

 The system must be updated through each major release.  Skipping releases will fail. 
 [B]
Upgrade from 8.04.1(Hardy Heron) to 8.10 (Intrepid Ibex)[/B]

 First become root then update apt-get and install the package "update-manager-core" (just in case): 
 user@server:~$ sudo su
root@server:/home/user# apt-get update
.
.
.
Reading package lists... Done
root@server:/home/user# apt-get install update-manager-core                    
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
update-manager-core is already the newest version.                              
The following packages were automatically installed and are no longer required: 
  libdns32 libisc32                                                             
Use 'apt-get autoremove' to remove them.                                        
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                  
Open the file /etc/update-manager/release-upgrades... 
 root@server:/home/user# vi /etc/update-manager/release-upgrades
... and change **Prompt=lts** to **Prompt=normal**: 
 [...]
Prompt=normal
Then run the upgrade. There may be questions about updating locally changed files. These might relate to network configuration (such as dhcp), dovecot and release-upgrades. Opting not to install the newer version should be OK. There may also be prompts to restart services. Since no critical services should be running yet on the system, it is OK to restart them. 
 root@server:/home/user# do-release-upgrade
.
.
.
Do you want to start the upgrade?                                               
                                                                                
                                                                                
1 package is going to be removed. 100 new packages are going to be              
installed. 248 packages are going to be upgraded.                               
                                                                                
You have to download a total of 184M. This download will take about 1           
minute with your connection.                                                    
                                                                                
Fetching and installing the upgrade can take several hours. Once the            
download has finished, the process cannot be cancelled.                         
                                                                                
 Continue [yN]  Details [d]y
.
.
.
Remove obsolete packages?                                                       
                                                                                
                                                                                
16 packages are going to be removed.                                            
                                                                                
 Continue [yN]  Details [d]y
.
.
.
System upgrade is complete.                                                     
                                                                                
Restart required                                                                
                                                                                
To finish the upgrade, a restart is required.                                   
If you select 'y' the system will be restarted.                                 
                                                                                
Continue [yN] y
After the reboot, your system is running Ubuntu 8.10 (Intrepid Ibex). 
 [B]
Upgrade from 8.10 (Intrepid Ibex) to 9.04 (Jaunty Jackalope)[/B]

 This process in identical to the upgrade from 8.04.1 to 8.10. 
Follow the steps for "Upgrade from 8.04.1 to 8.10".  The only differences will be in the output from the process. 
After the reboot, your system is running Ubuntu 9.04 (Jaunty Jackalope). 
 [B]
9.10 (Karmic Koala) not compatible with Sparc[/B]

 There is a broken package in 9.10 (Karmic Koala) that will cause a kernel panic and make the system unbootable: 
 Preparing to replace upstart 0.3.9-8 (using .../upstart_0.6.3-11_sparc.deb) ...
Unpacking replacement upstart ...
Processing triggers for man-db ...
Setting up upstart (0.6.3-11) ...
[  596.907361] Kernel panic - not syncing: Attempted to kill init!
[  596.907361] Kernel panic - not syncing: Attempted to kill init!
[  597.090555] Press Stop-A (L1-A) to return to the boot prom
[  597.090555] Press Stop-A (L1-A) to return to the boot prom
More information can be found at [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/436758](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/436758) 

As of 3/09/10 in that thread, there is no fix intended for release 9.10. 

In short, 9.10 (Karmic Koala) will not work on Sparc.  As of 3/17/10 release 9.04 is the highest available release for Sparc.

---

### Post by Dalton7182 on 2010-03-26
I can not Thank You enough for sharing this information with us. A million Thank You's. I also am new to UltraSparc architecture and have aquired an old sun enterprise 420r. I have been determined to install Hardy Heron on it and have spent a significant amount of time researching UltraSparc, OpenBoot, and Ubuntu for Sparc 8.04 Server. I was very pleased to start the installation process, however I ran into what I thought was a hang up after installing packages and the installation stated that it was "cleaning up". I have been scouring the forums and search engines for any clue how to resolve this to no avail and by luck I finally stumbled across this thread. My wife will be grateful that I will no longer be walking aroud looking like a twenty-six year old zombie who has deprived himself of sleep in favor of spending these last few nights trying to resolve this issue. Thanks again, Rich.

---

### Post by lnelson on 2010-03-26
I'm glad I could be of help for once to someone.  I've felt guilty for years for always mooching off of forums but never providing anything of my own.  With just a couple hundred more of these, I might actually pay my debt to society.

---

### Post by zeroseven02 on 2010-05-15
I'm trying to install ubuntu over a serial line to a Netra T1 105.  My only option would be text mode, however, textmode shows up with corrupted characters.  I was wondering if you had any experience with this, do I need to set different rates or something.  The Netra serial port is only 9600 baud.. I have that set correctly... not sure what the deal is here, and for the life of me I can't search the forums nor google effectively to find an answer here..

---

### Post by lnelson on 2010-05-15
I once plugged into an Ethernet port instead of the serial port and got garbage (obviously), but otherwise I have not seen what you describe.

---

### Post by zeroseven02 on 2010-05-18
It wasn't an ethernet port.  I have a cisco rollover cable connected to serial A on my netra t1, the opposite end plugs into an RJ45 to DB9 converter and from there a DB9 to USB converter so I can run the serial connection to my Macbook Pro.

Opening a Term I execute:

```
$ screen /dev/tty.usbserial 9600
```

leaving me at the lom> of the Netra.  This is where the fun starts.  I can poweron, get to the open boot promt and boot cdrom.  However, after it runs through it's initialization, the textmode install screen comes across corrupted.  I know it's trying to force the colored text mode through, I can see the blue and gray menus and background, I just can't read what they contain.  I was just wondering if you've experienced something like this before, or is there a vt100 serial option for install?

---

### Post by thebigob on 2010-06-03
Another thank you very much post. Though I have not tried this yet looks to be the business and explains a lot of the same problems I encountered.

Thank you so much to the poster

---

### Post by roddo1966 on 2010-08-21
Very informative post - thank you!

Explains why Dapper (server-only for sparc) was the only Ubuntu version that would successfully install on my Ultra Enterprise 2. I really wanted a desktop though, so I tried a few other distro's. Fedora couldn't find the network card and Gentoo was promising but a bit involved. Even OpenSolaris sparc install is complicated.

Then I tried Debian and realised that's where I should have started. Not just a sparc version, but server and easy network install of Gnome, KDE or Xfce desktops.  And it installed without incident. And it's the latest version. And it boots and runs beautifully. Amazed that a fifteen year old machine (even if it does have twin 300MHz processors and 2 Gig of RAM) can run a Linux desktop that is no slower to use than my usual (recent) x86 hardware.

All credit to Debian, and I recommend anyone wanting to install something useful on this kind of equipment to give it a shot!

---

### Post by timji on 2010-10-31
Thanks for your helpful How-To on getting modern Ubuntu distros up and running on SPARC hardware! My only regret is that I did not find it earlier; as things worked out, I spent a very frustrating week replicating all the problems you identified! 

So today, I'm following your advice in the hope of getting my Ultra 10 to run 9.04 soon. I've bumped into one oddity already, however. Apparently you were able to upgrade from Hardy to Intrepid, but AFAIK there isn't a SPARC port for Intrepid (judging from its absence on the servers I checked). So I upgraded by replacing all occurrences of "hardy" in my sources.list with "jaunty", which seems to do the trick.

---

### Post by TheHesser on 2012-12-13
Thanks lnelson! This walkthrough is just what I needed.
I was wondering if you know what the problem could be with my install.

I installed Ubuntu 8.04 Hardy Heron and then came to the screen where the installation hangs. Then I did exactly as you said and did an rescue. The check goes okay and when I reboot it keeps saying that Drive not ready - Can't open boot device
I don't get the Silo loader or anything else. (it was installed before when I got it by another person)

I tried boot disk1, disk2, scsi but it doesn't load.
setenv boot-device = disk1
setenv auto-boot? = true

Do you know what I need to do next?
This is my first cup of Ubuntu for Sparc and I am addicted.

Thanks for your input!

---

### Post by Hendrik_van_Dijk on 2013-08-28
I have found the initial problem:
It should have been boot disk
So "setenv boot-device disk" works.

But after following the upgrade from 8.04 to 8.10 my server hangs at the following:

Boot device: disk  File and args:
SILO Version 1.4.14
boot:
Allocated 64 Megs of memory at 0x40000000 for kernel
Uncompressing image...
Loaded kernel version 2.6.32
Loading initial ramdisk (8461366 bytes at 0x28000000 phys, 0x40C00000 virt)...
\

Can anyone help my with what could be the problem. I installed the server 3 times and followed the whole manual in this thread to the letter. All three times my server hangs at this stage of booting.

---

### Post by TheHesser on 2014-02-25
[COLOR=#000000]I have found the initial problem:[/COLOR]
[COLOR=#000000]It should have been boot disk[/COLOR]
[COLOR=#000000]So "setenv boot-device disk" works.[/COLOR]

[COLOR=#000000]But after following the upgrade from 8.04 to 8.10 my server hangs at the following:[/COLOR]

[COLOR=#000000]Boot device: disk File and args:[/COLOR]
[COLOR=#000000]SILO Version 1.4.14[/COLOR]
[COLOR=#000000]boot:[/COLOR]
[COLOR=#000000]Allocated 64 Megs of memory at 0x40000000 for kernel[/COLOR]
[COLOR=#000000]Uncompressing image...[/COLOR]
[COLOR=#000000]Loaded kernel version 2.6.32[/COLOR]
[COLOR=#000000]Loading initial ramdisk (8461366 bytes at 0x28000000 phys, 0x40C00000 virt)...[/COLOR]
[COLOR=#000000]\[/COLOR]

[COLOR=#000000]Can anyone help my with what could be the problem. I installed the server 3 times and followed the whole manual in this thread to the letter. All three times my server hangs at this stage of booting.[/COLOR]

---

### Post by tgalati4 on 2014-02-25
I would review the changes between 8.04 and 8.10 and see what changed in the kernel versions.  It's possible that there is a bug in the 8.10 kernel and your CPU.  So now you would search the net for that kernel version and bugs filed against the Sparc architecture.

Since both distros are quite old, why did you need to go from 8.04 to 8.10?  Did you consider a jump from 8.04 to 10.04, since I believe there is a direct LTS upgrade option.  Of course there is probably a very, very small chance that 10.04 would work out of the box.

How old is the machine?  Any date stamps on the hardware?  How many watts of power does it use?  For a 24/7 server this can become an issue.

---

