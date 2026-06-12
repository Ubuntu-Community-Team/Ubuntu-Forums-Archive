---
title: "Up to Date HIDS?"
date: 2015-06-29
forum: Security
---

### Post by Alebin on 2015-06-29
I'm having trouble finding an up-to-date HIDS that actually works right, or works at all.

I installed AIDE and followed the ubuntu wiki/community guide on that and then found some external resources and patched all that together to get something that actually installed and half worked, but the init process would just hang there for hours, without increasing the database size, and when I interrupted the process and ran a check it gave me both a message that said something was wrong/changed and message that said everything was ok.

I also installed OSSEC following the guide in the sticky here and got to the apache part with virtual hosts and had to go look that up elsewhere and patch it together to get it working, but then I had it running and it looked to be working right, then I go and change some files around in /bin and rename some stuff and move some stuff and wait for like 5 minutes, and it never detects an issue.

I just want something that actually works, is up to date and being actually worked on, that simply tells me if the base Ubuntu files are being altered.

---

### Post by bashiergui on 2015-06-30
> **Alebin said:**
> ...then I go and change some files around in /bin and rename some stuff and move some stuff and wait for like 5 minutes, and it never detects an issue.

I just want something that actually works, is up to date and being actually worked on, that simply tells me if the base Ubuntu files are being altered.If this quote accurately reflects what you want, then you want FIM, not HIDS. File Integrity Monitoring (FIM) will detect any changes in files in whatever directory you care about. 

OSSEC is open source. Tripwire has a free version.

---

