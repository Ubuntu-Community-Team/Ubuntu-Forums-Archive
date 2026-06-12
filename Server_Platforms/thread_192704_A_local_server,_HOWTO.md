---
title: "A local server, HOWTO?"
date: 2006-06-09
forum: Server Platforms
---

### Post by Isoss on 2006-06-09
I posted something similar but now it's kinda different since this time there is an Ubuntu-server installed.

I have two computers, a PC and a laptop. Both had ubuntu breezy and were connected with SSH and everything was fine.
Now I have installed ubuntu-server on my PC and ubuntu-desktop on my laptop. I have a bunch of websites which I have developed on my PC. But now I need another local server for easier job. so I have decided to set the PC as a server and develop using my laptop and ftp to the server (PC).

So, is there a HOWTO or some tutorial for that matter? or you may direct me if the steps are easy and I'll appriciate it.

---

### Post by tribaal on 2006-06-09
I'm not sure I understand exactly what your problem is, but:

1. You don't need to do a server install, a desktop install allows you to run server software, too. Server install is only important if you intend to run a very load-demanding application.

2. You can easily install an FTP server with apt/synaptic:
```
sudo apt-get install ftpd
```

3. Alternatively to FTP, you can use ssh to access the server's file. Make sure you install an ssh server on the server machine first ("apt-get install ssh"), then open nautilus on the client, type Ctrl-L (for "Location"), and type in ```
ssh://username@hostname_or_ip_adress_of_server
```
This will give you access to the server's filesystem just like if you were logged on. You can then just drag and drop files like you would do locally. 

ssh is slower than ftp, but it's encrypted on-the-fly (very secure). 

Hope this answers your concerns.

- trib'

---

### Post by Iowan on 2006-06-09
Check [http://www.howtoforge.com]("http://www.howtoforge.com") for info on setting up Ubuntu as an ISP. There's a how-to for either Breezy or Dapper. Kinda overkill, but should point you in the right direction.

---

