---
title: "Windows 2000 AD Domain and Linux's place in it"
date: 2005-06-02
forum: Server Platforms
---

### Post by NewbieNik on 2005-06-02
Can Linux recognise Windows 2000 users? I have installed Ubuntu 504 and Apache, php, mysql, samba and winbind.
I have got apache running and a simple web-site (Its, me...it has to be simple)
I have Netjuke running for my own music.
I have shared folders available to my windows 2000 users (if I open them to everyone)
Wbinfo -g or -u gives me the groups or users on my domain.
What I cannot do is set permissions for Windows groups to access certain folders. e.g Administrators only to access the "data-admin" folder, standard domain users to access "data-shared" folder.
I have tried setting samba to allow "DOMAIN"\administrators, but it won't have it. I created a W2K group called LinuxUsers and then a Linux group called LinuxUsers and gave them permission, but if I add myself to the W2K group it still wont let me access any folder that LinuxUsers has access to.

Am I missing something hugely obvious (like a 30-stone woman in orange) or is it a bit more subtle (The 30-stone womans friend in a nice shade of light blue)

Any help anyone can supply will be read with great enthusiasm (unless it's wrong!! Then I cry like the man I am)

---

### Post by LordHunter317 on 2005-06-02
[QUOTE=NewbieNik]Can Linux recognise Windows 2000 users? I have installed Ubuntu 504 and Apache, php, mysql, samba and winbind.
I have got apache running and a simple web-site (Its, me...it has to be simple)
I have Netjuke running for my own music.
I have shared folders available to my windows 2000 users (if I open them to everyone)
Wbinfo -g or -u gives me the groups or users on my domain.
What I cannot do is set permissions for Windows groups to access certain folders. e.g Administrators only to access the "data-admin" folder, standard domain users to access "data-shared" folder.
I have tried setting samba to allow "DOMAIN"\administrators, but it won't have it. I created a W2K group called LinuxUsers and then a Linux group called LinuxUsers and gave them permission, but if I add myself to the W2K group it still wont let me access any folder that LinuxUsers has access to.

Am I missing something hugely obvious (like a 30-stone woman in orange) or is it a bit more subtle (The 30-stone womans friend in a nice shade of light blue)

Any help anyone can supply will be read with great enthusiasm (unless it's wrong!! Then I cry like the man I am)[/QUOTE]
 Yes you can do this.  I highly recommend you go to samba.org and read the relevant sections of the HOWTO and work through it first, and come back and post any issues/questions you have.  It explains the process of joining a Samba 3.x machine to an Active Directory domain much better than I can.

---

