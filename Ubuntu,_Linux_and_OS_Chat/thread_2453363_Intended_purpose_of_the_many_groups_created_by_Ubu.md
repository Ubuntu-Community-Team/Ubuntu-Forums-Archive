---
title: "Intended purpose of the many groups created by Ubuntu install?"
date: 2020-11-08
forum: Ubuntu, Linux and OS Chat
---

### Post by David_Partridge on 2020-11-08
Loads of groups are created as part of the installation, some whose purpose is clear, many are not.

Is there a Wiki or tutorial or similar describing what each of these groups are intended to be used for?

Some are "well know" (e.g. syslog and sudo) but the rest are at least to me a mystery ...

Thanks
David

---

### Post by wildmanne39 on 2020-11-08
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by grahammechanical on 2020-11-09
This is an area where I am happy to remain ignorant. I have too many other matters buzzing around in my head. These links might help you.

[https://askubuntu.com/questions/1109859/why-is-syslog-a-user](https://askubuntu.com/questions/1109859/why-is-syslog-a-user)

[https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)

I may have misunderstood the information but this is the way I see it. System processes need to do their job. We can 1) let them have complete access to every part of the system. If we do that a system process code that has been compromised could do great damage to the system. 2) Require the real user to give permission every time a system process wanted to do its job. 3) Allow the system process to do its job but with very limit access to the system.

Regards.

---

### Post by David_Partridge on 2020-11-25
Not really very helpful e.g. there's a group called video - there are no folders or files with that group used to control access AFAICT, so what's it for? 

I worked for quite long time as a security consultant so am very well aware of the principle of least privilege.

I like to understand how the security of a system is set up which is why I asked the question in the first place.

David

---

