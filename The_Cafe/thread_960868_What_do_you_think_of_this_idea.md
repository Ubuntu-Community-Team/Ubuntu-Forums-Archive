---
title: "What do you think of this idea"
date: 2008-10-27
forum: The Cafe
---

### Post by linux_lover69 on 2008-10-27
[[IMG]http://brainstorm.ubuntu.com/idea/14785/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14785/)




There should be an easy and simple way to reset the system settings to the defaults. Like if someone messed up there computer and its being weird because they changed something they shouldn't have. It would be easier to just reset original settings instead of restarting, or finding what went wrong.

Another good idea could be to replace .config files if they are lost or broken without re-installation.

---

### Post by mouseboyx on 2008-10-27
Very good idea, of course it would have to implemented correctly.

---

### Post by linux_lover69 on 2008-10-27
> **mouseboyx said:**
> Very good idea, of course it would have to implemented correctly.

Of course. Im not to good at wording things so it probably doesn't sound as good as it could be.

---

### Post by inxygnuu on 2008-10-27
ta would help so much! i kinda messed with my system a tad, and now a lot of things don't work. Now i have to reinstall Intrepid:(.

---

### Post by init1 on 2008-10-27
> **linux_lover69 said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/14785/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14785/)




There should be an easy and simple way to reset the system settings to the defaults. Like if someone messed up there computer and its being weird because they changed something they shouldn't have. It would be easier to just reset original settings instead of restarting, or finding what went wrong.

Another good idea could be to replace .config files if they are lost or broken without re-installation.
Hrm, maybe it could replace everything except the /home folder. That would probably work.

---

### Post by linux_lover69 on 2008-10-27
> **init1 said:**
> Hrm, maybe it could replace everything except the /home folder. That would probably work.

Like a repair system option?

---

### Post by Ozor Mox on 2008-10-27
This is a good idea, though I don't know how it would be best implemented. The most frustrating thing is when something breaks and you know it is something really obvious and simple to fix but can't find it, so a reinstallation is the only way to sort it out, which feels somewhat like dropping a nuclear bomb to kill a mouse! A feature like this would save me from that pain again!

> Hrm, maybe it could replace everything except the /home folder. That would probably work.

It would have to be a live CD option if it did that wouldn't it?

---

### Post by Bölvaður on 2008-10-27
its good

---

### Post by OutOfReach on 2008-10-27
[Sysres]("http://launchpad.net/sysres") anyone?

---

### Post by linux_lover69 on 2008-10-27
> **OutOfReach said:**
> [Sysres]("http://launchpad.net/sysres") anyone?

yeah thats a nice program. But what if your like me and are too lazy to manually back up. Or forgot to back up?

---

### Post by OutOfReach on 2008-10-27
> **linux_lover69 said:**
> yeah thats a nice program. But what if your like me and are too lazy to manually back up. Or forgot to back up?

You can set a cron job to automatically make a backup every day, hour, week, or month.

---

### Post by linux_lover69 on 2008-10-27
hmmmm. To bad its not installed by default.

---

### Post by OutOfReach on 2008-10-27
> **linux_lover69 said:**
> hmmmm. To bad its not installed by default.

That would be nice if it was. :)

---

### Post by Grant A. on 2008-10-27
> **OutOfReach said:**
> You can set a cron job to automatically make a backup every day, hour, week, or month.

Well, I always find backing things up to another partition or a USB drive/DVD-RW medium the safest way to protect data. I never find those back-up programs useful. Usually they only just stick a .zip in your home folder, which is useless unless it is on another partition/drive.

---

### Post by linux_lover69 on 2008-10-27
So I just downloaded and installed it. And I think its a pretty good program. Its alot faster and better than other backup software. Now only if it had an option to reset my setting to system default.

---

### Post by linux_lover69 on 2008-10-27
> **Grant A. said:**
> Well, I always find backing things up to another partition or a USB drive/DVD-RW medium the safest way to protect data. I never find those back-up programs useful. Usually they only just stick a .zip in your home folder, which is useless unless it is on another partition/drive.

Its just backing up the preferences.

---

### Post by Grant A. on 2008-10-27
> **linux_lover69 said:**
> Its just backing up the preferences.

Still a pretty bad idea to back things up to the thing that you want to back up.

---

### Post by linux_lover69 on 2008-10-27
> **Grant A. said:**
> Still a pretty bad idea to back things up to the thing that you want to back up.

It backs up the 
/boot/grub/menu.lst
/etc/X11/xorg.conf
/etc/apt/sources.list
/etc/fstab

your not backing things up to the thing that you want to back up

---

### Post by Grant A. on 2008-10-27
> **linux_lover69 said:**
> It backs up the 
/boot/grub/menu.lst
/etc/X11/xorg.conf
/etc/apt/sources.list
/etc/fstab

your not backing things up to the thing that you want to back up

You are if you are running on one solid partition, and it back ups the data to $HOME.

---

### Post by linux_lover69 on 2008-10-27
Your Home folder is just part of the user account. If you have two user accounts then you have two home folders. Its backing up settings from the root drive your home folder.

---

### Post by Grant A. on 2008-10-27
> **linux_lover69 said:**
> Your Home folder is just part of the user account. If you have two user accounts then you have two home folders. Its backing up settings from the root drive your home folder.

Which if you happen to be on one partition, the same thing as backing up / to /. You see, if you delete that one partition, your / and your /home dirs are removed, so it negates the effects of back-ups.

---

### Post by linux_lover69 on 2008-10-27
> **Grant A. said:**
> Which if you happen to be on one partition, the same thing as backing up / to /. You see, if you delete that one partition, your / and your /home dirs are removed, so it negates the effects of back-ups.

Yeah but its backing up preferences not files so if you deleted your one partition or / then your screwed. The purpose of the backup is if you messed something up you can restore it to a working state, Not to fix a whole partition.

---

### Post by linux_lover69 on 2008-10-27
Haha I like to argue.   :lolflag:

---

### Post by Grant A. on 2008-10-27
> **linux_lover69 said:**
> Yeah but its backing up preferences not files so if you deleted your one partition or / then your screwed. The purpose of the backup is if you messed something up you can restore it to a working state, Not to **fix a whole partition**.

Would be nice if cron could do that, though. Kind of like what HP computers loaded with Vista do.

---

### Post by linux_lover69 on 2008-10-27
> **Grant A. said:**
> Would be nice if cron could do that, though. Kind of like what HP computers loaded with Vista do.

Yes that would be a nice thing to implement. But how to the HP computers with vista do it? Do they have a separate partition?

---

### Post by porteclefs on 2008-10-27
nah... they just send all of your data to google to pour over ;-)

---

### Post by linux_lover69 on 2008-10-27
> **porteclefs said:**
> nah... they just send all of your data to google to pour over ;-)

Haha I wouldn't dought it.

---

### Post by OutOfReach on 2008-10-27
You can also tell it to backup to another location...

---

### Post by Lord Xeb on 2008-10-27
Do you realize how many times I need this?

---

### Post by ilrudie on 2008-10-28
```
dpkg-reconfigure -a
```

from the man page:

dpkg-reconfigure - reconfigure an already installed package

-a, --all
           Reconfigure all installed packages that use debconf. Warning: this
           may take a long time.


This may not work for *everything* but it should go a long way.  Never tried it myself.

---

