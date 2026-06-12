---
title: "Idea &quot;Last known bootable config&quot;"
date: 2008-10-07
forum: The Cafe
---

### Post by bobbob1016 on 2008-10-07
This wouldn't be that hard to do.  Add a small program to watch the vital folders, as in to watch /etc, /bin and things like that, and the first time one of those files is modified after a boot, make a backup of the original file.  Same could be done for program versions.  Write a small file to /boot, after each boot, if the boot was successful, write a 0.  If it was unsuccessful write a 1.  Have the file checked first thing on boot, and say "I see that I was unable to startup last time, I will try with the last known good config."

There would be 3 levels of startup protection, full - would backup files and programs, configs, partial - would just backup the configs and none - wouldn't do any of this.

The benefits of this would be no more "I updated Ubuntu and now it won't boot." or "I modified my xorg.conf, and now can't boot" posts.

We could even add a way to remove specific updates, if they are problematic.  We could add a ping to the Ubuntu servers to say "are there any problematic updates?"  and if there are any that prevent booting after networking is started it would be removed automatically or after being prompted.  If there are any that prevent booting before networking, we could post them on ubuntuforums.org.  We could number code each update, so we just tell the user to enter (when prompted what to remove) 101010 and then that problematic update would be removed.

I know this is too late for Ibex, but could be in Jackalope.

Edit:  Yes I know backing up programs would take up a lot of space, but that is why we could add the "full, partial, none" choices.

---

### Post by LaRoza on 2008-10-07
[http://www.ubuntu.com/testing/intrepid/beta#%22Last%20successful%20boot%22%20recovery%20entry](http://www.ubuntu.com/testing/intrepid/beta#%22Last%20successful%20boot%22%20recovery%20entry)

---

### Post by bobbob1016 on 2008-10-07
Isn't that just the kernel though?  I meant backup xorg, and initd or whatever we're using now too.  My idea is a step further than that one.

---

### Post by LaRoza on 2008-10-07
> **bobbob1016 said:**
> Isn't that just the kernel though?  I meant backup xorg, and initd or whatever we're using now too.  My idea is a step further than that one.

That is a bit overkill don't you think?

Might as well just use a live disk or have it set to not save any changes at all (like in some public computers).

---

### Post by schauerlich on 2008-10-07
> **bobbob1016 said:**
> Isn't that just the kernel though?  I meant backup xorg, and initd or whatever we're using now too.  My idea is a step further than that one.

> **LaRoza said:**
> That is a bit overkill don't you think?

Might as well just use a live disk or have it set to not save any changes at all (like in some public computers).

Wouldn't a combination of the planned feature of Ibex and sysres do the trick?

---

### Post by bobbob1016 on 2008-10-07
Well it is overkill for those who are past the "let me tweak this to death" phase.  As in a new user who tries installing compiz via git, and breaks a bunch of files in the process, it could help.  That is why I said it should be easy to turn off, and have a middle level of just backing up modified config files.  Booting a LiveCD won't work as well, since if I install my Video Card driver, it needs to be done on boot.

I'm not saying to do this each boot, just after a failed boot.  A lot of new users are trying out Ubuntu, and they usually like to tinker with things above their grasp.  This is not itself bad, but if they can be fixed easily/automatically, it can't hurt.

Edit: "Wouldn't a combination of the planned feature of Ibex and sysres do the trick?"  Not 100% sure what sysres is.  This would have to be done automatically, not something a normal user could do.  I would do this, but I don't know how to code for Linux/Unix.

---

### Post by LaRoza on 2008-10-07
> **EDavidBurg said:**
> Wouldn't a combination of the planned feature of Ibex and sysres do the trick?

Not really. In my experience, nothing more than a backup of a config file was ever needed. sysres just automates that and gives it a no brainer interface.

The feature in Ibex looks nice, but I don't see a use for it really. And the feature mentioned here is way beyond that.

---

### Post by bobbob1016 on 2008-10-07
> **LaRoza said:**
> The feature in Ibex looks nice, but I don't see a use for it really. And the feature mentioned here is way beyond that.

I know my idea is really overkill for those who know how to tinker, and keep things working.  This would be like training wheels, so new users could tinker without worrying.

---

### Post by LaRoza on 2008-10-07
> **bobbob1016 said:**
> 
Edit: "Wouldn't a combination of the planned feature of Ibex and sysres do the trick?"  Not 100% sure what sysres is.  This would have to be done automatically, not something a normal user could do.  I would do this, but I don't know how to code for Linux/Unix.

You never heard of sysres? sysres is the latest product of the brilliant minds of this century lead by the most humble person in the world. See [https://launchpad.net/sysres](https://launchpad.net/sysres)

> **bobbob1016 said:**
> I know my idea is really overkill for those who know how to tinker, and keep things working.  This would be like training wheels, so new users could tinker without worrying.

Well, this is called "feature creep". A tinker-er is not a new user and shouldn't treated as such. The feature is for a fringe user who doesn't need it. You could always make it yourself to see how it goes, like the sysres program.

---

### Post by bobbob1016 on 2008-10-07
> **LaRoza said:**
> A tinker-er is not a new user and shouldn't treated as such. The feature is for a fringe user who doesn't need it. You could always make it yourself to see how it goes, like the sysres program.

Well I wouldn't think only a fringe could mess things up.  If someone messes up installing their wifi driver, or video driver, this could help.  I was thinking of doing this myself, guess I'll have to learn my Linux/Unix coding, I'd think python or perl maybe?

---

### Post by LaRoza on 2008-10-07
> **bobbob1016 said:**
> Well I wouldn't think only a fringe could mess things up.  If someone messes up installing their wifi driver, or video driver, this could help.  I was thinking of doing this myself, guess I'll have to learn my Linux/Unix coding, I'd think python or perl maybe?

For Ubuntu, use Python.

---

### Post by uberdonkey5 on 2008-10-07
> **LaRoza said:**
> You never heard of sysres? sysres is the latest product of the brilliant minds of this century lead by the most humble person in the world. See [https://launchpad.net/sysres](https://launchpad.net/sysres)


lol, its great she thought to develop that - I'll give it a go. Thanks. Not sure how to test it though? Just trash my system a bit?? :)

---

### Post by spupy on 2008-10-07
I think it is a great idea, but only if not overdone and turned into feature creep. I myself was thinking of something like this.
In my distro of choice, Gentoo, one can create packages from already installed programs. If the something goes wrong, you can install this package with your package manager and the thing will be working again. I currently have such packages of my system, I update the once in a while, and sometimes write them to a disk. The downside is that this requires a lot of disk space (currently 1,3GB).

One of the things I most hate about Linux (they aren't much, but still) is the bajillion libraries, each of them updating from 0.1.5-r2 to 0.1.5-r3 (you get the idea?). Each such update has the potential to brick a system, the developers can't test everything. It happened to me that after an update - some programs were not working. I had to hunt down logs, find what latest versions of several programs and libs were working, and install them back. It is not pleasant for me. And I can't imagine what will this be for a not so linux-savvy user, who can leave Ubuntu for much smaller troubles.
Why not create something that makes the OS more smooth and stable?
Sysres looks like something in the right direction. The next step would be to couple this program with the installation/update process and automate it.

---

