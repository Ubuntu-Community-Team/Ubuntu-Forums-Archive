---
title: "Server Setup"
date: 2012-06-25
forum: Server Platforms
---

### Post by ajf412 on 2012-06-25
Brand new to server stuff, so don't think I understand much of anything.  I can build PCs, but this is a whole other beast it seems.

I'm trying to set up a server in my home to run version control software to update my development team's software.  I don't think Tortoise SVN works on Ubuntu?  So I'm aiming for Bazaar, Apache, or CVN.  Whatever works.

Server:  HP Proliant ML350 G4p
2x 146 GB SCSI drives in RAID 1+0
HP Smart Array 641 Controller
Ubuntu 12.04 64 bit

I got non-free firmware "tigon/tg3_tso5.bin" on a USB stick.
I install Ubuntu to be a LAMP Server (I think that's correct?)
I install the non-free firmware when it asks, and it seems to install just fine.

After everything is installed, I take the CD out, let the program restart the server, and boot up.  It goes through the checks just fine, and then checks floppy, CD, USB, and then hard drive to boot.

Then the screen goes black and says:

Cannot Display This Video Mode
Optimum resolution 1280x1024 60Hz

I have a 2006 DELL flat screen.  It's not widescreen.

Now I am stuck.  Please... help!

Local computer shop here wants $175 an hour, and estimates it to be 5 hours to install Ubuntu.  =\  I can't afford that!

---

### Post by ajf412 on 2012-06-25
The same thing happens when I hold down SHIFT to load GRUB.  It says, "Loading GRUB" and then gives me the message that it cannot display this video mode.

---

### Post by darkod on 2012-06-25
Can you boot it successfully with the live cd in live mode (Try Ubuntu)?

If you can, boot it and let us know. You should have internet access in live mode.

---

### Post by ajf412 on 2012-06-25
Is that available in the server edition?

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
> For a live CD, avoid the "alternate CD" & the Server Edition because it has no desktop.

I have the 12.04 install disk, and it loads up the installer just fine.  Is the Live CD something other than this?  It allows me to check disk, check memory, etc...

---

### Post by ajf412 on 2012-06-25
I have no OS on this server.

---

### Post by darkod on 2012-06-25
Yes, the live cd is different from the server cd and the alternate install cd. The live cd is the standard Desktop image, which can run from the cd and allow you to troubleshoot if your system from the hdd can't boot.

What do you mean you have no OS on the server? You said you installed it, only it doesn't boot successfully. Maybe it doesn't boot right now, but if you installed it, then you have an OS.

Yes or no?

Otherwise, without an OS on the server, what are you trying to boot?

---

### Post by ajf412 on 2012-06-25
Right.  I meant, no working OS, like windows or anything.  I'll give the LiveCD a try.

---

### Post by kennethconn on 2012-06-25
So the server OS installed fully without errors, correct?
 
Did you install the server OS without a GUI / desktop?
 
THat sounds to me like a monitor message as opposed to a server OS message displayed on-screen.
 
When you get the error message about the resolution, press return. Are you getting the command line prompt to login?
 
If you set up networking correctly during intsall, can you SSH into the server?

---

### Post by ajf412 on 2012-06-25
I tried the 12.04, 32 bit download of Ubuntu (That's what was recommended) for the Live CD.

It seems to load up a desktop just fine.  It shows me the Ubuntu desktop, and I can go into the Ubuntu forums, and see this post.  =)

So what can I do to get the server version working?  Or can I do what I need to do with desktop Ubuntu running on the server?

I just need version control software to work.

---

### Post by ajf412 on 2012-06-25
So the server OS installed fully without errors, correct?
Correct.

Did you install the server OS without a GUI / desktop?
I installed whatever the ISO gave me.

THat sounds to me like a monitor message as opposed to a server OS message displayed on-screen.
Monitor is working fine with the Live CD.

When you get the error message about the resolution, press return. Are you getting the command line prompt to login?
I get nothing.  It sits there at that error message.

If you set up networking correctly during intsall, can you SSH into the server?
I have no idea what that means.

---

### Post by ajf412 on 2012-06-25
I'm guessing you mean access it from my computer:

I am on Windows 7.  I don't see it among my network computers and devices.

---

### Post by darkod on 2012-06-25
OK, if you can boot the server into the live desktop, open terminal and post the result of:
```
sudo fdisk -l
```

I think you can try to enter the installation with chroot and change the resolution of grub2. But lets see the fdisk results first to make sure which is the root partition.

---

### Post by ajf412 on 2012-06-25
Disk /dev/cciss/c0d0: 146.8 GB, 146804797440 bytes
255 heads, 63 sectors/track, 17848 cylinders, total 286728120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000a62a

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *        2048   274147327   137072640   83  Linux
/dev/cciss/c0d0p2       274149374   286726143     6288385    5  Extended
/dev/cciss/c0d0p5       274149376   286726143     6288384   82  Linux swap / Solaris

---

### Post by darkod on 2012-06-25
OK, the c0d0p1 is the root.

First, to mount and prepare for chroot:
```
sudo mount /dev/cciss/c0d0p1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside your installation. To edit the grub2 settings:
```
nano /etc/default/grub
```

Find the line that says #GRUB_GFXMODE=640x480, remove the # at the beginning. You can leave the resolution at the default 640x480 as first try, or change it into the suggested 1280x1024. The grub2 menu doesn't need high resolution anyway. After you edit the file, press Ctrl + O to save, and then Ctrl + X to close it.

To insert the change in the grub.cfg file run:
```
update-grub
```

Exit the chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart without the desktop live cd and see if it worked.

Usually that would be the answer to the resolution message, but lets see.

---

### Post by ajf412 on 2012-06-25
When I try to enter:  "sudo chroot /mnt"

I get:  "chroot:  failed to run command '/bin/bash': Exec format error"

---

### Post by darkod on 2012-06-25
I am not sure what that error means unfortunately. That is the standard chroot procedure. Maybe someone else will have an idea.

Since you mentioned that holding SHIFT doesn't display the grub2 menu also, you can't add the resolution parameter. That's why I thought the chroot is the best bet.

You can edit the /etc/default/grub without the chroot, but you can't run update-grub without it, and you need update-grub to activate the change made.

---

### Post by ajf412 on 2012-06-25
Ah, found this elsewhere:

"You'll have to boot on a 64bits liveCD if you want to chroot into a 64bits environment."

I'll download the 64 bit and try again.

---

### Post by kennethconn on 2012-06-25
You really should read up more on the documentation before you jump into installing and configuring a server OS. That might not be what you want to hear, but it does not make it bad advice. 
 
>  
"Crawl, walk, then run"


---

### Post by ajf412 on 2012-06-25
I should, but I don't really have the luxury of time right now.  I need to get this up and running before the end of the month, so a lot of this is trial and error, and hope that I don't jack up the hardware.

---

### Post by ajf412 on 2012-06-25
Okay, it's working, but I don't see #GRUB_GFXMODE anywhere.

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
                               [ Read 34 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by ajf412 on 2012-06-25
oh wait nm.  i'm dumb

---

### Post by ajf412 on 2012-06-25
DOH!

Same message has been displayed.  =\  I tried to put in 1280x1024.  I can go back and try it with the smaller resolution.

---

### Post by ajf412 on 2012-06-25
It worked with the 640x480!

Thank you very much sir.  God bless.

---

### Post by stalkingwolf on 2012-06-26
you can also use the grub rescue disk and advanced options and there is an option to uncomment the same line.

---

