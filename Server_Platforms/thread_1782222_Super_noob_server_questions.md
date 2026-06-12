---
title: "Super noob server questions"
date: 2011-06-14
forum: Server Platforms
---

### Post by Brad_J on 2011-06-14
So, I'm wondering if anyone here can help me find some resources that I should read to get started. I'm planning on setting up a home HTTP server for hosting my files and accessing them from anywhere. I realize that this is probably easier to do with FTP, but I want to be able to maybe host some kind of content on the server in the near future. Now, technically, I'm not using Ubuntu for this, I'm using Debian with no GUI because I heard that it was better for servers and no GUI because I'm running this off of an old pentium 3. I find these forums much more accessible, though, so I came here.

What I've done so far is install LAMP and set up a phpMyAdmin account. I'm not able to view anything from any of my computers, even the ones on my home network. I haven't really looked into the reason that it's not letting me, and I didn't really expect it to work with what little I've done so far, but I'm in a little over my head and hope you guys can point me in the direction of some documentation or pointers to get started as I am very new to all of this stuff, including Linux.
 
-Brad
 
PS - I'm at work right now and can't post any output from my server until I get home, but if you reply requesting some kind of output, I will put it up first thing when I do get home.

---

### Post by arrrghhh on 2011-06-14
Uhm... Ubuntu Server doesn't have a GUI either...

Also, I'm going to be sending you Ubuntu-specific docs, although they should "just work" for Debian, you might have to modify them to get 'em to work...

Any reason you didn't just opt for Ubuntu Server 10.04..?

[Ubuntu Apache doc](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Things to check would be - is the httpd service running?```
ps -A |grep httpd
```
Is the server listening on port 80?```
netstat -ano |grep 0.0.0.0:80
```

The next questions would really be about your network and how you're trying to hit the box - on your LAN, I assume you can ping the server?  Can you connect to any other services?  SSH, etc.  How are you trying to get to the webpage, just type the LAN IP (ex. 192.168.0.90) into a web browser while being on the same LAN/subnet as the server...?

---

### Post by Brad_J on 2011-06-14
No specific reason that I didn't use Ubuntu Server other than I hadn't heard a whole lot about it and I wanted to mess around with other distributions of linux. Also, I was using the external IP to attempt to access the box with no luck. I really did this last night just before I went to bed and I didn't even think to ping the box... I don't know why, I'm new to this. I will get back to you on the other things, though.
 
-Brad

---

### Post by Brad_J on 2011-06-14
Another question I had was regarding SSH, is there any useful documentation on that? I've heard a lot about it, but still have no idea how to use it properly. Sorry, if this is the wrong place to ask this, but it kind of pertains to the topic so I figured I'd ask here.

---

### Post by ruffEdgz on 2011-06-14
Here are some Ubuntu documents on SSH:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)
[http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html](http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html) -- a good site to learn more about Linux in general

Cheers!

---

### Post by Brad_J on 2011-06-14
Thanks for the help guys, I just got home from work. Arrrghhh, I typed both of those scripts into the server but they both showed nothing; even outputting them to a txt file yielded no results. I did, however, figure out how to access the test php page that I couldn't access before. The internal ipv4 worked. I must've been pretty tired this morning, though, because I completely skipped over all the documentation that this forum provides at the top. I think I'm going to restart everything and try Ubuntu Server because there is so much more information specific to that than Debian and if I run into trouble I don't want it to be because of the distribution that I'm using. Would you suggest using 10.04?

Since I'm using a crappy old laptop, my hard drive space is pretty limited, and buying a new laptop HDD that works for my ancient Dell Latitude is much more expensive than attaching an external usb hard drive. So, my question is will that work? I don't care that much about download and upload speeds being slightly affected, and I'm pretty sure it's a USB 1.0 port, but will a usb hard drive be reliable enough for what I'm trying to do?

-Brad

---

### Post by arrrghhh on 2011-06-15
> **Brad_J said:**
> Thanks for the help guys, I just got home from work. Arrrghhh, I typed both of those scripts into the server but they both showed nothing; even outputting them to a txt file yielded no results. I did, however, figure out how to access the test php page that I couldn't access before. The internal ipv4 worked. I must've been pretty tired this morning, though, because I completely skipped over all the documentation that this forum provides at the top. I think I'm going to restart everything and try Ubuntu Server because there is so much more information specific to that than Debian and if I run into trouble I don't want it to be because of the distribution that I'm using. Would you suggest using 10.04?

Since I'm using a crappy old laptop, my hard drive space is pretty limited, and buying a new laptop HDD that works for my ancient Dell Latitude is much more expensive than attaching an external usb hard drive. So, my question is will that work? I don't care that much about download and upload speeds being slightly affected, and I'm pretty sure it's a USB 1.0 port, but will a usb hard drive be reliable enough for what I'm trying to do?

-Brad

I would recommend 10.04 for a server, yes.  If the commands I had you put in earlier spat out nothing, I'd say Apache isn't running/isn't installed.

If you're going to start over, that's fine...

As for the USB/external drive question - it should be fine, so long as you be aware of heat.  A lot of external enclosures don't have fans or any cooling method, and I've seen a lot of them fail from too much heat.

Also, are you planning on using this as the boot disk or just a place to store some data?  The latter is always OK, the former doesn't always work out so well.

---

### Post by Brad_J on 2011-06-15
I was just planning on using it as a place to store information, but I could use it as either. I'm currently having some problems with ubuntu server though(new post in networking if you would care to take a look: [http://ubuntuforums.org/showthread.php?p=10942529#post10942529](http://ubuntuforums.org/showthread.php?p=10942529#post10942529)), one of which involves me being unable to detect usb devices that are plugged in. I'm not sure if this will change if I decide to boot off of the external HDD or if it even applies to external hard drives, but what kind of problems were you talking about for deciding to set it as the boot disk?
 
-Brad

---

### Post by arrrghhh on 2011-06-15
> **Brad_J said:**
> I was just planning on using it as a place to store information, but I could use it as either. I'm currently having some problems with ubuntu server though(new post in networking if you would care to take a look: [http://ubuntuforums.org/showthread.php?p=10942529#post10942529](http://ubuntuforums.org/showthread.php?p=10942529#post10942529)), one of which involves me being unable to detect usb devices that are plugged in. I'm not sure if this will change if I decide to boot off of the external HDD or if it even applies to external hard drives, but what kind of problems were you talking about for deciding to set it as the boot disk?
 
-Brad

I'll post a response in your networking thread.

As for the USB HDD it kinda varies on the machine.  The reason I say it will always work as a data store but might or might not work as a boot disk is some machines do not support booting off of a USB device.  If you are able to use it as a boot disk, more power to you - but just a word of warning, that you might have issues depending on your machine.

Can you give me the output of:```
lsusb
``` and ```
mount
```Please?

After you plug in the hard drive, thanks.

---

### Post by Brad_J on 2011-06-15
I don't actually have access to my server because I'm at work(slow day). I'll respond as soon as I get home, though.

---

### Post by Brad_J on 2011-06-15
I actually didn't see that you asked me to plug in the hard drive. I don't have it yet, but I was going to purchase one in the next couple days so I'll give you the output of the usb stick I've plugged in for now. After running "lsusb" it says:
```
Bus 001 Device 004: ID 068f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
When I plug in the flash drive initially it gives the "write through" message from above. At least now I know that it is being recognized as a flash drive.

There are a bunch of things that come up after running mount, but since I don't have the external HDD right now, not a lot of it is useful. I'll post what is there if you want but I don't want to type out the ~15 lines that are there for no reason. If this is of no use, I'm sorry, I'll post again in a day or two when I get the new HDD. Thanks, though.

-Brad

---

### Post by arrrghhh on 2011-06-16
> **Brad_J said:**
> I actually didn't see that you asked me to plug in the hard drive. I don't have it yet, but I was going to purchase one in the next couple days so I'll give you the output of the usb stick I've plugged in for now. After running "lsusb" it says:
```
Bus 001 Device 004: ID 068f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
When I plug in the flash drive initially it gives the "write through" message from above. At least now I know that it is being recognized as a flash drive.

There are a bunch of things that come up after running mount, but since I don't have the external HDD right now, not a lot of it is useful. I'll post what is there if you want but I don't want to type out the ~15 lines that are there for no reason. If this is of no use, I'm sorry, I'll post again in a day or two when I get the new HDD. Thanks, though.

-Brad

lol, I thought you said the hard drive wasn't being detected...

[quote=Brad_J]one of which involves me being unable to detect usb devices that are plugged in.[/quote]

Made me think you meant the hard drive... but your network controller is USB?  I'm sorry...

Are you not using ssh to get into the server?  That way you can copy&paste the output - much easier ;).

Edit - I've never used a USB HDD on Ubuntu Server, but [this post](http://ubuntuforums.org/showpost.php?p=10946639&postcount=11) seems to indicate you need a package in order to get your USB drives to automount.

---

### Post by Brad_J on 2011-06-16
> **arrrghhh said:**
> lol, I thought you said the hard drive wasn't being detected...
 Sorry, I meant just usb stick, not hard drive. 
> **arrrghhh said:**
> but your network controller is USB? I'm sorry...
 
Are you not using ssh to get into the server? That way you can copy&paste the output - much easier ;).
My network controller is just a 10/100 Mb PC Card that doubles as a modem, it doesn't connect through usb. I would just use ssh to copy paste, but I'm not even able to ping the laptop over my network. Although, if I were, I would have a lot more hope for this project.
> **arrrghhh said:**
> 
Edit - I've never used a USB HDD on Ubuntu Server, but [this post]("http://ubuntuforums.org/showpost.php?p=10946639&postcount=11") seems to indicate you need a package in order to get your USB drives to automount. Thanks, that's probably the reason it won't let me access my USB stick. Is there a script to manually mount a drive after booting?

---

### Post by arrrghhh on 2011-06-16
> **Brad_J said:**
> My network controller is just a 10/100 Mb PC Card that doubles as a modem, it doesn't connect through usb. I would just use ssh to copy paste, but I'm not even able to ping the laptop over my network. Although, if I were, I would have a lot more hope for this project.

Is it a PCMCIA card then...?  I need to check back on your other thread, I haven't looked at it in a few :p.  

Edit - Just checked the thread, I thought you were running Ubuntu Server.  I'll let those guys troubleshoot your issue...

> **Brad_J said:**
> Thanks, that's probably the reason it won't let me access my USB stick. Is there a script to manually mount a drive after booting?

No script.  You'd have to manually mount it.  So if you know the /dev location, use the mount command.  If you know the UUID, set it up in FSTAB and it'll always be mounted on boot.  AFAIK that applies to USB hard drives as well.

But since you're not using Ubuntu Server, none of what I mentioned really applies.  If you're using the Desktop version, none of this applies - USB drives should automount without any fuss in the Desktop edition, as soon as they're plugged in.

---

### Post by Brad_J on 2011-06-16
:P it looks like we've had some miscommunication.
> **arrrghhh said:**
> Is it a PCMCIA card then...? I need to check back on your other thread, I haven't looked at it in a few :p. 
 
Edit - Just checked the thread, I thought you were running Ubuntu Server. I'll let those guys troubleshoot your issue...

I believe that it is a PCMCIA card, I can send a picture but I don't know a whole lot about variations of these cards. I am running Ubuntu Server, I just switched over to the desktop live cd to connect to the internet because it doesn't work in the server.
 
> **arrrghhh said:**
> 
No script. You'd have to manually mount it. So if you know the /dev location, use the mount command. If you know the UUID, set it up in FSTAB and it'll always be mounted on boot. AFAIK that applies to USB hard drives as well.

I meant command, I've been kind of using them interchangably, but I guess a script is when it spans more than one line and is executed through a .sh file? What is the command to mount a drive and is there any useful documentation on FSTAB? I've heard about it a lot, but I don't actually know how to use it.

---

### Post by arrrghhh on 2011-06-16
> **Brad_J said:**
> :P it looks like we've had some miscommunication.

Heh, I think I'm more confused now than before :p.

> **Brad_J said:**
> I believe that it is a PCMCIA card, I can send a picture but I don't know a whole lot about variations of these cards. I am running Ubuntu Server, I just switched over to the desktop live cd to connect to the internet because it doesn't work in the server.

Shouldn't matter honestly, if you can get it to work on the Desktop edition (LiveCD or otherwise) you (we) should be able to get it working in the Server version.  We'll leave that talk for the networking thread you already have tho. 

> **Brad_J said:**
> I meant command, I've been kind of using them interchangably, but I guess a script is when it spans more than one line and is executed through a .sh file? What is the command to mount a drive and is there any useful documentation on FSTAB? I've heard about it a lot, but I don't actually know how to use it.

Yea, a script can be a .sh file.  Many lines of commands to automate tasks usually.

[Fstab Ubuntu Community Docs](https://help.ubuntu.com/community/Fstab) are always a good place to start.

As for the command to manually mount it, you have to know the /dev location.  We'll assume /dev/hda1 for this example:```
sudo mount /dev/hda1 /media/usbkey
```This also assumes the mount point /media/usbkey exists - you can mount wherever you want, but this is "typically" where mountpoints go.  If the disk is automounted, it always ends up in /media.

Sometimes with mount you have to specify file system, but it usually knows.  If you have to specify, -t vfat, -t ext3 etc is necessary after the mount statement.

---

### Post by Brad_J on 2011-06-18
> **arrrghhh said:**
> 
Sometimes with mount you have to specify file system, but it usually knows.  If you have to specify, -t vfat, -t ext3 etc is necessary after the mount statement.
I know that the default fs for linux is ext3 right now, but what would you recommend formatting the external drive to? I just got it last night and right now it's ntfs, which should work for just storing files. Is it easier / are there any advantages to working with ext* for file storing in linux?

Also, not at home right now and haven't touched the server box in a couple days, but I should have free time tomorrow and maybe later today and I will try to get past these networking/storage hurdles by Monday. I'll let you know when I mess up something :p

---

### Post by arrrghhh on 2011-06-20
> **Brad_J said:**
> I know that the default fs for linux is ext3 right now, but what would you recommend formatting the external drive to? I just got it last night and right now it's ntfs, which should work for just storing files. Is it easier / are there any advantages to working with ext* for file storing in linux?

Also, not at home right now and haven't touched the server box in a couple days, but I should have free time tomorrow and maybe later today and I will try to get past these networking/storage hurdles by Monday. I'll let you know when I mess up something :p

I would recommend ext4 personally.  The main reason being file fragmentation - NTFS is awful, and needs constant management.  The only reason you should go with NTFS is if you ever plan on plugging the drive directly into a Windows machine.  Even then, there's ways around it, but reading a non-Win drive on a Win machine is not just as simple as plugging in the drive ;).

---

### Post by Brad_J on 2011-06-20
> **arrrghhh said:**
> I would recommend ext4 personally.  The main reason being file fragmentation - NTFS is awful, and needs constant management.  The only reason you should go with NTFS is if you ever plan on plugging the drive directly into a Windows machine.  Even then, there's ways around it, but reading a non-Win drive on a Win machine is not just as simple as plugging in the drive ;).
Cool, I've read that ext was a lot better than ntfs for fragmenting, but will it cause any problems for downloading files to a windows machine off of the server? Also, does ext require any kind of defragmenting at any time and how would I do it? I should also mention that I found the external HDD in the /dev/ directory under the name sdb1 and mounted it successfully in Ubuntu Server. I've switched back to Debian now because of the networking issues and now I can't seem to mount the drive. I get an error message stating that I must specify the filesystem and when I put ntfs, it says ```
fs is not a valid filesystem
```
Any thoughts on this? I know that the external HDD is being detected so I'll figure it out eventually, but maybe you have some knowledge of Debian that will help. Thanks.

---

### Post by arrrghhh on 2011-06-20
> **Brad_J said:**
> Cool, I've read that ext was a lot better than ntfs for fragmenting, but will it cause any problems for downloading files to a windows machine off of the server? Also, does ext require any kind of defragmenting at any time and how would I do it? I should also mention that I found the external HDD in the /dev/ directory under the name sdb1 and mounted it successfully in Ubuntu Server. I've switched back to Debian now because of the networking issues and now I can't seem to mount the drive. I get an error message stating that I must specify the filesystem and when I put ntfs, it says ```
fs is not a valid filesystem
```
Any thoughts on this? I know that the external HDD is being detected so I'll figure it out eventually, but maybe you have some knowledge of Debian that will help. Thanks.

Try -t ntfs-3g.  Not sure tho, this isn't a Debian forum...

If you use samba, there will be **no** issues accessing files from Windows machines.  I do it all the time, and the only slight issue is permission preservation, which samba does a pretty good job of handling - just read up on how that works, especially if you want to restrict access at all.

ext* doesn't need to be defragmented.  The file system doesn't fragment, so no need to defrag.  (I've been told it basically cleans up fragments as they happen.. so for all intensive purposes, the file system does not fragment).

---

### Post by Brad_J on 2011-06-22
> **arrrghhh said:**
> 
If you use samba, there will be **no** issues accessing files from Windows machines.
Cool, I'll read into using samba, then. 
> **arrrghhh said:**
> 
ext* doesn't need to be defragmented.  The file system doesn't fragment, so no need to defrag.  (I've been told it basically cleans up fragments as they happen.. so for all intensive purposes, the file system does not fragment).
I figured out how to mount the drive and I formatted to ext4 yesterday. My network problems are fixed and I have a LAMP server running on my local network. I think that I can handle most things myself until I run into my next major issue; everything seems to be behaving as it should right now. I'm going to mark this thread as solved as the first post is not exactly even relevant anymore. Thanks a lot for your patience and help.

-Brad

---

