---
title: "Why other distros don't use Unity?"
date: 2015-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by enricobe on 2015-10-10
Hello, 
I would like to understand why other distros don't use Unity. I don't mean they should use Unity as default DE, but no one seems to provide Unity in the repositories.
Take FEDORA, they provide "Desktop: Awesome, Cinnamon, Enlightenment, GNOME, KDE, LXDE, MATE, Openbox, Ratpoison, Xfce" but not Unity. I don't know any distribution that provides Unity as alternative DE.
I've read that Unity is only a Shell for GNOME, and not a real DE, but Cinnamon is a shell too.

I don't think there are license-related issues as unity is GPL licensed, but I would like to better understand why this happens. I think Unity is far better that default-GNOME UI...

Thank you ):P

---

### Post by monkeybrain20122 on 2015-10-10
Because it is very hard to port it to other distros. My understanding is that it uses a patched version of gnome which breaks compatibility with upstream(and also out of sync, Unity's gnome is older) so unless the distro also switches to Ubuntu's patched version of gnome it would have to maintain two versions of many gnome libraries.

There were attempts to port Unity to Fedora and Debian a few years ago  but were both dropped eventually because of those reasons.The Arch guys are persistent, the effort is still going on, you can get a feel of some problems involved here [https://bbs.archlinux.org/viewtopic.php?id=125423&p=2](https://bbs.archlinux.org/viewtopic.php?id=125423&p=2)

---

### Post by enricobe on 2015-10-10
> **monkeybrain20122 said:**
> Because it is very hard to port it to other distros. My understanding is that it uses a patched version of gnome which breaks compatibility with upstream so unless the distro also switches to Ubuntu's patched version of gnome it would have to maintain two versions of many gnome libraries.

There were attempts to port Unity to Fedora and Debian a few years ago  but were both dropped eventually because of those reasons.The Arch guys are persistent, the effort is still going on, you can get a feel of some problems involved here [https://bbs.archlinux.org/viewtopic.php?id=125423&p=2](https://bbs.archlinux.org/viewtopic.php?id=125423&p=2)

Thank you very much for your reply. It's sad to understand how difficult is the porting on other distros. I believe Canonical is a good company and I guess there are good reasons behind the patches they introduced (maybe due to Convergence), but if any other company had did it I would have thought they want in some way block the porting or make it very very difficult :-k

---

### Post by mikodo on 2015-10-10
^^^  Very Good point! Canonical/Ubuntu catches the ire of a lot of linux users. They often fail to mention what, Ubuntu and its' volunteers and staff contribute to FLOSS. I won't hi-jack your thread anymore than that.

---

### Post by monkeybrain20122 on 2015-10-10
> **enricobe said:**
> Thank you very much for your reply. It's sad to understand how difficult is the porting on other distros. I believe Canonical is a good company and I guess there are good reasons behind the patches they introduced (maybe due to Convergence), but if any other company had did it I would have thought they want in some way block the porting or make it very very difficult :-k

Well among other things Unity is a Compiz plugin whereas Gnome shell uses mutter, they are incompatible right there. Also canonical cannot build a stable Unity based on upstream gnome because it keeps changing. Each gnome shell new release breaks compatibility with many gnome-shell extensions even. Unity is a lot more stable.

For a project like Ubuntu I can completely understand why Canonical would want to have control over the pace and tempo of development of its flagship DE rather than having to count on the gnome devs, they remove features and make changes from one release to the next often apparently arbitrarily (to see the latest and greatest(?) gnome shell at work you have to  check out Fedora. Take nautilus for example, functions are removed and  the UI is inconsistent,--like why are menu and button scattering all  over the places?)  I think it would be good actually if Unity is to break with gnome completely (unity 8).

I wouldn't think there is any intention to make it difficult to port.

---

### Post by enricobe on 2015-10-10
> **mikodo said:**
> They often fail to mention what, Ubuntu and its' volunteers and staff contribute to FLOSS. I won't hi-jack your thread anymore than that.
My english is not so good and I can't fully understand what do you mean 8-[ I can't understand if you're pro-Canonical or not :)

I think that canonical has been one of the main driver to Linux diffusion for home-users, but this Unity's problems seem strange to me. Anyway, I'm not a developer and I can only trust in Canonical's reputation which is very good for me :)

> **monkeybrain20122 said:**
> Well among other things Unity is a  Compiz plugin whereas Gnome shell uses mutter, they are incompatible  right there. Also canonical cannot build a stable Unity based on  upstream gnome because it keeps changing. For a project like Ubuntu I  can completely understand why Canonical would want to have control over  the pace and tempo of development of its flagshio DE rather than leaving  it to the wimps of the gnome dev. I think it would be good actually if  Unity is to break with gnome completely (unity 8) seeing how changes in  gnome upstream are often regressive and arbitrary (want to see the  latest and greatest gnome shell you have to check out Fedora)  
I wouldn't think there is any intention to make it difficult to port.
I agree with you that Unity should "fork" completely from GNOME, I just don't know if it's so simple

---

### Post by monkeybrain20122 on 2015-10-10
> I agree with you that Unity should "fork" completely from GNOME, I just don't know if it's so simple 						

I guess it is not simple so they are sticking with gnome for the moment until Unity 8. :)

Yeah and btw in the early days of unity Canonical tried to submit patches upstream  but they were all rejected by gnome, so it is not that Canonical is  deliberately trying to break compatibility by patching downstream.

---

### Post by mikodo on 2015-10-10
> **enricobe said:**
> My english is not so good and I can't fully understand what do you mean 8-[ I can't understand if you're pro-Canonical or not 

Your English is fine! I am not so sure about mine. I support Canonical/Ubuntu and its' people. It was nice to hear "you" say what you are saying. I have heard too many people complaining about Ubuntu for not giving back to the "open-source eco-system". When, the "opposite" is true. What you have been saying is, "refreshing" to hear.

Thank you.

:)

---

### Post by enricobe on 2015-10-10
I think that all FOSS developers must be thanked for what they are doing  and Canonical too. Ubuntu is not perfect and doesn't respect Stallman's  rules about Free Software, but I think it has contributed a lot to  Linux diffusion.

> **monkeybrain20122 said:**
> I guess it is not simple so they are sticking with gnome for the moment until Unity 8. :)

Yeah and btw in the early days of unity Canonical tried to submit patches upstream  but they were all rejected by gnome, so it is not that Canonical is  deliberately trying to break compatibility by patching downstream.

It's sad to hear these things. I'm not a developer (as I've said before) but I really can't understand why the FOSS community doesn't work together to bring beautiful software with community improvements. I also hope that Canonical will help the Arch developers to introduce Unity in the next releases.

---

### Post by grahammechanical on 2015-10-10
> [COLOR=#000000]I really can't understand why the FOSS community doesn't work together to bring beautiful software with community improvements.[/COLOR]

They are human and humans are both saints and sinners and can switch between the two without warning. I appreciate the work of Ubuntu developers whether they are unpaid community developers or paid Canonical engineers. But I did not join a Ubuntu cult when I installed Ubuntu or signed the Ubuntu Code of Conduct. It is not wrong to disagree but it does matter how we go about disagreeing. Our method of expressing a different opinion can make or break a community regardless of the ethical foundation of the community. Here is an example. It is a negative example. Perhaps others could find positive examples.

[http://sarah.thesharps.us/2015/10/05/closing-a-door/](http://sarah.thesharps.us/2015/10/05/closing-a-door/)

Regards

---

### Post by buzzingrobot on 2015-10-10
> **enricobe said:**
> ...Awesome, Cinnamon, Enlightenment, GNOME, KDE, LXDE, MATE, Openbox, Ratpoison, Xfce...


Some of those are Desktop Environments that include, and depend on, a window manager, and the others are only windows managers.

A window manager is the tool that's responsible for drawing windows on the display, moving them around, etc.  I.e., managing them.

A Desktop Environment typically is more complex and provides other integrated capabilities:  File management, search, etc. Since a DE needs to manage windows as part of what it does, they all include a window manager. Sometimes a DE can be made to use a different window manager and sometimes it cannot. 

Unity's window manager is Compiz. I don't believe it can use another window manager, at least as currently implemented.

And, while there are hundreds of distributions, few of them have the resources to support and maintain a port of something as complex as Unity. For example, Fedora's primary focus is on Gnome. The other window managers and DE's are typically made available by an individual or group of individuals who do that voluntarily and comply with Fedora's rules and standards.

Plus, Canonical's success with building Ubuntu and Unity as brands means the first thought of anyone who wants to run Unity is jvery likely just to run Ubuntu.

---

### Post by forrestcupp on 2015-10-10
If you remember back to when Unity was first released, most of the Linux world hated it and vowed to never support it. I don't know if it's because they hate Ubuntu and Canonical for trying to commercialize Linux and make it mainstream, or if they just thought that Unity sucks. I suspect it was a mixture. I definitely don't have any ill will toward Ubuntu, but I never did care for Unity. And I really did try. I ended up preferring KDE out of all of them.

---

### Post by enricobe on 2015-10-10
It's ok if you choose another DE, I think that more *QUALITY* DE we can choose from and better is. For everybody. 
I don't like when few people create a fork just because they want to change a little part of the software and the result is very poor. But when the fork (or a new project) has a big community or a big support like Unity has, it's a good thing. More choice, more freedom. This is why I hope that Unity will be integraded in other distros.

---

### Post by monkeybrain20122 on 2015-10-10
I suppose porting may be easy for Mint which uses Ubuntu's libraries more or less as they are anyway (so no need for patching or maintaining two versions of gnome) But Mint has it own DE and a main source of Mint users are Unity haters :) so I guess there is no point doing that. I am not sure if even gnome shell or KDE are available on Mint.

---

### Post by enricobe on 2015-10-10
> **monkeybrain20122 said:**
> I suppose porting may be easy for Mint which uses Ubuntu's libraries more or less as they are anyway (so no need for patching or maintaining two versions of gnome) But Mint has it own DE and a main source of Mint users are Unity haters :) so I guess there is no point doing that. I am not sure if even gnome shell or KDE are available on Mint.

According with distrowatch, Mint supports: Desktop: Cinnamon, GNOME, KDE, MATE, Xfce :)
Anyway I agree when you say that the porting may be more difficult than other DE. 

> **monkeybrain20122 said:**
> But Mint has it  own DE and a main source of Mint users are Unity haters
This part I'm sure it's real, sadly. I will never use KDE because I really don't like it at all, but I'm happy that a KDE version of Ubuntu is available. :) I don't like KDE but KDE applications (like K3B) are often better than others counterparts. Choice is good

---

### Post by forrestcupp on 2015-10-11
> **monkeybrain20122 said:**
> I suppose porting may be easy for Mint which uses Ubuntu's libraries more or less as they are anyway (so no need for patching or maintaining two versions of gnome) But Mint has it own DE and a main source of Mint users are Unity haters :) so I guess there is no point doing that. I am not sure if even gnome shell or KDE are available on Mint.

Yeah, the whole reason they even created Cinnamon was because they were ticked off about Unity. And the reason they integrated Mate was because they were mad about Gnome 3. I don't think there's much chance they're going to bring Unity to Mint. But I guess they did end up putting Gnome Shell in.

---

### Post by mastablasta on 2015-10-12
> **enricobe said:**
> 
This part I'm sure it's real, sadly. I will never use KDE because I really don't like it at all, but I'm happy that a KDE version of Ubuntu is available. :) I don't like KDE but KDE applications (like K3B) are often better than others counterparts. Choice is good

actually in my opinion they should have gone with KDE and build on top of that rather than Gnome. but I guess they had more experience with gnome so they stayed there.

KDE has many looks. I am not sure what particular part you do not like, but they copy a lot from windows and windows copies a lot from them. the philosophies are the ones that matter here. Gnome hides features and menues as to not overwhelm the user, while KDE tries to put as many options into a GUI. which is why the programs seem good to you - they give you options. in gnome they have fewer options, but they are the ones most people use. for someone new to PC this approach is a lot easier.

for those of us that like to have it all in GUI KDE is better.

you are probably bothered by the launcher. I think that one had some changes lately. and even before you could get classic mode (looks kind of like winXP only fancier), you could get homerun launcher (takes up whole screen kind of like unity - [https://userbase.kde.org/Homerun](https://userbase.kde.org/Homerun)), then you have homerun kicker ([https://blogs.kde.org/2014/01/29/homerun-120](https://blogs.kde.org/2014/01/29/homerun-120)) which looks kind of like win7, then there is a netbook version for small screens ([https://en.wikipedia.org/wiki/KDE#/media/File:Screenshot_of_KDE_4.4_plasma-netbook.png](https://en.wikipedia.org/wiki/KDE#/media/File:Screenshot_of_KDE_4.4_plasma-netbook.png)), they had touch implemented a lot earlier. mostly I would just use alt+f2 to launch what i need. it offers a lot more customization than Unity, though as I understand from reviews Unity progressed nicely in this area as well.


but bottom line - use what works best for you. to me KDE and XFCE still look and act best. too bad that KDE has such large system usage. I hope they get that down a bit. but on the other hand it is packed with various features some of which most people do not use (activities :O ).

---

### Post by monkeybrain20122 on 2015-10-12
I don't like kde either. One reason I don't like it is exactly that it looks too much like Windows, it may be a selling point for some people but  not for me. :) Otherwise I find the plasma widgets rather buggy and dark theme has been broken for years (switch to a dark theme and typing in all text boxes in certain applications such as Firefox becomes invisible), the default blue grey theme is very ugly IMO.

 I don't like the kickoff/classic menu (menus are overrated, if they are so intuitive and convenient people wouldn't be piling launcher icons all over the desktop) Homerun and rosa menu kind of look like the dash but without the functionality (rosa is probably not available in Kubuntu without compiling, IIRC it was in Fedora or rpm can be downloaded)

Kde is not modular, it comes with a lot of crap that I would never use, but removing them may break the desktop.. In that sense it is not very customizable at all. So this may answer your question why unity is not built off kde, say whatever about gnome, it is a lot more modular. It is ridiculous how many kde dependencies it pulls in for just one application.

I don't really care for "customising" the look endlessly if the default is sensible enough, changing several settings in ccsm is good enough to go for me in Unity. I don't even change the wall paper, I like most of unity's default :)

If kde is your cup of tea you should try OpenSuse. It has the best implementation of kde IMO. At least it looks less like Windows 7 out of the box. :)

---

### Post by forrestcupp on 2015-10-12
> **mastablasta said:**
> actually in my opinion they should have gone with KDE and build on top of that rather than Gnome. but I guess they had more experience with gnome so they stayed there.

KDE has many looks. I am not sure what particular part you do not like, but they copy a lot from windows and windows copies a lot from them. the philosophies are the ones that matter here. Gnome hides features and menues as to not overwhelm the user, while KDE tries to put as many options into a GUI. which is why the programs seem good to you - they give you options. in gnome they have fewer options, but they are the ones most people use. for someone new to PC this approach is a lot easier.

for those of us that like to have it all in GUI KDE is better.

you are probably bothered by the launcher. I think that one had some changes lately. and even before you could get classic mode (looks kind of like winXP only fancier), you could get homerun launcher (takes up whole screen kind of like unity - [https://userbase.kde.org/Homerun](https://userbase.kde.org/Homerun)), then you have homerun kicker ([https://blogs.kde.org/2014/01/29/homerun-120](https://blogs.kde.org/2014/01/29/homerun-120)) which looks kind of like win7, then there is a netbook version for small screens ([https://en.wikipedia.org/wiki/KDE#/media/File:Screenshot_of_KDE_4.4_plasma-netbook.png](https://en.wikipedia.org/wiki/KDE#/media/File:Screenshot_of_KDE_4.4_plasma-netbook.png)), they had touch implemented a lot earlier. mostly I would just use alt+f2 to launch what i need. it offers a lot more customization than Unity, though as I understand from reviews Unity progressed nicely in this area as well.


but bottom line - use what works best for you. to me KDE and XFCE still look and act best. too bad that KDE has such large system usage. I hope they get that down a bit. but on the other hand it is packed with various features some of which most people do not use (activities :O ).
That's exactly why I love KDE. I prefer having a lot of features and options built in, rather than having a minimal system. But unlike other people, I don't usually have to worry about having to get something working on an older and smaller system. So I understand in those cases why you would prefer light over features.

---

### Post by vasa1 on 2015-10-12
> **monkeybrain20122 said:**
> ... and dark theme has been broken for years (switch to a dark theme and typing in all text boxes in certain applications such as Firefox becomes invisible), ...
That happens with other DEs as well and even if one doesn't use a DE. So nothing to do with specifically kde.

The fix or workaround isn't too difficult. One example is in the README here: [https://github.com/BunsenLabs/bunsen-themes/tree/master/Bunsen-Blackish](https://github.com/BunsenLabs/bunsen-themes/tree/master/Bunsen-Blackish).

I can understand a casual user running away in horror, but for lovers of the dark side, the fix is worth it ;)

---

### Post by buzzingrobot on 2015-10-12
> **forrestcupp said:**
> That's exactly why I love KDE. I prefer having a lot of features and options built in, rather than having a minimal system. But unlike other people, I don't usually have to worry about having to get something working on an older and smaller system. So I understand in those cases why you would prefer light over features.

If only they'd fix KWallet and go back to indexing Kmail mail messages in Desktop Search.:D

---

### Post by night_sky2 on 2015-10-12
> **monkeybrain20122 said:**
> I suppose porting may be easy for Mint which uses Ubuntu's libraries more or less as they are anyway (so no need for patching or maintaining two versions of gnome) But Mint has it own DE and a main source of Mint users are Unity haters :) so I guess there is no point doing that. **I am not sure if even gnome shell** **or KDE are available on Mint.**
The is a KDE edition of Linux mint. I am not sure how popular it is though.

I wonder if we will ever see an official edition of Ubuntu Cinnamon? I have fallen in love with this DE, for it's flexibility and modern look and it's getting better with every release.

---

### Post by mastablasta on 2015-10-13
> **monkeybrain20122 said:**
> 
If kde is your cup of tea you should try OpenSuse. It has the best implementation of kde IMO. At least it looks less like Windows 7 out of the box. :)

I tried it two times and in both times it failed me. some strange show stopping bugs. it is just less polished it seems. and only occasional version works well. Netrunner also has good implementation of KDE (Kubuntu based).

yes it does bring in dependencies (in gnome or in windows especially) but I am not sure it matters in KDE. like I said it's software has many features. features that most people will never use. so some of it is clutter. but there is also so many useful stuff. 

I am not sure why they are not more modular. but they aim to have all those services tightly connected, integrated and unified, so this could be one of the reasons. I never really went into this since we mostly just use defaults. well, we did change the wallpaper and the theme is a bit less blue but still one of the oxygens...

OpenSuse has default dark theme I believe.

---

