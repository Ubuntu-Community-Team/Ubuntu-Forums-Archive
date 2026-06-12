---
title: "SILO fails to install"
date: 2006-06-20
forum: Sun Sparc Users
---

### Post by gavinj44 on 2006-06-20
Hi There, 

I am trying to install Ubuntu on a Sun Ultra 10, all seems to go well until the part where SILO is written to the disk, this step fails ... 

>    [!!] Install the SILO boot loader on a hard disk 

The 'silo' package failed to install into /target/.  Installing SILO  
as a boot loader is a required step.  The install problem might       
however be unrelated to SILO, so continuing the installation may be   
possible.                                                             

SILO installation failed.  Continue anyway?                

<Go Back>                                       <Yes>    <No>



You can continue the install but obviously cannot boot the installation when complete.

Any advice ?

Regards,
Gavin Jones

---

### Post by gavinj44 on 2006-06-21
Hi There, 

I managed to get silo working by using apt-get install silo (by starting a root shell from the rescue CD) and setting up silo.conf by hand.

It now boots off the disk but can't find the kernel when I look in /boot it doesn't appear to be installed e.g. no symlink for vmlinuz in / ?

Has anyone else got this to work on an Ultra 10 ?

Not sure if this makes a difference but I am installing using a serial console.

Regards,
Gavin

---

### Post by gavinj44 on 2006-06-24
I take it that others out there have managed to get this working on Sun Ultra 10's ?

Everytime I attempt to install from the CD I have burnt it fails on the installing SILO step.

Any ideas ? I'd really like to get the Ultra 10 up and running as a server, it has run Debian fine in the past with SILO working fine, that to was installed over a serial console.

Regards,
Gavin Jones

---

### Post by rooihond on 2006-06-25
Hi,

I also had the Silo install part fail on me. As a matter of fact I couldn't get any of the CD ISOs to boot - MMU Miss error.

So I was doing Netboot installs. I just downloaded the latest boot.img file and did a tftpboot and installed 100% without any errors with rgds to the Silo part. 6.06 is now running happily on my Blade 2000,2X36GB, 2X900Mhz,PGX32,OBP4.16.4

SMP kernel is installed and working.

Now looking at the LAMP setup ....

rgds
Derek

---

### Post by allnameswereout on 2006-06-29
Its a known issue, noted in the release notes.

I had the problem too sometimes, but after a few CDROM boots managed to succeed.

---

### Post by rcotten on 2006-08-08
So did anyone find the final answer to this?

I am having the same issue with a U10.  my silo.conf looks like:

Partition=1
root=/dev/hda1
timeout=50
image=/vmlinuz
label=linux



No matter where I look I can't find the vmlinuz link... so I know that is an issue.  I can boot to rescue cd and get shell access with no issues but from eprom boot disk0:a gets me the "not an executable file" message.

Best regards,

Ray

---

### Post by allnameswereout on 2006-08-15
If you don't have that vmlinuz link then do ls -l /boot/vmlinuz* and see if /boot/vmlinuz symlink exists and works and change your silo.conf appropriately.

Example of my silo.conf

[i]root=/dev/hda1
partition=1
default=Linux
read-only
timeout=50
append="quiet splash"

[b]image=/boot/vmlinuz
        label=Linux
        initrd=/boot/initrd.img

image=/boot/vmlinuz.old
        label=LinuxOLD
        initrd=/boot/initrd.img.old[/b][/i]

---

### Post by claudiomet on 2006-09-27
The partition where is the kernel bootable image must be an ext2, ext3 or hfs  filesystem... reiserfs or other filesystem is not supported by silo.

In my case I have a first 100Mb partition with ext3 filesystem with mountpoint /boot and my next partitions (/ and /home) are reiserfs ...and of course, the swap.

---

