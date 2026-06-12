---
title: "QDE - qt desktop envirement"
date: 2009-08-10
forum: The Cafe
---

### Post by Orange Kingdom on 2009-08-10
I am wondering if it is possible to make a desktop envirenment
based only on the qt toolkit.

KDE is based on qt but why not only qt?

---

### Post by The Toxic Mite on 2009-08-10
> **Orange Kingdom said:**
> I am wondering if it is possible to make a desktop envirenment
based only on the qt toolkit.

KDE is based on qt but why not only qt?

You mean, a Qt-based DE, but without all the KDE applications?

---

### Post by phrostbyte on 2009-08-10
What else is KDE based on?

kdelibs itself is based on Qt.

---

### Post by hanzomon4 on 2009-08-10
Qt DE's off the top of my head... KDE

---

### Post by Orange Kingdom on 2009-08-10
> **The Toxic Mite said:**
> You mean, a Qt-based DE, but without all the KDE applications?

Yes,for example SM-player is a qt only application. It runs without kdelibs.

---

### Post by cdekter on 2009-08-10
KDE is built exclusively on QT but extends it in many ways. This is to provide functionality that is Linux-specific and does not exist in QT by default. Some examples of this would be icon themes and standard buttons. kdelibs also provides a lot of convenience code such as pre-built message dialogs, config dialogs etc. It is quite possible to write an app for KDE that does not have any kdelibs dependencies, but it would not integrate as well.

---

### Post by disturbed1 on 2009-08-10
To help the OP out -

Gnome is to GTK what KDE is to QT. Not only do both DE's require a tool kit, but a plethora of DE specific widgets and wizbangs.

Lxde is to GTK what the OP wants for QT. A light weight window manager without all of the heavy weight over head that builds without any necessary 3rd party wizbangs and widget from the different DE.

Somewhere between Gnome and LXDe lays Xfce. As Xfce does require a tool kit (GTK) and a few DE specific widgets and wizbangs (Exo ....) but is not as  fat as Gnome :)

---

### Post by chucky chuckaluck on 2009-08-10
you might be able to do something like an lxde-frankenstein thing using qlwm as the wm, arora for the browser, vlc for media, juffed for a text editor, fsirc for irc crap. i never found a qt file manager i could get to work though. qtconfig would work great as a theme manager without kde stuff installed.

---

### Post by SunnyRabbiera on 2009-08-10
You know there are many GTK based DE's, so far KDE is the only QT based DE and KDE in its current state is well... bleh.
Now that QT is 100% open source maybe its time for another QT based DE.

---

### Post by CJ Master on 2009-08-11
> **SunnyRabbiera said:**
> You know there are many GTK based DE's, so far KDE is the only QT based DE and KDE in its current state is well... *awesome*.
Now that QT is 100% open source maybe its time for another QT based DE.

Fix'd that for you.

I don't see a point on another QT based DE, it'd just slow down progress.

---

### Post by Jimleko211 on 2009-08-11
> **CJ Master said:**
> 

I don't see a point on another QT based DE, it'd just slow down progress.
Uh...what?  This can only help progress...develop some great ideas that are harder to implement in KDE.

---

### Post by HappinessNow on 2009-08-11
Rat PoisonQT DE

---

### Post by lykwydchykyn on 2009-08-11
I love KDE 4.  But I'd also like to see a slimmed-down DE based on Qt; if it could bring some novel ideas to the table, why not?  Why does it have to be either "KDE stinks" OR "we don't need another Qt DE"?

Though, I think the problem is that most people who start out writing a "minimal DE" want to make it as fast and small as possible; Qt has the reputation (deserved or otherwise) of being heavier than Gtk.  So Gtk gets picked.  By the time the DE grows beyond "fast and light" status (*cough* XFCE *cough*) the choice of toolkit is pretty well entrenched and unchangeable.

See the LXDE FAQ q5 on toolkits:
[http://lxde.sourceforge.net/faq.html](http://lxde.sourceforge.net/faq.html)

---

### Post by SunnyRabbiera on 2009-08-11
> **CJ Master said:**
> Fix'd that for you.

I don't see a point on another QT based DE, it'd just slow down progress.

Feh KDE4 so far is all flash and no substance, KDE4 might look nice but in terms of functionality I think it phails.

---

### Post by coqui1212 on 2009-11-16
I'd agree with that, KDE just tried it and it really isnt as stable or feature complete as GNOME....on the other hand it is very pretty not going to knock it off for that.

---

### Post by hoppipolla on 2009-11-16
Well, **IMO** Qt is the best toolkit in the world so...  I think it would be a good place to start! ^_^

---

### Post by Chronon on 2009-11-17
> **coqui1212 said:**
> I'd agree with that, KDE just tried it and it really isnt as stable or feature complete as GNOME....on the other hand it is very pretty not going to knock it off for that.

What do you mean by feature complete?  It has been rock solid for me since 4.2.

---

### Post by coqui1212 on 2009-11-17
well some programs by default just didnt seem, right. Hopefully this gets fixed with project timelord. till then I'll keep on having to customize my GNOME desktops to get the look I want. GNOME on the other hand very feature-complete and stable, but by default bland, KDE=fruit loops GNOME=cheerios

---

### Post by Crunchy the Headcrab on 2009-11-17
> **coqui1212 said:**
> KDE=fruit loops GNOME=cheerios
Oh snap!  I love fruit loops.  *drooling*

And all this time I thought I preferred Gnome over KDE.  I'm gonna have to seriously reconsider my choice in DE now.

---

### Post by kk0sse54 on 2009-11-17
I don't know about DEs but some QT WMs are:
Antico
QLWM
Integrity WM (outdated)

---

### Post by Muppeteer on 2009-11-17
> **SunnyRabbiera said:**
> Feh KDE4 so far is all flash and no substance, KDE4 might look nice but in terms of functionality I think it phails.

Eh what? I get far more done in KDE than i ever did in 3 years of using Gnome. I'm guessing you haven't used it past 30 mins.

---

### Post by SuperSonic4 on 2009-11-17
> **SunnyRabbiera said:**
> Feh KDE4 so far is all flash and **no substance**, KDE4 might look nice but in terms of functionality I think it phails.

Bold bit is false. Forget your opinion - it is factually false!

The rest is your opinion and fair enough there. I disagree with you, I can use KDE4 to make business documents and have been since KDE 4.0

Look on the bright side, at least KDE isn't stuck in the 90s

---

### Post by ichat on 2010-08-13
> **SuperSonic4 said:**
> Bold bit is false. Forget your opinion - it is factually false!

The rest is your opinion and fair enough there. I disagree with you, I can use KDE4 to make business documents and have been since KDE 4.0

Look on the bright side, at least KDE isn't stuck in the 90s

the most stupid thing to do is 'saying someone's a troll and than trolling yourselfe. 

face it,  KDE IS  mutch more resource hungry than gnome is,  many of its apps are inferior to what they could have been. 

really the only kde superior app is k3b ...    (compared to gnomebaker) ..... 

even somthing as stuppid as Epiphany -  feels faster than  konquerer. 

 where kde3 was kinda nice, kde4 is all about the looks,   hell even lxde will get better than kde if they dont better themselves. 

QT is a great toolkit, and has more potential than GTK,   but the have to invest in sleekness,  and more modular  design....

---

### Post by Simian Man on 2010-08-13
QT already has a fantastic desktop in KDE4.  The biggest problem with QT is lack of great applications.  Making another QT desktop seems pointless when most KDE users have to use a GTK+ web browser.

---

### Post by cariboo on 2010-08-13
@ichat, if you look at the poster above you, their beans are burnt, which means that particular poster does not have access to the forums anymore. There really was no reason to open up this thread again. Closed.

---

