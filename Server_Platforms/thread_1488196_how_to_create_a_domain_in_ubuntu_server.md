---
title: "how to create a domain in ubuntu server"
date: 2010-05-19
forum: Server Platforms
---

### Post by franco_85 on 2010-05-19
i need your help, i´m new in ubuntu server
and i want to know  what program to use in ubuntu server to administer pc´s and users,
for example in windows server i used  Active directory to do so but what can i use in Ubuntu???
i need to:
1 create a domain
2 addd pc´s to that domain
3 add users 
Thanks for your help!!!!

---

### Post by jjcv on 2010-05-20
Have a look at **samba**.

[http://wiki.linuxquestions.org/wiki/Setting_up_a_Samba_Server#Configuration]("http://wiki.linuxquestions.org/wiki/Setting_up_a_Samba_Server#Configuration")

---

### Post by franco_85 on 2010-05-20
i´ll look at it, i though that samba was just to share folders with windows OS

---

### Post by volkswagner on 2010-05-20
A little help on the search strings.

Samba as a PDC (Primary Domain Controller)

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

Turnkeylinux has a [prebuilt VM]("http://www.turnkeylinux.org/domain-controller") if you have the means to check it out.

---

