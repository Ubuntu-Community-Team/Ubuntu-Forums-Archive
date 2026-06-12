---
title: "Audacity problem running under 12.04 with Xfce. Disappearing menu."
date: 2012-05-22
forum: Ubuntu Studio
---

### Post by irv on 2012-05-22
This problem is just when running Studio with Xfce. While using Audacity if I go to the Preferences to make changes and then come back to the main screen I lose the menus.It just disappear. 
Is this a bug? Was just wondering if anyone else is having this problem?
This might have something to do with Xfce because if I use Audacity under Ubuntu 12.04 Unity the menu appears in the top panel and it will return but under Xfce it appears in the main screen window so when it disappears it never returns.

---

### Post by sgx on 2012-05-23
Hi, you might compare xfce dependencies to those of
audacity, and adjust if there are newbies among them.
Does the problem vanish with the newest, or an
older version of audacity, like 3.12 or 2.0?

Hopefully it's just a gui toolkit or setting needing an update
that won't wreak havoc elsewhere. Another light window set,
lxde, openbox, e17, might be handy, to log into temporarily,
as the 12.04 public beta gets put through the ringers ;)
Cheers

---

### Post by jejeman on 2012-05-23
It is same on my installatio too. But it is just gui glitch, resizeing window renders back the menus, wich are there but not shown.

---

### Post by irv on 2012-05-23
> **sgx said:**
> Hi, you might compare xfce dependencies to those of
audacity, and adjust if there are newbies among them.
Does the problem vanish with the newest, or an
older version of audacity, like 3.12 or 2.0?

Hopefully it's just a gui toolkit or setting needing an update
that won't wreak havoc elsewhere. Another light window set,
lxde, openbox, e17, might be handy, to log into temporarily,
as the 12.04 public beta gets put through the ringers ;)
Cheers

To answer the question about the older and newer version of audacity. The problem is with the older version 2.0. I guess I didn't know there was a newer one out here. I just installed the one from the package manager. And when running under Ubuntu 10.10 there was no problem.
Seeing I am running 2.0, I will look for 3.12 and see if that fixes the problem.

---

### Post by irv on 2012-05-23
> **jejeman said:**
> It is same on my installatio too. But it is just gui glitch, resizeing window renders back the menus, wich are there but not shown.

What version are you running?

---

### Post by jejeman on 2012-05-23
I'm running default version for 12.04, 2.0.0, which is the last development stable release.

---

### Post by irv on 2012-05-23
I went out to Audacity website and it looks like I am running the latest version. 2.0.
 [http://audacity.sourceforge.net/about/news]("http://audacity.sourceforge.net/about/news")
I can't find 3.12, is that a beta version?

---

### Post by jejeman on 2012-05-23
> **irv said:**
> I can't find 3.12, is that a beta version?That is probably 1.3.12. which is version in 10.04.

---

### Post by irv on 2012-05-23
After doing some searching I found this answer on the Audacity forum.
> It's a known bug related to the version of WxWidgets. It seems to occur when Audacity is built against WxWidgets 2.8.12.
If you look in Audacity "Help > About Audacity > Build Information" it should say, in the "core libraries" section, which version of WxWidgets Audacity was built with.

The workaround (I've only tested this on Debian based distros) is to resize the window and the menus should then reappear.
This problem is not just in Ubuntu but also in both Fedora 16 and openSUSE 12.1.
[ATTACH]218561[/ATTACH]

EDIT: I also found this:
> The bug was already listed on the Audacity bug tracker, but as it did not occur with any "official" builds it was allocated a fairly low status. Now that distros are updating their version of WxWidgets the bug is starting to appear in those official builds and the situation will only get worse 'till it is fixed, so the priority has now been raised so now it is listed as very high priority ("P2").

---

### Post by irv on 2012-05-23
This is as far as we can go with this for now so I am going to mark it solved. Even though it is really not solved but bug that is not yet fixed.

---

### Post by sgx on 2012-05-23
Sorry for the confusion of stating 3.12 instead of 1.3.12
the stable version found here:

[http://packages.debian.org/stable/sound/](http://packages.debian.org/stable/sound/)

Have gone to the shop for a can of stronger coffee. :wink:

---

### Post by irv on 2012-05-23
> **sgx said:**
> Sorry for the confusion of stating 3.12 instead of 1.3.12
the stable version found here:

[http://packages.debian.org/stable/sound/](http://packages.debian.org/stable/sound/)

Have gone to the shop for a can of stronger coffee. :wink:

I had a feeling that's what you were trying to say. Now that I found all this other information I am just going to stay with 2.0 because the fix is easy. Just resize the window until the bug gets fixed.

---

### Post by Wrapperband-0 on 2012-06-27
I managed to get the menu back by pressing Ctr-N. a new instance of Audacity starts with the menu back.

XFCE over Kubuntu.

(as a temporary fix)

---

