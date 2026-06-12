---
title: "Ubuntu Server administration"
date: 2014-12-02
forum: Server Platforms
---

### Post by niki85 on 2014-12-02
Hello all,

I'm new with all this,
Before i have server admin who do all this staff like update/upgrade/mysql migration/server migration ...
right now i want to teach and learn all this staff, and myself administration my linux ubuntu server,
can you suggest me some tutorials, some first commands, steps which i need to learn ?
Can you make some little tutorial about basic server opitmization/administration ?
How optimize apache,nginx,mysql,ffmpeg ...

Thanks.

---

### Post by slickymaster on 2014-12-02
*Moved to the ***Server Platforms*** sub-forum*

You can start here: [https://help.ubuntu.com/14.04/serverguide/index.html](https://help.ubuntu.com/14.04/serverguide/index.html)

Edit: There's also a PDF version of ^^^ -> [https://help.ubuntu.com/14.04/serverguide/serverguide.pdf](https://help.ubuntu.com/14.04/serverguide/serverguide.pdf)

---

### Post by niki85 on 2014-12-02
When i install ubuntu first what i do is,

```
sudo apt-get update && apt-get upgrade
```

and then

```
sudo apt-get install curl
```

and then i install my favorite cp in my case this is vestacp with this cp i get all apache,mysql ... I left out something ?

Thanks.

---

### Post by MAFoElffen on 2014-12-02
Actually-- I would recommend reading Mark G. Sobell's "A Practical Guide to Ubuntu Linux". A text like that will teach you Linux, as related to Ubuntu and it's services, both Desktop and Server editions and services. It's hard for me to recommend a beginner to look at the Ubuntu Server Guide and expect them to understand know what them are really doing, what the pieces all do... and how they fit together and work together. If not planned and configured right, well...

You can always dabble and learn, but easier when you have an explanation of what it all means. There are so many choices of what you can do, but I always figure if you teach someone the how something works, then they can be informed enough to make smart decisions for the direction they need to go, for what they want to do, based on their business needs and goals. On the other side of that, you don't have to be an expert to succeed. If you have a basic understanding of how it's supposed to work, you can surround yourself with people that know how to make those pieces work together, and be able to direct them to that goal.

Just some thoughts. Every can supply advise,. But I like to provide enough info for someone to make their own decisions.

---

### Post by mastablasta on 2014-12-03
depends what this server does but if you look at Zentyal it is pretty easy to understand and plenty of things are done there with GUI.

---

### Post by niki85 on 2014-12-03
I will read this book for sure,
I get ubuntu installed,
I ask what all i need configure before I install e.g. [http://vestacp.com/](http://vestacp.com/) or cp [http://cpanel.net/](http://cpanel.net/) i add above what all command i do before i install, this is good or bad i need to do something more ?
And how optimize apache,mysql ... how i can upgrade mysql e.g. ?

Thanks.

---

### Post by mastablasta on 2014-12-03
cpanel needs to be payed for. A free alternative is Zpanel. this is ment more for hosting (i.e. if you want to rent your server space to others).

what are you trying to do with server? what is your goal?

As for optimisation - again what is your goal? by default Apache comes with some "sane" defaults that are there for a reason. depending on what you want to do with it is how you will then have to change these defaults. for example my host had by default set I think 256MB memory for processing. since I needed more and I had 1 GB assigned I changed the setting to 512MB. it was optimal for my website. I am not sure what would be optimal for you. 

we would need at least some general things you plan to do on this server of yours. is this a company server, file server just a webserver serving a couple of pages? in many such cases cpanel, vestacp and such may be overkill.

mind you if you plan to do hosting you have a lot of reading to do. especially on securing the server and accounts.

---

### Post by MAFoElffen on 2014-12-03
+1 on Zental. If you have a small business and are used to graphical menuing and such... Zental is a way to go. You loose some over-head from the graphical layer, but not any more the other server OS'es. You have another port open on your server, but in a shop, you just adjust for that. 

Zental is presented well, using graphical panels over an Ubuntu Server core. It's done in a way that graphically leads a user to configure and manage that server. I like it and think it is very intuitive. I do recommend it to some of my friends and customers.

I guess what you need to figure out first is to assess your business needs and goals. No sense in rushing into something without that. But then again, I'm a consultant. That's what people pay *me* for.

---

### Post by niki85 on 2014-12-03
Guys thanks for answer really,

I want to host my websites on server, there i will have more websites e.g. 10,
So you not suggest me vestacp ?
I get installed ubuntu or which OS i choose but then i don't know what next i mean i know but don't know if this is good way i make update/upgrade of OS, install curl and then install vestacp, but yes i see there is little to much cpu and i don't know how i can see why is big cpu and how to optimize this ?
I need to learn how administartion server because i want myself do all this without any help because my server admin can't be always here online.

Thanks.

---

### Post by FakeOutdoorsman on 2014-12-03
You mentioned ffmpeg. See the [FFmpeg Documentation](http://ffmpeg.org/documentation.html) and [FFmpeg Wiki](http://trac.ffmpeg.org/wiki/). The wiki contains many articles written by other users to supplement the official docs.

Since Ubuntu does not offer ffmpeg until 15.04 you will have to [download](http://ffmpeg.org/download.html), [compile](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), or use a [PPA](https://launchpad.net/~mc3man/+archive/trusty-media).

---

### Post by mastablasta on 2014-12-05
> **niki85 said:**
> Guys thanks for answer really,

I want to host my websites on server, there i will have more websites e.g. 10,
So you not suggest me vestacp ?
I get installed ubuntu or which OS i choose but then i don't know what next i mean i know but don't know if this is good way i make update/upgrade of OS, install curl and then install vestacp, but yes i see there is little to much cpu and i don't know how i can see why is big cpu and how to optimize this ?
I need to learn how administartion server because i want myself do all this without any help because my server admin can't be always here online.

Thanks.

if you will be the host (I mean others will login and be guests on your server) then you need vestacp, zpanel or cpanel. or rather it will be easier for them to set up their sites and such,

if however you are the host you do not need those. depending on what platform you use to develop your websites - the platforms usually handle multiple websites. i am talking about Joomla, Drupal, Wordpress and similar.

in any case knowledge of administration and securing the server is needed.

if they are all your websites you will also need to read up on web server you plan to use. Apache or ngnix or something else.

---

### Post by TheFu on 2014-12-05
If you just want to get stuff working, search for "perfect server" online.  If you care about security, there is a constant, continuous, learning curve that never ends. Start by reading the sticky posts in the security sub-forum, the sticky posts in the server sub-forum and all the similar questions - lots of people as the same question you are asking here already.

There is no shortcut to answers. Only time, effort, and total immersion will really lead to true Linux Admin knowledge.  People may claim they are secure for years, which just means that nobody has bothered to hack them.  I've been hacked a few times - nothing is as humbling. Expect to be hacked.  A 100% fully patched 14.04 server of mine was hacked in October with just a few services running.  I don't run Java or Php on it and it didn't have a web server (which is a major attack vector).

Be paranoid, have 60+ days of versioned backups. Those are my best recommendations for today.

---

