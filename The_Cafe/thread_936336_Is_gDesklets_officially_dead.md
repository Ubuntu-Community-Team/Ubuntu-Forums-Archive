---
title: "Is gDesklets officially dead?"
date: 2008-10-02
forum: The Cafe
---

### Post by itsjustarumour on 2008-10-02
Is "gDesklets" officially a dead project?

Theres been no news or activity on the gDesklets site for six months now, many of the developers seem to be working on other projects, and from what I can see it isn't even registered as a project on [www.gnome.org](www.gnome.org) any more.

In the meantime, the old packages remain unmaintained and are becoming more and more broken and obsolete.  For example, the weather control has been broken for nearly three *years* (yes, I know about the GoodWeather gDesklet that can be made to work, but thats a community-provided hack.)  And what few "new" gDesklets there have been can be counted on one hand...

Are there any developers out there who can shed some light on the current state of play?  Can we *ever* expect new packages?  Even just a new weather gDesklet would be nice!

And what about other "desktop widget" type systems?  "aDesklets" appears to have been dead for a long time now.  "Screenlets" is dead, following the sad departure of the remaining main developer (and all-round Screenlets hero) Whise a few months ago.  There is "Universal Applets", but thats very "experimental".  "Google Gadgets" in its Linux version is also in early development, and from my experience is rather buggy and unstable.

So -what do other forum members think about "the state of desktop widgets on Linux today"?  Where does the future lie?  Which widget system do you think is most worthy of our support?  :-)

---

### Post by CarpKing on 2008-10-02
Universal Applets is heading toward a stable release soon, IIRC.  If the other projects are as dead as they sound, it seems that UA is the future, at least for Gnome.  It seems to open up some exiting possibilities of integration with other projects.

---

### Post by billgoldberg on 2008-10-02
Wait, what, screenlets is dead?

---

### Post by CarpKing on 2008-10-02
> **billgoldberg said:**
> Wait, what, screenlets is dead?

Whise was the main one working on it, and he left the project a few months back.  Universal Applets is a fork of it in which development is continuing.  UA development and use is still discussed in the Screenlets section of the Compiz-Fusion forums, so there isn't a great loss of continuity.

---

### Post by itsjustarumour on 2008-10-02
> **billgoldberg said:**
> Wait, what, screenlets is dead?

Yes, and has been for some months.  Although many people are still working on Applets for the Screenlets framework, the main project itself is dead.

Long story short (and I'll try and stay clear of politics here!), Screenlets originally had 2 main developers, Whise and RYX (Rico Pfaus) who based the project at [www.screenlets.org](www.screenlets.org)  RYX was Webmaster of the site, and suddenly went missing, leaving Whise on his own.  The project forum then moved to [http://forum.compiz-fusion.org/forumdisplay.php?f=102](http://forum.compiz-fusion.org/forumdisplay.php?f=102)  

Other developers were on board too, but in June Whise had a very unfortunate and public spat with another developer (Aantn) and abandoned Screenlets to work on his own projects.  Aantn then forked Screenlets, thus creating "Universal Applets".

[http://forum.compiz-fusion.org/showthread.php?p=65210](http://forum.compiz-fusion.org/showthread.php?p=65210)

September 1st, 2008, 06:49 PM 
"Screenlets has been abandoned, and Whise is working on a project to run OS X widgets on Linux."

So thats it, in a nutshell I guess.  I've tried UA but couldn't get it to work - have other peeps had more success with it?

---

### Post by UbuWu on 2008-10-02
Universal applets is a fork of screenlets and seems to be developed much faster.

---

### Post by billgoldberg on 2008-10-02
Oh.

I'm glad to hear they are building further on the base (just like google gadgets did).

---

### Post by hanzomon4 on 2008-10-02
what happened to RYX?

---

### Post by itsjustarumour on 2008-10-02
> **billgoldberg said:**
> Oh.

I'm glad to hear they are building further on the base (just like google gadgets did).

Exactly - Screenlets had a fantastic level of awesome goodness, but there was still a lot to be done - it was only a 0.12 release after all!  

Reckon I'll go try downloading UA again and see how I get on...

:-)

---

### Post by itsjustarumour on 2008-10-02
> **hanzomon4 said:**
> what happened to RYX?

I don't know - I gather from his old posts that Whise tried at some length to get hold of him, but he just.... disappeared.  Hopefully nothing too bad happened to him...

---

### Post by billgoldberg on 2008-10-03
> **itsjustarumour said:**
> I don't know - I gather from his old posts that Whise tried at some length to get hold of him, but he just.... disappeared.  Hopefully nothing too bad happened to him...

[not funny]

Maybe it was one of Hans Reiser's aliases.

[/not funny]

---

### Post by conundrumx on 2008-10-03
Screenlets 0.1.2 is plenty usable for the time being.  :)

Maybe when UA grows up a little bit more I'll make the switch.

---

### Post by itsjustarumour on 2008-10-03
I've just checked out UA again and it wants me to uninstall my beloved Screenlets, so I think I'll hang fire for the moment as its my main Hardy box (the other one is running Intrepid Beta - tried installing UA on that but no joy).

Does anybody actually know what UA looks like?  Doing a quick image search on Google doesn't find much in the way of screenshots - do they look the same as Screenlets?

---

### Post by Technoviking on 2008-10-03
Is there a PPA for Universial Applets for Hardy?

---

### Post by itsjustarumour on 2008-10-04
> **Technoviking said:**
> Is there a PPA for Universial Applets for Hardy?

I've been using this one:

deb [http://ppa.launchpad.net/ketilwaa/ubuntu](http://ppa.launchpad.net/ketilwaa/ubuntu) hardy main


Edit:  See this thread for further details [http://forum.compiz-fusion.org/showthread.php?t=6889](http://forum.compiz-fusion.org/showthread.php?t=6889)

---

### Post by zekopeko on 2008-10-04
> **itsjustarumour said:**
> I've just checked out UA again and it wants me to uninstall my beloved Screenlets, so I think I'll hang fire for the moment as its my main Hardy box (the other one is running Intrepid Beta - tried installing UA on that but no joy).

Does anybody actually know what UA looks like?  Doing a quick image search on Google doesn't find much in the way of screenshots - do they look the same as Screenlets?

you can safely uninstall screenlets and put UA. UA is just a rename and broader goal for screenlets. basically the point is that you can use UA to have them on your desktop, or your gnome panel or avant or another dock

---

### Post by itsjustarumour on 2008-10-04
> **zekopeko said:**
> basically the point is that you can use UA to have them on your desktop, or your gnome panel or avant or another dock

Ah, I didn't realise that - thats VERY cool! :guitar:

---

