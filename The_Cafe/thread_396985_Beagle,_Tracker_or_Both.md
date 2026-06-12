---
title: "Beagle, Tracker or Both?"
date: 2007-03-30
forum: The Cafe
---

### Post by daz4126 on 2007-03-30
Hi, 

I've been experimenting with the deskbar applet, which I think uses a search backend. It is a great launcher tool and might mean I can ditch all my shortcut icons on the panel and desktop, allowing me to launch stuff quickly from the keyboard.

I've noticed that there seem to be two search tools - beagle and tracker. Just wondering if one is better than the other (or what are the advantages/disadvantages of each) or if they can work in unison together (and if this is advisable). I have beagle installed, but it never seems to be that good at finding anything - this is contrary to what I hear about it, so am I doing something wrong? I have it indexing my root partition (/) but there doesn't seem to be a front end for indexing, so I don't know where it is up to on that or what it is actually indexing.

If anybody has any advice on this I'd really appreciate it. 

...and does anybody know how to get the dynamic beagle thing in the panel that makes it like spotlight (for mac)?

cheers,

DAZ

---

### Post by jongkind on 2007-03-30
I use Beagle and it works very good for me. This gives a good comparison:

[http://www.osnews.com/story.php?news_id=16984]("http://www.osnews.com/story.php?news_id=16984")

---

### Post by Mateo on 2007-03-30
neither, until there is an applet that shows the results in the applet itself and doesn't have to launch a new application, and doesn't take up 10+meg of memory.

---

### Post by daz4126 on 2007-03-30
What is a guy to do then for searching?

DAZ

---

### Post by Wolki on 2007-03-30
> **daz4126 said:**
> I've noticed that there seem to be two search tools - beagle and tracker. Just wondering if one is better than the other (or what are the advantages/disadvantages of each) or if they can work in unison together (and if this is advisable).

Beagle currently searches more things (emails, chat logs ...) than tracker, but has a considerably higher footprint. I use tracker, since I don't really search for stuff with either (I tend to know where my files are, and with mails and the like I search in the relevant program directly so I won't get tons of useless hits) and thus value the low memory consumption.

I guess you could run both at the same time, though I would doubt it's worth it right now.

> I have beagle installed, but it never seems to be that good at finding anything - this is contrary to what I hear about it, so am I doing something wrong? I have it indexing my root partition (/) but there doesn't seem to be a front end for indexing, so I don't know where it is up to on that or what it is actually indexing.

Beagle has command line status monitoring, I think beagle-status, beagle-stats or something like it. IIRC there are two programs, one for showing the current status of the indexing daemon, one for showing how many objects of each type are indexed.

> ...and does anybody know how to get the dynamic beagle thing in the panel that makes it like spotlight (for mac)?


That's deskbar with the beagle-live-query handler.

---

### Post by Mateo on 2007-03-30
> **daz4126 said:**
> What is a guy to do then for searching?

DAZ

gnome already provides one.

---

### Post by Nikron on 2007-03-30
I use whereis/locate   I tried beagle, but I could never find anything with it..

---

### Post by el mariachi on 2007-03-30
> **Nikron said:**
> I use whereis/locate   I tried beagle, but I could never find anything with it..

Did you index all the files?

---

### Post by daz4126 on 2007-03-30
> **Nikron said:**
> I use whereis/locate   I tried beagle, but I could never find anything with it..

Beagle finds nothing for me either. How do you ensure that all the files are indexed?

DAZ

---

### Post by cody50 on 2007-04-16
I like how beagle shows you all of your stuff when it finds it, organized into categories, but right now it is indexing and is absolutely raping my p3 in this old box I am running. so beware if you have lower end stuff, it bogs it down. I heard tracker would be included in feisty so i'm going to try that.

---

### Post by hanzomon4 on 2007-04-17
I've played with both and I like both. Beagle can index more file types but I didn't miss anything when using tracker. One thing to understand about beagle/tracker vs locate/find is that beagle/tracker searches within files and file meta-data like mp3-tags or the contents of pdf files. 

I forgot how but you can watch tracker and beagle index your files in real-time from the command line, I just don't remember how; sorry :oops: 
My advice don't index root(/)!! Just index your home dir and perhaps /var/log. Use locate or "find" to find system files. One other thing is that you can use beagle in nautilus to quickly find files, you can do the same with tracker but you would need a patched nautilus. You just run your search in a nautilus browser and the results pop up in the same window.  

Now where's Butteblues?

:popcorn:

---

### Post by gnomeuser on 2007-04-17
Beagle works really well for me, I believe C# allows for speedy development and better control of issues related to coding errors. Tracker is low on resources but that's it's only saving grace it seems, it supports nearly nothing, it's search UI is horrible to use. I'd rather currently watch the Beagle developers work on their memory use it seems to be a better product.

Ultimately it shouldn't matter, what we need to support is the Xesam spec which will allow applications to hook into any indexer that supports that standard. That way distributions can pick what product works best for their deployment and applications really don't care about anything but the functionality - the way things where meant to work.

---

