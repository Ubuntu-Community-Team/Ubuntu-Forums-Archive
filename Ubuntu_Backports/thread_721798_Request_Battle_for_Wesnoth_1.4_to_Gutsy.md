---
title: "Request: Battle for Wesnoth 1.4 to Gutsy"
date: 2008-03-11
forum: Ubuntu Backports
---

### Post by Taxi on 2008-03-11
Version 1.4 of Battle for Wesnoth was just released on March 8.  It's a fairly major release with a lot of new functionality and bug fixes, so I think it's worthy of backporting - plus you backported 1.2.8 :).

Anyway, sorry, but I don't have a Launchpad account and don't want to sign up for one at the moment.  Maybe sometime soon, but I just wanted to put this out there since I was keeping an eye on the Wesnoth development efforts.

EDIT: Oh yeah, and I did check Launchpad first to make sure it wasn't already requested.

---

### Post by firefeather on 2008-03-11
I'm surprised to hear 1.2.8 was backported. I though they didn't backport stuff unless it was a major bugfix or security update. You could try getting it on [getdeb]("http://www.getdeb.net/app/The+Battle+for+Wesnoth") in the meantime.

---

### Post by Taxi on 2008-03-12
> **firefeather said:**
> I'm surprised to hear 1.2.8 was backported. I though they didn't backport stuff unless it was a major bugfix or security update. You could try getting it on [getdeb]("http://www.getdeb.net/app/The+Battle+for+Wesnoth") in the meantime.

Thanks for the reply, but I still think it's a pretty ideal candidate for backporting.  Backporting is a different and completely separate process from the stable release and security updates.  In fact, number four [_here_]("https://help.ubuntu.com/community/UbuntuBackports#head-37a793d5ee480081f1c9f19e07fcdcdae5e6a9ed") specifically excludes bug and security fixes from justifying requests for the Backports project, as there are already processes in place to integrate those patches into the stable releases of the applications.

So anyway, I just wanted to put in the request.  If it's deemed unworthy or goes unnoticed since I didn't use Launchpad I'll definitely look into using getdeb.  Thank you for the link.

I'd also like to thank the Backports team.  In my opinion the Backports repository is indispensable due to the justified tendency for FOSS to be released pre-1.0 and the active development much of that software goes through.  Keep up the good work!

---

### Post by Taxi on 2008-03-12
It looks like someone requested it in Launchpad a few hours ago: [https://bugs.launchpad.net/gutsy-backports/+bug/201443](https://bugs.launchpad.net/gutsy-backports/+bug/201443)

Thank you to that person and I second the request!

---

### Post by firefeather on 2008-03-13
> **Taxi said:**
> Thanks for the reply, but I still think it's a pretty ideal candidate for backporting.  Backporting is a different and completely separate process from the stable release and security updates.  In fact, number four [_here_]("https://help.ubuntu.com/community/UbuntuBackports#head-37a793d5ee480081f1c9f19e07fcdcdae5e6a9ed") specifically excludes bug and security fixes from justifying requests for the Backports project, as there are already processes in place to integrate those patches into the stable releases of the applications.

Wow, sorry, I didn't know about that at all. Thanks for helping me understand that.

---

### Post by Taxi on 2008-03-30
It looks like v1.4 has been backported for amd64 and powerpc, but not for i386: [http://packages.ubuntu.com/gutsy-backports/games/](http://packages.ubuntu.com/gutsy-backports/games/).

Is the procedure to do them one at a time or is this an error?  Will the campaigns be backported eventually as well?  They have also added new official campaigns that would be worthy of backporting; see [http://packages.ubuntu.com/hardy/games/](http://packages.ubuntu.com/hardy/games/).

It looks like the backport is considered finished on Launchpad, though...  ?

Thanks for any info.

By the way, while looking through the gutsy-backports/games page I noticed that the latest version of Pioneers has been backported.  It was probably done a while ago; I just hadn't noticed or updated automatically since the package names had changed.  Thanks for that backport, too!

---

### Post by Taxi on 2008-04-03
I just got the updates.  Thanks, folks!

---

