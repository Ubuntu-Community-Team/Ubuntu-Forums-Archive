---
title: "Email sending issues.."
date: 2012-12-28
forum: Server Platforms
---

### Post by springs1 on 2012-12-28
Hi all,

I'm running ubuntu server and having issues on sending email from the command line using the "mail" command.

each time i try to send emails i get a returned delivery message. I remember when i installed the OS that it asked for a domain name and i stupidly put in the one i wanted to use for system emails.

Is there a way to remove this and return the machine back to how it would normally send emails?

---

### Post by sffvba[e0rt on 2012-12-28
*Thread moved to **Server Platforms**.*


404

---

### Post by d4rk0wl on 2012-12-29
Are you using postfix or sendmail?

On postfix you can edit the main.cf file in /etc/postfix or you can run
```
sudo dpkg-reconfigure postfix
```
to generate a new main.cf file and be prompted with the same questions as you were upon installation

Regards,
D4rk0wl

---

### Post by springs1 on 2012-12-31
thanks for the info.

This it was an issue with postfix.

turned it off, installed sendmail and worked out the box.

---

