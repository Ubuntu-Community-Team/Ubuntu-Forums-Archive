---
title: "Help me decide - to Jackalope or not to Jackalope"
date: 2009-04-26
forum: The Cafe
---

### Post by samjh on 2009-04-26
I'm having a crisis... a geek crisis.  I can't decide whether to install Jaunty. :p  Usually I'm pretty decisive about everything, but I'm torn on this one.

Right now, I'm running a very well-setup Debian Lenny system.  Reliability-wise, it has been faultless.  It's fast and efficient.  I have it customised exactly as I want, including hand-installations of newer software to replace the obsolete ones from Debian repos.

But should I switch back to Ubuntu and install Jaunty?

I run a production system for work and study, so it needs to be reliable (no weekly crashes, thanks).  On the other hand, I'd like up-to-date Firefox, OpenOffice, and Qt, which Ubuntu provides regularly, but Debian stable does not at all.

I'd also like feedback on how ext4 users are finding their system's performance and reliability.  My filesystems of choice have been ext3 and JFS, and both have served me very very well.  Is ext4 worth the risk of change?

What to do, what to do, what to do? :D  Enlighten me with your collective wisdom!

---

### Post by ad_267 on 2009-04-26
I've had no problems with 9.04+Ext4 so far, and it seems like there's a good speed increase from 8.10. I voted to install 9.04, but if you have a good setup already that you're happy with then there isn't a lot of point in changing that.

---

### Post by wolfen69 on 2009-04-26
i've been running ext4 with 64bit jaunty for about 5 weeks without any issues. runs flawless for me. in fact, it's the best OS i've ever used in 20 years. 

and i could never go back after getting used to the speed increase. i'm spoiled now.

---

### Post by sports fan Matt on 2009-04-26
I dont know if its possible but dual booting?

---

### Post by amac777 on 2009-04-26
I voted to stick with your current setup. Just re-read your post and it sounds clear that what you want is what you have right now. Of course, you could always install Jaunty on another partition to play with and see if it runs just as well. But I wouldn't replace or delete your current Debian system if it's working so well for you.

---

### Post by RichardLinx on 2009-04-26
I'll vote Jaunty. While you may have your Debian system customised just the way you like it, there's no reason why you can't fo the same with Ubuntu. I think your post is  neutral but leans more towards Ubuntu: 
> I'd like up-to-date Firefox, OpenOffice, and Qt, which Ubuntu provides regularly, but Debian stable does not at all.

---

### Post by cmay on 2009-04-26
you should leave your debian intact at all costs.  what is the ultimate solution to your present situations questions and problems  is to buy a new computer which you should jackalope all the way :)

---

### Post by OutOfReach on 2009-04-26
Using Jaunty has been a very very good experience for me, everything is just faster. Ext4 has given me no problems what-so-ever. Jaunty is rock solid and quite possibly the best release of Ubuntu for me, I love it!

---

### Post by Sashin on 2009-04-26
Speed: Jackalope
Stability: Lenny

Both are fast though and both are stable in my opinion. It's just a matter of what you want greater.

---

### Post by telmac on 2009-04-26
DO NOT SWITCH!

atleast for  right now, wait until it is confirmed to work properly.

---

### Post by mohitchawla on 2009-04-26
I have had a few hang ups with Kubuntu 9.04. I am not _completely_ sure if it is KDE or the ext4 file system, but I think its the ext4 system as the system has hung up on me during some file operations with another partition that I have that is formatted as ReiserFS. So, if you plan to have other distros or partitions with other formats on your system along with Jaunty, that might not be a good idea due to limitations posed on manipulating an ext4 partition or manipulating from an ext4 partition. Parted/GParted doesn't have support for ext4 yet...the only way to manipulate ext4 _easily_ is Parted Magic 4.0. So do remember to have Parted Magic with you in case you just might run into some problem. 

So, I would say Jaunty+ext4+Parted Magic live CD is a good _and_ safe option.

---

### Post by samjh on 2009-04-26
Thanks for the advice folks.

I think I'll stick with Lenny for the time being, and trial Jaunty on a VM instead. :)

---

