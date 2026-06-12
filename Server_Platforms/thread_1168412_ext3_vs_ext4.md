---
title: "ext3 v/s ext4"
date: 2009-05-24
forum: Server Platforms
---

### Post by salim.madni on 2009-05-24
dear gurus

can we get any chart,article,documentaion how ext4 is better than ext3.

is before release of ubuntu 9.04, is some also use in any of distribution. is it safe to go live production with this

if we made our partition using ext4, is it more secured,reliable,stable than ext3

we plan to use for email server you suggest advise or shell we just make ext3

any pros and crons we can study reserch, since i need to made report submit to my seniors. 

regards
salim

---

### Post by kerry_s on 2009-05-24
it's still to unstable. google ext4 data loss and you'll see.

---

### Post by salim.madni on 2009-05-24
so using 9.04 safe with ext3 max, right? and using 9.04 with ext4 is very unstable so far yet even final release comes, ubuntu choose as default ext4...can some one share experences of live production and testing results of ext4...highly apprecaited

i found this comments below, from the website 
[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Ubuntu 9.04 and later include ext4 as a manual partitioning option at installation time, including support for ext4 as the root filesystem.

For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this decision for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found here.

---

### Post by mellowd on 2009-05-24
ext3 all the way.

On a production server you always use tried and trusted tech. ext4 is neither yet.

If it were for a home server and you were fooling around then i'd use ext4

---

### Post by koenn on 2009-05-24
> **mellowd said:**
> ext3 all the way.

On a production server you always use tried and trusted tech. ext4 is neither yet.


+1


known poblems :
[http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems)

ext4 is available as an option, but shouldn't be used in production

---

### Post by windependence on 2009-05-24
I'd go one step further and say I'd not use 9.04 in production either. There are still bugs in 8.10. I use 8.04 for any production stuff.

-Tim

---

### Post by koenn on 2009-05-24
> **windependence said:**
> I'd go one step further and say I'd not use 9.04 in production either. There are still bugs in 8.10. I use 8.04 for any production stuff.

-Tim

I'd stick to LTS myself, but that's already being discussed in an other thread : [http://ubuntuforums.org/showthread.php?t=1168454](http://ubuntuforums.org/showthread.php?t=1168454)

---

### Post by Vegan on 2009-05-24
I use a basic LAMP stack so I am fine with 9.04 as indicated in my profile < over there. If you go to my site, that is 9.04 running the standard LAMP stack.

---

