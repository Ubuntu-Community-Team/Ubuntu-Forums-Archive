---
title: "WindowsXP/virtual box"
date: 2012-09-08
forum: Virtualisation
---

### Post by hodag on 2012-09-08
I'm now attempting to get WindowsXP working in the virtual box under Ubuntu 10. Is there anyone around that has some knowledge of this? One problem I've had is that the windows emulation won't talk to the outboard USB 2000 gig drive. I need a way around that issue.

---

### Post by idoitprone on 2012-09-08
> **hodag said:**
> I'm now attempting to get WindowsXP working in the virtual box under Ubuntu 10. Is there anyone around that has some knowledge of this? One problem I've had is that the windows emulation won't talk to the outboard USB 2000 gig drive. I need a way around that issue.

Did you install guest addons?
devices -> usb device -> drive

It should show up in windows xp

---

### Post by anewguy on 2012-09-08
And.....while I personally haven't run into a need for it lately with my XP VM in virtualbox, it is also possible to add filters for usb devices specifying if they can be accessed, etc.  It used to be if you just created a new "rule" with nothing it that it would allow any USB device.

---

### Post by coldraven on 2012-09-08
Did you install VirtualBox from the Software Center or from the Vbox web-site?
It used to be the case that for USB support you need the version from the web-site. (plus the Guest add-ons)
I'm not sure if this is still true

---

### Post by hodag on 2012-09-08
Educationally challenged: mild autistic (Aspergers), 72+ yrs old , memory shot to smithereens, mental processes cluttered and worthless.  I did not install anything on this machine, someone else did. Someone who declines to help me now. I don't know where the Vbox software came from. Nor why it won't see/talk to the outboard drive. Nor how to add the Network folders so they show up on under the Vbox such that I can access the data I need to. Think of me as an absolute beginner with a load of very bad habits to unlearn and a kinky way of looking at things that doesn't help. 

That's why I am here: to unlearn so I can learn (if possible).

---

### Post by hodag on 2012-09-08
> **idoitprone said:**
> Did you install guest addons?
devices -> usb device -> drive

It should show up in windows xp

It ain't there... so where do I get it? For Ubuntu 10.04, if possible...

---

### Post by idoitprone on 2012-09-08
> **hodag said:**
> It ain't there... so where do I get it? For Ubuntu 10.04, if possible...

srry that wasnt for guest addons

that the steps to emulate the usb port

device-> install guest addons

to install guest addons

shutdown machine

device->usb device-> choose you usb

---

### Post by hodag on 2012-09-09
Dunno what was done by my partner in the last 24 hrs, but now from the virtual box I have access to the outboard USB device as well as the network, only why is my desktop's lower menu bar a good inch up from the bottom of the screen and sort of centered? Shouldn't it be at the bottom of the screen and all the way across? Can't find how to put it where I think it should be. It's as distracting as heck to an elderly autistic user (ME!)...

---

### Post by pqwoerituytrueiwoq on 2012-09-09
> **hodag said:**
> It ain't there... so where do I get it? For Ubuntu 10.04, if possible...you have to add /media as a shared folder in 10.04 with the stock virtualbox version

---

### Post by afz12 on 2012-09-10
I have several XP machines running under Ubuntu 12.04 (also on previous versions). There is a trick to it - nothing to do with filters. There is a file where you need to add your name to vboxers. I forget where but I'll track it down - it may be in etc?

Your name goes in the last line of the file. After this, USB works fine.

Also if you have a SD drive, this may work without the addition. You could use this as a test for correct functionality.

Once the USB connects then pen drives or USB hard drives should be OK. My notebook, after adding my name and not before, works well - I've tested it up to 500 GB USB hardrives of 3 different brands. Hope this helps - others may know the file name and position anyway!

---

### Post by afz12 on 2012-09-10
hodag

I found it

Here is the sequence that worked for me (on 2 Ubuntu machines, etc)

step 1 - open a terminal and type, with your login name "yournamehere" as below
sudo usermod -a -G vboxusers yournamehere

step 2
look in your files to /etc/group
group is a fine, click to open it and you will see a list of text commands
go to the end of the text file "group"

ensure the last line reads
vboxusers: x : 125 : yournamehere

step 3
See if the USB works now, if not reboot.

I don't know what any of this means - I just followed instructions from some time back. Good luck!

---

### Post by hodag on 2012-09-10
Thanks, you're great, but. . . 

my /usr/local/etc dir responds to 'ls -l' with 

total 0 

I could enter 'md group', but then what da heck to do I do?

not even gotten to the question of how to tell VirtualBox to let me use a system CD drive so as to install a windows app's installation disc...

---

### Post by afz12 on 2012-09-10
Hi hodag

I think you are looking in the wrong place. /etc begins at the root of your directionary structure. Open File System and select the directory named

etc

i.e. the is /etc, not some other version nested down many other layers as you have

Click to open this, and you will see more directories, followed by a list of file. THere should be about 50 of each. You need to scroll down to the file named group.

These files don't have extensions but look very different from directories.

Click on group and it will open. The line comments will look like the following

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
and so on. Scroll to the last lines

yournamehere:x:1000:
sambashare:x:124:yournamehere
vboxusers:x:125:yournamehere

yournamehere is the first name you used when you installed Ubuntu, this is automatically generated when you enter your full name. It might be fred for example, if your full name was fred hyperguru for example

This should just be a check, as the terminal comment listed previously should have generated the last line anyway - this line makes USB work for any Virtualbox OS you want to instantiate.

This should work. It's an unfortunate hassle as much earlier versions of Ubuntu didn't need this carryon.

As for the CD - this step is extremely easy in Virtualbox. Open SETTINGS - probably right click on the XP OS and you weill see General, System, Display, Storage etc. Open Storage. You will see IDE Controller. Under this is XP 250 GB Dynamic ... (my example 1) and then Another thing. Look across to Attributes and there is a symbol to change drive from Virtual to CD/DVD Drive. Select this and then tick the box called Passthrough. This should make CD and DVD drives work regardless of Ubuntu settings.

If this still doesn't work I wonder if you have the correct version of Virtualbox? There are 2 - the proper one and a useless DUD. To be sure you don't get the lemon, I'd download the latest version directly from the Virtualbox site and also the extension pack. Virtualbox will install easily if you use the Ubuntu Software Center option. The you install the extension pack using Virtualbox as the install with option.

From memory the DUD version is something like an OSE and it never works - it looks like it does until you do something like USB.

If this still doesn't help, I suggest you post on the absolute beginners forum as there are people there far wiser than I in the ways of Linux. I only know what works on notebooks I use. Just because it's a Virtualbox question shouldn't matter but it's worth a shot anyway.

Good luck

---

### Post by hodag on 2012-09-13
> **afz12 said:**
> 
snip 

Also if you have a SD drive, this may work without the addition. You could use this as a test for correct functionality.

snip



What are "SD" drives?

---

### Post by BlinkinCat on 2012-09-13
[http://en.wikipedia.org/wiki/Solid-state_drive](http://en.wikipedia.org/wiki/Solid-state_drive)  -  ;)

---

### Post by afz12 on 2012-09-13
Sorry - SD was just meant to refer to a plug in memory card like a USB stick. These are used in cameras to record pictures. They have capacities from about 4 GB to 32 GB and transfer rates up to about 22 MByte / second - a bit slower than a good USB stick. The other use for "SD" refers to an internal solid state replacement for a hard drive - these let the computer/notebook wake up a lot faster than mechanical hard-drives. SD slots are fairly popular in notebooks these days and Virtualbox tends to see them as a "shared folder" rather than a USB item.

---

### Post by hodag on 2012-09-15
> **afz12 said:**
> Sorry - SD was just meant to refer to a plug in memory card like a USB stick. These are used in cameras to record pictures. They have capacities from about 4 GB to 32 GB and transfer rates up to about 22 MByte / second - a bit slower than a good USB stick. The other use for "SD" refers to an internal solid state replacement for a hard drive - these let the computer/notebook wake up a lot faster than mechanical hard-drives. SD slots are fairly popular in notebooks these days and Virtualbox tends to see them as a "shared folder" rather than a USB item.

Ah. Well, this isn't a notebook nor laptop system, but I have never looked all that closely at the hardware end of things. That's the purview of my partner who deals with the domain server and the hardware and operating system software of all of our in-house systems, the lan and so on. He's the one who dragged me, kicking and screaming, into this Ubuntu system. He chose the hardware of our 1st home system and more or less keeps up with the pulse of the industry changes. 

Me, I try to stick as long as possible with software I am very familiar with, even when the original creators no longer support it. And that's sometimes because despite the bells & whistles software creators add to some applications, they destroy others which I find more valuable than the new stuff they add. 

I'm still looking for a sort program as flexible as the one I first used in the 60's, and hanging on as hard as I can to my Dos based Wordstar 4 because none of the new word processing apps I know of can highlight and move whole columns of data within a text file. I have done a lot of manipulation of pure text files, mostly with grep and/or Wordstar before creating the html files for my website. Not that we get a lot of honest-to-gosh users instead of hacking attempts.  

Well, my initial problem seems nicely solved now so I'll go back to lurk mode for a while, folks. 

Thanks for all the help.

---

