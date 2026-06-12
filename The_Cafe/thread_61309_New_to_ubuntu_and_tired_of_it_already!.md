---
title: "New to ubuntu and tired of it already!"
date: 2005-08-31
forum: The Cafe
---

### Post by nilly on 2005-08-31
I would say im new to linux!, ubuntu is the first dist i run on my main computer, have fiddled with gentoo on xbox earlier and some with redhat and mandrake.. And i would have to say that i love ubuntu!! much!, and then we have the repositories that are never up to date!! getting sick of it, and newbie as i am compiling my own software usually ends up in a bunch of broken packs and a wellfilled harddrive!..

What would you guys recommend to switch to, if i would switch.. i really love the ease of use ubuntu presents, and sudo is awesome.. and it must go with my laptop.. (Ubuntu does :)) Damn ubuntu rock!

Help me!

---

### Post by darkfox on 2005-08-31
[QUOTE=nilly]I would say im new to linux!, ubuntu is the first dist i run on my main computer, have fiddled with gentoo on xbox earlier and some with redhat and mandrake.. And i would have to say that i love ubuntu!! much!, and then we have the repositories that are never up to date!! getting sick of it, and newbie as i am compiling my own software usually ends up in a bunch of broken packs and a wellfilled harddrive!..

What would you guys recommend to switch to, if i would switch.. i really love the ease of use ubuntu presents, and sudo is awesome.. and it must go with my laptop.. (Ubuntu does :)) Damn ubuntu rock!

Help me![/QUOTE]
 If I understand correctly, you like everything about Ubuntu apart from the not-up-to-date repositories.
If this is correct, then I have a suggestion and a comment:

Suggestion: Try adding 'backports' repositories to you sources list. Backports repositories contain some applications not containined in the other official repositories, and also newer versions of some of the applications that are. This will solve your problem and allow you to keep ubuntu. More information at the Backports forum ([http://www.ubuntuforums.org/forumdisplay.php?f=47]("http://www.ubuntuforums.org/forumdisplay.php?f=47")) and the Wiki ([https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backports%29]("https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backports%29"))

Comment: The official repositories are pretty up to date in my opinion - at least as up to date as you could realisically expect while being stable enough to use well (they undergo pretty robust testing first). Backports will give you newer packages but at a cost of stability - they won't be very well tested. Your choice (which is what its all about, after all).

---

### Post by Kvark on 2005-08-31
The easiest way to add the backports repository to your sources list is by follwoing the steps at:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)


If you really want the latest then you should be using the development version of Breezy. It's prolly not 100% stable yet but you can't get more bleeding-edge up-to-date then when using something that isn't even officially released yet.

---

### Post by tom-ubuntu on 2005-08-31
Is it just me or is the slowness of the repos mention A LOT in the last couple of days/weeks?

---

### Post by nilly on 2005-08-31
Thanks for your answers, i have backports added and even tough i find other distributions (read gentoo) faster with new versions of apps, as i run gentoo on my xbox. One example thats been bothering me for a while is amarok, why isnt 1.3 in hoary repos or backports.. its darn stable and an official realease.. i use it everyday, its on gentoos portage..

Note that im not pissing on ubuntu..

---

### Post by GeneralZod on 2005-08-31
[QUOTE=joeuser]Is it just me or is the slowness of the repos mention A LOT in the last couple of days/weeks?[/QUOTE]

I think that's because it's a fairly recent thing: prior to sometime around the beginning of August, there were a steady stream of updates coming from backports.  At that point, though, things slowed to a trickle - I don't know the exact date when the stream cut off, but the last post in the Accepred Requests portion of backports ([http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)) was from the 3rd of August.  

Having said that, a couple of days ago I had some updates for the first time in ages, si I guess jdong was just taking a well-deserved summer break :)

---

### Post by Brunellus on 2005-08-31
If you wanted bleeding edge, stay with Gentoo...can't get any more bleeding-edge than that.

Ubuntu is the medium between Debian (which releases once every geological epoch or so) and Gentoo (the state of permanent revolution).  It makes for a nice desktop.

---

### Post by KingBahamut on 2005-08-31
Honestly , you want bleeding edge, compile from source. 

Thats what I do. 

=)

---

### Post by nilly on 2005-08-31
And its sad to leave this very nice community that is all about ubuntu (the spirit of ubuntu), anyone tryed Gentoo on a modern laptop?.. Amd64, Ati9700, Wifi etc etc?.. ubuntu just kicked of right from the installation..

---

### Post by N'Jal on 2005-08-31
>  	Honestly , you want bleeding edge, compile from source.  

Yeah use LFS nothing can be more bleeding edge, or not than that. Might try it one day many many years in the future.

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=nilly]
What would you guys recommend to switch to, if i would switch.. [/QUOTE]

Debian Sid.

---

### Post by darkfox on 2005-08-31
[QUOTE=poofyhairguy]Debian Sid.[/QUOTE]
 Tee-hee.   Very droll.

Nilly - I too run Gentoo but only as a secondary desktop, something mad to tinker with. It is insanely stupid in its approach, which is jolly good fun indeed. Interestingly, having optimised everything on it and compiled the lot from source, Ubuntu still has a quicker start-up (when running the same number of services) on my machine. I also noticed comments backing this up on the Gentoo forums, which as you know are also really friendly.

Stick with Ubuntu and if you need some packages more recent than Backports and don't mind the untestedness, get the hang of compiling from source - it'll be a good learning experience.  Even better, learn some stuff about packaging and contact the Backports team offering to contribute!

---

### Post by Lord Illidan on 2005-08-31
Yeah, compiling from source is a good idea, if you want to learn more about the way Linux works.. I've done it for most apps, and do not leave the community... it is the best thing about Ubuntu..

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=darkfox]Tee-hee.   Very droll.
[/QUOTE]

Thanks, I looked that up and you added to my vocabulary:

> droll   Audio pronunciation of "droll" ( P )  Pronunciation Key  (drl)
adj. droll·er, droll·est

    Amusingly odd or whimsically comical.

---

### Post by xequence on 2005-08-31
Ive heard good things about mepis though I havnt got it to work well...

I dont have many problems with the repositories. If something isnt in it I just have to live without it as I have no idea how to compile and it seems that there is different code for every thing to install and none of it works :P

Heh, about them being up to date... I have no problems...

---

### Post by occy8 on 2005-08-31
> Originally Posted by nilly
What would you guys recommend to switch to, if i would switch.. 

I'll switch to breezy in a while :) 

In the meantime the safety updates are enough for me since my system works fine and I lost my broadband because I moved house

---

