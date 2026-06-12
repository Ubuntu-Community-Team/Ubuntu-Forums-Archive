---
title: "Need to use apt-proxy with Warty to feed Hoary machines?  Heres how"
date: 2005-04-02
forum: Server Platforms
---

### Post by moopere on 2005-04-02
So, anyone who only uses stable distributions for servers (ie, warty) will know by now that their warty server will not properly feed hoary development boxes by use of apt-proxy.

With only days left until hoary ships I imagine that things on this front are unlikely to change.

The problem is that hoary is using apt 0.6.x and bzip/gpg signed packages whereas warty uses the (now) older gzip/non signed packages.  Warty ships with apt-proxy v1.3x which is not able to correctly feed bzip2 packages (need apt-proxy v1.9x+ to do this).

This would be a serious backwards compatability flaw in ubuntu I guess if it weren't for the fact that apt-proxy is not in main....

Well, then, why not take a risk and move from an unsupported warty apt-proxy to an unsupported hoary apt-proxy?  The answer is that apt-proxy is now written in python (arrgghh!!) and hoary is fully python 2.4 whilst warty is python 2.3.   Upgrading apt-proxy in warty from hoary bumps python 2.3 out and puts python 2.4 in - pretty drastic and I've found during experimentation that this does not work at all well.  Probably better to upgrade the warty server to hoary.

However, I am not that happy with the prospect of churning servers over every 6 months because of backwards compatability errors...

The good news is that Debian does not really have an unsupported package section (well, not in the same sense that ubuntu does), and as a result they need to take such backwards compatability breakages rather seriously.

Thankfully therefore, Debian unstable (and sarge too!) is still at python 2.3, and grabbing apt-proxy v1.9x from there has few dependencies, does not change the python revision and works a treat.

My Wary server is now functioning again to fully serve my local machines (Debian, Warty & Hoary) and doesn't require me to move up to Hoary until I'm ready to do so (and frankly, I hate versioning servers more than about once every three years or so...security concerns aside of course).  

Cheers,
Craig

---

