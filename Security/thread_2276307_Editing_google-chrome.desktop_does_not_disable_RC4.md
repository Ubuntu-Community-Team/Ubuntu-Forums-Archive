---
title: "Editing google-chrome.desktop does not disable RC4 and SSL3"
date: 2015-05-01
forum: Security
---

### Post by a.borque on 2015-05-01
Hello!
I am on Ubuntu 14.04.2 (32bit, Unity) with latest Chrome-browser from googles ppa.

To start Chrome automatically  with rc4 and ssl3 disabled and in incognito-mode I edited google-chrome.desktop as suggested on many sites.
Now every exec-line looks like

Exec=/usr/bin/google-chrome-stable --cipher-suite-blacklist=0x0001,0x0002,0x0004,0x0005,0x0017,0x0018,0xc002,0xc007,0xc00c,0xc011,0xc016,0xff80,0xff81,0xff82,0xff83 --incognito --ssl-version-min=tls1

Then I rebooted.

Unfortunately this does not any of the things I expected it. RC4 and SSL3 are still usable and it is not in incognito-mode.

I have attached google-chrome.desktop (extension changed to txt). 

What is wrong?

Thanks
A.Borque

---

