---
title: "[SOLVED] Gnome Flashback no longer works in Wily"
date: 2015-05-30
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-05-30
Gnome Flashback no longer works in Wily, after the last upgrade. There is no gnome-flashback-session in the repos.

---

### Post by kerry_s on 2015-05-30
they probably assume everyone will just use ubuntu-mate now that it's a offical ubuntu. which makes since for people who want to use but don't want to be left behind.

i use ubuntu-mate 15.04 currently.

---

### Post by deadflowr on 2015-05-30
The package name is gnome-session-flashback, fwiw
You can still install it.

currently for me:
```
gnome-session-flashback:
  Installed: 1:3.14.0-3ubuntu11
  Candidate: 1:3.14.0-3ubuntu11
  Version table:
 *** 1:3.14.0-3ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages
        100 /var/lib/dpkg/status
```
It still runs fine for me.

And flashback always gives you two sessions to choose from.(effects or no-effects)
Are both busted for you?

---

### Post by Chanath on 2015-05-30
> **deadflowr said:**
> The package name is gnome-session-flashback, fwiw
You can still install it.

currently for me:
```
gnome-session-flashback:
  Installed: 1:3.14.0-3ubuntu11
  Candidate: 1:3.14.0-3ubuntu11
  Version table:
 *** 1:3.14.0-3ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages
        100 /var/lib/dpkg/status
```
It still runs fine for me.

And flashback always gives you two sessions to choose from.(effects or no-effects)
Are both busted for you?

I reinstalled that again, and it started working. By the way, when you install Gnome-session-flashback in Ubuntu-Gnome, you get only the one with Metacity, as there is no Compiz installed.

---

### Post by Chanath on 2015-05-30
> **kerry_s said:**
> they probably assume everyone will just use ubuntu-mate now that it's a offical ubuntu. which makes since for people who want to use but don't want to be left behind.

i use ubuntu-mate 15.04 currently.

I might use Ubuntu-Mate, but I'd have to re-install Gnome apps or XFCE apps, such as Files or Thunar, Gedit, etc. I don't like some of the Mate apps, in other words, I'm not used to such apps. I actually like Gnome 3 and KDE5 Plasma. I've made my Xubuntu to look even prettier. All are Wily now.

Thanks Kerry, I'd try Ubuntu-Mate. I'd see, if I can install my usual apps and make it prettier.

---

### Post by kerry_s on 2015-05-30
> **Chanath said:**
> I might use Ubuntu-Mate, but I'd have to re-install Gnome apps or XFCE apps, such as Files or Thunar, Gedit, etc. I don't like some of the Mate apps, in other words, I'm not used to such apps. I actually like Gnome 3 and KDE5 Plasma. I've made my Xubuntu to look even prettier. All are Wily now.

Thanks Kerry, I'd try Ubuntu-Mate. I'd see, if I can install my usual apps and make it prettier.

i just got use to the mate apps. i only install xfce4-appfinder for use on my dock(plank) as my menu. i'm using a netbook, so i use mate-netbook to maximize my small 10" screen.

but yeah, you should try mate if you haven't in awhile. with 15.04 they have panel profiles so you can select the type of panel setup you want to start with than tweak from there. i use eleven cause i like the dock style.

---

### Post by QDR06VV9 on 2015-05-30
Mate for this Old Fart is like coming back Home.LOL It's just nice and comfortable. 
@Chanath You won't get left behind if you stay in touch with the forums here.
We leave no one Behind:)
Sorry Off Topic

---

### Post by Hazzabin on 2015-05-31
I go with runrickus comment, and I'm running Mate 15.10, it is good

---

### Post by kerry_s on 2015-05-31
> **Hazzabin said:**
> I go with runrickus comment, and I'm running Mate 15.10, it is good

does it have mate 1.10 yet ? system monitor-> system

---

### Post by Chanath on 2015-05-31
> **runrickus said:**
> Mate for this Old Fart is like coming back Home.LOL It's just nice and comfortable. 
@Chanath You won't get left behind if you stay in touch with the forums here.
We leave no one Behind:)
Sorry Off Topic

Writing from Ubuntu-Mate 15.10 live. Its like coming back home. 
But, if Gnome-flashback would still be there, I'd use Gnome3, so I could have both Gnome-shell and Flashback.

---

