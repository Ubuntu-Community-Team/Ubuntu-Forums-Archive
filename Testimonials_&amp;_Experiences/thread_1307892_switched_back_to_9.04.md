---
title: "switched back to 9.04"
date: 2009-10-31
forum: Testimonials &amp; Experiences
---

### Post by fillintheblanks on 2009-10-31
I would have to say 9.10 is not a very good release. Gave it a try for a few hours and gave up


1. The new grub - ok I know in previous Ubuntu releases you could disable the grub by invoking the 'hiddenmenu' option in menu.lst but now there is no such option, the new parameters are to confusing

2. empathy or epithany IM - out of the box it refused to connect to msn, I don't know why. it just wouldn't connect so I gave up

3. new software store - I don't like it. Add/remove was way better, it had ratings, you had the option to sort programs and see download progress of each file, everything was in clear view segregated nicely. now with the software store/center it just hides stuff and theres too many buttons to press

4. wouldn't compile wine 1.1.32 - like 30 minutes into compilation it aborts due to some compilation error. I tried couple of times same result, I gave up

5. the new volume control - its ****. it hides a whole whack of options. as a result my sound was not working out of the box. after like 1 hour I figured out to go into 'alsaconfig' in the terminal and find the correct setting to change from digital to analog. ok that made the sound work but my FM tuner card was still mute (no gnomeradio for me)


I went back did a fresh 9.04 install, everything worked

wine compiled on first try, msn connected in pidgin, sound worked out of the box, gnome radio works. I can disable grub easily I'm happy. 


Why fix something that's not broken? 9.10 tries to change too many things that were working great, and now they don't work anymore. not a very good release in my opinion, I am sticking with 9.04

---

### Post by Eagles18 on 2009-10-31
I,too,dislike the new software store.However,I love everything else about 9.10

---

### Post by meho_r on 2009-10-31
C'mon, how can Software Center be a show-stopper? And Empathy? Just use Synaptic as always and Pidgin. I'm personally not too much happy with Karmic, but it's not that bad.

---

### Post by solwic on 2009-10-31
> **meho_r said:**
> C'mon, how can Software Center be a show-stopper? And Empathy? Just use Synaptic as always and Pidgin. I'm personally not too much happy with Karmic, but it's not that bad.

It's not bad...it's just not as good as I thought it was at first.  Too many stupid little bugs, and like the OP said, they tried to change too many things that worked perfectly, replacing them with things that were experimental/beta at best.  

But they'll iron it out.  This just reaffirms what a friend told me when I told him I was installing Karmic.  His advice was to give it a while, and I didn't listen, and here I am, waiting 12 hours for Jaunty updates to download over a 6Mbps connection....

Live and learn, I guess.

---

### Post by HappyFeet on 2009-10-31
> **meho_r said:**
> And Empathy? Just use Synaptic as always and Pidgin.

That makes too much sense. ;)

And why do you have to compile wine? You can get a .deb of the latest wine at launchpad.

Oh well, I think karmic is an improvement, but if you don't like it, don't use it. I myself am getting ready to wipe out kubuntu 9.10. Good luck to you.

---

### Post by solwic on 2009-10-31
> **HappyFeet said:**
> That makes too much sense. ;)

And why do you have to compile wine? You can get a .deb of the latest wine at launchpad.

Oh well, I think karmic is an improvement, but if you don't like it, don't use it. I myself am getting ready to wipe out kubuntu 9.10. Good luck to you.

You can run Pidgin just fine, but there's no way to turn off Empathy.  At least, not that I could find.  So you're running two IM clients when you only need one.  

As for the Software Center...I didn't see much change, beyond the aesthetics.  It worked the same, essentially.

---

### Post by ugm6hr on 2009-10-31
New releases of an OS always add new features at the expense of stability and familiarity.

The 6-monthly release schedule makes these issues more apparent for some.

I normally wait a few months before installing a new version, and just use alternate versions (inc LTS) i.e 6.06, 7.04, 8.04, 9.04... might wait til 10.04 LTS. Still undecided.

---

### Post by jdrodrig on 2009-10-31
> **ugm6hr said:**
> New releases of an OS always add new features at the expense of stability and familiarity.

The 6-monthly release schedule makes these issues more apparent for some.



Familiarity is a reasonable cost, stability is not!

---

### Post by regomodo on 2009-10-31
#

---

### Post by solwic on 2009-10-31
> **ugm6hr said:**
> New releases of an OS always add new features at the expense of stability and familiarity.

The 6-monthly release schedule makes these issues more apparent for some.

I normally wait a few months before installing a new version, and just use alternate versions (inc LTS) i.e 6.06, 7.04, 8.04, 9.04... might wait til 10.04 LTS. Still undecided.

That's not a bad idea, actually.  Just skip every other release.  Think I might try that. 

How long is the support period for a non-LTS release?  A year?

---

### Post by meho_r on 2009-10-31
> **solwic said:**
> That's not a bad idea, actually.  Just skip every other release.  Think I might try that. 

How long is the support period for a non-LTS release?  A year?

18 months.

---

### Post by solwic on 2009-10-31
> **meho_r said:**
> 18 months.

For NON-LTS releases?  Seriously?

---

### Post by NCLI on 2009-10-31
1. The new grub - ok I know in previous Ubuntu releases you could disable the grub by invoking the 'hiddenmenu' option in menu.lst but now there is no such option, the new parameters are to confusing
-----------------
The parameters are different to what you're used to, of course. Try reading some documentation.
-----------------

2. empathy or epithany IM - out of the box it refused to connect to msn, I don't know why. it just wouldn't connect so I gave up
-----------------
Then install Pidgin, tadah!
-----------------

3. new software store - I don't like it. Add/remove was way better, it had ratings, you had the option to sort programs and see download progress of each file, everything was in clear view segregated nicely. now with the software store/center it just hides stuff and theres too many buttons to press
-----------------
The Software Store can sort items, the ratings in Add/Remove were worthless, you can still see individual file progress(it's actually been improved), and finally: You can actually reinstall Add/Remove programs from the Software Center or Synaptic.
-----------------

4. wouldn't compile wine 1.1.32 - like 30 minutes into compilation it aborts due to some compilation error. I tried couple of times same result, I gave up
-----------------
Compilation isn't exactly straightforward, and shouldn't be expected to"just work." Wine is in the repos, or, if you really want to compile it, ask people here for advice when you encounter an error. Odds are it won't work in 10.04 either.
-----------------

5. the new volume control - its ****. it hides a whole whack of options. as a result my sound was not working out of the box. after like 1 hour I figured out to go into 'alsaconfig' in the terminal and find the correct setting to change from digital to analog. ok that made the sound work but my FM tuner card was still mute (no gnomeradio for me)
-----------------
You can still change from digital to analog mode in te new settings menu. Did you ask here in the forum when you were unable to find it?
-----------------

I'm noy annoyed at you, personally, just at the incredible amount of people who don't post 'till they've decided they're not even going to try to solve their problems!

---

### Post by ugm6hr on 2009-10-31
> **jdrodrig said:**
> Familiarity is a reasonable cost, stability is not!

New features = untested code.

This obviously occurs in shades of grey rather than black and white, but instability is inherent with new features.

No program can introduce new features without any bugs; the length of time spent testing can mitigate this instability, but 6 monthly release schedule doesn't allow that much testing time to stabilise the bleeding edge features.

And yes, every release gets 18 months of support.

---

### Post by danielshewchuk on 2009-10-31
How do you get the sound to work?? What did you type in the terminal? Please help

---

### Post by meho_r on 2009-10-31
> **solwic said:**
> For NON-LTS releases?  Seriously?

Yep, non-LTS has support for 18 months. LTS is supported for 3 years on desktop and 5 years on servers.

---

### Post by solwic on 2009-10-31
> **meho_r said:**
> Yep, non-LTS has support for 18 months. LTS is supported for 3 years on desktop and 5 years on servers.

Cool.  That makes me feel better about sticking with Jaunty for now.  

Thanks.  :)

---

### Post by kg4cna on 2009-10-31
This is why I don't upgrade right away.  Give 'em time to iron out the bugs first.  I'll be waiting on the next LTS before upgrading.

A~

---

### Post by Vakman on 2009-10-31
> **fillintheblanks said:**
> I would have to say 9.10 is not a very good release. Gave it a try for a few hours and gave up
2. empathy or epithany IM - out of the box it refused to connect to msn, I don't know why. it just wouldn't connect so I gave up
3. new software store - I don't like it. Add/remove was way better, it had ratings, you had the option to sort programs and see download progress of each file, everything was in clear view segregated nicely. now with the software store/center it just hides stuff and theres too many buttons to press
I agree this Empathy client is not very good at all. MSN did not work right away but it has fixed itself it seems. No idea why they would replace a great client like Pidgin. Empathy looks so basic.
My biggest complaint is this software store. What in the world was wrong with Add/Remove. This software store does not even look good. Most importantly there is not an option to sort by ratings, 
you can't just mark something for installation; it automatically starts, instead of checking a box you have to open it and hit install; this is fine except when you click install it does not auto-navigate back to the previous page.
Far better than 9.04 was and even at release.

> **solwic said:**
> 
As for the Software Center...I didn't see much change, beyond the aesthetics.  It worked the same, essentially.
Most certainly not. Much more annoying to use now. It is just unbelievable how they did this. Single worst thing about 9.10.

> **jdrodrig said:**
> Familiarity is a reasonable cost, stability is not!
+1

---

### Post by solwic on 2009-10-31
> **Thisislaw said:**
> I agree this Empathy client is not very good at all. 

+1.  Empathy sucks.  Pidgin is much, much better, both aesthetically and functionally.  

[quote=Thisislaw]
Most certainly not. Much more annoying to use now. It is just unbelievable how they did this. Single worst thing about 9.10.
[/QUOTE]

I only used it a couple times.  I'm a CLI guy.  "apt-get install" is my bestest friend.  :biggrin:

---

