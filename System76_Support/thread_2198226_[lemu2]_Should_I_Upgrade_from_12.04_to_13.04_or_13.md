---
title: "[lemu2] Should I Upgrade from 12.04 to 13.04 or 13.10?"
date: 2014-01-07
forum: System76 Support
---

### Post by Conzar on 2014-01-07
I have a lemu2 running 12.04 LTS.  I see that the system76 driver is only available for 13.04 and 13.10.  Should I upgrade?  If so, to which version?  

Also why should I upgrade?
IE, Intel Graphics Driver has newer drivers in 13.x?

Thanks

---

### Post by ddraper2 on 2014-01-07
I can't really give you the reason for updating but if I was going to update I would go for 13.10. I received my system with 13.04 and I upgraded to 13.10 with no problems. I can't see any real differences other than there is one annoying bug where the sound does not restart properly when resuming after suspend. There is a simple workaround to run a few commands that will reset and restart the sound system. I have a small shell script I wrote to take care of it. The fix is posted in the Installation and Upgrade section of the forum.

---

### Post by joe4ska on 2014-01-18
I'd wait for 14.04 LTS since it's right around the corner and you'd have to update from 13.10 by July anyway. ([13.04 support ended already]("https://wiki.ubuntu.com/Releases"))

I urge you backup your system before upgrade just in case. I use [Clonezilla]("http://clonezilla.org/").

You will not likely need the driver I'm currently running Ubuntu Studio 13.10 on a Lemu4 and the items that the driver once enabled in previous Ubuntu versions now work automatically.

---

### Post by bridger2 on 2014-01-20
> **joe4ska said:**
> I'd wait for 14.04 LTS since it's right around the corner and you'd have to update from 13.10 by July anyway. ([13.04 support ended already]("https://wiki.ubuntu.com/Releases"))

I urge you backup your system before upgrade just in case. I use [Clonezilla]("http://clonezilla.org/").

You will not likely need the driver I'm currently running Ubuntu Studio 13.10 on a Lemu4 and the items that the driver once enabled in previous Ubuntu versions now work automatically.

I'm with joe4ska on this one.  What you do is entirely up to you— I cannot think of any serious issues with upgrading to 13.04 or 13.10 (excepting the privacy issues associated with the dash routing your searches through web servers by default).  Personally, though, I'm waiting to see what 14.04 LTS is like.  Long-term support releases tend to be a bit more stable, and are (as the name implies) supported for longer.

---

