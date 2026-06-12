---
title: "is VSFTPD the best solution for virtual authentication?"
date: 2013-01-15
forum: Server Platforms
---

### Post by Demonarc on 2013-01-15
Ive been messing with Linux on and off for awhile now and finally decided to switch my home server to Ubuntu server. I have everything working great so far but ran into a ftp issue. What im trying to do is have multiple logins, 3-5 users at a time that have full read write delete access to a folder on my comp /share/share/. And also keeping them chroot 'd to that directory just encase its compromised.  After doing alot of research I was able to make accounts that were added to my /etc/passwd file with read write and delete privileges, but if a user posted the file another user could not delete it. Is it worth making a MySQL server and learning how to add username and passwords to it or is there a easier way? and if I have to use mysql with pam and vsftpd does anyone have a detailed walkthrough I could use? saw alot of weak ones that didn't explain anything  for a new user :(

I just formatted my comp to start everything over. :)

---

### Post by chadk5utc on 2013-01-16
I believe you can accomplish what you want with user management
[https://help.ubuntu.com/8.04/serverguide/user-management.html](https://help.ubuntu.com/8.04/serverguide/user-management.html)
I also suggest reading and becoming familiar with the server guide found here
 [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/) this is a great reference.
This one for securing SSH 
[https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)
All the security link are also worth reading
[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

---

