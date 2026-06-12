---
title: "KDE in Windows?"
date: 2006-07-31
forum: The Cafe
---

### Post by hizaguchi on 2006-07-31
I found [this guide]("http://wiki.kde.org/tiki-index.php?page=KDE+on+windows") for compiling KDE in Windows.  This is very interesting to me, because I have to use Windows frequently for CAD software.  I was wondering if anybody had tried this approach and could give me some insight on the results.  Can I run Windows apps in KDE this way?  Granted, I'd still be stuck with that Windows system under it, but at least it wouldn't be so ugly and I could use Kate and Amarok. :)

---

### Post by Jucato on 2006-07-31
Haven't tried it yet but would be very, very, interested. However, I think this is more applicable to KDE 4 rather than the current KDE 3.5.x series. It also looks very complicated.

Hope someone has had any experience with this.

---

### Post by mips on 2006-07-31
Besides Linux, KDE4 is also suppose to be available for Windows & OSX if I recall correctly. They reckon with Qt4 & code cleanup it would be easier to port to other OSs, so you might see it on multiple OSs

---

### Post by Jucato on 2006-07-31
Yeah KDE 4 is supposed to be able to run on Windows, too. I'm not sure how much setup it would require. The only problem is waiting for it to come out.

The wiki, as far as I can tell, is about compiling the KDE 4 trunk on Windows. And since it's not even "beta", it's bound to be pretty useless for everyday usage, I suppose.

---

### Post by fuscia on 2006-07-31
"would you care for some whipped cream on your dog mess?"

---

### Post by Jucato on 2006-07-31
> **fuscia said:**
> "would you care for some whipped cream on your dog mess?"

"No, but I would certainly like to take my bitter pills with some sweet tasting juice." :D

---

### Post by Kimm on 2006-07-31
As far as I know OS X can run KDE3, mostly since its Unix based.

---

### Post by mips on 2006-07-31
> **Fenyx said:**
> 
The wiki, as far as I can tell, is about compiling the KDE 4 trunk on Windows. And since it's not even "beta", it's bound to be pretty useless for everyday usage, I suppose.

The instructions seem good and look pretty simple but that's not to say you are not going have problems. Yeah, it's not even beta yet so you might as well delve into black magic at this stage ;)

---

### Post by exisn on 2006-07-31
Though it's a long time ago, I managed to get KDE up and running by using cooperative linux and the X server from cygwin. It runs decently although a bit too slow for me.

I think this was the site I used back in the days:
[http://kde-cygwin.sourceforge.net/kde3/]("http://kde-cygwin.sourceforge.net/kde3/")

---

### Post by hizaguchi on 2006-07-31
The more I read about this the less worthwhile it seems.  Certain programs, like Kate, AmaroK, Kontact, and Konqueror, are irreplaceable in Windows.  But at the same time, I'd rather do without them than to jump through flaming hoops while juggling pink chickens just to end up with a solution that is noticably hacked together.  I think I'll wait for KDE4.  Either that or try to get SolidWorks working in Linux.  Think I need 3D graphics support for that though.

---

### Post by hizaguchi on 2006-08-07
If anybody is interested in this kind of thing and doesn't want to wait till KDE4, coLinux with Xming is a workable option.  The lack of any good documentation makes it a total pain to set up, and running a whole desktop environment on it is pretty slow, but individual apps are pretty quick.  It's worth it to me just for Kate and AmaroK.

---

### Post by Lord Illidan on 2006-08-07
Kate - [notepad++]("http://notepad-plus.sourceforge.net/uk/about.php")
Amarok - [Music Cube]("http://www.musikcube.com/") or [Foobar2000]("http://www.foobar2000.org/")
I am in the same boat, mate. I need Turbo Pascal for school, and it works like a dog under Dosbox and Dosemu...so I have to make do without those two apps..

---

### Post by hizaguchi on 2006-08-07
> **Lord Illidan said:**
> Amarok - [Music Cube]("http://www.musikcube.com/")
:o How did I not know about this?  I've been using Foobar since the mp3 gods decided all Windows players should look like Fisher Price car stereos.  Musikcube looks nice though!  And definately looks more fully featured than Foobar.  Thank you!

Notepad++ doesn't look like it'll quite do what I need though.  I write alot of Matlab/Octave scripts and Kate is incredibly useful because of the built-in terminal to run them in.  It does look nice though, and maybe that feature is in there and I don't see it.

Have you tried running FreeDos (or even Windows) in VMware for your Pascal?  Windows XP runs fairly well with VMtools installed... just not nearly good enough for CAD.

---

### Post by Terracotta on 2006-08-07
> **Lord Illidan said:**
> Kate - [notepad++]("http://notepad-plus.sourceforge.net/uk/about.php")
Amarok - [Music Cube]("http://www.musikcube.com/") or [Foobar2000]("http://www.foobar2000.org/")
I am in the same boat, mate. I need Turbo Pascal for school, and it works like a dog under Dosbox and Dosemu...so I have to make do without those two apps..

Oh yuk are you serious? These programs don't even come close to Amarok, amarok isn't like the next iTunes or winamp rip off you know, completely different setup. Well wait for kde4 core libs to be ported to windows, then Amarok and kaffeine and... will follow. Plasma on the other hand isn't going to be ported since it needs an X-server too much.

---

### Post by hizaguchi on 2006-08-07
> **Terracotta said:**
> Oh yuk are you serious? These programs don't even come close to Amarok, amarok isn't like the next iTunes or winamp rip off you know, completely different setup. Well wait for kde4 core libs to be ported to windows, then Amarok and kaffeine and... will follow. Plasma on the other hand isn't going to be ported since it needs an X-server too much.
I dunno, I just installed Musikcube and I like it so far.  No, it doesn't have as many wild features as AmaroK, nor is it as attractive or integrated with the desktop environment.  It is the best Windows player I've ever seen though, and what's out now is still just a release candidate.  So you're right, it's not as good as AmaroK.  But this is Windows we're talking about, and if you're going to use such a deprecated OS you have to be willing to make some sacrifices. :)

---

### Post by Terracotta on 2006-08-07
> **hizaguchi said:**
> I dunno, I just installed Musikcube and I like it so far.  No, it doesn't have as many wild features as AmaroK, nor is it as attractive or integrated with the desktop environment.  It is the best Windows player I've ever seen though, and what's out now is still just a release candidate.  So you're right, it's not as good as AmaroK.  But this is Windows we're talking about, and if you're going to use such a deprecated OS you have to be willing to make some sacrifices. :)
Lol, you're right about that, but well I don't use amarok for its features I just use it because it is plain simple, it took me no hassle to come from winamp and wmp to amarok, but going from amarok to iTunes, rythmbox or any other iTunes lookalike was euhm :-k  shocking difficult, don't ask me why.

---

### Post by XDevHald on 2006-08-07
This seems interesting, I'm working on the dev of it right now to get it imported onto windows XP pro and will see how it burns up. I've got dapper 6.06 on the other end, so it shouldn't be a big deal to do a little running around in the flames ;)

Wish me luck and hope winblows doesn't throw a laughing gas on me hehehe.

**EDIT: **This address does not exist: 
svn co svn://anonsvn.kde.org/home/kde/trunk/kdesupport/qt-dbus

---

