---
title: "Adding Basic UI for Server Admin Noob"
date: 2006-12-09
forum: Server Platforms
---

### Post by ccheatham on 2006-12-09
I have two Ubuntu installs on computers my neighbor put in the trash.  I chose the server install on one to keep things light but, it would be nice if i could use a UI to do stuff if I wanted.  The other box i used the desktop distro.  I would like to VNC to the server eventually after I stick it in a closet!  Thanks in advance for ideas :).

---

### Post by tturrisi on 2006-12-09
lightweight gui:
xorg (gui)
fluxbox (lightweight window manager)
nedit (powerful lightweight txt editor)
emelfm (file manager)
dillo (lightweight web browser)
apt-get install fluxbox xorg nedit emelfm dillo

if prefer gnome then just do:
apt-get install xorg gnome-core

...and your vnc package of choice.

---

### Post by drokmed on 2006-12-14
Webmin.

It's a basic admin gui you install on the server.  From any pc, point your web browser to the server, login, and it has icons/modules to configure pretty much everything on your server, including stuff you never knew was there!

I install webmin on all my servers, it rocks.

---

### Post by chrisfay on 2006-12-14
> I install webmin on all my servers, it rocks.

Agreed!

I also put Webmin on all my servers, especcially if someone else needs to manage anything. 

Just watch out for new packages and the default location that webmin looks to edit their configuration files. I haven't installed Webmin in a while but I remember it defaulted to editting Apache1's config files even though I had installed Apache2. Just something to look out for.

Don't be afraid of the CLI, it beats all!

---

### Post by pmasiar on 2006-12-14
very light, character-based, but still very visual: **midnight commander**. You can even create your own commands: couple lines long bash scripts, and you can run them from the menu (F2). Best tool ever - and includes oldish, but still very useful visual editor. First tool I install on all my boxes. mc to the rescue!

---

### Post by drokmed on 2006-12-15
> **chrisfay said:**
> Agreed!

I also put Webmin on all my servers, especcially if someone else needs to manage anything. 

Just watch out for new packages and the default location that webmin looks to edit their configuration files. I haven't installed Webmin in a while but I remember it defaulted to editting Apache1's config files even though I had installed Apache2. Just something to look out for.

Don't be afraid of the CLI, it beats all!

You brought up a point I didn't want to mention :)

Now that you have, yes, it's true, we sometimes have to give other people access to the management tools we use.  Fortunately, webmin lets you create individual users personal access logins.  However, it's a good thing, to limit someone else (besides me!) to access webmin, but only for what I want.

Just for the record, i've only given two others access to one of my webmin servers... both for the same reason.  I have a squid/dansguardian server, and the owner of the company wants to see who accesses what.  I gave him (only) access to the sarg reporting tools, to see who is surfing the web when and where.  He demanded it, so I complied.  Objective satisfied acceptably.

The other is similar, but a manager who wants to modify the dansguardian permissions, for his department.  Alas, he doesn't understand all the technical implications, but he is learning the access controls.  It takes time for me to teach him, but he is a better manager for it.

For the people reading this thread who use webmin, it's not the end all, but it sure makes life easier in many situations.  I've had to train two people to access it, and I control their access.  It's helped my job alot.  I find it a very useful tool.

lol I just re-read the original poster.  Basic IU for server admin noobs?  Dude, read up on webmin, it's a nice start.  Always remember, read up!  Ask in the forums!  Search first though :) the same questions get asked over and over, over time that is...

Good luck.

---

