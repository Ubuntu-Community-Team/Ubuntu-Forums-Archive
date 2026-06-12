---
title: "a good FTP server"
date: 2008-06-21
forum: Server Platforms
---

### Post by DFord425 on 2008-06-21
What is a good FTP server program to install? What is good a beginner who wants to learn. Does apache have an FTP server built in or is it just a web server?

---

### Post by windependence on 2008-06-21
What exactly is it that you want to do? If you just want to put web files on your webserver, I would suggest WinSCP (from Windows) or SCP from another Linux box instead of installing a full blown FTP server. If you need one then VSFTP should work fine.

-Tim

---

### Post by DFord425 on 2008-06-21
Thanks, i installed vsftp, but im not able to connect to it. Im trying to use FireFTP. When i log in do i use my username/password to log in for the FTP server?

---

### Post by ginjabunny on 2008-06-21
you need to configure it, look at /etc/vsftpd.conf there are lots of comments in it, also unless you intend to allow anonymous use then I suggest you disable it.

---

### Post by DFord425 on 2008-06-21
I congifured it following this example 
[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html). Is that a good config, i didnt see anything in their about logging in.

---

### Post by undertakingyou on 2008-06-21
For what it counts I use proftp and it works great.  Easy to set up and use.

---

### Post by windependence on 2008-06-21
> **undertakingyou said:**
> For what it counts I use proftp and it works great.  Easy to set up and use.

Equally as good IMHO.

-Tim

---

### Post by jeremy1138 on 2008-06-21
There is a really cool server program that I have for windows called HTTP File Server.  It has many features and is very customizable...  There is only minimal configuration required and it doesn't even require any installation process.  All you have to do is save it on your computer and open it.  It's great.  Is there anything like that available from Linux?  Here is the website:
[http://www.rejetto.com/hfs/?f=intro](http://www.rejetto.com/hfs/?f=intro)
Take a look.

---

### Post by chocbar31 on 2008-06-22
Konqueror!

---

### Post by ginjabunny on 2008-06-22
it seems that vsftpd is not setup to allow PASV mode by default, so when I used gftp it won't connect if I specify port 21 but will connect if leave it blank, so I presume it connects on port 20, if you want to force PASV mode connections the you have to change the vsftpd.conf line

connect_from_port_20=NO

---

### Post by cheruvim on 2008-06-22
Most clients will try PORT and then if that doesn't work it will fail over to PASV mode... I think pasv_enable is defaulted to YES on vsftpd. However, you would be wise to set pasv_min_port and pasv_max_port in the configuration and then open those ports on your firewall if applicable.

---

### Post by cariboo on 2008-06-23
I have to put my vote in for proftpd, it works right out of the box.

Jim

---

### Post by DFord425 on 2008-06-24
I am still unable to connect. Im using a computer that is wirelessly connected to one router while the FTP server is connected to another router that is wirelessy bridged of the first router. I turned the firewall off on the bridge router, should i configure the firewall on the first router? I didnt think about that because the connection is not coming from the modem.

---

