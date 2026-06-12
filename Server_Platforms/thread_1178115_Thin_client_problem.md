---
title: "Thin client problem"
date: 2009-06-04
forum: Server Platforms
---

### Post by pjbharrison on 2009-06-04
We have installed a server and 30 thin clients in my daughters school.
The server has 2GB ram and 2 Xeon 1.7Ghz cpus. The clients are a mix of P3s and P4s. The OS is Ubuntu 8.10. Edubuntu is also installed. When more than a few machines are booted the cpus both run at 98-100% and everything grinds to a halt.

Any suggestions?
Please bear in mind we are newbies to Ubuntu and Linux. Please be gentle with us as we are not very au-fait with computing!

---

### Post by Sealbhach on 2009-06-04
> **pjbharrison said:**
> We have installed a server and 30 thin clients in my daughters school.
The server has 2GB ram and 2 Xeon 1.7Ghz cpus. The clients are a mix of P3s and P4s. The OS is Ubuntu 8.10. Edubuntu is also installed. When more than a few machines are booted the cpus both run at 98-100% and everything grinds to a halt.

Any suggestions?
Please bear in mind we are newbies to Ubuntu and Linux. Please be gentle with us as we are not very au-fait with computing!

Hi, I don't know much about Ubuntu Server edition, but you could run "top" to see what process or application is using up all the CPU. Press "c" to see top CPU usage, or "m" for top memory usage.

Further information here:

[http://www.informit.com/articles/article.aspx?p=770644](http://www.informit.com/articles/article.aspx?p=770644)


.

---

### Post by pjbharrison on 2009-06-07
Thanks for the reply.
Unfortunately that webpage doesn't make sense to me. Got anything in english?  :)

---

### Post by jbruced on 2009-06-07
Ok, I haven't had experience with this either, but I did a little research.

Have you read:

[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient)

A lot of things can cause problems, 

high graphics applications,
regular hubs instead of high speed switches etc..

Are you the IT person in charge?


These forums are great, I'm sure you'll get some very qualified help soon.

May I suggest you try launchpad.net (the Ubuntu section), there seems to be a high geek level there sometimes.

Gl
I'll check back(want it to work for you)

Bruce


[edit] other possibilities
[QUOTE]=
Hard drive SCSI is faster than IDE: We've seen LTSP servers slow to a crawl when more than 10 clients are running from IDE drives. SCSI drives are better equipped to handle the multiple read/write requests.[/QUOTE}

---

### Post by jbruced on 2009-06-07
Ok, I haven't had experience with this either, but I did a little research.

Have you read:

[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient)

A lot of things can cause problems, 

ide drives in the server(instead of scsi),
high graphics applications,
slow network cards,
regular hubs instead of high speed switches etc..

Are you the IT person in charge?

These forums are great, I'm sure you'll get some very qualified help soon.

May I suggest you try launchpad.net (the Ubuntu section), there seems to be a high geek level there sometimes.

Gl
I'll check back(want it to work for you)

Bruce

---

### Post by pjbharrison on 2009-06-08
Hi jbruced

Thanks for the reply.
We have fulfilled all of the requirements on the 
[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient)  page.
All machine boot fine. All the thin clients have 10/100 lan cards and 32Mb graphics cards. They are minimum P3 1Ghz with 256Mb ram. Some are P4 2.8hz with 512MB ram. The switches are either 10/100 or gigabit.
I'll check the Hard Drive in the server. Its a Dell Precision 530 and I think it has a SCSI H/D. 
Regards
Paul

PS A friend of a friend suggested something about reducing caching and also mentioned mmu?
Any idea what he meant? I haven't been able to contact him about it.

---

