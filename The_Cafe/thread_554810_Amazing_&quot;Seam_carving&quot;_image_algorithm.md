---
title: "Amazing &quot;Seam carving&quot; image algorithm"
date: 2007-09-19
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-09-19
This algorithm is incredible!
It does everything I have wanted an image editor to be able to do, and more, completely intuitively.

I will let the links explain.

[YouTube video (showing enlarging and shrinking, as well as an incredible object removal technique)](http://www.youtube.com/watch?v=6NcIJXTlugc&eurl=http%3A%2F%2Fkoke%2Eamedias%2Eorg%2Farticles%2F2007%2F08%2F22%2Famazing%2Dnew%2Dimage%2Dresizing%2Dtechnology%2F)

[Lots of links (and a nice example image).](http://www.hackszine.com/blog/archive/2007/09/open_source_seam_carving.html?CMP=OTC-7G2N43923558) Particularly nice is that there is indeed a free plugin for GIMP.


If F-Spot starts using this algorithm, for example, I, and probably many others, will worship it as the ultimate photo manager ;)

---

### Post by Nano Geek on 2007-09-19
Man, that's cool!

---

### Post by Lord Illidan on 2007-09-19
Cool!

---

### Post by starcraft.man on 2007-09-19
That is amazing. Me want bad...

---

### Post by notwen on 2007-09-19
This would be very useful, hope it somehow makes it's way something in the repos.

---

### Post by Mr. Picklesworth on 2007-09-19
Well, [the GIMP plugin](http://registry.gimp.org/plugin?id=10292) does have a deb file for Feisty.

---

### Post by starcraft.man on 2007-09-19
> **Mr. Picklesworth said:**
> Well, [the GIMP plugin](http://registry.gimp.org/plugin?id=10292) does have a deb file for Feisty.

Bookmarked, will try later.

---

### Post by GavinZac on 2007-09-19
i've been playing around with this in GIMP 2.4 on Gutsy, im impressed.

first i tested it with a graphic cartoony image, and resizing in two dimesions at the same time. It was a bit unfair on the cartoon to do the more rigourous two dimesional rescale on it, but im not overly unhappy with how it performed. a less detailed cartoon would have held up quite well!
[img]http://www.lustr.us/liquidrescale/1.jpg[/img]
[img]http://www.lustr.us/liquidrescale/2.jpg[/img]

then i decided to test a landscape image with just adjusting the height. this worked very well, the only concern being that the line of the sea level was distorted slightly; this wouldnt be as obvious on most images, and it was mostly caused by the big chunk of rock next to it as well as choosing to distort it vertically rather than horizontally.
[img]http://www.lustr.us/liquidrescale/3.jpg[/img]
[img]http://www.lustr.us/liquidrescale/4.jpg[/img]

my verdict: this rocks, and has plenty of applications right now, and will only get better as time goes on. kudos!

---

### Post by DoctorMO on 2007-09-19
[http://www.corsix.org/retargetr.html](http://www.corsix.org/retargetr.html) <- foss

---

### Post by Mr. Picklesworth on 2007-09-19
It also has some trouble when there is a lot of energy right beside the edge of another object. For example, [this Zen garden picture](http://www.flickr.com/photos/90361640@N00/282104656/), when resized horizontally, gets really wavy looking rocks.

One thing that I am quite impressed by with this algorithm is scaling upwards. Edges get kind of weird, but the actual surface details stay surprisingly sharp.

Scaling down sure beats cropping in a lot of cases. It's fun how this lets me cram stuff into a single frame, without sacrificing much detail. It isn't aesthetically pleasing in *every* case, but it is another very neat tool on the shelf.
I wish I could figure out how feature discarding worked in this GIMP plugin, though.

The algorithm does a really good job of detecting the focal points. It would be nice to see that used elsewhere -- even as a tool of its own.

---

### Post by conehead77 on 2007-09-19
Wow, awesome! Nice tool to resize some pics for my desktop :)

---

### Post by Chilli Bob on 2007-09-19
Used tastefully, this could be wayyyyyyy cool.

---

