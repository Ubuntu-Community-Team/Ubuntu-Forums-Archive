---
title: "All Wordpress requests take 10-11 seconds no matter what"
date: 2017-01-25
forum: Server Platforms
---

### Post by courtney2 on 2017-01-25
I have a wordpress site that I have set up right now, and I can't for the life of me figure out why, but when I try to connect to the server for the first time, click a link to another page, or click on anything on the admin page each request consistently takes 10-11 seconds, then loads almost immediately after that. Basically, a horrible time-to-first-byte for each request. I think this is directly related to something with Wordpress because I have Nextcloud on the same network and computer (in a separate VM) and that time-to-first-byte is usually below 200ms. What's causing this? I've tried caching via WP plugins, Redis cache, disabling various plugins...I also tried changing to a lighter theme and that didn't fix it either. What could possibly be causing this constant 10 second delay? My webserver is Nginx

---

### Post by Habitual on 2017-01-26
sounds like caching. local.
New site gets all of it and stores it in cache.
Successive visits to same URI and you get cached content.
Try Shift+Reload and see if it acts like the first visit...and report, please. Thanks.

---

### Post by courtney2 on 2017-01-26
Hi Habitual,

Doing what you said still takes the 10 seconds it takes for a new connection

---

### Post by Habitual on 2017-01-26
sorry, I'm out of ideas.

---

### Post by SeijiSensei on 2017-01-27
How much memory does the server have?  Perhaps MySQL is memory-starved and needs to dredge up records from the disk cache?  That's the only thing I can think of.

Also one other test you could try is directly entering the URL of a graphic embedded on one of the pages after clearing your browser cache.  Apache can sometimes be slow with graphics; I've not used nginx.

I assume the site has no links to off-site content which needs to be displayed.  If so, then your performance is dependent on the speed of the off-site servers.

---

### Post by courtney2 on 2017-01-31
Memory? Whatever the max is for LXD containers :) so not sure. MySQL shouldn't be starved because I have MySQL on another VM (or container if you will) and it isn't even complaining.

Here are my findings. It is absolutely a Wordpress issue I'm having, or something related to it. I created a test.php file that measured the load time as well as sending me a 3MB picture. Took 5 seconds on a 4Mbps download speed. Page generated in 0.694 seconds.

There are calls to googleapis and gstatic, which I would like to banish, then I might try a Redis cache or another suggested caching method. I also noticed a couple of my pictures are being downscaled. Perhaps that image is being downscaled on each visit too?

---

