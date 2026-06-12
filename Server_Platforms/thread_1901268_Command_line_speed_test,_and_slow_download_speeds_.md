---
title: "Command line speed test, and slow download speeds on samba share."
date: 2011-12-28
forum: Server Platforms
---

### Post by Johndo1 on 2011-12-28
I've got a file server set up on an old desktop. It's more or less just a side-project I've been working on until now. I'm using it to store all of my movies and what not since I ran out of space on my hard drive. It's entirely wireless because someone sleeps in the room with the router, and they don't want the server running in there all the time, making noise, and heating the room up.

Anyway, I'm using samba and whenever I FTP to the shares, I get relatively slow speeds. When I try to drag and drop the files through ubuntu it's even slower. I port forwarded for the FTP, and it only sped it up a little bit. I ran a speed test on my laptop, and I'm getting around 10 Mbps download, and 3 mbps upload. When I FTP to the file server, however, I'm getting around 300 kb/s. I'm wondering if anyone can help me speed these transfers up, or if anyone knows how to run a speed test over the command line so I can check the download/upload speed on the server.

P.S. Should my upload/download speeds even factor in? It's all on the same network going through the same router anyway... As far as I know, I'm not even going through the ISP, so how would their upload/download caps even affect this?

---

### Post by Paddy Landau on 2011-12-28
As you are communicating through the router, your hardware determines your maximum speed. Your ISP is totally irrelevant (and could even be down or disconnected without affecting your personal server).

I don't know where your bottleneck lies with FTP. You may want to check its settings -- perhaps you have enabled speed limits?

---

### Post by Johndo1 on 2011-12-28
> **Paddy Landau said:**
> As you are communicating through the router, your hardware determines your maximum speed. Your ISP is totally irrelevant (and could even be down or disconnected without affecting your personal server).

I don't know where your bottleneck lies with FTP. You may want to check its settings -- perhaps you have enabled speed limits?

I'm using filezilla, and it doesn't have speed limits enabled, so that's not the problem. When I run this: 

wget --output-document=/dev/null [http://speedtest.wdc01.softlayer.com/downloads/test500.zip](http://speedtest.wdc01.softlayer.com/downloads/test500.zip)

I'm getting around 300 kib/s on the server. Which is slow. I'm not entirely sure where that file is hosted, however, so I can't be sure it's not that, but it seems to me like the server is doing something that is making it slow because when I run that same command on my laptop I get around 500 kib/s, which is also slow, but still faster than what the server is getting. I need a better file closer to PA to test with, but I can't seem to find one.

---

### Post by a2j on 2011-12-28
are you connecting to the server via LAN IP? could wireless be the bottle neck? how old is "old desktop"?

---

### Post by jchung on 2011-12-28
Have you tweaked your network settings?

[http://www.psc.edu/networking/projects/tcptune/](http://www.psc.edu/networking/projects/tcptune/)

---

### Post by Johndo1 on 2012-01-03
Found the problem. I've been using vsftpd as my ftp server, and in the configuration file (/etc/vsftpd.conf) it had the default connection port as port 20. So, I commented that line, as you can see in the code below, and now I'm getting much better speeds. (Nearly 1mb/s, which isn't THAT fast, but decent considering the fact that I'm sending the info through the floor, to the router, and back up through the floor to the server via crappy wlan cards and all.) 

Here's what my config file looks like for vsftpd.

> 
 # Config file /etc/vsftpd.conf
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=021
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
#connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
idle_session_timeout=600
data_connection_timeout=120
ftpd_banner=**** your **** ************.
ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem


---

### Post by Paddy Landau on 2012-01-04
Great, I'm glad you found the problem. This may help others with a similar problem; please [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others.

---

