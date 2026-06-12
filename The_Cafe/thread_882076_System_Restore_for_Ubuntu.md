---
title: "System Restore for Ubuntu"
date: 2008-08-06
forum: The Cafe
---

### Post by LaRoza on 2008-08-06
I have been working on a system restore program for a while (rather, more like randomly working on whenever I feel bored at night) and I finally got it to the point where I can release it.

It is the first release: [http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

Hope someone finds it useful.

So, next time someone complains of a lack of a system restore program point them to that, and tell them people listen if you complain enough. Now the only question is: "Is it good?"

It works, and was used by me, so it is useful to me.

---

### Post by kevin11951 on 2008-08-06
> **LaRoza said:**
> I have been working on a system restore program for a while (rather, more like randomly working on whenever I feel bored at night) **and I finally got it to the point where I can release it.**

It is the first release: [http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

Hope someone finds it useful.

define... if it works well enough, i will use it, what can it do?

---

### Post by LaRoza on 2008-08-06
> **kevin11951 said:**
> define... if it works well enough, i will use it, what can it do?

It does what I want it to do. I am a programmer, so have zero insight on what the users want so I won't pretend to know ;)

It has a GUI or a CLI, and can make named restore points of system settings (and users can add settings to include). If you try it (the creation of restore points has zero risk), the only change to the system will be a .sysres directory in your home (which you can browse or delete).

I have used it to restore, with no problems, and it uses md5 sums to prevent errors.

---

### Post by fiddledd on 2008-08-06
> **LaRoza said:**
> I have been working on a system restore program for a while (rather, more like randomly working on whenever I feel bored at night) and I finally got it to the point where I can release it.

It is the first release: [http://sourceforge.net/projects/sysres/](http://sourceforge.net/projects/sysres/)

Hope someone finds it useful.

So, next time someone complains of a lack of a system restore program point them to that, and tell them people listen if you complain enough. Now the only question is: "Is it good?"

It works, and was used by me, so it is useful to me.

Don't you ever sleep? :)

---

### Post by Lostincyberspace on 2008-08-06
Does it just compress the system or what?

---

### Post by Dual Cortex on 2008-08-06
You should really describe what it does. What exactly do you mean by "system restore"? There could be a lot of different ways to approach this task.

---

### Post by mc4100 on 2008-08-06
> **Dual Cortex said:**
> You should really describe what it does. What exactly do you mean by "system restore"? There could be a lot of different ways to approach this task.

Just tried it ... it backed up:

/etc/fstab
/boot/grub/menu.lst
/etc/X11/xorg.conf
/etc/apt/sources.list

as specified in the file "list.rules" in ~/.sysres

Edit:
Just had a better look at the Sourceforge page, it's right there:
> It backs up grub settings, repository settings, video settings, and fstab by default.

---

### Post by OutOfReach on 2008-08-06
Cool, I was working on something like this (just for the fun though.), I'll definitely have to try this.

---

### Post by Lostincyberspace on 2008-08-06
Hey LaRoza do you think that in a future version you could have it make a list of installed packages that run, through apt, when you restore so you can get back to a full system quicker.

---

### Post by LaRoza on 2008-08-06
> **Lostincyberspace said:**
> Hey LaRoza do you think that in a future version you could have it make a list of installed packages that run, through apt, when you restore so you can get back to a full system quicker.

Already done: [http://ubuntuforums.org/showpost.php?p=5535477&postcount=78](http://ubuntuforums.org/showpost.php?p=5535477&postcount=78)

It works with sysres, although it is completely separate (it uses the same directory).

It was going to be integrated with sysres, but I abandoned that idea a while ago.

---

### Post by bp1509 on 2008-08-06
d

---

### Post by LaRoza on 2008-08-06
> **bp1509 said:**
> What seperates this from TimeVault?

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

Depends for Timevault: python, python-gnome2, python-glade2, gksu, sudo, nautilus, gnome-terminal, python-nautilus, python-notify, python-gobject, python-gobject-dev, libpango1.0-0

Depends for sysres: python, python-tk (not needed to use cli)

sysres is meant to be a system restore program, not a generic backup program.

---

### Post by Lostincyberspace on 2008-08-06
well from what I can see the back up works fine now I just need to have a reason to install again to test the restore.

---

### Post by LaRoza on 2008-08-06
> **Lostincyberspace said:**
> well from what I can see the back up works fine now I just need to have a reason to install again to test the restore.

Your home needs to be reachable for it to work, that is where it stores its list. ~/.sysres

---

### Post by Lostincyberspace on 2008-08-06
I have a separated /home partition so no worries. 

Don't you think 2 weeks is getting a little long for an Ubuntu install.

---

### Post by LaRoza on 2008-08-06
> **Lostincyberspace said:**
> I have a separated /home partition so no worries. 

Don't you think 2 weeks is getting a little long for an Ubuntu install.

Oh, that would work (you can also copy the directory, as it doesn't get that big even with hundreds of restore points)

2 weeks? What do you mean? I only install when I want another version or distro.

---

### Post by tom66 on 2008-08-06
Looks good. I might use it.

I could see this being a potentially useful feature for Intrepid or a later version. Maybe a cron which makes a backup every day or so and then if Ubuntu detects a problem it can give the option to restore. Also, perhaps on each major change, or if a change is logged, then a backup could be made at that point.

---

### Post by LaRoza on 2008-08-06
> **tom66 said:**
> Looks good. I might use it.

I could see this being a potentially useful feature for Intrepid or a later version. Maybe a cron which makes a backup every day or so and then if Ubuntu detects a problem it can give the option to restore. Also, perhaps on each major change, or if a change is logged, then a backup could be made at that point.

I don't like things being automated.

I don't like the auto restore points in Windows (they take up so much space). 

This can be used in any Linux (if it doesn't have the files, they can be easily changed.) There is a list in the code, system_restore.py, that has the list and it can be changed easily (remember to wipe settings using advanced)

How many times does one change these settings? sysres can be used to backup random files, but I don't know why it would be used that way.

---

