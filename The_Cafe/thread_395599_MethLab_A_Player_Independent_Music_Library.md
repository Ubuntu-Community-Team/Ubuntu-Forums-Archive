---
title: "MethLab: A Player Independent Music Library"
date: 2007-03-28
forum: The Cafe
---

### Post by OffHand on 2007-03-28
The developer of Nicotine, which is now forked to Nicotine+, made a new application named MethLab. Check the first reply for details about MethLab.

Website: [http://methlab.thegraveyard.org](http://methlab.thegraveyard.org)



First we will have to make sure we have all the dependencies. I think I have covered them here, but if I missed any let me know. ([Source]("http://methlab.thegraveyard.org/wiki/Dependencies"))

dependencies: python2.5 python-ctypes, python- tagpy, libboost-python1.34.1, python-gtk, subversion

```
sudo aptitude install python2.5 python-ctypes python-tagpy libboost-python1.34.1 python-gtk subversion
```


Alright, now that we have all the dependencies covered we can download the svn source code... ([Source]("http://methlab.thegraveyard.org/wiki/MethLabFromSubversion"))

Now we are going to download the svn repository. 

```
svn co http://methlab.thegraveyard.org/svn/trunk methlab
```

Now we will have to navigate inside the directory.

```
cd methlab
```

And finally start up MethLab

```
./methlab
```

If you want to update your copy of MethLab, type:

```

cd methlab
svn update

```

---

### Post by OffHand on 2007-03-28
About MethLab


**What is it?**

MethLab is a music library manager that allows you to perform queries on your music. It can also interface with various music players to play or enqueue the results of your query.

**Goals**

MethLab aims to provide:

    * A clean and simple to understand (and to use) interface.
    * A non-instrusive addition to the music player you're already using. 

**Supported platforms**

MethLab is being developed on arch linux so that is the primary 'target'. However, there should be very little platform dependent code (exception being the audio player drivers). As long as you get the dependencies installed, MethLab will probably run. MethLab would run on windows if there was a useful audio player driver.

**Supported players**

Currently, MethLab supports a handful of players: XMMS, Beep, Audacious and MPD. The MPD audio player driver can only be used with the MPD database source.
[B]
Database sources[/B]

MethLab collects its data from a database source. Currently two database sources are included with MethLab: the filesystem source and the MPD source. The filesystem source uses a tagging library (tagpy or mutagen) to extract metadata tags from the files in your music library. The MPD source connects to the music player daemon and synchronizes MethLab's database with the MPD library. The MPD source only works with the MPD audio player driver.

---

### Post by OffHand on 2007-03-29
bump

---

### Post by OffHand on 2007-03-30
bump

---

### Post by OffHand on 2007-04-01
up

---

### Post by stokedfish on 2007-04-01
Honestly, I'd prefer a better Museek.

But yeah, looks promising!  ;)

---

### Post by OffHand on 2007-04-02
> **stokedfish said:**
> Honestly, I'd prefer a better Museek.

But yeah, looks promising!  ;)

:) 

bump

---

### Post by banjobacon on 2007-04-02
There's probably little interest in this because most people who want a music library already use Amarok, Rhythmbox, Banshee, Exaile, Listen, or one of the other several player/library combinations.

---

### Post by OffHand on 2007-04-02
> **banjobacon said:**
> There's probably little interest in this because most people who want a music library already use Amarok, Rhythmbox, Banshee, Exaile, Listen, or one of the other several player/library combinations.

Yeah probably... it's a crazy idea. Nevertheless, I find this application great to find and play my music very quickly.

---

### Post by joeblow1102 on 2007-04-05
Just so you know, your efforts are not in vain.  I'm currently using your program because Madman keeps crashing on me.  I think this has a lot of potential and thanks for making a music library program!

Edit: I do have two small requests though.  1.  can methlab remember which view i'm in.  say i am in artists/albums view, and minimize methlab to tray, when i go to methlab again, it takes me to search options mode.  2.  can the artists/albums view mode be more tree-like?  instead of showing everything, can it just show artists, then when i click on the artist name, it shows me the albums.

---

### Post by OffHand on 2007-04-06
> **joeblow1102 said:**
> Just so you know, your efforts are not in vain.  I'm currently using your program because Madman keeps crashing on me.  I think this has a lot of potential and thanks for making a music library program!

Edit: I do have two small requests though.  1.  can methlab remember which view i'm in.  say i am in artists/albums view, and minimize methlab to tray, when i go to methlab again, it takes me to search options mode.  2.  can the artists/albums view mode be more tree-like?  instead of showing everything, can it just show artists, then when i click on the artist name, it shows me the albums.

I am glad you like it :)  I did not program it myself though: a friend of mine programmed it.
To request new features or improvements, please go to the following website and file a new ticket:

[http://methlab.thegraveyard.org/](http://methlab.thegraveyard.org/)

Cheers,

OffHand

---

### Post by zanglang on 2007-04-07
Hmm, this is looking pretty interesting! Having used Sonata (Python mpd client) for a while, music management in these super minimalistic mpd clients always seemed a little lacking...

Will give it a spin and see how it turns out. Thanks. ;)

---

### Post by joeblow1102 on 2007-04-09
I'm actually not allowed to create a new ticket because I don't have access to the creation of a new ticket, probably because I'm not logged in.  Also, I'm not allowed to create a new account, or I can't find where to do this.

---

### Post by OffHand on 2007-04-09
> **joeblow1102 said:**
> I'm actually not allowed to create a new ticket because I don't have access to the creation of a new ticket, probably because I'm not logged in.  Also, I'm not allowed to create a new account, or I can't find where to do this.

Click this link: [http://methlab.thegraveyard.org/newticket](http://methlab.thegraveyard.org/newticket)

(you do not have to register to file a ticket)

---

### Post by Mateo on 2007-04-09
does it minimize to the tray?

---

### Post by OffHand on 2007-04-09
> **Mateo said:**
> does it minimize to the tray?

Yes, it does.

---

### Post by darkhatter on 2007-04-09
ever thought of name change :lolflag:

---

### Post by OffHand on 2007-04-09
> **darkhatter said:**
> ever thought of name change :lolflag:

Well, he called his other application Nicotine. I wonder what will be next...

 :guitar:

---

### Post by OffHand on 2007-04-10
bump... (don't forget to svn up regularly as ML is under construction all the time)

---

### Post by warp99 on 2007-04-10
> **darkhatter said:**
> ever thought of name change :lolflag:


I hate to say it, but if I said "I have Methlab" most likely I would get served with a search warrant. Remember I live in the meth capital of the world aka Des Moines, Iowa. :frown:

---

### Post by OffHand on 2007-04-11
> **warp99 said:**
> I hate to say it, but if I said "I have Methlab" most likely I would get served with a search warrant. Remember I live in the meth capital of the world aka Des Moines, Iowa. :frown:
Well, I see where you are coming from but I can't imagine you would use it totally out of the context.
You can always suggest a name change through a ticket though.

---

### Post by H.E. Pennypacker on 2007-04-11
I'll check it out some other time, because I am currently using CrackLab.  It fills my needs!

---

### Post by OffHand on 2007-04-11
> **H.E. Pennypacker said:**
> I'll check it out some other time, because I am currently using CrackLab.  It fills my needs!

Use whatever floats your boat, I always say  ;)

---

### Post by OffHand on 2007-04-14
bump

---

### Post by OffHand on 2007-04-16
Bump

---

### Post by Mateo on 2007-04-16
yeah, i don't like it for the name also.  same reason i don't like damn small linux.  i wanted to install damn small linux on my mother's computer, but didn't because of the name.

---

### Post by OffHand on 2007-04-16
Seriously... you guys need to relax a bit and do not take everything so seriously. It's just a joke...

---

### Post by hanzomon4 on 2007-04-16
> **Mateo said:**
> yeah, i don't like it for the name also.  same reason i don't like damn small linux.  i wanted to install damn small linux on my mother's computer, but didn't because of the name.

I'll never understand this think :confused: 

Can Meth-Lab interface with music-players that have their own library(listen, exaile!, amarok) and does it work with video?

---

### Post by Mateo on 2007-04-16
> **OffHand said:**
> Seriously... you guys need to relax a bit and do not take everything so seriously. It's just a joke...

a "joke" that is costing you potential users.  i personally don't think the "joke" is hilarious enough to justify having to explain to every person who uses my computer why I have a program called "methlab" installed.

---

### Post by OffHand on 2007-04-16
> **hanzomon4 said:**
> I'll never understand this think :confused: 

Can Meth-Lab interface with music-players that have their own library(listen, exaile!, amarok) and does it work with video?

Currently, MethLab supports a handful of players: XMMS, XMMS2, Beep, Audacious and MPD. Methlab indexes music files only atm. As I am not the developer I don't know if it can be implemented or if he wants to implement it. Your best chance is to file a ticket on the website and ask for it.

[http://methlab.thegraveyard.org/newticket](http://methlab.thegraveyard.org/newticket)

---

### Post by OffHand on 2007-04-19
up

---

### Post by ABCC on 2007-04-26
Having fun bumping and grinding OffHand?

---

### Post by OffHand on 2007-11-04
For those that are using MethLab... if you have not updated for a while cd into your MethLab folder and run svn up

Hyriand commited some nice updates.

---

### Post by banda on 2008-01-28
hey thanks to whoever created methlab.. i have been using it with audacious over the last few months, no problems whatsoever!

one small feature i would like added is the ability to adjust the column widths(right now it adjusts itself according to the content).. and maybe a borderless ui??

---

### Post by OffHand on 2008-01-28
> **banda said:**
> hey thanks to whoever created methlab.. i have been using it with audacious over the last few months, no problems whatsoever!

one small feature i would like added is the ability to adjust the column widths(right now it adjusts itself according to the content).. and maybe a borderless ui??

For a feature request you will have to file a ticket. This is the MethLab website: [http://methlab.thegraveyard.org/](http://methlab.thegraveyard.org/)

MethLab is not actively in development right now but the guy who wrote it might do it anyways.

---

### Post by 00l0 on 2008-07-03
hey i'm interested in methlab,
i run methlab, i scan all my music library, but when i click on enqueue a certain song/album, i get this error message:

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.atheme.audacious was not provided by any .service files

what am i missing?

thank you!

---

### Post by OffHand on 2008-07-04
> **00l0 said:**
> hey i'm interested in methlab,
i run methlab, i scan all my music library, but when i click on enqueue a certain song/album, i get this error message:

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.atheme.audacious was not provided by any .service files

what am i missing?

thank you!

Did you install all the dependencies? Is Audacious already running when you queue the songs? Which version of Audacious are you running?

P.S. You can also try the xmmsalike driver instead of Audacious dbus.

---

### Post by JoZ3 on 2010-09-14
Any new alternative?

---

