---
title: "The Ultimate Ubuntu Server Project :)"
date: 2014-01-30
forum: Server Platforms
---

### Post by ally2 on 2014-01-30
Hello guys so I have some free time on my hands, And I want to give something back to the community as a way of helping newbies I am a newbie myself I have quite alot of free time on my hands so figured over the course of the next few days I will attempt to setup a Ubuntu Server with the eventual aim of documenting everything I do and publishing it through a WordPress blog. Little bit of history about my capabilities and experience I have dabbled with various Linux distributions over the last few years as a hobby am pretty competent at using the BASH shell am not afraid to get my hands dirty and with the aid of the wealth of knowledge from you kind people hopefully I gain reach the goal of documenting everything as a means of giving something back.

So I will lay out the initial steps of the configuration I have in mind I will be working virtually so will be using small partitions to get a feel now I will underline the goals below please comment on the best approach to get things configure and criticize or direct me in the right way.


1) Initial installation I will be using Ubuntu Server with 3 separate hard disks ( small sizes 8 Gigs) in a virtual configuration, I was thinking of having one for the Main O/S layout and 
    and having the other two in some form of raid or a LVM configuration so that I can document how to work with LVM's / Raid good idea? please suggest a better suggestion if I am
   going about this wrong.

2) Ok so once the installation is complete I would like to have the option of installing a GUI now I am thinking something lightweight LXDE or Gnome 2

3) Once the GUI is installed I want to be able to access the server remotely so will need to configure SSH and want to learn and document how to secure it same for VNC

4) FTP configuration was thinking of setting up proftpd or vsftpd i'm not sure which one to go with? basically would like to document the steps to setup a FTP server, secure it and
    be able to access the FTP shares and upload files from Windoze boxes on my network.

5) SAMBA configuration I was thinking of using the second hard disk as a Data share, So I will need to learn how to setup shares things like Music / Movies I would like to learn how
    to implement security and authentication tbdsam back-end the best approach?  will also need to learn how to mount Samba shares in Fstab and also wouldn't mind looking at 
    alternative configuration methods such as SWAT as a means of documenting for newbies if they do not feel comfortable using the Command line.

6) Some way of backing up the data of the Samba share from the second hard disk to the third hard disk either by tar or rsync and documenting how to use crontab is there a better
    approach? 

7) Setting up a Torrent server in which I can manage downloads remotely suggestions? 

8) Setting up a Apache web server and hosting blog 

9) Securing the system 

10) Basic Bash scripting introduction and maybe putting some useful scripts to work on the system and documenting them for other users 

11) System monitoring tools and hard disk monitoring tools 


Those are my initial goals like I said I have alot of time on my hands and wish to give something back to the members of the community I am dedicated to the cause and my goal is to setup a hub where people who are new can follow my work and learn more about Ubuntu Server. 

Feel free to comment back and suggest ideas to me like I say this is all new to me and will be a exciting journey :)

Many Thanks For Your Help 


:)

---

### Post by rubylaser on 2014-01-30
Hello, and welcome to the forums! I think your goals are admirable, but if you want to help out, ensuring that the things you are setting up are documented in the [community wiki]("https://help.ubuntu.com/community/") is a great way to give back. Many of the things you mentioned are already documented there. 

In regards to your steps, you can skip steps 2-4, and just install Ubuntu Deskop with SSH and use SFTP to not need vsftpd either. If you are going to install a GUI anyways, there really isn't much of a reason to go with the Server version IMO. With Ubuntu Desktop, SAMBA sharing is as easy as right-clicking on the folder and sharing it like Winders. All the rest are pretty straightforward and can be setup with some simple Googling.  If you really want to "learn" how these things work, I'd encourage you to use SSH and the CLI.

---

### Post by ally2 on 2014-01-30
Lets get hardcore :) the GUI stuff can wait for a later date, I will be going in command line only anything you would change? Regarding the partition scheme? I want to be able to get a feel for LVM and Raid, 

Once the project gets underway and I start the documentation process I will submit it for changes / improvements

---

### Post by CharlesA on 2014-01-30
> **rubylaser said:**
> Hello, and welcome to the forums! I think your goals are admirable, but if you want to help out, ensuring that the things you are setting up are documented in the [community wiki]("https://help.ubuntu.com/community/") is a great way to give back. Many of the things you mentioned are already documented there.

+1. 

> In regards to your steps, you can skip steps 2-4, and just install Ubuntu Deskop with SSH and use SFTP to not need vsftpd either. If you are going to install a GUI anyways, there really isn't much of a reason to go with the Server version IMO. With Ubuntu Desktop, SAMBA sharing is as easy as right-clicking on the folder and sharing it like Winders. All the rest are pretty straightforward and can be setup with some simple Googling.  If you really want to "learn" how these things work, I'd encourage you to use SSH and the CLI.

Agreed. Personally, if this is going to be a server, it shouldn't need a GUI (IMHO). SSH access would work for.

---

### Post by rubylaser on 2014-01-30
> **ally2 said:**
> Lets get hardcore :) the GUI stuff can wait for a later date, I will be going in command line only anything you would change? Regarding the partition scheme? I want to be able to get a feel for LVM and Raid, 

Once the project gets underway and I start the documentation process I will submit it for changes / improvements

Sounds like a good plan :)  If you are going to try this in a virtual machine initially (I would encourage that), I would make myself a few similar sized disks and try the popular solutions.  mdadm RAID1 for boot, LVM with mdadm, ZFSonLinux, or even SnapRAID.  There are alot of neat tools on Linux and each is suited for a task, so it's nice to try things out so you can pull them out of your toolbox later when needed..  Another thing you could learn about is virtualization with a hypervisor like KVM.

---

### Post by Doug S on 2014-01-30
> **rubylaser said:**
> Hello, and welcome to the forums! I think your goals are admirable, but if you want to help out, ensuring that the things you are setting up are documented in the [community wiki]("https://help.ubuntu.com/community/") is a great way to give back. Many of the things you mentioned are already documented there.Please also consider to contribute via the [Ubuntu Serverguide project]("https://wiki.ubuntu.com/DocumentationTeam/SystemDocumentation/UbuntuServerGuide"), which is in dire need.

---

### Post by ally2 on 2014-01-31
Ok so I have three Small Hard Disks SDA, SDB, SDC each disk is 10 gig in size

I am looking at finding a suitable partition layout scheme for a server so far I have 

SDA

/boot 200MB
/ - 4 Gig
/home - 4 gig ( will be shared out via Samba)
Swap - remainder of disc

Questions I have are below

1) Is this a good partition layout for a server if not why not?
2) I was thinking of having the above layout setup in Raid1 mirrored to SDB good move?
3) I want to incorporate LVM in the future in the tutorial to show people how to get it up and working
4) I was thinking of backing up the contents of SDA+SDB to SDC through rsync good move? 

How would you improve the above? and how do you layout your server configs break it down on a noob level for me :)

---

