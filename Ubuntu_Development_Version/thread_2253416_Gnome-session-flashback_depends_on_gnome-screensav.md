---
title: "Gnome-session-flashback depends on gnome-screensaver again..."
date: 2014-11-19
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-11-19
Why is gnome-session-flashback dependant on gnome-screensaver once again. This was fixed before and I just noticed it's back when I tried to remove gnome-screensaver.
Grrr :mad:

---

### Post by mc4man on 2014-11-19
Removed - need to ck. something

---

### Post by mc4man on 2014-11-19
Well it seems it comes from the new source of  'gnome-flashback'.  Maybe it needs it or maybe the dep was in the control file & just left there.
(- wasn't gnome-session-flashback previously part of the gnome-panel source? Now it is it's own source...

---

### Post by muktupavels on 2014-11-19
It probably was added back accidentally.

---

### Post by Cavsfan on 2014-11-19
> **albertsmuktupavels said:**
> It probably was added back accidentally.

Thanks for investigating mc4man but Alberts fixed it the first time and he probably has the best insight to what happened.

I tried removing /etc/xdg/autostart/gnome-screensaver.desktop and rebooting but gnome-screensaver still started up.

I hope they will remove it shortly.
Thanks Alberts!

---

### Post by Cavsfan on 2014-11-25
> **albertsmuktupavels said:**
> It probably was added back accidentally.

Alberts, would a bug report help to get the dependency changed to recommends or is that necessary?

Thanks

---

### Post by Cavsfan on 2014-11-25
If anyone is interested in having a working xscreensaver in gnome flashback this will get you there: [http://ubuntuforums.org/showthread.php?t=2186247&highlight=gnome-screensaver](http://ubuntuforums.org/showthread.php?t=2186247&highlight=gnome-screensaver)

I just tried it and it still works.

---

### Post by zika on 2014-11-25
Can You remind as (using gnome-flashback and gnome-screensaver and old enough to not remember what started all this...) what is the problem with gnome-screensaver that You have?

---

### Post by Cavsfan on 2014-11-25
> **zika said:**
> Can You remind as (using gnome-flashback and gnome-screensaver and old enough to not remember what started all this...) what is the problem with gnome-screensaver that You have?

Gnome screensaver is just a lock and not really a screensaver plus it's not being maintained. Xscreensaver is a working screensaver and is maintained. 
I also like Mate screensaver - you can display pictures from a folder that constantly change.
Gnome-session-flashback depends on gnome-screensaver so it gets installed along with flashback and you cannot remove it.

This happened during the Saucy development cycle and was carried over into Trusty. But it was fixed [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)

The problem is back with Vivid and Alberts said in post #4 of this thread "It probably was added back accidentally."

So for now, until the dependency is made into a suggests that is a workaround.

---

### Post by zika on 2014-11-26
> **Cavsfan said:**
> Gnome screensaver is just a lock and not really a screensaver plus it's not being maintained. Xscreensaver is a working screensaver and is maintained. 
I also like Mate screensaver - you can display pictures from a folder that constantly change.
Gnome-session-flashback depends on gnome-screensaver so it gets installed along with flashback and you cannot remove it.

This happened during the Saucy development cycle and was carried over into Trusty. But it was fixed [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)

The problem is back with Vivid and Alberts said in post #4 of this thread "It probably was added back accidentally."

So for now, until the dependency is made into a suggests that is a workaround.Now I remember. &#8222;Only lock&#8220; is very fine with me and that's the reason I do not see any malfunction of Gnome-screensaver. I would not even want it to do anything more. Just lock and blank. And it does. But even without it xset does blank, very fine with me, even lock is (let's say) too much for me. Thank You.

---

### Post by muktupavels on 2014-11-26
> **Cavsfan said:**
> Alberts, would a bug report help to get the dependency changed to recommends or is that necessary?

Thanks

No, it is not needed. Fix should be already in updates.

---

### Post by Cavsfan on 2014-11-27
Thanks for the replies. I seen the fix was in today's updates. I was able to delete gnome-screensaver.

```
gnome-flashback (3.14.0-3ubuntu6) vivid; urgency=medium

  * Move gnome-screensaver from Depends to Recommends.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Wed, 26 Nov 2014 15:08:57 +0300
```

I think this is a positive for those who use screensavers.

---

