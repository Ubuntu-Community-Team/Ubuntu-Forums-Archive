---
title: "Is my web server being hijacked?"
date: 2006-11-25
forum: Server Platforms
---

### Post by robk86 on 2006-11-25
Hi, I'm new to the forum.

I am running Ubuntu Server 6.06 with LAMP installation and am using Apache 2. I am new to servers, but I looked at my "apache.log" file and there is usually just GET requests (mostly me testing the website), but there are about 30 CONNECT requests to what appear to be mail servers at Google and Microsoft as well as unnamed IPs.  I'm wondering if someone is hijacking my server to send spam or something.  I recently used apt-get to update the OS and am wondering if this could have caused it as it was a couple days before this happened.  This is not an important website so I shut it down until I could figure this all out, but I could put it back up if it helps.

I have attached the log entries in question (some in the middle are GET requests from me testing it).

---

### Post by MJN on 2006-11-25
You'll be pleased to hear there's nothing to worry about - the CONNECT ..:25 requests were all met with a code 405 i.e. 'Method not allowed' hence nothing actually happened.

They were just trying to find an open HTTP proxy (and yours isn't).

Mathew

---

### Post by robk86 on 2006-11-25
Thanks for the reply.  I've only checked the log a few times but I don't think I've seen those before, maybe a few things I din't recognize, but not a bunch a e-mail servers like now.  So, what does it mean that they were trying to open an HTTP proxy and who's they?  Could it be because I recently implemented XML HTTP Request into my website design?  I guess I'm a little paranoid about this stuff.  Well thanks for the info, I guess I'll start up my server again.  Also, would using the FTP server in Ubuntu for me to remotely store files on or maybe share files with others(password protected) make the server less secure?

---

### Post by MJN on 2006-11-25
'They' is all the cheeky buggers out there upto no good. The only thing you did to 'attract' them was connect to the Internet with a web server...

As for what they were trying to do, they're looking for badly secured proxy servers. Proxy servers exist to act on behalf of other machines e.g.to retrieve a web page from another server on bahalf of the requesting client. Unfortunately some HTTP proxy servers are so badly secured that they will go further than just proxy port 80 requests but also allow traffic to be sent to port 25... this opens up an opportunity for spamming with it looking like it's coming from the proxy.

As for the FTP, it's arguably one of the weakest protocols around as everything is sent in the clear (i.e. unencrypted)... and this includes your usernames and passwords. This opens up the possibility of someone 'sniffing' this info off the network... Better to use encrypted methods instead, e.g. install an SSH server and use SFTP clients.

Mathew

---

### Post by robk86 on 2006-11-25
Now I understand.  I saw something about SSH when I was reading about how to use the FTP server, but it looked complicated.  I will probably look into it some more and ask questions on the forum if I need to.  Thanks again.

---

### Post by MJN on 2006-11-25
You'll be pleased to hear SSH is actually dead easy, and is secure out of the box - install it and you'll likely be good to go.

Furthermore, FTP is one of the hardest protocols to get working particularly when you've got NAT routers in the way which many/most of us have so is best avoiding for that reason alone!

Mathew

---

