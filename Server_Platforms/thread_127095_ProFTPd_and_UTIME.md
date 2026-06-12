---
title: "ProFTPd and UTIME"
date: 2006-02-08
forum: Server Platforms
---

### Post by Ric_ on 2006-02-08
Hi all,

I have a proftpd set up that works nicely. Apart from slow logons which I'm attempting to fix using

ServerIdent                     off
UseReverseDNS                off

I'll post and let you know how this goes.

However, I'm using gftp to upload and I knotice this error on every file I upload.

500 'SITE UTIME' not understood

Then i drop into PASV mode and the file transfers OK.
I did a lot of googling and found reference to mod_site_misc which mentions UTIME support. This should work when in /etc/proftpd.conf

  <Limit SITE_UTIME>
    AllowAll
  </Limit>

But alas it doesn't help.

Does anyone have any ideas on how to make proftpd support this feature? I can imagine the first responses will be switch to vstfpd or pureftpd. I would love to try them out but syscp won't let me!

---

