---
title: "Ubuntu FTP Server"
date: 2015-07-12
forum: Server Platforms
---

### Post by dmytro2 on 2015-07-12
Hi everyone) I've faced a problem which I can't figure out how to fix. I have a ubuntu server(amd64) 15.04 running as a guest in VirtualBox on my home machine. Network is set up to use Network bridge model.
What I want to do is to set up an FTP server which I can access from outside of my intranet.
Right now I have successfully (as far as I can say) installed vsftpd daemon. I can even access it from intranet (via address 192.168.0.104) but accessing it via global ip (which I will refer as global-ip, and which is router ip) causes request timeout expiration. 
I have forwarded port 2001 (which I use as port for ftp).
To access ftp server I use following URLs:
Within intranet: [ftp://192.168.0.104:2001](ftp://192.168.0.104:2001) - it works within intranet
Outside intranet: [ftp://global-ip:2001]("ftp://global_ip:2001") - causes request timeout expiration
I have googled a lot on this issue but I didn't manage to solve this problem. Maybe someone can help me out. I'll be thankful for any help or suggestion.
P.S.
I have apache web server running on VM that I can access using global_ip (at least I can see index page in my browser) even from outside computer.

P.P.S.
Here is content of my vsftpd.conf file (I have removed all comments):

listen=YES
listen_port=2001
anonymous_enable=NO
local_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

---

### Post by TheFu on 2015-07-12
For home use, FTP doesn't make sense. Please use **sftp** which is part of the **openssh-server** package. Then only 1 port need be opened - the same one for ssh.  You also get an encrypted connection so the passwords aren't send in clear-text.  Plain FTP should have died out in the early 1990s, IMHO.  **FTPS is not equivalent.**

Every networked OS has an ssh and sftp client.  For Unix/Linux-based clients, you can trivially use ssh-keys, which are even MORE secure. No passwords.  Also, run something like fail2ban or denyhosts to prevent brute force attacks.  Nobody should get to hack at your server.

Anyway - hope this helps.

---

### Post by dmytro2 on 2015-07-13
Thanks for you reply) but I still don't get why ftp fails while web-server is reachable.

---

### Post by Bucky Ball on 2015-07-13
*Thread moved to **Server Platforms**.*

... and your duplicate thread closed.

---

### Post by Lars Noodén on 2015-07-13
> **dmytro2 said:**
> Thanks for you reply) but I still don't get why ftp fails while web-server is reachable.

FTP has failed (in general) because both the authentication and data transfer occur unencrypted, meaning that anyone on the same network as the source and destination, as well as any network in between can read the traffic.  Again, that includes any user name or password.  It is also harder to set up because of how the client connects to the server.  For details read on passive vs active FTP, but ...

If you're wanting to provide anonymous downloading, the better options are http, https or even bittorrent. 

If you want people to have to log in using a username or password, then the safe but easy way to do that is with SFTP.  As TheFu mentioned, it is part of the package openssh-server. That's easy but many can help when (if) there are questions.  Using FTP in this context would make the machine a hazard.

---

### Post by TheFu on 2015-07-13
> **dmytro2 said:**
> Thanks for you reply) but I still don't get why ftp fails while web-server is reachable.

Plain FTP uses 2 ports so both need to be opened unless you force the server to use only 1.  Also, what you are calling the "global-IP" is also called the "WAN IP" or the "Internet Address". Your term was very clear.  I've heard global-IP used for mobile applications with some vendors - think it is a specific IP stack implementation. No matter.

sftp is generally better, easier, more secure and if you setup ssh, then many librsync backup tools work, rsync works, sftp, scp, ssh, NX all work over that same port.  I kinda wish training classes would stop teaching plain FTP at all. There just aren't many good reasons to have it.  Even for PXE boot systems, http can be used instead.

---

### Post by dmytro2 on 2015-07-15
Thanks again) The biggest problem with sftp for me is that I can't set ssh up either. However things seem to go better, because I at least can access it via WAN IP from my home network. But I will probably create a separate thread for this, and I would be very happy to have some advises from you.

---

### Post by mastablasta on 2015-07-15
SSH is easier to setup. good documentation is online. you can look either at Ubutnu or Debian docs about it. Securing it is a bit more difficult but shouldn't be too hard as well.

basically you install the ssh server package and then modify the config file to your needs. default is quite good aside form password. and perhaps you wish to change the port. for example it looks like my new modem/router doesn't allow 22 to be open so I will probably need to change the port or open another one.

---

### Post by dmytro2 on 2015-07-19
Thanks)

---

