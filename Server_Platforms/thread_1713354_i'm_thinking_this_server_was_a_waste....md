---
title: "i'm thinking this server was a waste..."
date: 2011-03-24
forum: Server Platforms
---

### Post by adduds on 2011-03-24
k so here's the deal i've been running a ubuntu server box 10.10 for about two weeks now as far as getting  software like pms-linux, transmission-daemon, webmin installed and working was easy

i'm using this box mainly for downloading movies and streaming them in my house aswell as music through a firefly a DAAP stream

my problem is i'm downloading movies that are .rar files that need special unpacking, or .mkv that need reauthoring to play on my ps3 and can't really do it from the box without a gui...or don't know how

it just seems that this server is alot more work that i thought it'd be...i'd love to have my gui back but it seemed to load videos slower fast forward and rewind are/were laggy

seems that i'm not set up quite right does everyone have trouble constantly with their boxes? or am i just learning??

---

### Post by cariboo on 2011-03-24
There are several lightweight desktops available in the repositories, you don't have to use the ubuntu desktop, another suggestion would be to not install gdm/kdm/xdm, and just start the gui when you need it by entering startx at the prompt, then longing out of the gui when you are finished.

For lightweight desktops, have a look at Lubuntu or the gnome-desktop-environment.

---

### Post by adduds on 2011-03-24
i've done some reading and i really do like the suggeestion of starting and stopping on a need to need basis as the keeps the cpu cycles to a min...

i've seen open box it seems to be reputable?

---

### Post by volkswagner on 2011-03-24
.rar files should not require a GUI.

What trouble have you had?

There is a lot of documentation on the subject.  Perhaps tackling one item at a time, you can have your terminal working for you!  

[OneLink]("http://ubuntuforums.org/showthread.php?t=248165").

---

### Post by SeijiSensei on 2011-03-24
> **adduds said:**
> my problem is i'm downloading movies that are .rar files that need special unpacking, or .mkv that need reauthoring to play on my ps3 and can't really do it from the box without a gui...or don't know how

The command-line rar and unrar programs are in the repositories.  They don't ship by default because there are patents involved.  As for reauthoring .mkv to.mp4, the command line programs mencoder and ffmpeg can handle these tasks.  They're not for the faint-of-heart, though.  These are extremely powerful programs with a *lot* of [options]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html").

> it just seems that this server is alot more work that i thought it'd be...i'd love to have my gui back but it seemed to load videos slower fast forward and rewind are/were laggy

It sounds to me like you'd be much better off using the desktop version.  The difference between it and the server version is largely what packages are installed by default.  The server version is more appropriate for professional users who are accustomed to using the command line and who want things like the Apache web server and the Postfix SMTP server installed by default.

---

### Post by adduds on 2011-03-26
running desktop version won't that effect transcoding videos to a ps3?

---

### Post by CharlesA on 2011-03-26
> **adduds said:**
> running desktop version won't that effect transcoding videos to a ps3?
It probably won't.

---

### Post by adduds on 2011-03-27
well this is good news :) lol

i want to be able to change mkv to some format to burn it to a standard dvd so i can use it in a standard dvd player :)

---

### Post by SeijiSensei on 2011-03-27
Use [mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html") if you want complete control over the entire process from the command line; [DeVeDe]("http://packages.ubuntu.com/lucid/devede") if you want a decent gui interface to mencoder.  DeVeDe also lets you make DVD menus.  It has an annoying [bug]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011") when dealing with MKV sources, though; it's unable to calculate the size of the resulting file it creates on the DVD.  I've found I've needed to make a couple of trial runs with different bitrates entered manually.

For streaming to a PS3 take a look at [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/").

---

### Post by adduds on 2011-03-29
could i install desktop edition on my server box and start the gnome environment as needed from ssh? and then view my desktop via vnc over my home network?

---

