---
title: "Why do i have Online Accounts twice?"
date: 2012-10-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-10-12
is this a bug?
why do i have Online Accounts twice?
even thou i have no chat client installed and i have perform this command several times:
sudo apt-get remove gnome-online-accounts*
sudo apt-get purge gnome-online-accounts*
sudo apt-get autoremove
sudo apt-get autoclean

---

### Post by jbicha on 2012-10-12
That's bug [1040193]("http://pad.lv/1040193"). I gave a partial and somewhat grumpy explanation on my [blog]("http://jeremy.bicha.net/2012/10/06/ubuntu-online-accounts-and-gnome/").

---

### Post by x-shaney-x on 2012-10-12
This is all pretty awful, if not that major a deal really.
I had been a big fan of unity til recently but I feel I hate it more and more.

I'm all for distros coming up with their own desktop environments and such but I feel these environments should work with other environments, not break them.

---

### Post by funicorn on 2012-10-13
Because you are using gnome3 and ricotz testing/stable ppa, which is not good. gnome-control-panel 3.6.0 is not for Unity and it works not properly.  So purge these ppas soon.

---

### Post by kuvanito on 2012-10-13
> **funicorn said:**
> Because you are using gnome3 and ricotz testing/stable ppa, which is not good. gnome-control-panel 3.6.0 is not for Unity and it works not properly.  So purge these ppas soon.
dead wrong!
i am not using any ricotz ppa for your information
and this is a BUG!

---

### Post by cariboo on 2012-10-13
> **kuvanito said:**
> dead wrong!
i am not using any ricotz ppa for your information
and this is a BUG!

Have you filed a bug report yet?

---

### Post by funicorn on 2012-10-13
That's not an affirmative evidence. It's possible you upgraded gnome-control-panel using some ppa to 3.6.0 then disable it. To confirm this, type in terminal
```

apt-cache madison gnome-control-panel
dpkg -l gnome-control-panel

```
The first command outputs available package versions in the repository, and the second displays that of the currently installed. Compare and check whether you are using a version other than all available ones in the current repository.

---

### Post by Mr. Picklesworth on 2012-10-13
cariboo907, funicorn: jbicha already pointed to the bug report. Just scroll up and everything will make sense :)

The issue is reported in [bug #1040193]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1040193"). This happens out of the box if you use System Settings with any session other than Unity. As I wrote the bug description, just run this in a terminal and you can see for yourself:
```
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```

---

### Post by cariboo on 2012-10-13
> **Mr. Picklesworth said:**
> cariboo907, funicorn: jbicha already pointed to the bug report. Just scroll up and everything will make sense :)

The issue is reported in [bug #1040193]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1040193"). This happens out of the box if you use System Settings with any session other than Unity. As I wrote the bug description, just run this in a terminal and you can see for yourself:
```
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```

I realized that, after opening this thread again, at times even I don't read every thread from the start, even though I urge others to do so. :-D

---

### Post by scradock on 2012-10-13
This is all very confusing! Are you guys in the same universe as I am? I am running an updated (current) QQ with almost nothing removed, but I find (either installed or available with the standard repos - no ppas):

NO package named gnome-control-panel - it's gnome-control-center

NO package named ubuntu-online-accounts - only gnome-online-accounts

Has the offending package simply been eliminated?

---

### Post by mc4man on 2012-10-14
> **scradock said:**
> This is all very confusing! Are you guys in the same universe as I am? I am running an updated (current) QQ with almost nothing removed, but I find (either installed or available with the standard repos - no ppas):

NO package named gnome-control-panel - it's gnome-control-center

NO package named ubuntu-online-accounts - only gnome-online-accounts

Has the offending package simply been eliminated?

confusing, yes.
panels are generally in gnome-control-center package though I believe uoa comes from gnome-control-center-signon & or deps of.

Saw a weird happening here where I don't use online accounts (goa or uoa), & most of the related had been removed. 
(have some needed to run gnome-shell on another user account & build the latest totem git to ck. some recent fixes.
 Out of the blue starting getting a red cog warning for 'online accounts' on a unity only user that showed up on every login after nautilus or FF were opened. Clicking on produced the 'dead end' as seen in screen

Finally resolved though haven't discovered the cause

---

### Post by funicorn on 2012-10-14
sorry I input the wrong package name, it should be gnome-control-center, as you've mentioned. Still you should check the package versions as I suggested.

---

### Post by kuvanito on 2012-10-14
i am laughing my head off
i started this thread as i was seen double or a ghost,never mind it was a BUG,some said no,some said yes and finally i see every one seing what i saw,this is kind of funny,at least the last one by mc4man and the pic,no account for null,hehehehehe :lolflag:

---

