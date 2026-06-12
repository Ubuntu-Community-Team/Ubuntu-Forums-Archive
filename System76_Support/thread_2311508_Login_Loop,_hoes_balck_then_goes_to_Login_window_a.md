---
title: "Login Loop, hoes balck then goes to Login window after getting Gnome"
date: 2016-01-27
forum: System76 Support
---

### Post by William_Griff_Hage on 2016-01-27
Hello, I recently got gnome in my System76 Oryx Pro computer, and when I logged out like the tutlrial I watched said, I can't login now, it goes to a black screen whem I login, and then loops back to the login screen. I tried ctrl-alt-f1 and f2 to get to the terminal, and the screen becomes black and no terminal screen. What is happening, I have read it's driver errors, how do I fix this now, I have important files I am not risking on deleting.

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
First, don't panic.

Second. If none of those valuable files are in an encrypted partition or container, you can boot from something else, a live disk for example, and copy them securely to external media before you do anything more. Ideally you should back up any important data externally anyway so if you haven't already done that, now would be a good time before proceeding further.

Third, don't panic.

Fourth, you need to post more details. It is much more likely someone can make useful suggestions if you tell them EXACTLY what you did. In DETAIL.  Not just a vague ref to "the tutorial". Step by step.

Fifth, don't panic, or did I say that already?

---

### Post by William_Griff_Hage on 2016-01-27
Sorry if I have panicked, I have backed up the files on an external drive, how do I fix this though? I just read others have had the same issue, and they said in a step by step that after a reboot, that you would do ctrl-alt-f1 or f2, but his has proven to fail for me, since my screen goes to black. Is there a special way to enter the terminal from a reboot on a System76 computer/laptop? It's just really stressing this has occured. Sorry for the title errors, wrting + panic = Errors in Writing. Is there any solution to help me in this ordeal? Is it Gdm or the driver update, I really don't know?

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
OK, then, so whatever you do, including possibly following my own possibly bad advice, you can't screw up too badly if your data is safe.  I don't know about others but that makes feel much less stressed about answering. |>:)

Now, mea culpa perhaps. My comedy distracted from the second major point of my post which was:> **Dreamer Fithp Apprentice said:**
> Fourth, you need to post more  details. It is much more likely someone can make useful suggestions if  you tell them EXACTLY what you did. In DETAIL.  Not just a vague ref to  "the tutorial". Step by step.

There are a lot of tutorials on the net dealing with gnome.

---

### Post by ndrwgn on 2016-02-04
Yeah, so I'm having the same issue; the first thing I did was install gnome-shell. Then black screen. Then I reinstalled the os about three times (UEFI pain). Then I got it working. Then black screen. Only now do I realize what the problem is; kernel upgrades break nvidia (did you update your system?). I'm still working through it, been awhile since I've had to unscrew proprietary drivers. I'll post when I get there.

---

### Post by ndrwgn on 2016-02-04
I have a desktop. Ready?
sudo apt-get purge* nvidia
reboot. that will give you a desktop on the nv drivers. then you can reinstall
sudo apt-get install system76-driver-nvidia
reboot
But.... in order to get up and running again you need to 
sudo dpkg-reconfigure gdm
and select lightdm. I'm still trying to get gdm to work.

---

