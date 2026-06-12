---
title: "Why is Ubuntu requesting an a record to hotmail.com on startup?"
date: 2006-05-23
forum: Server Platforms
---

### Post by interprb on 2006-05-23
Hi All,
:confused: Is it a normal for ubuntu to request an "a" record from hotmail.com on boot process? We see dns records in real time. I know that we connect to ubuntu for updates... and other.  Thanks.

---

### Post by az on 2006-05-23
[QUOTE=interprb]Hi All,
:confused: Is it a normal for ubuntu to request an "a" record from hotmail.com on boot process? We see dns records in real time. I know that we connect to ubuntu for updates... and other.  Thanks.[/QUOTE]

Not unless you have some application like hotwayd runnning (hotway, gotmail, hotsmtp)

---

### Post by interprb on 2006-05-23
Thanks for the help.:) I am not aware of any of these programs as we don't use hotmail in any way. I also checked services which shows no unusual activity. It happens when the system is booting and intermittently and when shutting down. 
Also, we don't allow recursion from the outside. This ubuntu box is specificly asking for an a record for hotmail.com which returns 64.4.32.7 and 64.4.33.7. Thanks ..

---

### Post by interprb on 2006-05-24
Ok, I did a fresh install on diffrent machine and no hotmail request made. What I need to know is where in the os could an a request be made. I incld. dns records of fresh install and what ubuntu does at boot time as far as connecting with ubuntulinux.org ... plus hotmail request from other u-box.


[COLOR="Red"] "Fresh Install Box"
13:26:18   Request from 192.168.2.49 for AAAA-record for ntp.ubuntulinux.org.
13:26:18   Sending reply to 192.168.2.49 about AAAA-record for ntp.ubuntulinux.org.:
13:26:18   -> Answer: No AAAA-Records available for ntp.ubuntulinux.org.
13:26:18   -> Authority: SOA-record for ubuntulinux.org. = esperanza.ubuntu.com. [2006050301]
13:26:18   Request from 192.168.2.49 for AAAA-record for ntp.ubuntulinux.org.benoc.net.
13:26:18   Sending reply to 192.168.2.49 about AAAA-record for ntp.ubuntulinux.org.benoc.net.:
13:26:18   -> Header: Name does not exist.
13:26:18   -> Authority: SOA-record for benoc.net. = ns1.benoc.net. [2006041601]
13:26:18   -> Additional: A-record for ns1.benoc.net. = 65.82.253.50
13:26:18   Request from 192.168.2.49 for A-record for ntp.ubuntulinux.org.
13:26:18   Sending reply to 192.168.2.49 about A-record for ntp.ubuntulinux.org.:
13:26:18   -> Answer: A-record for ntp.ubuntulinux.org. = 82.211.81.145
[/COLOR]     END
_________________________________________________________________

[COLOR="SeaGreen"] "Bad Box"
13:30:47   Request from 192.168.2.201 for AAAA-record for ntp.ubuntulinux.org.
13:30:47   Sending reply to 192.168.2.201 about AAAA-record for ntp.ubuntulinux.org.:
13:30:47   -> Answer: No AAAA-Records available for ntp.ubuntulinux.org.
13:30:47   -> Authority: SOA-record for ubuntulinux.org. = esperanza.ubuntu.com. [2006050301]
13:30:47   Request from 192.168.2.201 for AAAA-record for ntp.ubuntulinux.org.benoc.net.
13:30:47   Sending reply to 192.168.2.201 about AAAA-record for ntp.ubuntulinux.org.benoc.net.:
13:30:47   -> Header: Name does not exist.
13:30:47   -> Authority: SOA-record for benoc.net. = ns1.benoc.net. [2006041601]
13:30:47   -> Additional: A-record for ns1.benoc.net. = 65.82.253.50
13:30:47   Request from 192.168.2.201 for A-record for ntp.ubuntulinux.org.
13:30:47   Sending request to 69.55.225.40 (ns1.blackcatnetworks.co.uk.) for A-record for ntp.ubuntulinux.org.
13:30:47   Reply from 69.55.225.40 about A-record for ntp.ubuntulinux.org.:
13:30:47   -> Answer: A-record for ntp.ubuntulinux.org. = 82.211.81.145
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns.ubuntu.com.
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns0.blackcatnetworks.co.uk.
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns1.blackcatnetworks.co.uk.
13:30:47   -> Additional: A-record for ns.ubuntu.com. = 82.211.81.173
13:30:47   -> Additional: A-record for ns0.blackcatnetworks.co.uk. = 193.201.200.34
13:30:47   -> Additional: A-record for ns1.blackcatnetworks.co.uk. = 69.55.225.40
13:30:47   Sending reply to 192.168.2.201 about A-record for ntp.ubuntulinux.org.:
13:30:47   -> Answer: A-record for ntp.ubuntulinux.org. = 82.211.81.145
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns.ubuntu.com.
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns0.blackcatnetworks.co.uk.
13:30:47   -> Authority: NS-record for ubuntulinux.org. = ns1.blackcatnetworks.co.uk.
13:31:01   _**Request from 192.168.2.201 for A-record for hotmail.com**_.
13:31:01   Sending reply to 192.168.2.201 about A-record for hotmail.com.:
13:31:01   -> Answer: A-record for hotmail.com. = 64.4.33.7
13:31:01   -> Answer: A-record for hotmail.com. = 64.4.32.7[/COLOR]

Need Help Please.

---

### Post by interprb on 2006-05-26
Something is very very wrong. I have firestarter on web server with port 80 open everything ealse closed. While locking and un-locking the firewall on web server I noticed the live dns log on dns server showed an "a" record request for hotmail.com everytime I unlocked firestarter. 

I need help please.

---

### Post by interprb on 2006-05-28
YEA !!!! :p :p  php script in cms causing part of the problem. Also a bot from msnbot on server plus external firewall rules set mths ago on paremiter firewall to kill some bots because of banwidth issue. Funny, you adjust one thing and have to do 20 to make it right.  

Thanks to all.

---

