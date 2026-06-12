---
title: "Password Manager Wanted"
date: 2018-05-06
forum: Ubuntu/Debian BASED
---

### Post by David_Tuff on 2018-05-06
I am new to Linux. Have installed Chalet OS. On Windows PC I use Sticky Password Manager. I have exported in XML and imported into KeePass. It works, but need to copy and paste credentials into browser. Does anyone have a better Password Manager that actually populates the credentials into the browser automatically?

---

### Post by TheFu on 2018-05-06
> **David_Tuff said:**
> I am new to Linux. Have installed Chalet OS. On Windows PC I use Sticky Password Manager. I have exported in XML and imported into KeePass. It works, but need to copy and paste credentials into browser. Does anyone have a better Password Manager that actually populates the credentials into the browser automatically?

No passwords should be automatically put into browsers without positive user actions, IMHO. Things that are convenient are seldom secure.  It is a normal trade-off.

I have an issue with .net-based tools, so I use KeePassCX.  The DB is cross platform, so using it on Android, Windows, and Linux works.  I replicate the DB out to my devices nightly, but only use 1 system to modify the DB.  In my mind, this is "the system of record." It isn't enforced, except in my mind.

Anyways, KeePassXC has an autotype capability that will enter the userid{tab}password{enter} by default, when invoked.  The trick is to have the browser/login page behind KeePassX with the cursor in the password field before {alt-tab} back to KeePassXC.   <cntl>-v starts the autotype.   For login pages that need something different, there is a small scripting language to control tabs, delays, enters ... so even multi-page logins can be handled.

Of course, everyone knows that using passwords is a total security failure these days, so using key-based authentication really is best.  Lacking that, 2FA is a stopgap.

I'm not on 18.04, so I don't know if anything changed around this since 16.04.  I do remember having to install pinentry to gain access to my gpg-keys using the password DB for unlocking. pinentry provides a secure channel, unlike X11.

Sorry if my opinions aren't desired. Just ignore.

---

