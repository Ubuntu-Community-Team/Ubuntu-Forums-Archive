---
title: "HP ProLiant DL160 G6"
date: 2009-08-08
forum: Server Platforms
---

### Post by deejross on 2009-08-08
I am trying to install Ubuntu Server 8.04 in a brand new HP ProLiant DL160 G6, however, I am running into one roadblock after another. Before I even got these servers, I posted a question in these forums about hardware compatibility with these servers. The answer I got was, "Of course it will work, it's not Windows and doesn't need drivers to make hardware work."

Well apparently it does need drivers, because I can't get the DVD drive, network interfaces or the hard drives detected by Ubuntu Server, so I can't even install it.

I have tried Ubuntu Server 8.04 (64-bit) and Xubuntu Desktop 8.04 (64-bit) (thinking that it had something to do with the -server kernel) and neither are detecting the hardware.

So my question is, do I need to try the newest (Jaunty) version of Ubuntu Server to make this work, or are there workarounds?

The hard drives are configured to emulate IDE drives (so no RAID), so I don't understand why Ubuntu won't pick them up.

Please help! Thanks for your time.

---

### Post by deejross on 2009-08-08
I sort of answered one of my questions. I downloaded and installed the Jaunty version of Ubuntu Server and that seems to detect the hardware, however the hard drive partitioning seems to have stalled at 33%. (UPDATE: Partitioning just took a really long time. Longer than I've ever seen.) And since eBox works best with Hardy, Id still like to know if there's a way to get Hardy to run on the server.

---

### Post by samosamo on 2009-08-09
I think you found that linux will run on pretty much anything as long as the kernel you are using is as new as the hardware you are installing it on.  Common sense, right?

---

### Post by deejross on 2009-08-09
Yea, except that the server is new to me...this model has been around for a little while.

---

### Post by T-Train on 2009-11-20
This will not cover everything but check out this page for support.

[http://www.ubuntu.com/partners/hp](http://www.ubuntu.com/partners/hp)

---

