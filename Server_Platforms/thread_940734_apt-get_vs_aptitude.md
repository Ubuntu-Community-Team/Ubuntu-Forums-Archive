---
title: "apt-get vs aptitude"
date: 2008-10-07
forum: Server Platforms
---

### Post by lykwydchykyn on 2008-10-07
I tend to notice that in the Ubuntu community people post command line installation instructions using apt-get.  I used to use apt-get a while back, but when Debian Etch was released, it caught my eye that the "official" package manager for Debian was switched to aptitude.  So since then I got into the habit of using aptitude on Debian.

I just wonder, does the Ubuntu community stick to apt-get as a matter of policy, or is it just user habit?  I know that the big reasons to use aptitude are (1) better conflict resolution and (2) it keeps a database of which packages were explicitly installed vs which ones were installed as dependencies, so that it can uninstall dependencies that aren't needed.  Now, it seems like on Ubuntu there are some other things doing the dependency tracking and so forth.  So is aptitude not recommended?

Anyone have a comment on that?

---

### Post by cdenley on 2008-10-07
> **lykwydchykyn said:**
> I tend to notice that in the Ubuntu community people post command line installation instructions using apt-get.  I used to use apt-get a while back, but when Debian Etch was released, it caught my eye that the "official" package manager for Debian was switched to aptitude.  So since then I got into the habit of using aptitude on Debian.

I just wonder, does the Ubuntu community stick to apt-get as a matter of policy, or is it just user habit?  I know that the big reasons to use aptitude are (1) better conflict resolution and (2) it keeps a database of which packages were explicitly installed vs which ones were installed as dependencies, so that it can uninstall dependencies that aren't needed.  Now, it seems like on Ubuntu there are some other things doing the dependency tracking and so forth.  So is aptitude not recommended?

Anyone have a comment on that?

I think apt-get tracks which packages were installed as a dependency as well. I was about to say what apt-get can't do is skip the recommended packages. However, I just upgraded to intrepid, and the new version of apt-get now seems to have it.

Aptitude is better at resolving conflicts, but seems more likely to remove packages in order to resolve dependencies. Of course, it warns you before it removes anything, but apt-get always seemed more stable to me. Is apt-get the stable version of aptitude?

---

### Post by lykwydchykyn on 2008-10-07
> **cdenley said:**
> I think apt-get tracks which packages were installed as a dependency as well. 

If it does, it didn't used to.  That's what makes me wonder, if ubuntu's version of apt-get has some extra configurations that track this differently than aptitude.

> 
Aptitude is better at resolving conflicts, but seems more likely to remove packages in order to resolve dependencies. Of course, it warns you before it removes anything, but apt-get always seemed more stable to me. Is apt-get the stable version of aptitude?

No they're different front-ends for APT.  I've never noticed less stability than apt-get, but if you mix the two you can wind up in trouble, because apt-get won't tell aptitude that you've explicitly installed things, so aptitude is "apt" to remove them.  Which is probably why Debian saw fit to make one "official".

---

### Post by cdenley on 2008-10-07
> **lykwydchykyn said:**
> If it does, it didn't used to.  That's what makes me wonder, if ubuntu's version of apt-get has some extra configurations that track this differently than aptitude.

It definitely does. I did a "sudo apt-get install package", then a "sudo apt-get remove package", and it says
> 
The following packages were automatically installed and are no longer required:

then lists all the packages which were previously installed as a dependency and not explicitly selected. I can then do a "sudo apt-get autoremove" to remove those packages. Maybe that feature didn't used to be in apt-get, but like skipping recommended packages, features in aptitude seem to get into apt-get eventually, which is why I thought it might be a more stable version of the same frontend.

Where did you read that aptitude was the official frontend as opposed to apt-get? Just curious.

By the way, I switch between the two all the time, never had a problem.

I just tested it some more, and apt-get also seems to see which packages were installed as a dependency by aptitude, and aptitude can see what was installed as a dependency by apt-get. I can't imagine a scenario where switching between the two can cause a problem.

---

### Post by lykwydchykyn on 2008-10-07
> **cdenley said:**
> 
Where did you read that aptitude was the official frontend as opposed to apt-get? Just curious.


[http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt](http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt)

They must have fixed apt-get with that tracking feature then, I know I had these sorts of problems with etch when it was in testing, or maybe sarge.

---

