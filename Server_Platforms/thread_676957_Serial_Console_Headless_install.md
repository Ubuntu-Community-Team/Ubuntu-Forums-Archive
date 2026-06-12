---
title: "Serial Console Headless install"
date: 2008-01-24
forum: Server Platforms
---

### Post by RoarinPenguin on 2008-01-24
Hi Gents.

This is my very first post here, as I read this great a lot but have not been able to find a proper answer...
I'm trying to install Ubuntu onto an Intel appliance, having only serial console and NO Monitor/Keyboard connectors.

As far as I learnt, this is not possible since at least initial screen must be shown in a proper VGA monitor.

Please show me I'm plain wrong :)

Thanks, 

   RoarinPenguin

---

### Post by koenn on 2008-01-24
I think you're wrong. 
If I understand correctly, it's very well possible to install on a headless server, using a serial terminal. Most linux installation manuals describe that option. The dificulty is most likely to be in 
a/ can the device run a linux installer, or boot from a linux installation medium of some sort, and
b/ how you going to get all the required files to that device. 

Since you don't tell much about your "intel appliance', it's hard to judge, but how about :
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html)
[http://www.howtoforge.com/setting_up_a_serial_console](http://www.howtoforge.com/setting_up_a_serial_console)
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/rhbootdisk.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/rhbootdisk.html)
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/upload.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/upload.html)

---

### Post by RoarinPenguin on 2008-01-24
Ciao.
Thanks for the quick reply.
All docs you mention assume to have already a Linux system.

My situation is:
[LIST]
[*]system has only serial console
[*]I have one external USB cd reader
[*]I do not have monitor, keyboard and mouse
[*]I do not have another linux system to rebuild an ISO
[*]I have a CD with Ubuntu Server 7.10
[/LIST]

Question is now: how to instruct the initial boot to be shown on serial console... all I see in my telnet emulator (tried Tera Term and Putty) is:
Boot from CD:
and shortly after a blue screen with a blinking cursor on top left.

If I press Enter I "hear" cd in CDROM starting but nothing is shown on screen.

Thanks again in advance for the patience and support.

---

### Post by koenn on 2008-01-24
you need a boot image / installer that is compiled/configured to output to a serial console in stead of to a (non-existing) monitor. I believe  the 3th link I posted, and this : [http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-boot-loader-syslinux.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-boot-loader-syslinux.html) , explain how to do that for a boot floppy. I'm quite sure it can be modified for booting from CD - Or you can use it to find suitable search terms and look for a boot CD howto.

I assume you've verified that your appliance can actually boot from a USB CD-drive and is capable of installing and running Linux ?

---

### Post by koenn on 2008-01-24
missed this :
> I do not have another linux system to rebuild an ISO
so you should get one  :-)
or look for a Windows (or whatever you're using) program that can build customized iso's
or use floppies and a usb floppy drive ? 
or put a floppy image on a usb flash drive and see if that works
or ....

---

### Post by RoarinPenguin on 2008-01-28
Well... I did the same with CentOS5.1 and noticed that I can have a boot prompt where to type: "linux test console=ttyS0,9600,8,n,1" and proceed with text based installation on text console.
I believe a "server" system should allow this by default without particular boot image...
what's your opinion about?
TIA.
RP

---

### Post by koenn on 2008-01-28
well, you can add boot parameters to the ubuntu setup prompt as well. (press F1, F2, f3 ... at the boot prompt ..) .Whether that particular 'console ... " parameter is supported by the ubuntu server install image, I don't know. 

Should it ? never thought about it. Yours is the first case where I see a use for it. I do know there's an installer option to install over a secure shell.  You can also run an unattended install (no user intervention, so no need for keyboard or monitor) if you modify the preseed file, but that requires a remastered CD - if only to replace the default preseed file. If your appliance can boot from a USB stick, that's also a possibility, and an easier way to install with a custom preseed file.

I think you should get hold of an Ubuntu Install Manual - if it exists ; if not, try a Debian install manual and assume Ubuntu works the same. 
[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)

If you can do this console thing with CentOS, you might install that, and if you really want Ubuntu, try to start an Ubuntu install from within CentOS. 

I think you're gonna have to be creative and create a sollution with the bits and pieces you can fiend - I don't think there's any out-of-the-box sollution to this.

---

### Post by RoarinPenguin on 2008-01-28
Yes... that's same conclusion I thought...
Not that I want to make any polemic with my referring to CentOS, simply was mentioning similar experience done with another Linux Server distro.
Maybe it's my past experience with Unix, but I see great potential in having within a Linux distro an ability to be installed onto Intel-based appliances...
Great usages as dedicated and specialized servers, low consumption servers, dial in boxes, etc.
I'll make some tries with Ubuntu to see if I'm able to make any usage of USB device to boot... 
apparently the appliance BIOS allows booting from USB sticks and so on, but I have scarse experience in creating bootable USB stick.
Let's see where this brings me.
Thanks for having shed some light on this topic, hoping it'll be useful for others as well.
Ciao, 

   RP

---

