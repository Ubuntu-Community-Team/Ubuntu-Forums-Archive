---
title: "[Idea] purge low quality software from the repositories, add &quot;landfill&quot; repository"
date: 2007-10-29
forum: Ubuntu Brainstorm
---

### Post by mangar on 2007-10-29
There's a lot of low quality - buggy, crash prone, obsolete or unmaintained.

Why keep them in the repositories? Lets enumerate them, test viability, and if not appropriate for general consumption, move to a "landfill" repository.

candidates:

1. xmms (uses gtk v1), beep-media-player(unmaintained) --> made obsolete by Audacious.
2. gDesklets (unmaintained) --> made obsolete by screenlets.
3. gimmie (at it's current state- stale, crash prone).
4. camorama (unmaintained, crash prone)  --> made obsolete by Cheese.
5. koctave (unmaintained, crash prone).
6. azureus (unmaintained, crash prone) --> made obsolete by deluge.
7. x-cd-roast,  (unmaintained) --> made obsolete by brasero.

---

### Post by smartboyathome on 2007-10-30
> **mangar said:**
> 6. azureus (unmaintained, crash prone) --> made obsolete by deluge.

A lot of people will argue this one. There are people who really like Azureus.

Also, just because software has a few bugs, makes it not viable for the repos? :lol:

---

### Post by ccw on 2007-10-30
> **mangar said:**
> There's a lot of low quality - buggy, crash prone, obsolete or unmaintained.

Why keep them in the repositories? Lets enumerate them, test viability, and if not appropriate for general consumption, move to a "landfill" repository.

candidates:

1. xmms (uses gtk v1), beep-media-player(unmaintained) --> made obsolete by Audacious.
2. gDesklets (unmaintained) --> made obsolete by screenlets.
3. gimmie (at it's current state- stale, crash prone).
4. camorama (unmaintained, crash prone)  --> made obsolete by Cheese.
5. koctave (unmaintained, crash prone).
6. azureus (unmaintained, crash prone) --> made obsolete by deluge.
7. x-cd-roast,  (unmaintained) --> made obsolete by brasero.

You don't have to install them.

---

### Post by ccw on 2007-10-30
> **mangar said:**
> There's a lot of low quality - buggy, crash prone, obsolete or unmaintained.

Why keep them in the repositories? Lets enumerate them, test viability, and if not appropriate for general consumption, move to a "landfill" repository.

candidates:

1. xmms (uses gtk v1), beep-media-player(unmaintained) --> made obsolete by Audacious.
2. gDesklets (unmaintained) --> made obsolete by screenlets.
3. gimmie (at it's current state- stale, crash prone).
4. camorama (unmaintained, crash prone)  --> made obsolete by Cheese.
5. koctave (unmaintained, crash prone).
6. azureus (unmaintained, crash prone) --> made obsolete by deluge.
7. x-cd-roast,  (unmaintained) --> made obsolete by brasero.

Unmaintained?

2. Oct 4:  [http://www.gdesklets.de/index.php?q=node/22](http://www.gdesklets.de/index.php?q=node/22)
4. Oct 9:  [http://camorama.fixedgear.org/](http://camorama.fixedgear.org/)
6. [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by whitewizardcoder on 2007-10-30
> **mangar said:**
> 6. azureus (unmaintained, crash prone) --> made obsolete by deluge.

Azureus is still maintained and is constantly being updated.  They just released a new version called Vuze.  We just need to get the newest version into the repos.

---

### Post by jr.gotti on 2007-10-30
It's a good idea in theory, but will never work due to the simple fact that not everyone shares your opinons on the "quality" of software. What works for you may not work for others and vica-versa. As was said before...simply don't install it. In my opinion repos are supposed to contain as much software as they can. Thats the beauty of Ubuntu (or I guess apt...) Whenever I want something 9 times out of 10 its an apt-get install away. I don't want that changing based on someone elses opinions of the software i needed.

---

### Post by mangar on 2007-10-30
I agree that discussion is necessary, yet some software is obviously  deprecated, for example - beep media player has been discontinued, and been forked into audacious.

About azureus  - the version in the repositories is old, slow and unstable (depends on gcj), shipping it does disservice to ubuntu, as it's shipped broken.

Gimmie, as present in the repositories, is crash prone, so are camorama, koctave, and due to interface problems, gDesklets. 

There is no obvious way to differentiate between high quality software and not-ready, or deprecated software, therefore unmaintained or known as problematic software should, in my opinion, be moved to a repository of software known to be problematic.

---

### Post by kerry_s on 2007-10-30
hey, i use some of that old stuff, it's usually alot less bloated then the new stuff, and sometimes run much better. doesn't matter if it's not maintained if it still does the job. don't be selfish!
also it may be problematic for some people, but may work perfectly for others.

---

### Post by 23meg on 2007-10-30
Also, having an area designated for "low quality software" wouldn't be the best way to get along well with your upstreams.

---

### Post by jmesquita on 2007-11-04
I would take this discussion into a higher ground by mentioning the new Xinerama GTK app introduced by Gutsy. Whoever uses Intel video cards will know what I am talking about.

Why on earth use Xinerama when it dropped support for most of the non Nvidia cards when we have RandR available as well?

I guess this would be an "obsolete" software before it is released, isn't it?

About the repo, I think that maybe a status of the project could be added to the package manager and let the user decide. If the project has lame activity, don't use it, or has a large # or bugs not being assigned to anyone, so on so forth ...

Regards,

João Mesquita

---

### Post by chrisccoulson on 2007-11-05
> 2. gDesklets (unmaintained) --> made obsolete by screenlets.

Screenlets only works for people running Compiz, so it definately hasn't made gDesklets obsolete

---

### Post by zanglang on 2007-11-05
"Low quality" is a bit harsh, a lot of the less used packages you've described is just not as actively updated and featurefull than the others. Like Azureus, for example. The repository version is pretty bad, but Deluge isn't any better either in the stability department.

What would be interesting is if we can integrate user reviews and ratings ala Linspire CNR, or like in the recent Hardy blueprints. Packages that are getting obsoleted by newer, better software can be debtagged "obsolete", "unmaintained", etc. Moving in to a "landfill" just sounds like its getting abandoned from Ubuntu forever.

---

### Post by S3Indiana on 2007-11-06
> **zanglang said:**
> What would be interesting is if we can integrate user reviews and ratings ala Linspire CNR, or like in the recent Hardy blueprints. Packages that are getting obsoleted by newer, better software can be debtagged "obsolete", "unmaintained", etc. Moving in to a "landfill" just sounds like its getting abandoned from Ubuntu forever.The value in a site like [CNR.com]("http://www.cnr.com") is the additional information that's associated with the package (reviews, ratings, forum discussions, package documentation, etc.) that won't be found in the typical package manager...

---

### Post by LaserJock on 2007-11-07
> **S3Indiana said:**
> The value in a site like [CNR.com]("http://www.cnr.com") is the additional information that's associated with the package (reviews, ratings, forum discussions, package documentation, etc.) that won't be found in the typical package manager...

Well, that is basically being discussed for Hardy: [https://blueprints.launchpad.net/ubuntu/+spec/add-remove-software-improvements]("https://blueprints.edge.launchpad.net/ubuntu/+spec/add-remove-software-improvements")

-LaserJock

---

### Post by santiagoward2000 on 2007-11-07
:lolflag: The idea seems very popular!!!
Still, although everyone can use these applications, perhaps it would be nice to have a notice for the ones that are no longer developped.

---

### Post by qamelian on 2007-11-09
> **mangar said:**
> There's a lot of low quality - buggy, crash prone, obsolete or unmaintained.

Why keep them in the repositories? Lets enumerate them, test viability, and if not appropriate for general consumption, move to a "landfill" repository.

candidates:

1. xmms (uses gtk v1), beep-media-player(unmaintained) --> made obsolete by Audacious.
2. gDesklets (unmaintained) --> made obsolete by screenlets.
3. gimmie (at it's current state- stale, crash prone).
4. camorama (unmaintained, crash prone)  --> made obsolete by Cheese.
5. koctave (unmaintained, crash prone).
6. azureus (unmaintained, crash prone) --> made obsolete by deluge.
7. x-cd-roast,  (unmaintained) --> made obsolete by brasero.

I can't speak for all the apps on your list but there are four of the seven that I use frequently and I don't find them crash prone at all. And just because you think an app is obsolete or an app is unmaintained, does not mean that there aren't people who use it for one reason or another. There are a few old, unmaintained apps that I use either because I prefer them to more "modern" alternatives or because they sometimes just work better (for my needs) than apps that have taken their place.

---

