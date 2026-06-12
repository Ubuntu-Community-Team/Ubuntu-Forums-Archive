---
title: "User auth. -  Ubuntu Server w/ Ubuntu Desktop"
date: 2007-03-18
forum: Server Platforms
---

### Post by mvip on 2007-03-18
Hi Ubuntu folks,

With the Desktop improvements of the latest releases of Ubuntu Desktop I'm seriously considering migrating on of the offices I administrate completely over to Linux. All the software that is not available for Linux will run under Wine, so no problems as far as that is concerned. 

My thoughts is to install a server with Ubuntu Server, and then Ubuntu Desktop on the clients (a handful of them). The only thing I really need from the server is to share files, but I would also like to have central user management. 

Now, as far as I know, there are two ways to go when it comes to central user authentication; Kerberos or Samba w/ PDC. Kerberos seems to be the hardcore Unix-way to do it, while Samba PDC is more like a mixed-enviroment solution. Both of these solutions may use OpenLDAP as a backend, which is great. And as for the file-sharing, I guess NFS goes with Kerberos, while obviously Samba takes care of the Samba file-sharing.

What I really want to know is what kind of experience people have when it comes to this. Which is the most 'ubuntu:ish' way to go, and what would work with the least amount of tweaking/hacking?

I know Fedora supports PDC user-logins out of box, but i'm not sure if Ubuntu Desktop does the same.

---

### Post by mvip on 2007-03-20
Seriously, have nobody done this with Ubuntu Server/Client? Central user management feels like a required feature if you have more than like 2 clients. 

Another option is to use NIS, which would also solve the problem. However, I'm interested in people's experience on the subject matter. 

How do the Ubuntu-folks solve their central user management?

---

### Post by Mr. C. on 2007-03-20
You have to define what type of clients you expect to be managing.

In an all Unix/Linux environment, you can use NIS, LDAP, or rsync your use databases.

In a Unix/Linux/Windows world, you can use LDAP, or Samba PDC.

With under 20 users/desktops, I wouldn't consider a heavier, more complex or expensive solutions.  Simple, understandable, manageable administration has higher priority than an all-encompassing solution.  This is especially true with light turnover or new hires.

When you get to 75+ users, in mixed environments, then it might warrant the larger solution.  

MrC

---

