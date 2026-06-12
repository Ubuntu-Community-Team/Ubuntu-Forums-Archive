---
title: "Updating an Older Release"
date: 2017-05-05
forum: Security
---

### Post by BuntuSeriously on 2017-05-05
Greetings.

I have an older version which is no longer supported by the maintainers.  Security is a moderate concern moving forward.

Commonly understood, I have two choices in the matter: I can pay $150 per year to Canonical for ongoing access to updates, or I can ditch the whole thing and start over again with a later version.  I am loathe to get rid of the version which I now have; as it's all set up just the way I want it (maximum usability).

In light of this, I might even do my own updates if needed.  Of note, physical intrusion on this installation is not a concern at all; as it's just me and my system (and no one else cares).

So, looking at the critical ongoing update path from a remote intrusion security perspective *ONLY*, is there some coherent resource out there which would keep a list of relevant updates for previous versions of Ubuntu and its variants?

Any other ideas/input which would give fruitful insight as to the dynamics of a scenario such as this would be appreciated as well.

Thank you!

---

### Post by TheFu on 2017-05-05
> **BuntuSeriously said:**
>  So, looking at the critical ongoing update path from a remote intrusion security perspective *ONLY*, is there some coherent resource out there which would keep a list of relevant updates for previous versions of Ubuntu and its variants?

No. That doesn't exist.  

You can follow CVEs, if you like, but you'll have to manually handle all updates, probably from source. Nobody will be reporting issues with older releases, so very quickly, you'll have a false sense of security that doesn't reflect reality. Doing the patching is more work that you can imagine.  To see the amount of effort, just get a count of packages on the system.

Here's the count on a minimal reverse-proxy server:
```
$ dpkg -l|wc -l
677
``` It could be lighter. I wasn't trying to be too limiting on the packages, but the system has only 1 purpose.

On a VM host:
```
$ dpkg -l|wc -l
1362
```

On a desktop using only 16G of storage:
```
$ dpkg -l|wc -l
2614
```

See the pattern? The problem gets big, quickly.

If you want to keep a working system as-is, fine.  Take it off the network that has internet access and use it only for the 1 or 2 specific reasons you need to keep it around. Lock down the firewall so only communications to 1 other, highly secured, system are allowed.  **For everything else, use a supported, patched, release.**

I've been just finishing up moving my last 12.04 server to 16.04 this week. Hasn't been fun, but for the last 4+ yrs, it has been very stable and very little effort to secure and maintain. That's a pretty awesome track record.  I look forward to 4 yrs more from the 16.04 system.

BTW, there have been remote execution bugs discovered in all kernels since 2.6 was released which were silently patched in Feb of **this year**. It was a big deal.  Any networked Linux system (including android, routers, servers, desktops, media players, whatever) had the issue. There are probably 50-150 other, similar issues that we don't know about.  My 2 yr old home router has the issue and doesn't have any patches available. Had to replace it, though I do use it as an internal WiFi-AP now.

---

### Post by BuntuSeriously on 2017-05-05
@TheFu

Thanks for the helpful, thoughtful insights.

I had hoped there might be some sort of community resource which would alleviate this type of difficulty, but I guess not...

Will be switching over as soon as I can determine the best vector for the next several years ;)

Have a great day --

---

