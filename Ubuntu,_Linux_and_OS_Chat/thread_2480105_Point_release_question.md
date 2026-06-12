---
title: "Point release question"
date: 2022-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by lovrenca on 2022-10-19
Greetings,
I have a question regarding point releases and their relevance in term of system requirements in let's say a programmer developer environment.
Does it make any sense to list a point release (e.g.: 20.04**.3**) in the system requirement or is it enough to just list the release "20.04".

My understanding so far is that point releases just include up-to date packages with all the bug-fixes and similar, which were not in the initial release. This way you get a more stable install ISO and a more stable fresh installation, but if you install 20.04.X and run update, you end up with the same system.
Is this correct or is there more to it?

---

### Post by guiverc on 2022-10-19
Ubuntu 20.04 LTS is a release  (*codename is **focal****regardless of upgrade level*)

The **.3**just shows the *upgrade level*, but it's still a Ubuntu 20.04 LTS system (*be it desktop or server install*).

From a [release announcement of Ubuntu 20.04.3 LTS]("https://fridge.ubuntu.com/2021/08/27/ubuntu-20-04-3-lts-released/") you'll find the following quote

> As usual, this point release includes many updates, and updated  installation media has been provided so that fewer updates will need to  be downloaded after installation.


ie. install a Ubuntu 20.04 LTS system with the initial released media, and applying all upgrades will result in the same system as those installed using Ubuntu 20.04.3 LTS media, alas some minor *flavor* exceptions.

Ubuntu 20.04 LTS ***flavors*** (I'll use Lubuntu 20.04 LTS as an example), the 20.04 & 20.04.1 media when installed defaulted to using the GA kernel stack, ie. using the original media will cause the 5.4 kernel to be installed; applying all upgrades will still be using the 5.4 kernel as the GA kernel uses the *more **stable* kernel. However installs of Lubuntu 20.04.2 LTS (*or later, thus 20.04.3*) default to the HWE kernel being used; thus an install of Lubuntu 20.04.3 LTS will result in the 5.11 kernel being used. This difference applies to *flavors* or any system using the HWE kernel stack.

All Ubuntu 20.04 LTS **Desktop** installs however defaulted to HWE kernel stack for all installs, thus no difference, ie. initial media & upgrades vs starting with a later ISO.

All Ubuntu 20.04 LTS **Server** installs default to the GA kernel stack, thus no difference between 20.04 LTS Server install or later media if all upgrades are applied.

ie.  the difference for 20.04 applies only to *flavors* of Ubuntu.  That wasn't the case with Ubuntu Desktop 18.04 LTS or earlier, as they used the defaults now used only by *flavors* of Ubuntu (ie. release matters here; but we're talking only about 20.04)

*Note:  I'm using 20.04.3 only as you did; it's rather old now, with the current 20.04 at 20.04.5.  At 20.04.5 the HWE kernel is 5.15*

For more details on HWE/GA kernel stack; refer [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by grahammechanical on 2022-10-19
The advantage of Long Term Support versions from the point of view of Enterprise users and possibly developers is stability. The interim versions (nine months support) are where the Ubuntu developers keep up to date with changes to the Desktop Environment; User Interface and other stuff. And so they work their way towards the next LTS release over a period of two years.

Regards

---

