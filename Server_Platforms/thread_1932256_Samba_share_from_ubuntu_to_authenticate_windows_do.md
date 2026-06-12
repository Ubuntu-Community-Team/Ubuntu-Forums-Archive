---
title: "Samba share from ubuntu to authenticate windows domain users"
date: 2012-02-27
forum: Server Platforms
---

### Post by Kanagaraj on 2012-02-27
Dear Ubuntu people,

I have an ubuntu 10.04.2 desktop joined into my windows domain running on Windows 2008 R2 AD server using pbisopen6.5 (formerly likewise open). 

My requirement is that I have a samba share /ubshare in this machine. which could be accessed by the domain users from their windows computers. All those users will fall under three groups namely, 

abc_read
abc_write
abc_full 

If the abc_read group people login they should have only read permission for the samba share.

If the abc_write group people login they should have have write permission for the share.

If the abc_full group people login they should have the full permission on the same share.

Please guide me how to achieve this.

---

### Post by SeijiSensei on 2012-02-27
Samba has directives to limit access by group membership.  Take a look at [this](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2611888).

---

