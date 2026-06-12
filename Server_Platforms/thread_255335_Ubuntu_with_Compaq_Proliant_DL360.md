---
title: "Ubuntu with Compaq Proliant DL360"
date: 2006-09-11
forum: Server Platforms
---

### Post by phantomxxinc on 2006-09-11
Hello this is my first post and i have been having a major issue with figuring something out.  I am installing a Ubuntu 6.06 install on my old Compaq Proliant DL360.  It is set up in a Raid 1.  It uses the Compaq SmartArray to set this Raid up.  But when i install it installs says it completes the installation but then acts like the hard drive was not recognized.  I have booted into a live cd and found the partion in c0d0p1 for the raid, but it is not mounting an booting on startup.  The errors i am getting are:

cpqarray: error sending ID controller
MP-BIOS bug: 8254 timer not connected to IO-APIC
/bin/sh: can't access tty; job control turned off

Is there anyway to set the raid up with a different tool.  It seems to me that it has something to do with the raid controller and the Compaq SmartArray.

Thanks in advance.

---

### Post by ihavenoideax2 on 2006-09-17
Perfect timeing. Getting a DL360 off ebay next week. Please if anyone knows how to fix let us know.

---

### Post by khansen46 on 2006-09-21
I am having the same issue with Xandros (also Debian-based). It appears this is a Kernel bug.Here is a link to some good documentation on it:
[http://www.mail-archive.com/debian-kernel@lists.debian.org/msg19788.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg19788.html)
If you read through the entire thread, there is some good information. I, personally, am not technical enough with Linux to be able to implement the fix. However, there are a lot of people working on it. I'm anxious for it to be completely resolved, as I have 6 Proliants waiting for an OS...

Ken

---

### Post by ihavenoideax2 on 2006-09-22
I can’t wait eather, Even though I have been using Linux for quite a while, I still don’t know how to do anything kernel wise (compile, install drivers, etc...). I just hope it gets done soon. I should be getting the server today. So when I try to set it up tomorrow when I have time, ill give you a follow up.

---

### Post by ihavenoideax2 on 2006-09-23
I found this tonight.
[http://www.mcnabbs.org/andrew/linux/proliant/]("http://www.mcnabbs.org/andrew/linux/proliant/")

---

### Post by bzsparks on 2006-09-27
I am having a similar problem trying to install on a Proliant ML370 G1.  This box has the Compaq Integrated SmartArray.  In the article that you posted a link to it said that booting from a LiveCd with a 2.4 Kernel solved the problem of the cpqarray module not finding the array properly.  I do not know of an Ubuntu Live CD that has a 2.4 kernel, is there one available?

---

### Post by ihavenoideax2 on 2006-09-27
You might just need to try an old debian or knoppix bootable live cd. I forgot what ver of knoppix had 2.4 kernel. Havent used that in a long time. Ill try to find it for you.

---

### Post by ihavenoideax2 on 2006-09-27
[http://ftp.ntua.gr/pub/linux/clusterknoppix/clusterKNOPPIX_V3.6-2004-08-16-EN-cl1.iso]("http://ftp.ntua.gr/pub/linux/clusterknoppix/clusterKNOPPIX_V3.6-2004-08-16-EN-cl1.iso")

Found this. Uses 2.4.27 kernel. Should Help.

---

### Post by stakk on 2006-09-28
Just try to append no-apic to you kernel line in the grub configution (menu.lst). 
That made my old ML350 G2 boot.

---

### Post by plettpc on 2006-10-31
Ok; I solved this prob, just follow vjshah's post #82466
It works a treat for 6.06 ,, PM me if u need help.

Basically install system:: reboot from cd :choose rescue : go through the motions untill it errors and puts u back into the menu.
select scroll down select shell: make dir /target.mount /dev/ida/c0d0p1 /target(be sure on initial setup which partition is your / part ie: P1 P2 etc.
chroot into /target
edit using vi as nano gives a error. just add cpqarray into the file./etc/mkinitrdfs/modules
run /usr/sbin/mkinitrdfs -o etc as stated(make sure u specify correct kernel version): cd to /boot
mv initrd.img-2.6.15......... to initrdold.img
mv initrd.img(new one we just made) initrd.img-2.6.15........
exit reboot without cd and it'll run perfectly.

Note: the correction in file:step 5 /etc/mkinitrdfs/modules
I'm still open for ideas to get 6.10 working same prob but no mkinitrdfs found yet.

---

### Post by plettpc on 2006-10-31
6.10 working too file is now /etc/initramfs-tools/modules
6.06                         /etc/mkinitramfs/modules

This works on all Compaq dl360 -dl380 servers with Compaq smart array.

---

### Post by scubanator87 on 2006-11-03
I was having the same problem here at work. Tried Several different install settings and mess with the smartstart cd 

for hours and couldn't figure it out. i finally found this post and adjusted it for my Edgy install: Here is what i 

did:

Booted from Install cd and chose Repair.

Go through the same start of the set up till error. 

after error a list of options will be available, scroll down and select "Start a Shell"

Make a folder to mount your install
$ mkdir /target

Now mount it for access (my partition defaulted to c0d0p1)
$ mount /dev/ida/<your partition goes here> 

now chroot
$ chroot /target

Now us vi/vim to edit the modules file to have the array boot on start. first make a back up!
$ cp ./etc/initframsfs-tools/modules ./etc/initframsfs-tools/modules_backup
$ vi ./etc/initframsfs-tools/modules

Once in vi, unless you have the commands memorized, you'll need a cheat sheet like me. i had to print it out to keep 

from running back to my desk over and over.how ever, you'll only need a few commands and i can help with that.

after you open its in command mode so do the following
hit j till your at the bottom of the document. 
hit o to open a new line after the current. 
type "cpqarray" and hit enter. this is the module for raid array
hit ZZ to save and exit

If your read the comments in the modules file, you notice that to update the list you need to run update-initramfs 

to update the init file. you need to run the -u option to update the list. 
$ update-initramfs -u 

Now all you have to do is reboot! yay your system now works. :-)

---

### Post by ihavenoideax2 on 2006-11-07
If only i can get my server to run. I think my server is over heating. Soon i have to fix that. I hope i can.

---

### Post by bzsparks on 2006-11-13
Until the kernel is updated to fix the issue I used a quick fix to get things up and running.  Using the edgy server install disk (or expert install with the desktop disk) go through all the steps as normal. 

After the base install has finished type <alt><f2> to enter a console.  Then rename /lib/modules/2.6.17-10-server/kernel/drivers/scsi/sym53c88xx_2/sym53c8cc.ko to sym53c8xx.ko.bak.  Type <alt><f1> to get back to the install.  

Once installation has completed the system will boot.  You can now leave the offending module renamed so it won't load or rename it back to its original name then blacklist the module, both ways accomplish the same goal the blacklist method is just a little more clean.

---

### Post by Worelock on 2006-11-18
Hello,
I can confirm that the instructions given in this post do work on 6.10. The system will then boot, however it is VERY slow. It takes some time once once you time in the username to logon before you actually get the password prompt.

I am runnin 6.10 on a DL360 spec'd with the following
Dual P3 933 Coppermine CPU's
1 gig PC133 Ram
1 x 36Gig Ultra3 HDD
1 x 76Gig Ultra3 HDD
ATI Video (onboard)
Dual Intel Nic's

It should be anything but slow, and it has me puzzled as to why it is.
Is there something I am missing with a tweak on the scsi driver or something like it? If anyone else ha seen this problem I would be interested to hear what you did to fix it.

Cheers

---

### Post by Worelock on 2006-11-18
Uhoh....
It looks like this might have actually been a hardware problem.

Non Fatal Error on c0d0 <----- that cant be good.
I replaced the 36gig disk with another one I had here and the system now seems to be running like a ferari!

---

### Post by fellz on 2006-12-26
hi!

i need to run a livecd to resize one of the ext3 partitions on our proliant dl370. does anyone know how to make the *livecd* find the compaq smart array 5i controller?

that'd be really great :-)

---

### Post by fellz on 2007-01-03
sorry, can anyone delete this message?

---

### Post by fellz on 2007-01-03
I couldn't find a Linux LiveCD that worked with the SmartArray 5i Controller. So if anyone has the same problem:

I finally purchased Acronis Disk Director Suite 10 and successfully moved and resized my ext3 partitions.

---

### Post by 5ketcher on 2007-01-12
Hi,

can somebody tell me how to build a raid on this machine? Is there a tool from Compaq?

Thanks in advance, Jan

---

### Post by fellz on 2007-01-12
hi,

while there are several possibilities the probably easiest one might be to use the SmartStart CD from Compaq/HP. DiskImages for the SmartStart CD can be found at hp.com. I've heard that only SmartStart v5.5 can handle the DL360. So you might need to get the "old" v5(.5).

When booting from the SmartStart CD you will be able to use the Array Configuration Program to create/modify your RAID array. It has an easy to use GUI.

---

### Post by fellz on 2007-01-12
here's the [link to the "old" SmartStart CD 5.5]("http://h18023.www1.hp.com/support/files/server/us/download/22678.html?jumpid=reg_R1002_USEN")

---

### Post by 5ketcher on 2007-01-17
thanks, I created a raid 0 with it. How do I format it now? I can not find the device. It is not /dev/sd... and not /dev/rd/... I do have something like /dev/ida/cd... but I can't fdisk it.

any suggestions?

---

### Post by fellz on 2007-01-17
i suggest you install gparted (if it's not already installed ?) - it has a nice GUI and should show you all partitions. you can then create/format your partition easily.

if you want to do it the hard way - here's what the partitions are namend on our DL 370 wit a smart array 5i:
/dev/cciss/c0d0p5     /
/dev/cciss/c0d0p1     /boot
/dev/cciss/c0d0p6     /usr/termapp
/dev/cciss/c0d0p7     /usr/appdata

---

### Post by 5ketcher on 2007-01-18
I might have a different firmware. On my machine the name of the device is /dev/ida/c0d0. I still have the same problem like before.
Correct me if I'm wrong. First I have to create the partitions (The Ubuntu installer doesn't see the device at all and gparted is not on the Ubuntu CD. Fdisk doesn't work ether).
Any Idea?

Thx, Jan

---

### Post by fellz on 2007-01-18
basically ubuntu's installer should create the partitions for you.
but it looks like you ran into the same problem as all the other guys in this thread. but if so i'm wondering that the installer does see the drive.

the normal procedure should be:

1. create your raid array (with the smart start CD)
2. start the ubuntu installer (using the ubuntu CD)
all the partitioning and formatting should then be done by/with the installer.

if you ran into the driver problem (the installer does not see any drives) you might try that:
> **bzsparks said:**
> Until the kernel is updated to fix the issue I used a quick fix to get things up and running.  Using the edgy server install disk (or expert install with the desktop disk) go through all the steps as normal. 

After the base install has finished type <alt><f2> to enter a console.  Then rename /lib/modules/2.6.17-10-server/kernel/drivers/scsi/sym53c88xx_2/sym53c8cc.ko to sym53c8xx.ko.bak.  Type <alt><f1> to get back to the install.  

Once installation has completed the system will boot.  You can now leave the offending module renamed so it won't load or rename it back to its original name then blacklist the module, both ways accomplish the same goal the blacklist method is just a little more clean.

but it sounds like you don't get that far?
where do you end up exactly?

---

### Post by 5ketcher on 2007-01-18
> 1. create your raid array (with the smart start CD)
That's what I did. I tried it with Ubuntu 6.06 and 6.10. Do you use the "server" or "desktop" version of Ubuntu. Is there anything special in the kernel?

---

### Post by fellz on 2007-01-18
as far as i know there's no difference in the desktop/server kernel.
i'm running ubuntu both as a server and as a desktop - but our compaq dl370 is running on redhat only...

---

### Post by fellz on 2007-01-18
it seems to be a tough problem. i recommend asking your question at [www.linuxquestions.org]("http://www.linuxquestions.org") . maybe they can help.

---

### Post by NigO on 2007-01-24
> **5ketcher said:**
> That's what I did. I tried it with Ubuntu 6.06 and 6.10. Do you use the "server" or "desktop" version of Ubuntu. Is there anything special in the kernel?

We've just completed an install on a proliant DL380, the install page where partitions are assigned to mount points failed, it wouldn't list any partitions, even though they were set up on the previous page.

I let it use the entire drive, so it produced a 140GB root partition and 12GB swap, then booted off the live CD after the installation was complete and used gparted to repartition the drive as I wanted it.

After that, cp -av to copy the var and tmp directories to their own partitions, mv to shift the existing dirs to oldvar and oldtmp in case it didn't work(!), edit /etc/fstab to give it the new mount points, and it all went ok on the next boot.

---

### Post by moneymonk on 2007-02-13
hey, Scubanator!!!

I followed your steps and got this far:

>Booted from Install cd and chose Repair.
>
>Go through the same start of the set up till error.
>
>after error a list of options will be available, scroll down and select "Start a Shell"
>
>
>Make a folder to mount your install
>$ mkdir /target
>
>Now mount it for access (my partition defaulted to c0d0p1) 
>$ mount /dev/ida/<my device>
/*Note: i think that my device was c0d0p5, and the mount appeared to work*/
>
>now chroot
>$ chroot /target

I then receive the error:

sh3.1#: chroot: cannot run command '/bin/sh': No such file or directory

I'm a total newbie, so I apologize if I'm ignorant.  Please help me get this beast running.

The Monk

---

### Post by cfgtech on 2007-03-29
when your Machine boots up hit F8 the rest is self explanatory
create a logical drive select your drives and save

---

### Post by maeltor on 2007-05-09
Has anyone had a problem related to this where Ubuntu (either 6 or 7) Server can't detect the geometry of the array?

---

### Post by astra2000 on 2007-05-29
> **maeltor said:**
> Has anyone had a problem related to this where Ubuntu (either 6 or 7) Server can't detect the geometry of the array?


i have the same problem:(

[http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360](http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360)

---

### Post by jaydeel on 2007-06-01
I'm having the same issue... with a Compaq Prolinea ML370 with Smart Array Controller

Once installer gets to partitioning, i get the message.
Unable to determine drive geometry/size. 

The raid disk shows up in the list, but the size shows 0G0.

/dev/ida/c0d0 exists, but no partitions are visible. ie c0d0p1, etc.

and fdisk /dev/ida/c0d0 isn't able to open the drive either.

Anyone else run up against this? is the option to downgrade to edgy?

I did a dmesg, and found errors identical to the post found below...

> For all 2.6 kernels before 2.6.18 (released Sep 20, 2006), there was a problem with the RAID driver in Linux. The error messages look like: "cpqarray: Finding drives on ida0", "cpqarray: ida0: idaSendPciCmd Timeout out, No command List address returned.", "cpqarray: error sending ID Controller", etc. It turns out that the RAID device would be taken by another driver (sym53c8xx) before the cpqarray driver could claim it.

What confuses me now is that the feisty server kernel is 2.6.20, shouldn't this be fixed? I know an issue regarding initrd has been reported to the bug list, but those are all cases where the install worked fine, but the initial boot did not. In my case I can't even get the drives partitioned. Does anyone know if this issue has been officially bug-reported?

Related threads...

[http://ubuntuforums.org/showthread.php?t=424425]("http://ubuntuforums.org/showthread.php?t=424425")
[http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360]("http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360")

---

### Post by shodan7 on 2007-12-23
This might be a bit off topic but someone may be able to help me.

My Compaq ProLiant DL360 (Generation 1) worked great for a long time running Ubuntu.  I hadn't turned it on in a few months and now when I do Processor 1 initializes 000/133mhz with 00 kilobyte cache.  Processor 2 initializes correctly at 1ghz/133mhz with 256 kilobyte cache.  I have the newest firmware and I have tried reseting the BIOS.  What could be wrong?  Did my processor go bad?

---

### Post by jaydeel on 2008-01-14
I recently had to install on this box again and wanted to use 7.10 (Gutsy) when I did... and thought about making the custom install cd, which should probably still work but I thought it was a lot of work... since it was a module conflict I wondered if I could just suppress loading the module somehow... 

Then i discovered a couple interesting kernel module parameters... that makes installing on this raid controller a breeze...  so.. upon booting press F6 to edit the kernel parameters and I added... this to the line... > sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes

Detected the array and everything worked like a charm.. even copies over your blacklist settings to the new installation. Hopefully the need for a custom install cd should be obsolete. 

Definately see this thread... 

[http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360]("http://ubuntuforums.org/showthread.php?t=384319&highlight=dl360")

---

### Post by silocade on 2008-01-20
Jaydeel ROCKS !!! Works like a charm.... For anyone else who is having this problem, go witht Jaydeel's Solution 

--------------------------------------------------------------------------------

I recently had to install on this box again and wanted to use 7.10 (Gutsy) when I did... and thought about making the custom install cd, which should probably still work but I thought it was a lot of work... since it was a module conflict I wondered if I could just suppress loading the module somehow... 

Then i discovered a couple interesting kernel module parameters... that makes installing on this raid controller a breeze... so.. upon booting press F6 to edit the kernel parameters and I added... this to the line... 
Quote:

sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes  

Detected the array and everything worked like a charm.. even copies over your blacklist settings to the new installation. Hopefully the need for a custom install cd should be obsolete. 

Definately see this thread...

---

### Post by adamos on 2008-04-10
I also verify this. sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes does the work for 7.10 I installed it on 6 proliant DL360 already

---

### Post by Deathrend on 2008-04-10
I use both an ML370 G2, and a DL580 G2, both oof which load 7.10, and 8.04 without a hitch (Other than the 580 not wanting to boot from CD's.

Did you guys use the smart array CD to set up the SmartArray, or did you use the Bios?  In all my time spent around HP servers, I've never seen much good come from the controller bios setups.  I juse use the SmartArray CD to set up the raid, and then set them up as though they're going to be used for windows server (Instead of Linux).  This does it for me

The ML370 Loads both 1.26 Ghz PIII's without a hitch, as well as the 6x36Gb RAID 5 set by the SmartArray.

The DL580 Loads all four 2.4ghz Xeons (HT) without a hitch.  To me, it sounds like your processor is either bad, or your VRam isn't seated properly.  The OS shouldn't effect the processor in any way, more so if it doesn't load properly on the POST.

As for the Kernel fix, I've never had that problem, the ML370 sees ~180Gb hard drive (The 6x36Gb Raid 5), and the DL580 sees ~440 (4x147Gb).

Other than the SmartStart CD, I don't think I did anything out of the norm for these.  I have stacks of them that we've recieved with our newer servers, so I don't think much of it.  I think you can download them from HP's webpage however, but they're fairly hard to find without help.

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=344318&prodTypeId=18964&prodSeriesId=345557&swLang=8&taskId=135&swEnvOID=4022](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=344318&prodTypeId=18964&prodSeriesId=345557&swLang=8&taskId=135&swEnvOID=4022)

Just set up the array with it, and format it for Windows.  I didn't use the CD to install the OS however (It loads the OS, instead of the OS installing from the CD, this is nice, however it's not made for Ubuntu).  I just started the servers up with the Ubuntu CD in it after the array is set, let the set up do the rest.  Another note, about half way through the set up, it looks like it hangs.. just give it time, it will finish.

Hope this helps.

---

### Post by stanz on 2008-04-10
I'm happy to see action on this old thread!!
I'm at a tech school attempting to {trying to}get a couple of their old Compaq's running.
Right now the ol' Proliant ML370 spiting out a couple of years of dust ~ while booting. 

All your info is a great help!! And that link too!!

---

### Post by Deathrend on 2008-04-10
When I first started dealing with HP servers, it took me so freeking long to find that, I really couldn't figure out why I couldn't edit the RAID array.  Some of the HP ML serius servers doesn't even have a ROM-Bios for setup, they only work via the CD, which becomes even more of a pain.  

I love HP servers, however, they run very well, even the old ones.  I have two I use for personal useage (Both servers my company planned to recycle).

ML370 G2
Ubuntu Server 8.04
2x 1.26 Ghz PIII Processors
4Gb ECC SDRAM
6x36GB SCSI
4x10/100/1000 Ports (2x Duel port cards)

DL380 G2
Ubuntu Server 8.04
4x 2.4 Ghz P4 Xeon (HT, looks like 8x 2.4ghz)
16Gb ECC DDR RAM
4x146GB SCSI
2x10/100/1000 (Single Dule Port)
External eSATA Array, housing 12x750GB Hard Drives on 2xRAID5 Arrays.

Both of which scream with Ubuntu Server

---

