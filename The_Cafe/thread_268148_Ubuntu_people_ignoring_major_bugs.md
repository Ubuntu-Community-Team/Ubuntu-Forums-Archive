---
title: "Ubuntu people ignoring major bugs"
date: 2006-09-29
forum: The Cafe
---

### Post by dv_ on 2006-09-29
I mean, really. The cups IPP bug - making printing via IPP impossible - is known for MONTHS and nothing happens. The totem-xine bug is known and nothing happens. I see these bugs as rather major, still they get ignored. Isnt it in Ubuntu's best interest to avoid such mistakes and outshine MS in this regard? (They are known for not fixing major bugs). Or do all bugs go to edgy nowadays?

---

### Post by NoTiG on 2006-09-29
I feel sorry for the devs. theres literally thousands of bugs and new ones submitted every minute. I cant wait for the day when i know enough to actually helps some.

---

### Post by Reshin on 2006-09-29
I don't know what to say to this. Be it major or minor bug/hole, MS is always gonna get it, even if they patch it at some point. On linux on the other hand you got no right to complain about even major holes left long unpatched and still treat it equal or better to commercial OSs. Just shut up or start learning to code. Forget and forgive

---

### Post by dv_ on 2006-09-29
Ok, maybe I am unfair to the devs, they must be showered with bugs. But a little feedback would be nice. There are several threads about the IPP issue for example, someone saying "the devs know about this bug and are addressing it" would be very nice. Without this feedback it looks as if they ignore it.

---

### Post by PriceChild on 2006-09-29
It will be fixed when its fixed... general rule of thumb.

Please remember that no-one has ANY obligation to fix anything in ubuntu.

Its a wonder that we are where we are :)

When someone figures out what's wrong, works out how to fix it, and more importantly, HAS THE TIME, they will fix it. Maybe you could help :)

Pricey

> Ok, maybe I am unfair to the devs, they must be showered with bugs. But a little feedback would be nice. There are several threads about the IPP issue for example, someone saying "the devs know about this bug and are addressing it" would be very nice. Without this feedback it looks as if they ignore it.I'd rather they devoted their time to bugs and improvements than changing their procedures.

---

### Post by dv_ on 2006-09-29
Well it seems that it is fixed now.

But: [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/55828](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/55828) according to this, the fix will not be included in dapper.... ever. Am I wrong?

---

### Post by PatrickMay16 on 2006-09-29
> On linux on the other hand you got no right to complain about even major holes left long unpatched and still treat it equal or better to commercial OSs. Just shut up or start learning to code. Forget and forgive

Yeah! How dare we complain when software updates break the X server and dump us into a command line, or mess up the kernel and leave us with an unbootable system. Totally unreasonable of us.

---

### Post by weatherman on 2006-09-29
> **dv_ said:**
> I mean, really. The cups IPP bug - making printing via IPP impossible - is known for MONTHS and nothing happens. The totem-xine bug is known and nothing happens. I see these bugs as rather major, still they get ignored. Isnt it in Ubuntu's best interest to avoid such mistakes and outshine MS in this regard? (They are known for not fixing major bugs). Or do all bugs go to edgy nowadays?
Sometimes it's frustrating, I guess it's something you get used to. One day bugs will be fixed, bugfixes should enter dapper as well.

---

### Post by DoctorMO on 2006-09-29
> Yeah! How dare we complain when software updates break the X server and dump us into a command line, or mess up the kernel and leave us with an unbootable system. Totally unreasonable of us.

I completly agree! We're just not thinking about this in the right way. this isn't something which falls under the terms of selling a product. if you want paid support then you know what you must do. if you don't want the responsibility to fix your own computer with a little help from your friends then please just pay for the support where you can just throw blame arround until someone fixes it for you.

Volenteers do not deserve to get treat like employees.

P.S spelling errors found in this post.

---

### Post by Paulus on 2006-09-29
omg he was being sarcastic!!

don't the ubuntu dev's get paid?  I thought they did for some reason

---

### Post by maniacmusician on 2006-09-29
> **DoctorMO said:**
> if you want paid support then you know what you must do

get tech support from canonical? 


buy [Impi Linux]("http://www.impilinux.co.za/")?

---

### Post by givré on 2006-09-29
> **dv_ said:**
> The totem-xine bug is known and nothing happens.
It is fix since a long time :
> totem (1.4.3-0ubuntu1) dapper-updates; urgency=low

  * New upstream release:
    - Bugs fixed:
      - "[dapper][totem-xine] when I try to change connection speed it
         crashes" (Malone: #41099)
    - 1.4.3:
      - Add AC3 and Monkey's audio to the known filetypes
      - [B]Draw the logo ourselves, so we don't crash on startup if the logo is 
        too big for the X video buffer (xine-lib) (Malone: #35229)[/B]
      - Fix a leak each time the logo was set (GStreamer)
    - 1.4.2:
      - Make showing/hiding the sidebar not resize the video or the window
      - Fix saving non-relative m3u playlists, and parsing relative PLS 
        playlists
      - Fix DVD playback when started from gnome-volume-manager
      - Pop down language and subtitle menus to avoid hangs when the language 
        or subtitle changes while the menu is open
      - Add Impulse Tracker and MOD files to the list of supported types
      - Add audio/vnd.rn-realaudio as a supported playlist format
      - Fix a new installation of Totem not using visualisation (GStreamer)
      - Fix a possible crash when the buffering is set to non-default values 
        (GStreamer)
  * debian/control.in:
    - Bumped Build-Depends according to configure.in.
  * debian/patches/07_default_visual_effect.dpatch,
    debian/patches/08_fix_overflow_when_calculating_ratio.dpatch:
    - dropped, included in release.

 -- Daniel Holbach <daniel.holbach@ubuntu.com>  Tue, 18 Jul 2006 11:59:13 +0200

---

### Post by dv_ on 2006-09-30
Its not. Installing totem-xine forces ubuntu-desktop to deinstall along with totem-gstreamer. totem-gstreamer deinstall is ok, but not ubuntu-desktop! Now, every time I want to upgrade Ubuntu, apt wants to uninstall totem-xine!

---

### Post by givré on 2006-09-30
> **dv_ said:**
> Its not. Installing totem-xine forces ubuntu-desktop to deinstall along with totem-gstreamer. totem-gstreamer deinstall is ok, but not ubuntu-desktop! Now, every time I want to upgrade Ubuntu, apt wants to uninstall totem-xine!
That's definitly not a bug.
ubuntu-desktop is a metapackage that aim is to install default ubuntu apps. So of course if you don't want the default apps, you'll have to remove it.
But i don't know who it could bother you when you want to upgrade. Only dist-upgrading have the power to install *-desktop metapackage.

---

### Post by bruce89 on 2006-09-30
> **givré said:**
> That's definitly not a bug.
ubuntu-desktop is a metapackage that aim is to install default ubuntu apps. So of course if you don't want the default apps, you'll have to remove it.
But i don't know who it could bother you when you want to upgrade. Only dist-upgrading have the power to install *-desktop metapackage.

With Breezy, *ubuntu-desktop* depended on either *totem-gstreamer* or *totem-xine*.  Is this no longer the case?  If so, this is a bug in *ubuntu-meta*, not *totem-xine*.

> **PriceChild said:**
> Please remember that no-one has ANY obligation to fix anything in ubuntu.

That's not quite true.  The only person with an obligation to fix a bug you want fixed is you.  From the [Mozilla Bugzilla]("https://bugzilla.mozilla.org/") [Etiquette]("https://bugzilla.mozilla.org/page.cgi?id=etiquette.html"):
> 1. Commenting

This is the most important section.
  [...]
  2. No obligation. "Open Source" is not the same as "the developers must do my bidding." **The only person who has any obligation to fix the bugs you want fixed is you.** Never act as if you expect someone to fix a bug by a particular date or release. This is merely obnoxious, and is likely to get the bug ignored.
  [...]
(Emphasis added).

---

### Post by dv_ on 2006-09-30
Pressing for bugfixes is necessary sometimes. Also, bug reports MUST be possible. It is not acceptable that only developers are allowed to report bugs, i.e. "its broken? then fix it yourself!" If someone releases a broken app, then there is nothing wrong with reporting encountered bugs (in detail). It is wrong of course to bug the devs every minute. But limiting the persons with the right to report something to developers is just plain ridiculous. So for getting a media player fixed one has to become an expert in video playback?

---

### Post by bruce89 on 2006-09-30
> **dv_ said:**
> Pressing for bugfixes is necessary sometimes. Also, bug reports MUST be possible. It is not acceptable that only developers are allowed to report bugs, i.e. "its broken? then fix it yourself!" If someone releases a broken app, then there is nothing wrong with reporting encountered bugs (in detail). It is wrong of course to bug the devs every minute. But limiting the persons with the right to report something to developers is just plain ridiculous. So for getting a media player fixed one has to become an expert in video playback?

No-one is suggesting denying non-devs from filing bug reports, not sure where you got that idea from.  Fairly recently they stopped non-members of the BugTeam from changing the severity of any bug after people putting their own bugs up to severe all the time.

---

### Post by PriceChild on 2006-09-30
> That's not quite true.  The only person with an obligation to fix a bug you want fixed is you.  From the [Mozilla Bugzilla]("https://bugzilla.mozilla.org/") [Etiquette]("https://bugzilla.mozilla.org/page.cgi?id=etiquette.html")

He he :)

That's brightened up my day :)

---

### Post by givré on 2006-09-30
> 1. Commenting

This is the most important section.
[...]
2. No obligation. "Open Source" is not the same as "the developers must do my bidding." The only person who has any obligation to fix the bugs you want fixed is you. Never act as if you expect someone to fix a bug by a particular date or release. This is merely obnoxious, and is likely to get the bug ignored.
[...]
I'll record that one :D

---

### Post by bruce89 on 2006-09-30
> 1. Commenting

This is the most important section.
[...]
2. **No obligation. "Open Source" is not the same as "the developers must do my bidding." The only person who has any obligation to fix the bugs you want fixed is you.** Never act as if you expect someone to fix a bug by a particular date or release. This is merely obnoxious, and is likely to get the bug ignored.
[...]

It does sound a bit like laziness on the developer's part here though, but the first bit **(bolded)** of it is the important bit.

---

### Post by alecjw on 2006-09-30
> **Reshin said:**
> I don't know what to say to this. Be it major or minor bug/hole, MS is always gonna get it, even if they patch it at some point. On linux on the other hand you got no right to complain about even major holes left long unpatched and still treat it equal or better to commercial OSs. Just shut up or start learning to code. Forget and forgive

I think it's the other way round. With Ubuntu, it's easy to submit a bug. With windoze, you cave to phone technical support, send them an email, faf about with their website etc. Or you can send an "error report", which usually just sends info about which program crashed. Very helpful, and you get to talk to a computer rather than real people.

And in Ubuntu, there's a community where everyone is helpful and kind to each other, somethimes helping the devs, trying to pay back their effort on this great OS. Whereas with windoze, you've given them the £250. That's it. You're done. They can fix anything themselves. You don't care.

---

