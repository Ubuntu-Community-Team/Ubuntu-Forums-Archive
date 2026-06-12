---
title: "Track Windows Logins with Ubuntu Server"
date: 2010-11-08
forum: Server Platforms
---

### Post by Magnesium on 2010-11-08
Howdy,

I am working on a project for a university research center, rewriting their reservation system and other things. Currently they are using something called "LabMan" to track computer usage (to bill for time). It has a part which runs on a Windows Server and listens to the other Windows Computers report their login and logout times. I want to completely get rid of that Windows server, but need some way to replace this "LabMan".

Any ideas? I know I could code something up, and I may still do that, but if I don't have to I don't want to... ;) In other words, does anyone know of a solution that would allow me to use my **Ubuntu** Server to track usage (logins and logouts) on all the **Windows** computers.

TIA!
Mg

---

### Post by Magnesium on 2010-11-08
Any ideas at all?

---

### Post by koenn on 2010-11-08
A while back I was looking for something similar, but all I found was rather elaborate internet cafe management software, and all very wwindows-only.

I ended up making this:
[http://users.telenet.be/mydotcom/program/bibmon/index.htm](http://users.telenet.be/mydotcom/program/bibmon/index.htm)

It does wat it's supposed to do : log user logon and logout times in a database.

caveats:
you'd have to install an odbc/jdbc driver + the logon and log off scripts on the PCs. In a managed environment, maybe this can be automated. 

the scripts contain a plain text password to the database, so a smart user might try and modify the entries. You might want something more secure (I didn't care, the pc's ware locked down pretty well, and we didn't charge for use of the computers so it's just time, not money)

---

### Post by Magnesium on 2010-11-08
> **koenn said:**
> A while back I was looking for something similar, but all I found was rather elaborate internet cafe management software, and all very wwindows-only.

I ended up making this:
[http://users.telenet.be/mydotcom/program/bibmon/index.htm](http://users.telenet.be/mydotcom/program/bibmon/index.htm)

It does wat it's supposed to do : log user logon and logout times in a database.

caveats:
you'd have to install an odbc/jdbc driver + the logon and log off scripts on the PCs. In a managed environment, maybe this can be automated. 

the scripts contain a plain text password to the database, so a smart user might try and modify the entries. You might want something more secure (I didn't care, the pc's ware locked down pretty well, and we didn't charge for use of the computers so it's just time, not money)

Oh that is perfect Koenn...thanks so much! Yeah security is not a giant issue here, anyone who uses these computers is "honest"...we just want another way to keep track of who is using what.

Thanks again!!!
Mg

---

### Post by koenn on 2010-11-08
welcome.

---

