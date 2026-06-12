---
title: "Samba PDC - 'Unknown User' error from Win2k, but logfile looks OK!"
date: 2006-09-04
forum: Server Platforms
---

### Post by chewtoy on 2006-09-04
Greetings.  I'm setting up an Ubuntu server for my small business.   That means running Samba as a PDC.

I think I've *almost* got it working (thanks to a HOWTO on [howtoforge]("http://howtoforge.com")), but I'm having trouble logging onto the domain from my Win2k box. I'm sure it's something simple, but it's apparently beyond me. Can someone point me in the right direction?

When I try to configure the Win2k box to logon to the domain for the first time, I get this: **"The following error occurred attempting to join the domain 'JGENET': Logon failure: unknown user name or bad password."**

Here's what I know:
[LIST]
[*]I get the error whether I try to logon to the domain as 'root' or as my username.
[*]I get the error whether I use my Samba root password or my system root password (I didn't expect the system root to work, but I tried anyway :) ).
[*]I get the error whether I'm logged onto Windows as Administrator, or as another (Administrator group) account.
[*]Win2k can see my Ubuntu box, because if I use a different/wrong domain name I get a domain-not-found error.
[*]My smbpasswd file is OK, because *smbclient -L localhost etc...* works on the Ubuntu box, for both the root account and my user account.
[/LIST]

Oddly, I've checked */var/log/log.the-w2k-box* and when I try to logon Samba spits a bunch of ***authentication successful*** messages into that file!  Yet Windows stubbornly insists on believing the user name/password are being rejected.

I'm not a complete newbie on Linux/Unix, but I'm definitely a novice at Linux/Windows networking.  So this has gone beyond my capabilities.

Can anybody de-mystify this for me?  I can provide plenty more configuration/logfile/etc. details.

---

### Post by bluefrog on 2006-09-05
if memory serves, you may have two buttons to join your machine to a domain, I think one will never work.

anyway check your /etc/samba/smb.conf
is there
invalid users = root
if yes comment it and try again. (well just seen that you can do smbclient with root so shouldn't be that..)

eventually post your smb.conf

James

---

### Post by hellmet on 2006-09-29
same problem here...
anyone know the solution??

or could anyone explain the exact procedure so that we cud follow??

---

