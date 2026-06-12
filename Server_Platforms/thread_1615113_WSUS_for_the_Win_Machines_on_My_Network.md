---
title: "WSUS for the Win Machines on My Network???"
date: 2010-11-06
forum: Server Platforms
---

### Post by JDorfler on 2010-11-06
Ok, I've got a few parts laying around and maybe a 100 bucks on NewEgg I can get a Windows Server going.  However, I have a few questions.  I already have two Ubuntu servers going.  My main concern is OS updates.  I have Ubuntu based distros covered via apt-cacher-ng on one of my Ubuntu servers.  I also have a nice squid server going with adzapper and so on.  However, I have a bunch of Windows based machines on my network, and I have very limited bandwidth.  I know I can run a virtual server on my main server, but I prefer to have an actual box just for a WSUS server for personal reasons.  This is only an option if there is no option for WSUS style updating through Linux on my current server.  

If I have to build a low powered Windows Server box in order to just push Windows updates for XP, Vista, and 7 to save bandwidth in the long run will a copy of Windows Home Server do the trick?  I read an article from MaximumPC that WHS 2.0 will have a WSUS feature, but is this feature available in WHS 1.0?  This is a really crappy way of storing updates and save bandwidth, but I don't know what other options I have.  I live and work in a very remote area and I've already done everything I can think of to help save bandwidth.  Like having a transparent proxy server and apt-cacher-ng running.  It's also helps run things a lot faster when updating Ubuntu based boxes and surfing the internet.  If I could just get the Windows updates out of the way I would be golden.

Any ideas and information would be appreciated.  I'll wait for WHS 2.0 if I have to.  I'm not buying a full blown copy of Windows Server just for updates, especially on a box that'll cost about 300 bucks when complete.  Still better than a prebuilt WHS box advertised on NewEgg for 600 bucks.

---

### Post by JDorfler on 2010-11-08
I did some research and the current WHS can use WSUS for up to 10 clients.  However, it's 32bit and I am not sure if it can handle the 64Bit OSes that are on my network.  Any suggestions?

---

### Post by pricetech on 2010-11-08
Probably best addressed on a windows forum, but I can give you this much information;
I made three attempts on three different servers to set up a working wsus and never succeeded. (Server 2k3) I don't feel too bad about the failure though since my predecessor failed at least 4 times.
Didn't see any possibility that a Linux box could fake it or I would have gone that route myself.

Good luck with it.

---

### Post by jaylark on 2010-11-08
You need to run Server 2003 RS or Server 2008.  You also need to join all your client machines to a functioning domain.  After that configuring your XP machines to get updates from WSUS is really easy.

The WSUS site actually has extremely good documentation on setting up the update server and group policy.  [http://technet.microsoft.com/en-us/wsus/default.aspx](http://technet.microsoft.com/en-us/wsus/default.aspx)

---

### Post by koenn on 2010-11-08
> **JDorfler said:**
> I did some research and the current WHS can use WSUS for up to 10 clients.  However, it's 32bit and I am not sure if it can handle the 64Bit OSes that are on my network.  Any suggestions?

Don't know if you can get WSUS to work on WHS, but you shouldn't worry about what OS the clients are, WSUS lets you select what OSes and other MS software you want updates for, gets them from Windows Updates, and makes them available for download by the clients. Not too different from a proxy, actually. 
(unless, of course, MS has crippled it for commercial reasons - but if so, you'd find out about it at the WSUS website)

---

### Post by JDorfler on 2010-11-17
Thanks everyone.

---

### Post by CharlesA on 2010-11-17
I was just going to mention it, but I see that koenn already did.

I don't think you can run WSUS on WHS, but I did find this:

[http://www.wegotserved.com/2009/03/12/update-how-to-run-wsus-on-windows-home-server/](http://www.wegotserved.com/2009/03/12/update-how-to-run-wsus-on-windows-home-server/)

Worth a shot, right?

---

### Post by JDorfler on 2010-11-18
Thanks.

---

