---
title: "What is meant by &quot;18 months of free update&quot; ?"
date: 2009-10-31
forum: The Cafe
---

### Post by emigrant on 2009-10-31
hi all,
what is mean by *18 months of free updates?* for each ubuntu desktop release? (not the LTS ones)
that means after 18 months the update manager won't work?
or the user won't be able to install new apps?

if i want to install jautny in 2015, i just get what it is in the cd and can't do any updates which are available on the internet right now? all these updates will get deleted by 2015?

please i want a clear answer :KS

thank you very much :)

---

### Post by RiceMonster on 2009-10-31
It means Canonical with stop supporting it after 18 months and there will be no more updates.

---

### Post by emigrant on 2009-10-31
:)
what im asking about is, if some one installs jaunty in 2015 will he able to get anything beyond what is in the cd?
will his addremove/progs and apt-get udpate and other apt-gets work?

---

### Post by 23meg on 2009-10-31
> **emigrant said:**
> 
if i want to install jautny in 2015, i just get what it is in the cd and can't do any updates which are available on the internet right now? all these updates will get deleted by 2015?


If you install any release past its supported lifecycle, you won't get any [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates"), and won't be able to install anything from the repositories, since they will have been removed.

As should be obvious, it's not a good idea.

---

### Post by stmiller on 2009-10-31
Ubuntu releases a new version every six months.  So a given release (unless it's LTS) gets 18 months of security updates, patches, etc.  

So for example Ubuntu 5.04 from 2005 is no longer receiving security updates, etc.

From wikipedia:
```
Version	Code name	Release date
4.10	    Warty Warthog	2004-10-20
5.04	    Hoary Hedgehog	2005-04-08
5.10	    Breezy Badger	2005-10-13
6.06 LTS	Dapper Drake	2006-06-01
6.10	    Edgy Eft	2006-10-26
7.04	    Feisty Fawn	2007-04-19
7.10	    Gutsy Gibbon	2007-10-18
8.04 LTS	Hardy Heron	2008-04-24
8.10	    Intrepid Ibex	2008-10-30
9.04	    Jaunty Jackalope	2009-04-23
9.10	    Karmic Koala	2009-10-29
10.04 LTS  Lucid Lynx	2010-04-29
```

It's not a big deal because you can simply upgrade to the latest release when the new release comes out. :)

---

### Post by emigrant on 2009-10-31
yes, i understand now.
but im thinking whether the latest releases would be enough compatilbe with older machines...

---

### Post by jpmelos on 2009-10-31
> **stmiller said:**
> It's not a big deal because you can simply upgrade to the latest release when the new release comes out. :)

Make a backup before you upgrade, since it can and might crash the system. Wait, if you already have the backup, why not fresh install? I'm saying that because lots of people report bad upgrades. Fresh installing is more recommended, plus, formatting the computer every six months is very healthy. Every system accumulates lots of garbage over time, that may make it less stable or fast.

---

### Post by Tipped OuT on 2009-10-31
> **emigrant said:**
> yes, i understand now.
but im thinking whether the latest releases would be enough compatilbe with older machines...

Should be. Ubuntu isn't like Windows, where each new release the hardware requirments go up.

If not, you can try other distro's that are light weight, like D.S.L.

---

### Post by Wim Sturkenboom on 2009-10-31
> **Tipped OuT said:**
> Should be. Ubuntu isn't like Windows, where each new release the hardware requirments go up.Doubt that. Upgrade from 6.06 to 8.04 made my system slower: longer boot time, firefox takes longer to produce the save dialog. So sorry, but I don't believe you.

---

### Post by Giant Speck on 2009-10-31
> **Tipped OuT said:**
> Should be. Ubuntu isn't like Windows, where each new release the hardware requirments go up.

The system requirements didn't really change between Windows Vista and Windows 7.

---

### Post by Pogeymanz on 2009-10-31
> **Tipped OuT said:**
> Should be. Ubuntu isn't like Windows, where each new release the hardware requirments go up.

If not, you can try other distro's that are light weight, like D.S.L.

Well, it doesn't increase the requirements as much, but you certainly can't put 9.10 on a computer that once ran 1.10 (if there was such a version).

---

### Post by emigrant on 2009-10-31
@ [Pogeymanz]("http://ubuntuforums.org/member.php?u=452867") :D

---

### Post by Tipped OuT on 2009-10-31
> **Pogeymanz said:**
> Well, it doesn't increase the requirements as much, but you certainly can't put 9.10 on a computer that once ran 1.10 (if there was such a version).

lol I knew someone was going to say some thing like this.

---

### Post by aysiu on 2009-10-31
If you're having performance issues on an old computer, the solution isn't to use an older version of Ubuntu (in fact, 9.10 is much speedier than 8.10 or 8.04).

The solution is to use a lightweight window manager (IceWM, OpenBox, Enlightenment) instead of a desktop environment (Gnome, KDE, Xfce). Also use lighter-weight programs (Sylpheed instead of Evolution, Dillo instead of Firefox).

You can build Ubuntu from scratch if you're worried the default installation brings in too many services:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by emigrant on 2009-10-31
thank you for your inputs.
at the moment i have a core2duo 3.0 GHz, 2GB, 256VGA machine, how long would you think i can keep putting latest releases? :D

---

### Post by aysiu on 2009-10-31
> **emigrant said:**
> thank you for your inputs.
at the moment i have a core2duo 3.0 GHz, 2GB, 256VGA machine, how long would you think i can keep putting latest releases? :D
Indefinitely. Those specs are fine.

I'm running Ubuntu 9.10 on a 1.6 GHz Atom processor with 2 GB of RAM, and it flies.

---

### Post by Tipped OuT on 2009-10-31
> **emigrant said:**
> thank you for your inputs.
at the moment i have a core2duo 3.0 GHz, 2GB, 256VGA machine, how long would you think i can keep putting latest releases? :D

Woah, you're worried about those specs? That's a nice A§§ computer you got there :D. No worries at all.

---

### Post by emigrant on 2009-10-31
:KS thanks:popcorn:

---

