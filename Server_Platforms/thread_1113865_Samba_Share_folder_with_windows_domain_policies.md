---
title: "Samba Share folder with windows domain policies"
date: 2009-04-02
forum: Server Platforms
---

### Post by aleroot on 2009-04-02
I have installed a Ubuntu Server in a Windows Enviroment , where i have a Windows Domain (Win 2003 PDC).

I have joined Ubuntu Server to the domain with Likewise, and everything is ok .

But How i can share a folder in my ubuntu server with windows domain permission(Like other windows Server) ? 


Thank in advance for answers !

---

### Post by senor_smile on 2009-12-04
I would like to know how to do this same thing.  I have tried likewise and can log into my ubuntu machine with the windows server 2003 active directory credentials, but I haven't figured out how to get my samba shares from the ubuntu machine to be accessible from another machine on the network using the active directory credentials.  I have tried searching but am turning up little results.

---

### Post by senor_smile on 2009-12-04
I spoke too early.  I may have found just the thing on likewise's website: 

[http://www.likewise.com/resources/user_documentation/Likewise-Samba-Guide-51.pdf](http://www.likewise.com/resources/user_documentation/Likewise-Samba-Guide-51.pdf)

I'll post back with my results.

---

### Post by munky99999 on 2009-12-04
Ya. Create the samba share normally. Then add a foreign security principal in order to list it in directory. This works even if the ubuntu box isnt part of the domain.

I havent used likewise to have tried it the correct way. Looks like you may have found it.

---

