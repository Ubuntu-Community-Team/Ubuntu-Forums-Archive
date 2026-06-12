---
title: "Idea:  Ultralight Ubuntu LiveCD"
date: 2005-08-20
forum: The Cafe
---

### Post by Brunellus on 2005-08-20
I'm a big LiveCD fan--it was a live CD that got me into Linux in the first place (Suse 9.1 live).  The fact that it's even possible to run a fairly complete OS from a single CD is a neat trick.

The Ubuntu livecds are excellent.  They bring Ubuntu's awesome hardware-detection and nice user environment to the masses.  Heck, Hoary Live wowed my non-techie, Windows-using best friend.

There's only one problem with it that I see--it's huge, and as a result, seems to run rather sluggishly.  More lightweight live distros like   [Damn Small Linux]("http://www.damnsmalllinux.org").  and [SLAX]("http://slax.linux-live.org/") are lighting-quick and responsive.  (My personal take on the latest version of SLAX is on my [blog]("http://www.livejournal.com/users/ouij")).

This got me to thinking--what if I could make a really cut-down (under 200MB) Ubuntu live cd?  

I'd have to get rid of a lot of cruft.  Most of the games would have to go.  GIMP would go.  Evolution would be replaced by sylpheed; firefox by enlightenment;  gnome itself by XFCE 4.  OpenOffice would have to yield to AbiWord (perhaps with a plugin to read/write .sxw files).  And so on.  I'd call it ***Ubique***--Latin for "everywhere".

So I have the idea in mind--I just need to know how to do it.  Questions:

1) is there a howto on how to remaster the existing ubuntu live cd for x86?

2) is there another such project underway anywhere?

3) am I the only one who thinks this would be a neat idea?

Comments, please!

---

### Post by BWF89 on 2005-08-21
But if you left all those things out you would have to have some sort of text come up as soon as you got to the desktop saying "Since running an entire operating system directly from a CD-ROM is very resource hogging we have left out many of the programs that come with the default setup of Ubuntu including a graphics editor, an office suite". Or people would think that Linux was just something  that only has a handful of programs to use.

As for replacing Gnome with Xfce. That's just not a good idea. I'm not saying theres anything wrong with Xfce but when you install Ubuntu it doesn't defaultly boot up with Xfce. So when your average unknowing computer user tried the Ubuntu live cd and decides to put it on his computer and the OS looks completely different he's going to think he did something wrong in the setup.

---

### Post by Brunellus on 2005-08-21
[QUOTE=BWF89]But if you left all those things out you would have to have some sort of text come up as soon as you got to the desktop saying "Since running an entire operating system directly from a CD-ROM is very resource hogging we have left out many of the programs that come with the default setup of Ubuntu including a graphics editor, an office suite". Or people would think that Linux was just something  that only has a handful of programs to use.

As for replacing Gnome with Xfce. That's just not a good idea. I'm not saying theres anything wrong with Xfce but when you install Ubuntu it doesn't defaultly boot up with Xfce. So when your average unknowing computer user tried the Ubuntu live cd and decides to put it on his computer and the OS looks completely different he's going to think he did something wrong in the setup.[/QUOTE]
 I don't intend to *replace* Ubuntu live, nor do Slax or DSL intend to replace Slackware or Debian (respectively).

They are different distributions, meant to serve different, and very specific needs.  Slax is meant to be portable and responsive--so you can carry the bare essentials of your favorite OS with you all the time.  

It isn't about winning over new users, necessarily.  I, personally, would like to carry Ubuntu with me all the time, but think it wasteful and inefficient to have to haul *everything* around with me as well.  I dont' do image editing when I'm on a live CD session, so strike GIMP altogether.  I don't need Rhythmbox's cataloging and indexing, either.  I don't need all of OOO's capabilities, only some of them.  I don't need to be able to play the dozen-odd games that are on there.

---

### Post by Burgundavia on 2005-08-21
Customizing ubuntu livecd
[https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo)

Also check out ubuntu-lite, which should make breezy+1

Corey

---

### Post by poofyhairguy on 2005-08-21
[QUOTE=Burgundavia]
Also check out ubuntu-lite, which should make breezy+1
[/QUOTE]

Basically:

Yes other people think its a good idea, and others are working on a light Ubuntu (using IceWM) for a future release. It would be great if you helped with that, but we would also welcome a new project as well. Anyone willing to put effort forth to help Ubuntu is a hero in this community.

---

### Post by ericsp on 2005-08-23
An ubuntu light version would be great. Where can I find info on the progress? I would favour an option when installing the full version of ubuntu:

( ) Standard (default)
( ) Light

Eric

---

### Post by Brunellus on 2005-08-23
[QUOTE=ericsp]An ubuntu light version would be great. Where can I find info on the progress? I would favour an option when installing the full version of ubuntu:

( ) Standard (default)
( ) Light

Eric[/QUOTE]
 Progress:  I'm still learning how to do it.  I won't even be able to do any real work on it until the weekend.

Just so you know--I'm not an official developer, nor do I even play one on TV.  Just an interested user who wants to see what he can do.

---

### Post by supernaut on 2005-08-23
How the hell would you replace Firefox with Enlightenment? Do you, perhaps, mean Dillo? Enlightenment is a desktop. ;)

---

### Post by Brunellus on 2005-08-23
[QUOTE=supernaut]How the hell would you replace Firefox with Enlightenment? Do you, perhaps, mean Dillo? Enlightenment is a desktop. ;)[/QUOTE]

I stand corrected.  Epiphany is what I meant.

---

### Post by xequence on 2005-08-23
I think it would be a good idea. The ubuntu live cd was really slow on my computer while installed to the hard drive it was faster...

---

### Post by drizek on 2005-08-23
I tried knoppix on my computer a couple days ago, and it was the fastest OS i have ever used.

you need 1gb of ram to run it, and when it is booting you have to type in "toram" and it copies the entire cd to ram and runs it from there. app launch speed was extremely fast and the whole thing was very responsive. if you have a gig or more of ram on your pc, i would recommend that you try it out.

an ubuntu live cd which would only require 512mb of ram rather than 1gb(knoppix has a LOT more apps installed than ubuntu) would be great. a "normal" option should still be available for those with less than 512mb of ram.

Edit: and OOo should be replaced by koffice, not abiword.

---

### Post by Brunellus on 2005-08-23
[QUOTE=drizek]I tried knoppix on my computer a couple days ago, and it was the fastest OS i have ever used.

you need 1gb of ram to run it, and when it is booting you have to type in "toram" and it copies the entire cd to ram and runs it from there. app launch speed was extremely fast and the whole thing was very responsive. if you have a gig or more of ram on your pc, i would recommend that you try it out.

an ubuntu live cd which would only require 512mb of ram rather than 1gb(knoppix has a LOT more apps installed than ubuntu) would be great. a "normal" option should still be available for those with less than 512mb of ram.

Edit: and OOo should be replaced by koffice, not abiword.[/QUOTE]

Since Ubuntu is, officially, a GNOME/GTK-based distribution, I wanted to stay with that.  GnomeOffice's Writer is Abiword.  

KDE-centric live CD distributions are fairly common.  Take your pick.  My favorite is SLAX, which will happily load to ram on 512 and maybe even 256 MB of RAM.

---

### Post by xequence on 2005-08-23
[QUOTE=Brunellus]Since Ubuntu is, officially, a GNOME/GTK-based distribution, I wanted to stay with that.  GnomeOffice's Writer is Abiword.  

KDE-centric live CD distributions are fairly common.  Take your pick.  My favorite is SLAX, which will happily load to ram on 512 and maybe even 256 MB of RAM.[/QUOTE]

Slax runs on 191 MB RAM ;D But for some reason it will only allow me to use 640*480 resolution... Ubuntu gives me 1024*768.

---

### Post by drizek on 2005-08-23
[QUOTE=xequence]Slax runs on 191 MB RAM ;D But for some reason it will only allow me to use 640*480 resolution... Ubuntu gives me 1024*768.[/QUOTE]
 no, load to ram is different. it copies the cd to ram and runs everything off of ram. it makes it extremely fast.

---

