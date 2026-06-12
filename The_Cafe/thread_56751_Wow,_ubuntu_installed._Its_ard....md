---
title: "Wow, ubuntu installed. Its ard..."
date: 2005-08-13
forum: The Cafe
---

### Post by xequence on 2005-08-13
All of the help sites (including ubuntuguide.org) are very hard and I dont understand them. I have a couple of problems and id like to know if anyone has any answers.

I downloded the java runtime stuff and its a .bin file on my desktop. I tried the thing on the terminal ubuntuguide said, it said:

> patrick@ubuntu:~$ sudo apt-get install sun-j2re1.5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
patrick@ubuntu:~$
patrick@ubuntu:~$
patrick@ubuntu:~$
 

WHat do I do?

ALso I dont know how to access a usb drive. I have it plugged in and I looked all over the places - computer stuff and couldent find it.

I cant wait till I am really good at this and everything is easy :P

---

### Post by BWF89 on 2005-08-13
[QUOTE=xequence]ALso I dont know how to access a usb drive. I have it plugged in and I looked all over the places - computer stuff and couldent find it.[/QUOTE]
The Ubuntu live cd had no trouble finding my 1GB PNY Attache flash drive.

Have you tried going to the foulder that lists all your drives and clicking on the one that's labled "sd1"? I believe sd1 is the USB flash drive.

---

### Post by jerome bettis on 2005-08-13
for java and stuff see here:  [http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

as for the usb thing it really should work.  plug it in and type tail /var/log/messages and see if it says anything about a new usb device connected.

---

### Post by Kyral on 2005-08-13
1) You need the universe enabled. Open a terminal and type sudo gedit /etc/apt/sources.list and then replace the ENTIRE THING with this

 ```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## KDE Repos
deb http://kubuntu.org/hoary-kde342/ hoary-updates main
deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main

``` 

then save it, run "sudo apt-get update && sudo apt-get dist-upgrade" to update the list and also grab the updated stuff from the Backports (Its nice stuff!) THEN do the sudo apt-get install sun-j2re1.5

Oh, don't worry about the breezy deb-src. Those won't take effect unless you decide to build stuff from source, which you shouldn't do for a while :D

---

### Post by drummer on 2005-08-13
[QUOTE=xequence]All of the help sites (including ubuntuguide.org) are very hard and I dont understand them. I have a couple of problems and id like to know if anyone has any answers.

I downloded the java runtime stuff and its a .bin file on my desktop. I tried the thing on the terminal ubuntuguide said, it said:

 

WHat do I do?

ALso I dont know how to access a usb drive. I have it plugged in and I looked all over the places - computer stuff and couldent find it.

I cant wait till I am really good at this and everything is easy :P[/QUOTE]
 To install java you must first enable the extra repositories for Ubuntu as per the Ubuntu Guide ( [http://www.ubuntuguide.org#extrarepositories](http://www.ubuntuguide.org#extrarepositories) ). Make sure that you read the first steps/note of each set of instructions:
Q: How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox?
1. Read General Notes
2. Read How to add extra repositories?  <-----
...

---

### Post by xequence on 2005-08-13
> THEN do the sudo apt-get install sun-j2re1.5

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

Same thing :(

> Have you tried going to the foulder that lists all your drives and clicking on the one that's labled "sd1"? I believe sd1 is the USB flash drive. 

You mean places - computer? It shows floppy drive, cd-rw drive, filesystem

---

### Post by aysiu on 2005-08-13
Are you sure you did 

*sudo apt-get update*

before trying to install Java?

In fact, use Synaptic Package Manager (System > Administration) instead. That's the graphical version of apt-get.

Load it up.
Click "Reload."
Click "Search."
Search for Name and Description (not just Name).
Then search for *java*.

What pops up?

---

### Post by aysiu on 2005-08-13
[QUOTE=xequence]
You mean places - computer? It shows floppy drive, cd-rw drive, filesystem[/QUOTE] In the computer > filesystem, browse to the folder called /dev after you've plugged in your USB drive. What shows up in that folder?

---

### Post by poofyhairguy on 2005-08-14
[QUOTE=xequence]
ALso I dont know how to access a usb drive. I have it plugged in and I looked all over the places - computer stuff and couldent find it.[/QUOTE]

Look under "computer" under the "places" menu. Is it there?

---

### Post by xequence on 2005-08-14
> Look under "computer" under the "places" menu. Is it there 

Nope. My mp3 player is a flash drive, so I can store data on it. In windows it plugged in and there were two seperate drives. (Its odd, but my mp3 player has two 512 MB memories in it.)

> In the computer > filesystem, browse to the folder called /dev after you've plugged in your USB drive. What shows up in that folder? 

A couple folders (evms, input, fd, loop, pts, mapper, net, shm, snd, video1394) and a whole bunch of different things that have icons that look like computer chips, hardd rives, a bomb, and a pipe.

ANd on the screen of my mp3 player it says "CONNECT" like it always does whenever I plug it in.

EDIT: Wait, USBDISK just popped up =O It is one of the flash memories. I think the first one. Its also on my desktop =O NOw just to be able to access the second memory in it :P

---

### Post by varunus on 2005-08-14
For java (and most programs) to work you need to enable something called the "extra repositories."  It seems you haven't done this yet; someone above was showing you how to.  For posterity, I'll show you how as well.

First of all, open the Text Editor (Applications->Accessories->Text Editor).

In the new file, paste the following:
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Multiverse repositories
 deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

## Hoary Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

 deb http://security.ubuntu.com/ubuntu hoary-security multiverse
 deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

```

Next, save that file as "sources.list" on your desktop.

Then, open up a terminal (applications->system tools->terminal) and type the following commands:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.old
sudo mv ~/Desktop/sources.list /etc/apt/sources.list
sudo apt-get update
``` 

What this does, summarized:

Ubuntu uses something called a repository to install software.  People have kindly posted up more than 16,000 programs for you to use; and Synaptic Package Manager will set up any program you want for you.  However, you have to tell your computer where to look for software; that's what we just did with the "sources.list" file.  You set up a list of sources for synaptic to get software from.  The "apt-get update" command is the console equivalent of pushing reload in the package manager.

Install all software you need from the package manager; its much cleaner and much much nicer than the installer-based system.  Everything from one place!

After you do these commands, open Synaptic by going to "system->administration->synaptic package manager".  Click search, and search for "sun".  You should see the sun-j2re package show up.  mark it for installation, and click "apply" at the top.  Let synaptic do its thing (it might complain about non-authenticated packages, these are just the community-contributed ones, don't worry) and you'll have java!

This should be how you install all of your programs; after doing the repository step above, you can just open synaptic and get them for most things.

"sudo apt-get install packagename" is the same thing as going to synaptic and installing a package; it just uses the terminal instead, and is therefore easier to put in the ubuntuguide.

---

### Post by xequence on 2005-08-14
THank you very much, I think it worked =D It didnt do any errors putting the code in and synaptic is downloading it right now :)

---

### Post by xequence on 2005-08-14
Well, I think ive sort of got the hand of it! NOw that I know how to use synaptic and the reposititry thingys are working I am pretty much set =D Hopefully :P

---

### Post by cowlip on 2005-08-14
Hi, I would just like to recommened you a guide to Linux.  It is helpful to understand the command line.

[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

---

### Post by xequence on 2005-08-14
Thank you :) Ill read it now.

---

