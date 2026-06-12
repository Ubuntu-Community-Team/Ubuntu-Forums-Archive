---
title: "NAS Setup - Ubuntu or FreeNAS"
date: 2011-10-27
forum: Server Platforms
---

### Post by GMHilltop on 2011-10-27
I am looking into setting up a NAS and I have a little bit of experience with the desktop version of Ubuntu but when it comes to the server version I have none.

Can the server version of Ubuntu be used in this sort of application?

FreeNAS is another option that I am looking at, but it and the ZFS file system is completely new to me. (I can deal with that, however I'd like to get the system up and running sooner rather than later).

Is there anyone that may have had experience with both and would care to comment?

Thanks.

---

### Post by rubylaser on 2011-10-27
FreeNAS will better faster to setup initially, but I've never been able to get good transfer throughput out of it.  Ubuntu with mdadm is great and will allow you maximum flexibility down the line.  If you want to try out ZFS, I'd suggest Solaris 11 + napp-it.  It performs much better than FreeNAS and supports much newer pool versions than FreeNAS.

So, in a roundabout fashion, either will work well, and it really depends if performance is an issue and what other services you'd like to provide on your fileserver.

---

### Post by kerry_s on 2011-10-27
Ubuntu server gives more options. you can choose what ever you want, there are a lot of web front ends if you need but most things is just editing a simple text file. 

I mainly use transmission-daemon & samba.

---

### Post by njparton on 2011-10-28
Go for Debian instead, it's more stable and reliable than Ubuntu.  Ubuntu is too cutting edge.

I started out with Ubuntu on my NAS but after several unrecoverable package breakages I switched to Debian and haven't looked back. Other advantage is that most of the guidance here applies to Debian too.

---

### Post by brighty22 on 2011-10-28
I originally had a FreeNAS box, but then converted it to an Ubuntu server. FreeNAS is very much set and forget, and it's worth noting that FreeNAS is a NAS OS, while Ubuntu is a full blown server OS. Despite the small addons, it's still essentially just a fileserver. After I installed Apache and MySQL on FreeNAS (don't ask.. it wasn't pretty) I decided to make the move. FreeNAS is by no means bad, but if you can see yourself wanting any more features in the future, I'd choose Ubuntu server from the outset. Learn some basic cli commands and install OpenSSH.. you'll be amazed.

---

### Post by GMHilltop on 2011-10-28
Nice cross section of comments folks - Thanks!

FreeNAS 8 apparently has been reworked from the ground up.

That is a good thing and a bad thing.

Good ===>  
[INDENT]The intent is to make it modular - kind of like Wordpress or Drupal - you add functionality modules as you need it.

You can boot from a Flash drive (you can do the same with ubuntu)

The ZFS file system and software raid options are quite extensive (not that I know a lot about them, but I am learning)

[/INDENT]Bad ===>
[INDENT]To Run the ZFS file system the recommended hardware requirements for FreeNAS 8 are significant!  (upwards of 1 GB of RAM per TB of storage - with a 4GB [actually 6GB] minimum to start)

Because it is so new, there will be growing pains and I am not exactly sure that I want to be 'experimenting' with something NEW to me (and the world) with data that I am trying to preserve.

[/INDENT]**njparton**:  I am not that familiar with Debian, I'll look, but can you tell me if there is anything special I need to add to make it work as a file server? 

**kerry_s**:  I am not familiar with 'transmission-daemon'.  Where do you get it?  What does it do?

I am new the the 'server' versions of Linux (and Linux in general)

Any quick tips, Pointers, or Links to Straight forward "How To" guides would be great.

Again, Thanks All for the comments

---

### Post by mattlach on 2011-10-28
OP:

You do realize you are posting on an Ubuntu forum, and your responses may be a WEE bit subjective?  :p

> **brighty22 said:**
> FreeNAS is very much set and forget, and it's worth noting that FreeNAS is a NAS OS, while Ubuntu is a full blown server OS. Despite the small addons, it's still essentially just a fileserver. After I installed Apache and MySQL on FreeNAS (don't ask.. it wasn't pretty) I decided to make the move. FreeNAS is by no means bad, but if you can see yourself wanting any more features in the future, I'd choose Ubuntu server from the outset. Learn some basic cli commands and install OpenSSH.. you'll be amazed.

Interesting.   What kind of issues did you have with FreeNAS?    The reason I ask is, I was under the impression it was essentially just a version of Slackware (a full featured linux distribution) that was pre-setup to serve as a NAS.   (I've never used it though so I could be wrong).

Personally, I currently have an Ubuntu Server (10.04 LTS) serving as (among other things) my NAS, hooked up to an external Drobo S.

As time has gone on, I have grown tired of this and wanted to take more control over my drives, so I have just finished building my new server (and I am in the process of setting it up). My intent is to run it with FlexRAID.  I installed Ubuntu Server 11.10 the other day, but I am having some issues with package dependencies.  I can probably work through them, but I am starting to wonder if Ubuntu was my best choice.  (I've been using Ubuntu for several years, and like it, but the last few releases have been a little curious)

Before I ran Ubuntu I was a hardcore Gentoo fan, but I gave up on it due to the high maintenance.  (granted I was running the unstable branch for hardware compatibility, and this is likely why it was high maintenance for me).  I went over there today to check it out, and I'm not sure I have it in me - right now - to revisit Gentoo.   Maybe when I retire (I'm 31 :p ) and have more time again.

Debian is an interesting choice, and one I hadn't given much thought, but I may consider it.

Whichever distribution you wind up with, the easiest and most efficient way to manage it is going to be with no GUI, from the command line.   That way you hide the server in a corner somewhere without a monitor and just SSH in to it to manage it.   If you haven't familiarized yourself with the linux command line, now is a good time to do so, so you are a little more comfortable when you are setting up your server.

---

### Post by GMHilltop on 2011-10-28
Yeah I figured the answers may be a bit jaded, but so far they have been thought provoking :-)

Sounds like either way I go there is going to be a bit of a learning curve with challenges to overcome.

I was sorta hoping to stick with something that is more GUI based as I don't have tons of time to learn command line stuff (love to - time's just not there right now).

Pro Ubuntu or not, Keep 'em coming.  It's giving me some good stuff to consider.

---

### Post by confusedstingray on 2011-10-28
I'm running ubuntu 10.04LTS server
like many people are suggesting using ssh to log in and control it is easy to learn
i have the server running a media server and file server visible to internal networks only.
i started like you are , may i suggest loading webmin which is a GUI and use the ssh as well
this way you can get the cli learning curve going at the same time have gui.  also look at the
website howtoforge.net many step by step tutorials to get you started.

---

### Post by GMHilltop on 2011-10-28
Thanks for the tips confusedstingray - Much appreciated. I'll give it a whirl.

I'm more than happy to have more weigh in on the subject - this has been great !

---

### Post by brighty22 on 2011-10-29
> **mattlach said:**
> 
Interesting.   What kind of issues did you have with FreeNAS?    The reason I ask is, I was under the impression it was essentially just a version of Slackware (a full featured linux distribution) that was pre-setup to serve as a NAS.   (I've never used it though so I could be wrong).

FreeNAS is a watered down version of FreeBSD - it's only something like 40MB when installed - nothing like a server OS. At one point I think the plan was to switch to Debian, but something happened and it's stayed with BSD. Debian is still a very good distro though.

---

### Post by collisionystm on 2011-10-29
> **GMHilltop said:**
> I am looking into setting up a NAS and I have a little bit of experience with the desktop version of Ubuntu but when it comes to the server version I have none.

Can the server version of Ubuntu be used in this sort of application?

FreeNAS is another option that I am looking at, but it and the ZFS file system is completely new to me. (I can deal with that, however I'd like to get the system up and running sooner rather than later).

Is there anyone that may have had experience with both and would care to comment?

Thanks.

Are you trying to do password authentication with your NAS?

Use Zentyal... Best god damn piece of software ever. It can do anything and I cannot stop recommending its use.

---

### Post by aquarius18 on 2011-12-12
> **collisionystm said:**
> ......Use Zentyal... Best god damn piece of software ever. It can do anything and I cannot stop recommending its use.

I have a spare tower (inherited from my neighbour) and rebuilt the box with parts out of another "spare" box. Now I am in the position as **GMHilltop** - use the thing as a NAS for media purposes and storage of docs. 

After reading umpteen posts I too have come to the conclusion to use Zentyal (based on Ubuntu server - latest LTS), so this thread has been very helpful in making a decision ....:guitar:

Thanks guys!

---

### Post by bermshield on 2012-12-18
Hello community,
  Any advices would be appreciated.
  My objective is to build a NAS with media streaming (itv, PS3, picture, music) services, with remote access, and 1 To of memory should be redundant (the rest doesn’t need protection).
  I used to handle HPlinux in an older life but reading the forums make me realise that it's been a while I've been disconnect…
  Anyways: I have 
  [FONT=Calibri]-          [/FONT]Mobo: AMD processor 64 bit,
  [FONT=Calibri]-          [/FONT]RAM : 4Gig
  [FONT=Calibri]-          [/FONT]HD1 : 1x sata 2 To
  [FONT=Calibri]-          [/FONT]HD2: 1x usb external  1To
  [FONT=Calibri]-          [/FONT]HD3: sata 250 Go
   
  1st question:
  Is it possible to have 1 To of RAID 1 volume (using HD2 and half of HD1) +  1.25 To RAID 0 volume (by combining half of HD1 and HD3)?
  2nd question:
  I believe ZFS is overkill for my needs, what formatting should I use then?
  3rd question:
  Any recommendation on ios: Ubunto NAS4Free or freenas 8.3 ?

---

### Post by Pedro72 on 2012-12-19
The following is based on my experience thus far and am in a similar boat to you.

My  first attempt was Ubuntu home server (after desktop experience) and was  in too deep. Command line is ok, but when things didn't work I  installed a GUI, then it didn't feel like a server.
I worked out my partitions were not really set up and a good server should have the partitions set up well. So I cried and looked for an alternative.

I hit FreeNAS and thought wow that was easy. Even getting plugins working is pretty easy. 
Then  I realised I would never run a web server off FreeNAS, and that  accessing from the wider web was insecure comparatively to other  alternatives.

Now, again I am looking at alternatives and  currently considering Ubuntu again (with more experience this time) or  Amahi (to make things easy for me). Or possibly Zentyal or Solaris 11 based on reading some comments.

What  I actually want to achieve is probably quite extensive for a novice and  maybe not in this order; owncloud for access to files everywhere.  Serviio for home media, transmission for downloads and eventually a web  server to host 1, 2 or possibly 3 sites eventually.

So my advice to the topic starter, if you want a NAS, freeNAS is great.
If  you want a server look elsewhere. I am tempted by Amahi to make the  whole process a lot easier for me however I cant see serviio on their  apps which is putting me off. (I know it works with my TV) 
And also I  kind of what to do it myself / fully understand what's going on.

---

### Post by mattlach on 2012-12-19
So, a little over a year later, here is my updated response.

For the longest time I ran an Ubuntu server as a NAS.   I set up SMB manually and it really wasn't bad as long as editing text files from console is an experience that scares you.

Then down the road I installed VMWare ESXi on my server.  (I had to run two different operating systems for something else, and didn't want to buy another server.

I decided to try out FreeNAS as a guest operating system under ESXi.

Let me say this.  FreeNAS is effing brilliant as a ZFS NAS.   Easy to set up and works very well.

The only downsides is that it REALLY likes RAM in ZFS (at least 1GB per TB of drive space + 2GB)and the more you give it the better it works.

I have a total of 12TB of drives in the system, So for me I would consider the minimum 14GB RAM, but I gave it 20GB, because I had it to spare, and the more the better.

For high write speeds, a lot of CPU power can also be needed, but typically for the speeds you are limited to by gigabit Ethernet, any semi-recent CPU you have in your server will likely be sufficient.

What I also learned was that I really don't like the BSD command line.  Sure you can install an alternate shell, but even so the commands use different syntax in many cases than what I am used to, and --help switches are less helpful.   MAN is not installed with FreeBSD either, so no help from manpages.

What I decided to do was to install a small ubuntu server for my general linux server needs as a separate OS under VMWare.   It accesses the FreeBSD storage via a virtual internal 10gig Ethernet connection using NFS.

I do all my typical linux server stuff on Ubuntu server instead, as I am much happier with the command line experience, but all the storage stuff is handled by FreeNAS.

This solution works for me, but is not necessarily entirely straight forward to set up, and will not be for everyone.

It did require me to purchase a motherboard/CPU combo that supported IOMMU/VT-D and a special IBM M1015 storage controller capable of being direct I/O mapped to the FreenNAS guest.  (I also had to flash the controller with a special JBOD IT firmware for it to work properly.

Anyway, these are just some thoughts on this topic.

---

### Post by spynappels on 2012-12-22
Nice update Matt, glad you found a system which worked for you. I agree that the CLI in Linux is much nicer to work in than the BSD one, but I work with several people who feel the exact opposite, so it shows it's a very personal, subjective thing.

I ended up doing something similar, but with a dedicated FreeNAS box providing all the storage for my ESXi server. Isn't it fun getting it all to work together nicely?

---

