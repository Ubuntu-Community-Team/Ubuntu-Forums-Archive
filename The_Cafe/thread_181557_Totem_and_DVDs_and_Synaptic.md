---
title: "Totem and DVDs and Synaptic"
date: 2006-05-24
forum: The Cafe
---

### Post by Dralt on 2006-05-24
Yesterday, I tried to get Totem to play DVDs. It requires quite a mess of packages, official, unofficial, legal, illegal, good, bad, ugly, various versions of various libraries, etc.

In brief, I couldn't get it to work. Even after I found and ran "bumps".

While doing this, a lot of packages got installed and I might want to revert to the point prior to this failed attempt.

Is there a way to tell Synaptic or apt to uninstall all packages installed after a certain date and time?

---

### Post by meng on 2006-05-24
Hmm, I'd like to know this too. Up until now, I've been doing this manually by looking at History under Synaptic, and deselecting the packages.

---

### Post by BoyOfDestiny on 2006-05-24
[QUOTE=Dralt]Yesterday, I tried to get Totem to play DVDs. It requires quite a mess of packages, official, unofficial, legal, illegal, good, bad, ugly, various versions of various libraries, etc.

In brief, I couldn't get it to work. Even after I found and ran "bumps".

While doing this, a lot of packages got installed and I might want to revert to the point prior to this failed attempt.

Is there a way to tell Synaptic or apt to uninstall all packages installed after a certain date and time?[/QUOTE]

This isn't really an answer, but I think it's worth mentioning. You do not need to enable unnofficial repositores to get DVD playback in totem. I'm running on dapper 64, and most of these repos were for 32-bitters' anyway...

There seems to be a fluendo plugin, haven't made use of it yet though... There is a decss script included with ubuntu for encrypted dvd playback... The rest, gstreamer .10 should have you covered...

You are running dapper right?

---

### Post by GarethMB on 2006-05-24
You need one deb file i believe libdvdcss.deb google it.

---

### Post by BoyOfDestiny on 2006-05-24
[QUOTE=GarethMB]You need one deb file i believe libdvdcss.deb google it.[/QUOTE]

Fine, I'll just give the location of the ubuntu script...

Warning, do not use this in the U.S, since it is illegal to watch your own DVD's (well those with CSS encryption) on Linux with unlicensed players.

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by Dralt on 2006-05-24
[QUOTE=BoyOfDestiny]This isn't really an answer, but I think it's worth mentioning. You do not need to enable unnofficial repositores to get DVD playback in totem. I'm running on dapper 64, and most of these repos were for 32-bitters' anyway...

There seems to be a fluendo plugin, haven't made use of it yet though... There is a decss script included with ubuntu for encrypted dvd playback... The rest, gstreamer .10 should have you covered...

You are running dapper right?[/QUOTE]

Yes, Dapper.

---

### Post by Dralt on 2006-05-24
[QUOTE=BoyOfDestiny]Fine, I'll just give the location of the ubuntu script...

Warning, do not use this in the U.S, since it is illegal to watch your own DVD's (well those with CSS encryption) on Linux with unlicensed players.

sudo /usr/share/doc/libdvdread3/examples/install-css.sh[/QUOTE]

Thanks for that! I'll give it a try tonight.

Any idea about my original question?

Is there a way to tell Synaptic or apt to uninstall all packages installed after a certain date and time?

My previous attempts led me to install packages from unofficial repositories, doubtful versions of doubtful libraries, etc.

---

### Post by andy101 on 2006-05-24
If you installed it from an unoffical repositry, if the repositry is no longer in your list, you can list all packages not found in the remaining (i.e. offical) repositries.

Open Synaptic, on the left hand side underneath the big list of catergories select: "status", this list should change, from this select "Installed (local or obsolete)"

this should show you packages installed either manually, or from a repositry you have since removed.

In mine I have castpodder, libdvdcss2 and others

---

### Post by Dralt on 2006-05-24
[QUOTE=andy101]If you installed it from an unoffical repositry, if the repositry is no longer in your list, you can list all packages not found in the remaining (i.e. offical) repositries.

Open Synaptic, on the left hand side underneath the big list of catergories select: "status", this list should change, from this select "Installed (local or obsolete)"

this should show you packages installed either manually, or from a repositry you have since removed.

In mine I have castpodder, libdvdcss2 and others[/QUOTE]

Once I'm done with that, is there a place where I could fetch the default source.list.
I have playing with my current source.list so much, I'm not sure if it's back to where it started after installation.

---

### Post by Iandefor on 2006-05-24
[quote=BoyOfDestiny]Fine, I'll just give the location of the ubuntu script...

Warning, do not use this in the U.S, since it is illegal to watch your own DVD's (well those with CSS encryption) on Linux with unlicensed players.

sudo /usr/share/doc/libdvdread3/examples/install-css.sh[/quote] Doesn't that require that libdvdread be installed already?

---

### Post by BoyOfDestiny on 2006-05-24
[QUOTE=Iandefor]Doesn't that require that libdvdread be installed already?[/QUOTE]

I believe it comes standard with the ubuntu install. I did not have to download it manually from synaptic, unless something I chose grabbed it as a dependency (gstreamer .10, vlc, mplayer, etc)

I can testify that it works fine though.

---

### Post by mapuo on 2006-05-25
I got Totem to play DVD's but there's no DVD Menus support... Totem just plays the first movie in the disc. Anyone with idea how to enable the DVD Menus support?

P.S. I got the libdvdnav4 package installed and the menus works with VLC, but i want to see the menus in Totem too.

---

