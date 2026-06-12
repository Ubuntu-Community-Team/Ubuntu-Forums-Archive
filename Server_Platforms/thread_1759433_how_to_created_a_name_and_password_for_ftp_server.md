---
title: "how to created a name and password for ftp server"
date: 2011-05-15
forum: Server Platforms
---

### Post by Fertech on 2011-05-15
I'm using Ubuntu 10.4  i set up the ftp server and config it. i'm trying to created name and password for my sister so she can login into my ftp server.

I also have one more problem, at this point i can only login into my internal ip, and when i try to login with the external ip, it wont let me in. so at this point i can only login on my local network.

---

### Post by Lars Noodén on 2011-05-16
Try using SFTP, it's part of the package openssh-server.  Unlike FTP, it is secure.  To set up a user for SFTP, just create a user on your system.  Then it just works.

---

### Post by terazen on 2011-05-16
Try "man adduser" to add your sister.

For the external ip problem, do you have multiple interfaces on your server or are you using 1 ip address?  You may need port forwarding setup on your home router.

---

### Post by Fertech on 2011-05-18
okay Lars Noodén, I download the openssh server. where is the config file and sftp folder.I can't seem to find it. I look in /var and in /etc and it's not there.

---

### Post by Lars Noodén on 2011-05-19
> **Fertech said:**
> okay Lars Noodén, I download the openssh server. where is the config file and sftp folder.I can't seem to find it. I look in /var and in /etc and it's not there.

The configuration file is **/etc/ssh/sshd_config**

The SFTP folder is the user's home directory, but that can be changed with [OpenSSH's built-in chroot](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) functionality.

---

### Post by Fertech on 2011-12-02
How can I login from the browser to my sftp server what do I type in the url

---

### Post by Lars Noodén on 2011-12-03
Browsers tend not to support SFTP.  Your file manager probably does.  Try in Nautilus or Dolphin.

sftp://example.org/

---

### Post by Fertech on 2011-12-04
Is sftp is port 21 too.

---

### Post by Lars Noodén on 2011-12-05
> **Fertech said:**
> Is sftp is port 21 too.

SFTP is port 22, just like SSH.

---

### Post by Fertech on 2011-12-05
how can i test if the sftp server is up and running?

---

### Post by Lars Noodén on 2011-12-06
> **Fertech said:**
> how can i test if the sftp server is up and running?

You can try connecting to it in Nautilus or FileZilla.  In Nautilus:

File->Connect to Server->Type->SSH

Or via the shell:

```

sftp *somehost.example.org*

```

---

