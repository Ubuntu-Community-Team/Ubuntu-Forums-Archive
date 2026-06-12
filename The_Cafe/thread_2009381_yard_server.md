---
title: "yard server"
date: 2012-06-24
forum: The Cafe
---

### Post by Gompa on 2012-06-24
I had a old p4 lying around the house and started wondering what I could do with it. (I already own a home media server.)
After some time I started wondering how long a desktop would survive outside in the rain, 
but realized that without any protection it would probably only take some drizzle to kill it.
So I taped up some of the holes and put it in my yard, 
and wrote a crappy twitter script to keep track of it [@yardserv]("https://twitter.com/#!/yardserv")

I dont recommend you doing this to your desktop, or any computer for that matter. 

Don't really know if its of interest to any of you but I thought I'd share it

---

### Post by sffvba[e0rt on 2012-06-24
:)


404

---

### Post by Lightstar on 2012-06-24
interesting test ;)
Not really sure how practical it is to have a desktop in the yard though

---

### Post by Gompa on 2012-06-24
> **Lightstar said:**
> interesting test ;)
Not really sure how practical it is to have a desktop in the yard though

yeah its running ubuntu server 12.04 but iam having a hardtime letting my fileserver act as a proxy for it

---

### Post by HansKisaragi on 2012-06-24
awesome sauce :) :KS

---

### Post by fatality_uk on 2012-06-24
Many years ago, my sister was about to throw out a TV that had been in the garden ALL winter under about a foot of snow. all that was wrong was the vertical hold (anyone remember CRT's :))

After two days of drying out and a quick twist with a screwdriver, all was well.

---

### Post by Gompa on 2012-06-25
[IMG]http://trinity.h-bomb.nl/foto/pcding.jpg[/IMG]
It's not a looker, but that's not the point.
I closed off all of the holes in the case, except for cpu fan intake and powersupply output, and stuck on some chinese food packaging hoping it will keep some water away from the cpu fan intake.

---

### Post by jwbrase on 2012-06-25
> **Gompa said:**
> I had a old p4 lying around the house and started wondering what I could do with it. (I already own a home media server.)
After some time I started wondering how long a desktop would survive outside in the rain, 
but realized that without any protection it would probably only take some drizzle to kill it.
So I taped up some of the holes and put it in my yard, 
and wrote a crappy twitter script to keep track of it [@yardserv]("https://twitter.com/#!/yardserv")

I dont recommend you doing this to your desktop, or any computer for that matter. 

Don't really know if its of interest to any of you but I thought I'd share it

The script that posts to Twitter is buggy. It loops back around to zero every 12 hours, and when showing a time less than 1 hour, it says "X min hours".

---

### Post by forrestcupp on 2012-06-25
> **jwbrase said:**
> The script that posts to Twitter is buggy. It loops back around to zero every 12 hours, and when showing a time less than 1 hour, it says "X min hours".

At least Twitter keeps track of when something is posted.

---

### Post by Gompa on 2012-06-25
> **jwbrase said:**
> The script that posts to Twitter is buggy. It loops back around to zero every 12 hours, and when showing a time less than 1 hour, it says "X min hours".

i know its a little buggy the problem is:
the server powered down because it was connected to a light switch(i know should have check t that) 

and the scipt i use is verry simple:
```
`uptime |cut -c14-18` hours
```

but it only works if the uptime is more than a hour

so yeah it could use some improving :redface:

---

### Post by mr-woof on 2012-06-25
You should make it a webserver, serving a special yardserver webpage :)

---

### Post by CharlesA on 2012-06-25
> **mr-woof said:**
> You should make it a webserver, serving a special yardserver webpage :)
That would be pretty cool!

Maybe something in php that could display uptime or some such thing...

---

### Post by Paqman on 2012-06-25
Sod that. Fit a webcam, a motion sensor and a paintball gun and have it post pictures to Twitter of it wasting all the neighbourhood cats.

You would win the internet if you did this.

---

### Post by CharlesA on 2012-06-25
> **Paqman said:**
> Sod that. Fit a webcam, a motion sensor and a paintball gun and have it post pictures to Twitter of it wasting all the neighbourhood cats.

You would win the internet if you did this.

That would be epic.

Here I was thinking of having something where it lists the time, and the temperature outside. ;)

---

### Post by Gompa on 2012-06-25
the webcam is a good idea.
still working on the apache server doh.
[ having a hardtime]("http://ubuntuforums.org/showthread.php?t=2010350") using my home server as a proxy

---

### Post by Porcini M. on 2012-07-02
> **paqman said:**
> sod that. Fit a webcam, a motion sensor and a paintball gun and have it post pictures to twitter of it wasting all the neighbourhood cats.

You would win the internet if you did this.

+1 8)

---

### Post by Gompa on 2012-08-16
yardserver is still running strong.
i have added a website to it and a webcam.
iam still looking for a way to add a humidity sensor

any way here is the link : [yardserv.h-bomb.nl]("http://yardserv.h-bomb.nl/")

---

