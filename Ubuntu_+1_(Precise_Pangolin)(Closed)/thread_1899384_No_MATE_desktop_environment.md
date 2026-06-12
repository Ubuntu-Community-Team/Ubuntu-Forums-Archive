---
title: "No MATE desktop environment?"
date: 2011-12-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by josephellengar on 2011-12-23
Does 12.04 not have MATE DE (fork of Gnome 2.X) in the repos? I couldn't find it. I really hate gnome fallback mode and have been using MATE on my 11.10 installation.

---

### Post by bluexrider on 2011-12-23
its in the Mint repos [http://packages.linuxmint.com/list.php?release=Lisa#main](http://packages.linuxmint.com/list.php?release=Lisa#main)

How to install Mate

[http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)

---

### Post by josephellengar on 2011-12-23
> **bluexrider said:**
> its in the Mint repos [http://packages.linuxmint.com/list.php?release=Lisa#main](http://packages.linuxmint.com/list.php?release=Lisa#main)

oh, thanks.

---

### Post by zika on 2011-12-23
> **bluexrider said:**
> its in the Mint repos [http://packages.linuxmint.com/list.php?release=Lisa#main](http://packages.linuxmint.com/list.php?release=Lisa#main)

How to install Mate

[http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)
Whenever I see „sudo“ in front of „gedit“ or other GUI command, I simply do not trust to the author of that „HowTo“... ;)
Think about that...

---

### Post by Hydrathe on 2011-12-23
> **zika said:**
> Whenever I see „sudo“ in front of „gedit“ or other GUI command, I simply do not trust to the author of that „HowTo“... ;)
Think about that...

 Excuse me if it is obvious, but why is that a bad thing? How should it be done?  Thx.

---

### Post by effenberg0x0 on 2011-12-23
> **zika said:**
> Whenever I see „sudo“ in front of „gedit“ or other GUI command, I simply do not trust to the author of that „HowTo“... ;)
Think about that...

Fully agree... You're absolutely right (yet, I can't loose this habit - so trust nothing I write lol). I probably issued gksudo about 2 or 3 times in my entire life. I hate the fact that it is kind of slow in comparison to sudo. The way the screen blinks for the dialog to pop etc, it's just too Mickey Mouse club to me.

---

### Post by zika on 2011-12-23
> **Hydrathe said:**
> Excuse me if it is obvious, but why is that a bad thing? How should it be done?  Thx.
„sudo“ for CLI...
„gksu“ for GUI...
Otherwise that is problems waiting to happen... Well  discussed matter...

---

### Post by effenberg0x0 on 2011-12-23
> **Hydrathe said:**
> Excuse me if it is obvious, but why is that a bad thing? How should it be done?  Thx.

$gksudo <something GUI>
like
$gksudo gedit

---

### Post by Hydrathe on 2011-12-23
> **zika said:**
> „sudo“ for CLI...
„gksu“ for GUI...
Otherwise that is problems waiting to happen... Well  discussed matter...

> **effenberg0x0 said:**
> $gksudo <something GUI>
like
$gksudo gedit

Thx a lot, first time I hear about it, :D

---

### Post by ronacc on 2011-12-23
I also agree that "technically" one should use gksudo for GUI apps but I have been using sudo for many years for GUI apps and have never had any bad consequences so for my own use I will continue .

---

### Post by jfernyhough on 2011-12-23
This is getting a little OT, but from a quick search I just did ("sudo vs gksudo"):

If you run a GUI app using sudo it will use your own home for config data (e.g. Firefox profile). This means that files can be written as root that your normal user won't be able to change. This can cause problems, unsurprisingly.

If you run a GUI app with gksudo it will use root's home for config data, meaning there are no problems with file permissions for your normal user.

You can still use sudo if you want by adding the -h flag (i.e. $ sudo -h <command>). This apparently has the same effect as using gksudo (but without the graphical password prompt).

---

### Post by zika on 2011-12-23
> **jfernyhough said:**
> This is getting a little OT, but from a quick search I just did ("sudo vs gksudo"):

If you run a GUI app using sudo it will use your own home for config data (e.g. Firefox profile). This means that files can be written as root that your normal user won't be able to change. This can cause problems, unsurprisingly.

If you run a GUI app with gksudo it will use root's home for config data, meaning there are no problems with file permissions for your normal user.

You can still use sudo if you want by adding the -h flag (i.e. $ sudo -h <command>). This apparently has the same effect as using gksudo (but without the graphical password prompt).
&#8222;sudo -H&#8220;, I suppose...

For some time I have alias gsudo=/usr/bin/sudo -H so I do not have trouble with a bug in gedit which invokes (empty) Unitled_Document every time You use gksu with gedit... ;)

---

### Post by kansasnoob on 2011-12-23
> **josephellengar said:**
> Does 12.04 not have MATE DE (fork of Gnome 2.X) in the repos? I couldn't find it. I really hate gnome fallback mode and have been using MATE on my 11.10 installation.

I'm curious what you hate so much about the new "fallback" session? I've been doing it for a while now in both Oneiric and Precise and almost forget it's gnome 3 most of the time, but I opted to use metacity:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I'm not trying to be argumentative, just curious :D

---

### Post by josephellengar on 2011-12-23
> **kansasnoob said:**
> I'm curious what you hate so much about the new "fallback" session? I've been doing it for a while now in both Oneiric and Precise and almost forget it's gnome 3 most of the time, but I opted to use metacity:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I'm not trying to be argumentative, just curious :D

The panel width. It annoys me so much how wide the panel is. Also, I've had various problems with custom keyboard shortcuts, old GTK2 themes, and similar things. It seems like not much thought was put into fallback mode.

---

### Post by kurt18947 on 2011-12-23
> **josephellengar said:**
> The panel width. It annoys me so much how wide the panel is. Also, I've had various problems with custom keyboard shortcuts, old GTK2 themes, and similar things. It seems like not much thought was put into fallback mode.

I suspect there wasn't much thought given to fallback.  I've read it was added only after it was discovered that machines will less capable graphics might not be able to run either Unity or Unity 2D.  During 11.10's gestation is certainly seemed that fallback and Gnome-shell were second class citizens compared to Unity.  I find Gnome-shell quite usable these days though, especially with a few extensions.

---

### Post by grahammechanical on 2011-12-24
I do like the way we on this forum sometimes go gloriously off topic but what has this to do with the 12.04 development branch not having Mate DE in its repos?

Should we expect it to be there? After all, 12.04 is still being developed. Surely it is up to the developers of Mate to produce a DE that integrates with 12.04. I want most if not all of Canonical's development effort to go into Ubuntu 12.04 and beyond.

Regards.

---

### Post by ronacc on 2011-12-24
I don't think that the discussion has wandered very far OT since it was the answer to the OP's question that spawned the posts about sudo .

---

### Post by Myrddin Emrys on 2011-12-24
> **grahammechanical said:**
> Should we expect it to be there? After all, 12.04 is still being developed. Surely it is up to the developers of Mate to produce a DE that integrates with 12.04.

I'm sure they will, whether or not it becomes an official package - they already have a nice 11.10-compatible version in their own repository:

[http://wiki.mate-desktop.org/doku.php/download](http://wiki.mate-desktop.org/doku.php/download)

Incidentally, I would suggest installing this rather than the Mint version mentioned above - mint-meta-mate leaves you with a 'mintified' Ubuntu, affecting everything from your login wallpaper to your browser settings; might as well just install Mint. The developers' package gives you a much cleaner installation for Ubuntu.

---

### Post by kansasnoob on 2011-12-24
> **josephellengar said:**
> The panel width. It annoys me so much how wide the panel is. Also, I've had various problems with custom keyboard shortcuts, old GTK2 themes, and similar things. It seems like not much thought was put into fallback mode.

I don't personally understand the panel "width" problem because I've always preferred a panel that runs all the way fro left to right, but I do understand that choice is a huge issue :D

Regarding the new keyboard shortcuts you'll notice I mentioned that in my "how-to". I still have some trouble with that but I'm finding I can change most of it in System Settings > Keyboard.

It's not so much broken as just different :)

---

### Post by kansasnoob on 2011-12-24
> **grahammechanical said:**
> I do like the way we on this forum sometimes go gloriously off topic but what has this to do with the 12.04 development branch not having Mate DE in its repos?

Should we expect it to be there? After all, 12.04 is still being developed. Surely it is up to the developers of Mate to produce a DE that integrates with 12.04. I want most if not all of Canonical's development effort to go into Ubuntu 12.04 and beyond.

Regards.

I wouldn't want to see it killed :)

Mate may or may not be a vialble DE option, I don't know, but worst case scenario I'd suggest it being moved here:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

But I honestly suspect that more questions will be asked about Mate. Why hide them :confused:

---

### Post by josephellengar on 2011-12-24
> **kansasnoob said:**
> I don't personally understand the panel "width" problem because I've always preferred a panel that runs all the way fro left to right, but I do understand that choice is a huge issue :D

Regarding the new key6board shortcuts you'll notice I mentioned that in my "how-to". I still have some trouble with that but I'm finding I can change most of it in System Settings > Keyboard.

It's not so much broken as just different :)

By panel width I actually meant height haha. You can't make it as short as it was in the old Gnome 2.

---

### Post by kansasnoob on 2011-12-24
> **josephellengar said:**
> By panel width I actually meant height haha. You can't make it as short as it was in the old Gnome 2.

I haven't tried reducing it, but increasing it makes a huge mess :D

I'm just focused on getting Gnome 3 to work well enough to suit me, I don't mind others pursuing a different path.

I noticed yesterday that Mint is pursuing a third path:

[http://www.pcworld.com/businesscenter/article/246881/ready_for_a_new_linux_desktop_meet_mints_cinnamon.html](http://www.pcworld.com/businesscenter/article/246881/ready_for_a_new_linux_desktop_meet_mints_cinnamon.html)

So they may have their own gnome-shell extension, a version of Mate, and now a cinnamon flavor :confused:

Wow!

---

### Post by josephellengar on 2011-12-24
> **kansasnoob said:**
> I haven't tried reducing it, but increasing it makes a huge mess :D

I'm just focused on getting Gnome 3 to work well enough to suit me, I don't mind others pursuing a different path.

I noticed yesterday that Mint is pursuing a third path:

[http://www.pcworld.com/businesscenter/article/246881/ready_for_a_new_linux_desktop_meet_mints_cinnamon.html](http://www.pcworld.com/businesscenter/article/246881/ready_for_a_new_linux_desktop_meet_mints_cinnamon.html)

So they may have their own gnome-shell extension, a version of Mate, and now a cinnamon flavor :confused:

Wow!

And I thought Ubuntu was taking on too much with Unity! But I guess Mint doesn't have to do the backend stuff, so what else do they have to do? :D

---

### Post by ranch hand on 2011-12-25
All that is describing is the gnome friperies extensions.  Been using them for some time now.  Available in the Fedora repos for a while even.

They do add some nice things to GS.

---

### Post by Myrddin Emrys on 2011-12-25
> **ranch hand said:**
> All that is describing is the gnome friperies extensions.

The pcworld article isn't very clear about the difference between  adding new features with extensions (as used in Mint 12) and Cinnamon  (the new project). Cinnamon is an alternative shell for Gnome 3, forked from the original.  They claim that the extensions approach is rather limited, and Cinnamon  will allow them to do more:

[http://www.webupd8.org/2011/12/cinnamon-gnome-shell-fork-with-gnome2.html](http://www.webupd8.org/2011/12/cinnamon-gnome-shell-fork-with-gnome2.html)

I'm impressed by Mint's approach to Gnome. Including MATE should raise its profile and give the project a bit of momentum, while MGSE and Cinnamon mean that even those who aren't fans of 'new desktop paradigms' will benefit from Gnome 3. Either way, there's a future for traditional UIs based on Gnome.

---

### Post by teh603 on 2011-12-25
Cinnamon looks interesting, but I'm sticking to KDE for the near future.

By the way, its not "gksudo," its "kdesudo." =p

---

### Post by zika on 2011-12-25
> **teh603 said:**
> By the way, its not "gksudo," its "kdesudo." =pYou have „gedit“ in K?

---

### Post by ronacc on 2011-12-25
many Gnome apps work very well in KDE and the other way around too .

---

### Post by mc4man on 2011-12-25
As far as the gksudo gedit 'bug', which is over 6 months old & may never be fixed, I don't recollect ever seeing  any indication that sudo gedit will cause any issues.
That's what I use & it's the easiest way to not get the annoying untitled document 1

---

### Post by zika on 2011-12-25
> **ronacc said:**
> many Gnome apps work very well in KDE and the other way around too .
I know that. Been there lot of times... My question was a lame effort to make a joke, better to say, to explain why Gnome was supposed in giving the answer... ;)

---

### Post by zika on 2011-12-25
> **mc4man said:**
> As far as the gksudo gedit 'bug', which is over 6 months old & may never be fixed, I don't recollect ever seeing  any indication that sudo gedit will cause any issues.
That's what I use & it's the easiest way to not get the annoying untitled document 1It is not so hard to add „-H“ just to be sure it does not, really, make any problem... ;)

---

