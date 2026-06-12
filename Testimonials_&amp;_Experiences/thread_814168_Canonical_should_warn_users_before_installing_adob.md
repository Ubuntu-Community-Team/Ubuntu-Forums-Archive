---
title: "Canonical should warn users before installing adobe flash player on their systems"
date: 2008-05-31
forum: Testimonials &amp; Experiences
---

### Post by dupersuper on 2008-05-31
right now many people are pointing their fingers at firefox3 and worse, ubuntu for the crashes that we know that is the fault of the flash player plugin.
since theres really nothing much Canonical or mozilla can do, at least put the blame where it is due :)

---

### Post by wolfen69 on 2008-05-31
yeah,OK. expect canonical to put in big letters on the homepage, "do not use flash. it will crash your computer". that will work. ive installed flash on more than a few ubuntu machines without incident. does that mean im the luckiest man alive? i think not. please....

---

### Post by Samhain13 on 2008-05-31
"Blame" would be harsh, but I agree that a warning regarding the Adobe Flash player should be issued. And yes wolfen69, you are one very lucky person. I'm not so unfortunate as to have my whole system crash because of a YouTube video, but Firefox does crash frequently because of Flash content. :)

---

### Post by kshane on 2008-05-31
Nice testimonial....

---

### Post by ukripper on 2008-05-31
This is totally absurd statement! Flash is not the only reason for crashes or lockups on Hardy. On one of my machine kernel revision was the culprit for freeze. Therefore, I am using 2.4-16 on Hardy instead of 24-17 for that particular machine which is perfectly running flash without any freeze or lockups.

Should i now say Canonical needs to warn us about the latest kernel revision provided through updates?

---

### Post by jrusso2 on 2008-05-31
> **dupersuper said:**
> right now many people are pointing their fingers at firefox3 and worse, ubuntu for the crashes that we know that is the fault of the flash player plugin.
since theres really nothing much Canonical or mozilla can do, at least put the blame where it is due :)

Actually I think its some changes Ubuntu made either to Firefox or the something else thats the cause, because I don't have this issue with Firefox 3 on mandriva or debian, only in Ubuntu do I hear about it.

Also don't have that issue on Windows.

---

### Post by LaRoza on 2008-05-31
I use Flash from the repos and Opera 9.50b2 with no problems or crashes.

---

### Post by Sef on 2008-05-31
I don't have a problem with Flash either.  I use epiphany mostly, but do use FF3 and Opera at times too.

---

### Post by thiebaude on 2008-05-31
Sorry , but on this one put the blame on the company that makes the flash player.

---

### Post by Happy_Man on 2008-05-31
I dunno... Flash hasn't been a deal-breaker for me, but as I've only noticed this on Hardy running ff3b5, I have to assume this is an Ubuntu issue:

Randomly when browsing Flash content, Firefox will crash. Just smoothly disappear like I clicked the close button. It's annoying. Very, very annoying. 

I'm just saying.

---

### Post by Geekkit on 2008-05-31
> **dupersuper said:**
> right now many people are pointing their fingers at firefox3 and worse, ubuntu for the crashes that we know that is the fault of the flash player plugin.
since theres really nothing much Canonical or mozilla can do, at least put the blame where it is due :)

And "we" know this because we've looked at the kernel/video drivers/fire fox system calls/OGL calls???

Not saying you're right or wrong but with a blanket statement like that you'd had better know what you're talking about.

---

### Post by Joeb454 on 2008-05-31
Why should Canonical warn users? It's not their fault that Flash support on Linux is under par.

And Canonical don't develop the kernel in anyway - they're a corporate sponser to Ubuntu from what I recall.

---

### Post by altariel on 2008-06-01
perhaps this link might help?
[http://ubuntuforums.org/showthread.php?t=747590&page=4](http://ubuntuforums.org/showthread.php?t=747590&page=4)

or this one?
[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

two things to add to those fixes
(if you have both flashblock and adblock addons that is)
- make sure that adblock does NOT replace blocked videos with a tab
- make sure that the site you most frequently watch flash content in (e.g. youtube) is whitelisted in the flashblock options

flash content still occasionally crashes/gets not shown, but does NOT kill firefox or use as much cpu :)

---

### Post by Barrucadu on 2008-06-01
If you're concerned about the stability of Flash and Firefox, use Opera then. It works great with Flash.

---

### Post by SneakyWho_am_i on 2008-06-01
lol, the problem has nothing to do with Firefox (and only affects Hardy, maybe Gutsy). If it is working great in Opera, cool (but it's not because of Opera. I think. I should try it for that, it would be pretty cool).....

I'm not going to go searching now but go look in Launchpad about it. In Hardy, pulseaudio is shipped by default. That's great, Pulseaudio rocks my socks. (NB by default Windows doesn't use pulse, although all the cool kids are downloading it right now probably)
flashplugin-nonfree is a nice thing to have, to unleash the full power of flash (that's the official flash player).
firefox (any version) is also nice.
Unfortunately, it is difficult to get sound in pulseaudio from adobe flash, as they've kind of got archaic sound interface code stuff in there. Exactly what they've done, I don't know. I'm not a programmer and it's closed-source at any rate.
Luckily, Adobe (I think? Someone, anyway) has coded a nice little extension to the flash player :) which allows external programs to interface with its sound-bits.

Ubuntu has a package called libflashsupport - built on that code, it allows flash to talk to pulse. Perfect! Sound from flash :)
Bad side is the crashes. if you start and stop the flash player in your browser a few times (playing sound), you will nuke it and the browser will crash. Why? I don't strictly know.
The problem is:
- NOT Firefox
- NOT pulseaudio
- NOT libflashsupport
The problem is:
- FLASH PLAYER
libflashsupport exposes an instability in the flash player and causes the crash. Check back over the changelog for libflashsupport and see with your own eyes, one of the updates to it was to make it no longer be a dependency of flashplugin-nonfree, because it causes too many crashes and it's something that just can't be fixed in Ubuntu as flash is closed source and the problem is in Flash.

Some people are miraculously not affected. If you're not affected, maybe:
- you're one of those very lucky few (it's all about how hard you press the keys)
or
- you're using a free flash player and not the proprietary one
or
- you're not using pulseaudio
or
- you're not using libflashsupport (which probably means you have no sound in flash)
or
- you don't sit on youtube all day
or
- you just don't watch noisy flash movies
or
- you're using 64 bit Ubuntu (which probably isn't affected because they have an extra package which we don't have right now on 32bit, I THINK, which helps alleviate the problem)
or
- you're using nspluginswrapper (which isn't in the 32 bit repositories)

nspluginswrapper means that if the movies crashes, it doesn't kill the whole browser. It works by moving each instance of the flash player into its own process instead of having it share (and crash) the firefox process.

So the original poster is kind of correct actually ;) although if I'm not mistaken, if you do a fresh install with the latest Hardy then you won't be affected by the bug (although you may not have sound in Flash, so it's the lesser of two evils??)

You have a good point, geekkit, but truly, "we" do "know" that it is (was) due to the flash plugin itself, and nobody can say that they know how the sound in Flash really works unless they work at Adobe, in my humble opinion.

Barrucadu and Altariel's suggestions I like, both. Firefox's extensions for content control rock my socks off. And Opera is quite the awesome browser.

> Actually I think its some changes Ubuntu made either to Firefox or the something else thats the cause, because I don't have this issue with Firefox 3 on mandriva or debian, only in Ubuntu do I hear about it.I don't know about Mandriva or Debian but in some distro or other (maybe all, I think I am thinking of Fedora) they are using nspluginswrapper and that works around the problem pretty nicely. So I suppose you can technically say that it's not due to something Ubuntu's changed about Firefox - rather, it's about something they haven't changed about it, yeah?

> Also don't have that issue on Windows.Windows doesn't have pulse by default. Even if it did, it would probably work fine because of not needing libflashsupport.

> Flash is not the only reason for crashes or lockups on Hardy. On one of my machine kernel revision was the culprit for freeze.
That's more to the point. It is very, very highly frustrating when the browser closes suddenly but at least you can pick up where you left off. When the kernel eats your face, it's not always so kind.

> Should i now say Canonical needs to warn us about the latest kernel revision provided through updates? Hear, hear! I think that they're doing just fine as it is.

Remember that getting all the latest updates is NOT the same as doing a fresh install with all the latest updates already set up.

---

### Post by Thanh-BKK on 2008-06-02
Hello :)

I think i am just lucky with this, or is it because i haven't touched anything "Adobe" yet? I run Ubuntu Hardy on two machines, one with the latest kernel update, the other without (i refuse to update that one because it runs 101% perfect and could not possibly get any better). 

With both machines i obtained flash capability thru the Ubuntu-repos, not from Adobe.

Both machines run YouTube or any other form of "flash in websites" absolutely flawless in FF 3.0 beta 5. 

One of them (the non-updated one) has a Nvidia graphics card, the other an ATI. 

The only reason why i am waiting for FF3 RC1 or full version is because of the "clear list" button in "Downloads", which is missing in the beta.

Best regards.....

Thanh

---

### Post by stchman on 2008-06-04
I use the flashplugin-nonfree on many different machines without incident.  I guess I am the 2nd luckiest man alive.

Anyone who has been using Linux knows that Flash for Linux has some bugs.  Adobe knows about them but wont fix them.  Adobe should just open source Flash 9 so the community can fix it quickly.

---

### Post by stchman on 2008-06-04
> **Thanh-BKK said:**
> Hello :)

I think i am just lucky with this, or is it because i haven't touched anything "Adobe" yet? I run Ubuntu Hardy on two machines, one with the latest kernel update, the other without (i refuse to update that one because it runs 101% perfect and could not possibly get any better). 

With both machines i obtained flash capability thru the Ubuntu-repos, not from Adobe.

Both machines run YouTube or any other form of "flash in websites" absolutely flawless in FF 3.0 beta 5. 

One of them (the non-updated one) has a Nvidia graphics card, the other an ATI. 

The only reason why i am waiting for FF3 RC1 or full version is because of the "clear list" button in "Downloads", which is missing in the beta.

Best regards.....

Thanh

If you use the flashplugin-nonfree from the repos you are using the Adobe plugin.

---

