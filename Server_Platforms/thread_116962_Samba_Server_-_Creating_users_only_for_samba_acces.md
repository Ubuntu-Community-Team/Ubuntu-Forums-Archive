---
title: "Samba Server - Creating users only for samba access"
date: 2006-01-13
forum: Server Platforms
---

### Post by byen on 2006-01-13
Hey guys,
I am following arnieboy's samba-how-to and have the following questions regarding samba users.
1.Does a user trying to access my samba share from his computer (xp) has to have a user name and password that can also help him log into my computer? (what if my pc gets hacked )
2. Is it possible to create a user for samba share access only? (ie. can log in to my samba shared folders but cannot log-in to my computer as a regular user)
3. Is there a way I can turn samba sharing on and off depending on the need? (I access a lot of wifi spots so..I guess this is one way to keep my files secure)
This may seem to be simple questions but I really need answers from users who have done this....

thank you for the time and help.
Goodluck.

---

### Post by LordHunter317 on 2006-01-13
[QUOTE=byen]1.Does a user trying to access my samba share from his computer (xp) has to have a user name and password that can also help him log into my computer? (what if my pc gets hacked )[/quote]Yes, but if you don't them to have shell access, give them /bin/true or something else similarly invalid for their login.

---

### Post by grendelkhan on 2006-01-14
This is correct, after you make the user, go into the users and groups program and change their default shell to /bin/false, then they can only have networked or ftp access and nothing else.

---

### Post by LordHunter317 on 2006-01-14
No, /bin/true is a better choice.  They still can't login, but PAM will fail login if the shell returns an error code, meaning some FTP daemons like ProFTPD will not work without changing their configuration.

---

### Post by Koybe on 2006-01-14
Or just do'nt set a password for the user. You can create a user with useradd without adding any passowrd. So it'll never be able to logon.

---

### Post by byen on 2006-01-14
[QUOTE=LordHunter317]No, /bin/true is a better choice.  They still can't login, but PAM will fail login if the shell returns an error code, meaning some FTP daemons like ProFTPD will not work without changing their configuration.[/QUOTE]
Would this also mean that he would have no other rights than to browse the shared folders?

thank you for the help guys. I really appretiate the help!!!!

---

### Post by bluefrog on 2006-01-16
samba.org menu "by example" will provide you with all you need to know.

james

---

