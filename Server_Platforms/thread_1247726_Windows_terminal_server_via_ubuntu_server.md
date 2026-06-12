---
title: "Windows terminal server via ubuntu server"
date: 2009-08-23
forum: Server Platforms
---

### Post by j-ring on 2009-08-23
Hello, I would like to ask you, if there is any possibility to connect a thin client, that would load a copy of Windows XP from the Ubuntu Terminal server? 
Thank you for your answers.

---

### Post by HermanAB on 2009-08-23
Yes.  It is commonly done, but maybe not the way you would think.

Install Virtualbox or VMware on Ubuntu, install Windows XP or Windows 2003 Server in that and connect to it using RDP Client from Windows.

---

### Post by j-ring on 2009-08-24
Thank you for your reply, but doesn't that allow to connect just one computer to the Server? I need to connect about 10 thin clients. I need this for my graduation project and I can not use Windows servers...

---

### Post by HermanAB on 2009-08-24
WinXP supports one RDP client.  Win2003 supports 3 RDP clients, but you can buy extra licences for more terminal server clients.  

Alternatively, you could run 10 Windows XP virtual machines and have each user connect to a different one, by setting the RDP port in the XP Registry to a non-standard value.

---

