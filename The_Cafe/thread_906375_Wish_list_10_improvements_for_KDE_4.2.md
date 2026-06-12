---
title: "Wish list: 10 improvements for KDE 4.2"
date: 2008-08-31
forum: The Cafe
---

### Post by sharks on 2008-08-31
Wish list: 10 improvements for KDE 4.2
[http://www.linux.com/feature/146323](http://www.linux.com/feature/146323)

---

### Post by regomodo on 2008-08-31
#

---

### Post by ssam on 2008-08-31
i have been having timeouts loading pages on linux.com (and sourceforge) over the past few days. is it just me?

---

### Post by mrgnash on 2008-08-31
After trying out KDE 4.1 today, I'd have to add 'not sucking' to the top of the list.

---

### Post by sharks on 2008-08-31
maybe its just you. i think if you use opendns , you wont have that problem

---

### Post by ssam on 2008-08-31
> **sharks said:**
> maybe its just you. i think if you use opendns , you wont have that problem

using opendns does not seem to give any benefit over my ISP (cached on my router)

```

sam@oberon:~$ dig linux.com

; <<>> DiG 9.4.2-P1 <<>> linux.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21842
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;linux.com.			IN	A

;; ANSWER SECTION:
linux.com.		2968	IN	A	216.34.181.51

;; Query time: 1 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Aug 31 16:47:23 2008
;; MSG SIZE  rcvd: 43

sam@oberon:~$ dig linux.com

; <<>> DiG 9.4.2-P1 <<>> linux.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42602
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;linux.com.			IN	A

;; ANSWER SECTION:
linux.com.		2839	IN	A	216.34.181.51

;; Query time: 37 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sun Aug 31 16:47:41 2008
;; MSG SIZE  rcvd: 43

```

====
if i ssh to Uni, i can access it from there. i have sent a message to my ISP

---

### Post by v8YKxgHe on 2008-08-31
> For example, i cannot move widgets on the panel to where i want despite using the svn version of kde4.

Not entirely true. You have to edit the panel (same as if you're going to resize it, move it etc) and then you can easily move the attached widgets/applet/things. At least in KDE 4.1

---

### Post by Canis familiaris on 2008-08-31
Another Wish: Canonical to treat KDE fairly and make Kubuntu 8.10 a good KDE distro rather than a half hearted attempt for just stopping KDE fans from completing.
Seriously KDE4 looks so nice and integrates so well that if incorporated well makes a great distro. Look at OpenSUSE 11 KDE4 for instance.
I just wish Kubuntu 8.10 is a nice KDE 4 distro.

---

### Post by regomodo on 2008-08-31
#

---

### Post by Trail on 2008-09-01
My thoughts on the article:

Easier theme installation.
Easy enough for me, and I don't care.

Automatically pause desktop effects while 3-D or full-screen apps run.
Also don't care. But there's a quick workaround I would guess, the turn compositing on/off plasmoid.

More Plasmoids in the online installer.
Had plenty when I last looked.

Include an RSS newsreader Plasmoid by default
I don't use RSS, I don't care, but I have spotted some such plasmoids online/repos.

Grid for organizing Plasmoids.
Wouldn't hurt.

List applications in the kickoff menu by name.
Don't care. I use `favourites' anyway, or `search' whenever something I rarely use is not there.

Customize favorite applications list.
This one I *do* want fixed. Nothing major, but kinda irritating.

Separate wallpapers for each virtual desktop.
Don't care, never use it.

Hiding and autohiding the panel.
This is one of the most irritating things in the computing world. PLEASE don't use autohiding when I am around. It's annoying as heck. Sadly, they've fixed this recently from what I head on planetkde. Pity :(

Make KDE faster.
Appart from the nVidia driver bug, KDE is fast for me. Which is a definite improvement since the early 4.0 betas, where it was kinda unusable. Now it's fast and not distracting. The only thing I'd like improved is kickoff's launch time when you click it. (It was annoying enough to make me switch to lancelot (out of curiocity as well) - lancelot is pretty good).

One more thing I'd like changed is the behavior of the textboxes in Konqueror; as I am typing this on `Quick Reply' here on UF this is in effect. The issue that I'm having is that when I try to mark with the mouse a region of text that spans through lines above the currect lines, instead of scrolling the textbox it bugs out and stays stationary. Annoying.

Also KNetworkManager sometimes does not automatically activate the default connection after booting, but I don't know if this is a KDE or a OpenSUSE issue.

---

### Post by regomodo on 2008-09-01
#

---

### Post by danbuter on 2008-09-01
I have a hard time believing this article was written has any relevance, considering it's author says that "It's the best desktop I've ever used". Like most Linux reviewers, he probably installed it, ran it for 10 minutes, and then wrote his review.
My wishlist:
1. Fix bugs!!!! This would take months just to make KDE4 stable.
2. Delete Dolphin.
3. Kill Plasma.
4. Fix bugs.
5. Stop hiding all the functions.
6. Stop trying to clone Vista, it's a bad idea.
7. Themes would be nice (I agree with this).
8. Fix bugs.
9. Get some actual important programs ported to QT4.
10. Fix bugs.

---

### Post by Trail on 2008-09-01
> **danbuter said:**
> 1. Fix bugs!!!! This would take months just to make KDE4 stable.

It's pretty stable for me. The bugs are mostly minor and aesthetic.

2. Delete Dolphin.

No way.


3. Kill Plasma.

Nope.

5. Stop hiding all the functions.

Hiding? More like, configurations are not implemented yet because developers are busy.


6. Stop trying to clone Vista, it's a bad idea.

Erm, not really. And also I've seen some pretty cool innovations. Folderview ftw, btw.

9. Get some actual important programs ported to QT4.

Like? I don't miss many programs (except Kdevelop/amarok/kmail which are underway)


Have *you* ran it for more than 10 minutes? Which distribution?

Anyway, what I actually wanted to post is that I included the latest unstable version a while ago. They seem to have put a fading animation while switching regular tabs in a window. Which annoyed me, because I usually keep it as fast as possible, but I thought what the heck, I'll use compositing for a while. And kickoff actually launches fast now!

---

### Post by mips on 2008-09-01
> **regomodo said:**
> 
What i do like is the replacement of default kde3 apps. Okular is massively superior to kpdf although a terrible .chm viewer. Dolphin is considerably easier to use than konqueror. Only a few weeks ago i would have thought that doing this was heresy but it works.


Rome was not built in a day, these things take time. The pace will however rapidly increase as many devs are busy rewriting their apps for kde/qt4, i'm already running some svn versions in Arch.

---

### Post by mips on 2008-09-01
> **Trail said:**
> 
One more thing I'd like changed is the behavior of the textboxes in Konqueror; as I am typing this on `Quick Reply' here on UF this is in effect. The issue that I'm having is that when I try to mark with the mouse a region of text that spans through lines above the currect lines, instead of scrolling the textbox it bugs out and stays stationary. Annoying.

Have to agree.

---

### Post by Nicolae on 2008-09-01
> **danbuter said:**
> I have a hard time believing this article was written has any relevance, considering it's author says that "It's the best desktop I've ever used". Like most Linux reviewers, he probably installed it, ran it for 10 minutes, and then wrote his review.
My wishlist:
1. Fix bugs!!!! This would take months just to make KDE4 stable.
4. Fix bugs.
8. Fix bugs.
10. Fix bugs.

Uh, I've been running KDE 4.1 since RC 1, which is, what, a month and a half now, and it's nowhere near _that_ buggy. It's certainly not bug-free, but there aren't any show-stopping instabilities, just minor glitches. Like the new device notifier randomly "losing" the name column so it's just an empty box with eject icons

> 2. Delete Dolphin.
3. Kill Plasma.

I'd have agreed with you if we were talking about Dolphin in KDE3, or even 4.0, but it's come a long way and it's certainly a viable replacement for konq now that it has _tabs_ and can show more than 3 columns. 
I'm kind of iffy on plasma, but I don't use any desktop widgets. The panel is certainly one of the more glitchy components of KDE4; systray icons not showing properly (I.E, kmix "stacking" on top of an image of the keyboard switcher, presumably because the systray applet isn't updating the images properly), but it's not horrible by any stretch of the imagination.

> 5. Stop hiding all the functions.

As already said, that's more an issue of it still being in development. I mean, there's still no admin mode in systemsettings, even in intrepid A4 :/. Fairly valid point here, I suppose.

> 6. Stop trying to clone Vista, it's a bad idea.

I'm inclined to agree here, the default is a bit Vista-like.

> 7. Themes would be nice (I agree with this).

Agreed here too, even if I probably won't use them as I'm quite happy with the ozone decorations+Obsidian coast or whatever color scheme, the latter of which I stole for my windows installs. 

> 9. Get some actual important programs ported to QT4.


Definitely agree here, though as said work in this area is continuing. 

Overall, though, I've been happy with KDE4. On the desktop. My laptop, though, not so much. My main outstanding issues with it are:
1. Nvidia sucks
2. if I hit the power button on my laptop it doesn't pull up the shutdown menu, which is more of a dbus/acpi issue than KDE4 itself.
3. The battery monitor app is crap, but apparently guidance-power-manager is back and working properly under KDE4 in intrepid.
4. Really, **** nVidia. with any kind of compositing wm running xorg idles at 10-15% CPU even with the latest beta drivers. It's ridiculous, but that's not exclusive to KDE4 so. 

I'm also looking forward to improvements in the KDE-PIM module that will (hopefully) come with 4.2, but I think at this point KDE4 is a viable replacement for KDE3 for most people.

---

### Post by Trail on 2008-09-02
>  Automatically pause desktop effects while 3-D or full-screen apps run.

There's some work on it.

From 31/8 KDE Commit-Digest:
> 
Lubo&#353; Lu&#328;ák committed changes in /trunk/KDE/kdebase/workspace/kwin: 
   Support for unredirecting fullscreen windows, i.e. games etc. can paint directly and not be slowed down by going through compositing.

Turned on and no UI option in the naive hope that it won't cause any real problems.
Maybe effects doing window previews should get API to suspend unredirect though.


---

### Post by grotto on 2008-09-02
Some of those proposed improvements are being worked on. [4.2 Feature Plan]("http://techbase.kde.org/Schedules/KDE4/4.2 Feature Plan")

---

### Post by GeneralZod on 2008-09-02
> **Nicolae said:**
> 
4. Really, **** nVidia. with any kind of compositing wm running xorg idles at 10-15% CPU even with the latest beta drivers. It's ridiculous, but that's not exclusive to KDE4 so.

To be fair, nVidia did actually spring into action and make a good attempt at fixing these issues, which I find interesting as KDE4 users are probably a niche-within-a-niche at the moment.

[http://www.nvnews.net/vbulletin/showthread.php?t=118602](http://www.nvnews.net/vbulletin/showthread.php?t=118602)

---

### Post by Trail on 2008-09-02
Well, not exactly "spring into action", considering the time they've taken so far :)

I was using the `nv' driver for quite a while in one of my laptops (responsible for p2p mostly).

---

