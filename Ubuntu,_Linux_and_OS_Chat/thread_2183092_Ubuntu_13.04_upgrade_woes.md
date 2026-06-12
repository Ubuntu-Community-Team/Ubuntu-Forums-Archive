---
title: "Ubuntu 13.04 upgrade woes"
date: 2013-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by stevecoh1 on 2013-10-23
Forgive me for venting.

I just upgraded from 10.04 through all the steps to 13.04.  On another PC a botched upgrade led me to a new install of 13.04.  That at least works.  On my main machine what I currently have is a piece of crap, sorry if I offend anyone.  Everything works, if I can get to it.  But "Unity" is like an albatross around its neck.  Every time Unity gets involved, it slows down to a turtle's pace.  Once I manage to launch an app, it works fine, no performance bottlenecks at all.  But with Unity,key presses and mouse clicks take forever to process.  

Now I know from my other machine, that on a fresh install, this performs acceptably.  But WHO ASKED FOR THIS???  Why, when I am trying to find something on my PC must I be made to wait even ONE NANOSECOND for the system to load some list of what someone thinks are other cool apps I might like to try?  And other cool apps that I can buy?  Why would I want to be "united" with this universe?  I just want to launch an app that I know is on my PC.

This is an advance?  No, this is hell.

I have liked Ubuntu for many years but I can't put up with this.  Is there a way to switch to a non-Unity-based version of Ubuntu without a fresh install?  Or if a fresh install is needed, what should I install, staying within the Ubuntu family, which I was a happy member of until this?

---

### Post by deadflowr on 2013-10-23
You can try install the ubuntu-gnome-desktop.
And then switch to it in the login screen.

Ubuntu uses lightdm, so logging in to another desktop is different than gdm.
In Ubuntu login screen, where the name and passowrd are, is will be an icon in the top right corner of the box.(This icon will only be there if you add other desktop environments, it is not there with the default Ubuntu as it only has one desktop environment).
Click on the icon will give you a selection of desktops to choose.
If you choose to install the Ubuntu gnome desktop, you should have three choices, gnome(this is the new gnome known as shell) gnome flashback/fallback/classic(no effects) and gnome fallback/flashback/classic. I state fallback/flashback/classic because I can't remember which one 13.04 calls it. But classic, or its name variant is the close to the old look, which is probably what you want.

Of course there are ways to remove the Ubuntu/unity desktop, but I never do, and don't really care to.

---

### Post by help_me2 on 2013-10-23
Try a fresh install of xubuntu. It's the closest thing to the old gnome desktop there is, and it's fast.

---

### Post by deadflowr on 2013-10-23
> **help_me2 said:**
> Try a fresh install of xubuntu. It's the closest thing to the old gnome desktop there is, and it's fast.

No, the closest is [Mate]("http://mate-desktop.org/").

It is the old gnome desktop.

I'd still recommend the new gnome, though.

Edit: No complaints on Xubuntu, though.
Quite a usable desktop.

---

### Post by Bucky Ball on 2013-10-23
You could install xfce4, log out, choose 'xfce session' from the session manager, log in. Simple and fast. You may never look back.

If you do like it, you might want to consider installing a full Xubuntu, but then, you might be running Ubuntu because you like the default apps.

---

### Post by 3rdalbum on 2013-10-24
> **stevecoh1 said:**
>  But WHO ASKED FOR THIS???

Well, the computing world has long been talking about blurring the lines between online and offline. Unity actually makes some decent steps toward that goal. It doesn't go anywhere near far enough, but it's about the closest yet. Have you ever tried to show a new computer user how to download music? It's a depressing experience - unless you use the Ubuntu One Music Store from the Dash, at which point it actually becomes almost as easy as playing an existing music file.

Who asked for GUIs? No computer user did - but they made things easier. Who asked for automobiles? Nobody - but they were an essential advancement with many social benefits. I'm sure the first car drivers and horse riders grumbled about how they were noisy, required roads, and didn't give you any companionship. Henry Ford famously said that if he asked consumers what they wanted, they would have said that they wanted "a faster horse". Sometimes you have to break with tradition, and just because your desktop doesn't have a hierarchical menu at the top-left corner and a taskbar at the bottom (and your car doesn't have four legs and an affinity for oats) doesn't make it inferior.

> Why, when I am trying to find something on my PC must I be made to wait even ONE NANOSECOND for the system to load some list of what someone thinks are other cool apps I might like to try?  And other cool apps that I can buy?  Why would I want to be "united" with this universe?  I just want to launch an app that I know is on my PC.

Pin it to the Launcher then, or hit the Super key and start typing its name or description. I'm pretty sure "Apps available for download" is able to be turned off, too; but I find it useful for the times when I think I've got a program installed but actually don't. Just like the Ubuntu One Music Store, downloading and installing programs actually becomes nearly as easy and seamless as actually launching a program.

Incidentally, once the Applications lens has loaded once, you shouldn't see any slowdown in displaying the Apps for Download; it won't take much more than a nanosecond to display them once they've been displayed once.

> I have liked Ubuntu for many years but I can't put up with this.  Is there a way to switch to a non-Unity-based version of Ubuntu without a fresh install?  Or if a fresh install is needed, what should I install, staying within the Ubuntu family, which I was a happy member of until this?

Of course; as always, there are plenty of other desktops available in the Ubuntu Software Center (or through Synaptic or apt-get if you prefer those). XFCE, LXDE and KDE are traditional old desktops. Gnome Shell is one of the new wave. There's Cinnamon and Mate available in PPAs. Choose your poison, install it and then choose it from the login screen.

---

### Post by v1k1ng1001 on 2013-10-24
Install some alternative desktops like xfce, mate, gnome or kde.  You can session into each one at login, try them and see which one works with your hardware best.  Sounds like xfce/xubuntu desktop might be for you.

---

### Post by craig10x on 2013-10-25
You can turn off the online search in the privacy section of system settings if you prefer...and the most EFFICIENT and SIMPLE way to use unity is to pin your favorites and most used apps to the unity dock (for quick 1-click access) and just use search for less used apps..

---

### Post by monkeybrain20122 on 2013-10-25
> **3rdalbum said:**
> 
Incidentally, once the Applications lens has loaded once, you shouldn't see any slowdown in displaying the Apps for Download; it won't take much more than a nanosecond to display them once they've been displayed once.




I find that the initial loading is a lot faster in 13.10. 

@OP, it takes me a lot longer to search through the menu than to use the dash, if it has been used recently it is right there when you open the dash, if not type in a few alphabets and it comes up. I doubt that you can search the menu in a nano second. In fact I have gotten so used to it that I find the "classic" menus in kde, xfce etc almost unusable, gnome shell is the only thing that offers a similar experience in that regard. If the menu is so great you won't find people pinning random launcher icons all over the desktop and aesthetically it is a total disaster. My desktop is squeaky clean.

---

### Post by rrnbtter on 2013-10-25
Greetings,

> **monkeybrain20122 said:**
>  I doubt that you can search the menu in a nano second.  My desktop is squeaky clean.

+1

---

### Post by whatthefunk on 2013-10-25
> **3rdalbum said:**
> Well, the computing world has long been talking about blurring the lines between online and offline. Unity actually makes some decent steps toward that goal. It doesn't go anywhere near far enough, but it's about the closest yet. Have you ever tried to show a new computer user how to download music? It's a depressing experience - unless you use the Ubuntu One Music Store from the Dash, at which point it actually becomes almost as easy as playing an existing music file.

Who asked for GUIs? No computer user did - but they made things easier. Who asked for automobiles? Nobody - but they were an essential advancement with many social benefits. I'm sure the first car drivers and horse riders grumbled about how they were noisy, required roads, and didn't give you any companionship. Henry Ford famously said that if he asked consumers what they wanted, they would have said that they wanted "a faster horse". Sometimes you have to break with tradition, and just because your desktop doesn't have a hierarchical menu at the top-left corner and a taskbar at the bottom (and your car doesn't have four legs and an affinity for oats) doesn't make it inferior.

But if your computer is using resources to generate lists of programs and products you dont want and didnt search for while doing a simple offline search, then it has failed in a massive way.  Breaking tradition doesnt necessarily make something better.

---

### Post by craig10x on 2013-10-25
Yes...but ubuntu doesn't force you to use it...you can turn off all online searches in like, 5 seconds...yes, it is on by default, but they aren't forcing you to use it...
Actually, i would leave it on (even though i don't really use it) because it generates revenue for ubuntu development...but i don't like the way it clutters up my searches on the dash...
So i turn it off and make occasional donations to Canonical instead...

---

### Post by whatthefunk on 2013-10-25
> **craig10x said:**
> Yes...but ubuntu doesn't force you to use it...you can turn off all online searches in like, 5 seconds...yes, it is on by default, but they aren't forcing you to use it...
Actually, i would leave it on (even though i don't really use it) because it generates revenue for ubuntu development...but i don't like the way it clutters up my searches on the dash...
So i turn it off and make occasional donations to Canonical instead...

Yes, you can turn it off but as you said yourself, having an annoying, screen cluttering feature as a system default and as your main source of income is just not good.

---

### Post by monkeybrain20122 on 2013-10-25
> **whatthefunk said:**
> Yes, you can turn it off but as you said yourself, having an annoying, screen cluttering feature as a system default and as your main source of income is just not good.

This is the prevalent business model of many free internet services (google, facebook etc) as well as non free products like TV, newspaper and magazines (reader and viewer subscriptions are not their main source of income), the customers are not the users, viewers or readers, but the advertisers who pay these entities, the users, viewers and readers are the products.

Canonical is doing something similar, but not all the way in that they provide an easy and sure fire way to turn off the feature (in Facebook, for example, the privacy settings are so convoluted and full of loopholes that even if you think you turn something off, information may still appear in places where you don't want them to be) So this is not the deal breaker for me, I would be very happy if they make this opt-in instead of opt-out. I suppose it is also a side effect of "convergence" because it seems on mobile there is a different balance point between privacy and convenience.

---

### Post by eyTkT7Y on 2013-10-26
> **stevecoh1 said:**
> I have liked Ubuntu for many years but I can't put up with this.  Is there a way to switch to a non-Unity-based version of Ubuntu without a fresh install?  Or if a fresh install is needed, what should I install, staying within the Ubuntu family, which I was a happy member of until this?

Check out this [blog by psychocats]("http://www.psychocats.net/ubuntu/index.php")... they give command line options to switch from unity over to several other flavors without a reinstall. Use at your own risk. Although I've used these a few times with very nice results.

---

