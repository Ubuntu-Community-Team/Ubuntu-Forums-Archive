---
title: "Starling Netbooks do not maintain Wifi connectivity; require reboot"
date: 2011-09-11
forum: System76 Support
---

### Post by bhaskar on 2011-09-11
My son and I each have a Starling Netbook, one a 32-bit 2010 model and the other a brand-new 2011 64-bit model.  Both had an annoying problem in that steady download of data in via Wifi (such as watching a Youtube video) would cause the Wifi to disconnect and reconnect, and after doing this several times, it would simply fail to connect.  Something was clearly amiss because the Network Manager applet would claim that it was connected, but no data would flow in either direction.

A bit at my wits' end, this afternoon, I reconfigured my router to use channel 1 instead of channel 6.  I have a neighbor down the street - not nearby - who was also using channel 6.  Since then, I have repeatedly forced data via the Wifi into my 32-bit Starling like stuffing food down the throat of a goose fated to become pate and it has not lost connectivity even once.

As the other computing devices at home had no trouble maintaining connectivity, I was convinced that it was a hardware problem - and perhaps the Starling's network cards are not as robust as the others - but at least my networking problem is solved.

---

### Post by Carleas on 2011-09-12
I'm having a similar problem, I'll have to try this.  How do you determine the channel of a wireless router you don't have access to?  I'm surrounded by other wireless signals.

---

### Post by bhaskar on 2011-09-13
In my case when I connect to my router's control panel via a browser, it tells me about other access points it sees and the channels).  I replaced my router's software with Tomato ([http://www.polarcloud.com/tomato]("http://www.polarcloud.com/tomato")).

---

### Post by isantop on 2011-09-15
> **Carleas said:**
> I'm having a similar problem, I'll have to try this.  How do you determine the channel of a wireless router you don't have access to?  I'm surrounded by other wireless signals.

Most access points use channel 6 by default, so choosing anything other than that would be a good place to start. If you still have issues on a different one, move on to another one.

---

