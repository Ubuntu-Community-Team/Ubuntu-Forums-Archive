---
title: "[idea] GUI identify non-free software"
date: 2007-10-28
forum: Ubuntu Brainstorm
---

### Post by Domhnull on 2007-10-28
I'm currently using the standard Ubuntu 7.10 version but I'm interested in Gobuntu.  It'd be nice if the standard version would more clearly identify software that wouldn't appear in Gobuntu.  That could be a simple 'non-free' tag in the Add/Remove Applications GUI, or a license column that lists what each application is licensed under.  I'd be more interested in that than the 'popularity' icon.  The drop-down filter does have an option for 'open-source' software but that doesn't necessarily equate with free software.  It'd also be nice to have a filter which shows 'installed non-free software' with a suggestion for alternatives if available.  So Firefox might show up on the list and suggestions would show alternatives.

---

### Post by earobinson on 2007-10-28
All of the software that comes with ubuntu is free, its just the drivers that are not.

fi you have any other questions about it feel free to post a program and ill let you know if its free or not.

---

### Post by Prometheum on 2007-10-28
But what about all of the codecs, RAR, deCSS, etc?

I think this would be a good idea, regardless of how little it would affect.

---

### Post by smartboyathome on 2007-10-28
> **Prometheum said:**
> But what about all of the codecs, RAR, deCSS, etc?

I think this would be a good idea, regardless of how little it would affect.

If this was implimented, would it be kept to Gobuntu only? I don't want it in Ubuntu, because I don't care if what I am using is free or not.

---

### Post by kellemes on 2007-10-28
> **smartboyathome said:**
> If this was implimented, would it be kept to Gobuntu only? I don't want it in Ubuntu, because I don't care if what I am using is free or not.

Same here..
Just wonder what the implications would be for packagers since they would have to mark a package based on the license.. The list of licenses is terribly long.

---

### Post by Domhnull on 2007-10-28
Certainly I can go through individual programs and look at what it is licensed under, for example, by checking the [Free Software Directory]("http://directory.fsf.org/").  Or taking a look at the documentation.  But I still think it's worthwhile to make that sort of information available in a clearly visible fashion within the Add/Remove Software GUI.  We should make it easy for users to identify non-free software on their systems and offer alternatives.    If someone is unconcerned about their freedoms that's fine, the information wouldn't make any difference to them.

---

### Post by pay on 2007-11-07
I can't believe that Ubuntu doesn't already have something like this. I mean it wouldn't take up that much room in Synaptic just to have GPL, BSD or Proprietary and it would help some users pick which software they wanted to install. I think that it is a great idea.

---

### Post by 23meg on 2007-11-07
Note that Ubuntu's components are separated according to their level of Freeness and support. However, for more fine grained control, it can make sense to implement per-package license information. [Debtags]("http://debtags.alioth.debian.org") can be ideal for this.

Now that there's talk of integrating PackageKit in Hardy+1, perhaps that's the place to do it. I suggest taking a look at development discussions related to Synaptic to find out why it hasn't been done yet.

---

