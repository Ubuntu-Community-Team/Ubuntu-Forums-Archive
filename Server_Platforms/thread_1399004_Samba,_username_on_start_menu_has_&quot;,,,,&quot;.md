---
title: "Samba, username on start menu has &quot;,,,,&quot; after it"
date: 2010-02-05
forum: Server Platforms
---

### Post by TheMightyGirth on 2010-02-05
Hi All,

I have just finished installing a new server for someone and noticed as I was joining machines to the samba domain that the name appearing at the top of the start menu had ",,,," after it.

After a little investigation I found the the description section of /etc/passwd also had the ",,,,". I believe they are being created by the adduser command and would have room number, office, home, other in them if I had filled in that info when creating users. I have now removed the ",,,," from /etc/passwd.

My problem is this, whilst I can now ensure new users don't get the ",,,," after their name, existing users still have it. Can anyone tell me where to look or which file to alter in order to remove the ",,,," from the existing samba users names.

Thanks in advance for any help.

Ta,
Gareth

---

