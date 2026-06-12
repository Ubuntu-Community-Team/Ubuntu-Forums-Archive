---
title: "Installing Xubuntu in place of Edubuntu on a non-UEFI computer"
date: 2015-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by mattharris4 on 2015-05-20
I have an approximately 8 year old HP desktop with 3.25 GB of recognized RAM and a Pentium 4 3.0 GHz CPU.  This computer has the traditional BIOS in it and not the new UEFI.  I decided today that I wanted to use Xubuntu for a while and see if the stickiness that I had scrolling through webpages with Edubuntu while other tabs were loading (and Ubuntu before it) on some RAM and CPU intensive sites would be less.  hat I was going to attempt to do was install Xubuntu to the root partition as a fresh install while leaving the other partitions alone (everything was backed up before this install).  

When I started the install process I came up on an option to erase the Edubuntu install and install Xubuntu fresh formatting the Ubuntu portion of my hard drive and otherwise reinstalling as if a new install (I don't know if that option will appear on all computers with a current Linux install or what would cause it not to appear).  That option worked as far as using Xubuntu (I haven't attempted to boot into Windows XP yet since the install).  Of course there was the usual install of programs I use, Pepper Flash install and turning the swappiness down from 60 to 5 but that went reasonably well.  The next step is to copy my documents, music, videos, etc. back to my Xubuntu partition. YouTube videos and internet seem to work at least as well as they did in Edubuntu from limited testing since the install.  The stickiness of scrolling through the usual suspect web pages was lessened some but not eliminated.  

Worst case scenario (SFGate.com with eight tabs running) RAM usage dropped from about 2-2.2GB with Edubuntu to about 1GB with Xubuntu.  I am actually getting slightly lower RAM usage here than with my laptop running Lubuntu!  64 bit installs evidently use more RAM than 32 but ones (I had done a limited test on the laptop using a USB and the 64 bit version of Xubuntu, its numbers were slightly higher than Lubuntu's on that computer).  Upon booting Xubuntu is using about 200MB of RAM, with Firefox started and on the landing page (Google) it uses about 300MB.  Making this post with two tabs open I am at about 365MB.  All are lower than my 64 bit laptop running Lubuntu for the same functions and at idle with the desktop Edubuntu was at about 1.1GB, with Firefox idling about 1.4GB and posting on this site about 1.6GB.

I still need to copy documents, music, etc. back to the computer and play some of the music and videos with it as well as attempt an XP boot but so far all is well.  Hopefully all stays well.

---

### Post by mattharris4 on 2015-05-20
I can report that I did not mess up my dual-boot with Win XP by eliminating Edubuntu and installing Xubuntu in its place.  Audio and Video work great although I had to install Rhythmbox in order to play my WMA music files (about 2000 of them).  The default music player does not play WMA files which for me consists of my whole CD collection (as I ripped them back in 2005 on a Win XP computer with Windows Media Player 7 and copied them from computer to computer over the years with a USB stick).  Downloaded music usually comes in the MP3 format which does play on the default music player but that left me only being able to play 1300 of my songs out of approximately 3300 -- which is a no-go for me.  

File transfer from my USB stick to my computer is also faster with Xubuntu, I averaged about 22MB/sec whereas with Edubuntu I was averaging about 11MB/sec.

One funny thing, though.  My Psensor would not register a temperature for my CPU, their website said to install lm-sensors.  After typing in the command and typing yes to several things (I typed no to one that the description it said was risky) I now have Psensor measuring the RPM speed of my cooling fans, three different temperatures (it displays four but one is 32 F which is impossible as my office is about 70 F as I type, I suspect the program as installed on this OS is meant to have four sensors and my computer only has three).  The CPU (I presume) is running around 147 F -- about 64 C (a little hotter than with Edubuntu but still acceptable), there are two other temps running 77 F and 90 F that I cannot identify the source of.  The temp registering at freezing along with one fan speed not registering was easy to eliminate from the display.

For the most part things are working relatively smoothly as it should, with this site up and three tabs the computer registers using 356MB RAM and about 8% CPU on one core and 6% CPU on the other.  Edubuntu registered at least 3 1/2 times the RAM and about four times the CPU usage for the same use.  Maybe I should have did this a few months ago rather than replacing RAM sticks to bring the computer up to 3.2GB of RAM (it originally had 2GB).  It would have saved me $40.

---

### Post by cariboo on 2015-05-20
This really isn't a support question. Moved.

---

