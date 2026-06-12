---
title: "Everyone Group XP"
date: 2007-12-18
forum: Windows
---

### Post by Black Mage on 2007-12-18
I'm helping out this non-profit organization with networking, and it turns out they do not actually have an actually DNS server, its a router acting as a DNS.
And I'm trying to create like a Drop Box on everyone computer where they type in the IP in the address bar, see a shared folder called drop box in which they can only write and not read, hence drop box. The problem is, the Everyone group only gives the option of if Full Control, Change, and Read. 

So how can I add the options of Write to the Everyone Group?

---

### Post by jrusso2 on 2007-12-18
Well you can make another group and give that write only to the share and remove the everyone group rights to that share and add the users to the new group.

Only problem is if you only give write access I am not sure if the users could see the share to write to it

---

### Post by Black Mage on 2007-12-18
I created another group but I couldn't actually define the priveleges and I couldn't edit the priveleges ofthe Everyone group. And there is no active directorydns server, everything is on a router.

So what should I do to make a drop box with write only priveleges to everyone?

---

### Post by K.Mandla on 2007-12-19
Moved to Windows Discussions.

---

### Post by digital_exhaust on 2007-12-19
[Hamachi]("http://https://secure.logmein.com/products/hamachi/vpn.asp?lang=en")?

---

### Post by psusi on 2007-12-19
Set the share permissions to full control, they are useless anyhow, and use the filesystem permissions to give everyone write only access.

---

