---
title: "Can a 10.04 LTS server still be upgraded?"
date: 2016-07-07
forum: Server Platforms
---

### Post by rhanthony2 on 2016-07-07
10.04 LTS Lucid is end of life, but I've just discovered a machine running it still. Is it possible to still upgrade it from there, or does EOL now mean that route is cut off? I am trying to avoid a whole rebuild and migration of everything... any chance?

---

### Post by uNoubu8a on 2016-07-07
Hi,

> When an Ubuntu release reaches its “end of life” it receives no further maintenance updates, including critical security upgrades. We highly recommend that you upgrade to a recent version of Ubuntu at this point.

From [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)



Cheers
404

---

### Post by QIII on 2016-07-07
Moved to Server Platforms.

---

### Post by DuckHook on 2016-07-08
> **rhanthony2 said:**
> 10.04 LTS Lucid is end of life, but I've just discovered a machine running it still. Is it possible to still upgrade it from there, or does EOL now mean that route is cut off? I am trying to avoid a whole rebuild and migration of everything... any chance?Welcome to the forums rhanthony2.

My memory does not go as far back as 10.04 anymore, but it reached EOL more than a year ago. When releases reach EOL, Ubuntu moves the repositories into an archive site and they are no longer available in the regular sites or mirrors. I believe there is usually a grace period, but I am almost certain that it is measured only in one or two months, and you would be well outside of that now. Going only by memory, I believe that you cannot upgrade unless the repository for the old version is reachable and readable. I suppose you could try changing your sources.list to point to the archive site but, frankly, I have never tried upgrading like that and at best it would be a high-risk procedure.

Moreover, it would not be possible for you to upgrade to the current release in one fell swoop. You can upgrade 12.04 directly to 14.04 and 14.04 directly to 16.04, but I believe that LTS to LTS upgrades only started with 12.04, though I am not sure about this. If it turns out that 10.04 must go through 10.10 then 11.04, etc, you would almost certainly run into a failed upgrade somewhere along the way.

Therefore, no matter how you look at it, you will need to backup your data before embarking on a highly risky upgrade adventure that has a remote chance of success. Even if you can go from LTS to LTS, there is no point stopping at 12.04 since you will be staring at the same problem is just a few months.

My recommendation: bite the bullet, make a provably restorable backup, then install 16.04 from scratch. You will likely spend less time installing apps and rebuilding your configs than trying to hunt down obscure little breakages that will drive you crazy. Moreover, you will get a pristine system without a lot of inherited obsolete settings and configs.

If you want to try the upgrade route on the basis that you've nothing to lose since the alternative is a fresh install anyway, then make sure your backup is restorable and your data is provably secure, make the necessary changes to your sources.list, do a final update, cross all your fingers and toes, hold your breath, knock on wood, and go for it.

---

### Post by mastablasta on 2016-07-09
instructions for upgrading End of life releases: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

upgrade at least to 14.04. 16.04 has systemd and if you have scripts and such they might need some changes. while 14.04 is still supported until 2019 and it should give you enough time to prepare for next upgrade.

---

### Post by MAFoElffen on 2016-07-09
DuckHook and mastablasta are both correct...

There is another, not recommended solution that I've used as an IT Professional to get old EOL versions to current, but is not for the light of heart and/or someone that does not have a good grasp of Linux. If need be I'll share that, but it involves going to external archives of repo's... and you have to do a few work-arounds to get there.  

With the time involved in doing it that way (Some Customers wanted to go that way ... I did an 8.04 to 14.04 for someone, with backups at each LTS step.), it is faster and easier to do what DuckHook suggested: (That is what I would recommend.)
- Back up what you have, so you can transfer your data, configs and scripts.
- Export a package list, so you have an idea of the pieces to recreate where you want to be.
- Install a fresh, clean, current LTS (such as 16.06).
 -- Install the services you need.
  --- Update the config's, using your old as reference. Some options may have changed or didn't exist before.
  --- Replace phased out packages with their replacement services
  --- Update your scripts to reflect any new framework changes
  -- if you had custom startup init.d scripts, they may have to be updated them for systemd compliance. Most mine still worked, just gave warnings in the sys log... until I updated them.
-- import your data.

That actually looks longer and harder than it is in reality. Like I said, that actually is shorter and easier than doing multiple release upgrades (LTS to LTS, until current). My experience, more than 50% reduction in time, between the two methods.

EDIT-- Note that I said "install services", instead of packages. Some of the specific packages evolved and either went away or changed into something else. There are still the same "services" out there, but it may not be what it was named 6-8 years ago. Things change.

---

### Post by rhanthony2 on 2016-07-25
Just so I don't leave you all hanging... I've decided to stand up a 16.04 beside this machine, and install all current packages (or replacements), and then transfer over configs and settings for each via ssh/scp. Then I can test each service as I need to, and prove out a good replacement. After that, put the 10.04 out to pasture and I'm done.  I *might*, for giggles try to upgrade the 10 to a 16 just to see if I can after that, and after it no longer matters to production. If I get that bored I'll let you know how it goes!

---

### Post by DuckHook on 2016-07-26
If you believe your problem to be solved, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

