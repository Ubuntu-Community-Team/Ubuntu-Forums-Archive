---
title: "Setting up a users rights"
date: 2006-08-17
forum: Server Platforms
---

### Post by jordans on 2006-08-17
Ok, I have a question. I am hosting a webserver and someone wants to have there website setup on the server. I only want them to be able to access /var/www/RJ . How do I go about setting it up so he can only access that one.

Thanks

---

### Post by Kurt` on 2006-08-17
How will they be accessing it? SSH? FTP?

With SSH, you could place them into a 'chroot jail'. Type 'man chroot' for info on that.

I've never setup a chroot jail over SSH though. I'm sure someone else can help you, or you can google for a tutorial easily. :)

Most FTP daemons support "jailing". Example:

Your buddy logs on with their credentials. They are jailed into /var/www/RJ automatically. Their FTP client displays / as their current location (they can't go "up" anymore). That way, they can only move around within that directory, and not traverse your entire system.

If you have any sort of scripting languages available (perl, php, etc), and they are able to upload/execute scripts, those scripts may be able to read/write to other files on your system. It is up to you to secure that.

---

