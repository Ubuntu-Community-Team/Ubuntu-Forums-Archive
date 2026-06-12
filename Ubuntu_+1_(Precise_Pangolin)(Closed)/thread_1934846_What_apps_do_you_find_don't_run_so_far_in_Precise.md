---
title: "What apps do you find don't run so far in Precise?"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mcellius on 2012-03-03
I thought it would be worth keeping a list of apps that were working fine in Oneiric and which so far don't run - at least for you - in Precise.  (If someone has started such a thread elsewhere, I apologize, and please point me to it.  Thanks!)

So far, I've found the following:

**Tanglet** (a Boggle-like game)

**Syspeek** (a system monitor indicator that displays CPU usage, memory usage, swap usage, disk usage and network traffic)
[B]
Touchpad Indicator[/B] (a system indicator that allows one to toggle the touchpad on or off)

---

### Post by jbicha on 2012-03-03
Could you go ahead and report bugs about these packages also? For instance:

```
ubuntu-bug tanglet
```

Or even better, use the built-in apport bug reporter to report a crash.

---

### Post by Elfy on 2012-03-03
and then post the bug report number so others can 'me too' them instead of adding duplicates :)

---

### Post by prusswan on 2012-03-03
gedit3 embedded terminal has a broken grey on white color theme. Doesn't seem to be following the rest of the system theme at all

---

### Post by AlanR8 on 2012-03-03
I find no problems, everything just seems to........work. I get some error messages but do you know, this is BETA software so what do you expect?

---

### Post by mcellius on 2012-03-03
Yes, I'll report these bugs.  I didn't know if it should be reported as other bugs or to whoever developed Tanglet.  But there were no crashes - these apps either just don't work or don't work properly (so apport doesn't work, AFAIK).  I don't know that it's a bug in Precise or not.

I don't know how to report that a package won't install, however: apport doesn't allow me to report such failure as a bug, since it can't find the program.

---

### Post by mc4man on 2012-03-04
> **mcellius said:**
> Yes, I'll report these bugs.  I didn't know if it should be reported as other bugs or to whoever developed Tanglet. 
installed tanglet - seemed to work fine, what was the issue? (played only one game..

---

### Post by ikt on 2012-03-04
> **AlanR8 said:**
> this is BETA software so what do you expect?

This is beta of an LTS, so I expect less bugs than a non-LTS release.

---

### Post by 23dornot23d on 2012-03-04
Cinepaint will not run in Precise .....

Yet you can force it and it runs fine ..... also Gnome4dfract is another one .....

( Why when Python 2.6 can work alongside Python 2.7 )

The

Dependancy ..... < Python 2.7 is required ..... yet ....

The case is satisfied when both are installed ...... question is why cant it check for this.

---

### Post by surfer on 2012-03-04
condor. [bug report]("https://bugs.launchpad.net/ubuntu/+source/condor/+bug/931517").

---

### Post by mcellius on 2012-03-04
> installed tanglet - seemed to work fine, what was the issue? (played only one game.For me, Tanglet appeared to install just fine, but play was not correct.  In the Strikeout version, it was not possible to make wrong guesses, so there was no "three strikes and you're out."  This allows for high scores, but was like shooting fish in a barrel.

It does work fine for me in Oneiric.

---

### Post by mcellius on 2012-03-05
> Originally Posted by **AlanR8** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11736627#post11736627") 				
 				*this is BETA software so what do you expect?*
 			 		 	 	 This is beta of an LTS, so I expect less bugs than a non-LTS release.

I've actually found it quite stable and good, and it gets better with each update, it seems.  Yeah, it has bugs, but they are getting fixed, so the actual LTS release should be very good.

That's why I started this thread, though: I wanted a place to post about programs that wouldn't run, but yet weren't necessarily bugs.

---

### Post by PaulW2U on 2012-03-05
One program I'm having problems with is cream, the add-on for gvim.

Ok, so cream is not really a program but a set of scripts that give gvim a more conventional look and feel. I find that cream runs perfectly well in all versions of Kubuntu that I have available and Precise's Gnome Shell but under Unity it's so slow loading and switching between files that it's not really worth bothering with.

As an aside, the global menu for cream is not static in as much as the menu items move around. At the moment the 'File' menu is in fourth position, it should be first and as I check what I'm typing it's decided to move to the first position in the global menu where it should be. ](*,)

May be I should go direct to the developer to see if he is aware of this problem with Ubuntu's Unity as previous cream bug reports have never been acknowledged.

Anyone else use cream?

---

### Post by mcellius on 2012-03-05
I'll file this one as a bug, too, although I'm not sure it qualifies.

I downloaded the ambiance-colors and radiance-colors themes.  When I switch to one of them (e.g. ambiance-green, but any of them do this) in Ubuntu Tweak, in the "Gtk theme" option, or in MyUnity under "Themes," text in some places becomes too light to very readable.   (E.g. in the Themes page in Ubuntu Tweak; the text becomes nearly unreadable.)

I don't know if this is a problem in 12.04 or in the themes themselves.

---

### Post by 23dornot23d on 2012-03-06
Synfigstudio crashes too on my system ....

```

root@keith-Aspire-7730ZG:/home/keith2/Downloads# synfigstudio

   synfig studio -- starting up application...

synfig(10716) [05:28:39 PM] info: Created directory "/root/.synfig"
synfig(10716) [05:28:39 PM] info: Loading modules from /opt/synfig/etc/synfig_modules.cfg

** WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed
synfig(10716) [05:28:40 PM] info: Created directory "/root/.synfig/tmp"

GLib-GObject-CRITICAL **: Object class gtkmm__CustomObject_N6studio15ValueBase_EntryE doesn't implement property 'editing-canceled' from interface 'GtkCellEditable'
GLib (gthread-posix.c): Unexpected error from C library during 'Invalid argument': pthread_cond_timedwait.  Aborting.
Aborted (core dumped)


```

just realised was root there

should have shown as normal user .....

> 
keith@keith-Aspire-7730ZG:~$ synfigstudio

   synfig studio -- starting up application...

synfig(5436) [06:43:32 AM] info: Created directory "/home/keith/.synfig"
synfig(5436) [06:43:32 AM] info: Loading modules from /opt/synfig/etc/synfig_modules.cfg
synfig(5436) [06:43:32 AM] info: Created directory "/home/keith/.synfig/tmp"

GLib-GObject-CRITICAL **: Object class gtkmm__CustomObject_N6studio15ValueBase_EntryE doesn't implement property 'editing-canceled' from interface 'GtkCellEditable'
GLib (gthread-posix.c): Unexpected error from C library during 'Invalid argument': pthread_cond_timedwait.  Aborting.
Aborted (core dumped)
keith@keith-Aspire-7730ZG:~$ 



---

### Post by jbicha on 2012-03-06
mcellius, that's a problem with those themes; they need to be updated for GTK 3.3/3.4.

---

### Post by mcellius on 2012-03-09
The touchpad-indicator bug has been fixed!  I received notification yesterday and the indicator is now available.

---

### Post by tekoholix on 2012-03-09
I can't seem, with Kubuntu 12.04, to get pulseaudio configured to pass audio over network.

Of course, I had not attempted this under the last couple of versions, either, so I can't say that it worked then, or that the instructions didn't simply become obsolete.

As well, none of the x2go stuff works any better than barely useable.  But, of course, that's likely to be the fault of x2go development not having been started for PP, as yet (at least as far as I've been able to find).

---

### Post by viperdvman on 2012-03-09
As neat of a concept as it is, changing the dash color in Unity seems to yield some odd-looking results. I don't really like the new color changer for one. All it gives you is the color diagram, opacity diagram, and a color hex code. Some of us prefer the RGB values. 

That aside, when I do change the color, it changes the color of both the dash and the launcher, which is fine. But what's worse is that the _launcher opacity functions_ have **almost no effect** on the colored launcher. That does sort of put off people who use GTK and Window themes (myself included) and are unable to match their Unity launchers accordingly.

The only other problem I've had (mind you, I'm running from a LiveUSB session), is that I can't get Synaptic to run after I've installed it.

Other than that, running the straight beta release, from LiveUSB, with no updates, I've had absolutely no problems running 12.04 Beta thus far. I'm having a better time running Precise beta on both my computers than I did running the Oneric beta. Hope some of the issues get fixed and features polished before the stable release.

---

