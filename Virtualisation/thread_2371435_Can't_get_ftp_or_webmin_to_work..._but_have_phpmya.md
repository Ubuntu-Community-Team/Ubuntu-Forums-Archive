---
title: "Can't get ftp or webmin to work... but have phpmyadmin and wordpress ok"
date: 2017-09-14
forum: Virtualisation
---

### Post by vgledhill on 2017-09-14
Hi you knowledgeable people.

Please can you help?  I have ubuntu running on a virtual box on my mac.  I have set up virtual directory structures and all the test html works.  

I then installed phpmyadmin and that works fine.  I have also setup a wodpress site on one of the domains and that works fine, except I can't update anything because of FTP.

Here's my problem.  I can't get webmin to work even though I have installed it as per directions [here]("http://www.meestuff.com/install-webmin-ubuntu-17-04/") and same with VSFTPD   I have been scratching my head and trying everything I have read from google, but still nothing with these two programs.  

Thanks in advance 
Vince.

---

### Post by mastablasta on 2017-09-14
webmin should not be used in ubuntu as some people reported weird things happening. there are other server GUIs (e.g. Zentyal, Ajenti...)

use sFTP instead of FTP. install OpenSSH , setup the keys (or just passwrod if this is a VM) and you should be good to go.

---

### Post by slickymaster on 2017-09-14
*Thread moved to **Virtualisation**.*

---

### Post by vgledhill on 2017-09-14
I don't simply want to transfer files via the terminal.  I want to use a graphic file transfer program like filezilla or something.  I also need the FTP to work because wordpress needs it in order to update and install plugins and themes.

---

### Post by vgledhill on 2017-09-14
I have followed this guide [https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-16-04)

To try and set up vsftpd and get as far as section 5 testing the connection.  But it fails.  In terminal on my mac when I try to connect, I get an operation timed out message.  Can't connect.

---

### Post by TheFu on 2017-09-30
filezilla supports sftp.

Very few people use webmin (or similar) on Ubuntu.  We see it as another vector for an attack that someone can take over the system. Learn the CLI interface.  It is faster, once you know how.

I can't help with FTP. Haven't used that dead protocol since the 1990s.  It should have been killed off back then.  **A quick google found that updating wordpress via sftp is possible.**

---

