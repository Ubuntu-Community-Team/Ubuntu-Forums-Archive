---
title: "Install base system fails on 10.04"
date: 2011-02-26
forum: Server Platforms
---

### Post by ubinoobie on 2011-02-26
Hi - complete ubuntu NOOB here - my uncle got me into trying out ubuntu and i'm trying to build a web server but I keep having a problem.  Everything loads fine until I get to the "Install base system" part of the installation and it puts up a red screen warning me that the install has failed.  My uncle gave me his ubuntu discs and even some different hard drives, but I keep getting the same problem at the same point of the installation.

Here is the rundown of everything i did.

System #1 - 
ASUS P5G41-M m/b with 4GB memory
Intel Core 2 quad q9300 cpu
two western digital 640GB hard drives

I was testing it out to run a raid 1 just to learn how to make a software raid array. its my first try at making a raid array.  The first time i used ubuntu server 10.04 32bit and the system failed at the install base system point.  I then used boot n nuke to clean the drives and tried 10.04 64bit.  it failed at the same exact point.

my uncle gave me 2 western digital 1.0TB hard drives and I tried again.  I got the same results.

At that point i gave all the hardware back to my uncle and he gave me a server board to try out because he bought it and hasnt touched it. so I built a second system.

System #2 -
Asus P7F-x server m/b with 8GB of kingstom ecc memory
Intel xeon 3430 cpu
two 1.0TB western digital hard drives

I used the same case and power supply for both systems, but I changed the dvd burner i was using in the 1st system to an older sony cd-rw that i know works from my game rig that i don't use anymore.

so i made sure the hard drives were completely wiped again, started with 10.04 32bit and got the same fail.  i wiped the hard drives again (it takes over 20 hours!) and tried the 64bit and got the same fail message.  I downloaded from ubuntu 10.04.2 64bit and made a new disc (i burned it slow at 16x). i formatted the hard drives again and tried again yesterday and got the same fail message.

i'm not sure what i am doing wrong.  could i be setting up the raid wrong and getting a problem?  after im done formating the hard drives today i'm going to try installing the 10.10 64bit version just to see if i get the same issue.

Any suggestions as to what i am doing wrong?  i feel i've changed the hardware and discs enough to rule out any of them being the problem, so i am at a loss.


Derrick the NOOB

---

### Post by gordintoronto on 2011-02-26
If it were me, I would skip the RAID and get on with it.

I'm not sure what you mean when you say you "wiped the hard drives." Ubuntu can partition and format hard drives during installation, and it only takes a couple of minutes.

I would install the Desktop edition, not the server edition. Having a GUI for web development makes life a lot easier. After installing Ubuntu you can install Apache, mysql and php. You'll also want a backup approach, since you won't be using RAID.

---

### Post by ubinoobie on 2011-02-26
> **gordintoronto said:**
> If it were me, I would skip the RAID and get on with it.

I'm not sure what you mean when you say you "wiped the hard drives." Ubuntu can partition and format hard drives during installation, and it only takes a couple of minutes.

I would install the Desktop edition, not the server edition. Having a GUI for web development makes life a lot easier. After installing Ubuntu you can install Apache, mysql and php. You'll also want a backup approach, since you won't be using RAID.


I am using Darik's boot & nuke to make sure nothing is on the hard drives when I go back to doing a fresh installation.  I know I can just partition the hard drives again but i am trying to do it from a clean install to make sure i'm not having a recurring issue because of old partitions.

as for installing server edition i know i can install the desktop edition but like i stated, i'm trying to learn about software raid arrays.  setting up a web server is the goal but i'd like to do it on a raid 1 array.  I just cannot figure out why i'm having the same issue at the same point of installation on different hardware setups and using different versions of ubuntu.

---

