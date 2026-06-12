---
title: "LTS Application Patches"
date: 2010-03-31
forum: Server Platforms
---

### Post by caseinpoint on 2010-03-31
This might be super simple so sorry in advance...

If I'm running an LTS version of a server and I need to update something like Samba to a version that is not in the package list for this for this version of LTS, what is the easiest way to upgrade or apply a patch?

I know I could install from source if I had to, but I'd like to see if there was an easier "with the system" way.

TIA!

---

### Post by fatbotgw on 2010-03-31
For a "with the system" way, the only way is with the "stock" repositories.  Otherwise if that version won't work for you, you can add look for an "aftermarket" repository or just roll your own from source/look for a .deb file.

My question would be why do you need to update past the LTS repository version?  With a new LTS about to come out, could you wait for it to come out and just upgrade the whole O/S?

---

### Post by caseinpoint on 2010-04-01
We have external auditors who recommend updates to Samba to versions that are not in my current LTS repository and Managment wants to know why I'm having trouble with the updates.

I'm somewhat fam with updating the sources.list file, but could I get to repositories for just Samba? Does something like that exist?

Again, I'm pretty new so thanks in advance.

---

### Post by fatbotgw on 2010-04-01
Well since you're on a real-world production server and not some roll-your-own server at home I would not suggest adding extra repositories.

That being the case, I would suggest you install from source.

Take a look [here]("http://www.jeremycole.com/blog/2009/12/01/upgrade-samba-3-0-28a-to-3-4-3-on-ubuntu-8-04-lts/") for starters.

Also, this might be of use as well:  [How to Compile Samba]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html")

---

