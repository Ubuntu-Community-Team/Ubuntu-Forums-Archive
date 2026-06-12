---
title: "My package manager is installing updates without prompting for a password"
date: 2010-12-18
forum: Security
---

### Post by i_dont_know_what_im_doing on 2010-12-18
My package manager (KPackageKit) seems to be able to install updates without authentication. (Installing new packages does prompt for a password, it's only the updates) This is on a fairly recent clean installation of Kubuntu 10.04, and I haven't made any big changes to anything. I've searched around, and I can't really tell whether this is supposed to be happening. The consensus seems to be "Switch to synaptic," but my concern is this: Somehow, a program was able to edit root files without any authentication. How is that even possible? What should I do about it? Thanks!

---

### Post by cariboo on 2010-12-19
I don't know if it's the same in Kubuntu, but in Ubuntu you can set updates to be installed automatically. See screen shot.

---

### Post by SeijiSensei on 2010-12-19
I was surprised the first time KPackageKit didn't prompt for a password during updates as well.  Apparently this is the correct behavior.  It doesn't bother me much since we're only talking about updates to existing packages.  As you say, installing new packages always requires a password.

There doesn't seem to be a method to alter this behavior in KPackageKit either.  I can tell it whether I want updates installed automatically, but not whether I want to require a password to do so.  On the other hand, if a password were required, it wouldn't be possible to implement automatic updating.

---

### Post by i_dont_know_what_im_doing on 2010-12-19
> I don't know if it's the same in Kubuntu, but in Ubuntu you can set updates to be installed automatically. See screen shot. 
I have that set to "only notify." Even if I open KPackageKit and manually tell it to update, it doesn't require a password.

> I was surprised the first time KPackageKit didn't prompt for a password  during updates as well.  Apparently this is the correct behavior.  It  doesn't bother me much since we're only talking about updates to  existing packages.  As you say, installing new packages always requires a  password.
Huh, weird. I guess that answers my question :). 

Just wondering, how is KPackageKit capable of doing that? If I open it and it's running under my username, it seems like it wouldn't be able to change root-owned files.

Thanks for the help!

---

