---
title: "XGL/Compiz time to stability"
date: 2006-05-04
forum: The Cafe
---

### Post by the_tiger on 2006-05-04
How long do you think it will be before xgl and compiz are easy to install and remain stable?

---

### Post by briancurtin on 2006-05-04
right now.

---

### Post by Mathias-K on 2006-05-04
[QUOTE=briancurtin]right now.[/QUOTE]

Please don't misunderstand me, but i disagree.

For me, "really easy to install" is when anyone can do it. 

A week ago i followed a guide to get the newest nVIDIA driver, and then a guide to get Xgl and Compiz working. I sat down, read each guide through several times, and then followed them to the letter, double checking each time that everything was in order.

All i got was a trashed X server.

To me, that is neither "really easy to install" nor "stable".

EDIT:
I think we both know that the_tiger is asking when Xgl / Compiz will about as easy to install as a program from Synaptic or any apt-get program. Why don't you just give him a nice and friendly answer? :)

---

### Post by 23meg on 2006-05-04
Easy to install, as in apt-get, right now. Stable and working with the majority of modern hardware, about two years.

---

### Post by the_tiger on 2006-05-04
I'm not talking about a total noob solution but one that is suitable for use as part of a stable main desktop. I don't want X breaking when I update.

---

### Post by Stormy Eyes on 2006-05-04
[QUOTE=Mathias-K]For me, "really easy to install" is when anyone can do it. 
[/QUOTE]

My wife did it, and so did my cat. :)

---

### Post by flankker on 2006-05-04
it only took me 15 minutes following the guide at the compiz forums, so i think its easy to install. 

stability is another thing. im my case, running games crashes xgl, the screensaver is laggy and some updates can break stuff. but all in all, at the pace this thing is evolving imo in 6 months this will be very stable.

---

### Post by Lovechild on 2006-05-04
I think it will be at least another year before AIGLX/XGL technology will be ready for deployment and that's even an optimistic estimate.

---

### Post by mstlyevil on 2006-05-04
It is stable enough for Novel to deploy in their Suse Linux Enterprise Desktop (SLED). As far as games go, if you want to play games there is a way to turn compiz on and off at will so you can play games. The games conflict with the openGL nature of the desktop so you just turn it off for games. 

I have been using it since the beginning and it is very rare a update or anything crashes my system due to compiz. It is stable and ready to use now and has improved tremendously in the few months it has been out.

Here is a link for a how-to to install it to be easy to turn on and off for games.

[http://doc.gwos.org/index.php?title=Swich_between_XGl_and_Xorg_through_GDM_]("http://doc.gwos.org/index.php?title=Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29&rcid=8079")

---

### Post by Lord Illidan on 2006-05-04
[quote=Lovechild]I think it will be at least another year before AIGLX/XGL technology will be ready for deployment and that's even an optimistic estimate.[/quote]

I betcha the folks at Novell would finish it sooner on their own. Now that it is in the public domain, it will be forked numerous times, eventually piss everyone off, and still manage to look worse than Vista and Apple.

---

### Post by Mathias-K on 2006-05-04
[QUOTE=23meg]Easy to install, as in apt-get, right now. Stable and working with the majority of modern hardware, about two years.[/QUOTE]

I must have missed that. If that is true, i know a few people that will be very glad :)

Do you have a link to it? Obviously it is another guide than the one i used..

---

### Post by nickle on 2006-05-04
[quote=Stormy Eyes]My wife did it, and so did my cat. :)[/quote]

I had a cat like that once until curiosity got the better of it...

---

### Post by briancurtin on 2006-05-04
i installed XGL/Compiz on arch through pacman and it worked immediately with one small exception that was my fault in xorg.conf. i had a default depth of 16 instead of 24. i changed the number and it has worked flawlessly for the last week, ie 100% of the time.

---

### Post by Mathias-K on 2006-05-04
[QUOTE=briancurtin]i installed XGL/Compiz on arch through pacman and it worked immediately with one small exception that was my fault in xorg.conf. i had a default depth of 16 instead of 24. i changed the number and it has worked flawlessly for the last week, ie 100% of the time.[/QUOTE]

Does that installation require people to read up on UNIX codes and guides, or is it just hassle free click and install?

---

### Post by Stormy Eyes on 2006-05-04
[QUOTE=Mathias-K]Does that installation require people to read up on UNIX codes and guides, or is it just hassle free click and install?[/QUOTE]

There's no such thing as hassle-free click and install with experimental software, especially when it comes to X11. :)

---

### Post by mstlyevil on 2006-05-04
[QUOTE=Mathias-K]Does that installation require people to read up on UNIX codes and guides, or is it just hassle free click and install?[/QUOTE]

You have to edit your GDM-Custom file and you have to create a executable script to use compiz. You also have to edit your xorg.conf file for your video card. Other than that you just add Quinstorms and raggeameaus repos to your sources.list and install it with apt-get.

---

### Post by Mathias-K on 2006-05-05
[QUOTE=Stormy Eyes]There's no such thing as hassle-free click and install with experimental software, especially when it comes to X11. :)[/QUOTE]

I am aware of that, but that's also the real question in this thread:

*"How long do you think it will be before xgl and compiz are easy to install and remain stable?"*

I think Xgl has to be click and install before I will call it "easy to install".

---

### Post by briancurtin on 2006-05-05
[QUOTE=Mathias-K]EDIT:
I think we both know that the_tiger is asking when Xgl / Compiz will about as easy to install as a program from Synaptic or any apt-get program. Why don't you just give him a nice and friendly answer? :)[/QUOTE]
i gave him an unfriendly answer? although i use a different distro, i obtained XGL and compiz just the way that you are talking about. "pacman -S xgl-cvs compiz-cvs"

[QUOTE=Mathias-K]Does that installation require people to read up on UNIX codes and guides, or is it just hassle free click and install?[/QUOTE]
i dont really know what "UNIX codes and guides" are. i added a repo in pacman, installed it via pacman, and then went through like 3 completely laid out steps in a wiki and it worked perfectly*. i didnt even have to think for myself at all. note: as i said earlier, im talking about Arch, not ubuntu, so my situation is a bit different.

* i did have to change one more thing, but it was my fault that i had my default color depth in xorg.conf too low. ive copied my xorg.conf from distro to distro and left the wrong number in there from the start but got away with it.

---

### Post by briancurtin on 2006-05-05
[QUOTE=Mathias-K]I think Xgl has to be click and install before I will call it "easy to install".[/QUOTE]
well then there isnt much easy to install software in linux. if users are afraid to edit config files, linux is not for them. this is another case where i say most *users* arent even ready for "the desktop"

---

### Post by poofyhairguy on 2006-05-05
[QUOTE=Lord Illidan]I betcha the folks at Novell would finish it sooner on their own. Now that it is in the public domain, it will be forked numerous times, eventually piss everyone off, and still manage to look worse than Vista and Apple.[/QUOTE]

Thats a great attitude.

---

### Post by poofyhairguy on 2006-05-05
[QUOTE=Mathias-K]
I think Xgl has to be click and install before I will call it "easy to install".[/QUOTE]

You can install XGL and Compiz now with some clicking in synaptic.

Now getting it to work is another thing.

---

### Post by poofyhairguy on 2006-05-05
[QUOTE=the_tiger]How long do you think it will be before xgl and compiz are easy to install and remain stable?[/QUOTE]

Depends on what you mean.

If you mean "easy enough to install that anyone that can follow directions can do it" then that day is now if you have some semi-modern Nvidia hardware. All it takes is following some guides.

If you mean "easy as in it has a GUI to install it," then I personally guess the answer is this summer as someone might have made a gui way to do it by then.

If you mean "stable as in part of the default distro" then the answer is "probably never." Those who love Gnome and develop it would hang themselves before they would allow for Compiz to be the default window manager in a major Gnome distro like Ubuntu. And on top of that, XGL is kinda a hack (ok....not kinda....it is...) and so any responsible distro that uses it by default will find itself in trouble. As far as I have found out, even Novell won't do this- they will have a GUI way to install XGL with tons of warnings saying its experimental stuff.

Basically it all comes down to what video card you have. Have a new Nvidia card? Then you can play with it this afternoon with my guide. Have an older Nvidia card (pre-Geforce 4 series), an ATI card, or a Intel Card? Then it might work for you, but it will be harder and there is little anyone can do to make it easier (outside of those at ATI, Intel).

---

### Post by helpme on 2006-05-05
[QUOTE=briancurtin]well then there isnt much easy to install software in linux.
[/QUOTE]
/me looks at all the apps in my menu that I installed by using a nice graphical app and that simply work.
/me looks at your post again.
/me looks at all the apps in my menu that I installed by using a nice graphical app and that simply work.
/me looks at your post again.
/me shakes head in disbelieve.

[QUOTE=briancurtin]
if users are afraid to edit config files, linux is not for them.
[/QUOTE]
/me looks at my desktop again, that worked ootb.
/me looks at yast.
/me looks at your post again.
/me shakes head again.

---

### Post by Mathias-K on 2006-05-06
[QUOTE=briancurtin]i gave him an unfriendly answer? although i use a different distro, i obtained XGL and compiz just the way that you are talking about. "pacman -S xgl-cvs compiz-cvs"[/QUOTE]

Your answer wasn't really unfriendly, but it hardly had the depth and quality that poofyhair's post had, even though i think you two both know quite a lot about the matter :)

[QUOTE=briancurtin]i dont really know what "UNIX codes and guides" are. i added a repo in pacman, installed it via pacman, and then went through like 3 completely laid out steps in a wiki and it worked perfectly*. i didnt even have to think for myself at all. note: as i said earlier, im talking about Arch, not ubuntu, so my situation is a bit different.

* i did have to change one more thing, but it was my fault that i had my default color depth in xorg.conf too low. ive copied my xorg.conf from distro to distro and left the wrong number in there from the start but got away with it.[/QUOTE]

[QUOTE=briancurtin]well then there isnt much easy to install software in linux. if users are afraid to edit config files, linux is not for them. this is another case where i say most users arent even ready for "the desktop"[/QUOTE]

What I call Linux/UNIX codes are all those wierd commands and wiki guides that you have to follow in order to get things working. I must say that I do not understand why things are like that with Xgl/Compiz.

After all, if you have an nVIDIA card, there is a strict order of codes that you have to paste into the terminal to get the driver working. Okay, but why isn't there just a "nvidia-8478-driver-nonfree" package in Synaptic that gives you a little warning and asks for confirmation and then *just does the install*? The same way with Xgl / Compiz.

Arnieboy and Automatix has helped me tremendously. Why aren't his work integrated into Synaptic / apt-get so that when you search for java, there is a package in multiverse named something like "java-install-nonfree"?

To me, it's a win/win situation. I love installing things from Synaptic / apt-get in Linux/Ubuntu. To me it's a huge advantage over Windows.

---

### Post by Stormy Eyes on 2006-05-06
[QUOTE=Mathias-K]I must say that I do not understand why things are like that with Xgl/Compiz.[/QUOTE]

Right now, Xgl/Compiz are still somewhat unstable and experimental technologies. The focus right now is on making it work well and consistently, not on making it easy for mere humans to install. :) Eventually this stuff will be installed by default, but I'm guessing that that's at least six months away.

---

### Post by briancurtin on 2006-05-06
[QUOTE=helpme]/me looks at all the apps in my menu that I installed by using a nice graphical app and that simply work.
/me looks at your post again.
/me looks at all the apps in my menu that I installed by using a nice graphical app and that simply work.
/me looks at your post again.
/me shakes head in disbelieve.
[/QUOTE]
/me asks you to gain some reading skills so you can read, as well as tie multiple sentences together at the same time
[QUOTE=helpme]/me looks at my desktop again, that worked ootb.
/me looks at yast.
/me looks at your post again.
/me shakes head again.[/QUOTE]
/me asks you what any of that has to do with anything

---

### Post by Gijith on 2006-05-06
I realize this is the wrong place, but searching the Dapper forum is a nightmare... Can anyone recommend the best/simplest/most-up-to-date guide to getting XGL/Compiz for nVidia and KDE??? :confused: 
I think I'm ready to finally try it.

---

### Post by Stormy Eyes on 2006-05-06
[QUOTE=Gijith]I realize this is the wrong place, but searching the Dapper forum is a nightmare... Can anyone recommend the best/simplest/most-up-to-date guide to getting XGL/Compiz for nVidia and KDE??? :confused: 
I think I'm ready to finally try it.[/QUOTE]

*meow* [Everything you need is in this thread.](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+nvidia+howto) *meow*

---

