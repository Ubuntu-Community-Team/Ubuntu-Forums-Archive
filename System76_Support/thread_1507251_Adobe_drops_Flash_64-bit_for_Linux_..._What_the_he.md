---
title: "Adobe drops Flash 64-bit for Linux ... What the heck?"
date: 2010-06-11
forum: System76 Support
---

### Post by samalex on 2010-06-11
Hey Guys...

As many of you I've been greatly anticipating the release of 64-bit Flash for Linux for almost a year now, well since I got my PanP5 last year.  32-bit Flash using the NSPlugin wrapper is horrible on my system, and through the 64-bit Alpha version worked it was always rather buggy.

Now on their website it says:
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)
> The Flash Player 10.1 64-bit Linux beta is closed.  We remain committed to delivering 64-bit support in a future release of Flash Player.  No further information is available at this time. Please feel free to continue your discussions on the Flash Player 10.1 desktop forums.

And even the [forum to discuss 64-bit Flash for Linux]("http://forums.adobe.com/community/labs/flashplayer10_64bit") has been closed and is now Read Only.  I bet they didn't want a backlash on the forums as people complained.

Also ZDNet has [posted an article]("http://www.zdnet.com.au/has-adobe-killed-64-bit-flash-339303810.htm") about it as well, so it's slowly starting to hit the media.

Hopefully Adobe isn't dropping 64-bit Flash for Linux all together, but it's weird how they've approached this since they've been saying for a while that getting this released was a priority.  I wonder if a huge bug was found or if something else happened that they're not disclosing.  

Anyone have more info?  I'll continue running the Alpha version of 64-bit Flash until more is known, but at this point you can't even download that from Adobe's website anymore.

Sam

---

### Post by formaldehyde_spoon on 2010-06-11
Poor form, Adobe.

Still available via a link here: [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

I wonder if they really are about to release a 64 bit 10.1?  If so, why did they need to pull this so early?

---

### Post by thomasaaron on 2010-06-11
I wonder if it has something to do with Steve Jobs' rant about Flash...

[http://www.guardian.co.uk/technology/blog/2010/apr/29/steve-jobs-flash-ipad-letter-dead](http://www.guardian.co.uk/technology/blog/2010/apr/29/steve-jobs-flash-ipad-letter-dead)

---

### Post by samalex on 2010-06-11
> **thomasaaron said:**
> I wonder if it has something to do with Steve Jobs' rant about Flash...

[http://www.guardian.co.uk/technology/blog/2010/apr/29/steve-jobs-flash-ipad-letter-dead](http://www.guardian.co.uk/technology/blog/2010/apr/29/steve-jobs-flash-ipad-letter-dead)

I dunno, but with Adobe getting so much negative press with Apple blasting at it, I'm not sure why they'd prompt more whoa's from the community by pulling 64-bit Flash for Linux.  Granted we're a minority of the Linux users, but this goes against what they've been saying for at least a year now.

Now's a good time for [Gnash]("http://www.gnu.org/software/gnash/") to start making waves if it supports 64-bit flash.  [FLOSS Weekly interviewed]("http://twit.tv/floss94") the guys with the Gnash project last year, and honestly it seems like a great project.  Anyone tried it out?

Sam

---

### Post by isantop on 2010-06-11
Right now it doesn't work really well, but it could easily be improved. If gnash gets really good really fast, it could easily be *the* Linux Flash Player.

---

### Post by bakelitedoorbell on 2010-06-11
I've been reading about this.  Apparently the 10.1 version patched [this security flaw]("http://www.adobe.com/support/security/advisories/apsa10-01.html"), that still exists in the 64-bit version 10.0.45.2 

Adobe just removed the 64-bit one instead of updating it.  Now I am wondering if I should try the 32-bit one again.  I stopped using it under Jaunty because I couldn't click on the buttons in a flash player window.  Would that bug still be there in 64bit Lucid Lynx?

How much of a security risk is the previous 64bit version of Flash?  *"This vulnerability (CVE-2010-1297) could cause a crash and potentially allow an attacker to take control of the affected system."*  Would this affect a Linux system as well as Windows?

---

### Post by satsujinka on 2010-06-12
It'll probably affect linux. I would just stay away from flash for awhile if you are on 64bit (or just in general.)

---

### Post by paulbary on 2010-06-13
Yet another reason for me to hate Adobe. <G>. Until recently I was using 64 bit Ubuntu but switched over to 32 bit for several reasons one of which was the buggy nature of 64 bit flash ... I've been toying with the idea of a new System 76 desktop box which would come preloaded with 64 bit ... are they using 32 bit flash with the wrapper? ... have people been having satisfactory experience with it on 10.04 ... I'm a big Hulu user so Flash is important to me, so despite my low opinion of Adobe, I've got to live with it at least for now ...

Paul

---

### Post by samalex on 2010-06-14
> **paulbary said:**
> Yet another reason for me to hate Adobe. <G>. Until recently I was using 64 bit Ubuntu but switched over to 32 bit for several reasons one of which was the buggy nature of 64 bit flash ... I've been toying with the idea of a new System 76 desktop box which would come preloaded with 64 bit ... are they using 32 bit flash with the wrapper? ... have people been having satisfactory experience with it on 10.04 ... I'm a big Hulu user so Flash is important to me, so despite my low opinion of Adobe, I've got to live with it at least for now ...

Paul

On my system whether I run 32-bit or 64-bit Flash both have problems.  I ditched the 32-bit version for the Alpha 64-bit version to get webcam support plus the 32-bit version running through the wrapper would often peg the CPU at 100% which the 64-bit Alpha version didn't do.  Problem though with the 64-bit version is it would often crash requiring the browser to be restarted to get Flash working again which was frustrating.

This is on Ubuntu 9.04, but I'd expect the same to happen on 10.04, which from what I've read from others is the case.  I just wish Adobe would be more upfront on their plans, because the 64-bit Flash page for Linux has said for almost a year now that they'll release it concurrently with all other versions of Flash, which hasn't happened.  If there's a major bug in the 64-bit version they need to say so with some estimates, even if just "we're working on it, stay tuned".  

I just hope more sites become HTML5 compliant because that'll be the saving grace here.

Sam

---

### Post by paulbary on 2010-06-14
Thanks for the info it is what I suspected would be the case.
I'd hate to buy a new '76 box and have to wipe it clean and install 32 bit right out of the gate, but that may be the case if I proceed with the purchase ...

Cheers!

---

### Post by silvertuna on 2010-06-17
FYI, some further comment on the problem - 

[http://www.h-online.com/security/news/item/Flash-Player-10-for-64-bit-Linux-vanishes-leaving-some-users-exposed-1023025.html](http://www.h-online.com/security/news/item/Flash-Player-10-for-64-bit-Linux-vanishes-leaving-some-users-exposed-1023025.html)

---

