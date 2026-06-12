---
title: "Winbind AD - PAM unable to dlopen(pam_winbind.so)"
date: 2016-11-24
forum: Security
---

### Post by spicysalsa on 2016-11-24
I'm having a bit of an issue with my AD authentication on my server at home.

Ubuntu Server 16.04.1, all recent updates
Samba Version 4.3.11-Ubuntu


I have installed: samba winbind libnss-winbind libpam-winbind krb5-user
Followed this guide: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

I have done this many times before, and had no issues, but recently I noticed that I am unable to login using AD credentials.

When attempting to log in with AD credentials, just by using "su - <aduser>", I see the following in the auth.log:

```
Nov 24 08:37:23 sanitarium su[7048]: pam_authenticate: Authentication failureNov 24 08:37:23 sanitarium su[7048]: FAILED su for ryan by vault
Nov 24 08:37:23 sanitarium su[7048]: - /dev/pts/0 vault:ryan
Nov 24 08:37:28 sanitarium sudo: PAM unable to dlopen(pam_winbind.so): /lib/security/pam_winbind.so: cannot open shared object file: No such file or directory
Nov 24 08:37:28 sanitarium sudo: PAM adding faulty module: pam_winbind.so

```

I see pam_winbind.so in /lib/x86_64-linux-gnu/security/, but if I hardlink it to /lib/security/pam_winbind.so, it still doesn't work.

Thoughts?

---

### Post by barry.pederson on 2016-11-24
I'm seeing the same error after yesterday updating an Ubuntu 14.04.5 server's Samba and associated packages (winbind, etc) from 2:4.3.11+dfsg-0ubuntu0.14.04.1 -> 2:4.3.11+dfsg-0ubuntu0.14.04.2

I also tried symlinking, but that didn't work either. In that case /var/log/auth.log showed 

> PAM unable to dlopen(pam_winbind.so): /lib/security/pam_winbind.so: undefined symbol: wbcAddNamedBlob

---

### Post by spicysalsa on 2016-11-24
That is exactly the error I get after linking as well...
At least I know I'm not alone. Thanks for your input on the package versions. I never really paid attention to that. Update, Dist-Upgrade, Reboot... WTF happened?

---

### Post by steve_Ogaldez on 2016-11-24
After samba update on Nov 23rd to  **2:4.3.11+dfsg-0ubuntu0.14.04.2**  have not been able to login to my AD.  I have tried to downgrade to 2:4.3.11+dfsg-0ubuntu0.14.04.1  but login to AD fails. Found out that  **/lib/security/pam_winbind.so** was missing created link from /lib/x86_64-linux-gnu/security/pam_winbind.so now I am getting...

PAM unable to dlopen(pam_winbind.so): /lib/security/pam_winbind.so: undefined symbol: wbcAddNamedBlob
Nov 24 12:45:01 [5190]: PAM adding faulty module: pam_winbind.so

Please post if anyone gets a resolution.  Thanks.

---

### Post by barry.pederson on 2016-11-24
There's a bug for this at

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1644428](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1644428)

Looks like there's a proposed new package that puts things back to the way they were in [COLOR=#000000]2:4.3.11+dfsg-0ubuntu0.14.04.1[/COLOR]

---

### Post by barry.pederson on 2016-11-25
Yes, they released the update to 2:4.3.11+dfsg-0ubuntu0.14.04.3 and it all seems good now.

---

### Post by steve_Ogaldez on 2016-11-25
Thanks. Its working again.

---

### Post by spicysalsa on 2016-11-29
I see this is fixed in 14.04, which is great. But I think I will need to bring this up with 16.04 as well. I'm still having the issue and no updates seem to be available.
Thanks all for your input. I'll report my findings on 16.04 in this thread as well.

---

