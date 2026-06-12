---
title: "My 128MB Linux Server :)"
date: 2012-02-21
forum: Server Platforms
---

### Post by d4m1r on 2012-02-21
First off, with 128MB of RAM I think it qualifies as more of a VPS  (Virtual Private Server) than a full linux server but anyway....This  thread is about the amazing number of things you can do with such  limited hardware, linux, and a low budget (more on that later).

Basically, the server is running Ubuntu 11.04 (x86), 15GB HDD, 1TB  monthly bandwidth, and 128MB dedicated ram but can go up to 256MB  (burst). After getting root SSH access and updating the OS, the system  was using 12MB of RAM at idle, which is extremely low. The only catch is  I stopped the Apache service and uninstalled the DNS service because I  don't need it. After reconfiguring Apache + PHP to my liking, I  restarted it and my VPS was still only using ~30MB/128MB. Setting up a  FTP server on it (vsftpd) only cost me 1MB. Installing a VoIP server  (Teamspeak 3) ate a little bit more at an additional 40MB but that still  brought my total to 70MB/128MB. Next I installed fail2ban which is a  server hardening/security suite, which uses about 40MB so I was at  110MB/128MB. And finally, I installed a VPN server (OpenVPN), and that  only uses ~4-5MB as well.

In general, I am very surprised how many applications I can run  simultaneously on such a budget server....Yes when people are actually  connected to teamspeak, FTP, or the VPN, those programs take a little  more RAM but I am still under my dedicated RAM quota and don't even  touch my burst RAM....Also, CentOS and Ngix seem to be more popular now  but I am used to Ubuntu and Apache so that is what I stuck with [IMG]http://files.overclock.net/images/smilies//smile.gif[/IMG] Finally the best part....This all costs me $1/month from [FastVPS.co]("http://www.fastvps.co/aff.php?aff=026")! [IMG]http://files.overclock.net/images/smilies//biggrin.gif[/IMG]

---

### Post by d4m1r on 2012-02-21
I forgot to mention that MySQL is really the only thing missing....The  trouble is that I could never get it to use under ~100MB, which is a  lot, and I have no plans to be running any databases so I just  uninstalled it.

Check out or ping the site in my signature as it is running off the VPS  and on FastVPS' network. Also, I am always looking for suggestions for  other things I could be using my server for [IMG]http://files.overclock.net/images/smilies//wink.gif[/IMG]

---

