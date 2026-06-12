---
title: "linux client authentication against Samba PDC?"
date: 2006-01-29
forum: Server Platforms
---

### Post by pabs on 2006-01-29
Is linux client authentication available through Samba?  I just got some of my WinXP boxes to auth against Samba.  I would like to do the same with my Ubuntu box if possible.  

I'm using "passdb backend = tdbsam" in my smb.conf file.  Eventually I am going to move to LDAP because I want a domain admin group, but for the time being, I'm hoping I can somehow auth with tdbsam.  Is it possible?

Thanks in advance!

---

### Post by mdr on 2006-01-31
yes it is possible, Winbind
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)


google is your friend :)

---

### Post by pabs on 2006-01-31
omg.. All I had to do was google my exact thread title and it mentions Winbind in the first result... lol

I did google... I swear!  I came up with the right search terminolgy when I posted this apparently... not before  :oops: 

Thanks for your help though MDR!!  Much appreciated.

---

