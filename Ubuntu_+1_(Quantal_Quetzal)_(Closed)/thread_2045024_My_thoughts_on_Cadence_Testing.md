---
title: "My thoughts on Cadence Testing"
date: 2012-08-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-08-20
I thought I would post a thread just to gather feedback on this. I know this idea of cadence testing been confusing and perhaps controversial. With that in mind, I wanted to both define the idea, and give you my thoughts on it. I also gave a summary of what I believe has happened so far this cycle since undertaking this idea.

So here it is!

[The grand cadence experiment]("http://www.theorangenotebook.com/2012/08/the-grand-cadence-experiment.html")

Comment here, on the blog, via my inbox -- wherever. Public conversations are preferred by me so all can be involved and comment, but feel free to send something privately if you wish.

---

### Post by ventrical on 2012-08-20
Nick,

Thats a masterpiece!

My comment is that something really significant has to be done with apport, our auto-bug reporting tool. It has become more of a nuisance than an asset. I have seen extremely GOOD talent  here being wasted on nvidia/xserver problems  while other significant bugs get swept under the carpet. Also, the fiasco with nautilus and the (me) and that problem getting totally ignored. So how are  us beta testers supposed to take these short shrifts with these video graphics problems and nautilus? Is it wrong for us to wonder who is steering the ship at Canonical? I make this statement because if nvidia is always going to fail (as it has now for the past three releases) then why is the Ubuntu braintrust not providing us with a simple a workable fallback?

Also the removal of Unity 2D just about killed Unity as a whole and left the flagship ubuntu concept dead in the water. 

 You , as sort of our emmissary :) ,have to keep up these excellent essays and drive home these crucial points, especially from  the U+1 point of view. I hope I am not sounding like I am speaking for anyone else but I think that most might conclude that the nvidia/unity 2d episode have created an extreme amount of unnecessary downtime.

Thanks for the great essay Guitara!

regards,

ventrical

---

### Post by critin on 2012-08-20
> **ventrical said:**
> Nick,

Thats a masterpiece!

if nvidia is always going to fail (as it has now for the past three releases) then why is the Ubuntu braintrust not providing us with a simple a workable fallback?

Also the removal of Unity 2D just about killed Unity as a whole and left the flagship ubuntu concept dead in the water. 

 You , as sort of our emmissary :) ,have to keep up these excellent essays and drive home these crucial points, especially from  the U+1 point of view. I hope I am not sounding like I am speaking for anyone else but I think that most might conclude that the nvidia/unity 2d episode have created an extreme amount of unnecessary downtime.

Thanks for the great essay Guitara!

regards,

ventrical

I agree with the great eassay, thanks Guitara!

You're speaking for me.  Running ubuntu as it is would be a waste of time.  Waiting for the updates and more news about them.

---

### Post by ventrical on 2012-08-20
My first lecture on 'Introduction to Algorithms' specifically dealt with 'downtime'.  Downtime simply equals 'waste'.  In C, C++ Turbo C, Asm86 etc.. the whole basic and simple idea is to write your programs as swift and economical as possible. Back several decades ago we had to use mainframes and terminals that ran off them. Each student has a booked session and so time had to be shared. To get the maximum production from your session you had to learn to eliminate downtime at all costs. That was the standard back then.  Now there is leisure , slack and walled garden  concepts. "If it's broke- just throw it out and get a new one." geesh ..

lol

thanks!

---

### Post by critin on 2012-08-20
> **ventrical said:**
> "If it's broke- just throw it out and get a new one." geesh ..

lol

thanks!

Oh no, not me.  I must get every last drop of use out of a thing before it's finished.  And even then, I think about what I can do to get it going again.  I thought my old Dell was finished a few days ago, but I decided it wasn't.  It fought me for an hour or so, but here it is.  lol  I'm determined it will run the latest 12.10.

---

### Post by VinDSL on 2012-08-20
> **guitara said:**
> I thought I would post a thread just to gather feedback on this.[...]

So here it is!

Comment here, on the blog, via my inbox -- wherever.
I must have read this, or something like it, 50 times in the past 3 days:

```
The nvidia-graphics-drivers package has been updated to correctly document
that it's not compatible with the new X server.  Thanks to Alberto for the
update!  So this addresses the biggest problem, which is that users who are
using the nvidia driver would get upgraded to a broken desktop (because the
loaded kernel driver wouldn't work with the new X).  Instead, [B][COLOR="DarkRed"]the nvidia
driver package is now uninstallable[/COLOR][/B] in quantal until a version becomes
available that's compatible with the current X server.  This should help
some quantal users being accidentally upgraded to a broken combination of
packages.
```

This is the first time that I got the true meaning of "uninstallable".

I thought "uninstallable" meant you could uninstall it.  Instead, it means that you cannot install it.  Bwahahahahaha!  :D

Anyway, I guess this is indicative of how confusing even simple things can be, in "Cadence Testing".

---

### Post by ventrical on 2012-08-21
> **critin said:**
> Oh no, not me.  I must get every last drop of use out of a thing before it's finished.  And even then, I think about what I can do to get it going again.  I thought my old Dell was finished a few days ago, but I decided it wasn't.  It fought me for an hour or so, but here it is.  lol  I'm determined it will run the latest 12.10.


Bravo for you.  Same here .. I have quantal installs on older machines with only a 600MHz processor!!  Unity 2D worked just great on that. This is the kind of testing I like to do. Get the older machines working. I'm not sure it has anything to do with the Cadence Testing experiment but that which cannot be documented through the bots can be documented here.

  I do , I really do appreciate and admire the efforts of those devs of apport and launchpad and the likes but it just seems that so many bug reports  fade off into the null corners of cyberspace.

 Bright spot is that Ubuntu is always growing and current problems always seem to get ironed out.

---

### Post by smartboyhw on 2012-08-21
balloons: Don't realize that you ARE guitara.... Good post! Maybe we should advance it to weekly cadence testing (instead per 2 weeks) and also testing daily dailies...:)

---

### Post by ventrical on 2012-08-21
> **VinDSL said:**
> I must have read this, or something like it, 50 times in the past 3 days:

```
The nvidia-graphics-drivers package has been updated to correctly document
that it's not compatible with the new X server.  Thanks to Alberto for the
update!  So this addresses the biggest problem, which is that users who are
using the nvidia driver would get upgraded to a broken desktop (because the
loaded kernel driver wouldn't work with the new X).  Instead, [B][COLOR=DarkRed]the nvidia
driver package is now uninstallable[/COLOR][/B] in quantal until a version becomes
available that's compatible with the current X server.  This should help
some quantal users being accidentally upgraded to a broken combination of
packages.
```This is the first time that I got the true meaning of "uninstallable".

I thought "uninstallable" meant you could uninstall it.  Instead, it means that you cannot install it.  Bwahahahahaha!  :D

Anyway, I guess this is indicative of how confusing even simple things can be, in "Cadence Testing".


Hey :)  I just seen that that was an honest to goodness brain fart! :) lol

---

