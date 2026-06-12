---
title: "plz..has ANYBODY tried Maemo??"
date: 2010-03-06
forum: The Cafe
---

### Post by rahilm on 2010-03-06
I know  there are many phones with android out there, since it is a google product. The closest competitor is Nokia's Maemo 5. So has anybody tried it?? Because I trust Nokia more than any company in the world, i would like to know how maemo actually is...Also, not a single memo device has been launched in my country and also they are pretty much expensive. 

I currently own an N70 for 3 years by now. So I am thinking of switching to an elegant device. 
(The iphone does not qualify as an elegant device in india). Almost everywhere i search for a comparison of Android and Maemo, i end up receiving "both are good".

From what I have read, they both are entirely different. Since android is google product, it will be much more popular. I read that photoshop has been released in android(??). Maemo is more close to our "regular debian" than android and android sdk is much more messy and different.

So If anybody has used both, then plz give a comparison wrt software and games availability (i don't care about speed, n70 is probably the slowest mobile you'll encounter). Else, a description of maemo would be helpful...

---

### Post by earthpigg on 2010-03-06
i haven't used either, but i have my heart set on maemo.

here's why:

[Maemo]("http://wiki.maemo.org/Root_access") -
> rootsh is available in Extras, and can be installed from the Application manager if you have Extras enabled.

Then, from the shell, run sudo gainroot (or root for short). This will give you a root shell. 

[Android]("http://android-dls.com/wiki/index.php?title=Root_For_RC30") -
> A rollback method for RC30 and RC33 users who want root. This method is a full device flash that will roll you back to RC29 which still has the root bug. After doing this you can then follow the instructions on Rooting Android and then Keeping Root to get yourself up to RC33 modified version that lets you keep root. [...insert detailed and painful jailbreak-like process of gaining root]

In android, you must exploit vulnerabilities and bugs - an generally be made to feel like a bad guy - to gain root access.

In maemo, it's totally allowed and the process is made easy.

that may not matter directly for some, but to me it indicates an atmosphere of respect for the customer. in terms of user freedom and user empowerment, an Android may as well be iPhone.

it also means you can install anything you wish, without relying on a paid app store... if i/you start installing things randomly from the debian repos, we will quickly discover that many don't work well on the small screen. however, if i/you/we pick the apps carefully we would be free to discover things that work well on the small screen. i bet, for example, a terminal based web browser and email client would run very beautifully on an n900, and faster than anything from any app store. a few custom key bindings would make it a truly elegant experience.

---

### Post by rahilm on 2010-03-06
hey, mplayer is available for maemo.
[http://maemo.org/downloads/product/Maemo5/mplayer/](http://maemo.org/downloads/product/Maemo5/mplayer/)
maemo 1 , android 0

---

### Post by rahilm on 2010-03-07
but android being a google product will eventually overtake maemo in terms of popularity (it already has). Also nokia OS are used majorly on nokia phones

---

### Post by ssam on 2010-03-07
pretty much any linux app can be recompiled for arm and run on maemo. its a fairly standard distro. (there are a few closed source bits)

android uses the linux kernel, though modified to the point where hardware drivers for android kernel can be used in a normal linux kernel. everything on top of the kernel is completely custom. you can't run normal linux apps, only sandboxed java apps.

there is also the openmoko phone, which is the most linux like and open source. you can even run debian or gentoo on it. the current hardware is more basic than most smart phones (no camera, 3g and lower spec CPU).

---

### Post by ssj6akshat on 2010-03-07
Hey.Did you forgot Moblin and Maemo have merged.Wait some more.

---

### Post by gnomeuser on 2010-03-07
I will tell you tomorrow when my N900 arrives, but I have used Maemo on the N810 for a long time and the most concerning fact is Nokias lack of updates to the platform and premature EOL of the project. This is the old pre version 5 Maemo, so I doubt the experience is all to comparable and even at that MeeGo 1.0 will switch a lot of things around including the choice to go with QT over Clutter and GTK+.

But stay tuned and check my blog of a review.

---

### Post by azangru on 2010-03-07
> **gnomeuser said:**
> I will tell you tomorrow when my N900 arrives.

Just wondering: did you order your N900 before or after learning that Maemo will soon be no more? Were you at all worried whether emergence of Meego could make N900 obsolete?

---

### Post by gnomeuser on 2010-03-07
> **azangru said:**
> Just wondering: did you order your N900 before or after learning that Maemo will soon be no more? Were you at all worried whether emergence of Meego could make N900 obsolete?

I ordered it after the MeeGo announcement. 

Regardless I was slightly concerned after my credit card was charged, reading one of the developers blog were Nokia wouldn't commit to supporting the N900 with MeeGo. However they came out yesterday announcing that MeeGo 1.0 will be targeted at the N900 and Intel ATOM platforms.

What I was most worried about was really Nokia's part in this, I own the N810 and it was so rarely updated and still contains serious bugs. They have a shitty track record maintaining and updating their Linux products. I was afraid that they would do the same with th N900. Now that we have assurances that MeeGo, being a larger project, will be supported and the emergence of the Mer project I am less worried about this aspect.

I am eagerly awaiting the arrival, sadly it is looking like it won't arrive before Monday around dinner time at the earliest.

---

### Post by azangru on 2010-03-07
> **gnomeuser said:**
> However they came out yesterday announcing that MeeGo 1.0 will be targeted at the N900 and Intel ATOM platforms.

I've seen this announcement too, specifically that MeeGo repositories are going to open up for N900 by the end of this month or something like that, but I couldn't figure how it's supposed to work. Will Maemo update itself quietly to MeeGo, or will it just use apps designed for MeeGo.

I wish they don't abandon the N900. It's an amazing device, but it pitifully lacks some basic apps, and its software needs some polishing here and there.

---

### Post by ve4cib on 2010-03-07
I've never used Android (other than briefly tinkering with an older version of the SDK), but I just got my N900 in the mail on Friday, and have been playing around with it since then.

Maemo is pretty nice.  It's been fairly intuitive to install/remove/update software, thought finding the MAC address so I could get it onto my LAN at home was more exciting.  My first instict was Terminal > $ ifconfig -a.  Unfortunately ifconfig (and indeed the entire set of standard GNU utils) isn't installed by default.  There's a package to get them though.  Anyway, the MAC address was also found by going to Applications > About.  So easy enough.

Overall I'm liking the N900.  The software selection is good -- nothing spectacular, and there's a lot of buggy/in-development software still -- but you can usually find something that will do what you need.

I have yet to use the N900 as an actual phone though.  I plan on signing up for a plan sometime next week and getting the SIM card.  I bought the device primarily as a PMP/pocket-computer, not as a phone.  Apparently it can't handle MMS (but does to SMS), but I doubt that will be an issue for me

This is the first I've heard about MeeGo supplanting Maemo on the N900.  That'll be interesting, but since MeeGo has been around since 1999 and has a fairly active community I'm expecting some good things to come from the arrangement.

---

### Post by rahilm on 2010-03-08
> **azangru said:**
> 
I wish they don't abandon the N900. It's an amazing device, but it pitifully lacks some basic apps, and its software needs some polishing here and there.

that is obviously true!!!! it is, after all, a LINUX device

---

### Post by gnomeuser on 2010-03-08
> **azangru said:**
> I've seen this announcement too, specifically that MeeGo repositories are going to open up for N900 by the end of this month or something like that, but I couldn't figure how it's supposed to work. Will Maemo update itself quietly to MeeGo, or will it just use apps designed for MeeGo.

I wish they don't abandon the N900. It's an amazing device, but it pitifully lacks some basic apps, and its software needs some polishing here and there.

I think a full on upgrade over the air is unlikely. You are switching the underlying OS from debian to a Fedora/openSUSE/homegrown system including a a switch from the ancient dpkg to a modern rpm with packagekit packaging solution (much yay, dpkg needs to die). This alone will make the update really hard to perform flawlessly. Another big upgrade is the move from gtk and clutter to qt (why oh why) which is likely to involve some rather nasty data conversion problems.

I think what is likely is that Maemo 5 will continue to get bugfixes till such a time as MeeGo is in a suitable state. Then it will be offered as an experimental upgrade which requires flashing the device.

This likely also means that feature upgrades for Maemo 5 won't be issued. The focus is MeeGo and you shouldn't expect to see major improvements be rolled out. I suspect Maemo 5 will handpick fixes from the MeeGo branch and port those, perhaps we will see upgrades to things such as Tracker since they already poured a lot of development into the much superior 0.7/0.8 branch which is nearly ready. Furthermore the developers of said software are very interested in moving all tracker deployments to the new code as it is much better in every way.

---

### Post by gnomeuser on 2010-03-11
I've played with my N900 for a bit now and wrote [a little review](http://davidnielsen.wordpress.com/2010/03/11/a-first-meeting-review-of-the-nokia-n900/) on my blog.

---

### Post by earthpigg on 2010-03-11
interesting review.

have you tried supernerd things, like using a conventional repo?

---

