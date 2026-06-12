---
title: "Noticed the sluggishness?"
date: 2005-12-16
forum: The Cafe
---

### Post by gamehack on 2005-12-16
Hi all,

I don't want to be bitchy but hasn't anyone noticed the sluggishness in most cases when running GNOME? The thing is that I frequently need Windows because of Adobe PS2 and I don't want to mess with emulation/virtual machines/etc so I've a separate win partition. When I switch from Windows->Breezy everything feels utterly sluggish. Try that: open firefox, open a few tabs with big pages and while they are loading try clicking on some other tab. There's like a 0.5 seconds timeout and everything starts to move in jerky way. Is it just me or have others experienced this? I know Firefox is not a proper GNOME application but still a GTK+ one(XUL one to be precise, but uses GTK+ for implementing XUL). And it's the same with all the desktop. I'm really happy with everything else, look, simplicity, everything but the performance is ridiculous. And yes, X.org uses 2D acceleration. Are the GTK+ developers blind or is there a big architectural/technical mistake in 2.x series? I'm sorry if I sound too bitchy. I just wanted to express my experience and see if someone else had the same experience. If you're going to flame me, please don't even reply. Thank you.

Regards

---

### Post by Knomefan on 2005-12-16
Actually there are a lot of people that also feel that Gnome is quite sluggish. Personally, I think it could be snappier, but I never really found it sluggish.

But be that as it may, better performance is one of the things the Gnome and GTK devs are really working hard on at the moment and we should see some improvements in the next Gnome release and probably even further improvements in the releases to come.

---

### Post by gamehack on 2005-12-16
[QUOTE=Knomefan]Actually there are a lot of people that also feel that Gnome is quite sluggish. Personally, I think it could be snappier, but I never really found it sluggish.

But be that as it may, better performance is one of the things the Gnome and GTK devs are really working hard on at the moment and we should see some improvements in the next Gnome release and probably even further improvements in the releases to come.[/QUOTE]
I'm watchin' Planet GNOME all the time and really enjoy when I see someone doing profiling work and optimize things. But I think the issues are much much deeper in the infrastructure. There's something fundamentally BROKEN in GNOME's architecture/underlying libraries and I would really want to see what it is, but ATM lack the tools and people to do it. Personally, when I finish a few personal projects which I cannot put off at the moment, I will devote all my time profiling the whole GNOME desktop.

Regards

---

### Post by spdl on 2005-12-16
[QUOTE=gamehack]Hi all,

I don't want to be bitchy but hasn't anyone noticed the sluggishness in most cases when running GNOME? The thing is that I frequently need Windows because of Adobe PS2 and I don't want to mess with emulation/virtual machines/etc so I've a separate win partition. When I switch from Windows->Breezy everything feels utterly sluggish. Try that: open firefox, open a few tabs with big pages and while they are loading try clicking on some other tab. There's like a 0.5 seconds timeout and everything starts to move in jerky way. Is it just me or have others experienced this? I know Firefox is not a proper GNOME application but still a GTK+ one(XUL one to be precise, but uses GTK+ for implementing XUL). And it's the same with all the desktop. I'm really happy with everything else, look, simplicity, everything but the performance is ridiculous. And yes, X.org uses 2D acceleration. Are the GTK+ developers blind or is there a big architectural/technical mistake in 2.x series? I'm sorry if I sound too bitchy. I just wanted to express my experience and see if someone else had the same experience. If you're going to flame me, please don't even reply. Thank you.

Regards[/QUOTE]

Hi gamehack,

I have not seen the sluggishness that you refer to.  And I also dual-boot between XP and ubuntu.

I also use Adobe PhotoShop and other Windows-based applications such as DreamWeaverMX and FLASHMX to name a few.  May I recommend you try [CodeWeaver's]("http://www.codeweavers.com/") CrossOver Office?  The three aforementioned programs were easy to install on it and work fast and beautifully in ubuntu Linux.  They offer a demo version for 30-days and if you like it, it's costs like $30.

There is also [Wine]("http://www.winehq.com/") that is freeware and may be usefull to you if you don't want payware.

I'm still a newb on ubuntu and Linux but I hope this information was usefull to you in some way.

---

### Post by Knomefan on 2005-12-16
[QUOTE=gamehack] But I think the issues are much much deeper in the infrastructure. There's something fundamentally BROKEN in GNOME's architecture/underlying libraries and I would really want to see what it is, but ATM lack the tools and people to do it. 
[/quote]
Hm, what makes you think so?

[QUOTE=gamehack]
Personally, when I finish a few personal projects which I cannot put off at the moment, I will devote all my time profiling the whole GNOME desktop.

Regards[/QUOTE]
Cool!

---

### Post by ssam on 2005-12-16
you could try another window manager, like xfce or openbox. there are ways of just swaping openbox (or anyother WM) into gnome [http://www.ubuntuforums.org/showthread.php?t=75471](http://www.ubuntuforums.org/showthread.php?t=75471)

gnome is getting lots of performance love at the moment, so it should get a bit faster for dapper.

---

### Post by benplaut on 2005-12-16
gnome seems nice and fast to me, but i agree about Firefox... that thing leaks memory like nuts, and is quite slow

---

### Post by gamehack on 2005-12-16
[QUOTE=ssam]you could try another window manager, like xfce or openbox. there are ways of just swaping openbox (or anyother WM) into gnome [http://www.ubuntuforums.org/showthread.php?t=75471](http://www.ubuntuforums.org/showthread.php?t=75471)

gnome is getting lots of performance love at the moment, so it should get a bit faster for dapper.[/QUOTE]
To be honest, that's not the solution to the problem(from my POV). I really want GNOME the way it is and I'm satisfied with it and really upset by its performance. So I plan to do something about it.

Regards

---

### Post by GeneralZod on 2005-12-16
Firefox is, in my opinion, *markedly* slower under Linux than Windows, in both start-up time and general "feel" - it frequently feels like molasses.  Apparently, 1.5 is quite a lot better.

---

### Post by mjewell on 2005-12-16
I agree that Firefox is slower under ubuntu than linux but don't know why.

I'm running ubuntu 5.10, Gnome 2.12.1, kernel 2.6.12-9-386 and *frequently* when I try to load a new page in Firefox, the "operation timed out" message is displayed.  

Evolution is fine for sending and receiving email.  From a terminal, I can ping the same sites I'm trying to load in Firefox.  

I've seen remarks that it may be a domain name resolution problem, but I don't know how to test for that.  

Has anyone noticed and/or fixed this problem?

---

### Post by poofyhairguy on 2005-12-16
[QUOTE=gamehack]Hi all,

I don't want to be bitchy but hasn't anyone noticed the sluggishness in most cases when running GNOME? The thing is that I frequently need Windows because of Adobe PS2 and I don't want to mess with emulation/virtual machines/etc so I've a separate win partition. When I switch from Windows->Breezy everything feels utterly sluggish. Try that: open firefox, open a few tabs with big pages and while they are loading try clicking on some other tab. There's like a 0.5 seconds timeout and everything starts to move in jerky way. Is it just me or have others experienced this? I know Firefox is not a proper GNOME application but still a GTK+ one(XUL one to be precise, but uses GTK+ for implementing XUL). And it's the same with all the desktop. I'm really happy with everything else, look, simplicity, everything but the performance is ridiculous. And yes, X.org uses 2D acceleration. Are the GTK+ developers blind or is there a big architectural/technical mistake in 2.x series? I'm sorry if I sound too bitchy. I just wanted to express my experience and see if someone else had the same experience. If you're going to flame me, please don't even reply. Thank you.

Regards[/QUOTE]

Its Firefox thats soo slow, not Gnome in that case. Firefox 1.0 in Ubuntu is far slower then Windows. The solution is to use 1.5 or Epiphany- both will make it feel like you have a new computer.

---

### Post by GeneralZod on 2005-12-16
[QUOTE=poofyhairguy]Its Firefox thats soo slow, not Gnome in that case. Firefox 1.0 in Ubuntu is far slower then Windows. The solution is to use 1.5 or Epiphany- both will make it feel like you have a new computer.[/QUOTE]

Is 1.5 really that much better? I've heard this from a few sources now and have been sitting on the fence about whether to upgrade...

---

### Post by gamehack on 2005-12-16
Cool, I'll try 1.5 on Linux and see how it runs ;)

Regards

---

### Post by BWF89 on 2005-12-16
Last December when I was duel booting with Fedora Core 2 after only a few days of running my system became sluggish. I don't know what it's like today because I haven't used Linux since then. (waiting to get my own computer to install it on)

Same thing happens when I try to run TuxRacer on Windows or Linux.

---

### Post by phen on 2005-12-16
that sluggishness made me switch from gnome to kde. the unwanted interruptions between clicking on "Applications" and the appearance of the menu annoyed me. i'd love to go back - but thats my new pc, i dont want it to run slow!

---

### Post by curuxz on 2005-12-16
cant say i noticed it being slow in gnome, just faster in kde if that makes sense :D

---

### Post by kairu0 on 2005-12-16
Gnome has always felt more sluggish than Windows on my new PC. I'm not talking about Firefox (although it isn't as loved as Windows' Firefox) but about Gnome. Gnome has been known to have memory-hogging problems for a long time and I can't wait for it to be improved in the next release.

I can't help but blame part of it on X11, too. X11 was not designed to show 24, 32 bit resolutions on large monitors with 3d elements.

Then again, I won't go back to Windows because I'll take the slugishness problems before the stability problems.

---

### Post by xequence on 2005-12-16
You might want to try FreeBSD. I was told it was really fast, and it can run gnome and every other linux program.

---

### Post by kairu0 on 2005-12-16
[QUOTE=xequence]You might want to try FreeBSD. I was told it was really fast, and it can run gnome and every other linux program.[/QUOTE]

Under FreeBSD, I'd use the same Gnome and the same X11, so I don't think it would make much difference.

---

### Post by xequence on 2005-12-16
[QUOTE=kairu0]Under FreeBSD, I'd use the same Gnome and the same X11, so I don't think it would make much difference.[/QUOTE]

Heh, I was just told FreeBSD was alot faster then linux.

---

### Post by dcast on 2005-12-16
Gnome is rather slow I tried kde and it was no better

---

### Post by mstlyevil on 2005-12-16
Firefox on Suse 10 KDE is faster than my Windows XP partitons version of Firefox. I am using 1.5 on both of them. When I was dual booting Ubuntu, I must admit that FF was slower under Gnome than in Windows. This could be a dependency issue in Ubuntu of some kind.

---

### Post by kairu0 on 2005-12-16
Enlightenment screams on my machine...then again, using Enlightenment makes me scream.

---

