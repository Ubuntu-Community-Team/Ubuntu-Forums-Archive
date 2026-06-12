---
title: "Upgrade my OBP to enable install."
date: 2006-06-20
forum: Sun Sparc Users
---

### Post by chris_andrew on 2006-06-20
Hi, all.

I am unable to install Dapper on my Ultra 10,  because the OBP doesn't support the install.  Can anybody tell me how to upgrade my crrent OBP?  I should mention that I don't have any Solaris disks.

Many thanks,

Chris.

---

### Post by gavinj44 on 2006-06-20
What error do you get from the install ?

---

### Post by chris_andrew on 2006-06-20
Hi,

The start of the post was here:

[http://www.ubuntuforums.org/showthread.php?t=198497](http://www.ubuntuforums.org/showthread.php?t=198497)

I moved it when the Sparc sub-forum opened.

Thanks,

Chris.

---

### Post by netztier on 2006-06-21
[QUOTE=chris_andrew]I am unable to install Dapper on my Ultra 10,  because the OBP doesn't support the install.  Can anybody tell me how to upgrade my crrent OBP?  I should mention that I don't have any Solaris disks.
[/QUOTE]

I've never upgraded an OBP myself, but googling for *Sun Ultra 10 OBP Upgrade* yields this [Document on sunsolve.sun.com]("http://sunsolve.sun.com/search/advsearch.do?collection=PATCH&type=collections&queryKey5=106121&toDocument=yes"). 

Basically, you put the file into the root directory of your harddisk, mark it executable and tell the system to boot from it at the "ok"-prompt. I am not quite sure how the PROM will react to the root partition having a linux file system (probably ext3), but i think that you'll just have to try.

Maybe adding a new boot option to silo to boot the "flash-update kernel" instead of the linux-kernel might help. I think I'll try this myself on the Ultra 5 at home. If anything else fails, downloading and installing a minimal version of Solaris might be a good idea after all.


kind regards

Marc

---

### Post by chris_andrew on 2006-06-21
Marc,

Sounds straight forward, with exception of the possible ext2/3 fs problem.  I'd be keen to hear how you got on with your Ultra 5.

Thanks for taking the time to reply.

Chris.

---

### Post by netztier on 2006-06-21
[QUOTE=chris_andrew]
Sounds straight forward, with exception of the possible ext2/3 fs problem.  [/QUOTE]

Browsing through the forums at [www.sonnenblen.de](www.sonnenblen.de) (German SUN hardware oriented forum) it seems that having a Solaris file system is a must. Since U10is an IDE based system, a bit of disk-swapping and installing an minimal solaris to some old small disk might provide you with a basis to work from.

The only other alternatives are network-boot (just as with Linux's boot.img) or a bootable CD-ROM. That's an interesting concept, but needs some special tools to fiddle with, but it might work best in the end.

We'll see...

kind regards

Marc

---

### Post by chris_andrew on 2006-06-21
Hmmm,

Doesn't sound very encouraging.  Net-booting seems like a pain, and I don't really want to mess with the network settings on my main box.  It might be back to Sarge, unless the development guys can sort the bug that I reported for SILO.  The silly thing is, the CD boots (see original post [http://www.ubuntuforums.org/showthread.php?t=198497](http://www.ubuntuforums.org/showthread.php?t=198497)
) so no problem there, it just gets stuck!!

Cheers,

Chris.

---

### Post by netztier on 2006-06-21
[QUOTE=chris_andrew]The silly thing is, the CD boots (see original post [http://www.ubuntuforums.org/showthread.php?t=198497](http://www.ubuntuforums.org/showthread.php?t=198497)) so no problem there, it just gets stuck!!
[/QUOTE]

Well, copying the flash-update image to /dev/hda1 doesn't work. It is found when invoked by the **boot disk /<flashupdate-filename>** OpenPROM command, but then:

```
Rebooting with command: boot disk /flashupdate
Boot device: /pci@1f,0/pci@1,1/ide@/disk@0,0 File and args: /flashupdate
SILO Version 1.4.10

Allocated 8 Megs of memory at 0x40000000 for kernel
/
Fatal error: Multiple loadable segments in your ELF image
Program terminated
ok
```


I also tried to burn a sparc-bootable CD with xcdroast and using the flash-update image as boot image, but when it would start to boot, it considered the file given to boot from as "not executable" and stopped. Bad luck then, or I might have missed some special option in xcdroast.

Hm. I wonder... if I had read up about solaris/linux parallel installations and multibooting I might have found out how to make SILO boot a Solaris installation - which might just have worked for the flash-update image too.

Well I didn't, so in the end, I opened the box, threw in a 10Gig IDE disk from the "I might need these one day" box, did a minimal install of Solaris 8, ftp'ed the flash-image from my file server and the rest was done in 5 minutes and I have OpenBoot 3.31 now.

So my suggestion is: get a copy of Solaris installation media, do a minimal install (maybe on a spare disk), bring the flash-update image to it's root partition and update the OBP. Requires a bit of screwdriver work, but will eventually succeed.

kind regards

Marc

---

### Post by chris_andrew on 2006-06-21
Marc,

Thanks for your good work.  I guess I'll have to see whether I can download Solaris from somewhere, and preferably not "Agree" to any licencing clause, that is non-free.  I guess it needs to be done.  Anybody know a URL?

Cheers,

Chris.

---

### Post by netztier on 2006-06-22
[QUOTE=chris_andrew]
and preferably not "Agree" to any licencing clause, that is non-free.  I guess it needs to be done.  Anybody know a URL?
[/QUOTE]

If you don't like the "classic" Solaris, why not try one of the OpenSolaris distros?

[http://www.opensolaris.org/os/about/distributions/]("http://www.opensolaris.org/os/about/distributions/")

Maybe Nexenta's "Debian with SunOS kernel" will work or [Solaris Express ]("http://www.sun.com/software/solaris/solaris-express/get.jsp")(link at the bottom of the page) is "free for non-commercial use" - grab your .iso image and have a go at it! :-)

kind regards

Marc

---

### Post by chris_andrew on 2006-06-22
Downloading Solaris Express.

---

### Post by sheen_austin on 2006-06-23
Hey Chris,
Were u able to do the flash upgrade?
I have been having the exact symptoms with my Ultra 10 but trying to do the flash upgrade has opened up a pandoras box.
I keep getting "Memory Address not Aligned" when I try to boot with command - "boot disk /flash-update-Ultra510-latest"
I tried googling the error and it seems like im the only one on the planet whos ever got this problem.

Regards,
Sheen.

---

### Post by chris_andrew on 2006-06-23
Hi,

To be honest, I gave up.  I filed a bug report, and am now installing Gentoo....not easy, but at least if it fails it is not a computer fault, it is my stupidity :-)

Cheers,

Chris.

---

### Post by chris_andrew on 2006-06-30
Anybody know whether the OBP problem will be ironed-out in the next 'point' release?

Cheers,

Chris.

By-the-way, my OBP *.version* is 3.15.2

---

### Post by netztier on 2006-07-03
[QUOTE=chris_andrew]Anybody know whether the OBP problem will be ironed-out in the next 'point' release?
[/QUOTE]

No clue there - but I keep stumbling across forum posts with trouble reports form U10 users.

btw - I sent you a private forum message - did it get through?

kind regards

Marc

---

### Post by chris_andrew on 2006-07-03
Marc,

Got your message.  Definetly like to try to upgrade the OBP.  Has this worked for anybody, or does it just cause different problems?

Thanks,

Chris.

---

### Post by chris_andrew on 2006-07-05
Hi, all.

I have upgraded my OBP to 3.31.  Unfortunately, I still have exactly the same problem.  In fairness to Sun, the upgrade was a 1 minute job.  If only PC BIOS were that easy.

Cheers,

Chris.

---

### Post by recupero on 2006-07-23
I went through many of your same conclusion for this problem:
but I am one step ahead....

OpenSolaris, right?...

Now all the disks I have I have been playing with Linux, so none of the original Sun Disk Labels is left.
Opensolaris finds no disks upon install, neither it's able to format.
Making up a Sun Disk Label on Linux (=whole disk partition) with the s command on fdisk is no help.

How can it be that the Linux-made Sun-Disk-Label is different from the OpenSolaris counterpart and
How can I completely erase the data of a disk (maybe then OpenSolaris works from the start...)
I am stuck here.

---

### Post by recupero on 2006-07-27
Chris, you who did.
Could you tell us the OS (solaris express) you used to build /flash-update.
If so, was the disk you worked on with a Sun Label or could the OS-installation format it?

---

### Post by chris_andrew on 2006-07-28
I found an ISO that boots straight from the PROM, and the update ran from that, no OS required.

Cheers,

Chris.

---

### Post by recupero on 2006-07-28
**[SIZE="6"]link ?[/SIZE]**=P~
[SIZE="2"](what you googled for?)[/SIZE]

---

### Post by chris_andrew on 2006-07-28
I have a small ISO.  Don't think it is available on the web.  I would pass it to you, but I'm not sure of Sun's view of this.  As it is just a patch, and not a proper software release, I'm guessing that they would be supportive, but as I say, i'm not sure.

Thanks,

Chris.

---

### Post by recupero on 2006-07-29
I bought a brand new HDD.
It also happens I work for a division making HDD controllers (Italian), but I pay for my disks...
Solaris Express worked, and also the OBP/POST upgrade  !!!

So my new 440MHz sparcIIi booted.

---

### Post by allnameswereout on 2006-07-29
Out of curiousity has anyone here used one of those Open Solaris clones together with flash-update? If such exist in live-cd format, would be even better.

---

### Post by chris_andrew on 2006-07-30
Why not just use the flash upgrade ISO, that Sun produce?  It runs from the CD and is OS independent.

Chris.

---

### Post by allnameswereout on 2006-07-31
Ah nice I did not know such existed. Do you have a URL?

---

### Post by chris_andrew on 2006-08-01
No URL, just got the ISO kicking around, here.

---

### Post by Delta_Farce on 2006-08-05
If you can't get hold of a flash ISO you can upgrade your firmware like this:

1) Zero the hard disk (get rid of existing Linux and BSD partitions)
2) Boot into OBP and install Solaris (use the ok boot cdrom -s command for single user mode)
3) At the prompt use format -e /dev/rdsk/c0t0d0s0 (for ide drives - not sure what scsi is called)
4) Set the drive type and you should be ok to install Solaris
5) Upgrade OBP using instructions from Sun

This is a long winded method, but it does work (I used it on a Sunblade 150). As others have mentioned the flash updates don't seem to work with BSD/Linux file systems.

Cheers,

Mark

---

### Post by allnameswereout on 2006-08-06
Since OBP can do netboot it should be able to download that flash binary and get the thing working as well. The flash utility is then loaded in RAM and running. Makes no difference regarding stability.

Otherwise, boot Solaris/SPARC installer, get a prompt, get networking, copy the flash thingy over, start the damn thing and off you go.

So its not really big deal.

---

### Post by chort on 2006-11-29
I found this thread via Google and was determined not to take the Solaris-on-another-disk cop-out, so I figured out how to net boot the PROM flash file.  It actually wasn't that difficult to figure out, thanks to the great man pages on OpenBSD.  Here's your answer:

[net boot your way to a new PROM]("http://www.smtps.net/netboot_flash_obp.html")

---

### Post by recupero on 2006-12-03
I executed the OBP as reported by Chris on a SunBlade1000.
Many thanks!!!

---

### Post by recupero on 2006-12-03
I executed the OBP as reported by Chris on a SunBlade1000.

**Many thanks!!!**:eek:

---

### Post by kingcharles1666 on 2008-01-03
Hi,
I just managed to flash my Ultra10 using the net boot method and because I used a Linux (Ubuntu with x64 bit) machine to host the boot image, the steps were a little different than the[ FreeBSD link]("http://www.smtps.net/netboot_flash_obp.html") referenced before.
So I decided to write it down for others to benefit and as a reminder for myself in case I need to do it again :-)

Here are all the steps (most copy paste from the referenced link):

1) Get the PROM flash update from[ sunsolve.sun.com]("http://sunsolve.sun.com/").

2) Get the MAC address of your primary NIC on the SPARC box. You can get this from the "ok prompt" by typing .enet-addr. Or look at the splash at boot up (press STOP-A)

3) Power-off the SPARC box and set the jumper to allow the PROM to be flashed (jp2 on Ultra 5/10 machines).

4) Unzip the flash update and copy the appropriate file to /var/lib/tftpboot on the Ubuntu machine you will be net-booting from

5) On my machine /etc/inetd.conf was already configured correctly to use the location as per step 4.
Check the file to see if it has:
*tftp		dgram	udp	wait	root	/usr/sbin/tcpd	/usr/sbin/in.tftpd -s /var/lib/tftpboot*

6) Decide what IP address you want to give your SPARC box. Put the **IP and hostname** in /etc/hosts in the normal fashion.

7) Put the** MAC address** (from step 2) **and hostname** in /etc/ethers (hostname is the one you put in  /etc/hosts).
This 'ethers' file does not exist yet so will need to create it yourself.

8) Convert the IP address you put in /etc/hosts for your SPARC box to HEX:

HEXIP=```
echo 207.200.74.2 | awk -F . '{ printf "%02X%02X%02X%02X\n", $1, $2, $3, $4 }
```(replace 207.200.74.2 with the IP address you selected in step 6)

9) Create a simlink from the image to the HEX IP address:
```
 cd /var/lib/tftpboot
```
```
 ln flash-update-Ultra510-latest =HEXIP
```  (replace =HEXIP with the result of step 8)

10) Now start rarpd with root privilege. This does not come installed by default in Ubuntu so you have to install it first. Use command line or synaptic to install it whatever you prefer.
```
sudo rarpd -ad
```

11) Now power your SPARC back on and send it a break (STOP-A) before it starts booting a kernel.  At the ok prompt, type:
```
boot net
```

If you did things right you will see a byte-counter in the upper left corner like:
265e00

this will continue to count up until it has downloaded the entire flash file.  When it is done it will execute automatically.

* When you get:

       Firmware Release(s)                Firmware Release(s)                   
 Currently Existing in the System      Available for Installation  /  Install?  

--------------------------------- -------------------------------------------  
OBP 3.11.9 1998/03/06 10:31        OBP 3.31.0 2001/07/25 20:36          no      
POST 2.2.9 1998/02/19 17:54        POST 3.1.0 2000/06/27 13:56          no      
                                                                                
Type sa if you wish to select all available firmware releases for               
installation.  Type h for help, quit to exit, or cont to continue:

go with: sa, then cont, then [enter]

* If everything goes well, you should see:

Erasing the top half of the Flash PROM.                                         
Programming OBP into the top half of the Flash PROM.                            
Verifying OBP in the top half of the Flash PROM.                                
                                                                                
Erasing the bottom half of the Flash PROM.                                      
Programming OBP into the bottom half of Flash PROM.                             
Verifying OBP in the bottom half of the Flash PROM.                             
                                                                                
Erasing the top half of the Flash PROM.                                         
Programming POST into the top half of Flash PROM.                               
Verifying POST in the top half of the Flash PROM.                               
                                                                                
Programming was successful.                                                     
                                                                                
Resetting ...


If the Net boot part does not work try installing xinetd.
After installing xinetd put the below line as the bottom line in the file /etc/xinetd.conf
```
includedir /etc/xinetd.d

```
check to see if the inetd.conf file is still referring to /var/lib/tftpboot

and retry the boot net command.

Have fun!

---

