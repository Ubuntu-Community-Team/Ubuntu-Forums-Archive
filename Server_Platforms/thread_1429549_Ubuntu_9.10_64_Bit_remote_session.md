---
title: "Ubuntu 9.10 64 Bit remote session"
date: 2010-03-14
forum: Server Platforms
---

### Post by RajeshSharma on 2010-03-14
Hello All , 


Currently using Ubuntu9.10 Desktop 64bit >>>

I want to remotely login into  this Ubuntu pc  Gnome Desktop from my office Windows PC with a separate user and one particular application assigned to this user ID.

Kindly advise me steps on this .

Thanks
Rajesh Sharma

---

### Post by HermanAB on 2010-03-14
The absolutely easiest way is with SSH and X forwarding.  Search Google for XminGW and PuTTY for Windows.

---

### Post by RajeshSharma on 2010-03-14
> **HermanAB said:**
> The absolutely easiest way is with SSH and X forwarding.  Search Google for XminGW and PuTTY for Windows.

I know that for Unix there is something called as Go Global UX server and client .

i tried with SSH >>> SSH Server Installed on UBuntu , able to login from Windows Putty , but not able to open any graphical application on it . 


I tried using SSH with X setting on putty but no use . While opening any application within it Error came as Cannot connect to X server .

I m sure something is missing with me ,

---

### Post by RajeshSharma on 2010-03-24
Thanks Herman for response on it .

Finally i found solution to my requirement . I configured FreeNx server with SSH Server and its working perfect for me !

---

