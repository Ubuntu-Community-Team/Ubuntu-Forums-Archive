---
title: "Novell bans proprietary Linux modules"
date: 2006-08-02
forum: The Cafe
---

### Post by newbie2 on 2006-08-02
> In a change of heart, Novell has ceased distributing proprietary software modules such as 3D video drivers that plug into the Linux kernel.
[http://news.com.com/Novell+bans+proprietary+Linux+modules/2100-7344_3-6100659.html](http://news.com.com/Novell+bans+proprietary+Linux+modules/2100-7344_3-6100659.html)
:mrgreen:

---

### Post by gamma on 2006-08-02
I just saw this today and was pretty amazed. I'm hoping Novell has something else up their sleeve, since they're the ones that created Xgl, and what's XGL with proprietary drivers? I doubt this will have any influence on NVIDIA/ATI releasing opensource drivers, but maybe they'll atleast release the specifications of their cards so people can easily make an opensource driver. Currently there are a few projects out there reverse engineering the cards to impliment 3D support. Here's hoping they succeed.

---

### Post by atrus123 on 2006-08-02
I heard that Novell is still making it easy to install the closed source modules, even if they're not bundling them.

Also, considering AMD's supposed move to make the ATI drivers open source, this move by Novell makes a bit more sense to me.  After all, there are still many ATI cards unable to achieve direct rendering from the open source driver (mine included).  

Now if only Adobe would release the Flash module open source...... but now I'm really dreaming.

---

### Post by gamma on 2006-08-03
I'd love to see the day where I can run my opensource flash with the nice eyecandy of Xegl (successor of Xgl allowing 3d on a 2d desktop, instead of the current 2d drawn as a 3d texture plane) with opensource Nvidia drivers.

If ATI opens their source that'd be great, because open source programmers would probably be able to achieve better performance than the a few paid people working by a roadmap. NVIDIA would see keeping their drivers closed source as a weakness, not a strength and we'd see opensource 3d drivers. Since they'd be released under the GPL they would be allowed to be bundled and included in the current kernel. Boy am I dreaming though, it'd be another 5 years before we see something like that...

I don't care about gaming, so my next laptop will probably have Intel integrated graphics which are opensource I've heard.

One last thing. I think the AMD-ATI deal was made so that AMD can integrate the graphics board into their chipsets. Someone made the reference this is the equivilent of Intel  way back when starting to include the math co-processor on the boards. I agree with this, and think we'll see things integrated.. we won't see graphics cards around forever.

---

### Post by forrestcupp on 2006-08-03
> **gamma said:**
> 
One last thing. I think the AMD-ATI deal was made so that AMD can integrate the graphics board into their chipsets. Someone made the reference this is the equivilent of Intel  way back when starting to include the math co-processor on the boards. I agree with this, and think we'll see things integrated.. we won't see graphics cards around forever.

I doubt it.  If all graphics were integrated, that would make it a lot harder for power-users to upgrade, which would make it a lot harder for graphic chip companies to make money.  Usually the integrated stuff is pretty low-level, and they also include a slot to upgrade.

---

### Post by Brunellus on 2006-08-03
Looks like the ubuntu-ization of OpenSuse and SLED to me.  Smart move, from a liability standpoint, and an interesting move from the software freedom standpoint.

---

### Post by Cynical on 2006-08-08
> **forrestcupp said:**
> I doubt it.  If all graphics were integrated, that would make it a lot harder for power-users to upgrade, which would make it a lot harder for graphic chip companies to make money.  Usually the integrated stuff is pretty low-level, and they also include a slot to upgrade.

No actually they make a lot more money on intergrated graphics, because most people don't use their computers for gaming.

---

### Post by hizaguchi on 2006-08-08
I installed Suse 10.1 a while back and I can verify that not only was the fglrx driver missing, but installing it (at least for AMD64) meant downloading the driver from ATI and building your own kernel module... for every kernel upgrade.  They must have something up their sleeve, because there's no way they'd go to the trouble of making desktop Linux so point-and-click friendly only to throw this roadblock in the way of new users.

---

