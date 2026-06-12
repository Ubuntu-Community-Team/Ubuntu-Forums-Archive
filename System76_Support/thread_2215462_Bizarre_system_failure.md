---
title: "Bizarre system failure"
date: 2014-04-06
forum: System76 Support
---

### Post by Joe_Knapka on 2014-04-06
Hi all,

I just experienced a very strange error on my Bonobo bonp5.  Executive summary: the / filesystem apparently spontaneously unmounted while the system was running. Upon reboot, everything appears normal, but... I'm worried.

I had Unity running with a terminal, a GIMP session, and Chrome open in different workspaces. Suddenly, the launcher and all status icons disappeared, although I could still switch between workspaces and my apps continued to run with no apparent problems.

However, when I switched to the terminal and did "sudo service network-manager status" (because the first thing I consciously noticed was the absence of the network-manager status icon), I got:

```
  sudo: command not found

```

Wait, what?

```
  which sudo

```

No output.

```
  ls

  ls: command not found

```

WHAT?!?

```
  mount

  mount: command not found

```

Buh wuh huh how?

```
  cd /
  echo *

```

Response:

```
  *

```

So... it appears my root filesystem is suddenly just GONE?

At this point I tried to save the image I had open in GIMP, and that apparently succeeded. (Upon reboot I re-opened the image, and it was in fact saved.) Then I thought long and hard about whether to reboot, or try to copy some important data off of machine before rebooting. Then I realized that it would probably not be possible to even mount an external disk, since /bin and /usr/bin were both apparently MIA, and if need be I could pull the internal disk and copy important stuff. So I took the plunge and powered off the machine. ("sync" and "shutdown -h" both resulted in  "command not found" - I was hoping "sync" might be a bash internal, but apparently not.)

Luckily, the it rebooted successfully, and I'm using it now to post this message. But I have NEVER seen this kind of utterly weird behavior from a Linux machine before except in cases of incipient catastrophic hardware failure. The root filesystem is on a 120GB SSD, and all the important stuff is on a 750GB spinning disk.

Has anyone ever seen anything like this?

Thanks,

- Joe

---

### Post by tgalati4 on 2014-04-06
Boot into the Rescue Shell and examine /var/log/syslog for errors.  Perhaps the SSD is defective.  Or a cosmic ray took out a bit and caused the kernel to act strange.

---

### Post by Joe_Knapka on 2014-04-06
> **tgalati4 said:**
> Boot into the Rescue Shell and examine /var/log/syslog for errors.  Perhaps the SSD is defective.  Or a cosmic ray took out a bit and caused the kernel to act strange.

Nothing in /var/log/syslog - it's a zero-length file. /var/log/syslog.1 latest entries are from the previous day.

I'm hoping the cosmic ray hypothesis is true. If anything like it happens again, I guess I'll replace the SSD.

Thanks,

JK

---

### Post by Joe_Knapka on 2014-04-07
It happened again :-(

---

### Post by CharlesA on 2014-04-08
syslog still blank?

---

### Post by Joe_Knapka on 2014-04-08
Yes, nothing in syslog. 

Completely different set of apps running this time, except for Chrome, which was running during both events. And possibly GIMP... I can't remember if I closed it earlier or not.

Once again, I had to reboot by power-cycling :-( I took the precaution of doing a clean shutdown after rebooting. I'll boot to single-user mode in a minute and run fsck.

---

### Post by Joe_Knapka on 2014-04-08
fsck found nothing amiss.

Nothing unusual-looking in dmesg.

Nothing in /var/log/syslog since April 5 (before the first incident).

I'm at a bit of a loss where to start investigating this. If it's an intermittent hardware failure that leaves no tracks... well that sucks :-(

---

