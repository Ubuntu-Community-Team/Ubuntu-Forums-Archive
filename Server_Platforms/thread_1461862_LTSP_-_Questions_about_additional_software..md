---
title: "LTSP - Questions about additional software."
date: 2010-04-24
forum: Server Platforms
---

### Post by Happybattles on 2010-04-24
Hi!
I've tried the old version of LTSP under Fedora 6, but now that I see Ubuntu has the latest version and... well... it's UBUNTU, I'm making the change.  However, I have a couple of questions.

1. If I want to remove software (such as most of the games) from the system so my students aren't wasting their time playing them, how do I do it?  Would I just log in the server itself, or would I log into one of the terminals?  From there would I just remove the software and the removal would be reflected in all of the workstations?

2. If I want to make a folder available to all of my students (such as a folder full of clipart), where does the folder have to be located, or can it be anywhere?

3. If I want to add new software... well... just look at #1.

---

### Post by garyedwardjohnston on 2010-04-24
I can't help directly but maybe this can :)

[https://help.ubuntu.com/community/UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

---

### Post by ICEB3AR on 2010-04-25
For installation of new software you could easily ssh @ the server and then
```

sudo chroot /opt/ltsp/i386
# e.g. for i386 image or change it to the right directory  
sudo apt-get install <new_package>

```

I expect that the removing of the packages works the same way.

---

