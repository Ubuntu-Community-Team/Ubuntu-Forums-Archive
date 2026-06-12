---
title: "Server &quot;lockdown&quot;"
date: 2009-01-18
forum: Server Platforms
---

### Post by lightningrod66 on 2009-01-18
Now that I have my Ubuntu 8.10 LAMP server running, I was wondering what is the best way to "lock it down" so that it is secure, and that only I (using a login) can add/edit/delete pages & files (from another computer or online).  Also, how can I test it to see how secure it is?

---

### Post by Eviltechie on 2009-01-19
If I get what you are saying, you should just be able to install a ftp server. Just make sure that your passwords are strong and you should be fine.

---

### Post by lykwydchykyn on 2009-01-19
I would skip ftp and just install ssh, then you can use sftp.  

Most things are configured securely by default, but anything can be more secure.  How secure do you want it to be?

---

### Post by Thirtysixway on 2009-01-19
You should get something like fail2ban to block bruteforce attacks against your system.  I also recommend changing the default port numbers on things like ssh and ftp to keep most of the automated scanners out there from finding your system's services.

---

### Post by lightningrod66 on 2009-01-19
I don't have a need for ftp, as I can connect to the server from another computer on my network to transfer files.  I have shared the /var/www folder with Samba on my network so that I can do this without ftp.  I was just wondering how to tell if someone (outside of my network) could access my server or not.

---

### Post by bigbearomaha on 2009-01-19
2 apps that can help a lot.

fail2ban and bastille

fail2ban to prevent bruteforce breakins and bastille to go through the system area by area and "lock it down"  ( bastille even has an undo feature if you find you made an error and want to redo it. )

Big Bear

---

### Post by lykwydchykyn on 2009-01-19
> **lightningrod66 said:**
> I don't have a need for ftp, as I can connect to the server from another computer on my network to transfer files.  I have shared the /var/www folder with Samba on my network so that I can do this without ftp.  I was just wondering how to tell if someone (outside of my network) could access my server or not.

If your server is behind a router, and you haven't forwarded any ports on the router, nobody can get to it (unless they hack your router, but at that point you have bigger problems).

If your server is directly connected to the internet and has a public ip (one that doesn't look like 192.168.xxx.xxx, 10.xxx.xxx.xxx, or 172.16-31.xxx.xxx), then you probably want to look closely at what services are running and what ports are open.

You might want to scan it using nmap from another machine.  If you have another ubuntu machine nmap is in the repositories.

---

### Post by lightningrod66 on 2009-01-19
My server IS behind a router.  I have forwarded only ports 80 (web), 3306(mysql), and 10000(webmin).  Anything I should be concerned with?

---

### Post by lykwydchykyn on 2009-01-20
Webmin could be a potentially dangerous thing to have open; if someone gets in there, it's all over.  Make sure
 - strong passwords
 - set webmin for some kind of lock-out on too many password failures
 - if you know what outside IP's you'll be using it from, limit access to those IP's.
  
As for mysql -- why do you have it open to the outside?  I'm not sure how secure that is.

---

### Post by lightningrod66 on 2009-01-20
> **lykwydchykyn said:**
> Webmin could be a potentially dangerous thing to have open; if someone gets in there, it's all over.  Make sure
 - strong passwords
 - set webmin for some kind of lock-out on too many password failures
 - if you know what outside IP's you'll be using it from, limit access to those IP's.
  
As for mysql -- why do you have it open to the outside?  I'm not sure how secure that is.

Thanks for the info.  I have setup webmin to lockout for failed login attempts, and removed the MySQL port forwarding. I don't know why I had that port forwarded?

Now, is there a way that I can check the security of the server?  For example, I can go to grc.com to check ports etc from my Windows computer.  Can I do something like this for my Ubuntu server?  Since my server is behind a router, its outside IP address is the same as my other computers, so I don't know what it is actually checking (router??).

---

### Post by lykwydchykyn on 2009-01-20
Well, you already know what ports are open.  It really comes down to the security of whatever code you're exposing to the world on those ports.

---

### Post by MeneM on 2009-01-20
Apart from the code you write, extra enhancements could be: Not using passwords with SSH, but only certificates.

Read this one as well: <[http://www.debian.org/doc/manuals/securing-debian-howto/]("http://www.debian.org/doc/manuals/securing-debian-howto/")>.

How is the firewall setup?
Snort (Intrusion detection system), logwatch, fail2ban, auditing, trying to break in yourself, enumerating, keeping everyting updated, etc.

Most importantly: Common Sense. Do not use "root" with the password: "3xtr3m3lys3cur3p4sswd" (Actually, that may be good... But root should not be allowed remote access. Always use "sudo")

Anyway's, entire dayjobs can be filled with this sort of thing ;-)

---

