---
title: "The quest for a MSN messaging client ..."
date: 2009-02-04
forum: The Cafe
---

### Post by bash on 2009-02-04
Well I am once again at the point that I don't seem to be able to find a MSN client that suits my needs. At least for me the seem pretty humble: Basic functionality (messaging, avatar and file transfer support - don't care about anything else) and a GTK+ interface. 

I don't know if anyone else is searching a MSN client atm or if everyone found something that suits them brilliantly, but I just want to list my findings so far:

**Pidgin**

Comes installed by default so first thing I tried again. Has my type of simple and slim layout and even supports the features I need. So what spoils the party? I use Pidgin for quite a few other protocols for other areas, so I don't want to mix all those contacts with my MSN contacts. Sadly Pidgin doesn't offer me the possibility to run multiply instances of it or the chance to have seperate contact lists for each account/protocol.

**emesene**

Link: [www.emesene.org](www.emesene.org)

Easy to get by to, just install it from the Repository or download a .deb from their page. After the release of the very promising version 1, they focus now on developing a complete rewrite. Meanwhile version 1 is pretty much unsupported and accumulated quite a few quirks over the past months. And I personally am not a big fan of their chat window. Way to clunky for my taste (But that's just personal opinion.

**amsn**

Link: [www.amsn-project.org](www.amsn-project.org)

Again pretty common and well known messenger. Simple install from the repos and your set. Got all the MSN features I need and isn't too bloated. Except the Interface makes my eyes. Not a big fan of tcl/tk for interfaces (Or at least not as long as I have a decent eye sight). Well version 2 which they are currently working on seems to finally bring along GUIs in toolkit of your (and my) liking. Sadly version 2 isn't to far along the way yet and in my view more a thing for devs to play and tweak around with and people who like to live on the bleeding-svn-edge. But that might be why it say "in development" ;)

**galaxium**

Link: [http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

So here we have a bit of a less known one. Used to be (and still is atm) my default MSN client. It is not included in the Repos but the provide a PPA (Link: [https://launchpad.net/~galaxium/+archive/ppa](https://launchpad.net/~galaxium/+archive/ppa)). I would advise to install the galaxium-svn package instead the galaxium one, as it offers a lot more features but is also quite stable. Sadly their development seems to have stopped. They don't provide a .deb for intrepid yet and had only 4 commints in the last 4 months and all of them small things like adding a line of code. This is not the first time though, as when I first found the client back in 2007 development also stopped for roughly a year and then they picked up again in mid 2008. So I'm hoping they come back this time as well. The client itself has quite a few features and a nice and clean interface. Sadly neither the old version nor the svn run completly stable for me. And I never managed to get file transfers to work with it.



So this is where I am currently at. Maybe someone finds this useful or informative. Besides that if anyone knows any other MSN clients I could take a look at just reply with their name. Got no problem with downloading/compiling things myself. My only criteria really is to find a client that fits me :)

---

### Post by Polygon on 2009-02-04
just use pidgin and have all of your msn contacts in their own group. Running two IM programs seems stupid and reminds me of my days before i discovered gaim/pidgin.

---

### Post by kk0sse54 on 2009-02-04
There's also Kopete

---

### Post by m_duck on 2009-02-04
I think there is a way to run multiple instances of pidgin, though I can't remember how. It may be a plugin...

EDIT: Just had a look and can't seem to find anything, so perhaps there isn't.

---

### Post by JordyD on 2009-02-04
> **Polygon said:**
> just use pidgin and have all of your msn contacts in their own group. Running two IM programs seems stupid and reminds me of my days before i discovered gaim/pidgin.

Or you could just mix them up. When you hover your mouse over them, it shows you the protocol. I'm not sure if they do it in Pidgin (since I use Kopete), but in Kopete they display the protocol via a little icon right next to the screen name.

---

### Post by Rokurosv on 2009-02-04
I second Kopete, it has great integration with KDE. You could also try Empathy [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

---

### Post by Polygon on 2009-02-05
> **JordyD said:**
> Or you could just mix them up. When you hover your mouse over them, it shows you the protocol. I'm not sure if they do it in Pidgin (since I use Kopete), but in Kopete they display the protocol via a little icon right next to the screen name.

he says he doesnt want his msn contacts mixed in with his other contacts from other protocols. and the solution to that is just put all of the msn contacts in a group together, that way they are separate.

---

### Post by igknighted on 2009-02-05
I'll second Empathy... it's soon to be the gnome default, and in many ways I think is already better than the current options.

---

### Post by Firestem4 on 2009-02-05
I have been using KMess for the past 2 weeks since my kopete decided to screw itself over lol. (I think it happened wheni upgraded to KDE 4.2) Anyways, KMess is nice. its very lite, simple and pleasing interface. It doesnt support some protocols (like mobile phone messaging).

---

### Post by Stu09 on 2009-02-05
> **Polygon said:**
> just use pidgin and have all of your msn contacts in their own group. Running two IM programs seems stupid and reminds me of my days before i discovered gaim/pidgin.

x2

---

### Post by Vince4Amy on 2009-02-05
> I'll second Empathy... it's soon to be the gnome default, and in many ways I think is already better than the current options.

Does Empathy support webcam on MSN/WLM? If so this will be awesome and I will install it even though I use KDE.

---

### Post by igknighted on 2009-02-05
> **Vince4Amy said:**
> Does Empathy support webcam on MSN/WLM? If so this will be awesome and I will install it even though I use KDE.

I dunno if all the code is in place yet, but the biggest draw to it over Pidgin is that webcams are either (a) supported, or (b) there is a roadmap in place on getting it done.  I'm not sure where exactly they are (and there was a HUGE leap from hardy->intrepid, so I would expect Jaunty to an equally huge leap), but go ahead and give it a try.

I think there is also a qt-based telepathy client (psi perhaps?).  Either that or Kopete is planning on switching to telepathy, I forget which.  Either way, a native KDE telepathy-based IM client is in the works too.

EDIT: [http://telepathy.freedesktop.org/wiki/](http://telepathy.freedesktop.org/wiki/)

---

### Post by bash on 2009-02-05
> **Polygon said:**
> just use pidgin and have all of your msn contacts in their own group. Running two IM programs seems stupid and reminds me of my days before i discovered gaim/pidgin.

Well to each it's own. I personally need and want in this case a properly seperated contact list for each protocol/account. The ideal solution would be if Pidgin could display multiple different contact lists.

> **C!oud said:**
> There's also Kopete

> **Firestem4 said:**
> I have been using KMess for the past 2 weeks since my kopete decided to screw itself over lol. (I think it happened wheni upgraded to KDE 4.2) Anyways, KMess is nice. its very lite, simple and pleasing interface. It doesnt support some protocols (like mobile phone messaging).

Kopete isn't bad. Neither is KMess. It's just I want a program with a GTK+ frontend.

> **Rokurosv said:**
> You could also try Empathy [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

> **igknighted said:**
> I'll second Empathy... it's soon to be the gnome default, and in many ways I think is already better than the current options.

Omg! I completly forgot about Empathy. The last time I tried it was during the Gutsy days. I'll give it a try. I hope the interface looks nicer, because last time I tried it, it was kinda clunky.

> **Vince4Amy said:**
> Does Empathy support webcam on MSN/WLM? If so this will be awesome and I will install it even though I use KDE.

I think I remember reading somewhere that Kopete wanted to get integration with Telepathy as well, which is the backend Empathy uses. But I don't know how specific those plans are.

---

### Post by Johnsie on 2009-02-05
I prefer the real MSN messenger to all those clients. It's the only client that has 100% support of all the msn features.

---

### Post by Vince4Amy on 2009-02-05
> I prefer the real MSN messenger to all those clients. It's the only client that has 100% support of all the msn features.

Actually last time I tried versions 6.2 > 7.5 worked great under WINE. 7.5 does require that resource hacker is used to change the version number (or run in Windows 2k mode) as Microsoft force an upgrade to that under XP. 

I just don't like running it through WINE but if you really need the full set of features I know that them versions work (Did when I tried).

---

### Post by Metallion on 2009-02-05
> **bash said:**
> Well to each it's own. I personally need and want in this case a properly seperated contact list for each protocol/account. The ideal solution would be if Pidgin could display multiple different contact lists.

I don't really see what's so different between groups and separate contact lists. You can just hide one group and show the other. If you show only one group at a time it's sort of like one contact list. It's even possible to be online on only a certain protocol.

---

### Post by bash on 2009-02-05
> **Johnsie said:**
> I prefer the real MSN messenger to all those clients. It's the only client that has 100% support of all the msn features.

If you need 100% feature compability there is no way around the official client. But for me personally, I find it too "bloated". Everywhere something's blinking, shaking, moving and so on. Although proper Voice and Video support in the linux clients would be nice. But apparently it is coming for amsn2 and empathy.

---

### Post by sertse on 2009-02-05
Hmm, have you tried the svn version of emesene? I don't know if it solves your issues, but its worth a shot.

[http://www.emesene.org/trac/wiki/SVN](http://www.emesene.org/trac/wiki/SVN)

And guys as if you're so.... defensive about your own preferred client that you defend rather than accept user's specific preferences...

---

### Post by Vince4Amy on 2009-02-05
> **sertse said:**
> Hmm, have you tried the svn version of emesene? I don't know if it solves your issues, but its worth a shot.

[http://www.emesene.org/trac/wiki/SVN](http://www.emesene.org/trac/wiki/SVN)

And guys as if you're so.... defensive about your own preferred client that you defend rather than accept user's specific preferences...

I do keep looking at Emesene but the webcam support is a drawback, does this work in the SVN? And I don't care what people use as long as it works and I'm always willing to change to whatever works best for me.

---

### Post by Bölvaður on 2009-02-05
for running multiple instances of pidgin

```
pidgin &
```

In pidgin each protocol may be put in sepperate group, I have multiple msn groups, one gfire, one jabbar.... and so on.

So you can have group names like
MSN-Joe-Customers,
MSN-Joe-Support,
MSN-Alice-Support,
Googletalk-Friends,
.... and so on.

You even could make subcontacts.. that is expand a user and drag other users into that one so it becomes a subinstance of it, which can be useful for organizing.

---

### Post by Wv0wvw88wvw0vW on 2009-02-05
Why not use [http://www.meebo.com/](http://www.meebo.com/) simultaneously with Pidgin? I'd come up with a more original suggestion, but Pidgin is too good lol

---

### Post by bash on 2009-02-05
> **Wv0wvw88wvw0vW said:**
> Why not use [http://www.meebo.com/](http://www.meebo.com/) simultaneously with Pidgin? I'd come up with a more original suggestion, but Pidgin is too good lol

Meebo's nice if you're on the move. But at home I prefer a "proper" program ;)

> **sertse said:**
> Hmm, have you tried the svn version of emesene? I don't know if it solves your issues, but its worth a shot.

[http://www.emesene.org/trac/wiki/SVN](http://www.emesene.org/trac/wiki/SVN)

And guys as if you're so.... defensive about your own preferred client that you defend rather than accept user's specific preferences...

Yep, gave it a try last week. As with amsn2 it looks promising. But atm isn't in a too usable state. 

> **Vince4Amy said:**
> I do keep looking at Emesene but the webcam support is a drawback, does this work in the SVN? And I don't care what people use as long as it works and I'm always willing to change to whatever works best for me.

Concerning planned features, such as Voice/Video, and their timeframe for emesene 2:

[http://emesene-msn.blogspot.com/2009/01/not-so-frequently-asked-questions.html](http://emesene-msn.blogspot.com/2009/01/not-so-frequently-asked-questions.html)

> **Bölvaður said:**
> for running multiple instances of pidgin

```
pidgin &
```

In pidgin each protocol may be put in sepperate group, I have multiple msn groups, one gfire, one jabbar.... and so on.

[...]

You even could make subcontacts.. that is expand a user and drag other users into that one so it becomes a subinstance of it, which can be useful for organizing.

Thanks for the tip with the multiple instances of Pidgin. Will give it a try. 



Btw, just read this in the release notes for the latest GNOME beta:

> ========================================
 NEWS: empathy-2.25.90
========================================

NEW in 2.25.90
==============
 - Rewrite Voice/Video call UI, and use farsight2 instead of stream-engine. (Sjoerd Simons).

So maybe we do get to see Voice/Video for MSN in Empathy soon.

---

