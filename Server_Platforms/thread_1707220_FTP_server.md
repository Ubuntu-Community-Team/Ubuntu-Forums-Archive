---
title: "FTP server"
date: 2011-03-15
forum: Server Platforms
---

### Post by nikhillife11 on 2011-03-15
Hey all,

I want to make my UBUNTU system a FTP server. I am begineer.. All I want is i can share photos and some files from my Ubuntu System at home to my system at my workplace and if need somewhere else too. I have a traveling job.So if anyone can help me with it or have a better idea can help me out...

Thanks

---

### Post by Kozley on 2011-03-15
Here's a [COLOR=Blue][tutorial]("http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-10.04-lucid-lynx")[/COLOR] about how to setting up proftpd with TLS (*Transport Layer Security*). But you didn't tell us which ubuntu version you use and the tutorial is to 10.04 but I think it would work for 10.10. Just skip out hostname and use your external ipaddress.

When you begin generate the SSL certificate as follows:
```
openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem
```Replace -days 365 to -days 3650, this make to 10 years.

Now you can edit your path where you want on /etc/proftpd/proftpd.conf:
```
[...]
# Use this to jail all users in their homes 
DefaultRoot            /path/to/your/own
[...]
```

---

### Post by Lars Noodén on 2011-03-15
If you can connect to the server with SSH then you already have SFTP installed and running and don't need to spend time on fiddling with FTP.  

Also, on your desktop you probably already have at least one [graphical SFTP client](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients)

---

### Post by nikhillife11 on 2011-03-16
Hey Lars,

Can u explain..I am weak at protocols and want to understand them better,So can you just eloberate what you meant.

Thanks

Also thanks to Kosley for the Idea...I will get back to you soon mate..

---

### Post by Lars Noodén on 2011-03-16
In a nutshell, [FTP is insecure](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol), SFTP is secure.  FTPS is hard to configure, [SFTP requires no additional configuration](http://howtoforge.com/node/5928).  FTPS and FTP require special client software, SFTP does not.

How did you first hear of FTP?

---

### Post by sherl0k on 2011-03-16
If you have shell access you can SFTP into a box using your usual login credentials. Filezilla supports SFTP out of the box and your session acts just like you were doing regular FTP.

---

