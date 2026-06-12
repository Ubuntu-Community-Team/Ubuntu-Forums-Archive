---
title: "Accessing VSFTPD remotely (ubuntu server)"
date: 2008-10-02
forum: Server Platforms
---

### Post by psychohamster on 2008-10-02
Running vsftpd for ftp access (obviously :) ). It is set up for non-anonymous chrooted/local-user access. I can log into it ok from the local network using ftp or using firefox on one of the windows machines. But when I try to access it from outside the network (using a remote desktop to control my home computer), All I get is to the log in box then about 3 minutes later I get a "425- unable to establish connection" error. Here is my config file.

background=YES
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Company Name
chroot_local_user=YES
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
nopriv_user=nobody
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=40100

Several things. I have port forwarding set up for 20,21,40000-40100. I have tested that and the ports are forwarding correctly. I also am using dyndns.org, and the server name I am using is resolving correctly. I can ping the ftp machine from outside the local network with no troubles.
Also, I thought my config file has passive enabled. But when ever I access it from the local network, I keep receiving the message "connection established, consider using PASV"

Anyone have any suggestions?

---

### Post by whitegourd on 2008-10-02
I'm running vsftpd on my home network as well and the settings you have look fine to me.

Have you ever hosted an FTP server with your current ISP before?  If not, you may want to verify that your ISP isn't filtering out the ftp ports.  Back when I was using Charter cable, I had to modify my ftp server to listen to another port since they blocked port 21.

Verify if your ISP is blocking anything that you're trying to access remotely

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by psychohamster on 2008-10-02
I've already talked with the isp, they aren't blocking it. I've run remote tests to ensure port connectivity, both 20,21 are open and receiving requests. But I keep getting "Unable to connect messages". I've checked the vsftpd log, and it is indeed getting the remote requests and confirming log-ins.

---

### Post by whitegourd on 2008-10-02
After comparing with what I have to what you have.  I don't have the "background=YES" option anywhere in the vsftpd.conf.  I also have "chroot_local_user=YES" remarked.

Maybe see if you can remark the two and try accessing your ftp server.  Are you using a web browser to access your ftp server or are you using an actual ftp client (i.e. filezilla)?  I think there is a setting in filezilla that you can set PASV.  I believe IE and Firefox for whatever reason reacted to my vsftp server differently.

---

### Post by psychohamster on 2008-10-02
the background=YES is to not run it as an inet daemon I believe (i've commented it for a test) The chroot_local_user.. is quite necessary as I don't wish logged in users to see the rest of the file structure. I've tried accessing with (on a windows machine), firefox,ie, and FTPCommander

---

### Post by whitegourd on 2008-10-02
Do you have "secure_chroot_dir=/var/run/vsftpd" enabled?  Another thing you can maybe try is to remark the PASV settings ...

pasv_enable=YES
pasv_min_port=40000
pasv_max_port=40100

---

### Post by psychohamster on 2008-10-02
actually the pasv weren't always on there. I tried adding them as the first step to resolving the issue thinking that maybe passive mode over active would work. No I don't have that chroot enabled, as I want them to go to their home directories (Which works fine on the local network.)

---

### Post by whitegourd on 2008-10-02
Gosh, I'm running out of things to think of.  I don't know if this would apply but are you restarting the vsftpd service for each adjustment that you do in the conf file?

---

### Post by lykwydchykyn on 2008-10-02
Nothing in /etc/hosts.allow or /etc/hosts.deny, is there?

Can you post the log output from vsftpd after a failed connection?

---

