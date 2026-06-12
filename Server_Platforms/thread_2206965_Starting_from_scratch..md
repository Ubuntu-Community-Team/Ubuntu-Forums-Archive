---
title: "Starting from scratch."
date: 2014-02-21
forum: Server Platforms
---

### Post by Darren_Scott on 2014-02-21
Hi folks, 
I have a question if I may. My SO and I run a small site that talks about disabled technology and other articles and news. It is a diversions eMagazine. Fogboundworkshop.

Now as we are both disabled and live in the UK anyone that lives here knows that the squeeze on disabled peoples finances is a big things right now. So we want to keep runing the site but need to bring it to home. Problem number 1 is We both do not know very much about linux at the moment so it will be a learn as we go. And problem 2 I was reading over the ubuntu server info and was not sure if doing it server wise or doing the cloud server would be best. 

So asking in here from people that know is the best source for finding out. 

Any help is truly appreciated 

Regards
D.....

---

### Post by Frogs Hair on 2014-02-21
Hello and Welcome Moving thread to server platforms.

---

### Post by dragonfly41 on 2014-02-21
Although this has been moved to servers sub-forum .. it might help if you can expand 
on your business model and constraints. 

And forming your business plan will help in applying for grants.

Planned online service?

Business or hobby?

Paying users?

Revenue flows hoped for?

Timescale to get to market?

Your technical knowledge for programming your own portal or would you prefer to pay for SaaS (Software as a Service)?

Any local help from enterprise centres supported by U.K. gov initiatives for disabled support?

...

Then you can choose the technology (local or cloud servers are only part part of the jigsaw puzzle) to match your goals and constraints.

---

### Post by Darren_Scott on 2014-02-22
Hi Dragonfly4

We already have everyting worked out for this and have done this a while go. The main question was basically which would be best the server version or the cloud version to run the site at home? It is just myself and my partner writing articles. 
I have a site already up and keeping it runing is my job and so far I am doing ok. But then again it is not a hugely technical site as some are. 
D//

> **dragonfly41 said:**
> Although this has been moved to servers sub-forum .. it might help if you can expand 
on your business model and constraints. 

And forming your business plan will help in applying for grants.

Planned online service?

Business or hobby?

Paying users?

Revenue flows hoped for?

Timescale to get to market?

Your technical knowledge for programming your own portal or would you prefer to pay for SaaS (Software as a Service)?

Any local help from enterprise centres supported by U.K. gov initiatives for disabled support?

...

Then you can choose the technology (local or cloud servers are only part part of the jigsaw puzzle) to match your goals and constraints.

---

### Post by dragonfly41 on 2014-02-22
I did some homework and twigged your profile from here .. 

[http://stats.kwsn.net/team.php?proj=wcg&teamid=16688](http://stats.kwsn.net/team.php?proj=wcg&teamid=16688)

It's just that I've helped other SME's in the past (in an Enterprise Centre) and often startups don't write down the goals they hope to achieve.  Just an 'elevator pitch' helps.

But if you've already jumped through those hoops I guess you're just asking how to run a Ubuntu server from home base?

There are *so many ways* of responding to your "starting from scratch" question .. so here is just a cocktail of ideas.

...

If you are writing articles then let's start with some authoring tools before we get to the server.

Perhaps writing e-books or other material which you can upload to your server?

Take a look at Scribus.

[http://www.scribus.net/canvas/Scribus](http://www.scribus.net/canvas/Scribus)

You can then publish e-books or PDF's.

There is another writing tool here .. Scrivener linux beta is free

[http://www.literatureandlatte.com/forum/viewforum.php?f=33&sid=7f1f4ce6723163f5e434235cb8772cba](http://www.literatureandlatte.com/forum/viewforum.php?f=33&sid=7f1f4ce6723163f5e434235cb8772cba)

...

Now you might wish to try serving content from home from a home based server.  But you would have to consider all the operational and security considerations which a SaaS or cloud based raw server might better cover for you leaving you to do the creative writing. And check any constraints from your ISP.   Home based servers (on port 80) may be blocked by your ISP.

Check your localhost server security holes from here ... 'Shields Up' test.

[https://www.grc.com/default.htm](https://www.grc.com/default.htm)

If you want to get to grips with a PHP MVC (PHP+MySQL) framework then you could look at [http://www.laravel.com](http://www.laravel.com) .. but be warned that there is a very steep learning curve which I feel may not be for you.

Take a look at tutorials in [http://www.culttt.com/code/](http://www.culttt.com/code/) before you jump into laravel MVC.

And 

[http://www.laracasts.com](http://www.laracasts.com)

[http://daylerees.com/composer-primer](http://daylerees.com/composer-primer)

[http://www.codeforest.net/laravel4-simple-website-with-backend-1](http://www.codeforest.net/laravel4-simple-website-with-backend-1)

...

If you are just writing blog articles on your server rather than programming then you can use an existing framework offered by any of these ...

[http://www.digitaltrends.com/social-media/best-free-blogging-sites/](http://www.digitaltrends.com/social-media/best-free-blogging-sites/)

Or to minimise programming needs you can setup an account in [http://www.drupalgardens.com](http://www.drupalgardens.com) which is drupal based.   You can start with a free site for a while provided you keep logging in regularly.

Or there is the free tier service from Amazon which you can experiment with .. but again quite a bewildering learning curve.  [http://aws.amazon.com/free](http://aws.amazon.com/free)

Another recommended site here ...
[http://www.digitalocean.com](http://www.digitalocean.com)

Ideally you should have a localhost environment for development then a workflow to upload your content to a remote server.

This flow from localhost -> staging server -> production is shown at [http://www.fortrabbit.com](http://www.fortrabbit.com) which is compatible with laravel.

[http://blog.fortrabbit.com/multi-stage-deployment-for-website-development/](http://blog.fortrabbit.com/multi-stage-deployment-for-website-development/)

Get yourself github and bitbucket accounts.

Also dropbox account for sharing. and or Ubuntu One account.

These ideas just scratch the surface.

...

To summarise answer to your **problem 1**

Just post questions in this forum.

To summarise answer to your **problem 2**

Keep *both* options open ... home server and cloud server. And also SaaS such as [www.drupalgardens](www.drupalgardens) where the server is managed.  But do keep backups of your creative work so that you can easily migrate to different servers.

There is no "best" solution.

Exploit free trials.

Stay with Ubuntu 12.04 LTS which will be supported until 2017. Not sure if you can support 32 bit or 64 bit architecture but research that.

If you still prefer to run your server from home then take a look at this thread ..

[http://ubuntuforums.org/showthread.php?t=2204064](http://ubuntuforums.org/showthread.php?t=2204064)

I added [https://ngrok.com/](https://ngrok.com/) as an option.

Investigate grants for your enterprise.

...

I hope that this rambling over a number of subjects covers some of the bases.

I suggest that you start with Scribus for authoring quality e-books to be uploaded.

Good luck.

---

