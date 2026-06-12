---
title: "Active Directory installation without any windows server?"
date: 2011-04-19
forum: Server Platforms
---

### Post by ozi_lion on 2011-04-19
Hello,

I want to know if there is any way to install and configure to use an active directory for domain controller in ubuntu server for using to authenticate both linux and windows client but without using any existed windows server. We want to use a local server for some reasons like user authentication and file sharing and etc. but do not have any existing windows server and i want to use domain group for our lan users to authenticate and allow them to see shared items on linux server. I searched the net but all I could find requires an existing and ready windows server with active directory and domain group. if possible how can i do that in ubuntu server without windows server?

thanks in advance,
best regards,

Ozcan Arslan

---

### Post by Fire_Chief on 2011-04-19
This post is a bit old but should get you close to working well.
[http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760")

Cheers!

---

### Post by ozi_lion on 2011-04-20
Thanks for your reply i will try and come back with results

---

### Post by HermanAB on 2011-04-20
Howdy,

Note that other Linux distros have wizards for that, so you could save yourself a lot of pain...

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Samba 3 is NOT capable of being an Active Directory Domain Controller. It's capable of acting as a Windows NT PDC/BDC though. Currently, there is no officially released Active Directory Domain Controller for any OS except windows. If you want client on XP with old style policies then go with Samba 3. If you want group policy on clients like Vista/7 etc, then your gonna need to test Samba4.

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

BTW, this is only in alpha stages, but i find that its still very stable and it tends to perform much better than Server 2008_R2 and 2003_R2.

---

