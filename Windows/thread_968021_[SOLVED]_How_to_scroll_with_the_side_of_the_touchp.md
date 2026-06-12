---
title: "[SOLVED] How to scroll with the side of the touchpad?"
date: 2008-11-02
forum: Windows
---

### Post by fiddler616 on 2008-11-02
Hello,
Windows broke a month or two ago--which wasn't a huge deal, but still annoying. I didn't have a recovery disk, but I just fixed it today by stumbling across an article detailing how to use a program called BartPE to make one. I couldn't seem to restore the existing Windows install, so I made a new one on a different partition (partition #1 is going to die soon). Apart from experiencing massive culture shock, I realize that I can no longer scroll with the edge of my touchpad. Now that I think about it, I guess the OEM put on a few utilities when the laptop shipped--and one of them enhanced the touchpad.

How do I regain this functionality? I have a phobia of taskbar-running bloatware. Should I take the original utility off my dead partition, or is there a good download? I've gotten a bit spoiled by repos.

Thank you.

---

### Post by smoker on 2008-11-02
if you go to the laptop manufacturers support website, usually by inputting model number there, you should get access to a download page where such utilities should be available,

---

### Post by fiddler616 on 2008-11-02
Thanks, that looks like it'll do it!

(The only setback is that reinstalling GRUB after installing Windows has messed up both OS's--I'm on a Live CD--but that should get sorted soon.)

---

### Post by smoker on 2008-11-02
there are plenty guides to reinstall grub with a quick search of the forum, but i always have a copy of this handy:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by fiddler616 on 2008-11-03
> **smoker said:**
> there are plenty guides to reinstall grub with a quick search of the forum, but i always have a copy of this handy:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Well, I managed to install GRUB from a Terminal from the Live CD--but it couldn't mount Ubuntu, and Windows was throwing up some kind of error. Sigh. So I reinstalled Ubuntu (I got fed up.) The only problem is that now GRUB can't even *find* Windows, but that's a thread in and of itself.
Cheers.

---

### Post by smoker on 2008-11-03
did you try the supergrubdisk? there is plenty info on the wiki for just about every grub problem, easy to use and handy to have in the toolkit!
[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)

best of luck

---

### Post by Ptero-4 on 2008-11-03
the synaptic driver for windoze is probably what "enhances" your trackpad under windoze.

---

### Post by fiddler616 on 2008-11-04
> **smoker said:**
> did you try the supergrubdisk? there is plenty info on the wiki for just about every grub problem, easy to use and handy to have in the toolkit!
[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)

best of luck

I tried it before I reinstalled Ubuntu--and all I could make it do was show the GRUB menu--nothing would boot off of it. Though I haven't done the specific recovering Windows instructions.
On [URL="http://ubuntuforums.org/showthread.php?p=6101841#post6101841"]the thread
[/URL] they're actually also recommending SGD disk (I really guess I should try it again) but there also seems to be an easier method involving editing menu.lst
I guess I'll see....

Thanks you

---

