---
title: "Ubuntu Server Config for XP Clients"
date: 2008-07-20
forum: Server Platforms
---

### Post by JohnFurner on 2008-07-20
Just installed Ubuntu Server 8.04. I need a jump start.

Got Ubuntu Server Guide, but it does not have steps to setup XP clients.

What is best step-by-step guide to get my XP PCs to see my Ubuntu Server?

Also, what is best guide to format my two 500 GB HDS. What is best format, not NTFS, right?

Sorry to bug you guys!

---

### Post by freebeer on 2008-07-20
It would be helpful if you posted what you wanted to serve to the Windows clients as that can have an impact on the answers.

The stock answer is usually Samba which allows your Windows client to share files on the Ubuntu Server.

You'll probably want to format the Ubuntu drives as ext3 (but others may have a different opinion depending upon what you want to do).

---

### Post by tinny on 2008-07-21
> 
Also, what is best guide to format my two 500 GB HDS. What is best format, not NTFS, right?


For your server machine? EXT3 is pretty standard...

> 
Got Ubuntu Server Guide, but it does not have steps to setup XP clients.


This is standard windows stuff and is outside of the scope of the Ubuntu documentation. 

> 
What is best step-by-step guide to get my XP PCs to see my Ubuntu Server?


SAMBA is the way to go. Have a look at this to get you started on the server side of your networking. [https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html)

---

