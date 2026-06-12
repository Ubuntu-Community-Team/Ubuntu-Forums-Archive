---
title: "gnome-keyring/seahorse 3.3.5"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jbicha on 2012-03-05
Hi, I've packaged the latest gnome-keyring and seahorse (Passwords and Keys) in the [GNOME3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3/+packages?field.series_filter=precise"). Since it's a major upgrade and is being considered for inclusion in Precise, we need to know if it causes any regressions or doesn't work properly.

You can comment here or at [bug 947447]("http://pad.lv/947447").

And of course, there's the caveat that the GNOME 3 PPA includes some stuff that won't make it into Precise and other stuff that isn't ready yet for Precise. Be sure you know how to use ppa-purge before trying PPAs like this. Thanks!

---

### Post by Mr. Picklesworth on 2012-03-05
Thanks for this PPA, jbicha! It's been really nice to have.

There is one odd thing. You know how you can right click an SSH key (or go to the Remote menu with one selected) and choose Configure Key for Secure Shell, and that's a really fantastically amazing feature? I find that that  option sometimes doesn't appear, and sometimes does, and I can't quite put my finger on the pattern.

Either way, nothing happens when I choose it.

Anyone else setting either of those things?

Edit:
Oh, quick BTW for people who might want something a tad more familiar (or who have a lot of passwords stored). Go to View > By Keyring in the menu and you can choose between various filters on the left side.

---

### Post by jbicha on 2012-03-05
Thanks, I can confirm that bug. Do you want to report it?

---

### Post by tista on 2012-03-05
Hi jbicha. ;)

Really thanks for your work!!

Then unfortunately I have an issue on "change password" of seahorse...

Please see my screenshot:
[img]http://i43.tinypic.com/mkyntt.png[/img]

Yeah if I want to change my "login" password by seslecting its right-click menu "change password" on Login-Keyring, then that dialog happens to show the error... :(

Now I'm employing this version:
```
ii  gnome-keyring                                  3.3.5-0ubuntu1~precise1                              GNOME keyring services (daemon and tools)
```

Any ideas?

P.S:
You knew well, I've used to live with gdm 3.2.1 for a meantime, so it might be caused gdm or not... Although I have not a clue anyway. ;) The other average-users didn't have such issue yet?

Best Regards,
Tista

---

### Post by jbicha on 2012-03-05
tista, I can duplicate that too (with lightdm). Could you report that against seahorse  too? That one's more serious and I'm curious whether it's gnome-keyring  or seahorse to blame, but seahorse 3.2 won't build against the new  gnome-keyring.

---

### Post by tista on 2012-03-05
> **jbicha said:**
> tista, I can duplicate that too (with lightdm). Could you report that against seahorse  too? That one's more serious and I'm curious whether it's gnome-keyring  or seahorse to blame, but seahorse 3.2 won't build against the new  gnome-keyring.

@jbicha

OK... my seahorse has this version:
```
ii  seahorse                                       3.3.5-0ubuntu1~precise1                              GNOME front end for GnuPG
```

And I also felt sad that lightdm sessions had this issue as well... So git had anything to go steps forward, like patches and workarounds? Or a specific problem on Ubuntu?

Regards,
Tista

---

### Post by jbicha on 2012-03-05
tista, I don't think this is specific to Ubuntu so you're welcome to report it on GNOME Bugzilla.

No relevant changes have been made on git since the version in the PPA and my quick search of bugzilla didn't show that this has been reported yet.

This is part of why gnome-keyring hadn't been upgraded sooner as with too much reshuffling, stuff will probably get dropped.

---

### Post by tista on 2012-03-05
> **jbicha said:**
> tista, I don't think this is specific to Ubuntu so you're welcome to report it on GNOME Bugzilla.

No relevant changes have been made on git since the version in the PPA and my quick search of bugzilla didn't show that this has been reported yet.

This is part of why gnome-keyring hadn't been upgraded sooner as with too much reshuffling, stuff will probably get dropped.

OK.. I would file this issue to bugzilla upstream ASAP... ;)

And good to know why it took long time to bump to...

Cheers,
Tista

**P.S:**
I've posted bug report to bugzilla:
[https://bugzilla.gnome.org/show_bug.cgi?id=671441]("https://bugzilla.gnome.org/show_bug.cgi?id=671441")

I hope it could help the devs... ;)

---

### Post by hugmenot on 2012-03-06
It works fine here. The flat list is a good idea.

Only issues I have are designwise (why does he have to make it look like nautilus? How do I focus the search field?) and a probable Chromi bug (all chrome passwords are duplicated).

---

### Post by Mr. Picklesworth on 2012-03-06
> **jbicha said:**
> Thanks, I can confirm that bug. Do you want to report it?

Okay, I reported that one over here:
[https://bugzilla.gnome.org/show_bug.cgi?id=671525](https://bugzilla.gnome.org/show_bug.cgi?id=671525)

I haven't reported the one with Configure for Secure Shell not doing anything (yet). Were you able to reproduce that problem, too?

---

### Post by tista on 2012-03-08
@jbicha

now that bug what I've posted to upstream bugzilla ([https://bugzilla.gnome.org/show_bug.cgi?id=671441]("https://bugzilla.gnome.org/show_bug.cgi?id=671441")) seems to be fixed by seahorse devs.. ;)

So if you have much time to work on it, please sync to upstream git master codes.

Best regards,
Tista

**EDIT**
Oh now it had been released as "3.3.5-0ubuntu1~precise2"?! seems to be fixed!! :)

Then I've noticed today I could not login into any sessions via gdm-3.2.1 anymore... although automatic-login seems well, but gdm-greeter never accept for my password on standard login... grrr :(

---

### Post by jbicha on 2012-03-08
Rico has a good working patch to build GNOME Shell without needing the new gnome-keyring. Since the "need" for the new code is gone, gnome-keyring will almost certainly stay at 3.2 in the normal Ubuntu repositories for 12.04 as the Ubuntu developers are trying to reduce risk where possible. It'll still be in the GNOME 3 PPA for those that want it.

Thanks for your help! We only found two bugs (neither of which has been reported before) and one of those has already been fixed.

---

