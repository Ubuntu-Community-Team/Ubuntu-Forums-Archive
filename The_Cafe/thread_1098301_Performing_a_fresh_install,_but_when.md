---
title: "Performing a fresh install, but when???"
date: 2009-03-16
forum: The Cafe
---

### Post by jreyes33 on 2009-03-16
Hey everyone,

Well, I'm about to perform a fresh install of Ubuntu, I'll install XP and then Ubuntu. The thing I'm not sure about is when should I do this. Should I do it now, or should I wait until 9.04 Jaunty release?

Another question: how should I divide my 100 GB disc (I'll put all my music, videos and documents on the Windows side). Is a 30 - 70 division all right??

Please help me with these issues.

Thanks

---

### Post by MikeTheC on 2009-03-16
Considering we're relatively close to the 9.04 release, you might want to wait.

However, consider that one of Debian's goals has always been to make a reality of smooth, in-place OS upgrades. Ubuntu, being based on Debian, has really inherited this trait in a big way. I've done plenty of in-place OS upgrades with Ubuntu, so I'm reasonably comfortable in recommending it as an alternative.

---

### Post by BGFG on 2009-03-16
I'd wait for jaunty, all indications say it will rock hard. 

As to partitioning, I'd give the XP C drive 15-20 gigs, create a 70 gig ntfs D drive(media dump), then give Ubuntu root or '/' 10 gigs and the rest to /Home. 

reason for the ntfs media dump rather than ext3 is than win cannot read ext3 while ubuntu reads ntfs flawlessly.

Hope this helps man.

---

### Post by jreyes33 on 2009-03-17
Thanks both of you. So I've made my mind and I'll patiently wait for Jaunty.

I'm sure that's the best option, update from a fresh install.

---

### Post by lisati on 2009-03-17
One further comment: Installing XP before Ubuntu can make the process easier. This is because Ubuntu's installation process copes better with other OSes being on the system than XP's installation.

---

### Post by jreyes33 on 2009-03-17
> **lisati said:**
> One further comment: Installing XP before Ubuntu can make the process easier. This is because Ubuntu's installation process copes better with other OSes being on the system than XP's installation.
Yes, I've read enough about difficulties when installing XP after Ubuntu, so I'll do this the safe/easy way

---

### Post by Therion on 2009-03-17
Another wait for 9.04 vote.  

Yes, it's absolutely going to be worth the wait if my experience with it is any indication of how things are going to be for the general populace.  
Intrepid left me cold but Jaunty is positively rocking my world.

---

### Post by BGFG on 2009-03-17
> **lisati said:**
> One further comment: Installing XP before Ubuntu can make the process easier. This is because Ubuntu's installation process copes better with other OSes being on the system than XP's installation.

BIG plus 1! :) i still have to hit f12 and change my boot drive to get into Xp :) don't much care though. prefer not to have grub littered with...well, you know :P

---

### Post by andrewabc on 2009-03-17
Yep, wait until 9.04 is released. And make sure to install XP before ubuntu.

You may want to try out the alpha6 livecd to make sure everything works.

---

### Post by ghindo on 2009-03-17
Why not install now and just upgrade when 9.04 comes out?

---

### Post by Skripka on 2009-03-17
> **ghindo said:**
> Why not install now and just upgrade when 9.04 comes out?

The one biggy being that a clean install is a clean slate-and has the most potential for things to work just fine .  Upgrading from on version to another has the potential for (more) problems.

---

### Post by andrewabc on 2009-03-17
Maybe use ext4?

---

### Post by Skripka on 2009-03-17
> **andrewabc said:**
> Maybe use ext4?

I'd wait until ext4 has been out a while longer...many of the problems I and others have been seeing with ext4 are due to devs not accustomed to the way Ext4 does things--which can cause (big) problems, such as data corruption.

Ext4 is fast, but it can eat your hampster if you aren't careful.

---

### Post by Bölvaður on 2009-03-17
I wouldn't have /home partition if you have a dedicated data partition.

unless if you are planning on keeping data on the /home partition that you wish to keep when you move to new release of ubuntu (or another distro) and do a fresh install.

if you will have a /home partition remember to delete all the config files that you dont wish to keep (everything except Documents,Videos,Music, Pictures.. and possibly  .thumbs and .icons)...well you'll learn :P Enjoy your stay

---

### Post by billgoldberg on 2009-03-17
> **jreyes33 said:**
> Hey everyone,

Well, I'm about to perform a fresh install of Ubuntu, I'll install XP and then Ubuntu. The thing I'm not sure about is when should I do this. Should I do it now, or should I wait until 9.04 Jaunty release?

Another question: how should I divide my 100 GB disc (I'll put all my music, videos and documents on the Windows side). Is a 30 - 70 division all right??

Please help me with these issues.

Thanks

You have to make up your mind about the when.

Ubuntu can run fine on 5gb, add another 5gb to make some space for extra programs and swap and you should be fine with 10gb for the two Ubuntu partition (9gb for /root and 1gb for /swap).

You could then use 90gb for XP.

If you aren't going to keep stuff on your Ubuntu partition, why would you waste 30gb on it?

---

### Post by jreyes33 on 2009-03-17
> **billgoldberg said:**
> 
If you aren't going to keep stuff on your Ubuntu partition, why would you waste 30gb on it?

Well, I'm sure I'll use Ubuntu almost full time, the Windows partition will be there mostly for gaming. That's why I thought 30 GB would be ok, because I want to install some heavy apps (xbmc, linux games, blender, etc.). You also have the updates coming constantly. Well maybe 20 GB will do it.

One more question, can I resize my partitions later (with GParted), without losing data on any partition?

---

### Post by andrewabc on 2009-03-17
> **jreyes33 said:**
> Well, I'm sure I'll use Ubuntu almost full time, the Windows partition will be there mostly for gaming. That's why I thought 30 GB would be ok, because I want to install some heavy apps (xbmc, linux games, blender, etc.). You also have the updates coming constantly. Well maybe 20 GB will do it.

One more question, can I resize my partitions later (with GParted), without losing data on any partition?

You may want more room. My initial ubuntu partition was only around 10gb. but after doing some work (change mp3 bitrates on lots of files using audacity) I actually ran out of space and got an error. Also if you ever use virtualbox that can take up 1-2gb or more depending on how often used and how many snapshots/virtual machines.

I have /home currently using 9.2gb (of 46gb), and / using 3.68 gb (of 20gb)

I'd give more space for ubuntu partition if it is going to be your main operating system and place to store files.

I havn't tried changing partition size after install. I've only done it after formatting/deleting partitions and creating new ones.

Why not split hard drive in half? 1/2 goes to windows and 1/2 goes to ubuntu? (oops I see you are putting all multimedia on windows partition) 
You should definitely have more than 20gb for ubuntu. Unless you are not planning on saving any files on ubuntu.

---

### Post by Primefalcon on 2009-03-17
wait

9.04 will use the new ext4 file system, so wait till then and do it all fresh with a shiny new ext4 file system

---

### Post by Skripka on 2009-03-17
> **Primefalcon said:**
> wait

9.04 will use the new ext4 file system, so wait till then and do it all fresh with a shiny new ext4 file system

I'd still say to wait on ext4 even then.  DEs and apps are known to get pissy on Ext4 from improper shutdown (i.e. hard power-off or power cut).  

Here's an Archer's wise take on the matter, borrowed from Arch Forums

[QUOTE=Ranguvar]
Just to head this off, because even though that's a good link, it's being misinterpreted by a lot of people: there is _no_ bug in ext4. The problem is that app devs got used to the behavior of filesystems that did not do delayed allocation (which speeds things up), instead of following the POSIX standard. XFS, ext4, and Btrfs now all do delayed allocation. What does this mean? If you want to be sure ext4 will not get all pissy at you when power is cut, add "nodelalloc" to your mount options in /etc/fstab. You'll lose some performance. Blame app devs. Kernel 2.6.30 will include more kludges that hurt performance less with hopefully the same effect.
[/QUOTE]

---

### Post by jreyes33 on 2009-03-17
> **Skripka said:**
> I'd still say to wait on ext4 even then.  DEs and apps are known to get pissy on Ext4 from improper shutdown (i.e. hard power-off or power cut).  

Here's an Archer's wise take on the matter, borrowed from Arch Forums
Yes, I will pass this time from ext4 file system and wait for it to "normalize".

I have to admit that I'm currently running on ext2 due to weird installation problems!

---

### Post by andrewabc on 2009-03-17
> **Primefalcon said:**
> wait

9.04 will use the new ext4 file system, so wait till then and do it all fresh with a shiny new ext4 file system

9.04 will use ext3 by default.
You have to go into manual partition and select ext4 in order to use it.

---

