---
title: "Not enough free disk space message on update"
date: 2015-05-23
forum: Ubuntu/Debian BASED
---

### Post by Idjit_BoB on 2015-05-23
I downloaded and am using Zorin 9 OS (based on Ubuntu 14.04) for a few months now. I am a new user to Linux and am having difficulty loading an Ubuntu update due to a free space issue.

I receive the following message:

> **Not enough free disk space**
The upgrade needs a total of 77.6 M free space on disk '/boot'. Please free at least an additional 5,173 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I followed the above instructions.

As shown below, I opened the terminal and typed in 'sudo apt-get clean'.
I then get a line requesting my password. (I assumed this is the administrator password requested when I first downloaded the OS.)
I use the admin password hit ENTER.
I get the original prompt and re-enter 'sudo apt-get clean'.get a blank screen.


```
idjit-bob@idjitbob-VGN-N220E:~$ sudo apt-get clean
[sudo] password for idjit-bob: [password]
idjit-bob@idjitbob-VGN-N220E:~$ sudo apt-get clean
idjit-bob@idjitbob-VGN-N220E:
```

I tried going to the '/boot' directory to execute the command with the same (lack of) results.

Boot list (including hidden files) as of 5/23/2015...

                         ```
idjit-bob@idjitbob-VGN-N220E:/boot$ ls -a 

 .                             initrd.img-3.13.0-52-generic 
 ..                            lost+found 
 abi-3.13.0-30-generic         memtest86+.bin 
 abi-3.13.0-48-generic         memtest86+.elf 
 abi-3.13.0-49-generic         memtest86+_multiboot.bin 
 abi-3.13.0-52-generic         System.map-3.13.0-30-generic 
 config-3.13.0-30-generic      System.map-3.13.0-48-generic 
 config-3.13.0-48-generic      System.map-3.13.0-49-generic 
 config-3.13.0-49-generic      System.map-3.13.0-52-generic 
 config-3.13.0-52-generic      vmlinuz-3.13.0-30-generic 
 grub                          vmlinuz-3.13.0-48-generic 
 initrd.img-3.13.0-30-generic  vmlinuz-3.13.0-49-generic 
 initrd.img-3.13.0-48-generic  vmlinuz-3.13.0-52-generic 
 initrd.img-3.13.0-49-generic 
 idjit-bob@idjitbob-VGN-N220E:/boot$  
  
```

I used a link provided by the forum and visited Tecmint and quickly read through the commands. Although I found information regarding “sudo apt” I don't understand (the modifier and) how to get the advanced permission necessary to execute the command 'sudo apt-get clean'.

Any help would be appreciated.

Thanks in advance.

---

### Post by TheFu on 2015-05-23
/boot is full.
You need to use dpkg to clean up old kernels. The default size for /boot, which is used for lvm and/or encrypted installations, is much too small to keep more than 2 or 3 kernels around.  

To get the exact package name(s) to remove, use **dpkg -l**.  You cannot use apt-get or aptitude or synaptic or software center to do this initial removal - you must use dpkg.  Then, use apt-get to autoclean and try the apt-get update again (once there is enough storage in /boot).  Going forward, only keep 2 kernels around.  Ubuntu-based systems need a little maintenance. [http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) explains. Pay careful attention to the kernel-cleanup stuff.

---

### Post by oldos2er on 2015-05-23
Thread moved to Other OS Support & Projects.

Zorin has its own support forums [here]("http://zoringroup.com/forum/viewforum.php?f=3").

---

### Post by Idjit_BoB on 2015-05-23
Thank you TheFu for getting back. I read through your instructions and checked out the website link for *Linux PC Maintenance*. Thanks...

... but first some background. I'm in over my head.

I have these old laptops I was getting ready to throw out, because they were slow and would freeze up constantly. Someone suggested using a Linux OS on them and now they both run like new. So I am pleased to have resurrected these laptops. Only thing is I am not a real computer savvy guy and am having difficulty using the terminal and understanding the Linux commands.

Anyway, I typed **dpkg -l** as you suggested in my /boot menu and I see a list that is between 400 to 500 lines long. Now I'm stumped. Am I supposed to delete/remove/uninstall the complete list?

One thing led to another and I spent most of the day googling around the internet - mostly the Ubuntu sites - trying to get a handle on this issue and now my head is spinning. I don't even know how to organize my thoughts. I must have re-read your instructions a half dozen times to see what I was missing.

I googled **dpkg** to get a better understanding of the command, but what I found just confused me further:
[http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html) 

I found this little piece at the Ask Ubuntu website [http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu) and am a bit confused because you mentioned not to use synaptic or aptitude to accomplish the initial kernel removal. I assume the key word being initial.

I also went to the blog on *System Maintenance for Linux PCs* which you posted and tried to download Aptitude and got the following message.

```
idjit-bob@idjitbob-VGN-N220E:/boot$ apt-get install aptitude
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
idjit-bob@idjitbob-VGN-N220E:/boot$ 
```

I'm afraid I need someone to hold my hand on this. So where was I? Oh yeah, am I supposed to remove the complete list of 400-500 lines? Is there a  simple command for this? Do I need to run a script (whatever that is)?

Regards
Idjit

---

### Post by Idjit_BoB on 2015-05-24
Sorry about that last post. I don't want you to get the wrong idea. You have already provided valuable information and I appreciate it very much. It's my lack of knowledge and the end of a fairly frustrating day - Linux-wise - that was getting to me.



Regards
Idjit
Amish Country-PA, USA

---

### Post by Elfy on 2015-05-24
Zorin comes with Synaptic. 

Open that. 

Click on Installed in the left pane. 

In the Quick filter at the top put 3.13.0

It should then show you the kernels you have installed.

Click on Latest Version.

That should sort them. 

It will then look *like* this - (but not exactly as I have different kernels installed.)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262184&d=1432480167[/IMG]

From your boot list we can see you have these installed.

config-3.13.0-30-generic
config-3.13.0-48-generic
config-3.13.0-49-generic 
config-3.13.0-52-generic  

In synaptic - highlight those that show the 3.13.0-30 and -48 as version, right click and mark them for complete removal.

Let it do it's thing then Apply.

---

### Post by Idjit_BoB on 2015-05-25
Thank you Elfy your post is much appreciated. I didn't know what I was looking at when I did the boot list until you pointed it  out to me. I'm not beating myself up over it but that should pretty much tell anyone my level of knowledge is a little below sea level.

 I was going to use Synaptic as you pointed out but I balked when TheFu said:
> You cannot use apt-get or aptitude or synaptic or software center to do this initial removal - you must use dpkg
I know I need to increase my proficiency on the terminal using code and am interested in hearing TheFu's reasoning for the removal method he describes.

In the future I will be studying up on Synaptic and follow TheFu's advice on "kernel-cleanup stuff."

Regards
Idjit
Amish Country-PA, USA

---

### Post by TheFu on 2015-05-25
Did **synaptic** work or not?

---

### Post by Idjit_BoB on 2015-05-26
TheFu,

I was going to wait for your thoughts before trying the ***Synaptic Package Manager***. I just tried it and the ***Mark for Complete Removal* **line is greyed out so no synaptic did not work. Rats!

To recap my semi-rant from a previous post when I ran **dpkg -l** I got between 400 to 500 lines of information. I searched for** *linux-image 3.13.0*** and I cannot find it anywhere within the dpkg generated list.

 I'm guessing that the list generated by **dpkg** is an unpacked image file or two or three, but I don't know for sure. If so how do I determine what of the 400 to 500 lines in the list to remove?

For instance in the list is
```
ii  xml-core       0.13+nmu2    all          XML infrastructure and XML catalo
```
Do I run **dpk -s xml-core**? (See results.)
```
idjit-bob@idjitbob-VGN-N220E:/boot$ dpkg -s xml-core
**Package:** xml-core
**Status:** install ok installed
Priority: optional
Section: text
Installed-Size: 188
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
**Version:** 0.13+nmu2
Depends: sgml-base (>= 1.26+nmu2), sed (>= 4.1.2-8)
Suggests: debhelper (>= 9.20120909)
Conffiles:
 /etc/sgml/xml-core.cat 055ba0bd3154c0a58b9bf8a0c9ecf2fa
Description: XML infrastructure and XML catalog file support
 This package creates the XML infrastructure directories and provides
 XML catalog file support in compliance with the current Debian XML
 Policy draft:
 .
   * infrastructure directories:
      - /etc/xml
      - /usr/share/xml/{declaration,entities,misc,schema}
      - /usr/local/share/xml/{declaration,entities,misc,schema}
 .
   * XML catalog schema: OASIS XML Catalog Committee Specification 1.0
 .
   * update-xmlcatalog(8): tool for maintaining the root XML catalog
     file and the package XML catalog files in the '/etc/xml' directory
     as well as local XML catalog files.
 .
   * dh_installxmlcatalogs(1): debhelper tool for installing local XML
     catalog files and registering XML entities in package XML catalog
     files and the root XML catalog file (requires debhelper package)
Original-Maintainer: Debian XML/SGML Group <debian-xml-sgml-pkgs@lists.alioth.debian.org>
```
Where Package, Status and Version are highlighted in bold. The status is installed so I would not run **apt-get autoclean** on this one item. Am I seeing this correct? Is there anything else I need to be concerned with in the Status Report such as dependencies?

I could then work through each line to identify the status of all the packages and run autoclean on those which are not installed.

Let me know if I'm getting warm or am completely off-base here.

What about multiple lines such as **xserver-xorg-i**?
```
ii  xserver-xorg-i 1:7.7+1ubunt i386         X.Org X server -- input driver me
ii  xserver-xorg-i 1:2.8.2-1ubu i386         X.Org X server -- evdev input dri
ii  xserver-xorg-i 1:1.9.0-1bui i386         X.Org X server -- mouse input dri
ii  xserver-xorg-i 1.7.4-0ubunt i386         Synaptics TouchPad driver for X.O
ii  xserver-xorg-i 1:13.0.0-1bu i386         X.Org X server -- VMMouse input d
ii  xserver-xorg-i 1:0.23.0-0ub i386         X.Org X server -- Wacom input dri
```
I assume this is one package with different versions and descriptions.

Once the packages which need to be removed are identified I'm still a bit shaky on the syntax for Linux to properly execute **apt-get autoclean** and **apt-get update**.

Please let me know if I am starting to see this correctly.

Thanks for your help.

Regards
Idjit
Amish Country-PA, USA

---

### Post by Idjit_BoB on 2015-05-26
Good thing I'm retired. I got some time on my hands.

Regards
Idjit
Amish Country-PA, USA

---

### Post by TheFu on 2015-05-26
Try this: [http://ubuntuforums.org/showthread.php?t=2278348&highlight=boot+full+dpkg](http://ubuntuforums.org/showthread.php?t=2278348&highlight=boot+full+dpkg)  Start around post #27 ...
and here's another - similar: [http://ubuntuforums.org/showthread.php?t=2235403&page=2&highlight=full+boot+dpkg+howto](http://ubuntuforums.org/showthread.php?t=2235403&page=2&highlight=full+boot+dpkg+howto)

Basically, use dpkg to find the list of installed kernels. Save the package names for all but the last 2 working kernels. The dpkg output first column says if a kernel is installed, partially installed, failed, or removed. You'll need to understand those.

Then use dpkg to remove those kernels you don't need anymore. Keep using the dpkg --list|grep .... to verify.
When you are all done, verify there is empty space on /boot - **df -h /boot**.

Next tell the package manager to finish installing the last failed kernel - **sudo apt-get -f install**. This should work now and should for grub to update.

Lastly, run an autoremove to clean up old packages - not just old kernels.  **sudo apt-get autoremove**.

It is much easier to remove older kernels BEFORE there is an out-of-space issue, so stay on top of the space in /boot.

Those links have exact examples of the needed commands. Be careful using any complex regex commands. I wouldn't use those from the first link.  As you see if you read those threads, getting to the exact solution took them some time. It is a learning process. Next time (if this happens again), it will be a 5 min fix.

---

### Post by Idjit_BoB on 2015-05-29
To TheFu:

Thanks for posting and then following up with an edit to help me understand.

I have been reading through the link you provided and using terminal to find the information as posted in that thread.

Unfortunately I am having issues trying to log into the forum. It seems that ***Ubuntu One*** doesn't recognize my password so every time I want to post I have to do a "Forgot Password" request. I am not as good at multi-tasking as I once thought I was. I am trying to get Ubuntu to resolve my log in problem and then will continue wit your recommendation.

Thanks. I will keep you posted (pun intended).

Best regards
Idjit
Amish Country-PA, USA

---

### Post by Idjit_BoB on 2015-05-30
TheFu:

Thanks for directing me to those other threads. It was nerve racking for someone with little to no knowledge of Linux. In the end the walk through wasn't so bad as hitting yourself in the head with a hammer 20 or 30 times. Or for that matter having to look at all those lines which popped up after some of those Linux commands.

There were no partially installed, failed or removed kernels when running **dpkg -l | grep linux-** nor do I remember seeing it discussed at [http://ubuntuforums.org/showthread.p...boot+full+dpkg]("http://ubuntuforums.org/showthread.php?t=2278348&highlight=boot+full+dpkg"). I am curious though how to remove kernels using the dpkg command.

I was able to remove **linux-image-3.13.0-30-generic** through the terminal with the **sudo apt-get autoclean**, **sudo apt-get clean** and **sudo apt-get autoremove **commands. This opened up enough space to use the *Synaptic Package Manager* and do a *Complete Removal* of **linux-image-3.13.0-48-generic.**

However, I did notice where the terminal command(s) removed **linux-headers-3.13.0-30** and **linux-headers-3.13.0-30-generic **the *Synaptic Package Manager *did not remove those headers associated with **linux-image-3.13.0-48**.

I did come up with a problem with **duplicate sources** and do not know what they mean or whether I need to clean them up. I was prompted to run the **apt-get update** but when I did I got the same prompt again.

```
[FONT=Courier 10 Pitch][SIZE=2]W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages) [/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages) [/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages) [/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages) [/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]W: You may want to run apt-get update to correct these problems[/SIZE][/FONT]
```

I learned something... not sure what it was, but I learned something. I saved everything as a document and will go over and try to digest it after my eyes recover and head recovers.

Regards
Idjit
Amish Country-PA, USA

---

