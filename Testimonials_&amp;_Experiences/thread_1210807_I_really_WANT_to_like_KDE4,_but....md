---
title: "I really WANT to like KDE4, but..."
date: 2009-07-11
forum: Testimonials &amp; Experiences
---

### Post by decoherence on 2009-07-11
I think Qt4 is great... i'm not a Qt developer, but I think it's a great set of widgets/frameworks.

I think KDE4 has a ton of potential and that we've only just scratched the surface. It's wonderfully configurable, drop-dead gorgeous and, best of all, there is evidence that some ACTUAL THOUGHT went in to making the thing pleasant to use.

But...

Konqueror won't play with my work's webmail system (groupwise)... Safari and Chromium do so I'm not sure why Konqueror chokes. Not only does it choke, it locks up the entire UI. Thinking there might've been something it had to 'work through' I left it and ate dinner. When I got back, it was still good and frozen.... couldn't even Ctrl Alt F1 in to a tty.

Oh, it also did something very strange with the text entry box for the body of an email... like you had to double-click the field before you could edit it. I haven't noticed that behavior anywhere else, so again I think it doesn't play nicely with my webmail.

Also, the plasma workspace dies frequently. Not a huge deal as it just comes back up, but not exactly confidence inspiring.

Just wondering if anyone else has experienced this sort of behavior. Is it expected from KDE4? Or am I just unlucky?

It's Ubuntu 9.04 on a typical netbook (lenovo ideapad), switched over to Kubuntu.

I'll be switching to PekWM + PyPanel for now... I'll miss the niceties but at least it'll be stable. (and snappier feeling but that's not very important to me.)

why not stick with gnome? i dunno. feel like a change, i guess.

looking forward to hearing from other kde4 users (or ex users)

---

### Post by HappyFeet on 2009-07-11
I've tried it and feel it is still not ready for primetime. I was never a big fan of KDE to begin with, but KDE4 still has a ways to go before I would consider using it on a production machine for myself or anyone else.

Yes, it is pretty, but I can make gnome look pretty damn good too. I prefer function over form. I know some people love it, and that's OK. My standards are just very high I guess.

---

### Post by Anzan on 2009-07-12
I much prefer Gtk to Qt.

And KDE4 seems to have lost the KISS that makes Unix-like systems so powerful and stable.

---

### Post by lykwydchykyn on 2009-07-12
My Krystal ball tells me you're going to get a lot of negative comments from this forum...

I've been a KDE user for at least 5 years, and I'll give you my advice:
 - There's no earthly reason you have to use Konqueror or any other KDE app.  I mostly use firefox.  Just because KDE is your DE doesn't mean you cannot pick best-of-breed for apps.
 - A lot of people will tell you Kubuntu isn't the best KDE distro out there.  I personally stick with it because I like debian package management and the Ubuntu release cycle works best for me.  But people say lots of good things about other distros' KDE packages -- e.g. Arch or OpenSuse.
 - the version that comes with Jaunty is still a bit buggy.  I'd recommend adding the Kubuntu ppa repository so you can at least be running 4.2.4.  See here: [http://www.kubuntu.org/news/kde-4.2.4](http://www.kubuntu.org/news/kde-4.2.4)
 - Plasma is sensitive to video cards.  My laptop (intel chip) seems to have a lot more trouble than my work desktop (Nvidia).  It also doesn't seem to be well-insulated from badly written plasmoids, so be careful which ones you use.

Though, frankly, if you can get by with a simple WM and pyPanel, why not?  A DE like KDE or GNOME is orders of magnitude more complex than an arrangement like that, and complexity always brings bugs.  The tradeoff is features, of course; but if you don't need the features...

---

### Post by decoherence on 2009-07-12
Thanks lykwydchykyn; useful advice and very insightful. I stick with Ubuntu for the same reasons.

While I can do fine with a window manager and xterm, I'm always curious about the latest and greatest in usability. KDE4 is brilliant and should be well worth the sophistication it adds to a system. I'll definitely check out those ppas, too. Latest and greatest and all.... short of building from source.

The bug that really depressed me was the full screen lockup... that was using Konqueror plus this wacky Groupwise webmail that was doing some asynchronous javascript thing at the time. If I can avoid that simply by avoiding Konqueror, that'd solve my biggest gripe. Still, I'm of the opinion that a full screen lockup just shouldn't happen. But like you said; all that sophistication can make a computer do funny things! It's a trade-off.

I'm looking forward to when KDE4 runs perfectly on this system (maybe with those ppas?) because it is really, *really* nice.

---

### Post by decoherence on 2009-07-12
Just an update on my KDE4 usage.... I've installed the versions from the PPAs and I'm using Chromium and Firefocks 3.5.

Happy to report that none of the issues in my first post are affecting me now. Thanks again lykwydchykyn!

---

### Post by lykwydchykyn on 2009-07-12
I haven't tried groupwise webmail in konqueror, though I do know konqueror's weakest part is it's javascript engine.  Anything with a lot of AJAX stuff (facebook, igoogle, etc) tends to screw up in konqueror.

Novell's cross-platform GW client works in Ubuntu with a little help from alien, btw.  I've been using it at work for years.

---

### Post by decoherence on 2009-07-13
> **lykwydchykyn said:**
> Novell's cross-platform GW client works in Ubuntu with a little help from alien, btw.  I've been using it at work for years.

me too. gw 8 was a real dog to build for x64. also, i was told it would support the multi-user calendar, which it doesn't. that's a must-have feature at my work, so I use evolution now instead. sure, i have to sigkill it two or three times a day, but at least I can see everything all at once. ;)

if i could just get my admin to set up that new calendar publishing host...

---

### Post by zugu on 2009-07-13
> **decoherence said:**
> Konqueror won't play with my work's webmail system (groupwise)... Safari and Chromium do so I'm not sure why Konqueror chokes. Not only does it choke, it locks up the entire UI.Safari and Chromium use Webkit, a different rendering engine (actually a fork of KHTML, the engine used in Konqueror). The Konqueror devs won't switch to Webkit, although there are more and more reasons to do so (Google, Nokia and Apple working together on Webkit vs a handful of developers coding KHTML). I guess it's the NIH syndrome, part of why I never liked KDE.

> **decoherence said:**
> Also, the plasma workspace dies frequently. Not a huge deal as it just comes back up, but not exactly confidence inspiring.You should probably wait until KDE 4.4 or 4.5.

---

### Post by ThisEndlessFall on 2009-07-13
KDE4 is more of a novelty than a serious DE.

---

### Post by vinutux on 2009-07-13
kde is good for looking not working

---

### Post by lykwydchykyn on 2009-07-13
> **decoherence said:**
> me too. gw 8 was a real dog to build for x64. also, i was told it would support the multi-user calendar, which it doesn't. that's a must-have feature at my work, so I use evolution now instead. sure, i have to sigkill it two or three times a day, but at least I can see everything all at once. ;)

if i could just get my admin to set up that new calendar publishing host...

I gave up building it for 64 bit, that's why I'm still on 32 bit. :-(

> 
Safari and Chromium use Webkit, a different rendering engine (actually a fork of KHTML, the engine used in Konqueror). The Konqueror devs won't switch to Webkit, although there are more and more reasons to do so (Google, Nokia and Apple working together on Webkit vs a handful of developers coding KHTML). I guess it's the NIH syndrome, part of why I never liked KDE.

Yep, that must be the reason there's a webkit backend for Konqueror in development, available in 4.3.

---

### Post by solwic on 2009-07-13
I like KDE, but Firefox doesn't look right in Kubuntu, and I don't know if there's a KDE equivalent of Gnome-Do. I have a lappy, and I hate touch pads.  Gnome-Do lets me use super-space and a few keystrokes to launch any program on my system. 

Haven't tried Kubuntu 9.04 yet.  Might load it up in a VM....

---

### Post by decoherence on 2009-07-13
"KDE4 is more of a novelty than a serious DE."

"kde is good for looking not working "

I've been using KDE4 for the past few days and, now that I'm not using the default Jaunty version, I don't see what it's lacking. You both have such definitive opinions, I'm sure you can give me specifics as to why it's not 'for working' or not a serious DE?

---

### Post by decoherence on 2009-07-13
> **iRun said:**
> Gnome-Do lets me use super-space and a few keystrokes to launch any program on my system. 


I love Gnome-Do as well. KDE4's kick-off application does the same thing once you bind it to a keyboard shortcut.

---

### Post by waspbr on 2009-07-13
IMHO KDE 4 looks good, the splash screen looks great, plasma does a great job on the desktop overall, but for some odd reason I can't help but fell a little claustrophobic in KDE.

I cannot really put my finger on it, but something bothers me, after a day or 2 in KDE I find myself craving some gnome. I have even used xfce for extended periods of time,but always end up going back to gnome for some odd reason.

---

### Post by Sxeptomaniac on 2009-07-13
I've found I generally prefer KDE over GNOME, so that's often what I've used, but I've run into stability issues in the past, so I have used GNOME for long periods, too.  I find myself consistently drawn back to KDE, though.  Something about it just clicks with me.

Konqueror is the weakest link in KDE right now, IMO.  I have never found it to be particularly useful as a web browser, because it feels clunky when compared to other current browsers.  I'm of the opinion that they should just stop bundling it with KDE and leave browser choice up to the user.

I've also hit some issues with certain Plasmoids on my laptop, but it hasn't been too much of a problem.  I think it has a lot of potential to allow users to create an unusually configurable desktop.

I really don't care if others dislike KDE, though.  It's what I prefer, and I have no expectations that they feel similarly.

---

### Post by decoherence on 2009-07-13
In the past I've found Konqueror to be useful mostly as a front-end to KIO slaves. For instance, the easiest and most reliable way I've found to connect to a Windows Mobile phone is to install Synce and access the phone through Konqueror -- even if I'm running GNOME.

---

### Post by lykwydchykyn on 2009-07-13
> **iRun said:**
> I like KDE, but Firefox doesn't look right in Kubuntu, and I don't know if there's a KDE equivalent of Gnome-Do. I have a lappy, and I hate touch pads.  Gnome-Do lets me use super-space and a few keystrokes to launch any program on my system. 


That's what krunner is supposed to do.  It's bound to alt-f2 by default, but you can change that.  Krunner is a pluggable command launcher, it can do all kinds of things from arithmetic to "desktop search" to basic launching.

It gets much more powerful in 4.3

---

### Post by ThisEndlessFall on 2009-07-13
> **decoherence said:**
> "KDE4 is more of a novelty than a serious DE."

"kde is good for looking not working "

I've been using KDE4 for the past few days and, now that I'm not using the default Jaunty version, I don't see what it's lacking. You both have such definitive opinions, I'm sure you can give me specifics as to why it's not 'for working' or not a serious DE?

The main thing is KDE4's lack of stability. It's like an early beta, it should not be used in full release distros. 
Kubuntu always seems to have the worst implementation of KDE4 stability wise, Mandriva always seems to do it so much better.

Other issues include having Konqueror as the default browser. It's very poor & unreliable at best. Kickoff is extremely restrictive and almost feels claustrophobic. Dolphin is just awkward compared to Nautilus. Unreliable WIFI that works flawlessly on GNOME but not on KDE4. Kpackagekit still has some major issues in Kubuntu. Just try and install Java through it and see what happens.

But overall it comes back to stability. KDE4 just doesn't have it.

---

### Post by decoherence on 2009-07-13
> It's like an early beta, it should not be used in full release distros. 

I'll agree that the KDE4 release in Jaunty has problems... that is what prompted this thread. I also wholeheartedly agree that distros jumped on it way too early. However, Kubuntu Jaunty is not indicative of the current state of KDE4, and since upgrading to the PPAs that were previously posted, it has been running great.

As far as having Konqueror as the default browser, well what do you expect? The default browser in GNOME is Epiphany, that doesn't stop people from running Firefox instead.

Kickoff can run as a simple menu system, if you want. It's configurable.

What about Dolphin do you find awkward? I haven't used it much yet. I find Nautilus pretty awkward, though, so maybe I'll find Dolphin unusable? Everything has seemed fairly straight forward so far, though.

And PackageKit has issues, period. Maybe KDE's implementation is especially bad but in any case I will not be touching it in GNOME or KDE for a while. Synaptic works fine in either environment, for now.

So in summary, stability has been fine for me since upgrading the PPA and switching to firefox. I'm easily able to use it as my primary system after making some concessions for bugs. Those concessions were not unreasonable, didn't negatively impact the workflow, and are the same sorts of things that happen in any desktop environment. (ie "Totem refuses to play this video no matter what!" "So use VLC")

I think your comment must've been based on the Kubuntu Jaunty release, which I also found to be unfortunately bad. But things are improving rapidly.

Now, whether or not KDE4.3 should've actually been KDE4.0... maybe, maybe not. The KDE developers did a funny thing in releasing 4.0 while repeatedly telling people to treat it more like a beta, and I've no doubt that this is the cause of much of the pissiness toward KDE4, but the decision DID get KDE4 in to a lot of people's hands. Would it be improving as rapidly if they had done a years-long beta program instead? We can't really say, but something to think about. I consider KDE4 a long term project that is currently in very solid shape. Unfortunately, Kubuntu doesn't reflect that.

---

### Post by Sxeptomaniac on 2009-07-13
If you don't like Kickoff, you don't have to use it at all.  I removed it from Plasma and use Lancelot instead.  It comes preinstalled, but it's just not the default launcher.

Kpackagekit may have potential, but I agree that it is currently not ready for regular use.  It's very difficult to find what I'm looking for if I don't know the name of the package, as the search feature is just bad.  I have Synaptic installed, anyway.

---

### Post by decoherence on 2009-07-13
Just another short update... in a fit of adventurousness (or perhaps masochism) I've upgraded this system to Karmic. I'm a glutton for punishment, I know.

Anyway, the network-manager applet broke for wireless. wicd works fine, though.

Also, this version of Konqueror doesn't choke on my work's webmail, so I think I'll keep using it, just for the experience. Maybe try the webkit back end, too.

Everything else seems good, and the upgrade went without a hitch but now I want to re-install Ubuntu desktop to check out the improvements to gnome! ;) But KDE4 has a new user -- I'm definitely switching back once I've satisfied my curiosity. Yeah, I'm hopeless.

---

### Post by HappyFeet on 2009-07-13
> **decoherence said:**
> The default browser in GNOME is Epiphany, that doesn't stop people from running Firefox instead.


Really? I've used almost every gnome based distro there is, and have yet to see Epiphany as the default browser. Where did you get this information? Actually, I have yet to see any gnome distro with Epiphany installed.

---

### Post by Bigtime_Scrub on 2009-07-14
> **HappyFeet said:**
> Really? I've used almost every gnome based distro there is, and have yet to see Epiphany as the default browser. Where did you get this information? Actually, I have yet to see any gnome distro with Epiphany installed.

Debian Lenny 5.0 has Epiphany and Firefox installed by default. Debian is Gnome based....

Anyway Ubuntu really isn't as good with KDE. The only reason to use it is if you like KDE and you want to stick with apt-get and Debian repositories. I do not like Suse but as a Gnome guy myself, I was very impressed with Mandriva 2009. It uses KDE 4.2 and it is done very very well. It is functional, beautiful, stable, and fast. But that is Mandriva where KDE is put first before Gnome.

---

### Post by lykwydchykyn on 2009-07-14
I've always gotten the impression that Kubuntu tries too hard to be a "pure kde" distro; that is, they want to use everything KDE by default.  I can understand that, there are some voices in the KDE community calling for distros to do less customizing so there can be a "definitive look" for kde (cf - [http://aseigo.blogspot.com/2009/06/building-brand-together.html](http://aseigo.blogspot.com/2009/06/building-brand-together.html)).  

I also have taken note that at least a few members of the Kubuntu team seem to be upstream contributors to KDE, so there's probably more of a "fix it at the source" than "fix it in the mix" going on there (in other words, instead of ripping out an application that isn't very good, keep it and try to get it improved upstream).

Bottom line, the focus of the Kubuntu project seems to me more about packaging KDE for Ubuntu than spinning a distro BASED ON KDE that maximizes user experience.

I mean for contrast, there's my old distro of choice, MEPIS.  MEPIS is also Debian based and KDE based, but totally different from Kubuntu.  Firefox is the default browser, Synaptic is the default package manager, and all the other apps are best-of-breed rather than strictly KDE.  

Each approach has its pros and cons.  Point is, it's just a shame to see users reject KDE in its entirety because one or two apps aren't up to snuff.  Maybe it's the "KDE only" and "GTK only" approach that K/Ubuntu take (respectively) to designing the desktop that makes people think they durstn't mix apps between the two.

---

### Post by solwic on 2009-07-14
> **lykwydchykyn said:**
> Maybe it's the "KDE only" and "GTK only" approach that K/Ubuntu take (respectively) to designing the desktop that makes people think they durstn't mix apps between the two.

Wouldn't surprise me.  Personally, KDE has a couple of apps that are pretty awesome.  Not many, but a couple.  Like ktorrent.  And YaKuake.  

But I can't wait til KDE4 matures in Kubuntu (if it ever does).  I got spoiled with the repositories, and apt-get, and the 'buntu way of doing things, so I won't switch to Mandriva or anything...I'll just hurry up and wait (and pray) for Kubuntu to grow up.  :)

---

### Post by decoherence on 2009-07-14
> **HappyFeet said:**
> Really? I've used almost every gnome based distro there is, and have yet to see Epiphany as the default browser. Where did you get this information? Actually, I have yet to see any gnome distro with Epiphany installed.

I stopped talking about what Ubuntu or whomever is shipping in their release when I installed the PPAs. I'm talking about the default for a specific desktop environment, which is not the same as the default for a distro. GNOME's browser is Epiphany. Check the docs at gnome.org if you don't believe me.

If most distros choose to make Firefox the default instead of Epiphany, it illustrates my point. So why wouldn't Kubuntu choose to override the desktop environment's default like Ubuntu and most other GNOME based systems do?

---

### Post by zugu on 2009-07-14
> **lykwydchykyn said:**
> Yep, that must be the reason there's a webkit backend for Konqueror in development, available in 4.3.Of course there is a webkit backend in development, but it won't replace the KHTML backend in official releases. It will always be a second class citizen. Clear example of NIH.

---

