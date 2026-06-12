---
title: "[IDEA] -- Desktop icons by default!"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by altonbr on 2007-10-23
It's simple:

$ gconf-editor
Apps >> Nautilus >> Desktop >> computer_icon_visible = 1
Apps >> Nautilus >> Desktop >> home_icon_visible = 1
Apps >> Nautilus >> Desktop >> network_icon_visible = 0
Apps >> Nautilus >> Desktop >> trash_icon_visible = 1
Apps >> Nautilus >> Desktop >> volumes_visible = 1

Why would these NOT show up by default? What beginner or even intermediate knows to go through the registry-like program 'gconf-editor' to enable desktop icons. This is extremely silly.

---

### Post by 23meg on 2007-10-23
[QUOTE=altonbr]Why would these NOT show up by default?[/QUOTE]

In the name of preventing redundancy and clutter by default. They're all available in other places (no pun intended), and a clean desktop is a Good Thing, perhaps especially for Windows converts tired of seeing loads of icons of "free" services and crapware on default desktops. volumes_visible is on by default, by the way.

---

### Post by altonbr on 2007-10-23
So the new Windows user knows to use the Places menu, after 5-10 years of Windows, right away?

Yes I know the volumes_visible is 1 by default, I was just showing what the settings should be.

But you see, if Ubuntu is about simplicity, how do you place the Home, Computer or Network folder on the desktop without gconf-editor?

---

### Post by r3m0t on 2007-10-23
Why do you want it on the desktop? Instead of pressing "Show Desktop -> Computer" and then bringing back your other windows, just go to "System -> Computer" every time. Problem solved.

---

### Post by smartboyathome on 2007-10-23
By the way, there is a tool called "desktop icon preferences" which is being developed that can (at this moment) let you choose what icons you want to show up on your desktop. It needs to be developed a little more before it goes into Ubuntu though.

[http://ubuntuforums.org/showthread.php?t=421266](http://ubuntuforums.org/showthread.php?t=421266)

---

### Post by 23meg on 2007-10-23
> **altonbr said:**
> So the new Windows user knows to use the Places menu, after 5-10 years of Windows, right away?

"Knowing how to use" a menu is a non-issue for anyone who is able to use a mouse or some other pointing device. To anyone who has used a menu driven interface, "Places" represents a clickable area. In an unfamiliar environment, the user will click around, and a menu clearly labeled "Places" contains all the items you list, minus the trash, which is right on the panel by default.

Does the ex-Windows user know how to use the "Places" menu? No. Can they and will they learn within a few seconds unless they're completely computer illiterate and are unable to use a pointing device? Yes.

> **altonbr said:**
> But you see, if Ubuntu is about simplicity, how do you place the Home, Computer or Network folder on the desktop without gconf-editor?

You can't. It's not discoverable for a non-technical user new to the environment what to do to place them on the desktop; they need to read documentation, do a search, or ask how to do it at a support facility. If you find this inappropriate, you may want to file a bug. I suggest not using statements like "This is extremely silly".

---

### Post by screaminj3sus on 2007-10-23
When I first used linux I had only used windows all ym life. I easily was able to find my way around and actually liked having no icons. Applications, Places, And System are all very well named and easy to figure out.

---

### Post by altonbr on 2007-10-23
You know what? You guys are correct.

I switch users from Windows to Ubuntu on the side of my main job and I've heard this complaint over and over again.

It makes sense to me to have it in a menu, but I guess everyone's been making me "make Ubuntu, Windows" without realizing it.

It's a different operating system. We do some things differently -- even if it's minor like this.

Feel free to close this thread, accept my apologizes for calling this "extremely silly" and lets continue our work on more important issues.

---

### Post by Perpetual on 2007-10-23
Funny thing, I tried Mandriva awhile back and was flustered because I could not figure out how to get rid of the icons on the desktop.  Having to google to figure it out was rather frustrating.

Yes, it was a very noob thing.  I suppose personally, I would have like to have found something under Preferences,  But that goes against the keeping there from being a cluttered mess of options in the menus.

---

### Post by aysiu on 2007-10-23
Linux Mint has an easy way of getting the desktop icons off or on the desktop.

The desktop icons should **not** be on by default (apart from volumes being visible), but they should also be easily enabled without people having to know about *gconf-editor*.

---

### Post by Perpetual on 2007-10-23
> **aysiu said:**
> Linux Mint has an easy way of getting the desktop icons off or on the desktop.

The desktop icons should **not** be on by default (apart from volumes being visible), but they should also be easily enabled without people having to know about *gconf-editor*.

Yes, LinuxMint does have a simple way of enabling/disabling icons on the desktop.

---

### Post by 23meg on 2007-10-23
[QUOTE=altonbr]It makes sense to me to have it in a menu, but I guess everyone's been making me "make Ubuntu, Windows" without realizing it.[/QUOTE]

Don't forget that you can "make Ubuntu Windows" for the folks for whom you're installing it, if needed. You can automate the process with a script with gconftool commands and have their icons on the desktop right after installation, or even make a custom Ubuntu CD with Reconstructor or something similar.

[QUOTE=altonbr]Feel free to close this thread, accept my apologizes for calling this "extremely silly" and lets continue our work on more important issues.[/QUOTE]

No need to close the thread, and no worries.

[QUOTE=aysiu]Linux Mint has an easy way of getting the desktop icons off or on the desktop.[/QUOTE]

How does it work there?

---

### Post by aysiu on 2007-10-23
> **23meg said:**
> 
How does it work there? It's an entry in the Gnome menu called MintDesktop, and it looks like this.

---

### Post by zachtib on 2007-10-23
just my $0.02


one of the reasons i was initially attracted to ubuntu was BECAUSE of the the lack of desktop icons.

i hate having extra crap on my desktop. i can deal with volumes, like external disks, but that's about it

---

### Post by exile on 2007-10-24
Please don't turn icons on the desktop on by default.. I'm begging.

---

### Post by sammm on 2007-10-24
I agree not having to many icons on the desktop.
But in the name of 'freedom of choice', putting desktop icons on your desktop (or anywhere else) should be as easy as:
 right clicking an item under 'Places' and have an option 'create a shortcut ...'.

---

### Post by jethro10 on 2007-10-24
I think I side on the idea of having icons easily available to "comfort" new windows users, who after all, is THE market and who we need to make a good first impression with.

I hear comment like "I hate a cluttered desktop" here , but remember you are users looking at the development forum for a new version of Ubuntu, WE can easily change them.

But a bad first impression on a new windows user is harder to solve.

J

---

### Post by andrewsomething on 2007-10-26
The menu that Mint uses looks like a great solution.

Personally, the very first thing I do to a fresh install of any Gnome desktop is to go into gConf and get rid of the mounted volumes icons....

---

### Post by Baby Boy on 2007-10-26
I doubt anyone grew up on Ubuntu instead of WIndows so we all have to learn how to use the panels and other shortcuts instead of icons. And I think it's really not that difficult to learn.

Why would anyone need icons when you can access everything you need in *so many ways*? In Windows I used to have 50-100 icons on Desktop but I got used to Ubuntu very fast and now I don't even remember why I needed all those icons.

My answer is NO,

---

### Post by Awalton on 2007-10-28
Didn't SABDFL already rule on this one in 2004? IIRC it goes something like...

<sabdfl>: no desktop icons at all, handle the problem elsewhere.

---

### Post by kellemes on 2007-10-28
> **jethro10 said:**
> I think I side on the idea of having icons easily available to "comfort" new windows users, who after all, is THE market and who we need to make a good first impression with.
J

So you want Ubuntu to be custom made for N00by Windows-users?
I really don't think this is the way to go..
If *buntu feels the need to get a bigger share of the desktop market they rather be *innovative* and *original* in offering "comfort" in the desktop-environment. I think they do this very well up to now..
Simply putting more icons on the desktop isn't original or innovative at all.

---

### Post by jethro10 on 2007-10-31
> **Awalton said:**
> Didn't SABDFL already rule on this one in 2004? IIRC it goes something like...

<sabdfl>: no desktop icons at all, handle the problem elsewhere.

The evolution of man, life and linux.

that's nearly 4 years ago, things may have changed.
I know I have since 2004.
J

---

### Post by jethro10 on 2007-10-31
> **kellemes said:**
> So you want Ubuntu to be custom made for N00by Windows-users?
I really don't think this is the way to go..
If *buntu feels the need to get a bigger share of the desktop market they rather be *innovative* and *original* in offering "comfort" in the desktop-environment. I think they do this very well up to now..
Simply putting more icons on the desktop isn't original or innovative at all.

I would be willing to have a few extra icons if it encouraged new users, yes.

However you need to calm down.
a) its not a big deal
b) Several new icons will not cause innovation to cease. The two do not need to be related :)
c) its not really "A way to go" its just a little thing.

J

---

### Post by CarpKing on 2007-10-31
I like the way it is by default now, but it would be nice to have something like Mint somewhere.

---

### Post by asphixmx on 2007-10-31
Well... I've been using Ubuntu for two months. I said goodbye to windows. I think there should be a easiest way to place the icons on Desktop. If you want them there or not, it's opt to you. BUT there should be an easiest way to choose. Ok, the places menu is great...but then I wonder why everytime a CD, USB memory,etc is inserted, an icon appears on desktop? If we want to be consistent, then the icon should appear ONLY on PLACES menu, don't you think? If it appears on desktop, then it is logical we want other icons on desktop, like the filesystem, home, etc.
By the way...I am very happy to be in the Linux community. Cheers.

---

### Post by altonbr on 2007-10-31
> **asphixmx said:**
> Well... I've been using Ubuntu for two months. I said goodbye to windows. I think there should be a easiest way to place the icons on Desktop. If you want them there or not, it's opt to you. BUT there should be an easiest way to choose. Ok, the places menu is great...but then I wonder why everytime a CD, USB memory,etc is inserted, an icon appears on desktop? If we want to be consistent, then the icon should appear ONLY on PLACES menu, don't you think? If it appears on desktop, then it is logical we want other icons on desktop, like the filesystem, home, etc.
By the way...I am very happy to be in the Linux community. Cheers.

I agree, if we're always about "no program duplication", then why are the volumes duplicated? I at least think the 'home' folder that contains all of the users files should be on the desktop, reminiscent of My Computer.

Since we'll never do this, what about coupling these options ONLY with the Windows Migration Assistant? When a user uses it to import their files and preferences, then it adds the 'home' folder, 'computer' folder and of course 'volumes' onto the desktop. Even better yet, only change the gconf it if they already have 'My Computer' ('Computer') and/or 'My Network Places' ('Network') on the desktop.

---

### Post by mysticmatrix on 2007-11-01
You can install GtweakUI from Add/Remove to obtain graphical way like Linux Mint does.

---

### Post by Bou on 2007-11-01
Setting the trash on the desktop is one of the first things I do, but I realise it's just a matter of personal taste. I don't have strong arguments for making it the default, but I would like an easy way to let the users do it themselves.

Maybe through some checkboxes in the preferences dialogue?

---

### Post by altonbr on 2007-11-01
> **Bou said:**
> Setting the trash on the desktop is one of the first things I do, but I realise it's just a matter of personal taste. I don't have strong arguments for making it the default, but I would like an easy way to let the users do it themselves.

Maybe through some checkboxes in the preferences dialogue?

But not through the migration assistant like I suggested?

---

### Post by leech on 2008-02-10
The thing that I find the most silly in this entire thread is that by DEFAULT on WINDOWS XP there is no MY COMPUTER and Network places!

Yes that's right, they aren't on the desktop by default.  If you install just a standard version of XP Professional, there aren't any icons on the desktop to begin with.  I always have to add the My Computer and My Network Places because I use them frequently.

The only icon that is on the default Windows XP install is the recycling bin.

Though I do think it rather odd that a common thing like wanting the Home folder or Computer icon on the desktop isn't in the Nautilus preferences (where it should be) and yet the option to enable spatial Nautilus is.  Something that more than likely most Windows converts would not want to use at all.

Kind of makes you think, eh?  But then if we wanted to be more like Windows we'd have to make it harder to change wallpapers, and would change nautilus so that when you right clicked on the desktop you'd have to select properties and appearance then get to the wall paper.  Let's not do that.

Leech

---

### Post by ubuntu-freak on 2008-02-13
One of the first things I do after installing Ubuntu is enable the various desktop icons in gconf. It's the default in Debian and I think it's attractive. Also, it gets a bit tiresome having to go to the places menu when I want to look in my home folder or filesystem. Plus, I had trouble getting fat32 partitions to show in the places menu but not on the desktop.
 
Nathan

---

### Post by decoherence on 2008-02-18
I think we should have certain icons on the desktop. Your 'typical' desktop metaphor (pre-MS-mangling) had a trash can (recycle bin) and a place for your files (your drive's partitions, in old-skool mac style, or your home directory in modern OS style) and some form of menu system to interact with these things. Removable media such as CDs or network volumes should show up on the desktop to clearly indicate that these things are in use.

Many people also expect newly installed programs to place an icon on the desktop. The presence of an obvious "Applications" menu should satisfy that expectation, but to be even more clear it should be called "Programs" not "Applications."

If people don't understand how an interface works, most of them are more likely to consider it broken than go on some journey of discovery unless they happen to be a kid.

I'm not suggesting we tailor Ubuntu for a Windows n00b. I'm suggesting we tailor it for those of us who have been using the desktop metaphor for more than five years. Forget how XP does it by default: Devices, home and trash on the desktop. By default. That's all.

I should just mention that I personally like having no icons on my desktop and tend to stick with that. My comments are based on real live reactions to real liveCDs from real live Windows and Mac users.

---

