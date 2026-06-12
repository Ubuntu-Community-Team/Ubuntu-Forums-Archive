---
title: "Succesfull KDE on Ubuntu"
date: 2005-01-23
forum: The Cafe
---

### Post by amiroff on 2005-01-23
Hello Ubuntuers!

I've just upgraded to hoary KDE and have to say that KDE on Ubuntu rocks not less than any other distro I've tried before.

Some tips: 

- Don't follow the tip on ubuntuguide about optimizing Nvidia performance as it somehow manages to freeze kde and X.

- Enable freetype autohinter module in /etc/fonts/local.conf

- Get Nuvola theme from KDE look

- Get pantherX cursors (they rock) from the same place

- Get lipsitck style and knifty window decorations from kalyxo.org (they work in ubuntu)

Here is my latest wonderful KDE desktop: [KDE on Ubuntu](http://www.amiroff.com/kde_ubuntu.png) (1280*1024 png file, 450 K)

My deepest thanks to everyone involved in development of this wonderful distro !

-- Metin Amiroff

---

### Post by BWF89 on 2005-01-23
If you hadn't told me that was Ubuntu I wouldn't ever have guessed...

---

### Post by amiroff on 2005-01-23
[QUOTE=BWF89]If you hadn't told me that was Ubuntu I wouldn't ever have guessed...[/QUOTE]
 Oh, I guess that is all about choice and customizability, what free software gives us...

Cheers

---

### Post by jakeslife on 2005-01-23
That is very tasty looking. If not follow the guide on the nVidia stuff, what should one do?

---

### Post by CowPie on 2005-01-23
[QUOTE=amiroff]Hello Ubuntuers!

I've just upgraded to hoary KDE and have to say that KDE on Ubuntu rocks not less than any other distro I've tried before.

Some tips: 

- Don't follow the tip on ubuntuguide about optimizing Nvidia performance as it somehow manages to freeze kde and X.

- Enable freetype autohinter module in /etc/fonts/local.conf

- Get Nuvola theme from KDE look

- Get pantherX cursors (they rock) from the same place

- Get lipsitck style and knifty window decorations from kalyxo.org (they work in ubuntu)

Here is my latest wonderful KDE desktop: [KDE on Ubuntu](http://www.amiroff.com/kde_ubuntu.png) (1280*1024 png file, 450 K)

My deepest thanks to everyone involved in development of this wonderful distro !

-- Metin Amiroff[/QUOTE]
 You just inspired me to install KDE 3.3!  It's much faster for Gnome but it takes 2ce the memory!!  But, I think I'll keep it for the speed :)  The integration of KDE and Gnome is amazing to me, freedesktop.org has done great work, my menus are now twice the size!

---

### Post by amiroff on 2005-01-23
[QUOTE=jakeslife]That is very tasty looking. If not follow the guide on the nVidia stuff, what should one do?[/QUOTE]
 Well, go on and follow it, just don't add these lines:

--
        Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
--

It took me nearly one week to figure out why KDE was freezing on me and not on others on irc, and I came to the idea it was due to these settings while I was in bed :) Desktop hasn't freezed by now after removing those lines, so I suspect I've found some kinda bug. Gonna enable these lines again and try to do some testing again later :)

Cheers,

---

### Post by amiroff on 2005-01-23
[QUOTE=CowPie]You just inspired me to install KDE 3.3!  It's much faster for Gnome but it takes 2ce the memory!!  But, I think I'll keep it for the speed :)  The integration of KDE and Gnome is amazing to me, freedesktop.org has done great work, my menus are now twice the size![/QUOTE]

Yes, I was a big Gnome lover (still am) but KDE's speed and responsive interface got me using it more and more. I do translation work of both KDE and Gnome to my native language, so I have both installed anyway. The main grip about KDE for me is that apps don't look identical to each other, which takes extra time to learn.

Cheers,

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=amiroff]Oh, I guess that is all about choice and customizability, what free software gives us...

Cheers[/QUOTE]I wish all KDE users are like amiroff :) Anyway, beautiful screenshot.

---

### Post by TravisNewman on 2005-01-23
That's a slick setup man!

But I have those lines enabled in my xorg.conf and it's fine. You may have found a bug ;) I hope it doesn't mess up on me.

See, I used to hate KDE, but I now realize it's because I was installing KDE instead of kde-base. I was getting ALL THAT BLOAT and it was killing me, but while I still like Gnome better, I'm starting to like KDE as well. AND I've been using XFCE a lot lately and occasionally Fluxbox (I'm on a tour), so I really don't know what I want to use! Especially when I see rockin' screenshots like that for one of the WMs that I'm NOT using. *sigh* ah well, that's one downside to having so many choices I guess ;)

---

### Post by amiroff on 2005-01-24
> **panickedthumb]That's a slick setup man!

But I have those lines enabled in my xorg.conf and it's fine. You may have found a bug  said:**
> 

Still XFree here, I haven't done dist-upgrade yet, just apt-getted the latest KDE and Gnome :) For some reason servers feel slow for me this week (no more than 10 K/s) so it will take some time.

[QUOTE]
See, I used to hate KDE, but I now realize it's because I was installing KDE instead of kde-base. I was getting ALL THAT BLOAT and it was killing me, but while I still like Gnome better, I'm starting to like KDE as well. 

Yes, you should know what to install, just install base, then individual apps. Gnome wins in terms of usability and look hands down, but again, technology beneath KDE and it's speed is worth the mention.   =D>

---

### Post by Quest-Master on 2005-01-24
> **panickedthumb]That's a slick setup man!

But I have those lines enabled in my xorg.conf and it's fine. You may have found a bug  said:**
> 
 > See, I used to hate KDE, but I now realize it's because I was installing KDE instead of kde-base. I was getting ALL THAT BLOAT and it was killing me
[quote]Yes, you should know what to install, just install base, then individual apps.

Why don't one of you guys write a HOWTO on it? I'm sure a lot of people would appreciate it and it would increase the awareness of KDE in Ubuntu.

---

### Post by ctt1wbw on 2005-01-24
Yeah, that would be great.  I would love to install KDE.  That pic from above is sweet, dude!

---

### Post by amiroff on 2005-01-25
[QUOTE=ctt1wbw]Yeah, that would be great.  I would love to install KDE.  That pic from above is sweet, dude![/QUOTE]

Well, I am not that much of KDE expert, nor am I Ubuntu one, but for sure, I'll try to write down something as soon as possible!

Glad you loved the sceenie! :)

---

### Post by ctt1wbw on 2005-02-01
I have Warty 4.10 right now.  I see that in Synaptic package manager, there is kde.  Is this Hoary or Warty kde?  Am I okay to go install this package?

---

### Post by Jad on 2005-02-01
[QUOTE=amiroff]Still XFree here, I haven't done dist-upgrade yet, just apt-getted the latest KDE and Gnome :) For some reason servers feel slow for me this week (no more than 10 K/s) so it will take some time.



Yes, you should know what to install, just install base, then individual apps. Gnome wins in terms of usability and look hands down, but again, technology beneath KDE and it's speed is worth the mention.   =D>[/QUOTE]
 congrats 
I hate KDE

---

### Post by Dylanby on 2005-02-01
> I have Warty 4.10 right now. I see that in Synaptic package manager, there is kde. Is this Hoary or Warty kde? Am I okay to go install this package? 

Unless you've edited your sources.list (under Synaptic: Settings => Repositories) those are Warty packages. I've never installed all of kde on Ubuntu but I believe you want to install the kde & kdebase packages.

If like me you only want specific kde packages be sure to install qt3-qtconfig or kcontrol so you can make those fonts look good (if you like AA fonts).

---

### Post by MaZiNgA on 2005-02-01
Nice work man, even though I hate KDE...!
I've installed it to see it though and still runs smooth with added Nvidia lines...Strange..

---

### Post by Randabis on 2005-02-01
[QUOTE=Dylanby]Unless you've edited your sources.list (under Synaptic: Settings => Repositories) those are Warty packages. I've never installed all of kde on Ubuntu but I believe you want to install the kde & kdebase packages.

If like me you only want specific kde packages be sure to install qt3-qtconfig or kcontrol so you can make those fonts look good (if you like AA fonts).[/QUOTE]

kde-core is what you want actually. It installs the core kde system without all the flab.

---

### Post by carney1979 on 2005-02-02
An alternative that I like is installing KDE 3.3.91 Beta1 via Konstruct.

It takes a bit more effort, but I've been running it trouble free for about 3 weeks now.

If you install it as a normal (non-root or sudo) user, it can be installed in your home folder. If you want to run two separate versions of KDE, you can. Just make sure you FULLY read the instructions that come with Konstruct.

It can be found here:  [http://developer.kde.org/build/konstruct/](http://developer.kde.org/build/konstruct/)

Download the unstable version for the latest. Some further instructions are here: [http://quality.kde.org/develop/cvsguide/buildstep.php](http://quality.kde.org/develop/cvsguide/buildstep.php)

Best of luck!

David

---

