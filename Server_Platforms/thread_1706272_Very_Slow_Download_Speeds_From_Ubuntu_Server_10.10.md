---
title: "Very Slow Download Speeds From Ubuntu Server 10.10 32 bit"
date: 2011-03-13
forum: Server Platforms
---

### Post by Chubbs[] on 2011-03-13
Hi, I am sort of new to Ubuntu Servers so bear with me. #-o

Whenever a client tries to download a file from my server via ftp, SAMBA, Teamspeak 3 File Transfer, etc., they report very slow download speeds, around 3-6 kb/s. 

If I try a ftp file transfer locally, the upload speeds are normal, but I still experience slow download speeds.

My server is connected to a router, which connects to the internet. All other machines connected to that router can upload and download files at normal speeds.

It seems to be a server problem, I just don't know where to start.

---

### Post by Chubbs[] on 2011-03-16
Any thoughts?

---

### Post by rubylaser on 2011-03-16
I'm a little unclear here.  Are you saying that on your local LAN, you get good speeds, but your clients are connecting to the server over the internet, and seeing much slower speeds?  If that's the case, that's to be expected.  Have you run an upload speed test to see what sort of upload speeds you get? 
[http://speedtest.net/]("http://speedtest.net/")
Also, what type of internet connection do you have?

I hope I'm understanding your scenario correctly.

---

### Post by Chubbs[] on 2011-03-18
No, let me try and be a bit more clear...

If any client (from the internet or the LAN) tries to download a file from the server, the speed is painstakingly slow, like 4kbs. 

All other connections work fine.

---

### Post by NedHanlon on 2011-03-19
What ports have you opened to allow ftp uploads? Are you forwarding them on the router, or are you using 21?

---

### Post by wongo888 on 2011-03-19
Is your ISP shaping their traffic?

---

### Post by Chubbs[] on 2011-03-21
I'm forwarding them on my router and I'm assuming its using port 21, but I also have 20 open...

I believe that my ISP is not the problem...

---

### Post by cmileto on 2011-03-21
Are you using dynamic dns for your domain name? I had horrible speeds on my server until I switched to a paid as opposed to free dynamic dns for my home server. Prob not your issue if its the same inside your lan, but thought Id throw it out there.

---

### Post by wongo888 on 2011-03-22
Is there anything unusual in your logs?

Can you give a detailed example of when it is "fast"?

---

### Post by Chubbs[] on 2011-03-22
Here is some of the log file of a failed download

Fri Mar 18 10:52:51 2011 [pid 3] [daniel] FAIL DOWNLOAD: Client "216.11.46.10", "/vmimages/ubuntu-10.10-desktop-i386.iso", 64860 bytes, 1.01Kbyte/sec

---

