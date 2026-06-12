---
title: "Can't Access FTP Externally"
date: 2011-08-04
forum: Server Platforms
---

### Post by Brad_J on 2011-08-04
I posted a similar thread a couple days ago, but I never got the response that I was looking for. I've tried quite a bit to solve this on my own but I have no idea how to do this, having never set up a working FTP server before.

I have an HTTP home webserver that I would like to be able to use to store files and practice coding on. So far I have the website visible outside of my network, and I can ssh to the box, but I would like to use FTP to upload and edit files using programs like filezilla and notepad++. I'm having a few other problems, but not being able to externally access ftp at all is my biggest.

An explanation of what is happening:
At work, I type [ftp://mydomain.org:](ftp://mydomain.org:)[port num] into a web browser and it prompts me for a username and password.
I enter everything correctly, the screen goes away, and it seems to attempt to load.
After a while (1 minute or so) it times out.

After this happened multiple times, I checked proftpd-tls.log and here are the results from one attempt today:
```

Aug 04 14:23:10 Brad-Server proftpd[30922] Brad-Server.home ([somestuff].telus.net[::ffff:xx.xxx.xxx.xxx]): FTP session opened.
Aug 04 14:23:10 Brad-Server proftpd[30922] Brad-Server.home ([somestuff].telus.net[::ffff:xx.xxx.xxx.xxx]): USER anonymous: no such user found from
[somestuff].telus.net [::ffff:xx.xxx.xxx.xxx] to ::ffff:192.168.1.80:[portnum]
Aug 04 14:23:10 Brad-Server proftpd[30922] Brad-Server.home ([somestuff].telus.net[::ffff:xx.xxx.xxx.xxx]): FTP session closed.
Aug 04 14:23:19 Brad-Server proftpd[30923] Brad-Server.home (::ffff:xx.xxx.xxx.xxx[::ffff:xx.xxx.xxx.xxx]): FTP session opened.
Aug 04 14:23:20 Brad-Server proftpd[30923] Brad-Server.home (::ffff:xx.xxx.xxx.xxx[::ffff:xx.xxx.xxx.xxx]): USER brad: Login successful.
Aug 04 14:24:02 Brad-Server proftpd[30923] Brad-Server.home (::ffff:xx.xxx.xxx.xxx[::ffff:xx.xxx.xxx.xxx]): FTP session closed.

```
Heavily edited, but I think it explains what's happening. How I understand this is that it first tries with an anonymous user since no name was specified in the url, but since I don't have that allowed, prompts me for a username and password. It seems to accept the username and password, but then closes the connection for no clear reason to me. Can anyone shed some light on this? If you need any output from my server just ask, I'll happily provide it if it helps solve my problem. Thanks for your time.

-Brad

---

### Post by Brad_J on 2011-08-05
Bump

---

### Post by Entilza on 2011-08-05
Try ftping manually through the command prompt.

---

### Post by Brad_J on 2011-08-05
> **Entilza said:**
> Try ftping manually through the command prompt.

Thank you for your response. I seem to be able to do that, although when I type in ls or dir it says "500 Illegal PORT command", and when trying to copy files over using get or recv, I get "425 Unable to build data connection: Connection timed out". Also, I still can't even connect through a web browser or filezilla. In filezilla, I get:

Status:    Server sent passive reply with unroutable address. Using server address instead.
Command:    MLSD
Error:    Connection timed out
Error:    Failed to retrieve directory listing

When it attempts to enter passive mode. Even when I have it default to active it still tries, and fails, to get into passive mode. The only way I am actually able to connect to ftp is over the same network(using local IP); I have no problems then. I think it must have something to do with my passive configuration but I'm unsure how to change that past what I've already done: changing the proftpd.conf file to specify passive ports and forwarding those ports. I hope this helps explain my situation better.

-Brad

---

### Post by HermanAB on 2011-08-06
If you have a small business server account with Telus, then it is your firewall.  If you have an el-cheapo home account, then it is Telus blocking FTP.

So, depending on the above, upgrade your account to a small business server account and configure your firewall to do FTP connection tracking, or use SSH, which is much easier to get to work and secure too.

---

### Post by Brad_J on 2011-08-07
> **HermanAB said:**
> If you have a small business server account with Telus, then it is your firewall.  If you have an el-cheapo home account, then it is Telus blocking FTP.

I have a home account, but are you talking about Telus blocking the ports or are they able to block the service entirely? I'm not on the default FTP port because Telus blocks port 21 and I'm sure the port I'm using isn't being blocked.
> **HermanAB said:**
> ... or use SSH, which is much easier to get to work and secure too.

I'd be fine with doing that if all else fails, but I'd like to be able to use things like filezilla and notepad++ ftp to upload and change things from Windows and that's not possible using ssh.

---

### Post by Brad_J on 2011-08-09
Bump for more info on this..

---

### Post by Entilza on 2011-08-09
Read up on port 20 / 21  Data ports FTP actually can use 2 ports one for connection one for data.  Maybe it's something here.  You mentioned you moved port 20 elsewhere.  There's that whole passive ftp port mode as well.  Very confusing.  Good luck.

---

### Post by Brad_J on 2011-08-10
Thanks for all the help everyone but, unless this problem solves itself, I think I'm probably stuck with the sshftp option. I will undoubtedly have questions as I have less experience with sshftp than I do with ftp, so if anyone has any good beginner's resources they could point me towards it would be appreciated.

-Brad

---

