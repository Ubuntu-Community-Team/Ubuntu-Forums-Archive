---
title: "Ubuntu FTP server"
date: 2015-07-13
forum: Server Platforms
---

### Post by dmytro2 on 2015-07-13
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

### Post by Bucky Ball on 2015-07-13
*Thread closed.*

See [here]("http://ubuntuforums.org/showthread.php?t=2286499"). Please don't post duplicates. You are getting help on your original thread. Post 'bump' to your existing thread if it doesn't see any action for >12 hours or so, or add further information, like you have done. Either will take the thread back to the top of the new posts list.

---

