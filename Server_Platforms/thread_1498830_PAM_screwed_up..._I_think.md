---
title: "PAM screwed up... I think"
date: 2010-06-01
forum: Server Platforms
---

### Post by yesrno on 2010-06-01
Hello folks,
Sure having a huge problem over here, I was screwing around with the PAM/SAMBA/WINBIND settings, and found myself with the following problem:
I now cannot loggin to our Ubuntu server with both AD credentials and the Linux credentials, in other words... I totally locked myself out of the server with only webmin access left. 
i was trying the following tutorial:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

But after entering all that I now cannot log on to the server anymore.
Is there any way to fix this easily ?

Thanks in advance!

---

### Post by HermanAB on 2010-06-01
Hmm, there are two ways to easily recover:
Re-install.
Restore /etc from a backup tarball that you made before messing with PAM.

Otherwise, boot with a CD and undo things manually.

---

### Post by yesrno on 2010-06-02
Would it be a solution to install a clean Ubuntu (same version) on a virtual machine, then copy the whole /etc/pam.d dir to the "ruined" Ubuntu :o ?
And If that would work, would only the /etc/pam.d directory work, or will I need to copy/replace any other files ?

---

### Post by yesrno on 2010-06-02
Okay that did the trick :D
Everything working fine now :)

---

