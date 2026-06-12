---
title: "ltsp client login error for local user"
date: 2013-11-12
forum: Server Platforms
---

### Post by bksyssathish on 2013-11-12
I build LTSP server and client. I have created a user(dennis) in LTSP server. I have created a user(admin) in LTSP client ( by using chroot /opt/ltsp/i386 ). Then, I updated the image by issuing the below commands.

```
ltsp-update-sshkeys

ltsp-update-kernels

ltsp-update-image -a i386
```

 Then, I rebooted the LTSP client.I got a login screen. When I try to login by using local user ( admin ), I am getting **No response from server, restarting**. Then, It's restarting the GUI and comes to the login screen again.  But, If I try to login by using Server username, I logged in successfully. But,  When I try to login from **Alt+Ctrl+F1** terminal in LTSP client, it is logged in successfully with local user. 

Here is my LTSP server 'syslog' : 
```

Nov 12 05:44:09 dennis dhcpd: DHCPDISCOVER from 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:09 dennis dhcpd: DHCPOFFER on 192.168.12.34 to 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:13 dennis dhcpd: DHCPREQUEST for 192.168.12.34 (192.168.12.10) from 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:13 dennis dhcpd: DHCPACK on 192.168.12.34 to 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:13 dennis in.tftpd[19684]: tftp: client does not accept options
Nov 12 05:44:28 dennis dhcpd: DHCPDISCOVER from 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:28 dennis dhcpd: DHCPOFFER on 192.168.12.34 to 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:28 dennis dhcpd: DHCPREQUEST for 192.168.12.34 (192.168.12.10) from 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:28 dennis dhcpd: DHCPACK on 192.168.12.34 to 00:1d:72:0b:b6:4c via eth0
Nov 12 05:44:28 dennis nbd_server[19676]: connect from 192.168.12.34, assigned file is /opt/ltsp/images/i386.img
Nov 12 05:44:28 dennis nbd_server[19676]: Can't open authorization file (null) (Bad address).
Nov 12 05:44:28 dennis nbd_server[19676]: Authorized client
Nov 12 05:44:28 dennis nbd_server[19699]: Starting to serve
Nov 12 05:44:28 dennis nbd_server[19699]: Size of exported file/device is 555429888
Nov 12 05:44:29 dennis nbd_server[19676]: negotiation failed
Nov 12 05:44:29 dennis nbd_server[19676]: Exiting.
Nov 12 05:44:35 dennis nbd_server[19676]: connect from 192.168.12.34, assigned file is /opt/ltsp/images/i386.img
Nov 12 05:44:35 dennis nbd_server[19676]: Can't open authorization file (null) (Bad address).
Nov 12 05:44:35 dennis nbd_server[19676]: Authorized client
Nov 12 05:44:35 dennis nbd_server[19701]: Starting to serve
Nov 12 05:44:35 dennis nbd_server[19701]: Size of exported file/device is 555429888
Nov 12 05:44:35 dennis nbd_server[19701]: Disconnect request received.
Nov 12 05:44:35 dennis nbd_server[19676]: Child exited with 0
```


auth.log
```
Nov 12 05:48:57 dennis sshd[19723]: Invalid user admin from 192.168.12.34
Nov 12 05:48:57 dennis sshd[19723]: input_userauth_request: invalid user admin [preauth]
Nov 12 05:48:57 dennis sshd[19723]: pam_unix(sshd:auth): check pass; user unknown
Nov 12 05:48:57 dennis sshd[19723]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.12.34
Nov 12 05:48:59 dennis sshd[19723]: Failed password for invalid user admin from 192.168.12.34 port 53391 ssh2
Nov 12 05:48:59 dennis sshd[19723]: Connection closed by 192.168.12.34 [preauth]


Nov 12 05:50:00 dennis sshd[19726]: Accepted password for dennis from 192.168.12.34 port 53393 ssh2
Nov 12 05:50:00 dennis sshd[19726]: pam_unix(sshd:session): session opened for user dennis by (uid=0)
Nov 12 05:50:10 dennis sshd[19872]: subsystem request for sftp by user dennis
```


I think, it is opening a ssh connection with LTSP server.

Why it is not checking the username in LTSP Client?
Whether am I missed any configuration?

---

