---
title: "vsftpd won't run after update on Ubuntu"
date: 2017-03-16
forum: Server Platforms
---

### Post by tonysamperi on 2017-03-16
Hello,

I open this thread because I'm really stuck and I don't know what to try anymore.

A few hours ago I decided to upgrade Ubuntu, since v 16 LTS was out.
I did't manage to do that due to some dependency error, but I found I had to run "sudo apt dist-upgrade" and I did.
So I have Ubuntu 14.04 now.

After that I wasn't able to connect FTP through filezilla (on Windows) anymore

Service VSFTPD is in status stop/waiting. I run sudo service vsftpd start but nothing happens.

Here's my vsftpd.conf

[ATTACH]274176[/ATTACH].

Hope anyone can help

Thank you in advance

---

### Post by cariboo on 2017-03-16
Did you try:

```
sudo systemctl start vsftpd.service
```

---

### Post by tonysamperi on 2017-03-16
> **cariboo said:**
> Did you try:

```
sudo systemctl start vsftpd.service
```


```
sudo: systemctl: command not found
```

It's not a matter of command. There's something wrong with the config. I can't understand what

---

### Post by cariboo on 2017-03-17
It looks like your upgrade didn't finish. Try:

```
sudo apt-get install -f
```

---

### Post by tonysamperi on 2017-03-17
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It seems it finished.

Yesterday I managed to start the service by running a clean install of vsftpd and changing options in the vsftpd.conf,
but when connecting from filezilla I got "ERRCONNECTION REFUSED"

---

### Post by tonysamperi on 2017-03-17
I upgraded to Ubuntu 16 and I made a fresh install of vsftpd.

Now the service is running and I can connect from the terminal, but I get "Wrong password" even if it's correct.
I cannot connect from outside, Filezilla remains hanged.

I also added 
```
vsftpd: ALL
```
in my /etc/hosts.allow

I attached my new vsftpd.conf

[ATTACH]274190[/ATTACH]

---

### Post by tonysamperi on 2017-03-17
I uninstalled everything and I installed proFTPd.

Now everything looks fine even with TLS.
I tested from Online FTP tester ([https://ftptest.net/](https://ftptest.net/)) and everything works fine,

but I still can't connect from Filezilla. It wont pass the "AUTH TLS" command

---

### Post by tonysamperi on 2017-03-17
And I made it.

The only way filezilla can work is forcing unsecure ftp.

Thank you everyone.

---

### Post by LHammonds on 2017-03-17
I seem to recall having issues with my external clients using FileZilla to connect to my vsftpd server (still running on Ubuntu Server 12.04 !!!)

It had to do with the supported encryption for the FTP server.  I think FileZilla client wants to connect using an older set of encryption protocols and you have to configure vsftpd to make use of those other protocols.

For those seeing this post in the future and having FileZilla client + vsftpd connection issues, this might help:

Not 100% sure this is all that needs to be done cause my memory sucks but I do know I added the following to the end of the /etc/vsftpd.conf file:

```
ssl_ciphers=HIGH
```

Here are some related posts:
[ No shared cipher suite between FileZilla and vsftpd/openssl ](https://forum.filezilla-project.org/viewtopic.php?t=23275)
[How to set up a secure FTP service with vsftpd on Linux](http://xmodulo.com/secure-ftp-service-vsftpd-linux.html)

---

