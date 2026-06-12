---
title: "Install Server or Default"
date: 2005-06-15
forum: Server Platforms
---

### Post by echokilo on 2005-06-15
I want to install Ubuntu and use it mostly as a Samba server. 

Should I install using the Server or Default install? 

If I don't start X-Windows, what additional services will be installed using the default install?

---

### Post by Trickyphillips on 2005-06-15
The 'Default Install' has chat programs, image editors, web browsers, text editors, media players, games, and many applications that a server doesn't need.

---

### Post by echokilo on 2005-06-16
Am I correct in saying that if I don't login to X-windows, these services won't start, but I will have the option to use X windows?

---

### Post by Trickyphillips on 2005-06-16
[QUOTE=echokilo]Am I correct in saying that if I don't login to X-windows, these services won't start, but I will have the option to use X windows?[/QUOTE]
 Only the services in init.d will run on startup. 

I suggest using the 'Server Install', then installing X. If you don't care about hard drive space at all, you could use the 'Default Install' for what you're trying to do.

---

