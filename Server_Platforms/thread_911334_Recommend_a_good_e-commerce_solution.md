---
title: "Recommend a good e-commerce solution?"
date: 2008-09-05
forum: Server Platforms
---

### Post by windependence on 2008-09-05
Well I'm usually giving out advice not wanting it but I have picked up lots of good ideas from some people here and I thought I would ask.

I have a client that is currently using OS Commerce for his e-commerce package. I don't know much about it as I usually run message boards and blogs, but he says they have problems updating the products because it's too complicated. I am moving the site to my servers soon and initially we will be using his current solution, but I wanted to get some suggestions from people that have used other packages.

What package do you like, and why? How is the install? Can your client update the product or do you do that?

I am honestly probably going to be running the site on FreeBSD, but the host box will be Ubuntu server with VMware. I would consider running Ubuntu server or JeOS as the guest OS if the ecommerce package is good enough to warrant it and won't run on FreeBSD.

Suggestions?

Thanks!

-Tim

---

### Post by cdenley on 2008-09-05
I was under the impression that oscommerce was a very easy-to-use solution. I think an alternative I've heard mentioned before is zencart, but I don't really have any experience with it.

I think oscommerce is the most common, but there hasn't been much development with it lately. Their most stable release doesn't seem to support php5.

---

### Post by volkswagner on 2008-09-05
If you don't get positive feedback here.  I asked the same question at opendesigns.org.  It is a dated thread, but may be worth your time.  

I have not had any experience, as I am still using paypal's solution.  I am still hoping for greater sales volume.  I just started to use paid hosting with a dedicated ip, so hopefully I am on my way to better SEO.



[http://www.opendesigns.org/forum/discussion/1484/opinions-wanted-for-shopping-cart-site/#Item_7]("http://www.opendesigns.org/forum/discussion/1484/opinions-wanted-for-shopping-cart-site/#Item_7")

---

### Post by father time on 2008-09-05
Message Deleted.

---

### Post by dj 2501 on 2008-09-05
Give Cubecart a try. It has a very easy to configure backend yet its powerful enough to integrate into the major credit card processors out there.

Editing the layout is also a snap.

You can have your client up and running within minutes and start adding products.

One question though. How come freebsd and not Ubuntu?

---

### Post by windependence on 2008-09-05
> **dj 2501 said:**
> Give Cubecart a try. It has a very easy to configure backend yet its powerful enough to integrate into the major credit card processors out there.

Editing the layout is also a snap.

You can have your client up and running within minutes and start adding products.

One question though. How come freebsd and not Ubuntu?

Thanks for the suggestion! I'll set up a VM and give it a try.

RE: FreeBSD, I'll probably start a flame war, but ther is no comparison between any Linux distro and *BSD. IMHO, *BSD is:

More secure

A LOT less bloat

Better memory management

A real OS, not just a kernel, integrated userland and kernel (I can elaborate, but it would be a long post)

It's true Unix

UFS2 with softupdates. No need to worry about your data after a crash. Support for large filesystems (2TB) 

bg_fsck. No waiting to boot because your FS will get checked in the background while the system is live. 

ACL and MAC framework for fine-grained user/resource control. 

GDBE encrypted disk subsystems, supports encrypted swap, FS, etc. 

Better SMP support.

There are probably many more I have forgotten to list but the main thing is it just works. If you enjoy tweaking your system all the time and you want a Unix-like OS, Linux is for you. If you are Yahoo! or a porn site, you run *BSD. When I get into my car, I just want it to work. Same with my server OS.

Here is another reason:

```
tiburon# uptime
 8:10PM  up 123 days,  2:19, 1 user, load averages: 0.02, 0.03, 0.00
```

Uptime would be more if I didn't just replace a fan. This is my web server box where one site I have gets 13,000 page views per day, and over 5 million hits per month.

For a more good objective advice on the differences, this is a great article:

[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

And another but not as good:

[http://www.articlesbase.com/operating-systems-articles/linux-vs-bsd-250471.html](http://www.articlesbase.com/operating-systems-articles/linux-vs-bsd-250471.html)


Before I get flamed, I just want to state that I am in no way bashing Linux, it's a great OS, and I hope someday it crushes Windoze. I am just stating what my and other's experences have been using the two operating systems. There is a reason if you go out to [http://uptime.netcraft.com/up/today/top.avg.html](http://uptime.netcraft.com/up/today/top.avg.html), you'll see *BSD uptimes in terms of YEARS.

Don't mean to bore you but you asked. :)

-Tim

---

### Post by volkswagner on 2008-12-11
> **windependence said:**
> Thanks for the suggestion! I'll set up a VM and give it a try...............

-Tim

Wondering what you decided.  I would like to get an inventory based site up (less than 200 items).  Currently I am using Paypal shopping cart.  It does not have any inventory management and is not very professional IMHO.

So, what did you decide and why?

Peace,
Eric

---

