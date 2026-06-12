---
title: "Would you want a klik for Ubuntu?"
date: 2005-08-03
forum: The Cafe
---

### Post by poofyhairguy on 2005-08-03
This site is neat:

[http://klik.atekon.de/](http://klik.atekon.de/)

Do you think it would be cool if Ubuntu had something like that, or is synaptic enough?

Cool part about Klik is that it wouldn't need official support, anyone can do it!

I wonder what answers will be.

---

### Post by poofyhairguy on 2005-08-03
Amazing!!!!

[http://klik.atekon.de/architecture/](http://klik.atekon.de/architecture/)

Comment on Ubuntu:

[http://klik.atekon.de/docs/?page=Using%20klik%20with%20other%20distros](http://klik.atekon.de/docs/?page=Using%20klik%20with%20other%20distros)

> 
klik in principle works with Ubuntu, but it is not yet officially supported. Please see [http://www.knoppix.net/forum/viewtopic.php?p=73016#73016](http://www.knoppix.net/forum/viewtopic.php?p=73016#73016) 

---

### Post by Lowe on 2005-08-03
[QUOTE=poofyhairguy]Amazing!!!!

[http://klik.atekon.de/architecture/](http://klik.atekon.de/architecture/)

Comment on Ubuntu:

[http://klik.atekon.de/docs/?page=Using%20klik%20with%20other%20distros](http://klik.atekon.de/docs/?page=Using%20klik%20with%20other%20distros)[/QUOTE]
 It's still very buggy, i tried it on kannotix a month ago and wasn't very impressed.

---

### Post by Knome_fan on 2005-08-03
With [http://www.niran.org/code/soc/](http://www.niran.org/code/soc/) combined with all the work that is being done to get more packages into universe and backports going official, I don't think the installing applications situation in ubuntu really needs something like klik.

It's still a great technology though, especially as it allows to "install" software on computers running from a LiveCD.

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Knome_fan]With [http://www.niran.org/code/soc/](http://www.niran.org/code/soc/) combined with all the work that is being done to get more packages into universe and backports going official, I don't think the installing applications situation in ubuntu really needs something like klik.
[/QUOTE]

That looks nice. I would love a script that would take all the universe programs and make gnome menu launchers for you as you install. A fix for the "debian menu."

---

### Post by Knome_fan on 2005-08-03
[QUOTE=poofyhairguy]That looks nice. I would love a script that would take all the universe programs and make gnome menu launchers for you as you install. A fix for the "debian menu."[/QUOTE]

I don't think a script should be needed. Isn't it "simply" a case of upstream and/or the package maintainers making sure that the app comes with a decent .desktop file? 
With all the work going into universe right now I'm pretty sure the situation will improve in the next release, especially if you consider that gnome-app-install seems to rely on valid .desktop files.

---

### Post by niran on 2005-08-03
All packages that provide GUI programs are supposed to add a menu entry. If a package you install doesn't add one, it's a bug. File it, and that program will end up being installable through gnome-app-install. All the data comes from the menu entries that are stored in the repositories, so getting it fixed by filing a bug will fix it everywhere the menu entries are used.

---

### Post by Omnios on 2005-08-03
Sounds very Linux sounds very interesting sounds like it will solve a lot of problems if it works. Only thing im not shure on is how it will handle dependencies thats where it sounds like others have failed.

 I find it a vairy interesting idea and its so Linux.

---

### Post by kanem on 2005-08-03
I once did a Mepis install just so I could try this Klik thing. Worked pretty well. As advertised, the application was just 'installed' in a folder in my home directory. By double clicking on a dmg image the app was started.

At least once though it asked me for permission to put stuff outside of my home.

I read all about it at their site, but still there are things I'm not clear about. Anyone who knows how this works want to explain here?

---

### Post by macgyver2 on 2005-08-03
Um, first off, where's the "I don't want it" option in the poll?

It sounds like citrix to me...I could be wrong though...

But if it's like citrix...ugh, it'll be sooo sloooooow.

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Knome_fan]I don't think a script should be needed. Isn't it "simply" a case of upstream and/or the package maintainers making sure that the app comes with a decent .desktop file? 
With all the work going into universe right now I'm pretty sure the situation will improve in the next release, especially if you consider that gnome-app-install seems to rely on valid .desktop files.[/QUOTE]

Its not that simple. Most of the Universe is ripped straight from Debian. The MOTU is not large enough to handle the Universe...most have pet packages anyway.

The real Debian repo relies on that damn, confusing, ugly (anything else?) Debian menu. So for them the way it is in fine. No use sending those bug reports to big Debian.

We don't have (and won't for a LONG time) have the manpower to fix the Universe EVERY TIME we update it from Sid. We need a script, or it will never happen.

The Universe is a hard to wield sword. There is a reason the real Ubuntu developers try to distance themselves from it.

---

### Post by Stormy Eyes on 2005-08-03
I wouldn't, but if it makes things easier for the newbies without getting in my way, I've got no objections. Apt-get is good enough for me.

---

### Post by UbuWu on 2005-08-03
[QUOTE=poofyhairguy]
We don't have (and won't for a LONG time) have the manpower to fix the Universe EVERY TIME we update it from Sid. We need a script, or it will never happen.
[/QUOTE]

I am not completely sure, but I thought there was a way in which changes to a package imported from debian are used again on importing of those packages for the next version of Ubuntu...

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=UbuWu]I am not completely sure, but I thought there was a way in which changes to a package imported from debian are used again on importing of those packages for the next version of Ubuntu...[/QUOTE]

Yep. for the main. As in what Synaptic touches by default- about 3000 packages. ALL of those install great.

Its the universe thats the problem. The other 11000 packages that lack the Ubuntu symbol in Synaptic. Those are taken straight from Debian for the most part. 

A script is the only sane way.

---

### Post by super on 2005-08-03
klik looks kool!  :razz: 

i don't think we need klik particularly **but** we need some work on the apt/synaptic tool. not in terms of functionality, it works great! the interface could be improved tho.

in my dream world synaptic would have things like screenshots, links to homepage of the software developers, descriptions and icons for all available software. i know its a lot of work, but if it was done by the developers of the programs it would be much easier. i tried lycoris once and they had something like this (albeit their repos were nowhere as large as ubuntu/debian's)

this would be far better than klik.

but, alas, i am no developer so i have no way to do this  :( 
so i'll just keep dreaming

EDIT:
found a pic of the Lycoris package management software
[this is the type of installer i am talking about](http://www.rcdrummond.net/articles/images/2iris.png) 
and i just read the thread about autopackage and saw some interesting stuff to be included in dpkg-2.0

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]
Its the universe thats the problem. The other 11000 packages that lack the Ubuntu symbol in Synaptic. Those are taken straight from Debian for the most part. [/QUOTE]

I don't think that's true anymore with launchpad and MOTUs. And as an important part of breezy, namely the new app installer will rely on .desktop files, I'm pretty sure there is great effort to make the situation a lot better than it is right now. Couple that with the existence of freedesktop.org specs about menu files that are now used by all major desktops and I think this will be largely solved in October with breezy.

Anyway, we'll see ourselves then, won't we?

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]I don't think that's true anymore with launchpad and MOTUs. And as an important part of breezy, namely the new app installer will rely on .desktop files, I'm pretty sure there is great effort to make the situation a lot better than it is right now. Couple that with the existence of freedesktop.org specs about menu files that are now used by all major desktops and I think this will be largely solved in October with breezy.

Anyway, we'll see ourselves then, won't we?[/QUOTE]

I imagine every package in Breezy's main will be working with the new tool.

I just worry about the Universe too much I guess. Its not that hard to use Smeg.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]I imagine every package in Breezy's main will be working with the new tool.

I just worry about the Universe too much I guess. Its not that hard to use Smeg.[/QUOTE]
No, you shouldn't worry about Universe too much, that was my point.

Also see what the developer of gnome-app-install had to say to it:
> All packages that provide GUI programs are supposed to add a menu entry. If a package you install doesn't add one, it's a bug. File it, and that program will end up being installable through gnome-app-install. All the data comes from the menu entries that are stored in the repositories, so getting it fixed by filing a bug will fix it everywhere the menu entries are used. 

And from the gnome-app-install page:
> You can now install almost any desktop application available in the Ubuntu repositories. If there are packages missing, they need .desktop files.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]No, you shouldn't worry about Universe too much, that was my point.

Also see what the developer of gnome-app-install had to say to it:
 

And from the gnome-app-install page:[/QUOTE]


Well...I don't think filing bug reports to Debian will work. They will go "WTF, my program is in the Debian menu."

But we could just add those desktop files or use SMEG. I'm looking forward to just seeing how the tools work.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]Well...I don't think filing bug reports to Debian will work. They will go "WTF, my program is in the Debian menu."

But we could just add those desktop files or use SMEG. I'm looking forward to just seeing how the tools work.[/QUOTE]
Huh? Nobody was talking about filing bugs to Debian. You are aware that there are MOTUs and Launchpad?

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]Huh? Nobody was talking about filing bugs to Debian. You are aware that there are MOTUs and Launchpad?[/QUOTE]

I know. I was more thinking out loud about how those patches might come off to the debian developers. I sometimes think....at what times is it good to seperate from Debian more? I think this is. I think Xorg, and the whole idea of a universe and main are awesome. 

I understand, the Universe will be fixed. That would be a BIG thing. I like it.

---

### Post by ubuntu_demon on 2005-08-04
I voted "I don't care" but it should be "other" (which isn't available).

I don't think we need klik for Ubuntu installations. We need a super nice gnome-app-install. 

But I think we do need something like klik for Ubuntu live cd/dvd. So we can "install" new stuff. Then the livecd becomes really good to work with. If I go to somebody without Ubuntu I can just pop it in and use my favorite applications.

Would be cool if there was some easy way to unofficially "install" mp3 while running from live cd/dvd.

---

### Post by Lovechild on 2005-08-04
The option for "No, I think it's a bad idea" is missing.

---

### Post by NoTiG on 2005-08-05
Well I have two questions:

Would it be possible for the developers websites to host this instead of having it all at just the klik website?

I see that it wraps the file with all the dependencies necessary, which makes it easier... but also wastes disk space and bandwith. Is it possible to have something like klik, except determine if your system has any of the dependencies, so you wont need to download the ones you already have and have them installed twice on your system?

---

### Post by probono on 2005-08-28
[QUOTE=NoTiG] Is it possible to have something like klik, except determine if your system has any of the dependencies, so you wont need to download the ones you already have and have them installed twice on your system?[/QUOTE]

klik does this already! 

Greetings,
probono

---

