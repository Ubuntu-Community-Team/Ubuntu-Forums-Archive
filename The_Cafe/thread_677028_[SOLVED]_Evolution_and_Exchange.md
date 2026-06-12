---
title: "[SOLVED] Evolution and Exchange"
date: 2008-01-24
forum: The Cafe
---

### Post by dgoodma on 2008-01-24
Finally figured it out.

Exchange points to the Web Address for your Web Email, OWA... [https://mail.xxxx.com](https://mail.xxxx.com)
the GAL is looking for your Active Directory Domain  XXXX.XXXX.COM
Now it works fully when I am on the Corporate Network, but the GAL does not work when I am not; that makes sense. Next step, VPN... but our corporate environment favors Windows solutions there...
******************************
I wish Evolution would integrate better with our Exchange environment.

When I configure it to use Web Mail, Email and Calendar work well. Where is my Directory? When you access Exchange with IE on Windows, you see all. When I use Firefox to access Web Mail, things do not display the same as on IE. Gave up on Wine, either does not work, or configuring it is beyond my abilities or time available to spend figuring it out.

I have tried IMAP, and again Email works fine, but cannot connect to our user directory. It prompts for a password to the GAL, when I enter my Active Directory id and password, it does not work.

i did configure an LDAP directory, but that only allows me to look up people from the directory, not within Email (from the To: line).

This area is one of the big challenges to suggesting that we should use Linux desktops in our corporate environment. 

Replacing Exchange is not an option.

We do have a Citrix server environment that serves up Outlook, but in general I think using Evolution or another Linux Email client might be an overall need in corporate environments, and an inhibitor to Linux adoption.

---

### Post by wbarnum on 2008-01-25
i have the same issue at my work.  bummer.

---

