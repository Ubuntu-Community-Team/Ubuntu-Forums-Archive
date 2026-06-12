---
title: "Connecting to services from outside network FTP and SSH"
date: 2009-07-30
forum: Server Platforms
---

### Post by ade234uk on 2009-07-30
OK I have set up port forwarding for INBOUND services on my router for FTP 21 AND SSH 22 to forward to 192.168.0.2 which is the machine that has has vsftpd and ssh installed.

I have also added inbound services on Firestarter in UBUNTU for FTP and SSH for anyone to connect.

I can connect to these services inside the network using 192.168.0.2 using filezilla for FTP and PUTTY, However if I enter my WAN ip address which I get from here [http://www.whatsmyip.org/](http://www.whatsmyip.org/) I cannot connect.

Is this because I am trying these services from within my network, or is there anything else I need to set within Ubuntu.

I have added screenshots of my router setup and firestarter.

[IMG]http://ubuntuforums.org/picture.php?albumid=1259&pictureid=4480[/IMG]


[IMG]http://ubuntuforums.org/picture.php?albumid=1259&pictureid=4479[/IMG]

---

### Post by ade234uk on 2009-07-30
Update:
I have now tried to connect to my ipaddress from outside the network and I cannot connect. Wondering if you could tell me what else I need to do.

---

### Post by i.r.id10t on 2009-07-30
Is your ISP blocking the ports?

---

### Post by ade234uk on 2009-07-30
I had a small lamp server on test about 6 months ago. 

I also used [http://www.grc.com/port_80.htm](http://www.grc.com/port_80.htm) and the ports are showing as stealth.

---

### Post by ade234uk on 2009-07-30
How can I check if my ISP is blocking the ports?

---

### Post by R.Bucky on 2009-07-30
try some quick troubleshooting. turn off Firestarter and then try connecting. have you made changes to your /etc/ssh/sshd_config file at all? do you have a static ip? or, are you using dyndns or something similar?

---

