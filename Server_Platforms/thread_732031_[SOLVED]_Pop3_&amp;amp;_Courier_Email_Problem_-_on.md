---
title: "[SOLVED] Pop3 &amp;amp; Courier Email Problem - only one domain doesn't work."
date: 2008-03-22
forum: Server Platforms
---

### Post by 3D Peruna on 2008-03-22
Running 6.1, updated.  The server is hosting multiple domains - email and web using ISPConfig.  Up until last Wednesday, everything was working fine.

Then, one domain stopped "POP"ping.  We can access the email via Squirrelmail or Webmail, but not POP3. Thunderbird, Outlook and Outlook Express all fail with that Account only.   They all give a "connection timeout" error.  

I've combed through the logs but can't see anything odd.  All of the other domains work just fine...and have been.

Any suggestions of what to look for?  How to fix it?  I've even gone so far as to reboot the server once (and it didn't help).

TIA :confused:
[B]
UPDATE: [/B] I think I got it solved:  It was a problem with the domain registrar.  There were some DNS issues that they needed to sort out.  Since they couldn't, I transfered the DNS to a different host and once everything synced up, it started POPing again.  Still, a very weird error.

---

