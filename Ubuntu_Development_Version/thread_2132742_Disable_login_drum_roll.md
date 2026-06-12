---
title: "Disable login drum roll?"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by x-shaney-x on 2013-04-05
Alas, 13.04 beta has brought with it a whole host of annoyances/issues.

So working through one at a time:  the drum roll on login.
Aside from just being annoying, I find it causes my computer to hang for a good 2 or 3 seconds before I am able to type my password.
I had the same problem in 12.10 but I was able to disable the sound (which also stopped the hanging issue) by adding the following: ```
[com.canonical.unity-greeter]
play-ready-sound = false
```
to /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override

In 13.04 this doesn't work.

So any way to disable it?

---

### Post by jonobr on 2013-04-05
It should be in

System> Preferences> Start Up Applications

Deselect the  Login Sound

---

### Post by x-shaney-x on 2013-04-05
I don't remember seeing that option in startup for ages and even then I'm sure it affected the login melody thing that played when the desktop was loading.
I'm talking about the drum roll on the login (Light DM) screen itself.

---

### Post by mc4man on 2013-04-05
The greeter options are somewhat unchangeable as a user though you can see them all in dconf-editor > com.canonical.unity-greeter
You could try disabling the sound there, whether it works or not don't know.
(in various bug reports on such it's been posted how to effect such changes, don't bother with anymore..

Another way that works here is to change the default, whether you should do so I don't know, did so here but I've no real attachment to my ubuntu install(s), ect.

```
gksudo gedit  /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
scroll down to bottom & edit the default for "play-ready-sound" to false
Then save, close gedit
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
Should execute without comment or error, if it does read carefully
Then  try a restart & see..

---

### Post by x-shaney-x on 2013-04-05
Well the first thing I noticed when I tried that is that I was told gksudo isn't installed.
I have read in recent times that one shouldn't run gedit as sudo but use gksudo instead but now it isn't installed?  Is this a beta error or just no longer available by default?

In any case, the drum roll is the least of my problems.  Having so many issues and had forgotten just how many workarounds I have to do on ubuntu these days to get things up and running to my liking, everything from getting brightness to work to getting 3 finger touchpad taps working.
Nothing to do with it being beta, just to do with ubuntu and partially my stupid laptop, though I don't have this many issues with other distros.
Shame as unity is taking shape so nicely...

But anyway, veering off-topic! But thanks for the info.  The code does work for me and I will refer back to it if I come back to ubuntu.

---

### Post by mc4man on 2013-04-05
gksu was not included in some daily images a little bit back (saw the same here),  but is currently back in.
(reason why it was pulled for a short time is unclear.
As far as 'sudo gedit' - 
In the past never saw any issue using that but as of 13.04 would not, would either use gksudo or go  to a root prompt first, then run gedit or just use nano or similar.
Can be seen by altering pref.'s for gedit, if one then used sudo gedit  it would open with your user pref.'s, not root's,  so seems a bad idea.

Has been mentioned that gksu(do) is on it's way out in Ubuntu in favor of pkexec but that doesn't appear to have materialized yet.

If one did install gksu on an install where it wasn't inc. then after installing must run gksu-properties & change mode from su to sudo

---

### Post by zika on 2013-04-06
```
alias gsudo='/usr/bin/sudo -H'
```

---

### Post by Courtney_Bodi on 2013-09-04
> **mc4man said:**
> The greeter options are somewhat unchangeable as a user though you can see them all in dconf-editor > com.canonical.unity-greeter
You could try disabling the sound there, whether it works or not don't know.
(in various bug reports on such it's been posted how to effect such changes, don't bother with anymore..

Another way that works here is to change the default, whether you should do so I don't know, did so here but I've no real attachment to my ubuntu install(s), ect.

```
gksudo gedit  /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
scroll down to bottom & edit the default for "play-ready-sound" to false
Then save, close gedit
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
Should execute without comment or error, if it does read carefully
Then  try a restart & see..

Thank you so much! This method worked perfectly for me, as far as I know : )

---

