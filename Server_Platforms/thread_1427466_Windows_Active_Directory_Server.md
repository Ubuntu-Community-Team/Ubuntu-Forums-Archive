---
title: "Windows Active Directory Server"
date: 2010-03-11
forum: Server Platforms
---

### Post by Josh89 on 2010-03-11
I would like to set up Some kind of windows user manager in an ubuntu sever. The windows network is already set up. I've scoured the net for hours and found nothing. Please if anyone can help post here!

Thanks, Josh.

---

### Post by gordintoronto on 2010-03-11
I *think* you want to set up a "domain controller" on Ubuntu.  If you Google that, you'll find several tutorials. Full Circle Magazine had a series which begins here:
[http://fullcirclemagazine.org/directory-server-on-ubuntu/](http://fullcirclemagazine.org/directory-server-on-ubuntu/)

---

### Post by mcarrara on 2010-03-12
Active directory is supported experimentally in Samba 3 and is expected to work in Samba 4.  Currently you can use Samba to authenticate like an NT domain using LDAP.  Or if it is a simple network manually create the accounts on the Samba server as Linux accounts.

Mark

---

### Post by HermanAB on 2010-03-12
Read the official howto on the Samba web site.

---

