---
title: "vsftpd -- 425 Error when connecting"
date: 2005-11-05
forum: Server Platforms
---

### Post by duminas on 2005-11-05
Trying to log in as an existing local user results in the following:
[quote=gFTP window]LIST -aL
425 Security: Bad IP connecting.[/quote][quote=vsftpd.log]Sat Nov  5 15:12:12 2005 [pid 25297] [ftpl] FTP command: Client "192.168.1.1", "LIST -aL"
Sat Nov  5 15:12:12 2005 [pid 25297] [ftpl] FTP response: Client "192.168.1.1", "425 Security: Bad IP connecting."[/quote]Before this, it acknowledges that my login is valid.

I am within my domain (behind the router), and people outside of the router (world) **CAN** log in. My configuration for vsftpd is below:```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
chroot_local_user=YES
chroot_list_enable=NO
pasv_enable=YES
pasv_min_port=4096
pasv_max_port=4099
listen_port=4097
connect_from_port_20=YES
ftp_data_port=4097
log_ftp_protocol=YES
xferlog_enable=YES
pam_service_name=vsftpd
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd.users
```If the userlist block at the end is confusing, that will check the file, and if their username for the login is not listed there, it will deny access. Any ideas? I need to be able to connect from behind.

Thanks~

---

### Post by stock1232 on 2008-02-17
I am having the exact same problem from behind my linksys router. Did you ever solve the problem? I have not tested ftp from outside my LAN.

---

### Post by BaseRunner on 2008-02-17
Hi,

I do not know the problem; if nobody knows immediate help pls. provide the output of the following command:
tcpdump -i <your interface> -s1500 -x host <your client's ip>
The output shows your username and password, so use a dummy account. Start the command above and then run the ftp client; when you see the error you can stop the tcpdump again.
Maybe we see there what is going on.

Cheers
Batta

---

### Post by faulkes on 2008-02-17
While this would just be a stab in the dark :

If you have PASSV enabled, such that external users can access the ftp 
server from outside the network, it is likely that client/ftp server expect to pass the same ip address of the server.  

When using port forwarding the situation is something like this

**Externally:**

client -> router WAN IP -> router LAN IP -> FTP server

client connects to WAN IP
WAN IP sends request through router to LAN IP
LAN IP sends request to FTP server
FTP server repsonds to PASSV by sending back what it thinks is it's IP of the WAN
[B]
Internally:[/B]

The same situation happens internally, except that the WAN / LAN IP's of
the router are not involved.

I suspect your configuration is setup to send back a PASSV ip address 
of the router WAN IP and this is causing a mismatch.

The easiest way to determine this is to look through the configuration file for
anything which relates to PASSV.  

The easiest way to test, is to tell your ftp client not to connect using PASSV (which is what almost all clients default too).

Faulkes

---

