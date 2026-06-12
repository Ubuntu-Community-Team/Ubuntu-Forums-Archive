---
title: "what add-ons (applet, skin, script, mods...) have you installed in Gnome Shell"
date: 2009-11-21
forum: The Cafe
---

### Post by legolas_w on 2009-11-21
Hi
I am wondering whether any one here is aware of add-ons for Gnome shell;
I am looking for applets, skins, mods, themes, or whatever installable for Gnome shell.

Thanks

---

### Post by Psumi on 2009-11-21
How do you install an applet? As far as I know, there are none.

I would really like the indicator applet in GNOME SHell, as well as a weather applet next to my time. But as far as I can tell, there are none.

By indicator applet, I mean the one that is currently readily available for the GNOME Panel. You also cannot start GNOME Panel while in GNOME Shell, so do not tell me to do as such.

Also, similarly to another user, I cannot use ALT+Tab to switch applications in GNOME Shell. I would like to have that available as well as the ALT+F2 dialog telling me commands I can choose from as I type (similar to the current GNOME Panel version.)

---

### Post by zagz on 2009-11-21
A quick question, If you are running Gnome shell then every time you update your system does Gnome shell get updated (providing there are available updates)?

tia

---

### Post by Psumi on 2009-11-21
> **zagz said:**
> A quick question, If you are running Gnome shell then every time you update your system does Gnome shell get updated (providing there are available updates)?

tia

If it is like any other application provided in the ubuntu repos, then no. It only updates when there are security updates.

---

### Post by zagz on 2009-11-21
> **Psumi said:**
> If it is like any other application provided in the ubuntu repos, then no. It only updates when there are security updates.


I tried GS about 3 weeks ago from the repos so I guess there's no real point in trying again to see if anything has come along.

---

### Post by fanum on 2010-03-08
> **legolas_w said:**
> Hi
I am wondering whether any one here is aware of add-ons for Gnome shell;
I am looking for applets, skins, mods, themes, or whatever installable for Gnome shell.

Thanks

There are some themes available now, The install process is alittle more involved than normal, but definitely doable, here is a link:

[http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html](http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html)

---

### Post by Jesus_Valdez on 2010-03-08
> **fanum said:**
> There are some themes available now, The install process is alittle more involved than normal, but definitely doable, here is a link:

[http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html](http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html)
Thanks! I just installed the "forrest" one, really easy and painless.


Now i just need to figure out how to keep the ubuntu notification system and I'll be happy.

---

### Post by fanum on 2010-03-09
> **Psumi said:**
> If it is like any other application provided in the ubuntu repos, then no. It only updates when there are security updates.

I think he was asking if you installed it from a repo, or compiled it yourself. If you did install from a repo, did you used the one found in the standard ubuntu repos? If so it is very out of date, and you will want to install from a PPA, I would suggest Ricotz, run this command in terminal:

sudo add-apt-repository ppa:ricotz/testing

then this one:

sudo apt-get upgrade

and as usual, run gnome shell using this command:

gnome-shell --replace

---

### Post by fanum on 2010-03-09
> **Psumi said:**
> How do you install an applet? As far as I know, there are none.

I would really like the indicator applet in GNOME SHell, as well as a weather applet next to my time. But as far as I can tell, there are none.

By indicator applet, I mean the one that is currently readily available for the GNOME Panel. You also cannot start GNOME Panel while in GNOME Shell, so do not tell me to do as such.

Also, similarly to another user, I cannot use ALT+Tab to switch applications in GNOME Shell. I would like to have that available as well as the ALT+F2 dialog telling me commands I can choose from as I type (similar to the current GNOME Panel version.)

As far as alt-tab, i have not gotten it working yet either, although, it is a feature that has been implemented in the PPA i have reffered to in my previous post. Here is what some people have done to get it working:

Quoting vange from a post on this forum link:
[http://ubuntuforums.org/showthread.php?t=1327681](http://ubuntuforums.org/showthread.php?t=1327681)

I got it working! Use gconf-editor and check your settings for the key apps->metacity->global_keybindings->switch_windows. For details, see this link: [https://bugzilla.gnome.org/show_bug.cgi?id=591671](https://bugzilla.gnome.org/show_bug.cgi?id=591671)

---

### Post by fanum on 2010-03-09
> **Jesus_Valdez said:**
> Thanks! I just installed the "forrest" one, really easy and painless.


Now i just need to figure out how to keep the ubuntu notification system and I'll be happy.

Are you referring to the new notification system available since 9.10? as far as i know, there are no plans on including that in gnome shell. They do have a new version, that has only been included since that last release, that is an improvement over the Ubuntu one (in my opinion), the alerts appear at the bottom of the screen, and will soon be interactive (something that is not available in the Ubuntu alerts).

---

### Post by Mystro256 on 2011-05-18
Not to bump and old tread but I found this today: [http://danigm.net/node/149](http://danigm.net/node/149). It's incomplete but works!

---

