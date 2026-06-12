---
title: "Preventing cloning of Ubuntu 10.04 server"
date: 2012-03-26
forum: Server Platforms
---

### Post by deepakdeshp on 2012-03-26
Is it possible to prevent cloning of an existing  Ubuntu 10.04 server? It is not going to be a fresh installation. It will be a web server and the document root contents have to be accessible to the clients. Nobody will login or ssh to the user using Linux user id. I do not want to protect the /var/www contents but sytem files and configuration of the server.

---

### Post by spynappels on 2012-03-27
If no-one has access to the server, other than to upload websites to /var/www/ and you secure FTP properly (I presume you are using FTP rather than SFTP or SCP, you said no-one could SSH in) they should not be able to see the rest of the directory structure, never mind clone it.

Having said that, you need to secure physical access to the server too.

---

### Post by deepakdeshp on 2012-03-27
Physically I will not be able to prevent access to the server.

Encrypting partitions may not help at all as the users will have access to all the passwords as thay will be using the system. So there does not seem to be any way to protect it.

Best bet may be to disable the usb ports and lock the server cabinet. Though not fool proof it will make the effort to clone that much more difficult.

---

### Post by rubylaser on 2012-03-27
What is the use case for this server?  If I thought the people that might be working on my server where that untrustworthy, they would no longer continue to be employees.  I

f they're just web hosting users, just encrypt the partition and chroot users into their own directories and don't allow them anywhere else.

If they all have the passwords and physical access to the server anyways, you're just wasting your time.

---

### Post by deepakdeshp on 2012-03-27
The use case is as follows:-

The server will be offerred  to users as a service and I would be bundling some applications on them and offer support. Users are not the employees in my company. My competitors would like to clone it and offer it as their offering.

But the users will have physical access to the machine and have the passowrds to use the system as a web server from their client machines.

---

### Post by spynappels on 2012-03-27
If they have physical access, they will be able to do anything they like with it.
If the use case is as outlined, you cannot impose the restrictions you want. If you want the restrictions, the use case is flawed.

---

### Post by deepakdeshp on 2012-03-27
> **spynappels said:**
> If they have physical access, they will be able to do anything they like with it.
If the use case is as outlined, you cannot impose the restrictions you want. If you want the restrictions, the use case is flawed.

Why can not I impose the restriction? Can anybody clone what I build? I spend a lot of efforts for the server build.

---

### Post by spynappels on 2012-03-28
If you give physical access to the server to untrusted users, they can do whatever they like with it, including cloning it.

If you want to impose the restrictions you are talking about, a prerequisite is that you secure physical access.

You say you spent a lot of time building this server and want to secure it to protect your investment, but if your use case works against that, the use case is flawed.

Would you like to explain in a little more detail what you are actually wanting to do, and maybe we may be able to suggest alternatives?

---

### Post by deepakdeshp on 2012-03-29
> **spynappels said:**
> 
You say you spent a lot of time building this server and want to secure it to protect your investment, but if your use case works against that, the use case is flawed.


I installed and configured a number of applications on it like Nagios etc which is a time consuming and I spent a lot of time building the server. I feel that it would be unfair for somebody just to go ahead and clone it without any efforts.

But without physical access restriction it is impossible, I guess. Disabling usb ports, setting BIOS passwords were some things I thought about, but with physical access these can be over ridden. By the way can we set BIOS  password or restrict usb ports by Ubuntu commands?

---

