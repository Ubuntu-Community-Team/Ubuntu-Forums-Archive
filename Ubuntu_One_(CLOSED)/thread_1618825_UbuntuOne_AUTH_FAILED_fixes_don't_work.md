---
title: "UbuntuOne AUTH_FAILED fixes don't work"
date: 2010-11-11
forum: Ubuntu One (CLOSED)
---

### Post by Bnonn on 2010-11-11
I recently ran out of space with my free 2 GB U1 account. So I upgraded to a 20 GB pack.

This was shortly after upgrading from 10.04 to 10.10, during which I changed the name of my computer from 'Rain' to 'El-Mustango'. Don't ask.

Anyway, in the process of upgrading U1 to 20 GB, I noticed the machine I had connected on the website was still called Rain. So without really thinking, I removed it.

Now I can't get U1 to sync. If it tries at all, it tells me that I've got no free space. And when I say "it tells me", I mean "someone should fix the bug where it pops up a notification for every single file it tries to sync".

I've gone through every fix I can find online. My issue is the u1sdtool -s shows:

> State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: IDLE
I've tried doing the standard fix of going into Seahorse and removing the U1 token, but there IS NO U1 token! So I don't know what to do. I've completely removed U1 and reinstalled it (purging all files, including all config) and that hasn't helped.

I tried running u1sync --authorize, but get the following message:

> u1sync: error: no such option: --authorize

Pretty sure that ain't right because, well, the man page says --authorize is a valid option.

I've also tried downloading ubuntuone-old-auth.py and running that, as per a comment I saw in a bug report; this just gives me the following:

> Traceback (most recent call last):
  File "ubuntuone-old-auth.py", line 8, in <module>
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
ImportError: No module named oauthdesktop.auth
Pretty sure that ain't right either. I've checked that python-oauth is installed and it is.

Help. I rely on U1 as a backup solution, and I'm paying now, so it would be rather nice to get it working.

---

### Post by yeagerfox on 2011-08-31
Hi,

I have the same problem.
I tried to remove my computer from U1, then restore it, but it's not better.

Did you get a solution ?

Thanks

---

### Post by duanedesign on 2011-09-01
One  of the most common reasons for this is the clock of the computer being off. Please check your time and date settings. If under Time & Date the option manual is selected you may try the set automatically over the internet option. If that is already selected please check that your time zone is correct and verify the time against an[ alternate reliable source ]("http://www.timeanddate.com/worldclock/"). If set automatically is off you will need to select manual and correct the time appropriately.

---

