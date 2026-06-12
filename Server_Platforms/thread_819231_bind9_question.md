---
title: "bind9 question"
date: 2008-06-05
forum: Server Platforms
---

### Post by fouadk on 2008-06-05
hi everyone...

i am trying to setup a mixed environment where i have a windows active directory and an ubuntu server running bind9 DNS

i was wondering if anyone has tried this before....

while googling i understood that i need to add something related to SRV but i am having no success...

please help...

thanks in advance

---

### Post by RealPSL on 2008-06-06
What you are looking to do is use Windows Active Directory (AD) with native bind. Your best bet is to follow the instructions provided by Microsoft since they know AD best.
[http://www.microsoft.com/technet/archive/interopmigration/linux/mvc/cfgbind.mspx?mfr=true]("http://www.microsoft.com/technet/archive/interopmigration/linux/mvc/cfgbind.mspx?mfr=true")

The easiest way to do this in my opinion is allow the IP address of the domain controller to dynamically update it's own A, SRV and CNAME records in DNS. This is covered in the document above.

---

