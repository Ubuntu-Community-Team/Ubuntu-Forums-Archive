---
title: "More Secure Server"
date: 2015-11-10
forum: Security
---

### Post by malb2 on 2015-11-10
Hi all,

I am new to Ubuntu and have an interest in web development. Before I start digging my heels into developing, I want to make sure my server will be secure. Like many others I worry about the sole sudo password and firewall options and want to know if there is anything I could do to reinforce that. I am running a machine with a pre-installed version of Ubuntu - so no virtual box. However, I do like the idea of keygen authorization. Is there a way I can use keygens still? - for instance, would it still work if I created another profile and made a key for that profile , or would that be redundant? What other options are there? 

Thanks for the help!

---

### Post by CharlesA on 2015-11-10
Have a read here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

It is geared for the Desktop but some apply to servers too.

I usually only create a keypair for the main users and allow them to login via SSH. If I need root access, I can either su to root or use sudo to gain root privileges. Easier to deal with imo.

---

### Post by robboguy on 2015-11-12
I found this guide useful [http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/), also I would go for an LTS version

---

### Post by mastablasta on 2015-11-12
while I found this one usefull: [http://hardenubuntu.com/](http://hardenubuntu.com/)

basically: 
- use sudo
- use keys
- use users for non admin tasks
- learn how to assign permissions and about file permissions
- use fail2ban or similar (make sure you create permanent jail)
- use unattended updates for security patches
- use firewall if needed
- AUTOMATIC BACKUPS!!!

there are more, but the more you complicate the more inconvenient for the users. good automatic backup is most important.

for development itself I found it is easier and faster to use virtualbox. you can save a snapshot and if you mess it up just restore it. take about a minute on my 11 year old single core PC. also there are premade images so you dont' have to loose time with installing and such. just unpack, deploy (Turnkey Linux, Bitnami stack...) in vbox and start developing.

good luck, have fun and post back if you are uncertain about some things.

---

