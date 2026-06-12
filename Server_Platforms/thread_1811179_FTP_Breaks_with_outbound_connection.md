---
title: "FTP Breaks with outbound connection"
date: 2011-07-24
forum: Server Platforms
---

### Post by adman4054 on 2011-07-24
I'm sending files to a remote server by way of FTP via a PHP script. With the firewall turned on these files are getting to the remote server with 0kb and the remote server is timing out before all the files are received. When the firewall is turned off the all files are received in tact. There are no outbound rules set in the iptables, looking for ideas on what to check next. Thanks in advance :)

---

### Post by e79 on 2011-07-24
Looks like a fireall problem to me, check the difference between [Passive & Active ftp]("http://slacksite.com/other/ftp.html") server...but again, I could be wrong but I'd def start from there.

---

### Post by adman4054 on 2011-07-24
> **e79 said:**
> Looks like a fireall problem to me, check the difference between [Passive & Active ftp]("http://slacksite.com/other/ftp.html") server...but again, I could be wrong but I'd def start from there.

I used "quote pasv" and no joy, but I'm I've read on the Internet that might not work on the sending end.

Thanks for the reply,

---

### Post by adman4054 on 2011-07-24
Can somebody tell me-- when an outgoing ftp connection is made is it port 21 from the sending server? Reason I ask is although there are no outgoing rules in my iptables, I do have this port closed for an incoming connection. Thanks

---

### Post by Gyokuro on 2011-07-24
depends on your firewall rules - do you use ufw or own rules? As normally you block in a firewall setup everything and only allow the ports which get used.

---

