---
title: "Is it worth moving from 10.04 to 11.04 on PanP5?"
date: 2011-04-30
forum: System76 Support
---

### Post by samalex on 2011-04-30
Hey Guys --

I've been rockin' along on my Panp5 for about two years now, loving 9.04 then moved to 10.04 last year.  But just curious, now that 11.04 is out are there any major Pro's to moving that way?  I honestly had no problems with 9.04 but moved to 10.04 mainly to get Ubuntu One and some other perks.  Are there any similar 'must haves' in 11.04 that won't be made availble to 10.04?  Also for anyone running a PanP5 what's the driver support like with 11.04?

Thanks --

Sam

---

### Post by HotShotDJ on 2011-04-30
Hi, Sam!

I just upgraded to 11.04 + Gnome3 (the new Unity made me insane... I just don't like the look & feel of it).  Gnome 3 will be nice someday... but it just feels unfinished, which is probably why Ubuntu developers didn't put it in 11.04 by default.

There are a few problems with 11.04 that developers are actively working on.  1) Bluetooth:  It works, but not very smoothly.  You need to go to the terminal and issue the following commands:```
sudo killall bluetoothd
sudo bluetoothd
```After that, I have to manually reconnect my bluetooth mouse.  All of this happened automatically in previous versions of Ubuntu once I turned on bluetooth with fn+F12. (See [Bug #762964]("https://bugs.launchpad.net/system76/+bug/762964"))

2) The fingerprint reader doesn't work as expected: see [This Post]("http://ubuntuforums.org/showpost.php?p=10735961&postcount=34") and [This Reply]("http://ubuntuforums.org/showpost.php?p=10738035&postcount=35") in [This Thread]("http://ubuntuforums.org/showthread.php?t=1669245").

Other than those two issues, I haven't found anything earthshaking wrong with 11.04.  On the other hand, I haven't found anything that would make it a "must have" upgrade.

As per usual, I'm going to see what's happening in KDE land with 11.04.  If I like it, I'll keep it it.  In any case, I need to do a complete reinstall to get rid of Gnome 3.

Good luck!

EDIT:  Ok... KDE land was a bust.  3d effects were a disaster... the simplest thing crashed my desktop.  And my dual monitor set up was a non-starter (as was the case in Gnome 3). Of course, the bluetooth bug is there too.  So, it is back to the default Ubuntu 11.04.  Maybe I'll get used to this Unity interface.  Its not too bad.. really.. sort of. (And there is always the option of the "classic" interface).

---

### Post by inof8or on 2011-04-30
Im get ready to switch over to the narwhal on my panp5 and have already on my tablet. The only reason its a must have for me is that a kernel update broke compatibility with my wacom bamboo pen and I was too lazy to fix it. Natty comes with working drivers for wacom devices right from the get go. Personally i like unity but i think it depends on preference and how long you've been with gnome or w.e. 

The one thing that bothers me about unity is that i have yet to get gnome-do to run in the background. (can start it though) Unity includes a similar function as gnome do in its main applet but its a little slow compared to gnome do. The past few version of ubuntu (from lucid on) I have found keybindings difficult to get to work consistently and this holds true in natty. (try changing alt-f4 to alt-X)   

Ill let you know how things go Sam

---

### Post by isantop on 2011-05-02
As an aside, the bluetooth issue has been fixed and is waiting to come down shortly. I'm not sure exactly when it will land, but it should be soon.

---

### Post by HotShotDJ on 2011-05-02
> **isantop said:**
> As an aside, the bluetooth issue has been fixed and is waiting to come down shortly. I'm not sure exactly when it will land, but it should be soon.It landed this morning (in proposed).  Works a treat!

---

### Post by johnnybgoode83 on 2011-05-02
I upgraded from Maverick to Natty and had it installed for an hour but I could not get on with Unity so I did a fresh Maverick install.  If this is the future of Ubuntu I am trully worried.

---

### Post by HotShotDJ on 2011-05-02
> **johnnybgoode83 said:**
> I upgraded from Maverick to Natty and had it installed for an hour but I could not get on with Unity so I did a fresh Maverick install.  If this is the future of Ubuntu I am trully worried.You know, you didn't HAVE to downgrade back to Maverick to avoid Unity.  You could have simply chosen Gnome Classic from the login screen.

I don't particularly care for Unity... it just seems "clunky" to me. And bloody unconfigurable -- "You'll do it OUR way and you'll LIKE it."  I DO like what I'm seeing with Gnome 3 though.  It just needs to be properly integrated into Ubuntu and polished up a bit, and more configuration options, of course.

---

### Post by HotShotDJ on 2011-05-04
Hi, again, Sam --

Well, I found a "deal breaker" with the Unity interface.  I cannot switch between dual-monitor and single monitor on my laptop.  That makes the Unity interface unusable to me, since I use an external monitor set-up when I'm working at my desk, but will often unplug and use my PanP5 in other rooms or even at meetings.  Additionally, the lack of configuration options has made the top panel useless for my mother -- she can't see it well enough and there is no way (that I've found) to increase the size of that panel.  Again, a deal-breaker.

Switching to "Classic" mode fixes these problems.  So for now, Unity has been banished from any computers that I manage (ok, it not like that's saying a lot... I manage 4 computers :lolflag:) Quite honestly, I already don't miss it. :)  Now all I need to do is put Docky back on the system, and I'll be happy again.

---

### Post by ebasa on 2011-05-04
No logical reason to upgrade from 10.04 until the next LTS release.

---

### Post by robtg on 2011-05-04
I did an online upgrade from 10.10 to 11.4 (PanP5).  The upgrade went fine but Unity left me a bit cold; it seems like a solution to a nonexistant problem on a laptop or desktop computer; change for the sake of change.  I guess I could have selected "classic" Ubuntu from the logon screen but I decided to scrap the whole thing and go back to 10.4 (LTS).  Firefox 4 and Libre Office are nice but not essential to me.

Rob

---

### Post by Zundap on 2011-05-06
Could i ask a question here?  If 11.04 is no  improvement on 10.04, why would they produce 11..04? Does anyone know?

---

### Post by HotShotDJ on 2011-05-07
> **Zundap said:**
> Could i ask a question here?  If 11.04 is no  improvement on 10.04, why would they produce 11..04? Does anyone know?There were many changes and updates from 10.10 to 11.04.  Some of those changes (eg Unity, LibreOffice) were quite visible to the user, while others were "under-the-hood."  The OP's did not ask if there were any improvements... there ARE many improvements.  His question was whether those improvements were worth the effort and potential pitfalls of upgrading on a specific system.

Ubuntu offers improvements/upgrades/new features on a regular 6 month development cycle.  To what extent these new versions are "worth it" is very much an individual decision.  Why do they do it?  To keep things moving forward and evolving.

To what extent people want to take part in that evolutionary process differs from individual to individual.  This is why Ubuntu users have choices... they can stick with the LTS releases and upgrade every couple of years, they can go with every 6 month release, they can even use developmental software (pre-release versions).  And of course, you can mix and match.  Its all about choice and evolution.  I think its pretty cool.

---

