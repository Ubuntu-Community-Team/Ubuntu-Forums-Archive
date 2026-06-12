---
title: "iTunes Server"
date: 2013-01-04
forum: Server Platforms
---

### Post by OliverHaslam on 2013-01-04
I know iTunes can be run using Wine, but it can be a bit flakey from what I hear. What I want to do though is just create an ITunes server, so something that can serve iTunes content to an Apple TV.
 
Is there either A) a solid way of running iTunes on Ubuntu, or B) a hacky way of making Ubuntu serve content to an Apple TV?
 
 
Cheers.

---

### Post by kpholmes on 2013-01-05
Theres a couple different ways. 

You could run windows xp in a small VM and with guest additions installed load your media to itunes. Keeps 1 copy of your music, and you can give it its own network card too for faster networking.

Or you could get vuze plus. It can transode and share to tons of media devices, apple tv, xbox, roku. Vuze is a java app so it works on all operating systems that can java, linux included.

I'm sure theres more ways, free and open source , but here's two solid ways ive done before.

---

### Post by cariboo on 2013-01-05
Seeing as Apple Tv is closed source, there isn't much we can do about it.

It may be a better idea to modify Apple TV to be able to use all your different media types.

Have a look at this [howto]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_on_Apple_TV_2"), it involves installing XBMC on your Apple TV device.

---

### Post by kpholmes on 2013-01-05
That would be the most ideal method but cant be used on the latest apple tv 3.

---

### Post by OliverHaslam on 2013-01-07
Thanks for the replies. The Windows VM method was one that I had in the back of my mind, yeah. May just go for that. 


Cheers.

---

### Post by volkswagner on 2013-01-07
Not sure what VM environment you are using, but I have a similar setup using Citrix XenServer.  My windows VM had no sound hardware so I installed [Virtual Audio Cable]("http://en.wikipedia.org/wiki/Virtual_Audio_Cable").

---

### Post by sirgad on 2013-03-14
I'm assuming, because no-one even comes close to mentioning them, that DAAPD and all its variants and forks (forked-daapd, mt-daapd, firefly2 etc.) are still dead as a dodo?  A cursory search of the web indicates this to be the case, but before creating another thread on the same topic, I thought I'd better respond here first.

Having to use either Windows XP in a VM or purchase a subscription to Vuze Plus seems a massive step backwards.  Were Apple just making things too difficult? :confused:

---

### Post by Stephen_at on 2013-04-06
Forked-daapd indeed is pretty dead - the developer retired and so its an orphaned project. Some people (including me) have patched versions which don't break as often but it still crashes far too often (but with my patches at least it only takes a few seconds to restart)

---

