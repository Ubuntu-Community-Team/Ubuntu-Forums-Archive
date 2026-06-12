---
title: "vsftp gives error 550 access denied on file upload"
date: 2008-11-14
forum: Server Platforms
---

### Post by Yorii on 2008-11-14
I think I put this in the correct category...

Anyhow, I installed a new Ubuntu Server 8.10 yesterday, installed vsftp and configured it up, at this time the server was on the same local network as the computer I was using for testing.
Everything worked fine, SSH, web site and ftp.

Today the server moved in at my friends house (because he's got a faster net :))

Now I get Error 550 Access Denied everytime I try to upload anything via ftp, I did exactly the same as I did at home, only difference is I have a firewall in between now.

My Firewall is a Microsoft ISA Server, so I started the the logger and tried to upload something.

What was strange is that the ftp server sent a request on a random port in the 12000-12999 range to my IP, which of course got blocked at the firewall. So I just made a new server rule opening the 12000-12999 range into my computer running the ftp client. Still nothing.

I started the logger in the ISA again and got very surprised that it was now trying a port in the 13000-range... a few more tries and it still tried the 13000-range...

So I added 13000-13999 to my previous rule and tried again and be amazed, it was now trying to use port 14848!!

I really have no idea what this is... is there some setting I should change in the vsftp.conf file or the ftp client? (Bulletproof FTP Client)

I have used other ftp servers with success from here, and a friend of mine is able to successfully use this ftp server (he has a firewall/router, no idea how it's configured though).

Any help would be greatly appreciated.

---

### Post by Yorii on 2008-11-14
Actually.. I think I'll just use sftp instead...

---

