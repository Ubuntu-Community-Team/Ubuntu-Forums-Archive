---
title: "Why DID gdmsetup suddenly become so minimal?"
date: 2009-11-01
forum: The Cafe
---

### Post by hoppipolla on 2009-11-01
Is it a new version of GDM? Was it overhauled in some way? Or are Ubuntu just trying to "refine" the OS and keep things kinda standardized? Will it go back in time?

Sorry for all the questions, it's just so weird to see a Gnome tool that has remained the same (or nearly the same) for as long as I remember suddenly get stripped of all it's options. Why is this?

Hoppi

---

### Post by samjh on 2009-11-01
It's being rewritten to work with PolicyKit, I believe.

---

### Post by FuturePilot on 2009-11-01
Yes, GDM was completely rewritten a while ago, Ubuntu stuck with the older version for a few releases and has now finally moved to the new version. No one has written a tool to configure it comparable to the old one yet.

---

### Post by yabbadabbadont on 2009-11-01
Because the ultimate aim of the gnome devs is to prevent any confusion among the unwashed multitudes by removing all configuration options...

(after all, they don't really need them anyway)

---

### Post by Exodist on 2009-11-01
> **yabbadabbadont said:**
> Because the ultimate aim of the gnome devs is to prevent any confusion among the unwashed multitudes by removing all configuration options...

(after all, they don't really need them anyway)


Just like the screen-saver applet.  It took a act of congress and talking one on one with the lead dev at the time of the gnome project to get the head dev of the screen-saver applet to at least add a freaking preview button.  They agreed also to add a simple configuration part to it, but as you can see that fell through and hasnt happend yet.

---

### Post by 23meg on 2009-11-01
This thread is a textbook example of how anti-GNOME FUD spreads.

---

### Post by Exodist on 2009-11-01
> **23meg said:**
> This thread is a textbook example of how anti-GNOME FUD spreads.
No FUD here.

---

### Post by 23meg on 2009-11-01
A lot of FUD here. There's the case of two factual posts being ignored in favor of a cynical one taken as if it were factual, and there's a horribly distorted recollection of an episode in the development of GnomeScreensaver cited in support of the usual grand conspiracy of feature removal.

---

### Post by Exodist on 2009-11-01
> **23meg said:**
> A lot of FUD here. There's the case of two factual posts being ignored in favor of a cynical one taken as if it were factual, and there's a horribly distorted recollection of an episode in the development of GnomeScreensaver cited in support of the usual grand conspiracy of feature removal.

Dude, i did in fact have to have a heated debate with the Dev of the screensaver applet after gnome switched from the traditional xscreensaver to the new gnome one. He in fact did not want to add a preview or anything. It lead up to be having to have a few email conversations to with the at that time lead gnome dev to influence it getting corrected.

If you say this did not happen, then you are in fact calling me a liar and I do get offended from that.

---

### Post by 23meg on 2009-11-01
> **Exodist]Dude, i did in fact have to have a heated debate with the Dev of the screensaver applet after gnome switched from the traditional xscreensaver to the new gnome one.[/QUOTE]

It wasn't a switch. XScreenSaver was never part of GNOME. GNOME had no screen blanking application before GnomeScreensaver. 

[QUOTE=Exodist]He in fact did not want to add a preview or anything. It lead up to be having to have a few email conversations to with the at that time lead gnome dev to influence it getting corrected.[/QUOTE]

Who was this "lead gnome dev"? Maybe you mean someone from the release team or something, because there's no such position as "lead gnome dev".

The classic discussion people tend to cite in distorted ways when they want to "Blame GNOME!&#8482 said:**
> this bug[/URL], which includes no reference to not wanting to implement a preview. 

[QUOTE=Exodist]If you say this did not happen, then you are in fact calling me a liar and I do get offended from that.

I do challenge you to prove it by citation.

---

### Post by Exodist on 2009-11-01
Challenging something with someone that happened well over two years ago is **FUD**. 
[I][B]
I have been in debates like this before that go no where. So I am dropping this and you can do what ever pleases you.[/B][/I]

---

### Post by 23meg on 2009-11-01
I have every right to challenge claims badmouthing a project I've volunteered lots of time and energy to. 

And of course, you have every right not to meet my challenge.

---

### Post by Frak on 2009-11-02
> **23meg said:**
> I have every right to challenge claims badmouthing a project I've volunteered lots of time and energy to.

This.

---

### Post by Exodist on 2009-11-02
> **Frak said:**
> This.
Wasnt trying to bad mouth anything. :-)
I am very passionate about gnome and everything about it as well.

---

### Post by cariboo on 2009-11-02
If you don't keep this thread on topic, it will be closed, and please keep it civil.

---

### Post by praveesh on 2009-11-02
Isn't this a modification made by the Ubuntu devs to make xsplash working ?

---

### Post by fluteflute on 2009-11-02
> **FuturePilot said:**
> Yes, GDM was completely rewritten a while ago, Ubuntu stuck with the older version for a few releases and has now finally moved to the new version. No one has written a tool to configure it comparable to the old one yet.
This is the truth as I understand it. Nothing to do with PolicyKit or xsplash.

---

### Post by purgatori on 2009-11-02
This is one reason why I said "hello" to XDM in 9.10.

---

### Post by hoppipolla on 2009-11-02
> **purgatori said:**
> This is one reason why I said "hello" to XDM in 9.10.

aww nooo but... KDM!

Additionally Entrance used to be amazing, I don't know about now...

Personally though I'm quite content with GDM, I'm happy so long as it logs me in lol

> **FuturePilot said:**
> Yes, GDM was completely rewritten a while ago, Ubuntu stuck with the older version for a few releases and has now finally moved to the new version. No one has written a tool to configure it comparable to the old one yet.

This sounds the most likely. I wonder why it was rewritten... always nice to see progress though so I'm sure things improved :)

---

### Post by 23meg on 2009-11-02
> **hoppipolla said:**
> I wonder why it was rewritten... 

[http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign)

---

### Post by hoppipolla on 2009-11-02
> **23meg said:**
> [http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign)

sounds good to me :)

---

### Post by tuwe on 2009-11-02
you can still theme gdm in some way.

```
sudo -u gdm dbus-launch gnome-appearance-properties
```

there you can edit colors and stuff of the login window and set a nice background.

---

### Post by hoppipolla on 2009-11-02
> **tuwe said:**
> you can still theme gdm in some way.

```
sudo -u gdm dbus-launch gnome-appearance-properties
```

there you can edit colors and stuff of the login window and set a nice background.

ooooo *tries* :)

EDIT -- Awesome! How does this work? Like, how am I setting preferences just for GDM and not the whole of Gnome?

---

### Post by falconindy on 2009-11-02
> **hoppipolla said:**
> ooooo *tries* :)

EDIT -- Awesome! How does this work? Like, how am I setting preferences just for GDM and not the whole of Gnome?

Notice the part where you're using the '-u gdm' to launch the gnome appearance properties. sudo isn't just for getting root privileges -- it's for assuming the rights of another user. gdm is the user in charge of the system when you see the login screen. Alter his themes and you'll alter the gdm theme. You're pretty much limited to changing the background. Feel free to fire up:
```
gksudo -u gdm dbus-launch gconf-editor
```
and see what else you can alter. There really isn't much.

---

### Post by hoppipolla on 2009-11-02
> **falconindy said:**
> Notice the part where you're using the '-u gdm' to launch the gnome appearance properties. sudo isn't just for getting root privileges -- it's for assuming the rights of another user. gdm is the user in charge of the system when you see the login screen. Alter his themes and you'll alter the gdm theme. You're pretty much limited to changing the background. Feel free to fire up:
```
gksudo -u gdm dbus-launch gconf-editor
```
and see what else you can alter. There really isn't much.

Cool thanks :)

Yeah I just changed the background and that's all. To be honest I have no gripes with the login screen really so I'm happy just leaving it. Sometime I might swap it for KDM if I get bored but even that is unlikely :)

---

### Post by hoppipolla on 2009-11-02
oo where did the default background go? I changed it and now it seems like the normal one has disappeared... does anyone know where it is stored? o.O

---

### Post by tuwe on 2009-11-03
> **hoppipolla said:**
> oo where did the default background go? I changed it and now it seems like the normal one has disappeared... does anyone know where it is stored? o.O

Which normal background? Backgrounds are stored in /usr/share/backgrounds, the xsplash background which is used by gdm by default can be found in /usr/share/images/xsplash

---

### Post by hoppipolla on 2009-11-03
> **tuwe said:**
> Which normal background? Backgrounds are stored in /usr/share/backgrounds, the xsplash background which is used by gdm by default can be found in /usr/share/images/xsplash

Thats the one - thanks! It looked nice when I changed it, but it didnt blend so well with the Ubuntu loading screens either side of it! I know I could probably change those too but tbh I quite like them! :)

Thanks anyway though, and Im sure lots of people DO want to change this stuff!

---

### Post by Megrimn on 2009-11-03
> **tuwe said:**
> you can still theme gdm in some way.

```
sudo -u gdm dbus-launch gnome-appearance-properties
```

there you can edit colors and stuff of the login window and set a nice background.

HALLELUJA, brother!

---

### Post by kenrmcl on 2009-12-11
> **tuwe said:**
> you can still theme gdm in some way.

```
sudo -u gdm dbus-launch gnome-appearance-properties
```

there you can edit colors and stuff of the login window and set a nice background.

Actually, I can't edit anything. I get

No protocol specified
No protocol specified
Cannot open display: 
No protocol specified

and hence have no opportunity to change anything. Looks like XDM is the way to go for me.

See ya
Ken

---

### Post by Psumi on 2009-12-11
For those of you going to xdm, try wdm.

---

### Post by hoppipolla on 2009-12-11
Why have they stopped working on Entrance? :(

Entrance is the very most awesomest :(

[http://xcomputerman.com/pages/entrance.html](http://xcomputerman.com/pages/entrance.html)

[IMG]http://i45.tinypic.com/nnofuh.jpg[/IMG]



I use KDM but... man Entrance needs some love, it looks so good O.O

---

### Post by wsonar on 2009-12-23
> **yabbadabbadont said:**
> Because the ultimate aim of the gnome devs is to prevent any confusion among the unwashed multitudes by removing all configuration options...

(after all, they don't really need them anyway)



Lame Lame Lame

good excuse to move all my devices to KDE

---

### Post by wsonar on 2009-12-23
a

---

### Post by hoppipolla on 2009-12-23
> **wsonar said:**
> a

b :D

---

### Post by hoppipolla on 2009-12-23
> **wsonar said:**
> Lame Lame Lame

good excuse to move all my devices to KDE

haha don't worry that's probably not really the reason, I mean I think they just gave it an overhaul and the configuration needs to catch up... maybe.

Personally I use KDM anyway though. It's a little rough around the edges but it's more configurable, blends well with my KDE desktop and I trust the KDE guys to keep it that way and at some point probably revamp it!

I'll only switch back to GDM if it gets VERY good, or if someone injects more life into Entrance!

---

### Post by sgk on 2010-05-07
@23meg, GNOME developers are supposed to develop for the community, not for themselves. So, they must respond to the needs and wants of the community. Otherwise the users will switch to something else. I myself, after almost 10 years of using GNOME (mostly), switched lately to OpenBox (and Conky, wbar, etc) and am thinking of using KDE 4.x when it gets richer in applications. 
Don't forget that the main reason a lot of people use Linux and its ecosystem, is that they can hack it, they can adapt to their needs and likes;), otherwise they could stick with Micro$oft.

---

