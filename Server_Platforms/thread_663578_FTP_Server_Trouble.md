---
title: "FTP Server Trouble"
date: 2008-01-10
forum: Server Platforms
---

### Post by Ikith on 2008-01-10
I've been having a lot of trouble setting up and starting an FTP server. I've used proftpd and gproftpd and I get it all setup and hit activate to start the server and I get an IPv6 hostname error I look through the config and it seems to have gotten rid of the IPv6 on and off configuration. I look through the UI and no luck there. I try to connect to it with the user name I setup and the connection doesn't go through. I have my router set up to foreward port 20, and 21 to that computer.

Are there easier to set up ftp servers or help for the above problem. I need something that allows me to create multiple users and put them in a sub directory inside of apaches www folder.

---

### Post by bunnynuts on 2008-01-12
I'm not certain that it is easier, but vsftpd is fairly simple. Additionally, there are multiple 'how-tos' posted in these and many other forums. You can set up the config file to designate a directory inside of /var/www. Depending on how much you trust the ftp users you may want to look into chroot and possibly having the ftp directory outside of /var/www.

---

