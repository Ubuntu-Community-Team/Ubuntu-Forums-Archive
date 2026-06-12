---
title: "Simple formatter"
date: 2008-01-05
forum: Ubuntu Brainstorm
---

### Post by xanikseo on 2008-01-05
It's very simple but important - especially for noobs. We need a super-simple formatter. Not like G-Parted which insists on having partitions, but a simple right-click-on-drive-and-select-format-and-then-select-file system-andmaybeallocationsize-and-click-format. It's really tiny, but it means that noobs won't be fiddling around with the terminal and not knowing what they're actually doing.

Unfortunately I can't do this myself because atm I only can write in web languages and bash :(.

---

### Post by autocrosser on 2008-01-05
I second this one---I've posted about this one before:

[http://ubuntuforums.org/showthread.php?t=580757](http://ubuntuforums.org/showthread.php?t=580757)

---

### Post by Ripfox on 2008-01-05
+1

---

### Post by mgw854 on 2008-01-05
Are you suggesting something like the Floppy Disk formatting window in Windows... select a name, a size, a format type, then click on "Format"?  I guess that wouldn't be overly horrible, but think about this from the standpoint of a noob.  They are going to click on it, not knowing what is happening, and could very well format their hard drive.  If we do decide to implement this feature, it should pop up a warning that tells you what formatting your hard drive does, and what you should be ready for.  That's just my feeling on things, anyone want to provide more insight?

---

### Post by ronacc on 2008-01-05
I'll throw in with mgw854 on this one , I'm usualy in favor of making things easy , but in this case with the dammage formating can do I would hesitate to make it too easy . MKFS from the terminal or gparted are not all that hard to use and atleast require you to think about what you are doing .

---

### Post by autocrosser on 2008-01-05
My suggestion was to "fold" gparted & Disk Manager into one app that formats, edits the fstab, assigns UUID's & cleans it all up after similar to MacOS's Drive Utility.

With UUID's now the defacto standard, the normal user has a harder time adding a new drive to the system--what I would like is a "one-stop" app that can be simple enough for the noob & allow a advanced menu for the poweruser.

For more info about Disk Manager:   
[http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/)

---

### Post by Planets on 2008-01-05
> **ronacc said:**
> I'll throw in with mgw854 on this one , I'm usualy in favor of making things easy , but in this case with the dammage formating can do I would hesitate to make it too easy . MKFS from the terminal or gparted are not all that hard to use and atleast require you to think about what you are doing .

That's what warning prompts are for. Inform the user that this process is irreversible and will destroy all data on the disk. The user will much appreciate spending 5 seconds reading 1 or 2 prompts rather than 5 hours restoring his or her data. That's also assuming the data was backed up.

Also, the developers are aiming for Ubuntu to rival Windows, correct? People who use Windows are not going to type anything into a terminal. I am a Windows user, and if Microsoft ever implemented anything which required something to be entered into the command prompt, I'd simply not bother using that feature.

---

### Post by ronacc on 2008-01-05
yes that would be a good addition  , what I was concerned about would be a one click ohsh*** . adding insult to injury if you use hardinfo to find the uuid of a partition it is listed twice with the first one you come to having the dashes ( - ) transliterated to underscores ( _ ) which of course is the WRONG format for fstab or grub you need to use the uuid the way it is shown all the way at the bottom of hardinfo , that is an unforgivable builtin boobytrap .

---

### Post by ronacc on 2008-01-05
> **Planets said:**
> That's what warning prompts are for. Inform the user that this process is irreversible and will destroy all data on the disk. The user will much appreciate spending 5 seconds reading 1 or 2 prompts rather than 5 hours restoring his or her data. That's also assuming the data was backed up.

Also, the developers are aiming for Ubuntu to rival Windows, correct? People who use Windows are not going to type anything into a terminal. I am a Windows user, and if Microsoft ever implemented anything which required something to be entered into the command prompt, I'd simply not bother using that feature.

you really should learn to use the terminal a little bit , it really is a better and quicker way to do some things. not for everything , no , I love gui's too but for some things the terminal is very handy. and btw there is a terminal in windows and you can do somethinngs with it that you cant from the gui .ms just don't tell you about it.

---

### Post by Planets on 2008-01-05
My point is the average user won't bother using the terminal. If Ubuntu targets the average user, then we have a problem.

---

### Post by ronacc on 2008-01-05
and I believe that the "average " user will use the terminal if it isn't made out to be arcane geeks only territory far too complex for the average joe or jane.

---

### Post by maybeway36 on 2008-01-05
I remember a small KDE app called KFloppy. Yes, it's a KDE app, but it would probably be very simple to make a GTK2+ version.

---

### Post by xanikseo on 2008-01-06
To be honest, I haven't really heard of anybody who uses Windows complaining that they accidently formatted something or other and that they lost a lot of data - and that's people who probably didn't install Windows and don't know anything or at least not that much about partioning and formating. 

As far as I remember, in Windows, there's a little warning box that asks if you want to continue.

---

### Post by mgw854 on 2008-01-06
If this box is focusing on less advanced users, I think that we should remove the option to format the boot drive.  Allowing people to just format drives that contain the boot information would be bad, leading to an unusable system.  This is something that should be handled from a more advanced application, or from an OS installer.

---

