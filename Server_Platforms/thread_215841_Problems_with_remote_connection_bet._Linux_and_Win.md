---
title: "Problems with remote connection bet. Linux and Win using SSH and Putty"
date: 2006-07-14
forum: Server Platforms
---

### Post by cocotu on 2006-07-14
Hi guys, I'm a total newbie doing these things. I have a LAMP server set up at work on the 4th floor and I'm trying to have a remote connection from my Windows machine on the 6th floor. I installed the openssh-server on the LAMP and putty on the win machine. The first time I tried to log in I got this message: "The server key was not found in the cache. You have no guarantee that the server is the computer you think it is. The server's rsa2 key is: ssh-rsa [some key]. If you trust this host, press Yes. To connect without adding to the cache press No. To abandon the connection press Cancel"

I press Yes. Then it ask me for the "log in as:" So in this case I'm not sure what to enter. In the LAMP machine I only have the root account set up, so I entered at putty and then the password. I'm not able to connect this way. Do I have to set up another user for remote access? I confused about this and I have read the instructions on help.ubuntu.com with no success. Do I have to configure the /etc/ssh/sshd_config file and create an user account?? What is the simplest way of doing this? And if I achive this task would I be able to connect from home? Right now I'm getting "Access Denied" error.

Thanks guys...

---

### Post by FredSambo on 2006-07-14
are you sure you are root?  

did you create a user name and password during install and afterward (once at the login prompt) did you log on under that account and then enable the root account?

---

### Post by FredSambo on 2006-07-14
you should be able to log on using your original user name and password (not root).

---

