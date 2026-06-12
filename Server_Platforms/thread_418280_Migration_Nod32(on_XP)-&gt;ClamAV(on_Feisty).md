---
title: "Migration: Nod32(on XP)-&gt;ClamAV(on Feisty)"
date: 2007-04-22
forum: Server Platforms
---

### Post by mac.ryan on 2007-04-22
I am installing and configuring a machine for a friend who is just switching from  Windows. She is not a geek and I would like to give her a machine that behaves "just as windows" - as far as she is concerned, and this includes for me also:[LIST=1]
[*]scanning automatically any media inserted in her computer (CD, usb, flash cards...) for viruses
[*]updating virus signatures regularly
[*]checking incoming retrieved by POP3 or IMAP4
[*][eventually scanning outgoing mail][/LIST]I installed ClamAV and clamav-deamon, but what I have difficulties in understanding is how to automated this process. I imagined that for point 2 I could simply set up a cron-job for root with the appropriate command (which I still have to find out)... but I have no clue for points 1,3 and 4.

Could somebody help me out with this? (Even pointing me out in the right direction without a detailed how-to would be **very** appreciated...)

---

### Post by mac.ryan on 2007-04-24
After some days of running the machine, I got the impression ClamAV is already behaving the way I want, at least for removable media, as at times I get strange windows opening, with ClamAV written somewhere.

I couldn't find any reference guide on this, yet.... any help?

(In the official documentation I found reference to clmuko and clamav-milter, but my general impression is that they operate on mail servers, rather than interecepting pop3/smtp traffic...)

---

