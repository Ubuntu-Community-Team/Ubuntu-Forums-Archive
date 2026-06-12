---
title: "Wha tis a &quot;domain&quot; in linux/ubuntu?"
date: 2009-04-08
forum: Server Platforms
---

### Post by Linuxwho? on 2009-04-08
Is there a domain "controller" like in windows?  As far as I know it sounds like its simply an entry in a hosts file.

Also, how does dns work?  Do u just check the box in the setup when installing the server?  Do you point other internal servers to it?  How does this work?  Thanks.

---

### Post by bluefrog on 2009-04-08
the best thing for you is to read the server guide. click on the help icon of your ubuntu desktop, type 'server guide' in the search box, scroll down a bit and you'll find it.

---

### Post by Linuxwho? on 2009-04-08
Ok, I will check that out.

---

### Post by juancarlospaco on 2009-04-09
On Linux LDAP, Windows AD do the same too, i think this is the Standard, LOL...

---

### Post by hyper_ch on 2009-04-09
what is a "domain" controller on windows?

---

### Post by Linuxwho? on 2009-04-11
> **hyper_ch said:**
> what is a "domain" controller on windows?

It is the server that holds the FSMO roles.  Let me think..  Domain Naming Master, Relative Identifier Master, infrastructure master, PDC emulator, schema master and Global catalog server.  It allows people or admins to logon for services or servers with one global account - for more than 10 machines typically.  Basically it controls security, ids for all objects, etc..so many servers can be used like one.

---

