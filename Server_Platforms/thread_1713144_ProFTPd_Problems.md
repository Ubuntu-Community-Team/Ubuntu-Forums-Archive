---
title: "ProFTPd Problems"
date: 2011-03-23
forum: Server Platforms
---

### Post by Jonakoudijs on 2011-03-23
Dear Ubuntu-friends/lovers/and so on,

I got a problem with a webserver of a friend of mine. My website is currently hosted on his server (and also a few other of my staging websites). In the beginning I installed ProFTPd on his webserver for easy access. It only never worked perfectly.

The problem is that when I download or upload a (big) file with FTP it works fine. But if want to copy for example a folder with a few more files (around 50) it breaks the connection and it will have to reconnect, then after 3/7 seconds it happens again and again, and.. you get the point. When I have a folder with a lot of files (+80) it crashes/breaks the connection at the moment it is indexing the files it has to copy.

I don't know what the problem can be, as far as I know the FTP server is configured correctly. I hope someone can help or push me a little in the right direction. If you got other suggestions or alternatives, it's no problem, I have full administrator rights to the server.

Thanks in advance!

---

### Post by falko on 2011-03-23
Did you try both active and passive transfers in your FTP client?

---

### Post by Lars Noodén on 2011-03-24
It might be time to retire old FTP.

If you can reach his server with SSH, then you already have SFTP installed and configured. You won't need any special [clients for SFTP](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) and turning off FTP means one less service to monitor and keep going.

SFTP is an easy, secure, and reliable way to transfer files.

---

### Post by Jonakoudijs on 2011-03-24
@falko yes, I tried both Active and Passive. It both didn't work as expected. I also tried disabeling the firewall but to no avail.

@Lars I know, I just have a hunch that if the normal FTP doesn't work, SFTP will also not work. Do you think that can make the difference/solve the problem?

---

### Post by Lars Noodén on 2011-03-24
> **Jonakoudijs said:**
> @Lars I know, I just have a hunch that if the normal FTP doesn't work, SFTP will also not work. Do you think that can make the difference/solve the problem?

Unlike FTPS, SFTP it's a different port, protocol and server software.  It's probably already installed and configured. So, yes it might work.

---

### Post by Jonakoudijs on 2011-03-24
> **Lars Noodén said:**
> Unlike FTPS, SFTP it's a different port, protocol and server software.  It's probably already installed and configured. So, yes it might work.

Ah ok right. Well I installed ProFTPd. You are saying I can use my existing ProFTPd installation? I assume I have uncomment this line in my config file:

```
#Include /etc/proftpd/tls.conf
```

What more do I have to do to setup the SFTP?

---

### Post by Lars Noodén on 2011-03-24
[proFTP does not do SFTP](http://proftpd.org/features.html) except as an [addon module](http://proftpd.org/docs/contrib/mod_sftp.html)

My main reason for suggesting SFTP is that you get it as part of openssh-server.  If you get it that way, it is easy and then there is no need for further configuration or other programs needed.  In short you will not need proFTP to transfer files securely and can uninstall it.

---

### Post by Lars Noodén on 2011-03-24
1. uninstall proftpd
2. install openssh-server, if it is not already there
3. connect using sftp client like Nautilus, Konqueror or FileZilla

---

### Post by Jonakoudijs on 2011-03-24
> **Lars Noodén said:**
> 1. uninstall proftpd
2. install openssh-server, if it is not already there
3. connect using sftp client like Nautilus, Konqueror or FileZilla

Ok great! Thanks for the fast responses!

I will try that. But where's the config I can edit. Because I need 3 users who get locked in their own directory. If there's no other way then it's ok, but I prefer the way that all three users are locked into their own directory.

---

### Post by Jonakoudijs on 2011-03-24
Allright, I've used some documentation from howtoforge.com and know how to put in the config file, now I only need to figure how to make it actually work!

But you were right, the first setup part is dead easy :D

---

