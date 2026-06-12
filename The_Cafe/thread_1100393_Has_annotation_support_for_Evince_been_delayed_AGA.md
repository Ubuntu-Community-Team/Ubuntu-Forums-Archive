---
title: "Has annotation support for Evince been delayed AGAIN?"
date: 2009-03-19
forum: The Cafe
---

### Post by Stefanie on 2009-03-19
I just saw that Evince/annotations has been moved to the Gnome 2.28 roadmap [http://live.gnome.org/Evince/Roadmap](http://live.gnome.org/Evince/Roadmap) . Why? This feature was promised for Hardy if I remember it correctly :o

I think annotations support (highlighting and commenting in pdf-files) would be a killer feature for a lot of users and many of us have been waiting for ages. I know, there's Xournal, but that's not good enough, and you can run apps like PDF-Xchange viewer through Wine, but a native app would be much better. I also know about Okular but I tried it and it is still much less functional than something like PDF-Xchange. Moreover, comments and such are not stored in the pdf-file itself but in a seperate file, which is pretty useless for me. 

I'm very disappointed about this being delayed again :(

---

### Post by olejorgen on 2009-03-21
I whish I could make a directed donation to a project trying to make a usable document reader :-/ They all suck. (on windows too, unless something have changed the past 2 years)

If it had real potential I could probably donate as much as $150 :)

---

### Post by Stefanie on 2009-04-01
>  Evince 2.26 without annotations
02:15

Annotations support is in our RoadMap since GNOME 2.20, and it has been the main goal since then. However, we failed in 2.22, in 2.24 and we are going to fail again in 2.26.

Lack of time is the main reason for this failure (remember that we, the Evince development team, are all volunteers), but it's not the only one. During the 2.25/2.26 cycle we have started to work on the annotations stuff, although (as usual) a little bit late, when the feature freeze deadline approached. When we had the minimum support already implemented, we realized that poppler didn't have support for writing annotations yet. I don't know why, but I was quite sure it was already implemented. The thing is that there isn't writing support for annotations in poppler right now. So we had, at least, two options: releasing evince 2.26 with annotations support in a read only mode or delaying the annotations support to the next cycle once again. Both have advantages and disadvantages, but the main reason why we decided not to release 2.26 with annots support is because we don't think that annotations are useful if you can't actually use them. I'm sure we were going to receive lots of bug reports about non editable popups.

So, what's the plan? The idea is to implement writing support in poppler ASAP, and merge the evince code early in the next development cycle.

Despite the annots stuff, I'm very happy with the work done during this cycle, but I think I'll better talk about Evince 2.26 later in another post.


[http://carlosgc.linups.org/gnome/evince-2-26-without-annots.html](http://carlosgc.linups.org/gnome/evince-2-26-without-annots.html)

---

