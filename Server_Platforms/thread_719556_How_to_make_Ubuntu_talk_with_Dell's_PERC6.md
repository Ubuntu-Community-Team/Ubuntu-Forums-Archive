---
title: "How to make Ubuntu talk with Dell's PERC6?"
date: 2008-03-09
forum: Server Platforms
---

### Post by tomcatf14 on 2008-03-09
I have installed Ubuntu 7.10 AMD64 to a newly acquired Dell PowerEdge 2950 with PERC6 raid card. How can i make Ubuntu to communicate with the PERC card to get the raid status and set notification just like how we can do with "mdadm".

---

### Post by Petersonz on 2008-03-13
See my posts:

[http://ubuntuforums.org/showthread.php?t=721342](http://ubuntuforums.org/showthread.php?t=721342)

and 

[http://ubuntuforums.org/showthread.php?t=722923](http://ubuntuforums.org/showthread.php?t=722923)

You will have reliability problems with the array failing suddenly under heavy I/O or at seemingly random intervals like hours and days.

For the tools, you need to try and get the Dell Openmanage manged Node to install which gives you the RAID tools in command line and web interface. But, since its made for Redhat or Suse, you will have a challenge getting them to install.

I relented and bought Redhat so I could move forward with the projects Im working on. 

Sorry I couldnt be more help.

---

### Post by gtdaqua on 2008-03-19
> **tomcatf14 said:**
> I have installed Ubuntu 7.10 AMD64 to a newly acquired Dell PowerEdge 2950 with PERC6 raid card. How can i make Ubuntu to communicate with the PERC card to get the raid status and set notification just like how we can do with "mdadm".

Ubuntu 7.1 will install smoothly on PERC6 - I have a similar one too. PE 1950 running 7.1 on PERC6.

You can install OMSA on 64-bit Gutsy and monitor cooling fans, temperature etc. To install OMSA you need OpenIPMI and IPMItool

Add this line to your /etc/apt/sources.list

```

deb ftp://ftp.sara.nl/pub/sara-omsa dell sara

```

Then type:
```

sudo apt-get install dellomsa

```

The latest version as of now is 5.3.x. To check if installation was successful, type this:

```

omreport system summary

```

That should give you a summary of your system properties.

After installation start the 'dataeng' services
```

sudo /etc/init.d/dateng enablesnmp
sudo /etc/init.d/dateng start

```

That will enable SNMP and motherboard monitors. 

To enable OMSA Web server:
```

sudo /etc/init.d/dsm_om_connsvc start

```

Then type in a browser https://serverip:1311". That will give you the login page but you wont be able to login! Thats wierd because in 32 bit Gutsy i am able to and it simply wont work in 64 bit Gutsy!!

Optionally, you can enable:

```

sudo /etc/init.d/dsm_om_shrsvc start

```

Here is the command to find out the PERC driver version

```

omreport storage controller

```

EDIT: Pl see my next post (post #5) to get the web console working.

---

### Post by likuidkewl on 2008-03-26
In re: the web interface you need to set a root password.

I used the graphical tool in Hardy and it was fine.
Note: after doing this be sure you create root a home dir in /home as this may error during updates.

Then login as root and the new set password on 
[https://localhosts:1311/](https://localhosts:1311/)

HTH

---

### Post by gtdaqua on 2008-03-27
Addition:

If you want to have the webserver work on 64-bit servers, you should make these changes:

1. Change the "/lib/security" path to "/lib32" in the file "/etc/pam.d/omauth"

2. Copy the below files  from a 32-bit DELL OMSA installed server
```

/lib/libsepol.so.1
/lib/libselinux.so.1
/lib/security/pam_unix.so
/lib/security/pam_nologin.so

```

to "/lib32" of your 64-bit server.

3. Then type

```

sudo ldconfig

```

Now you can logon via "https://ipaddress:1311/"

---

### Post by munwin on 2008-04-09
I tried today to install 8.04 beta server 64-bit on our new 2900 with a PERC6 (radi5 setup). Install seems to work until Grub setup. Then it fails. Even tried LILO - no good, either. After reading other posts, we may have to go with CentOS. I really DO NOT WANT TO, but I need a running server.

Canonical / Dell - THIS IS NOT GOOD ENOUGH. 

Dell - you should supply drivers, especially if you're trying to sell Ubuntu on the desktop. Don't piss off the Sys-Admins, or they won't recommend you.

Canonical - If your trying to cosy up to Dell/IBM/whoever, please try to include updated drivers in the server kernel. We can buy the hardware, but will have to go to another distro to use it.

I like Ubuntu. I use Ubuntu. Now Dell/Ubuntu are forcing me to use something else.

[/rant off]

---

### Post by gtdaqua on 2008-04-10
[rant on]
i agree. The free community gets to suffer the worst. Dell promptly supplies updates for RedHat and SUSE cutting us out on the knees and it claims it supports linux! The DKMS from dell is not a fantastic one either, it still is unreliable. 

As far as Canonical is concerned, storage is one part that has been long neglected and as Petersonz pointed out, the new hardy kernel arrives with the old megaraid_sas driver so which means not much of a way out!

Clearly if sysadmins are not happy, companies shouldnt take credit of what they are doing (or not doing).

[/rant off]

---

### Post by theuni on 2008-04-12
To those having trouble with newer Dell servers and Ubuntu... me too.

I tried every install I could think of including all newer betas, alternates, etc, but no joy. Different issues with each.

But I thought I'd throw it out there that I did manage (very easily) to get Debian Etch x64 running on my Poweredge 2900 w/ SAS 6i and Raid1 no trouble. In fact, the installer works perfectly with no extra fuss.

Hope this helps someone.

TheUni

---

### Post by diegoramos on 2008-05-12
I'm having the same problems. I'll try hard to put OM and update the PERC driver. If I succeed I'll make a HowTo here.


[]'s

Diego

---

### Post by gtdaqua on 2008-05-13
Putting OMSA is very easy. You can get the web console running too. But from where wud u get the drivers and update the kernel? I tried with Dell DKMS and did not work out!

Thanks for writing anyway! It wud be awesome if you managed to install the latest drivers!!

Pl do let us know how it went.

---

### Post by diegoramos on 2008-05-13
I downloaded the megaraid_sas rpm from Dell Website.

Then I used Alien to convert the rpm to .deb and ar to extract the content of the .deb file.

I installed in my system the latest kernel-headers (in my case: 2.6.22-14-server), and used aptitude to install dkms.

After that I opened the scripts that were in the rpm file and i found the 3 DKMS commands that you have to execute:

dkms ldtarball --archive=./megaraid_sas-v00.00.03.16-src.tgz (creates the DKMS tree)

dkms build -m megaraid_sas -v v00.00.03.16  (compile the driver)

dkms install -m megaraid_sas -v v00.00.03.16 (install the driver)

I'm having problems during the build part. It seems like dependency problems but my deadline is near and I'll have to try SuSe instead. As soon I'll finish this server I'll beback to try again.

ps. I also tried to use "DKMS build" showing the paths but didn't word.

dkms build -m megaraid_sas -v v00.00.03.16 -k 2.6.22-14-server --config /boot/config-2.6.22-14-server --arch i686 --kernelsourcedir /lib/modules/2.6.22-14-server/build

---

### Post by gtdaqua on 2008-05-14
I did all that! Didnt work! 

The dirver compiled without any errors and generated a fresh kernel. But after restart, the kernel did not load! I used dkms for compiling. Make sure you use the latest version to compile. It still did not work for me.

Thanks for the update. Pl keep posted on what you do..

---

### Post by gtdaqua on 2008-05-14
actually if you browse deeper, a source (not rpm) of driver itself is published. Compiling straight from there didnt work either! 

Dell simply is happy as long as it works in Red Hat or SUSE. Can't even write and verify a driver that works on a major kernel (ubuntu's) - definitely you cant blame ubuntu for its kernel.

---

### Post by quad3d@work on 2008-05-16
I just installed Hardy AMD64 on PE 2950 with PERC6 HW RAID5(one spare) and SAS bricks
 (15 300GB) on Linux raid+lvm.

Is there a PERC revision preventing it from working?

---

### Post by MianoSM on 2008-05-20
I have successfully installed 8.04 with the 2.6.24-16-server kernel on both a Poweredge 2650, and 1950.

The bios and perc needed to be updated to the very newest versions of firmware, otherwise no issues as of yet. Nothing in my dmesg at all. 

I am really upset about the fact that Dell will not support Ubuntu Server side, and yet pushes it desktop side. RHEL and SuSe are great, however they are not the essence of what Linux is or what it stands for.

I originally went with Linux because it would support larger amounts of RAM out of the box as opposed to going with a MS OS that was $3,000 on top of the server price. 

If there is anything that I can do to aide/influence dell to be more supportive of Ubuntu I'd be interested.

---

### Post by devil1591 on 2008-05-21
> **MianoSM said:**
> I have successfully installed 8.04 with the 2.6.24-16-server kernel on both a Poweredge 2650, and 1950.

The bios and perc needed to be updated to the very newest versions of firmware, otherwise no issues as of yet. Nothing in my dmesg at all.

hi there !

how did you update your PERC firware/driver ?
I thinks everythings fine for me, except the driver part...which gives me a "Degraded" State !

My server : PowerEdge 2950 with PERC 6/i running Ubuntu 8.04 Server

```

[root@serv-linux1 ~]~$ omreport storage controller
 Controller  PERC 6/i Integrated (Embedded)

Controllers
ID                                : 0
Status                            : Non-Critical
Name                              : PERC 6/i Integrated
Slot ID                           : Embedded
State                             : Degraded
Firmware Version                  : 6.0.2-0002
Minimum Required Firmware Version : Not Applicable
Driver Version                    : 00.00.03.10-rc5
Minimum Required Driver Version   : 00.00.03.13
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : 30%
Check Consistency Rate            : 30%
Reconstruct Rate                  : 30%
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : Not Applicable
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : 30%
Patrol Read Iterations            : 0

[root@serv-linux1 ~]~$ omreport storage vdisk controller=0
Virtual Disk 0 on Controller PERC 6/i Integrated (Embedded)

Controller PERC 6/i Integrated (Embedded)
ID                  : 0
Status              : Ok
Name                : Virtual Disk 0
State               : Ready
Progress            : Not Applicable
Layout              : RAID-1
Size                : 278.88 GB (299439751168 bytes)
Device Name         : /dev/sda
Type                : SAS
Read Policy         : No Read Ahead
Write Policy        : Write Back
Cache Policy        : Not Applicable
Stripe Element Size : 64 KB
Disk Cache Policy   : Disabled

```

---

### Post by gtdaqua on 2008-05-22
> 
The bios and perc needed to be updated to the very newest versions of firmware, otherwise no issues as of yet.


Yeah, i would like to know too. Did you upgrade the drivers for linux? If so, then congrats! And we would appreciate (actually desperate) if you could tell us how you did that..

See, the drive could play up occassionally, especially during very huge read/writes.

---

### Post by ha2432003 on 2008-06-04
Has anyone made any progress on this?

I have a Poweredge 1950 with a perc 6/i controller.  Everything seems fine, except for omreport giving a 'degraded' state on the raid controller (though every other indicator is that raid is working fine).

I've made some attempts to update the megaraid_sas driver with no success - the system doesn't come up on reboot (can't find the drives).

---

### Post by gtdaqua on 2008-06-05
so you are the one who posted in dell forums too. hope u have seen my reply there.

in a nutshell, dell is not bothered. They basically mean to to tell us to suck up and wait until someone else finds a solution.

---

### Post by Cody@unifocus on 2008-07-17
I did a search and found an entry from the dell archives.
[http://lists.us.dell.com/pipermail/linux-poweredge/2008-April.txt.gz](http://lists.us.dell.com/pipermail/linux-poweredge/2008-April.txt.gz)
-------------------------------------------------------------
 What I ended up doing was pulling the RH3 archive for the 8480E card
(not that it seems to really matter as the tarball inside the archive
looks to have the patches for all the supported versions of Linux in it)
from LSI's site, uncompressing that file and then uncompressing the
megaraid_sas-v00.00.03.13.tgz file.

I added these lines to the Makefile (per
[http://www.captain.at/programming/kernel-2.6):](http://www.captain.at/programming/kernel-2.6):)

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

Ran make and received a clean compile for megaraid_sas.ko.  Backed up
the old megaraid_sas module, added the new module, rebuilt the initrd
image, rebooted cleanly.
---------------------------------------------------------------

I downloaded the driver from LSI [http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN](http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN)
got the megaraid_sas-v00.00.03.13-src.tgz and extracted it on the server.  
Followed the instructions above and from this point I didn't know what to do.  
I looked at some of my old notes from getting the perc5 to work on dapper and tried that.  
I copied the megaraid_sas.ko file to /lib/modules/2.6.24-16-server/kernel/drivers/scsi/megaraid.  
I then ran “echo megaraid_sas >> /etc/mkinitramfs/modules” and then 
"mkinitramfs -o /boot/initrd.img-2.6.24-16-server 2.6.24-16-server" 
rebooted and the driver loaded.  The speed of disk access has drastically improved while under load.
I am a newbie and curious if this was the correct way to do this or if their is a better way.

---

### Post by gtdaqua on 2008-07-17
> **Cody@unifocus said:**
> I did a search and found an entry from the dell archives.
[http://lists.us.dell.com/pipermail/linux-poweredge/2008-April.txt.gz](http://lists.us.dell.com/pipermail/linux-poweredge/2008-April.txt.gz)
-------------------------------------------------------------
 What I ended up doing was pulling the RH3 archive for the 8480E card
(not that it seems to really matter as the tarball inside the archive
looks to have the patches for all the supported versions of Linux in it)
from LSI's site, uncompressing that file and then uncompressing the
megaraid_sas-v00.00.03.13.tgz file.

I added these lines to the Makefile (per
[http://www.captain.at/programming/kernel-2.6):](http://www.captain.at/programming/kernel-2.6):)

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

Ran make and received a clean compile for megaraid_sas.ko.  Backed up
the old megaraid_sas module, added the new module, rebuilt the initrd
image, rebooted cleanly.
---------------------------------------------------------------

I downloaded the driver from LSI [http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN](http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN)
got the megaraid_sas-v00.00.03.13-src.tgz and extracted it on the server.  
Followed the instructions above and from this point I didn't know what to do.  
I looked at some of my old notes from getting the perc5 to work on dapper and tried that.  
I copied the megaraid_sas.ko file to /lib/modules/2.6.24-16-server/kernel/drivers/scsi/megaraid.  
I then ran “echo megaraid_sas >> /etc/mkinitramfs/modules” and then 
"mkinitramfs -o /boot/initrd.img-2.6.24-16-server 2.6.24-16-server" 
rebooted and the driver loaded.  The speed of disk access has drastically improved while under load.
I am a newbie and curious if this was the correct way to do this or if their is a better way.

Thats amazing and a wonderful job you've done! And, umm, you are not a newbie! Could you post the exact command for the KDIR and PWD format that you typed. I will try to compile today on my 1950 and see what happens.

A walkthrough would be one of the most important posts in the internet. Well done, Cody@unifocus!

---

### Post by Cody@unifocus on 2008-07-18
I replied to gtdaqua but have not heard anything from him.  This was my reply in case anybody wants to try this.
> 
 Here is what i put in the Makefile. The only thing i changed was the obj-m. I double checked the KDIR path and it seams OK. It would be
/lib/modules/2.6.24-16-server/build
which is a sym link to
/usr/src/linux-headers-2.6.24-16-server/

I am confused by the shell but I think it needs to be there by searching other makefiles.

obj-m := megaraid_sas.o

KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

Here is my oemreport

Controller PERC 6/i Integrated (Embedded)

Controllers
ID : 0
Status : Ok
Name : PERC 6/i Integrated
Slot ID : Embedded
State : Ready
Firmware Version : 6.0.2-0002
Minimum Required Firmware Version : Not Applicable
Driver Version : 00.00.03.13
Minimum Required Driver Version : Not Applicable
Number of Connectors : 2
Rebuild Rate : 30%
BGI Rate : 30%
Check Consistency Rate : 30%
Reconstruct Rate : 30%
Alarm State : Not Applicable
Cluster Mode : Not Applicable
SCSI Initiator ID : Not Applicable
Cache Memory Size : 256 MB
Patrol Read Mode : Auto
Patrol Read State : Active
Patrol Read Rate : 30%
Patrol Read Iterations : 2

This is a VMware box with 4 VM's. After I installed the driver the speed seemed normal, but now it is back to being slow, but not as slow as before. The numbers look good on hdparm but it takes longer than it should to complete (about a minute). I am no longer getting disk read errors on my vm's but it still seems slow.

/dev/sda:
Timing cached reads: 4996 MB in 2.00 seconds = 2500.60 MB/sec
Timing buffered disk reads: 24 MB in 4.75 seconds = 5.06 MB/sec

Give it a try and if it works give it a few days to see if the performance changes. It seams that if I only run one vm it is OK, but the more vm's I run the slower the response time is. I also see the sluggishness on the host OS not just the VM's.

After reviewing the reply I noticed that the buffered reads are pretty slow.  After a reboot they are faster but not as fast as I think they should be.  Before the driver upgrade the speed was in the KB's.

---

### Post by gtdaqua on 2008-07-19
thanks for your email. i think i have to give up. 'make' command does not run succesfully. it returns:
```

make
: Nothing to be done for `default'

```

How did you run make and make install? what were the files present?
this is all I have:
```

dkms.conf  megaraid_sas.c  patches
Makefile   megaraid_sas.h  redhat_driver_disk

```

---

### Post by Cody@unifocus on 2008-07-21
I wonder if you need some additional packages to compile it.  The only thing I can think of is build essential and linux headers.  I have to have these to build vmmon for vmware. 

```

sudo apt-get install build-essential linux-headers-`uname -r` 

```

---

### Post by Cody@unifocus on 2008-07-21
ok your Makefile must be perfect for this to run.  I was able to recreate your error because thier was not a space before the last line.  Copy and paste this into your Makefile and it will run.
```

obj-m   := megaraid_sas.o

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```

---

### Post by gtdaqua on 2008-07-21
> **Cody@unifocus said:**
> ok your Makefile must be perfect for this to run.  I was able to recreate your error because thier was not a space before the last line.  Copy and paste this into your Makefile and it will run.
```

obj-m   := megaraid_sas.o

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```

Nope, still doesnt work! Its the same result. And I have build-essential and the headers already. VMWare is already setup on this PE1950 server.

---

### Post by gtdaqua on 2008-07-22
ok wait, i got the "make" successfully - NEVER COPY PASTE THE MAKEFILE CONTENT FROM ELSEWHERE. ADD A TAB BEFORE THE LAST LINE "MANUALLY". THANKS, [BHASKIE]("http://lwn.net/Articles/21817/")

I have some additional files on the folder now - let me continue the experiment and revert.

---

### Post by gtdaqua on 2008-07-22
Success!! Megaraid_sas Driver has been succesfully upgraded. Cody, YOU ARE A GENIUS. DELL, KISS CODY'S FEET.

I did everything as Cody said except the "echo" command. This has worked. No more DKMS horsesh#t. 
```

 Controller  PERC 5/i Integrated (Embedded)

Controllers
ID                                : 0
Status                            : Non-Critical
Name                              : PERC 5/i Integrated
Slot ID                           : Embedded
State                             : Degraded
Firmware Version                  : 5.1.1-0040
Minimum Required Firmware Version : 5.2.1-0060
**Driver Version                    : 00.00.03.16**
Minimum Required Driver Version   : Not Applicable
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : 30%
Check Consistency Rate            : 30%
Reconstruct Rate                  : 30%
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : Not Applicable
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : 30%
Patrol Read Iterations            : 50

```

But the firmware version is out of date and so the state is still 'degraded'. But this is a breakthrough nevertheless.

---

### Post by Cody@unifocus on 2008-07-22
gtdaqua,
Glad to see you got it installed.  I do have a question.  Your driver is
version 03.16 and I have 3.13.  Where did you get that from?  I can't find
it on LSI's site.  Also I just upgraded my Firmware on my perc.  I Downloaded 
the newest redhat one from dell at
[http://ftp.us.dell.com/SAS-RAID/RAID_FRMW_LX_R189149.BIN](http://ftp.us.dell.com/SAS-RAID/RAID_FRMW_LX_R189149.BIN) 
then downloaded omsa live 5.4 at 
[http://linux.dell.com/files/openmanage-contributions/omsa-54-live/](http://linux.dell.com/files/openmanage-contributions/omsa-54-live/)
and installed it.  worked like a champ.  For anybody that is having I/O issues 
on the 6/i with a RAID 1 or 10 this Firmware update is supposed to address it.  
I will test to see

---

### Post by noirtim on 2008-07-22
Thanks everyone for your help. Special thanks to Dell Gold support. I just want to quickly outline the process for updating the PERC 6/i firmware and the linux megaraid_sas driver. The following worked for me on a 32-bit PE1950 install using Ubuntu server 8.04.1.

**Firmware update:**
Download the firmware (RAID_FRMW_LX_R189149.BIN) from [http://support.dell.com](http://support.dell.com)

Download and write to CD the CentOS-based live CD from dell to perform the firmware upgrade:
[http://linux.dell.com/files/openmanage-contributions/omsa-54-live/omsa-54-040308.iso](http://linux.dell.com/files/openmanage-contributions/omsa-54-live/omsa-54-040308.iso)

Once booted, transfer the 'RAID_FRMW_LX_R189149.BIN' file to your working directory and run:
```

sh RAID_FRMW_LX_R189149.BIN

```

Firmware update complete!
But observe that the results of
```

omreport storage controller

```
Shows the controller in a degraded state. Read on to upgrade the Linux driver.

**Linux Megaraid_SAS driver update:**
Now that you are booted into Ubuntu 8.04.1, download the source:
[http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN](http://www.lsi.com/cm/License.do?url=/support/downloads/megaraid/sas/hardware_drivers/linux/RH3-U4_3.13-1.zip&prodName=MegaRAID%20SAS%208480E&subType=Driver&locale=EN)
Unzip, untar, and decend into the driver directory for 'megaraid_sas-v00.00.03.13-src.tgz'. Alter the 'Makefile' to mirror the following (be sure to tab the last line manually):
```

obj-m   := megaraid_sas.o

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules


```

Run the following:
```

make
make install

```

Next you must add the module to your existing kernel:
```

cp megaraid_sas.ko /lib/modules/2.6.24-19-server/kernel/drivers/scsi/megaraid

```

Now make the boot image:
```

mkinitramfs -o /boot/initrd.img-2.6.24-19-server 2.6.24-19-server

```

Reboot. After running the controller report with 'omreport storage controller'

Observe a non-degraded RAID configuration:
```

#omreport storage controller

 Controller  PERC 6/i Integrated (Embedded)

Controllers
ID                                : 0
Status                            : Ok
Name                              : PERC 6/i Integrated
Slot ID                           : Embedded
State                             : Ready
Firmware Version                  : 6.0.3-0002
Minimum Required Firmware Version : Not Applicable
Driver Version                    : 00.00.03.16 
Minimum Required Driver Version   : Not Applicable
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : 30%
Check Consistency Rate            : 30%
Reconstruct Rate                  : 30%
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : Not Applicable
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : 30%
Patrol Read Iterations            : 2

# omreport storage vdisk controller=0
Virtual Disk 0 on Controller PERC 6/i Integrated (Embedded)

Controller PERC 6/i Integrated (Embedded)
ID                  : 0
Status              : Ok
Name                : EREBOR-RAID1
State               : Ready
Progress            : Not Applicable
Layout              : RAID-1
Size                : 136.13 GB (146163105792 bytes)
Device Name         : /dev/sda
Type                : SAS
Read Policy         : No Read Ahead
Write Policy        : Write Back
Cache Policy        : Not Applicable
Stripe Element Size : 64 KB
Disk Cache Policy   : Disabled


```

LVM seems to work fine:
```

# df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/LVroot-part--root
              ext3    7.5G  1.2G  6.0G  16% /
varrun       tmpfs   1012M   56K 1011M   1% /var/run
varlock      tmpfs   1012M     0 1012M   0% /var/lock
udev         tmpfs   1012M   52K 1011M   1% /dev
devshm       tmpfs   1012M     0 1012M   0% /dev/shm
/dev/sda1     ext3     46M   24M   20M  55% /boot
/dev/mapper/LVhome-part--home
               xfs    125G   21M  125G   1% /home


```

Thanks to Cody@unifocus, gtdaqua, devil1591, Dell Gold support, and everyone else!

---

### Post by gtdaqua on 2008-07-22
> **Cody@unifocus said:**
> gtdaqua,
Glad to see you got it installed.  I do have a question.  Your driver is
version 03.16 and I have 3.13.  Where did you get that from?  I can't find
it on LSI's site.  Also I just upgraded my Firmware on my perc.  I Downloaded 
the newest redhat one from dell at
[http://ftp.us.dell.com/SAS-RAID/RAID_FRMW_LX_R189149.BIN](http://ftp.us.dell.com/SAS-RAID/RAID_FRMW_LX_R189149.BIN) 
then downloaded omsa live 5.4 at 
[http://linux.dell.com/files/openmanage-contributions/omsa-54-live/](http://linux.dell.com/files/openmanage-contributions/omsa-54-live/)
and installed it.  worked like a champ.  For anybody that is having I/O issues 
on the 6/i with a RAID 1 or 10 this Firmware update is supposed to address it.  
I will test to see

Firmware upgrade is very easy even for a noob. Make a Win98 Boot CD, transfer the firmware exe file to the CD. Boot and run the exe file and you're done. All files must DOS-compatible. No Long filenames are allowed.

Goto dell website and choose the server model and select RHEL Enterprise 5 version and choose Perc5i/6i _driver_. You will see tgz format of the megaraid_sas file. Untar and you will find the source package as another tgz file. Then follow your own instructions and you will get it!

Savvy??
:)

---

### Post by gtdaqua on 2008-07-22
> **noirtim said:**
> Thanks everyone for your help. Special thanks to Dell Gold support.........
......



It was the same Dell Gold Support that turned its back on me when I raised the issue and said a driver for Ubuntu or debian linux is not available and "no one" has compiled it from source to have it work on other linux flavours. Only RHEL and SUSE are extensively supported. That was one real 'gold' support experience I had.

---

### Post by gtdaqua on 2008-07-22
I flashed the firmware update too - you can do this with almost any OS. After flashing, my server looks good now. I took OMSA 5.4 64-bit package from the sara.nl guys (which btw is a remarkable achievement by someone outside dell doing this) and here is the output of omreport storage controller:

```

 Controller  PERC 5/i Integrated (Embedded)

Controllers
ID                                : 0
Status                            : Ok
Name                              : PERC 5/i Integrated
Slot ID                           : Embedded
**State                             : Ready**
*Firmware Version                  : 5.2.1-0067*
Minimum Required Firmware Version : Not Applicable
*Driver Version                    : 00.00.03.16*
Minimum Required Driver Version   : Not Applicable
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : 30%
Check Consistency Rate            : 30%
Reconstruct Rate                  : 30%
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : Not Applicable
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : 30%
Patrol Read Iterations            : 50

```

---

