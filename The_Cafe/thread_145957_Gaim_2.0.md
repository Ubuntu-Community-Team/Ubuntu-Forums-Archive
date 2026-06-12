---
title: "Gaim 2.0?"
date: 2006-03-17
forum: The Cafe
---

### Post by jsmidt on 2006-03-17
Does anybody know why gaim 2.0 still hasn't been released.  It's own website gives you the feel it should have been released a month or two ago.

---

### Post by earobinson on 2006-03-17
> Beta 2: The Sequel to Beta
**We're basically refining crude oil into a usable product.** Only instead of refining crude oil, we're making Gaim better. But it's really the same thing. Really.

Please grab beta 2 and let us know what you think. With any luck we won't need to make any major changes, and [B]Gaim 2.0.0 final will be out before you can prove the theory of special relativity.
[/B]
* Update - January 24th, 2006 - 5:32PM EST *

Gaim 2.0.0 beta 2 does not include voice or video ("vv") support for any protocols. We've done some work toward vv compatibility for Google Talk, but it isn't ready for the general public yet. It is unlikely this will change for the final release of Gaim 2.0.0, but vv will be a primary focus for the next major release of Gaim after that.

* Update - January 27th, 2006 - 5:59PM CST *

Known bugs:

    * Sorting the buddy list by status is broken in Gaim 2.0.0 beta 2. The next release, be it beta 3 or the final 2.0.0, will have this bug fixed.

    * Duplicate saved statuses show up in the status selector.

    * Some people are experiencing sound playback issues on Linux when using libao. Using the Command method or copying the sound files from beta1 are both workarounds. We're looking into this.

Still in testing is what the i get out of that. Still lots of bugs that need to be fixed to make it usable.

---

### Post by Miguel on 2006-03-17
I can't help myself, but do the Gaim devs consider the Michelson-Morley experiment proof of the special theory of relativity???

:twisted: :twisted: :twisted: :twisted: :twisted:

---

### Post by bjweeks on 2006-03-17
Gaim is a slow moveing project.

---

### Post by Sheinar on 2006-03-17
Gaim 2.0 was only worth looking forward to because of the supposed vv support anyway. Now the only thing it really has going for it is the version number, which makes it seem like an important release.

---

### Post by Tipo on 2006-03-17
Well, 2.0.0 brings many many fixes, it says it right in one of the posts, "2.0.0 will fix any problem you've ever had with Gaim".  

Personally, I would rather have a working file transfer than audio/video, and 2.0.0 claims to fix the file transfer.

---

### Post by Sheinar on 2006-03-17
Bug fixes are expected. In any release. (Not that I expect them to fix half of the problems that Gaim currently has.) Working file transfer *and* vv support would have been worthy of a 2.0 release. From what I've seen so far, this isn't shaping up to be what I'm sure was originally expected of it.

At least them taking time between the beta2 and the next beta or final release hopefully shows they're working hard to improve it, instead of releasing it prematurely.

---

### Post by BWF89 on 2006-03-17
[QUOTE=Tipo]Personally, I would rather have a working file transfer than audio/video, and 2.0.0 claims to fix the file transfer.[/QUOTE]
Same here, people say that it works for them but I've never gotten Gaim's file transfer to work (useing AIM) even after a fresh install of Windows XP.

---

### Post by bjweeks on 2006-03-17
[QUOTE=BWF89]Same here, people say that it works for them but I've never gotten Gaim's file transfer to work (useing AIM) even after a fresh install of Windows XP.[/QUOTE]

Works for me.

---

### Post by dosed150 on 2006-03-17
file transfer always works for me it can just be painfully slow sometimes

---

### Post by magnusbb on 2006-03-17
[QUOTE=dosed150]file transfer always works for me it can just be painfully slow sometimes[/QUOTE]

Yes, all the time, actually, and that's because Gaim 1.5 can't transfer P2P but has to go via a Microsoft server.

---

### Post by mustang on 2006-03-17
File transfer works on Windows for me but not on Ubuntu...

---

### Post by granite230 on 2006-03-17
[QUOTE=dosed150]file transfer always works for me it can just be painfully slow sometimes[/QUOTE]

It's actually slow enough for people to cancel the file transfer and tell me Linux sucks anyway...

---

### Post by jsmidt on 2006-03-18
[QUOTE=Miguel]I can't help myself, but do the Gaim devs consider the Michelson-Morley experiment proof of the special theory of relativity???

:twisted: :twisted: :twisted: :twisted: :twisted:[/QUOTE]

Actually probably the best experimental evidence for the special theory of relativity is being done in our particle accelerators.  Quantum Field Theory, which is the version of quantum mechanics assuming special relativity is correct, has been experimentally verified to 9 signifigant figures.
 
To the layman this means the theory is so good it is like theoretically predicting the distance between New York and LA and experimentally finding you were only off by the less than width of a human hair!!!  Now that is experimental proof for both quantum mechanics and special relativity.


By the way for all those wise guys out their who say you can't unite quantum mechanics with relativity, it is General Relativity you can't unite with quantum mechanics.  Special Relativity works just fine and man is it accurate!  \\:D/

---

### Post by Virogenesis on 2006-03-18
[QUOTE=magnusbb]Yes, all the time, actually, and that's because Gaim 1.5 can't transfer P2P but has to go via a Microsoft server.[/QUOTE]
MSN File Transfer
The MSN protocol supports several different file transfer methods which are used under different network conditions. Currently, Gaim only supports a method that transfers through the MSN servers. While this is guaranteed to work under any network condition (even if both sides are behind NAT devices, for instance), it is unbearably slow.

Your task this summer is to implement at least one other MSN file transfer protocol: one that directly connects the two clients. You will also need to provide a mechanism that will easily fallback on the slow through-the-server method in case your new method fails. This may involve reverse engineering, but there are other free software implementations you may use as a reference.

**Rejected**


granite230: Ignore the idiots its simple they clearly know nothing.
Gaim would still have the same probs on windows.

Also file transfer did get fixed in gaim 2 as you can now direct connect to AIM I was actually surpised when i first tried gaim 2 as a contact of mine wanted to show me some pictures and I was damn its not going to work and it connected I just had to smile to myself. 
But yeah Slow MSN file transfer won't be fixed I don't think as it got rejected.

[http://gaim.sourceforge.net/summerofcode/](http://gaim.sourceforge.net/summerofcode/)

---

### Post by Stormx on 2006-03-18
I have some real problems with the latest beta anyway. A lot of the time, people get "message cannot be delivered" when sending messages to me, and I always have to engage the convo.. etc.

Otherwise 2.0 is nice, with nudges and custom emoticons, and the smooth way it adds messages to the window. But I've gone back to the 1.x series because of the connectivity problems.

---

### Post by Project 318 on 2006-03-18
File transfers between linux gaim and linux gaim work, while file transfers between windows gaim and linux gaim don't.  
Also, file transfers between the offical aim client and gaim work fine.
This is with gaim 2.0beta2 on both ends.

It's always struck me as weird so hopefully whatever causes that to happen will be fixed.

---

### Post by s_spiff on 2006-03-18
are we talking on GAIM or physics? [ not thati can understand any of these :P ] .
by da way.. any place..where a under grad. can read about theory of relativity..without all the over the head terminologies? [ is that possible?]

---

### Post by jsmidt on 2006-03-18
[QUOTE=s_spiff]
by da way.. any place..where a under grad. can read about theory of relativity..without all the over the head terminologies? [ is that possible?][/QUOTE]

If you want a non-too-technical explaination which is enough to impress anyone I would recommend "The Elegant Universe" by Brian Greene.  You would learn a lot about string theory too.  If you are willing to put up with a fair amount of math without being a purely graduate texbook on General Relativity I recommend  "General Relativity" by Sean Carroll.  Although I do warn you the math is on the border of Undergrad/Grad Mathematics.  

But like I said, Brian Greene's book is readable by all on an undergraduate, maybe even high school technical level. Any knowing a little about string theory would definatly put you on the forefront of physics.  In fact if the gaim people said it won't be released before they prove string theory it may not be released this century.

---

