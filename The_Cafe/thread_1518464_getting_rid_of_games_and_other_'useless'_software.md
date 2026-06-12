---
title: "getting rid of games and other 'useless' software"
date: 2010-06-26
forum: The Cafe
---

### Post by wannabegeek on 2010-06-26
waz up folks,

I just wanna vent a little and say that it's really annoying un-installing  all the 
funky little games that come with my ubuntu installation...

Should I use a different option when installing to avoid having to go through 
this clean up process ?

thanks,
wbg

---

### Post by CharlesA on 2010-06-26
Wouldn't the minimal cd work for that?

---

### Post by Stancel on 2010-06-26
the default games suck so bad. Some of them are good (Solitaire is always fun of course), but more than a few are just awful.

---

### Post by Lucradia on 2010-06-26
> **CharlesA said:**
> Wouldn't the minimal cd work for that?

+1 to that.

After installing mini.iso,

sudo apt-get install gnome

BOOM! All done.

---

### Post by K.Mandla on 2010-06-26
> **Lucradia said:**
> +1 to that.

After installing mini.iso,

sudo apt-get install gnome

BOOM! All done.
After [xorg]("http://packages.ubuntu.com/search?keywords=xorg"), you could also install [gnome-desktop-environment]("http://packages.ubuntu.com/search?keywords=gnome-desktop-environment") or [gnome-core]("http://packages.ubuntu.com/search?keywords=gnome-core"), both of which are lighter than the default, but still bring in the basic Gnome environment.

Of course, if you're using Arch Linux, you can install the gnome and gnome-extras groups and get a system that boots on 75Mb or so. ...

---

### Post by Kdar on 2010-06-27
You can disable links in the menu. I am pretty sure they don't take up as much space.

---

### Post by Paqman on 2010-06-27
> **K.Mandla said:**
> 
Of course, if you're using Arch Linux, you can install the gnome and gnome-extras groups and get a system that boots on 75Mb or so. ...

That's about what gnome-core will boot to on Ubuntu minimal.

---

### Post by cascade9 on 2010-06-27
> **K.Mandla said:**
> Of course, if you're using Arch Linux, you can install the gnome and gnome-extras groups and get a system that boots on 75Mb or so. ...

Not that impressive, really. 75MB? Without all the stuffing around you have to do with arch, a (stock) debian Xfce install is 70MB or under.

> **Kdar said:**
> You can disable links in the menu. I am pretty sure they don't take up as much space.

Yes, but why would you? Its a dirty hack, and a minimal install is a much better option IMO. That would depend on what other stuff the OP uses though.

---

### Post by Lucradia on 2010-06-27
> **Kdar said:**
> You can disable links in the menu. I am pretty sure they don't take up as much space.

Actually... some of the games _alone_ take upwards of 10-15 MB of space, and yes, some of them are loaded by default. Go figure.

---

### Post by K.Mandla on 2010-06-27
> **Paqman said:**
> That's about what gnome-core will boot to on Ubuntu minimal.
Hmm. Not in my experience. 

[http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/](http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/)

> **cascade9 said:**
> Not that impressive, really. 75MB? Without all the stuffing around you have to do with arch, a (stock) debian Xfce install is 70MB or under.
And an Xfce install in Arch?

---

### Post by cascade9 on 2010-06-27
> **K.Mandla said:**
> And an Xfce install in Arch?

Around 65MB IIRC (which pretty much what debian stable/squeeze/sid/sidux is as well). 

I dont have a running arch install now, so no way of checking that.

---

### Post by yester64 on 2010-06-27
> **wannabegeek said:**
> waz up folks,

I just wanna vent a little and say that it's really annoying un-installing  all the 
funky little games that come with my ubuntu installation...

Should I use a different option when installing to avoid having to go through 
this clean up process ?

thanks,
wbg

Never wasted time thinking about the games. They are small and don't take a lot of space anyway.
But you can of course uninstall them. Not sure if you can avoid them at installation. That would be perhaps better.

---

### Post by Lucradia on 2010-06-27
> **yester64 said:**
> Never wasted time thinking about the games. They are small and don't take a lot of space anyway.
But you can of course uninstall them. Not sure if you can avoid them at installation. That would be perhaps better.

Download the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

after installation...

```
sudo apt-get install gnome-core xorg gdm synaptic
```

Then use synaptic as you would before software center. (Software center is not installed with gnome nor gnome-core metapackages.)

---

### Post by WinterRain on 2010-06-27
> **Lucradia said:**
> Actually... some of the games _alone_ **take upwards of 10-15 MB of space**, and yes, some of them are loaded by default. Go figure.

**[SIZE="6"]Say it isn't so![/SIZE]**
[IMG]http://static.open.salon.com/files/home-alone1243399120.png[/IMG]

---

