---
title: "proper permissions of /home/users ?"
date: 2008-04-27
forum: Security
---

### Post by rompstar420 on 2008-04-27
What is the proper set of permissions that I should use when running a server that is open to the public on certains ports.  I allow port 80, FTP, and SS traffic to be forwarded to my local linux box.  So I run:

Apache
FTP Server
SSH Login

I want to make sure that I use the proper set of permissions so that everything is gravy from a security perspective.  Thanks ahead of time.

RompStar

---

### Post by hggdh on 2008-04-28
Well, it will all depend on what type os usage this box has. A good rule of thumb is: if it is open to the public on certain ports, then it is open to the public. Period. In other words, a potentially vulnerable system. So there is a whole truckload of things you should consider, not only /home!

But, generically, /home/<user> should be at *least* 750. On my machines it is 700 by default (which is to say, unaccessible by anyone else except root and the owner).

---

### Post by Dr Small on 2008-04-28
Here are a few pointers.

1) Don't use FTP. This is one of the most insecure protocols out there. If someone between your box and the destination (meaning ISPs or even people on the client end) are sniffing packets, it would be very easy to obtain the username and password for the FTP account on your box.

2) Secure down SSH. There are multiple ways to do this. It depends upon the type of traffic you will be receiving as to what measures to take. Your best bet is to change it to a non standard port, disable root logins, enable KeyBasedAuth and disable PasswordBasedAuth.

3) Securing Apache. There isn't much to be said here. Just make sure you have proper permissions set on files, and that they are not world writable.

4) Since we previously discussed FTP as being insecure, you can use SFTP. If you have SSH installed, then it is very simple to connect via SFTP. All you need is a FTP client that supports the SFTP Protocol. gFTP is one client that I know of and use that supports SFTP.

---

### Post by Oldsoldier2003 on 2008-04-28
Dr Small: I agree about FTP. the only valid reason left for ftp is anonymous ftp service (download only) and even that is debateable for most users.

---

### Post by rompstar420 on 2008-04-28
Thanks guys for your time and explanations.  I FTP locally from my network at home, I never FTP from the outside and no one else uses FTP, it's for my use only.  But I see your point, I will get started on securing and understanding, thanks!

I don't host for many people, it's just me right now, so I want to start learning on early in what I have to do.

Thanks!

RompNess

---

