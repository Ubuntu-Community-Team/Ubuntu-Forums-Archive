---
title: "I need help connecting a linux to a server 2000 domain"
date: 2009-07-14
forum: Server Platforms
---

### Post by grizzyfizzy on 2009-07-14
Hello I am a newbie to linux so any help would be nice. I need to connect my linux to a windows 2000 domain server at work. I have tried samba but cannot seem to make it work.

---

### Post by juancarlospaco on 2009-07-14
Samba connect with folders, shares, and printers.
Likewise connect to the domain itself.
[I]You can use the resources of the domain without being inside them, 
but it ask authentication eveytime you use it.[/I]

---

### Post by Vegan on 2009-07-14
> **grizzyfizzy said:**
> Hello I am a newbie to linux so any help would be nice. I need to connect my linux to a windows 2000 domain server at work. I have tried samba but cannot seem to make it work.

To get SAMBA to work with a Windows 2000 Server domain is straight forward but if you want to be able to use Windows Active Directory etc. then you need to set it up for that. There are a couple of books available to assist you with that level of interoperability.

I do not use Windows 2000 anymore as I dumped it in favor of Linux servers which do everything I want. You might want to consider the migration that way as in the long run you will be far happier.

---

