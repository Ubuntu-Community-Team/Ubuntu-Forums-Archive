---
title: "[SOLVED] File Transfer via gFTP"
date: 2008-11-14
forum: Server Platforms
---

### Post by frankleeee on 2008-11-14
I assume this is the right place in the forums. So I installed ssh and gFTP I can get the computers to recognize each other but how do I actually transfer files. I install both ssh and gFTP on 2 computers. A link to a manual or wiki or a explanation would be really helpful, as I have no clue to ssh.

---

### Post by HermanAB on 2008-11-14
Did you install the ssh-server?  You need both the server and client packages, then you need to run the server of course and open port 22 in your firewall.

Cheers,

Herman

---

### Post by binbash on 2008-11-14
[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

---

### Post by volkswagner on 2008-11-14
Not sure if you have been here.  Many questions can be answered.


[http://gftp.seul.org/readme.html](http://gftp.seul.org/readme.html)[http://gftp.seul.org/readme.html]("http://gftp.seul.org/readme.html")


Also try man pages for ssh.

```
man ssh
```

---

### Post by frankleeee on 2008-11-14
> **HermanAB said:**
> Did you install the ssh-server?  You need both the server and client packages, then you need to run the server of course and open port 22 in your firewall.

Cheers,

Herman

Yes I installed the ssh server I am not familiar with how to open ports though.

---

### Post by Philio on 2008-11-14
If you want to do SFTP then you just need to open port 22, assuming your running SSH on the default port.

---

### Post by frankleeee on 2008-11-14
> **binbash said:**
> [http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

I looked at this link before I posted, but not being a geek it is all greek to me, thanks though

---

### Post by Philio on 2008-11-14
gFTP is an FTP client, not a server.
If you want an FTP server you will need to install something like vsftpd, proftp etc.
However as you have installed the SSH server you don't nescessarily need a separate FTP server as you can do FTP over SSH aka SFTP (Secure FTP).

---

### Post by frankleeee on 2008-11-14
> **volkswagner said:**
> Not sure if you have been here.  Many questions can be answered.


[http://gftp.seul.org/readme.html](http://gftp.seul.org/readme.html)[http://gftp.seul.org/readme.html]("http://gftp.seul.org/readme.html")


Also try man pages for ssh.

```
man ssh
```

I had looked at this page before posting but was unable to find the right answer but I probably didn't try hard enough. I am unfamiliar with opening ports, the computers will recognize each other with 
ssh localhost in the terminal, but I have no clue where to go from there. I installed gFTP as it was recommended for easy file transfer, I am not really sure who the host or user is in gFTP. The host appears to be the computer I am using. I know this probably sounds rather confusing but I am not familiar with this ssh stuff.

---

### Post by frankleeee on 2008-11-14
> **Philio said:**
> gFTP is an FTP client, not a server.
If you want an FTP server you will need to install something like vsftpd, proftp etc.
However as you have installed the SSH server you don't necessarily need a separate FTP server as you can do FTP over SSH aka SFTP (Secure FTP).

Yes I realize that, I downloaded it as it seemed it might make things easier, but this does not seem to be the case. Fortunately I have a friend who is setting up a dual boot on a apple computer right now and will get me set up with the correct instructions on how to use the ssh sever to transfer files. Thanks for your comments.

---

