---
title: "SpamAssissin Plugin Razer2"
date: 2010-12-13
forum: Server Platforms
---

### Post by William_in_Kanata on 2010-12-13
Ubuntu 10.04.1 lts 64 Bit

We are periodically seeing the following error message from spamd:

 spamd[2601]: razor2: razor2 check failed: razor2: razor2 had unknown error during get_server_info at /usr/share/perl5/Mail/SpamAssassin/Plugin/Razor2.pm line 190. at /usr/share/perl5/Mail/SpamAssassin/Plugin/Razor2.pm line 330.

I am no Perl expert (not even a beginner), so I have no idea what this is trying to tell me, except that there is some kind of problem. I am guessing that it has to do with call to get_server_info, but I can't find where this is actually executed. There is no function in Razor2 that has this name.

Any pointers will be greatly appreciated.

Thanks for your time.

William.

---

### Post by laymer on 2011-02-15
hey,
 
I have the same problem. New installation and everything!!
 
I hate it when this happens, no answers on the web so we must be the first to figure it out.
 
_WARN: razor2: razor2 check failed: Connection refused razor2: razor2 had unknown error during get_server_info at /usr/share/perl5/Mail/SpamAssassin/Plugin/Razor2.pm line 190. at /usr/share/perl5/Mail/SpamAssassin/Plugin/Razor2.pm line 330.

---

### Post by Firefishy on 2011-03-18
Unblocking port 2703 and reinstalling razor fixed the issue for me.

---

