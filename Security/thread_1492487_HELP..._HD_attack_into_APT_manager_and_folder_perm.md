---
title: "HELP... HD attack into APT manager and folder permissions"
date: 2010-05-24
forum: Security
---

### Post by eaglemystic69 on 2010-05-24
OK, 
WOW . . .

I may not be a code worrior, yet I have been a Ubuntu convert from Apple for about 3yrs now.  Since 1984-2006 now hackers or viruses.  And Until now Ubuntu has been clean, well I have been good with repos, etc.

1.  Recently I found "Odd" behavior with my Amarok 1.4 player, ffmpeg, winff. 

2.  During a Synaptic upgrade there were some "unauthorized changes".  I have seen this before due to some of my software, so I ignored it. . .

To my bewilderment, "It" erased Amarok 1.4 player, ffmpeg, winff, all image kernels, claimed domain over my system permissions, and external HD.

B4 I shutdown, downloaded LUCID 10.4. . . restarted, then copied over all info possible to minimize a complete delete of my system.

Upon restart, indeed all kernel images were gone, Only live CD allowed me access to repartition my HD.  

NOW. I have Lucid running, and have been denied access to my external HD and partitioned (internal HD).  I used Nautilus to copy over files to my internal laptop HD, yet permissions continue to be an issue.  The INFECTED FOLDERS are owned by "User 999-user#999.  I must micro manage every folder and file to gain "partial permission".  The dialog box stutters and never allows me to go down to "Root"

What do I do . .. .  Wanta see sum info . .. .please send me the code ya want to see.:confused:

---

### Post by bodhi.zazen on 2010-05-24
> **eaglemystic69 said:**
> OK, 
WOW . . .

I may not be a code worrior, yet I have been a Ubuntu convert from Apple for about 3yrs now.  Since 1984-2006 now hackers or viruses.  And Until now Ubuntu has been clean, well I have been good with repos, etc.

1.  Recently I found "Odd" behavior with my Amarok 1.4 player, ffmpeg, winff. 

2.  During a Synaptic upgrade there were some "unauthorized changes".  I have seen this before due to some of my software, so I ignored it. . .

To my bewilderment, "It" erased Amarok 1.4 player, ffmpeg, winff, all image kernels, claimed domain over my system permissions, and external HD.

B4 I shutdown, downloaded LUCID 10.4. . . restarted, then copied over all info possible to minimize a complete delete of my system.

Upon restart, indeed all kernel images were gone, Only live CD allowed me access to repartition my HD.  

NOW. I have Lucid running, and have been denied access to my external HD and partitioned (internal HD).  I used Nautilus to copy over files to my internal laptop HD, yet permissions continue to be an issue.  The INFECTED FOLDERS are owned by "User 999-user#999.  I must micro manage every folder and file to gain "partial permission".  The dialog box stutters and never allows me to go down to "Root"

What do I do . .. .  Wanta see sum info . .. .please send me the code ya want to see.:confused:

Sounds like normal behavior to me.

The crux of your problem is that you interrupted an upgrade after over reacting to what was likely a warning. My guess is you have additional unofficial repos, possibly ppa.

At any rate, you interrupted the upgrade and the upgrade was in process of removing / installing new packages, ie upgrading. 

Often an interrupted upgrade == problems, in any OS.

So you did a fresh install, and transferred some data. Use 999 == the uid of the user "ubuntu" on the live CD.

So now all you have is a permissions problem.

Depending on the file system, simply

sudo chown 
sudo chmod

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

Of course those commands will not work on every file system , so if you have problems tell us what file system you are using (FAT, NTFS ??? )

I see nothing to suggest a security breach and IMO you are jumping at shadows.

---

### Post by houseworkshy on 2010-05-24
I don't have a clue, however there are several things which may help someone with more knowlage to help.
   
".sudo_as_admin_successful" which is a hidden file in your home directory.
The log files in your System>Administration.
The output from the "finger" amd "netstat" commands in the terminal
A list of browser add-ons
A report from sheildsup.com
A list of your repositories
If used details on setups of "app-armour" and "iptables"
If used details of your wine installation, esp if you have allowed it to have a drive anywhere below home ( that is a default which enables you to use wine from anywhere but I've read a few posts which don't like it for security reasons )
Virtualisations such as VirtualBox may be worth a mention too.
Some tools worth installing and running 
rkhunter
Wireshark
Tyger
ClamAV
Htop
Sysinfo

Some of that lot should be able to gather enough info to enable someone who is an expert security wise to be able to help you.  Good luck.

I was writing while the poster above, who is a wiz on security, was posting.  So it looks like much of my post is invalid.  I'll leave it anyway as some of it may be useful to someone sometime.

---

### Post by eaglemystic69 on 2010-05-24
Thank you for the quick responses.   My internal HD is ext4, and external is NTFS incase I need Windows access.

OUTPUT:
eagle@eagles-laptop:~$ sudo chown
chown: missing operand
Try `chown --help' for more information.
eagle@eagles-laptop:~$ sudo chmod
chmod: missing operand
Try `chmod --help' for more information.
eagle@eagles-laptop:~$ chmod --help

I will do my best to read over the "File Permissions" link sent over.  I did view it before and it was rather foreign to my minimal code ability.  I will see if I am able to apply it.

".sudo_as_admin_successful" was a blank doc.

---

### Post by bodhi.zazen on 2010-05-25
> **eaglemystic69 said:**
> Thank you for the quick responses.   My internal HD is ext4, and external is NTFS incase I need Windows access.

OUTPUT:
eagle@eagles-laptop:~$ sudo chown
chown: missing operand
Try `chown --help' for more information.
eagle@eagles-laptop:~$ sudo chmod
chmod: missing operand
Try `chmod --help' for more information.
eagle@eagles-laptop:~$ chmod --help

I will do my best to read over the "File Permissions" link sent over.  I did view it before and it was rather foreign to my minimal code ability.  I will see if I am able to apply it.

".sudo_as_admin_successful" was a blank doc.

The link I gave you will give you examples of how to manage permissions on the ext4 partition.

The ntfs partition is different. See

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

These are "basic" shell commands.

You can also manage these things with graphical tools.

```
gksu nautilus
``` - use nautilus to set ownership and permissions.

For the ntfs partition, install ntfs-config.

---

### Post by eaglemystic69 on 2010-05-26
Thank U, 

Ur Avatar clearly suits U.  GIU recommended with or other than "[houseworkshy]("http://ubuntuforums.org/member.php?u=807954")".  Either way, I shall discover the still space necessary to concentrate on these Ubu/Linux teachings. . .

---

