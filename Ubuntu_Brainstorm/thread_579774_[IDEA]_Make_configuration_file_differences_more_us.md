---
title: "[IDEA] Make configuration file differences more user friendly"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by johann_p on 2007-10-18
When a package update or distro update wants to overwrite a configuration file, the user can display the differences before choosing to keep the old one or install the new one. Currently the differences are shown in raw diff output format.

This is nearly incomprehensible for anyone who is not a developer. This should be shown in a side-by side comparison way like e.g. kdiff3 does.

---

### Post by Zdravko on 2007-10-18
Why would I want to see the differences between configurations files?

---

### Post by johann_p on 2007-10-18
> **Zdravko said:**
> Why would I want to see the differences between configurations files?
This is actually quite important: if a new version of a software package has additional/changed configuration file parameters it will not simply replace the old config file with a new one (so not to destroy your old config data) but it will also not just keep the old one (so that important new settings are not missed).

In order to let you decide, currently you can choose between "keep" or "replace" and to help with your decision, the differences between old and new version are shown.

My gripe is that the differences are shown in a totally user-unfriendly format instead as a comparison old versus new side-by side, with an option to merge old with new where necessary.

---

### Post by BungaMan on 2007-10-18
I agree, I had about 5 or 6 times that the upgrade asked me about which file to keep.

In fact it should be improved to know if the user ever changed it.  It were mostly files I didn't even know existed.  As a more experienced user I knew what was going on but imagine a beginner seeing this popup...

---

### Post by aysiu on 2007-10-18
Having used Ubuntu since Hoary (5.04), I've learned the safest thing to do is replace instead of keep configuration files when upgrading.

---

### Post by greg_g on 2007-10-18
> **aysiu said:**
> Having used Ubuntu since Hoary (5.04), I've learned the safest thing to do is replace instead of keep configuration files when upgrading.

Except when you are sharing a printer.  With the replaced config file you now have to find that howto from long ago to re-enable that.

When it replaces the file, does it make a backup? (cupsd.conf.20071018 or whatever)  That and saying "if you need to see your old file, it is named <config-file>.<date>" might help.

---

### Post by Zdravko on 2007-10-19
Ah, yes - now I see. Nice idea.

---

### Post by Paul Dufresne on 2007-11-16
I am about to write a specification about this.
Hopefully, in the next two hours.
I should be posting the link on bug #69412:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/69412](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/69412)

I intend to steal your Title. :)

---

### Post by teasum on 2007-11-16
I agree with most of the posts here, and I think both improvements can be implemented:

1) When upgrading, provide a simpler side-by-side comparison of old and new config files, and 
2) include an option, even if only for 'advanced' users, to create a backup of the overwritten config file.

When I upgraded, I unded up copying and pasting some of those messages because I wasn't sure whether I would obliterate some manual tweak I had made to enable some of my hardware to work.

---

### Post by deecee52 on 2008-05-11
> **aysiu said:**
> Having used Ubuntu since Hoary (5.04), I've learned the safest thing to do is replace instead of keep configuration files when upgrading.


Given that Hardy has been released, this topic is still relevant.  I upgraded to Hardy Heron, and there is still a need for both better comparison and also the ability to save the old configuration.  If you cannot save the configuration, there should be an option to backup all of your config files in one place at the beginning of the install so that you can easily find them after the upgrade.

---

### Post by johann_p on 2008-05-12
I upgraded Gutsy to Hardy on my laptop a few days ago and got prompted for about 8 config files in that way. For about 4 of them a *merged* version of old and new would have been the right choice: the old ones contained additional settings needed for my particular installation while the new ones contained stuff that was either new in the program or e.g. the names of newer system libraries.

So whatever I chose, it was the wrong selection. :(

A graphical compare with a way to merge and edit the resulting config file (and backup both old versions) would be of immense help.

On my desktop PC (which I have not yet upgraded because I fear the not so uncommon problems) i expect even more config file prompts because I have installed many more programs that are not installed by default. 

Apart from bugs in the upgrade process, this is really the single most annoying problem in my opinion, and apart from being not user-friendly, let alone newbie-friendly at all (showing naked diff output), it can cause problems and a lot of work after the upgrade.

---

