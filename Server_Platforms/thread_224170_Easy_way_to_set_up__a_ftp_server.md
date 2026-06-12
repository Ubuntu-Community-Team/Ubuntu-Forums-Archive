---
title: "Easy way to set up  a ftp server?"
date: 2006-07-27
forum: Server Platforms
---

### Post by jørgen on 2006-07-27
I want to set up a ftp server sp that i can acces my files from anywhere. 

What is the easiest way to do that if i have no prior experience with servers?

---

### Post by jørgen on 2006-07-27
Anyone? I have tried to search the forum and google for tutorials, but it doesn't work!

---

### Post by lamego on 2006-07-27
Install it:
```
sudo apt-get install vsftpd
```
Configure it:
```
sudo nano /etc/vsftpd.conf
```

---

### Post by jørgen on 2006-07-29
> **lamego said:**
> Install it:
```
sudo apt-get install vsftpd
```
Configure it:
```
sudo nano /etc/vsftpd.conf
```

That's not really an easy way. I have no idea how all those settings should be! Isn't there a wizard or something for Linux, just like it's for Windows?

---

### Post by chrisfay on 2006-07-29
> **jørgen said:**
> That's not really an easy way. I have no idea how all those settings should be! Isn't there a wizard or something for Linux, just like it's for Windows?

For the most part, no...

You can install a web based server monitor like webmin but that would be overkill if all you need is an ftp server. 

Try to sudo apt-get install the ftp server like above poster or, 
sudo apt-get install proftpd (my choice). Once you have it installed, the config file is really easy to modify. 

Steps:

1. Create a new user and group. I use group "ftp" for simplicity. Make sure and choose the folder for your user that you want to access through ftp. Add your new user to the "ftp" group.

2. Modify your proftpd config file to include:

user
ftp

(like this)
[IMG]http://cjfay.com/images/proftpd.jpg[/IMG]

To access your folder through ftp:
[ftp://usr@ip.com](ftp://usr@ip.com)

substituting usr for your user that you created and ip for your external IP. (you may have to open port 21 for inbound/outbound traffic if you use a router or firewall)

---

