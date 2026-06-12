---
title: "[SOLVED] FTP server not accessible via web browser !!"
date: 2008-09-19
forum: Server Platforms
---

### Post by tarun.winlin on 2008-09-19
Thanks to your support I successfully configured my FTP server (ProFTPD).

I am using active ftp & am able to successfully access my ftp server both locally & from remote locations.

Question I have is when I use this on any browser like IE, or Moziall, or google chrome [ftp://tarunlohumi.homeip.net](ftp://tarunlohumi.homeip.net), I am not able to get to my ftp server.

Yes, I have disabled anonymous logins & using a username & password to login into my ftp server.

Also, I tried [ftp://username:password@tarunlohumi.homeip.net](ftp://username:password@tarunlohumi.homeip.net) - but it still does not works - why?

---

### Post by HermanAB on 2008-09-19
Common browsers typically only support "Passive FTP".  Your FTP server needs to be configured for that.  

The exception is Konqueror which supports every protocol under the sun.

Cheers,

Herman

---

### Post by tarun.winlin on 2008-09-19
You were spot on. I changed the mode to passive on the server & it works like a charm now !!

Thanks a ton !!

---

### Post by RFXCasey on 2008-10-02
Yes, I have disabled anonymous logins & using a username & password to login into my ftp server.

How do you do this? I have a debian server setup for local and web access. I am by no means a security expert. Any suggestions on locking it down would be appreciated. Also I can only connect to my proFTPD server using a client like filezilla when I'm using active mode as I can't get passive mode to work. Is there something special I have to do. I am running dansguardian, firehol, and tinyproxy and was wondering if that had something to do with it. Does proFTPD support connections from a browser by default. Do you have to set it up or add a module to it? Sorry for all the questions.:confused:

---

### Post by lykwydchykyn on 2008-10-02
If I'm not mistaken, in passive mode the server opens up a random high port to transmit data, whereas in active mode it uses port 20.  In your proftpd config, you should be able to specify a range of ports to use for passive mode data transfer.  You'll need to make sure the ports in this range are open in your firewall.

---

### Post by RFXCasey on 2008-10-03
Thanks, I'll give that a try.

---

