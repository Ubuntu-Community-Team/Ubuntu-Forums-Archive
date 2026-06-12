---
title: "Samba File Server"
date: 2010-11-28
forum: Server Platforms
---

### Post by grenadingbadger on 2010-11-28
How do I set up a server to where it does not give a password prompt to access a shared folder?

---

### Post by capscrew on 2010-11-28
> **grenadingbadger said:**
> How do I set up a server to where it does not give a password prompt to access a shared folder?

Check the ***[SIZE="2"]map to guest (G) [/SIZE]*** section of the smb.conf chapter of the Samba doc's [**_[COLOR="DarkSlateGray"][SIZE="2"]here[/SIZE][/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

The default guest account is the account: *nobody*.  I set this to *smbguest*.  Check the section of the above manual called ***[SIZE="2"]guest account (G)[/SIZE]***.

FYI: the (G) in the above means that the stanza belongs in the **Global **section of the smb.conf file.

---

