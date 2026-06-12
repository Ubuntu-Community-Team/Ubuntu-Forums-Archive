---
title: "Server Vs Desktop"
date: 2008-08-17
forum: Server Platforms
---

### Post by davethewave83 on 2008-08-17
I installed server because I wanted to test out a LAMPP. I was wondering what the advantages of running Servuntu *my nickname for Ubuntu Server* are vs running a desktop version with LAMPP support, if any.

-Is it more secure
-Is it faster
-Is it more stable/less likely to get a kernel panic
etc? 

Thanks!

---

### Post by cariboo on 2008-08-17
> Is it more secure

I don't think there is any difference as far as security is concerned, if they both are box stock.

> Is it faster

Yes you don't have the overhead of running a gui.

> Is it more stable/less likely to get a kernel panic

Yes because you usually don't run cutting edge software on a server.

Jim

---

### Post by Oldsoldier2003 on 2008-08-18
> **cariboo907 said:**
> I don't think there is any difference as far as security is concerned, if they both are box stock.


There is an argument that Server is more secure for the reason that there are less packages that can have code vulnerabilities. Since you don't have X or a bunch of applications installed, there are fewer "points of entry".

[uhelp]/community/ServerGUI[/uhelp]

---

### Post by brian mcgee on 2008-08-18
> **davethewave83 said:**
> I installed server because I wanted to test out a LAMPP. I was wondering what the advantages of running Servuntu *my nickname for Ubuntu Server* are vs running a desktop version with LAMPP support, if any.

-Is it more secure
-Is it faster
-Is it more stable/less likely to get a kernel panic
etc? 

What is the 2nd P? Python? Perl?

Anyway, the server version has lower system requirements, so you'll see a bigger performance difference on older machines. The command line isn't more or less stable, but since that's what you'll be using (most likely), your interface will be more stable. The biggest advantage is that fewer processes will be able to error and consume unusually high CPU time.

As far as security goes, if you purpose the server version with the ubuntu-desktop metapackage installed as a server, you're not necessarily going to sacrifice security, since GNOME won't likely be used for anything except administration. Honestly, the bigger concerns are open ports, running services, keeping the box up to date etc. Don't worry too much about a DE. That said, I prefer no desktop environment on my servers. Keep it clean, keep it simple.

I've seen the server version do amazing things on a decade old Compaq desktop. Try it for a few months, and let yourself get used to it.

---

### Post by The Titan on 2008-08-18
> 
I've seen the server version do amazing things on a decade old Compaq desktop. Try it for a few months, and let yourself get used to it.


I use ubuntu server on a garbage can computer, 500mhz and i stuck 3 256mb RAM and a 60g HDD and it works great for a local file server.  Now im going on to do more interesting things with it but yeah...  Point of the story is, Secure and Fast.  Moreso than desktop? No idea.

---

