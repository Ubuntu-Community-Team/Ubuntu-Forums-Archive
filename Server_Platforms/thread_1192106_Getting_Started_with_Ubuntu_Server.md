---
title: "Getting Started with Ubuntu Server"
date: 2009-06-19
forum: Server Platforms
---

### Post by ultimatebuster on 2009-06-19
Hi all! I have a desktop laying around at home on which I want to install Ubuntu Server.

I will mainly use this to share a USB printer for a couple of Windows machines (Vista, 7, and XP), and share the ability to write and read its hard drive for these Windows machines (Map network drive option on Windows).

I also will put up a HTML and a PHP site so that whenever someone goes to a certain IP Address in my LAN/WAN, it shows up.

Here are some specs:

HP Pavilion Desktop:
[LIST][*]3.06GHZ Intel Pentium Processor, Single Core, 64-Bit capable[*]1.5GB DDR2 RAM (2x256MB + 1x1024MB)[*]Intel 82915G/GV/910GL Express Chipset[*]200GB 7200RPM HDD
[/LIST]

Other Accessories:
[LIST][*]D-link WBR1310 Wireless Router (Hardwired to the desktop)[*]HP LaserJet 1020 USB Printer
[/LIST]

These are all old stuff. Thought I might do the experiement for educational purpose. This will also allow me to use this desktop for something.

These are my questions:
[LIST=1][*]What version of Ubuntu should I install? (32bit, 64bit)[*]Is this desktop sufficient to run Ubuntu Server 9.04?[*]Can all the stuff that I want to do be done with Ubuntu Server?[*]Do I need GUI/Webmin? Any disadvantages to both of these?
[/LIST]

BTW: I have some experience with Ubuntu.

Thanks!

EDIT: Question 5. Should I use 3 partitions? O/S | Network Storage | Web page serving

---

### Post by techstop on 2009-06-19
> **ultimatebuster said:**
> 
These are my questions:
[LIST=1][*]What version of Ubuntu should I install? (32bit, 64bit)[*]Is this desktop sufficient to run Ubuntu Server 9.04?[*]Can all the stuff that I want to do be done with Ubuntu Server?[*]Do I need GUI/Webmin? Any disadvantages to both of these?
[/LIST]

BTW: I have some experience with Ubuntu.

Thanks!

IMHO;

1. 64-bit, it's generally faster, although it doesn't really matter in your case. I just like running 64-bit wherever possible.
2. Yes, absolutely. People achieve what you want from old Pentium 2's with 256MB of RAM and the like...
3. Yes.
4. You don't need GUI or Webmin.*

*Installing ubuntu-desktop on a server so you have a gui really defeats the point of installing server edition in the first place. 

Secondly, webmin has not been available in the ubuntu repos for some time, I think due to security issues. It can be installed, but it's up to you. It might make your server easier to manage.

EDIT: You might also want to look at a custom distro like [ClarkConnect]("http://www.clarkconnect.com"). It's administered by a web interface, and you can share printers, files, serve web pages etc....It will take less time to get going than customising ubuntu server from scratch.

---

### Post by ultimatebuster on 2009-06-19
> **techstop said:**
> IMHO;

You might also want to look at a custom distro like [ClarkConnect]("http://www.clarkconnect.com"). It's administered by a web interface, and you can share printers, files, serve web pages etc....It will take less time to get going than customising ubuntu server from scratch.

Intresting... Looking it up

Edit: Seemed to be more of an Internet server. 
I need a home server, and I have DHCP

---

### Post by techstop on 2009-06-19
> **ultimatebuster said:**
> Intresting... Looking it up

Edit: Seemed to be more of an Internet server. 
I need a home server, and I have DHCP

No, not quite. You can set it up in two modes; gateway or standalone. Standalone mode is what you would use. You don't *have* to use it as the DHCP server either.

See the last two categories on this page;

[http://www.clarkconnect.com/info/features.php](http://www.clarkconnect.com/info/features.php)

Anyway, probably getting off-topic for an ubuntu forum, but ClarkConnect will do what you want, with less effort, than building ubuntu server from scratch.

---

### Post by ultimatebuster on 2009-06-19
I need to Install from HDD/USB Stick because the DVD drive is not working

---

### Post by Vegan on 2009-06-19
> **ultimatebuster said:**
> I need to Install from HDD/USB Stick because the DVD drive is not working

New DVD drives are dirt cheap now, and its worth investing.

---

### Post by v3xtra on 2009-06-20
Even better is to pull it from whatever you're working on now ( assuming it is a desktop as well ) and just use that one, and then once you are done installing everything, put it back in your current desktop.  Done that numerous times.  :)

---

### Post by Ian_F on 2009-06-20
@ultimatebuster

I've done a similar thing to you and felt slightly nervous about having to do everything using the command line. So, I installed Ubuntu Server and I run VNC to give me a virtual desktop as and when I need it. Everything else I do via Webmin.

With Jaunty you can install the OS/swap on just part of the drive and leave the rest of the drive to use as you see fit.

---

### Post by ultimatebuster on 2009-06-20
Oh yeah, I have to install via USB drive. 
The DVD drive's lens maybe too dirty (used it once or twice, max)

---

### Post by ultimatebuster on 2009-06-22
bump!
I also feel like ubuntu has a bigger community, which means more help can be offered.

---

### Post by ghen on 2009-06-22
do you have any more questions or have you tried the install yet?

---

### Post by ultimatebuster on 2009-06-22
> **ghen said:**
> do you have any more questions or have you tried the install yet?

Yes, How do install Ubuntu Server via USB Drive?

I saw a lot of desktop version install on google. Is it going to be the same or is it different?

---

### Post by techstop on 2009-06-22
> **ultimatebuster said:**
> Yes, How do install Ubuntu Server via USB Drive?

I saw a lot of desktop version install on google. Is it going to be the same or is it different?

Go to the "official" source;

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

It won't matter what version you are installing. I used the unetbootin method to install UNR on my Dell Mini 9. Works great.

---

### Post by ultimatebuster on 2009-06-23
So I've installed ubuntu 9 server on virtual box. I install webmin to manage the server. It tell me i can logon to [https://virtualserver:10000/](https://virtualserver:10000/) to manage the server. 
However, I can't do it on the computer I'm running virtual box on. 
I just want to try it before the real thing. How do I make it work?

---

### Post by techstop on 2009-06-23
> **ultimatebuster said:**
> So I've installed ubuntu 9 server on virtual box. I install webmin to manage the server. It tell me i can logon to [https://virtualserver:10000/](https://virtualserver:10000/) to manage the server. 
However, I can't do it on the computer I'm running virtual box on. 
I just want to try it before the real thing. How do I make it work?

You probably have the guest network in virtualbox set to NAT, meaning that the guest has a 10.*.*.* IP address, which will not be accessible from your host with a 192.*.*.* address.

Change guest networking to bridge, then both your host and guest will be on the same subnet, and you will be able to access the web interface of webmin from your host.

---

### Post by ultimatebuster on 2009-06-24
> **techstop said:**
> You probably have the guest network in virtualbox set to NAT, meaning that the guest has a 10.*.*.* IP address, which will not be accessible from your host with a 192.*.*.* address.

Change guest networking to bridge, then both your host and guest will be on the same subnet, and you will be able to access the web interface of webmin from your host.

Sorry, you lost me there. I'm a network newbie

---

### Post by techstop on 2009-06-25
> **ultimatebuster said:**
> Sorry, you lost me there. I'm a network newbie

I don't have my linux box to hand, so this is from memory...

Open virtualbox, click the "Settings" button for your virtual machine. Under the Network heading, change "Attached To" to Bridged. It's probably on NAT now.

---

### Post by ultimatebuster on 2009-06-25
> **techstop said:**
> I don't have my linux box to hand, so this is from memory...

Open virtual box, click the "Settings" button for your virtual machine. Under the Network heading, change "Attached To" to Bridged. It's probably on NAT now.

Thanks a lot man! It's now working. 

I'll see if I have anymore questions. (Probably will)

Question Time!
If I want a Windows XP/Vista/7 computer to map a network drive that's hosted on the Ubuntu server (LAN), do I need to create a separate NTFS partition and share the folder /media/DRIVENAME

---

### Post by snkiz on 2009-06-26
you could do that but when windows goes down it will take your ntfs partition with it. You would have to reboot windows in safe mode to fix it. a least thats what happens with a shared ntfs partition on my dual boot setup. better to use samba properly configured.

---

### Post by ultimatebuster on 2009-06-26
I was considering SAMBA. 
This is not dual boot, if I understood you correctly. I'm putting the server on an old desktop computer. I need to share the HDD in the LAN network so that other computer can access that partition (read and write)

I installed SAMBA. However I can't seem to find the module in Webmin. Also, SWAT appears to be not installed.

---

### Post by snkiz on 2009-06-26
If you install samba after webmin then the module will not be loaded. Look in unused modules, you will see samba, If you click refresh modules the samba module *should* be loaded under servers. you'll have to forgive me I can't remember what SWAT even is let alone where to find it. servers are kinda set it and forget it ya know. I realize the your not doing a dual boot just trying illustrate the pitfalls of mounting partitions directly with windows... It CAN do some wired stuff.

---

### Post by ultimatebuster on 2009-06-27
I just finished installing the real thing. SAMBA module can now be found. 

I created 2 partition, one is FAT32, mounted at /media/store
one is NTFS, mounted at /media/4gbsto
using the instructions @ [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

I added this 2 lines to /etc/fstab:
```
/dev/sda3 /media/store fat32 defaults 0 0
/dev/sda4 /media/4gbsto ntfs defaults 0 0
```

Will this assure that these 2 folder are mounted automatically once the server boot-up if I ever decide to shut it down?

Now, how do I share these 2 folders (/media/store and /media/4gbsto) to Windows XP/Vista users so that they can read and write??

Also, I have a HP LaserJet 1020, how do I share it via SAMBA?

---

### Post by snkiz on 2009-06-28
that should be ok. Do you still have webmin installed? I find it easier to handle samba through webmin. you can setup your printer under the hardware tab with cups I'm not a printer guru mine just works. Then share it through samba. I believe samba is setup to share local printers by default so you *should* be good to go.

---

### Post by snkiz on 2009-06-28
other things of note 
> **ultimatebuster said:**
>  

I created 2 partition, one is FAT32, mounted at /media/store
one is NTFS, mounted at /media/4gbsto
using the instructions @ [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)


I don't understand why you used dos filesystems on your server. To my knowledge its not necessary at all and without defrag utilities it will cause issues down the line. And this:
> 4 Enable The root Account

After the reboot you can login with your previously created username (e.g. administrator). Because we must run all the steps from this tutorial as root user, we must enable the root account now.

Run

sudo passwd root

and give root a password. Afterwards we become root by running

su makes me nervous. I see sudo as a reminder that if you screw up you could hose your box. be warned not that hard to type four letters. and lastly if your accessing your server from a windows machine get putty (goolge knows all) because sometime you will need access to the config files directly.

---

### Post by ultimatebuster on 2009-06-29
oh no, I just did what I think is good for my computer. I didn't enable root, it makes me nervous as well. 

And what's going to cause issues, and more importantly, what's not?

Also, I've been working on how to share the printer for over a day at this point. I found this in Google: [http://ubuntuforums.org/showthread.php?t=1192043](http://ubuntuforums.org/showthread.php?t=1192043).

I have the same printer, and the same situation, however my windows computer still cannot see the printer when I add a network printer.

---

### Post by snkiz on 2009-06-29
FAT and NTFS are non journaling filesystems that require occasional defraging. Ubuntu does not provide defrag utilities because they're unnecessary with *nix filesystems. You may also run into issues with file permissions, long file names. To be honest I'm not sure because I don't do it. Besides IMHO: its counter productive because your not accessing the file system with windows your accessing it with Ubuntu and windows is accessing samba. As far as you printer sorry I couldn't be more help, guess I was lucky mine works without me screwing with it.

---

### Post by ultimatebuster on 2009-06-29
> **snkiz said:**
> FAT and NTFS are non journaling filesystems that require occasional defraging. Ubuntu does not provide defrag utilities because they're unnecessary with *nix filesystems. You may also run into issues with file permissions, long file names. To be honest I'm not sure because I don't do it. Besides IMHO: its counter productive because your not accessing the file system with windows your accessing it with Ubuntu and windows is accessing samba. As far as you printer sorry I couldn't be more help, guess I was lucky mine works without me screwing with it.

More about the file system. So you are saying if I have an ext3 partition and share it through SAMBA, windows still will recognize it?

I'm newbie in any sort of networking. The only knowledge of networking for me is sharing a folder/printer on windows. How would I set up the partition to share in SAMBA?

---

### Post by snkiz on 2009-06-30
> **ultimatebuster said:**
> More about the file system. So you are saying if I have an ext3 partition and share it through SAMBA, windows still will recognize it?

Thats what I'm saying BTW your running jaunty you should use ext4, it way faster. But you can use any file system you want, I have ext2, ext3, ext4, and riserfs (riser is a pain don't do it ) on my systems. If you want to know more have a look [here ]("http://en.wikipedia.org/wiki/File_system#File_systems_under_Unix-like_operating_systems"). sharing works the same way through samba however the mount defaults are different in fstab. So read up ```
man fstab
``` for the various options to get your permissions right. It may seem harder at first but its the right way to do it, less headaches in the end.

---

### Post by ultimatebuster on 2009-07-08
Wow, I'm done using Webmin and command line. Since I'm running this as a home server (possibly putting a wordpress installation onto it), is it worth it to ditch Webmin/commandline for a GUI (Gnome desktop)?

---

### Post by Ian_F on 2009-07-08
> **ultimatebuster said:**
> Wow, I'm done using Webmin and command line. Since I'm running this as a home server (possibly putting a wordpress installation onto it), is it worth it to ditch Webmin/commandline for a GUI (Gnome desktop)?

I find some things are easier using Webmin whilst others are easier using a gnome desktop. So, I'd say use both. Well, all 3 if you include Putty.

I went for a "virtual" desktop using VNC. It's perfect for my needs.

---

### Post by caco on 2009-07-09
Hello IMHO to share folders in ubuntu in easier in GUI, well except if you are a guru in Samba/NFS.

Nice to see you stuck with ubuntu, how is the 'education' progressing ;)

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by snkiz on 2009-07-09
+1 for use both its your server run it how you want. Isn't choice great

---

