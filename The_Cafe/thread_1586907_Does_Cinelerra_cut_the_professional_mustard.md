---
title: "Does Cinelerra cut the professional mustard?"
date: 2010-10-02
forum: The Cafe
---

### Post by Jaecyn42 on 2010-10-02
I'm asking this on behalf of a friend who has encountered Malware problems on his XP laptop.  He has asked me to help salvage his data an repair the problem; so naturally, I suggested he try out Ubuntu, if only for his web-browsing.

This got us started on a discussion about Open-Source Non-Linear Editors and how they stack up against Avid Media Composer, which currently serves as the *de facto* Industry leader NLE in Television and Film.

He is currently working as Production Crew for the local Public Television affiliate and would like to have a NLE of equivalent capacity to Avid Media Composer for his personal use at home.

Naturally, I told him there are Open Source options: Cinelerra, Kino, LiVES, etc; but digital video is not my forte and I honestly do not know much about the professional capabilities of any of these programs, except that Cinelerra is commonly considered the most advanced Open Source NLE.

So, here I am, asking The Community.  Is Cinelerra the best that Open Source has to offer in NLEs?  If not, which NLE are superior to Cinelerra?  Above all, can open-source meet or exceed Avid Media Composer in capacity and usability?  

Bare with me if I seem a little ignorant on the subject; again, Digital Video isn't my forte

---

### Post by sdowney717 on 2010-10-02
you can look into these, I dont know how good they are for what you want.

1) Kdenlive

2) Kino

3) Blender

4) Cinepaint

5) Cinelerra

6) Pitivi

7) Lives

8 Avidemux

9) Slideshow creator

10) Vivia

11) Jahshaka

12) Lumiera

13) Openshot

---

### Post by sdowney717 on 2010-10-02
[http://www.blender.org/development/release-logs/blender-242/video-sequence-editor/](http://www.blender.org/development/release-logs/blender-242/video-sequence-editor/)

blender I think is probably good.

---

### Post by Jaecyn42 on 2010-10-02
> **sdowney717 said:**
> [http://www.blender.org/development/release-logs/blender-242/video-sequence-editor/](http://www.blender.org/development/release-logs/blender-242/video-sequence-editor/)

blender I think is probably good.

I have heard that Blender is very good; there was a post just recently about Sintel, a film created in Blender.  Looked interesting.

At any rare, Blender isn't exactly the program he needs.  While he already admits that Linux can do very impressive things in 3D Animations (see Pixar); he works exclusively with live-action.

Blender is cool, make no mistake; but my friend wouldn't get much use out of it.

---

### Post by kaldor on 2010-10-02
> **Jaecyn42 said:**
> I'm asking this on behalf of a friend who has encountered Malware problems on his XP laptop.  He has asked me to help salvage his data an repair the problem; so naturally, I suggested he try out Ubuntu, if only for his web-browsing.

This got us started on a discussion about Open-Source Non-Linear Editors and how they stack up against Avid Media Composer, which currently serves as the *de facto* Industry leader NLE in Television and Film.

He is currently working as Production Crew for the local Public Television affiliate and would like to have a NLE of equivalent capacity to Avid Media Composer for his personal use at home.

Naturally, I told him there are Open Source options: Cinelerra, Kino, LiVES, etc; but digital video is not my forte and I honestly do not know much about the professional capabilities of any of these programs, except that Cinelerra is commonly considered the most advanced Open Source NLE.

So, here I am, asking The Community.  Is Cinelerra the best that Open Source has to offer in NLEs?  If not, which NLE are superior to Cinelerra?  Above all, can open-source meet or exceed Avid Media Composer in capacity and usability?  

Bare with me if I seem a little ignorant on the subject; again, Digital Video isn't my forte


Considering some major feature-films were made using Cinelerra, I consider it professional enough :)

Old, but: [http://digitalcontentproducer.com/dcc/video_video_penguins/](http://digitalcontentproducer.com/dcc/video_video_penguins/)

I *think* Pixar uses it.

Edit: Ah, I was thinking of CinePaint: [http://www.cinepaint.org/](http://www.cinepaint.org/)

---

### Post by Warpnow on 2010-10-02
Lightworks, a professional video editor, is going open source and currently has a private beta for linux.


No, Cinellerra is not professional quality. Lumiera is closer, but incomplete.

---

### Post by Jaecyn42 on 2010-10-02
> **Warpnow said:**
> Lightworks, a professional video editor, is going open source and currently has a private beta for linux.

That's excellent news. Thank you.

> No, Cinellerra is not professional quality. Lumiera is closer, but incomplete.

Could you elaborate on this point a little?  How does Cinelerra fail to measure up, more specifically?

---

### Post by forrestcupp on 2010-10-02
Cinelerra is pretty amazing, and you can do a lot with it.  The main reason people are biased against it is because they don't want to spend the time on the learning curve.  It's not as intuitive as something like Sony Vegas, but you can do a lot with it.

My main complaint with Cinelerra is that it can't handle a lot of different video formats.  If you use it, make sure to use the CV version.

---

### Post by decoherence on 2010-10-02
the interface for cinelerra won't be a problem if he works with AVID or any other 'real' NLE. it might feel 'old school' but it won't be hard to figure out. my main problem with cinelerra is that every time i've used it, it has had stability problems to the point of making me running away screaming. I haven't used it in a year or so tho, so maybe it's better now?

it has a feature-set more or less equivalent to Premiere 4, iirc.

think again about blender. it's not just for 3d anymore! ;) although I would say its built-in NLE is great for compositing I'm not sure I'd want to do anything long form on it.

Pitivi is fine if all you want is to cut and splice with the occasional cross dissolve. I wonder if it would be useful to use it alongside Blender, sort of like how people use Premiere alongside After Effects (or whatever.)

If he does end up checking out blender keep in mind they'll be releasing a new version with a brand new interface soon. (beta available from their site or the ricotz ppa)

Finally, Discreet Smoke/Fire will run on Linux. I have no idea if it runs on Ubuntu tho. FORscene is another one that may or may not suit your friend's purposes.

---

### Post by Warpnow on 2010-10-03
Last I checked, Smoke/Fire only run on a custom version of RHEL with a custom kernel. Closed parts of this custom RHEL check for a dongle which has a unique id for every user. 

So, even if you get the RHEL with the custom kernel, you'd need a dongle of someone who owns this software, which costs as much as a nice car.

As far as Cinellera, its featureset is fine. Its UI is annoying and slow, and it is terribly unstable. Lumiera is supposed to be a rebuild basically...but I've not seen much happening on it lately...

Best bet will likely be Lightworks. Its not far off.

MainActor had a linux port. Its a Premiere-Like editor. They stopped supporting their linux port a while back, but...it can be gotten still, though with some difficulty.

---

### Post by sdowney717 on 2010-10-03
> think again about blender. it's not just for 3d anymore!

that is what that link I posted implies to me also.

---

### Post by forrestcupp on 2010-10-03
> **Warpnow said:**
> Lumiera is supposed to be a rebuild basically...but I've not seen much happening on it lately...Right.  It will be 50 years before we see anything out of Lumiera.

> **Warpnow said:**
> Best bet will likely be Lightworks. Its not far off.Does anyone know when they are going to release Lightworks Open Source?  Their web site has a signup, but I couldn't find any info that actually says when they are releasing it.  All I could find are 3rd party blogs that say fall of this year.  I don't understand what takes so long about opening up the code.

---

### Post by decoherence on 2010-10-03
> **Warpnow said:**
> So, even if you get the RHEL with the custom kernel, you'd need a dongle of someone who owns this software, which costs as much as a nice car.

Well, the dude is using Media Composer, so if his main desire is to get away from a virus-ridden system, the Discreet programs might do it for him if he can justify the cost. That said, I have never used smoke or fire so they could be completely NOT what op's friend is looking for. Just tossing out names, really.

Then again, if op's friend wants his AVID system to be virus free, he could do what Mac users did back in the System 7/8/9 days.... just remove any networking functionality. They didn't do it because of viruses but because AppleTalk and OpenTransport killed the ability to capture video at full frame rate and triggered all kinds of bad behavior when running the system at a high load. Nonetheless, even without networking they somehow managed to get their work done ;) Of course these days s/he'd have to worry about USB keys and Sony products as well.

Ramble off

---

