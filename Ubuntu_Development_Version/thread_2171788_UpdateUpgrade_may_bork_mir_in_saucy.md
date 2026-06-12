---
title: "Update/Upgrade may bork mir in saucy:"
date: 2013-09-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-09-01
I had to comment out   type=unity to get  the upgraded installs to work that were previously working just fine.

[http://ubuntuforums.org/showthread.php?t=2171762](http://ubuntuforums.org/showthread.php?t=2171762)

---

### Post by grahammechanical on 2013-09-03
I noticed this on Friday (I think). It  loaded in low resolution mode. Only it either never got to the log in screen or if it did let me log in it went to a black screen. Still happening today. I used Recovery mode to update but I cannot get to a working desktop even using Resume.

On Friday I put in a new Saucy install on Ext4 and then installed unity-system-compositor and I was unable to load that to a desktop.

I am now back to using Raring for a bit. I am going to leave unity-system-compositor on there and see if it is corrected by an update. X-mir was looking good and giving optimistic impressions for Mir but things are not looking so good now. 

I hope the devs do not get some nasty surprises when the release candidate ISO images are tested.

Regards.

---

### Post by lonniehenry-gmail on 2013-09-03
I have found that the libmirclient2, libmirplatform, libmirprotobuf0, and libmirserver1 appear in the repos first and synaptic will let you update them immediately without warning that you should wait for the unity-system-compositor to have the same version number.  If they do not match, it will bork the system.

---

### Post by ventrical on 2013-09-03
> **grahammechanical said:**
> I noticed this on Friday (I think). It  loaded in low resolution mode. Only it either never got to the log in screen or if it did let me log in it went to a black screen. Still happening today. I used Recovery mode to update but I cannot get to a working desktop even using Resume.

On Friday I put in a new Saucy install on Ext4 and then installed unity-system-compositor and I was unable to load that to a desktop.

I am now back to using Raring for a bit. I am going to leave unity-system-compositor on there and see if it is corrected by an update. X-mir was looking good and giving optimistic impressions for Mir but things are not looking so good now. 

I hope the devs do not get some nasty surprises when the release candidate ISO images are tested.

Regards.


Thanks for you reply.
 It was a real surprise for me and I initially thought I had fried my two nVidia graphics adapter cards while overclocking @ speeds above 4GHz. Then ,after after zsyncing the daily, I re-installed and ended up with another useless facsimile  of an .iso. I would not think at first that unity-system-compsitor would have anything to do with the wierd lightdm/logon bug so I went to:

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

 and commented out mir and all is running well now.

---

### Post by ventrical on 2013-09-03
> **lonniehenry-gmail said:**
> I have found that the libmirclient2, libmirplatform, libmirprotobuf0, and libmirserver1 appear in the repos first and synaptic will let you update them immediately without warning that you should wait for the unity-system-compositor to have the same version number.  If they do not match, it will bork the system.


 I was originally going to make this post as a warning post but I don't want to sound too controversial in these difficult times of ... err .. umm, development and transition..:) lol

regards..

---

