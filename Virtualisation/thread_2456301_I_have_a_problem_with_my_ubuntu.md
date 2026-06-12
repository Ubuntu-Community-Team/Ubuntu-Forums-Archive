---
title: "I have a problem with my ubuntu"
date: 2021-01-08
forum: Virtualisation
---

### Post by faithx on 2021-01-08
Hello everyone, I am **new** to all this Linux, they told me to choose this distro, but, when installing it, everything was fine, I decided to restart my laptop and pum, ***neither the interface, nor the icons, nor the files are capable of being reproduced*** , I need help, I'm starting to be crazy, I can't even take screenshots, only Firefox  :(:(

---

### Post by mikewhatever on 2021-01-08
So, no hardware specs, no version of Ubuntu, no clear details... What can we do for you?

---

### Post by faithx on 2021-01-08
Ok, Im going to share my hardware specs, Processor: Ryzen 3-3200U with radeon vega graphics 3, 8 GB Ram, I'm using Ubuntu 20.04

---

### Post by faithx on 2021-01-08
Maybe I can uninstall ubuntu and reinstall it which will take years

---

### Post by howefield on 2021-01-08
You have posted to the "*Virtualisation*" forum, so presumably this is a virtual machine, can you explain a bit more about how exactly you installed it, you don't have an interface yet manage to use Firefox ?

Have a read at the Posting Tips which you will [find here]("https://ubuntuforums.org/showthread.php?t=2158945"), and produce a post which might give someone a clue as to where to start helping you.

PS. Exactly how many years did it take to install in the first place, curious minds need to know.

---

### Post by TheFu on 2021-01-08
> **faithx said:**
> Maybe I can uninstall ubuntu and reinstall it which will take years

On current generation "average" hardware, an install should take 10-15 minutes.

I've see some first logins under virtual machines take 10 minutes on Core i7 hardware, but that was long ago and easily traced back to improper hypervisor settings. I've also seen some 20.04 Ubuntu desktops be really, really slow under some other conditions. I didn't troubleshoot very much for that one, I just switched to a different DE and that solved it for me. A few weeks later, I ended up doing a fresh install and I do still see some slowness if I keep using that 1 problem DE, but with any other DE/WM that I've tried, that virtual machine is very fast and responsive.

Some terms:
[LIST]
[*]DE = Desktop Environment
[*]WM = Window Manager
[/LIST]
These are the different layers for the GUI.  99% of the time, we don't need to know much about these things, just which one we are using.

Before everyone volunteering tries to start guessing at issues, please tell us:
[LIST]
[*] which hypervisor you are using
[*] which OS, number and DE "flavor" you are running - or trying to run
[*] exactly what you do to boot into the OS that is having issues.
[/LIST]

As for the details about hardware, the easiest way to provide that is by installing and running a simple command from any terminal:
```
$ inxi -Fz
```
Then just copy/paste that output back into these forums and wrap in 'code-tags' [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains. The Advanced Reply makes that just a little easier, but any forum reply button works fine.

Nobody started out knowing all these things.  Don't be too afraid to try things, provided you aren't using **sudo** whenever you try stuff.  If you do use sudo, be extra careful. Unix-like systems, like Ubuntu, will happily allow you to shoot yourself in the head, if you like.


We really do want to help you have a great experience. Just need some information. And you are welcome to the forums.

---

