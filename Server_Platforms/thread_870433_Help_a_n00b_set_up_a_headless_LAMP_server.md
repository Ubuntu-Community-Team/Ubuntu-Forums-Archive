---
title: "Help a n00b set up a headless LAMP server"
date: 2008-07-25
forum: Server Platforms
---

### Post by 80x on 2008-07-25
I've always wanted to try setting up my own web server. I want to do something along the lines of what this guy has done: [http://stooge.myftp.org]("http://stooge.myftp.org"). I just want to have my own little server that I can mess around with, keep in my closet, and serve a simple website from that anyone in the world can visit.

However, I'm a big n00b in 3 ways:
1) I've never set up a server before.
2) I've never used Linux before.
3) I've never used a command line interface before.

I picked Ubuntu because it's supposed to be one of the most popular/reliable Linux distros. I've got a junky old computer that used to run Windows 98, but I just installed Ubuntu Server Edition (Hardy Heron) on it (with LAMP, OpenSSH, and Samba). I was able to log in, navigate around, and investigate a bit with commands like "cd" "pwd" "ls" and "man" but I need a bit of help getting everything up and going. I thought about installing the Xubuntu GUI (which would make everything much easier for a n00b like me) but I decided that I'd rather stick with the CLI and do things the "right way" instead of the "easy way". Anyway, there are 3 things that I need help with at the moment:

[COLOR="Red"]1)[/COLOR] Figuring out how to use both hard drives, CD-ROM drives, floppy drive, etc.
[COLOR="Lime"]2)[/COLOR] Setting up the wireless card with ndiswrapper.
[COLOR="Blue"]3)[/COLOR] Making it headless with OpenSSH and Webmin.


[INDENT][COLOR="Red"]1)[/COLOR] As I said, I was able to navigate around the system a bit. However I was unable to figure out how to access things like the second hard drive or the floppy drive. The computer has 2 hard drives (one is 8.5 GB, the other is 40 GB), 2 CD-ROM drives (one internal, the other external and connected by USB), a floppy drive, and a zip drive. I installed Ubuntu on the 8.5 GB hard disk (at installation I chose Guided - Entire Disk) and figured I would use it for system files, programs, etc., while I thought I would use the 40 GB disk for documents, website files, storage, etc. However, I can't figure out how to access the 40 GB disk, or any of the drives. The floppy drive had a light that used to turn on under Windows 98, but it's not lighting up now that Ubuntu is installed.

[COLOR="Lime"]2)[/COLOR] The wireless card is a Belkin Wireless Desktop Network Card, model F5D6001 (ver. 2114). I downloaded ndiswrapper (ndiswrapper-1.53.tar.gz) and the correct Windows XP driver (NET8180.INF), put them on a floppy disk, and put the floppy disk in the computer. But then I was unable to figure out how to access the floppy drive (see above - problem #1). Once I'm able to use all the drives, I will need help installing and configuring ndiswrapper.

[COLOR="Blue"]3)[/COLOR] I would like to put the box in my closet and store the monitor, speakers, keyboard and mouse in my garage. I will need help figuring out how to install/use Webmin and OpenSSH. I'm on vacation and at home now, but pretty soon I'm going to have to go back out of town again for college, so that's all I want to do for now: set it up headless in the closet so I can access it and mess around with Apache/MySQL/PHP and set up a simple website on it remotely from another computer while I'm out of town. (I plan to get a free hostname from dyndns.com)[/INDENT]



**PS: When you give me commands to type, it would be great if you could explain what each line does, because I like to know why things work, rather than just copying and pasting blindly.**

PPS: Thanks in advance to anyone who wants to help me!!! :-D

---

### Post by Uluen on 2008-07-25
1) Your second disk is probably not mounted if you didn't ask the installer to use it.

```
# mount
```

```
# man mount
```

```
# cat /etc/fstab
```

This will install the SSH server so you can log in from another computer with a client like [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/"):
```
# apt-get install openssh-server
```

---

### Post by hrod beraht on 2008-07-25
> **80x said:**
> ...so that's all I want to do for now: set it up headless in the closet so I can access it and mess around with Apache/MySQL/PHP and set up a simple website on it remotely from another computer while I'm out of town.

If you checked LAMP and SSH during the install, then your website is up and running already. And it should already be available at [http://youripaddress](http://youripaddress)

However, if you have this computer behind a router, there is one more step you need to do first, and that is to port forward http and ssh requests to this computer. That is from your internet ip address through the router to your local lan address (usually something like 192.168.1.100).

To make it easy, you should give your server a static ip address so that it doesn't change. Basically, change the /etc/network/interfaces file to a static address:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup (backup the original just in case)

sudo nano /etc/network/interfaces

Change:
auto eth0
iface eth0 inet dhcp

To:
auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0

```
The above would give your server a static local lan address of 192.168.1.150 (no special reason for the number 150. you can make it another number if you wish. most routers will assign from 100 onward)
Note: this also assumes your network assigns address as 192.168.1.xxx and the router itself is at 192.168.1.1. Check the status page of your router to make sure (or use *ifconfig* and *route* commands to see similar information).

After you save the changed file, restart networking:
```
sudo /etc/init.d/networking restart
```

So after giving your server a static ip, you can then forward the ports for http and ssh in your router and forward them to your server (i.e. 192.168.1.150). So that way, when an http request comes in from the internet, your router will send the request to the specified ip of your server. Forward ssh the same way within your router (if you aren't sure how to access your router, try [http://192.168.1.1](http://192.168.1.1))

Once you've done all that, simply try going to [http://yourinternetipaddress](http://yourinternetipaddress) and you should see the default apache **It works!** web page.

And to ssh into your server, simply type *ssh username@ipaddress* in a terminal (or use the PuTTY program if you are on a windows computer.

Bob

---

### Post by 80x on 2008-07-26
Hey guys, thanks for the replies! However, in order to set up port forwarding, I've got to get onto the network. In order to do that, I've got to set up the wireless card. I can't set up the wireless card until I get ndiswrapper and the XP driver onto the computer (via floppy disk or CD). I can't use floppy disks or CDs until I get this mounting business sorted out!


Am I correct in thinking that I need to mount any sort of hard disk or drive (floppy, zip, CD, etc) in order to use it? I tried following this tutorial: [[COLOR="Navy"]https://help.ubuntu.com/community/InstallingANewHardDrive[/COLOR]]("https://help.ubuntu.com/community/InstallingANewHardDrive"). However, I ran into some trouble and have some questions:

**1)** The 2nd hard disk is formatted in FAT32. If I want other (Windows XP) computers on my network to be able to add/remove/change files on it (Is that what Samba is for?), does it have to stay FAT32, or can/should I reformat it as ext3? Or is FAT32 only recommended if I've got both Windows and Linux installed on the server itself (I've only got Ubuntu)?

**2)** The 2nd hard disk still has a ton of files leftover from when the computer was running Windows 98. How do I wipe the disk clean?

**3)** I mounted the 2nd hard disk successfully, but it became unmounted after I rebooted the computer. I tried using gksudo (as instructed in the tutorial I linked to above) in order to edit /etc/fstab and set up an automatic mount at boot, but it said gksu wasn't installed. When I tried installing gksu, it said "E: Couldn't find package gksu". What is gksu/gksudo? Do I need it? How do I install it? Is there another way to edit /etc/fstab to set up an automatic mount at boot?

**4)** When I tried mounting the zip drive without a zip disk in it, it said "No medium found". When I tried mounting it with a zip disk in, it said "You must specify the filesystem type". How do I mount/use the zip drive?

**5)** When I type "sudo lshw -C disk", both hard disks, both CD drives, and the zip drive show up. The floppy drive doesn't. Also, each CD drive has multiple logical names. The internal one has "/dev/cdrom" "/dev/scd0" and "/dev/sr0". The external one has "/dev/cdrom1" "/dev/cdrom2" "/dev/scd1" and "dev sr1". Right now, when I type "ls /media" it shows cdrom, cdrom0, cdrom1, floppy, floppy0, HardDisk2 (created by me, and temporarily mounted to, but I was unable to set up automatic mount at boot) and zip (created by me, but I was unable to mount the zip drive to it). How do I mount/use the floppy drive and the 2 CD drives?


Thanks a lot to anyone who can help with those questions! I'm learning fast how to use the CLI and thinking that it's not so hard after all... I just need a bit of help with the initial set up of the computer.

---

### Post by kunixos on 2008-07-26
OK! Yes you need to mount your drives in order to use them. 

1> ```
$ sudo mount -t vfat /dev/hdX /media/hdX
```will mount your FAT32 device (the -t tells it a filesystem type follows and the 'vfat' is for a virtual FAT16/32 format. You can replace the /media/hdX with where you want to mount it. This is fine for windows and Linux and will probably work for what you intend it for without formatting (remember: formatting ERASES the entire disk!)

2> in order to 'wipe it clean' you'll need to reformat it.```
$ sudo fdisk /dev/hdb
```will bring you to the disk formatter. from there you can type 'm' for help with options, but what you're doing is probably a clear Delete 'd' previous partition table and then 'n' create one. once you're done setting up the partition table, you'll need to format the new partition(s)```
$ sudo mkfs.ext3 /dev/hdbX
```where hdbX is the new partition (you can search for other filesystem types to create by typing 'mk' and hitting tab for autocomplete options).

3> gksudo is a graphical sudo tool. Since you're using CLI, you'll only need to type 'sudo' and then your commands. To modify fstab, type```
$ sudo nano /etc/fstab
```and then edit the text file to include a line like```
/dev/hdbX /media/hdbX defaults 0 0
```subbing in your drive number/mount point/options/etc.

4> You cannot mount disks with no disks. Simple. To specify the filesystem type just use```
-t *systemtype*
``` in the 'mount' command. Most likely your ZIP disks are formatted for 'vfat' so that should work.

5> you mount them with the same commands used above. you should not need to use a filesystem type on CDs unless you are mounting images (in which case '-t iso9660' is what you'd use). As for the multiple names, as long as you use one of the device names it'll recognize what you mean. then just choose the mount point in the /media folder for the 'point' the data will be located.

More stuff... Read the man page for mount. Read more on the wiki and forums. These questions are pretty basic, and a lot of really handy guides already exist. I don't mind answering these questions for you now, but if you'd really like to get into the CLI side of the house and 'dig into' Linux then you're going to have to learn some research tools. Google can answer most of the questions you just posted.

Keep a positive attitude though, I've done this same project and it was worth the effort!

Don't forget to read about Apache and understand how it works. Also research SSH Keys for secure authentication. On a side note, you might want to have this computer physically attached to the router (no wireless) as it'll make the lag less when you try to access it from the net.

You can also use Free DNS services on the net to 'hide' your IP address and mask it with a regular URL. [http://www.no-ip.com]("http://www.no-ip.com") is one that I used for a while.

One more thing. ndiswrapper is something you download from the ubuntu repos and then setup with the files from your XP driver. Search for how to set it up on Google or check their official site. It's pretty straight forward stuff. You can check what kind of wireless card you have (if you don't already know) by typing```
$ lspci | grep Network
```and it should tell you!

Hope this all helps! Don't give up!

---

### Post by songshu on 2008-07-26
> **80x said:**
> 

Am I correct in thinking that I need to mount any sort of hard disk or drive (floppy, zip, CD, etc) in order to use it? I tried following this tutorial: [[COLOR="Navy"]https://help.ubuntu.com/community/InstallingANewHardDrive[/COLOR]]("https://help.ubuntu.com/community/InstallingANewHardDrive"). However, I ran into some trouble and have some questions:

yes, you are right. 

mount /cdrom 

> 
**1)** The 2nd hard disk is formatted in FAT32. If I want other (Windows XP) computers on my network to be able to add/remove/change files on it (Is that what Samba is for?), does it have to stay FAT32, or can/should I reformat it as ext3? Or is FAT32 only recommended if I've got both Windows and Linux installed on the server itself (I've only got Ubuntu)?


ext3 is recommended.

if you do
# sudo fdisk -l
it will show all drives

# sudo mkfs.ext3 /dev/hdXX

where hdXX is the 40GB drive that showed up to MaKe the File System ext3
> 
**2)** The 2nd hard disk still has a ton of files leftover from when the computer was running Windows 98. How do I wipe the disk clean?


the above command mkfs will do that if i'm not mistaking.

> 
**3)** I mounted the 2nd hard disk successfully, but it became unmounted after I rebooted the computer. I tried using gksudo (as instructed in the tutorial I linked to above) in order to edit /etc/fstab and set up an automatic mount at boot, but it said gksu wasn't installed. When I tried installing gksu, it said "E: Couldn't find package gksu". What is gksu/gksudo? Do I need it? How do I install it? Is there another way to edit /etc/fstab to set up an automatic mount at boot?


gksudo is only if you have installed a desktop, (its the graphical thing)

# nano /etc/fstab
will do it for you

> 
**4)** When I tried mounting the zip drive without a zip disk in it, it said "No medium found". When I tried mounting it with a zip disk in, it said "You must specify the filesystem type". How do I mount/use the zip drive?


you have to specify the file system 
i guess its a dos formatted disk, so you would do.
# mount -t vfat /dev/XXXX /zip

> 
**5)** When I type "sudo lshw -C disk", both hard disks, both CD drives, and the zip drive show up. The floppy drive doesn't. Also, each CD drive has multiple logical names. The internal one has "/dev/cdrom" "/dev/scd0" and "/dev/sr0". The external one has "/dev/cdrom1" "/dev/cdrom2" "/dev/scd1" and "dev sr1". Right now, when I type "ls /media" it shows cdrom, cdrom0, cdrom1, floppy, floppy0, HardDisk2 (created by me, and temporarily mounted to, but I was unable to set up automatic mount at boot) and zip (created by me, but I was unable to mount the zip drive to it). How do I mount/use the floppy drive and the 2 CD drives?


just like the harddrive you can do those in /etc/fstab as well

---

### Post by antilog on 2008-07-26
That's some ambition!  I've learned a lot about gnu-linux from doing what you're doing, having a project and figuring things out, with the aid of google, forums, tutorials and wikis.  One general principle I have found in life in general that helps me be a decent community member is that of the "guru etiquette", for lack of a better term.  Try to do a task yourself using all your resources, then when you are stumped, seek help from someone more knowledgeable than you (a guru), and show them what you have tried so far.  People are more willing to help when you are not lazy (I am not saying you are), and you will learn more.  Even if it requires a lot of searching and trying 6 different things, it is worth it.  When I had the itch to try linux, it seemed rough, and I never thought I would be able to do what I can do today.  

A couple things I learned to make things much easier:
- Accessing server files - i used to ftp in, open the config in windows notepad, then save, and ftp it back.  That sucks.  Use SSH (I use putty) to get a CLI.  This way you can have the CLI of your server up, and a web browser, and copy and paste commands directly from the browser into the CLI.  For editing configs, nano is extremely handy. I hated using vi, but nano is helpful and intuitive.  So if you need to add some lines you found in a forum to a config file, just SSH in, nano the file and copy and paste.
- get comfortable with the CLI and basic commands.  While a GUI should do most things, it is not nearly as elegant as accessing files directly in the CLI, especially for networking.  My success rate at configuring or fix networking stuff in Linux is far greater when using the CLI.  
- speaking of commands, learn basic file commands (li, mv, rm etc...) and learn chmod, chown, tar, cat, nano and learn some basic switches.  
- apt-get is relatively easy to use to get packages
- wget is used to download files from internet.  When I am installing stuff, I'll SSH into my server, cd to /tmp, copy a link address from a web browser (say for VMWare Server), then back in the shell, type wget then paste the address. 
- speaking of directories, learn the basic directory structure of linux.  you will become familiar with where to find things.  get in the habit of always downloading tars to 1 directory, and work with them there.  I use the /tmp, some people use their /home/user directory.  

For you specifically, I recommend dropping a LAN NIC in that box to at least get the server setup and save yourself a lot of headaches. Wifi config can be a bear.

Forgive me if some of this is redundant or not applicable, there is a ton of info posted in this forum, and I just wanted to share some general stuff I have learned.

Enjoy....

---

