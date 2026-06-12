---
title: "vsftpd help"
date: 2009-02-16
forum: Server Platforms
---

### Post by P8ntBal1551 on 2009-02-16
How do you get vsftpd to allow connections over the internet? Because my friend can't connect to my server over the internet when he types in my IP into an ftp client.
Also, how do i make it so every user can only access their root folder?

---

### Post by brian_p on 2009-02-16
> **P8ntBal1551 said:**
> How do you get vsftpd to allow connections over the internet? Because my friend can't connect to my server over the internet when he types in my IP into an ftp client.

If you have a router you need to do some forwarding.

---

### Post by P8ntBal1551 on 2009-02-16
> **brian_p said:**
> If you have a router you need to do some forwarding.

ya i sorta figuredf that one out, that's my isp blocking that, i already forwarded that port.
but i would like help on the other problem, all the users that sign into the server all go to the same folder
also the server isn't needing passwords for some reason.....

---

### Post by P8ntBal1551 on 2009-02-17
bump;
how do you get vsftpd to have a different folder for different users that sign in?

---

### Post by HermanAB on 2009-02-17
Vsftpd and Proftpd should work the way you want out of the box.  If you changed the configuration file, change it back and restart it.

Cheers,

Herman

---

### Post by brian_p on 2009-02-17
> **P8ntBal1551 said:**
> bump;
how do you get vsftpd to have a different folder for different users that sign in?

Along these lines?

[http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html)

---

### Post by P8ntBal1551 on 2009-02-17
> **brian_p said:**
> Along these lines?

[http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html)

thank you :D

---

### Post by P8ntBal1551 on 2009-02-18
ok but now all the files are going to one folder

---

### Post by P8ntBal1551 on 2009-02-18
never mind, I figured it out

---

