---
title: "Why apt update via unsecure http?"
date: 2023-11-30
forum: Security
---

### Post by eitanc on 2023-11-30
Hi,

I am at version 20.04.

When I run "apt update", the log shows access to [http://security.ubuntu.com](http://security.ubuntu.com).
Why does this process is using non secure method? why not via https:// ?

---

### Post by TheFu on 2023-11-30
[https://www.debian.org/doc/manuals/securing-debian-manual/deb-pack-sign.en.html](https://www.debian.org/doc/manuals/securing-debian-manual/deb-pack-sign.en.html)

---

### Post by eitanc on 2023-11-30
Thank you @TheFu, I am aware of the packages being signed, but:

1. It is not the only issue, plain http is at risk of many attacks due to it open content, like redirection and injections
2. Using plain http these days is already a bad practice for a long time

I don't see a reason why not migrate all http URLs to httpS.

---

### Post by sudodus on 2023-11-30
We [who help here] at the Ubuntu Forums are volunteers, and cannot modify how updates/upgrades are distributed.

If you have enough time and energy, you can file a bug at [Launchpad](https://launchpad.net/) or start a discussion at [Ubuntu Discourse](https://discourse.ubuntu.com/) where it is more likely that you can reach those who might be able to modify how updates/upgrades are distributed.

---

### Post by eitanc on 2023-11-30
Thank you for directing me!

---

### Post by TheFu on 2023-11-30
There are times and places where HTTPS gets in the way and requires corporations to install a man-in-the-middle cert to ensure they can scan everything for MS-Windows viruses. It can also screw with local caching of repos and packages, at least for the most popular, current, current, tools deployed widely. 

The needs of a single-user system don't always align with the needs of a corporate user with 2K desktops and 50K servers.  Supporting either would be a workaround that could address both types of needs.

People who seek privacy in what they download would likely use a VPN. Of course, that wouldn't prevent certain parts of the world from mandating those keys are provided to the govt. We've seen that plenty of times.
People who seek assurances that what they get is uncorrupted and valid are already addressed.
BTW, HTTPS isn't nearly as secure as people believe, I'm sorry to say.  It is the standard and we all assume it is ok in the latest variants, but we also all know that any but the latest versions have been cracked.

Nothing is ever perfect, so we need to allow for the less-bad to be used rather than seeking perfection.  It is just a matter of time for TLS v1.3.x to be cracked, after all.

---

### Post by Tadaen_Sylvermane on 2023-11-30
I also remember reading somewhere about the network overhead of that many ssl connections for distributing packages. Having to establish an https for each package, then multiply by X number of people downloading at the same time potentially. It was just to much. By contrast the signing method is far more secure and lighter on the servers than an https repository as mentioned above by TheFu.

No system is perfect. And like TheFu said, just because it's https doesn't guarantee a damn thing. You can't trust any single thing to protect you. It's a process like any other security thing. While not perfect the signing method is much more robust than https alone.

---

### Post by ian-weisser on 2023-11-30
> **eitanc said:**
> 
1. It is not the only issue, plain http is at risk of many attacks due to it open content, like redirection and injections
2. Using plain http these days is already a bad practice for a long time

I don't see a reason why not migrate all http URLs to httpS.

This claim pops up regularly.
Use https all you like: Some mirrors do offer https connections.
See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) and [https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

Generally, redirections and injections and other nasties don't work because there are already layers of protections built into apt and built into the repositories. Many of those protections are older than https. The Debian Developers of 20 years ago were not stupid nor trusting. It's a monument to their fiendish deviousness (yeah, I said it) and forethought that apt and https can work harmoniously together.

Here's one reason https is hard to implement:
Mirrors  are donated by volunteers. They come and go. Ubuntu does not control  them, and cannot put their own certificates on them.
This means that  https users who check will see mirror certificates that say "FooCorp" or  "University of Foo" instead of "Canonical" or  "Ubuntu"
And this is where those https good intentions run amok: Folks will be misled that their mirror is a poisoned site or MITM attack. Being good netizens, they will spread their false conclusion, needlessly confusing the entire community.
This https-for-all suggestion has been on the radar of the Ubuntu Mirror Team for 18 years, and no solution yet suggested has been realistic and implementable.

So folks are welcome to use https.
But mirrors are not required to safely distribute using https.
And apt can work safely and securely without https.

---

