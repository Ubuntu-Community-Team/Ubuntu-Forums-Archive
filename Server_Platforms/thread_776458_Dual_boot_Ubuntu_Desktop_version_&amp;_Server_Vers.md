---
title: "Dual boot: Ubuntu Desktop version &amp; Server Version installing in the same machine"
date: 2008-04-30
forum: Server Platforms
---

### Post by hannah187 on 2008-04-30
Hi All,

I am currently running Hardy 32 bit Desktop version on my Thinkpad. I have got 1 root (10gb) partition, 1 logical partition (9gb for my data files), 1 swap (1gb). I have all ready copied all my data on my flash drive. 

I have got 2 queries:
1.	Can I install 7.10 server in my Thinkpad keeping my Hardy Desktop version intact? I like to run both Desktop version and Server in the same laptop (dual boot).
2.	If yes, could someone be kind enough to tell me how. I have got Ubuntu 7.10 server install CD with me. 

Kind regards to all

---

### Post by hannah187 on 2008-05-01
Hi guys.. is this possible please..

many thanks for your time

---

### Post by ginjabunny on 2008-05-01
I think this worked but was quite a while back that I tried it, I think I dual booted Fedora and Ubuntu.

If I remember correctly the problem I had was that the grub loader points to the second system you install, the way I got round this was to have a 150MB /boot partition as the first partition, then install the first system then backup the /boot partition and install the second system so they can both use the same /boot and swap but must have different / [root] partitions, then when grub loads from the /boot you can change the /boot/grub/menu.list to load whatever you want.

There maybe easier ways!?

---

### Post by FrankVdb on 2008-05-02
You could run the server in a virtual machine on the desktop or run the desktop in een virtual machine on the server. VMWare and VirtualBox offers user-friendly solutions to do that.

---

### Post by hannah187 on 2008-05-03
> **FrankVdb said:**
> You could run the server in a virtual machine on the desktop or run the desktop in een virtual machine on the server. VMWare and VirtualBox offers user-friendly solutions to do that.

hey thanks..
so what I am hearing is that dual boot between Desktop and Server on the same machine is not possible. I hope I am wrong.

---

### Post by andguent on 2008-05-03
It most definitely is possible. You may however, need to learn how to rebuild grub on your own, and/or manually combine the menu.lst file from two different installs.

To back up for a second... Why do you want to dual boot server and desktop?

Keep in mind that the biggest difference between server and desktop is what software is installed. You can definitely install and run Apache, MySQL, & PHP on a desktop box and configure it identical to the way it ususally would be on a server install.

The reverse is also true, take a server and install the package 'ubuntu-desktop'. It will pull down gobs of user packages like web browsers, pdf viewers, etc. You basically end up with a server & desktop combined. 

Either of the above two options will probably be less work then dual booting it, or VM'ing it. Luckily it is Linux, so you can do it however you want. :)

---

### Post by CorvisRex on 2008-05-03
andguent is pretty right on here.   There is no reason you can't do it at all.  I have done it.  I always have a group of partitions just for a server installation (currently Ubuntu server) the installation is pretty much normal,  just a little grub work to set up the grub menu, that is all.  But it depends on why you are doing it...I set up a server seperately, so that I can test, mangle, fix, play, without any risk of messing any data, And so I can change different servers and test them, (Next:CentOS)
But pretty much  all the server software is available to pretty much any setup,  There is no reason you CAN"T  install apache, php etc on your regular Ubunutu, without installing the actual server OS.  Really depends.  Sometimes setting the servers up in VM, or just installing the server packages in you regular desktop is enough without having to dual boot.

my 4 cents....

raven

---

### Post by ghostknife on 2008-05-03
OK.

Step 1: Install the one and create the desired partitions during installation. 4 should be sufficient. 
a. Make the 1st one and mount point as /boot
b. Make the 2nd one the desired size for the server root (/) mount point
c. Make the 3rd one the desired size for the desktop root (/) mount point
d. Make the 4th one your swap parition (which would be shared)

Step 2: Boot this installation and copy the whole /boot directory to some location inside it's root (say /root or whatever won't be lost during the second install).

Step 3: Then install the second one and remember to select the OTHER root partition as your mount point. You can optionally use the alternative system's root as a mountpoint like /mnt/server on the desktop installation, and /mnt/desktop on the server installation.

Step 4: Boot the second installation and backup your current /boot to a second location. Then please do the following commands and paste the output. I'll guide you again from here.
```

ls -l /path/to/first/installation/boot/backup
ls -l /path/to/second/installation/boot/backup
```

Please do them in this order and specify which is which (ie. server/desktop).

Then also paste your menu.lst file from both of these backup location's grub subdirectory, like /path/to/boot/backup/grub/menu.lst. Specify which is which (ie. server/desktop)

---

### Post by hannah187 on 2008-05-05
Thanks a lot guys for this information.. I am new in Linux world and reasonably computer savvy. I just wanted to see the server side and have a little play. This is my spare machine hence I am not too worried about data loss. I use this machine to learn different side of Linux. Thanks again for all the help.

---

### Post by andguent on 2008-05-05
If looking to learn the hard way, rebuilding grub manually is a very good skilll to have. Later when you play/break other things like software raid, it is good to be able to fall back on it when needed. I wouldnt recommend doing it on a live machine though. :) Good luck. Happy learning.

---

### Post by rgeddes on 2008-05-14
I just posted a similar question... and realized I had another similar question... 

I have an Ubuntu server running and from time to time I'd like to take advantage of the GUI tools (I assume this means the desktop) to manage the server.  When I'm done I'd like to be able to off-load (not "sudo apt-get remove") the GUI tools so they are not taking up resources(memory, CPU time, etc) the server can use in it's operation.

I think the server/desktop dual boot solution would require a reboot every time you wanted to switch, not to mention downing the servers while the desktop is running.

I guess what I'm asking is ... is there a way to load/unload the Ubuntu desktop from memory without interrupting the server?

Thanks
Richard

---

### Post by andguent on 2008-05-14
[http://ubuntuforums.org/showpost.php?p=4749704&postcount=2](http://ubuntuforums.org/showpost.php?p=4749704&postcount=2)

---

