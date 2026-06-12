---
title: "Power saving for headless server"
date: 2010-08-02
forum: Server Platforms
---

### Post by emma_peel on 2010-08-02
Hello dear forum.

I'm looking for documentation to reduce the power consumption of my headless server. After a couple of google researches, I did not find any satisfying doc. Even the help.ubuntu.com site does not give any advice.

The server provides basic services, SMTP, SMB, Apache, UPnP, SSH, FTP ... That would be nice if the server could switch to (very) low power consumption state, and go back to normal if required. We could also imagine to adjust some settings according to the workload.

That would be very helpfull if you could indicate some help pages, blogs, feedback, package name, that would do the job.

Thank in advance.

---

### Post by arrrghhh on 2010-08-02
Well that's tricky.  I found a fairly recent thread on having a server sleep & wake automatically - [http://ubuntuforums.org/showthread.php?t=1335400](http://ubuntuforums.org/showthread.php?t=1335400)

However, that doesn't seem to be what you want.  The 'low power' stuff would be handled by your processor and motherboard I would think, assuming your server supports processor scaling the system should do that automatically, on-the-fly...

Correct me if I'm missing something there, but isn't that what you're looking for?

---

### Post by LightningCrash on 2010-08-03
cpufreq, when available, can automatically adjust the frequency (and thereby the power consumption) of the CPU on the fly

it is likely that you already have it installed

---

### Post by emma_peel on 2010-09-05
> **arrrghhh said:**
> Well that's tricky.  I found a fairly recent thread on having a server sleep & wake automatically - [http://ubuntuforums.org/showthread.php?t=1335400](http://ubuntuforums.org/showthread.php?t=1335400)

Thank you for your reply.

This looks a very good solution. The only weak point that I see, is that is based on WOL. If the server is not awake, in most of the case, when the services are called, the magic packet is not sent.

Anyway, the suspend and hibernate states are what I'm looking for. This is probably the best way to reduce the consumption of the server.

At a starting point, I have set up a short timeout before idle for the hard drive (hdparm -S) and I'm now digging a little the WOL-based solutions.

---

