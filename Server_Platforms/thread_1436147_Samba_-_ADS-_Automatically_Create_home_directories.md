---
title: "Samba - ADS- Automatically Create home directories"
date: 2010-03-22
forum: Server Platforms
---

### Post by robertomason on 2010-03-22
:popcorn:At work, using [SambaKerberos]("https://help.ubuntu.com/community/Samba/Kerberos?action=fullsearch&context=180&value=linkto%3A%22Samba/Kerberos%22") and [ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?action=fullsearch&context=180&value=linkto%3A%22ActiveDirectoryWinbindHowto%22"), I joined my machine to our ADS network. Again using [ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?action=fullsearch&context=180&value=linkto%3A%22ActiveDirectoryWinbindHowto%22"), I modified both common-account and common-auth with these settings.

file: /etc/pam.d/common-account 
account sufficient       pam_winbind.so
account required         pam_unix.so

file: /etc/pam.d/common-auth 
auth sufficient pam_winbind.so
auth sufficient pam_unix.so nullok_secure use_first_pass
auth required   pam_deny.so

According the the doc, when I first log in as a domain user, it should create the home directiroy /home/<whateverdomain>/<theusername>, but it doesn't. Am I doing something wrong, did I miss something.

Thank You
Roberto

---

### Post by cdenley on 2010-03-22
Did you modify /etc/pam.d/common-session, as the guide I believe you were referring to instructed you to do?
```

session required pam_unix.so
session required pam_mkhomedir.so umask=0022 skel=/etc/skel

```

---

### Post by robertomason on 2010-03-23
Thanks, that was it. I guess I went through the doc a little to quickly:D

---

