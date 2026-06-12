---
title: "home folder as part of install"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by pdlethbridge on 2007-10-20
It would be nice that the home folder stays as home folder on a new install. Unless you catch it at the early part of the install when the partitions are set, it changes its name to something like hda2 and you loose the home folder unless you reinstall

---

### Post by Blackcomb on 2007-10-24
I'm trying to understand the problem. You mean that you have a separated partition for \home, and on a fresh install it doesn't automatically mount the partition to \home again?

in that case, I don't think to automate this in the installation is a useful idea... just set the mount-point in the partitioner and your problem is solved.

on the other hand: how will the installation "know" by itself what partition you want to use as your home-folder? (you're talking about a new installation)

---

### Post by Bou on 2007-10-24
This proposal might be closely related to [this other]("http://ubuntuforums.org/showthread.php?t=584151"). If Ubuntu should create a /home parttion with little to no user intervention, then it just makes sense that it should mount it automatically as well.

> **Blackcomb said:**
> on the other hand: how will the installation "know" by itself what partition you want to use as your home-folder? (you're talking about a new installation)

I think the migration assistant already does. Never actually used it myself, but it seems to identify /home partitions and the users in it. Instead of transferring preferences, files and the like it could just mount it again as /home.

Please,pdlethbridge, do create a spec about this.

---

### Post by pdlethbridge on 2007-10-24
Bou, I appreciate your very well worded answer.
I have loads of time on my hands as I'm retired so if I have a problem with the OS, I'm not afraid to reinstall. Now when you install and after the Language, country and time zone screen there is the partition screen. Now I always manually partition when I install but When the screen comes up to list the partitions, they are not listed as **/ **or **home** but are given **sda1** or something similar. This would indicate that somewhere between the time you are running the OS, without the cd, and the install screen, the drive designations are changed. Why is this happening? If I have a 9 gig partition set as **home** it should be recognized as **home** in the new OS without me having to change it, unless I want to. I know you have to check the box if you want to format, but why do both **/** and **home** have to be reassigned as** /** and **home** in a manual install?

---

### Post by Bou on 2007-10-25
> **pdlethbridge said:**
> If I have a 9 gig partition set as **home** it should be recognized as **home** in the new OS without me having to change it, unless I want to. I know you have to check the box if you want to format, but why do both **/** and **home** have to be reassigned as** /** and **home** in a manual install?

Actually that sounds like the way it *should* work indeed. I think you should:

-Create a new spec, and / or
-Modify the spec I pointed to earlier, and include this, and / or
-Just file a bug, since it's ubiquity not giving the desired results.

---

