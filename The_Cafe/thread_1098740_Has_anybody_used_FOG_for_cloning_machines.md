---
title: "Has anybody used FOG for cloning machines?"
date: 2009-03-17
forum: The Cafe
---

### Post by Roasted on 2009-03-17
I just wanted to poke my head around here and speak something I came across in case anybody else can benefit from this. I work in a school district and I have a big project coming up where I'm not too sure how our current cloner, which does 5 drives in 45 minutes, will stand up to the magnitude amount of computers we are getting.

As a test I took a spare PC, a P4 3.0ghz with 1gb of RAM and installed Ubuntu 8.10 32 bit on it and set up FOG accordingly to the wiki documentation I found. 

I haven't tested it on multicasting due to the fact I don't have a switch available that has it enabled, but even unicasting seems to be fast.

I searched the forums here to find nobody has really talked about FOG, so I wanted to take my recent discovery of FOG and throw it out here in case anybody else can benefit from it.

Note - They do have a SourceForge Forum, but since FOG is primarily written for Fedora + Ubuntu, I figured I'd mention it here. :)

---

### Post by mips on 2009-03-17
This is the first I have heard of FOG, looks interesting.

Another thing you could look at is CloneZilla although I have never used it.

---

### Post by kevin11951 on 2009-03-17
> **mips said:**
> This is the first I have heard of FOG, looks interesting.

Another thing you could look at is CloneZilla although I have never used it.

+1 for clonezilla, we have been using it for our high school computer recycle project.

---

### Post by Roasted on 2009-03-17
I spent over 4 months trying to figure out Clonezilla Server edition. I use the LiveCD of Clonezilla a lot, but the Server side was just a royal headache.

When I did finally get it working, I successfully cloned a computer, only to find out it did not copy over the MBR properly so my image was useless.

I saw a 20 minute video on YouTube of an unbiased and thorough review of FOG vs Clonezilla, and in the video they even mentioned some users had this MBR problem that I had.

Clonezilla has potential, but it doesn't seem to be worth the headaches I encountered. It took me 4 months to even get it going. It took me 2 hours to have FOG fully functional. Granted, I don't have Wake-On-LAN or the hostname change service figured out, but I'm able to clone computers now after a few hours of reading and installation with FOG.

Nothing against Clonezilla, I really dig their LiveCD. I just found FOG to be much easier with it's web based frontend to manage everything and the ease of installing it. Just make sure you leave the MySQL root PW blank when you install it - I found that out the hard way!

---

### Post by namdung on 2009-05-27
After months of unsuccessful attempts to trying out Clonezilla, I discovered FOG just yesterday. The server was ready within the hour and image deployment within the next few minutes using the following guide.
[http://community.spiceworks.com/how_to/show/373](http://community.spiceworks.com/how_to/show/373) 

FOG is ideally meant to clone Windows images and has several features which will take time for me to learn. 

> Apparently I'm not being able to properly clone Ubuntu images using FOG. I was able to install few Ubuntu images but the rest landed up giving **Fatal Error: Disk Device not found**. Anybody knows how to resolve this?

I'm now able to clone Ubuntu following the post below.
[http://sourceforge.net/forum/forum.php?thread_id=3175814&forum_id=730844](http://sourceforge.net/forum/forum.php?thread_id=3175814&forum_id=730844) 

Will further update.

---

### Post by whitenight639 on 2009-08-18
> **namdung said:**
> After months of unsuccessful attempts to trying out Clonezilla, I discovered FOG just yesterday. The server was ready within the hour and image deployment within the next few minutes using the following guide.
[http://community.spiceworks.com/how_to/show/373](http://community.spiceworks.com/how_to/show/373) 

FOG is ideally meant to clone Windows images and has several features which will take time for me to learn. 



I'm now able to clone Ubuntu following the post below.
[http://sourceforge.net/forum/forum.php?thread_id=3175814&forum_id=730844](http://sourceforge.net/forum/forum.php?thread_id=3175814&forum_id=730844) 

Will further update.

I've in stalled FOG today and im not overly impressed, im getting the same error message but am trying to clone (upload) a windows system with only one partition, I have tried both single fixed partition and the resizable option, I have also tried running fdisk but It dosnt seem to work, also the graphical PXE menu dosnt load for me and lookin in ubuntu /hosts/pxelinux.cfg/default the file looks like its been copied from my windows server as its exacly the same, this confuses the hell outta me. 

My BIOS is abit wierd I can change some setting about the disk but but it makes no difference and also causes windows not to boot so not worth imaging then!

---

### Post by Cheesemill on 2009-08-18
I use FOG as the primary imaging solution in our company (a UK charity) and have done for about 8 months now.
 
Whenever we get a new hardware model in we install XP SP3, Microsoft Office, the FOG service and several custom apps before running sysprep on the machine and uploading it to FOG.
 
Deploying a new machine is then as eay as booting it from the network and selecting 'full inventory and imaging' from the FOG PXE menu, we just enter the required name for the new PC and FOG takes care of the rest. The image takes about 4 minutes to deploy to the machine and then the FOG service renames the machine and joins it to the domain.
 
I've successfully used the multicast option as well for all of our machines at head office, they're all set to WOL and re-image themselves on a Saturday night so we don't have any problems with Windows slowdown or virus nasties (it also taught the users pretty quickly to never save anything on local storage :)). By multicasting in groups I can re-image all 200 machines in 10 minutes!!
 
I've had a couple of problems with hard drives not being recognised, this can usually be fixed by enabling SATA legacy mode in the BIOS.
When this doesn't work I've found that updating the FOG PXE kernel image provides the updated drivers that are needed.
 
Since I started using FOG I must have saved 100's of man hours of Windows installation, not to mention the other benefits such as host inventory, user logon monitoring, scheduled ClamAV scanning and much more.
 
All in all a big thumbs up for FOG.

---

### Post by Roasted on 2010-04-05
After having spoken with more users about FOG, I find several people are skeptical of using it based on the fact they are not that experienced with Linux. Of course, installing it is literally 3-4 commands in the terminal, but some users still aren't entirely comfortable with that.

I ended up throwing together a PDF, explaining in detail how to install FOG on Ubuntu and how to use the basics of FOG. I threw it in a Google Doc and shared it to anyone.

I can't program to save my life, and I feel like open source software has given me so much. I wanted to do what little I could to "give back", so I figured some easy installation instructions promoting the use of FOG (and indirectly, Linux itself) might not be such a bad thing.

Feel free to distribute this doc to anybody who is having trouble installing FOG or is a little skeptical of even trying it.

[http://docs.google.com/fileview?id=0B331nxAPBQEMMTcxY2Y5ZWQtYTI0ZS00YjZmLTk2ZDktNGUxMDFkOGNhOTBk&hl=en](http://docs.google.com/fileview?id=0B331nxAPBQEMMTcxY2Y5ZWQtYTI0ZS00YjZmLTk2ZDktNGUxMDFkOGNhOTBk&hl=en)

---

