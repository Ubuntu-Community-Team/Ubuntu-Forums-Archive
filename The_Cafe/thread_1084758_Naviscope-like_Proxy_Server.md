---
title: "Naviscope-like Proxy Server?"
date: 2009-03-02
forum: The Cafe
---

### Post by Rangelus on 2009-03-02
I'm wondering if something exists that has similar functionality to the old windows program naviscope.  For those who don't know of it, it's a simple proxy server that has several features I like.  The ones I am most looking for are:
GUI which lists all connections being made through it, with the ability to cancel those connections.
Ad-blocking
URL grabbing (for grabbing files from youtube, etc)

Note, I'm not looking for an anonymous proxy (I'd just use tor if I was), just a simple http proxy that hopefully has the features above.

Thanks in advance.

ETA: I'm using intrepid ubuntu, obviously. :)

---

### Post by Rangelus on 2009-11-15
I hate to both resurrect an old thread, and also shamelessly self-bump, but I'd still love an answer.  Every so often I go google-hunting for a naviscope replacement, but I've yet to find anything suitable.  Perhaps the knowledgeable people here can help?

---

### Post by The Real Dave on 2009-11-15
I know [Squid]("http://www.squid-cache.org/") can probably do everything you list, but not with a GUI that I'm aware of. I use Squid on my computers just to cache, but its extremely configurable, if your willing to work with the config file. The config file is really well documented though, its 5000 lines long, but most of that is explaination :lolflag: Google, it theres plenty of tutorials, and you can install it through the repos with 

```
sudo apt-get install squid
```

Seems there is some sort of stats utility 

> How do I see system level Squid statistics?

The Squid distribution includes a CGI utility called cachemgr.cgi which can be used to view squid statistics with a web browser. See ../CacheManager for more information on its usage and installation. 

I'm gonna install it and see what it's like :)

---

### Post by Rangelus on 2009-11-16
> **The Real Dave said:**
> I know [Squid]("http://www.squid-cache.org/") can probably do everything you list, but not with a GUI that I'm aware of. I use Squid on my computers just to cache, but its extremely configurable, if your willing to work with the config file. The config file is really well documented though, its 5000 lines long, but most of that is explaination :lolflag: Google, it theres plenty of tutorials, and you can install it through the repos with 

```
sudo apt-get install squid
```

Seems there is some sort of stats utility 



I'm gonna install it and see what it's like :)

Thanks for the suggestion.  I took a look at squid, and it does a lot of things that Naviscope does, (precache, logs, etc).  It's definitely a nice little tool, and I'll be keeping it installed.  Unfortunately, the one thing that's missing (a GUI, more on that in a bit) is basically the most important feature for me.

In way of explanation, the feature I find the most useful with Naviscope is a bar which pops up, listing all connections (i.e. all objects being downloaded) through your browser.  So, for example, it will list all images, icons, scripts, etc, in real time, as they are being downloaded.  This bar is interactive, so that you can click any item to cancel that specific download.  This is mainly useful when grabbing .flvs from youtube and the like, as Naviscope lists the real URL of the file.

Yes, I know I can use one of the hundred or so FF addons which provide embedded video downloading, and yes I could just look at the log file from squid to see what was downloaded after the fact.  That is basically what I am doing right now, but I feel there aught to be a replacement for Naviscope, since it's a handy little tool.

If I had any kind of coding experience, I would attempt to write my own.

---

