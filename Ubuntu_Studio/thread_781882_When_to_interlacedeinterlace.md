---
title: "When to interlace/deinterlace?"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by lledurt on 2008-05-04
I am a new to video editing in general so sorry for what probably is a simple question.

I have read quite a bit about interlacing and deinterlacing on the net but need some advice.

I have a DVD converted from an old 8mm film.  I use Cinelerra.  I am rendering it for use on a DVD player on a conventional TV.

When I deinterlace it it looks great on the computer.  Does it need to be interlaced again before I render it on a DVD for use on a conventional TV?  Should I not deinterlace it at all?  Does it only need to be deinterlaced if it is being used on a plasma or a computer?

When I get the material transfered from film, Why do they interlace it?

What are everyones thoughts?

Thanks.

P.J.

---

### Post by kaiataris on 2008-05-06
Any footage you get that came from film will be interlaced by default (conventional TVs use **fields** not **frames**)

If the edited footage is going back to traditional TV, don't deinterlace. If the edited footage is going to be deployed on the web or for digital distribution, then deinterlace before you edit.

-Kai

---

### Post by lledurt on 2008-05-06
Thanks,
Why do they interlace film that was never meant to be on a tv.  I can only assume the companies that transfer from film to DVD assume it will be on a TV.  Are there people that transfer film without deinterlacing it?  
Is there a difference in playing it on a tv v/s a LCD tv?
P.J.

---

### Post by philc on 2008-05-08
> **kaiataris said:**
> Any footage you get that came from film will be interlaced by default (conventional TVs use **fields** not **frames**)

If the edited footage is going back to traditional TV, don't deinterlace. If the edited footage is going to be deployed on the web or for digital distribution, then deinterlace before you edit.

-Kai

Both your assertions are contradictory to what I believed......

Footage shot on film is actually progressive, not interlaced. When film is projected onto a screen, it remains progressive. If film is then telecined to tape, it becomes interlaced. Film upconverted to HD can remain progressive though. e.g. 720p Most TVs do indeed display content interlaced, although some modern HDTVs are capable of progressive display.

Why would you deinterlace before editing? Deinterlacing effectively reduces the quality the picture, unless using accurate inverse telecine for content originally from film. I would always edit with the highest quality master material available, and only deinterlace at the render/output step.

Happy to learn something new though if I'm wrong.

---

### Post by Parasytic on 2008-05-13
One problem with editing an interlaced digital source video is cutting scenes together. Usually, splicing the cuts together in such a way that the interlacing flows properly is a difficult task to do by hand, and I do not know of any software that will automatically do the work for you as you are building scenes.

This has some additional drawbacks, as well. Anyone familiar with cutting fast-paced action scenes knows how much difference can be seen just by adding or omitting a single frame. Because of the way interlaced fields are typically stored in digital formats, via telecine or similar processes, you may find yourself with less room to cut out or tack on single fields per frame.

I figure it's worth mentioning, since quality came into the scope of discussion.

---

