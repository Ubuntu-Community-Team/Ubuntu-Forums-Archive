---
title: "Is a weekly automatic update a good idea on a server?"
date: 2008-10-23
forum: Server Platforms
---

### Post by ian_hawdon on 2008-10-23
Hi there,

I finally got round to upgrading my Gutsy Gibbon server to Hardy Heron (just before the next release!) and everything went smoothly! No longer do I have to worry about end of life... well until 2013! But I don't the my 10 year old server will still be functioning by that point!

Anywho, when I was running Gutsy, I wasn't updating the packages (I know, kinda risky!) I was thinking of a low maintenance way of doing this now I have 4 1/2 years (give or take) of support!

I read you can add the following command as a cron command:

```
apt-get update && apt-get --yes upgrade
```

and doing this on a weekly basis sounds ideal, but is this really the best solution, or should I be more selective on what I choose to update?!

With the 31st of October fast approaching, maybe some good server update horror stories are in order :)

---

### Post by lykwydchykyn on 2008-10-23
It really depends on
 - what you're running
 - how disasterous it is if it goes down
 - how much you trust Ubuntu

I use a package called cron-apt to do nightly updates on a lot of my Debian/Ubuntu servers, but only the non-mission-critical ones and only using the stable repos.  The nice thing about cron-apt is that I can configure it to email me when it actually updates.

---

### Post by ian_hawdon on 2008-10-27
> **lykwydchykyn said:**
> It really depends on
 - what you're running

I am running a small LAMP server, which actually doesn't meet the minimum 300MHz Processor requirement (266MHz), but actually runs remarkably well!

It hosts my website ( [http://www.op-ezy.co.uk](http://www.op-ezy.co.uk) ), and another site for someone else (since then, it makes it a bit more important that the server should be stable)

>  - how disasterous it is if it goes down 

Well, if my site goes down, it's not much of a problem for me, as the server is in my house, I can sit in front of the terminal and punch keys till it works again ;-) but the other person using the server for hosting, doesn't have root access, and doesn't know how to use any GNU/Linux command line environment!

>  - how much you trust Ubuntu 

Well, their updates seem a lot more stable than the likes of openSUSE, and far more easier than the likes of Slackware! I still like the sound of an automatic weekly update, all the repos on the server are just Ubunutu's original stable ones, so I'm guessing not too much can go wrong!

> I use a package called cron-apt to do nightly updates on a lot of my Debian/Ubuntu servers, but only the non-mission-critical ones and only using the stable repos.  The nice thing about cron-apt is that I can configure it to email me when it actually updates.

The final thing is, if the update contains a kernel, is there a way to let the system automatically reboot to take advantage of it?

---

### Post by lykwydchykyn on 2008-10-27
Dunno about the last question; you could probably hack something together, but I don't think cron-apt has an option for that.

I'd say you should be fine upgrading automatically.

---

