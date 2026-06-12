---
title: "how to use apt-cacher for several distros?"
date: 2009-01-08
forum: Server Platforms
---

### Post by bluelightav on 2009-01-08
Hi Everybody,
I am using apt-cacher since quite a while to upgrade hardy over the LAN. But now I want to add intrepid machines as well. What is the procedure to tell a) the server that there are 2 sets of archives and b) the clients. All the tutorials I found only set up one distro, never 2. Does somebody know how to do this?
Any help appreciated.

---

### Post by bluelightav on 2009-04-06
No special configuration needed. You just work with 2 different sources list (which you anyway do) and it works fine.

---

### Post by kpoole on 2009-04-07
You replied in thread to a private mail so others might be confused by what prompted the old thread to pop-up again.

But, on the basis of your saying it was simply a matter of pointing the Intrepid machines at the Hardy apt-cacher I took the chance and pointed an Intrepid machine at my Hardy apt-cacher (Actually at a backup Hardy apt-cacher.  I'm not completely impulsive. :-) and did an apt-get update.  I then checked the /var/cache/apt-cacher/headers directory and see there are a new set of Intrepid header files there.  And, since the different Ubuntu versions will be looking for packages listed in their particular header files not the latest version that happens to be available this will likely work just fine.  This might even be better than what I was thinking of since if they do backport a particular package from Intrepid to Hardy so that it becomes common to both it will already be there waiting for whichever client needs it after the other requests it.

At any rate, if it really does continue this simply then I have a nice little apt-cacher for the next few years and versions since I've got the apt-cacher setup on a Hardy Heron server which will still be supported itself for a while yet.  (I might have to resize the partition holding /var/cache though.  This might get a little large after a while.  The Hardy apt-cache is almost a gig now.  Perhaps there's a way to clean out older packages that will no longer be asked for. :-)

(yeah, I just merged the Intrepid apt-cacher cache with the Hardy cache and we're up at 2 gigs all of a sudden.  Let's see, 4 more years of Hardy server support, 8 more distros in general, 8 or 10 more gigs but maybe not so bad if I upgrade at the next LTS in 2 years or so.  :-)

Thanks for the info.  If this really continues to work so well I'll update my other post with this info as well.

---

