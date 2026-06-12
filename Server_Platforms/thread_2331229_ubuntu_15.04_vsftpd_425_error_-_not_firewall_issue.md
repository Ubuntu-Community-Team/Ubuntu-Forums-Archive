---
title: "ubuntu 15.04 vsftpd 425 error - not firewall issue"
date: 2016-07-19
forum: Server Platforms
---

### Post by mikejf12 on 2016-07-19
Hi 

I wanted to ask about a vsftpd error running on ubuntu 15.04, I have vsftpd running 

sudo vsftpd restart

and I have a config file set up /etc/vsftpd.conf. ( Ive edited this file a lot trying to solve a 425 error ) 

listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
data_connection_timeout=240
check_shell=NO

I have a windows 7 client host on the same network that logs in a user mule without any error. However when carrying out any subsequent action like ls or put the action times out with 

425 failed to establish connection. 

I had assumed that this was a firewall issue so I enabled ftp and tested access. Still no solution .. finally I disabled the firewall and still had the issue. i..e 

ufw allow ftp
ufw status verbose
ufw disable

Ive been reading vsftpd ubuntu forum entries and trying to get this to work for days. So finally I need to ask for help. Without a firewall to cause the problem what could it be ? 

cheers

Mike F

---

### Post by mikejf12 on 2016-07-19
The windows 7 actions just time out 

[COLOR=#008000]C:\temp>ftp xxx.168.40.88
Connected to xxx.168.40.88.
220 (vsFTPd 3.0.2)
User (xxx.168.40.88:(none)): mule
331 Please specify the password.
Password:
230 Login successful.
ftp> ls
200 PORT command successful. Consider using PASV.
425 Failed to establish connection.
ftp>[/COLOR]

---

### Post by mikejf12 on 2016-07-19
The /var/log/vsftpd.log contains the following when trying to put a file to the server 

[COLOR=#008000]Wed Jul 20 10:00:59 2016 [pid 5087] CONNECT: Client "xxx.168.40.161"
Wed Jul 20 10:01:06 2016 [pid 5086] [mule] OK LOGIN: Client "xxx.168.40.161"
Wed Jul 20 10:02:09 2016 [pid 5089] [mule] FAIL UPLOAD: Client "xxx.168.40.161", "/home/mule/messages", 0.00Kbyte/sec[/COLOR]

---

### Post by steeldriver on 2016-07-19
What about the Windows firewall? maybe it's blocking the outgoing connection?

See [https://wiki.filezilla-project.org/Network_Configuration#Setting_up_FileZilla_Client](https://wiki.filezilla-project.org/Network_Configuration#Setting_up_FileZilla_Client)

---

### Post by mikejf12 on 2016-07-19
As I said above I thought about firewalls, first I used ufw to allow ftp, ssh, http etc and even a passive ftp port range. Then to prove it wasnt the firewall I used ufw to disable the firewall

---

### Post by darkod on 2016-07-20
It might still be a firewall issue, look both on the client (what steeldriver suggested above, to look at the win7 not the server) and the server.

On the server post the output of:
```
sudo iptables -L -n -v
```

That should show us if the iptables policies are ACCEPT or maybe DROP.

Also you said the client is on the same local network, right? If the client is on the same local network, how come the vsftpd.log seems to show public IP for the client?

Are you accessing the ftp server through the internet? In such case, it's a different story. Your router firewall will be between the client and the server, it doesn't metter if you disabled the firewall on the server itself.

PS. Accepting the login and then dropping the connection right away is 99% firewall issue. You need to explain to us your setup, where is the server, where is the client, etc... Then we can help you sort it out.

---

