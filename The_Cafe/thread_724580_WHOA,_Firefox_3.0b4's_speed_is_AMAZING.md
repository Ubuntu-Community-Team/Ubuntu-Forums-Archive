---
title: "WHOA, Firefox 3.0b4's speed is AMAZING"
date: 2008-03-14
forum: The Cafe
---

### Post by jdong on 2008-03-14
I just got my Hardy update for Firefox 3.0b4, and the speedup leaves me speechless.

I am on 100mbit internet so most of my web browsing delays are in rendering time, and this release just makes Firefox FLY and feel like Safari or Opera, even better in many cases (i.e. heavy table sites)


I am right now merging my Firefox 3.0 beta3 packaging with the beta4 packaging in Hardy to generate some backports. Expect about 1 week total time between now and the availability of official firefox 3 beta 4 backports :)

---

### Post by OrangeCrate on 2008-03-14
If it gets any faster, I'm going to need a seatbelt. 3.0b4 is really really cool!

:)

Edit:

I'm on a 10/1 connection.

---

### Post by picpak on 2008-03-14
WHOA, none of my favourite extensions work in Firefox 3.0b4! It's too bad. If they did, I'd switch in a heartbeat.

---

### Post by Joeb454 on 2008-03-14
You can't expect your plugins to work in a beta piece of software really though.
It'd be nice don't get me wrong, but it's just not gonna happen :)

Also jdong, is the Firefox 3 b4 going in Hardy's backports or Gutsy backports?

I can't wait til the final release of FF3 :) It's already better than FF2

---

### Post by jdong on 2008-03-14
> **Joeb454 said:**
> You can't expect your plugins to work in a beta piece of software really though.
It'd be nice don't get me wrong, but it's just not gonna happen :)

Right, currently it's still a beta and until the API finalizes (i.e. release candidate stage) no responsible plugin developer should mark their extension Firefox 3 compatible.

> 
Also jdong, is the Firefox 3 b4 going in Hardy's backports or Gutsy backports?

It will be in Gutsy backports and is already in Hardy final. In fact, I am building its backport locally right now for testing (I've spent the time since my original post working on that)

These backports take a lot of my time to put together because I need to sift through the Hardy changes very carefully -- I want the Firefox 3.0b4 backport to install side-by-side with Firefox 2.0 on Gutsy and for the profiles to be safely duplicated rather than clobbered.

In other words, install Firefox 3 to play with it, and it'll work on a copy of your profile. Don't like it? Uninstall it and Firefox 2 and your Firefox 2 settings are untouched.

---

### Post by kindofabuzz on 2008-03-14
> **picpak said:**
> WHOA, none of my favourite extensions work in Firefox 3.0b4! It's too bad. If they did, I'd switch in a heartbeat.

[http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta)

---

### Post by Joeb454 on 2008-03-14
Sure jdong :) I can understand that

I have Firefox 3 running from ~/firefox ;) I changed the shortcuts in the menu's to point to that instead of Firefox 2, so if I ever want Firefox 2, I just run firefox from a terminal :)

---

### Post by jdong on 2008-03-14
> Final warning: These changes may lead to unexpected wacky behavior. Proceed at your own risk! 

Heed that warning from the site. Make a backup of your ~/.mozilla before doing this, lest be locked out from a crash-on-startup Firefox and be forced to take a lesson in editing firefox config with a text editor.

---

### Post by picpak on 2008-03-14
> **kindofabuzz said:**
> [http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta)

Is that a really a wise idea? To just hack it to work like that? I can see there being unwanted side effects.

---

### Post by jdong on 2008-03-14
> **picpak said:**
> Is that a really a wise idea? To just hack it to work like that? I can see there being unwanted side effects.

When it don't fit, defeat all safety features and make it fit :)

---

### Post by Joeb454 on 2008-03-14
:lolflag: Sounds like the kinda thing I'd do ;)

---

### Post by picpak on 2008-03-14
Yeah, well, I want to too. :lolflag: Are there any debs for Gutsy for beta 4?

---

### Post by Joeb454 on 2008-03-14
Their might be one on getdeb.net :) Though I'll probably wait for the backport of jdong's :) I wouldn't want all that hard work to go to waste

---

### Post by p_quarles on 2008-03-14
Swiftweasel released their version of beta 4 earlier today. That's the easiest thing to use if you don't want to wait for the repositories.

---

### Post by picpak on 2008-03-14
Nothing on GetDeb. I'll wait for jdong, his debs are of better quality than getdeb anyways.

---

### Post by doojsdad on 2008-03-14
The Acid3 test [_results_]("http://en.wikipedia.org/wiki/Image:Acid3_firefox3.png") aren't bad either. I <3 Firefox.

---

### Post by jdong on 2008-03-14
I just uploaded a preliminary test backport (just = 30 seconds ago) for Gutsy into the Backports PPA:
[https://launchpad.net/~ubuntu-backporters/+archive](https://launchpad.net/~ubuntu-backporters/+archive)

**WARNING:** These are TESTING packages. I've only tested on my machine that nothing seems to blow up. I do not recommend installing this unless you are daring of heart and would like to help me test.

Wait for firefox 3.0~b4+nobinonly-0ubuntu1~gutsy1~ppa1  and xulrunner 1.9~b4+nobinonly-0ubuntu1~gutsy1~ppa1  to build successfully before adding that repository (or wait before accepting updates until the above versions show up).

If you use these packages, I would like to ask for you to report feedback at [https://bugs.launchpad.net/gutsy-backports/+bug/191796](https://bugs.launchpad.net/gutsy-backports/+bug/191796) to help speed up the testing process.

---

### Post by kindofabuzz on 2008-03-14
My adons work fine.  Check out the mozillazine.org forums if you need help with anything.  best forums ever. =)

---

### Post by Polygon on 2008-03-15
when is this gonna be backported to gutsy? been waiting at least a week...

---

### Post by jdong on 2008-03-15
> **Polygon said:**
> when is this gonna be backported to gutsy? been waiting at least a week...

Patience, boy, I just spent 2.5hrs working on this backport; the Hardy packages were only introduced on March 13th, see my previous post for test packages (AMD64 and lpia built, i386 is currently sitting in the build queue)

---

### Post by Polygon on 2008-03-15
oh, i thought that was your own personal repo, and i forgot you were a packager ;)

---

### Post by OrangeCrate on 2008-03-15
> **jdong said:**
> When it don't fit, defeat all safety features and make it fit :)

I notice that a couple of my extensions have posted .xpi files. One was user generated, and posted in the comments section of the extension site, and the other was developer generated, to "help with testing". Out of curiosity, what is your opinion on those?

Edit:

No need to comment, unless my understanding is wrong. I just found an explanation that I missed the first time around. I guess if you trust the source, they're O.K, and FF only allows them for approved extensions. It blocks all others. Thanks anyway.

---

### Post by jdong on 2008-03-15
> **OrangeCrate said:**
> I notice that a couple of my extensions have posted .xpi files. One was user generated, and posted in the comments section of the extension site, and the other was developer generated, to "help with testing". Out of curiosity, what is your opinion on those?

Edit:

No need to comment, unless my understanding is wrong. I just found an explanation that I missed the first time around. I guess if you trust the source, they're O.K, and FF only allows them for approved extensions. It blocks all others. Thanks anyway.


Right; just remember that an xpi browser extension could do ANYTHING on your system that your user account can (i.e. create/delete files, run programs/commands locally, etc) PLUS it has easy access to all the browser contents, like the passwords you're typing in, the stored passwords, etc etc etc. I'd be very cautious about trying xpi's that are not from the developer himself or someone else that you trust.

---

### Post by jdong on 2008-03-15
> **Polygon said:**
> oh, i thought that was your own personal repo, and i forgot you were a packager ;)


:) If all goes well, these packages will become the Firefox 3.0beta4 backports.

---

### Post by Joeb454 on 2008-03-15
I'll be looking forward to getting it :)

---

### Post by StOoZ on 2008-03-15
when its planned to be released?

---

### Post by jdong on 2008-03-15
You can follow the progress on [https://bugs.launchpad.net/gutsy-backports/+bug/191796](https://bugs.launchpad.net/gutsy-backports/+bug/191796), but right now I need about 3 or 4 beta testers to test the packages I provided in the PPA and report back on them before I continue.

---

### Post by tbroderick on 2008-03-18
Just installed beta 4 and have been using it all day. Very nice. It does seem lighter and faster, not sure if it's actually is though.

---

### Post by SomeGuyDude on 2008-03-18
Swiftfox is usually the most recent build of FF. Currently I'm on 3.05pre.

---

### Post by mech7 on 2008-03-18
> **SomeGuyDude said:**
> Swiftfox is usually the most recent build of FF. Currently I'm on 3.05pre.

Firebug doesnt work :(

---

### Post by imronak on 2008-03-18
> **picpak said:**
> WHOA, none of my favourite extensions work in Firefox 3.0b4! It's too bad. If they did, I'd switch in a heartbeat.

Dude, i also had the same problem. but i installed FF3 bets B-) and its awesome

Regarding addons, the addon authors are making there addons compatible wiht FF3. I got half of them working.

and i also didnt have any issue with my previsous version of FF2. it still runs fine.

---

### Post by bash on 2008-03-18
I installed the .debs from your PPA. Work nice so far. Only thing that isn't there is Flash. Haven't tried if Java works. But any idea how to get Flash working?

---

### Post by jdong on 2008-03-18
> **bash said:**
> I installed the .debs from your PPA. Work nice so far. Only thing that isn't there is Flash. Haven't tried if Java works. But any idea how to get Flash working?

```

ln -sf /usr/lib/firefox/plugins/* /usr/lib/firefox-addons/plugins

```

---

### Post by Lord Illidan on 2008-03-18
I'd just like to ask, Jdong, how are you building firefox? Are you using Ubuntu's cairo library or Firefox's? Because I recall having a problem with fonts looking extremely ugly when I used Mozilla's binaries.

---

### Post by jdong on 2008-03-18
> **Lord Illidan said:**
> I'd just like to ask, Jdong, how are you building firefox? Are you using Ubuntu's cairo library or Firefox's? Because I recall having a problem with fonts looking extremely ugly when I used Mozilla's binaries.
This package is actually using Mozilla Cairo, I believe, as system Cairo in Gutsy is not new enough.

However, otherwise this package is the same as the one that ships in Hardy -- I only backed out the changes that set Firefox 3.0 as the default Firefox, which we clearly don't want in Gutsy :)

---

### Post by Lord Illidan on 2008-03-18
But don't you notice that the fonts look icky, or was I over sensitive when I used it in Hardy?  
I am using an LCD btw.
Hell, it bothered the hell out of me in Arch until I got a [pkgbuild which uses system-cairo]("http://aur.archlinux.org/packages.php?ID=15172").

---

### Post by jdong on 2008-03-18
Hmm it seems to look like any native app, but I am using Firefox's cairo.

---

### Post by anantshri on 2008-03-18
got the install done yeternight, speed is blazing for me too, also for the extension freaks have patience coz extensions are slowly making thier ways in ff3 also.


but stil i am missing Webdeveloper as well as google toolbar in FF. hoping to get them soon in FF3

---

### Post by SomeGuyDude on 2008-03-18
> **mech7 said:**
> Firebug doesnt work :(

I did the little hack to make all my extensions work. Some don't work (any of the ones not updated for 3 at all), but everything that's listed for any of the FF3 betas is fine.

---

### Post by kmak on 2008-03-19
jdong, thanks and nice work.

Firefox 3 does seem promising, however I am experiencing terrible font rendering under what I assume is mozilla-cairo.

---

### Post by kpkeerthi on 2008-03-19
Been using it for about a week. Very impressive. Best beta software I have ever used.

---

