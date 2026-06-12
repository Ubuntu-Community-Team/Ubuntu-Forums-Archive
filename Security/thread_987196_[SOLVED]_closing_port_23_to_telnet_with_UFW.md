---
title: "[SOLVED] closing port 23 to telnet with UFW"
date: 2008-11-19
forum: Security
---

### Post by allinthefamily on 2008-11-19
I have a new install of Intrepid, and scanned for port stealth using the [Shields Up!]("http://www.grc.com/x/ne.dll?rh1dkyd2") service. This scan told me that port 23 is open to telnet, and this is a serious security issue. I enabled UFW and denied any incoming to port 23/tcp.

This is what I get when I "sudo UFW status"

miles@miles-ubuntu:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
23/tcp                     DENY    Anywhere
23/udp                     DENY    Anywhere
23/tcp                     DENY    Anywhere


However, follow-up Shields Up! scans keep telling me that port 23 is still open to telnet! 

How do I close this port? Or, is this a false reading/ i.e. not a security threat?

Thanks!

---

### Post by cdenley on 2008-11-19
The port would not be open on your computer unless you installed a server which listens on that port. Your router is either running a server on port 23, or is forwarding traffic on that port to another server.

Why does everyone use that service and not understand how it works? There have been many posts like this one. Search before posting.

---

### Post by Titan8990 on 2008-11-19
IMO its best to just use nmap to scan yourself from a remote location.

---

### Post by cdenley on 2008-11-19
> **Titan8990 said:**
> IMO its best to just use nmap to scan yourself from a remote location.

Since most people don't have shell access to a remote location, I suggest simply looking at what is listening on which port.
```

sudo netstat -tlnp

```

---

### Post by Titan8990 on 2008-11-19
But that only tests your local machine and not your entire network. It doesn't matter what ports are listening on his local machine if those ports are not forwarded on his router.

---

### Post by cdenley on 2008-11-19
> **Titan8990 said:**
> But that only tests your local machine and not your entire network. It doesn't matter what ports are listening on his local machine if those ports are not forwarded on his router.

It matters if your router or another computer on the LAN is compromised, or you simply don't trust the users on your LAN. It all depends on the needs of the individual, but the OP seemed to be concerned about closing the ports on his computer.

---

### Post by prshah on 2008-11-19
> **allinthefamily said:**
> miles@miles-ubuntu:~$ sudo ufw status
Status: loaded
To                         Action  From
--                         ------  ----
23/tcp                     DENY    Anywhere
23/udp                     DENY    Anywhere
23/tcp                     DENY    Anywhere


However, follow-up Shields Up! scans keep telling me that port 23 is still open to telnet! 

You probably have WAN enabled for Telnet in your router's ACL (Access Control List).

Open the router's configuration page (typically [http://192.168.1.1](http://192.168.1.1) ) and look for something called "ACL" or "Access Control List" (it may be something else, depending on your router.)

In the list of options, disable WAN access to Telnet, but leave LAN access enabled.

---

### Post by allinthefamily on 2008-11-19
I guess I should clarify my first post. First of all, I'm pretty n00bish, but I have been researching this issue. I am indeed most concerned with making sure that port 23 on my laptop is not open; I take this laptop everywhere and connect to many different networks. 

It is possible that port 23 is open on my router at home and this is what Shields Up! found. I will have to check this out when I get home. Thanks for the tip on this everybody.

Following is the output of sudo netstat -tlnp

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      5325/smbd       
tcp        0      0 0.0.0.0:5679            0.0.0.0:*               LISTEN      5580/odccm      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5179/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      5325/smbd       
tcp        0      0 0.0.0.0:990             0.0.0.0:*               LISTEN      5580/odccm      

I'm not really sure what this means. How can I be sure I am blocking port 23? I don't think I see it here.

Thanks!

---

### Post by cdenley on 2008-11-19
You have two servers running on your laptop: samba and odccm. Is that intentional? Depending on how the servers are configured, they could make you vulnerable to other users on your LAN.

You have three options:
-configure them so they are secure
-remove them
```

sudo apt-get remove samba odccm

```
-block them
```

sudo ufw enable
sudo ufw default deny

```

No need to worry about cups. That's not listening for remote connections.

> 
I'm not really sure what this means. How can I be sure I am blocking port 23? I don't think I see it here.

It's not about blocking ports. If there's no program listening on a port, there is no need to block it. The output you posted shows no processes listening on port 23. There are processes listening on other ports, though. They aren't accessible from the internet at the moment, though, since your router isn't forwarding incoming traffic to you.

The columns to pay attention to is "Local Address" and "PID/Program name". The local address "127.0.0.1:631" means that process is listening on the local loopback device (127.0.0.1) on port 631. This means you can only connect to it locally. If it were "0.0.0.0:631", that would be a problem. That would mean that the process is listening for connections from all interfaces, and connections to the process could be established from over the internet. The program name "cupsd" indicates that the cups print server is the process listening on the port.

---

### Post by prshah on 2008-11-19
> **allinthefamily said:**
> I'm not really sure what this means. How can I be sure I am blocking port 23? I don't think I see it here.


Here's an easy way to confirm if it is in fact your router; login to the net as usual; find out the ip address assigned to the router (see it at [http://www.whatismyip.com](http://www.whatismyip.com) ). Now, disconect your laptop (and shutdown any other machines connected to the router) and connect your laptop to the net by some other means (some _other_ wireless, dialup, etc) and now use Shields Up to scan the ip address you've got from above. If it still says Telnet is open, then you can be sure it's your router.

---

### Post by scorp123 on 2008-11-20
> **allinthefamily said:**
> sudo netstat -tlnp Try this one: ```
sudo lsof -n -i -P 
``` ... it will not only list open ports but also the name of the application that's behind the open port!

Example output:```

COMMAND     PID   USER   FD   TYPE DEVICE SIZE NODE NAME
portmap    4587 daemon    4u  IPv4  15159       UDP *:111 
portmap    4587 daemon    5u  IPv4  15164       TCP *:111 (LISTEN)
rpc.statd  4607  statd    5u  IPv4  15201       UDP *:967 
rpc.statd  4607  statd    7u  IPv4  15212       UDP *:39807 
rpc.statd  4607  statd    8u  IPv4  15215       TCP *:35215 (LISTEN)
avahi-dae  5225  avahi   14u  IPv4  16387       UDP *:5353 
avahi-dae  5225  avahi   15u  IPv4  16388       UDP *:36652 
sshd       5266   root    3u  IPv6  16460       TCP *:22 (LISTEN)
sshd       5266   root    4u  IPv4  16462       TCP *:22 (LISTEN)
cupsd      5330   root    2u  IPv4  25343       TCP 127.0.0.1:631 (LISTEN)
cupsd      5330   root    4u  IPv4  25346       UDP *:631 
rpc.mount  5491   root    6u  IPv4  16868       UDP *:57768 
rpc.mount  5491   root    7u  IPv4  16873       TCP *:41025 (LISTEN)
dhclient   6004   root    5u  IPv4  18397       UDP *:68 
vino-serv  6304    ron   16u  IPv6  20867       TCP *:5900 (LISTEN)
gnome-do   6315    ron   18u  IPv4 112604       TCP 192.168.21.51:57468->208.97.189.214:80 (CLOSE_WAIT)
gnome-do   6315    ron   20u  IPv4 108062       TCP 192.168.21.51:36569->208.97.189.214:80 (CLOSE_WAIT)
gnome-do   6315    ron   21u  IPv4 110254       TCP 192.168.21.51:56850->208.97.189.214:80 (CLOSE_WAIT)
gnome-do   6315    ron   22u  IPv4 115391       TCP 192.168.21.51:37281->208.97.189.214:80 (CLOSE_WAIT)
firefox    6540    ron   24u  IPv4 115464       TCP 192.168.21.51:44426->69.63.176.168:80 (ESTABLISHED)
firefox    6540    ron   64u  IPv4 111214       TCP 192.168.21.51:58861->209.132.177.110:443 (ESTABLISHED)
gvfsd-htt  7852    ron    9u  IPv4  24923       TCP 192.168.21.51:60073->172.16.11.100:443 (CLOSE_WAIT)
ssh       19126    ron    4u  IPv4  50719       TCP 192.168.21.51:37220->192.168.21.50:22 (ESTABLISHED)
```

---

### Post by allinthefamily on 2008-11-20
Thanks for all the help. Turns out port 23 on my router was forwarding somewhere unnecessary, I just closed it. Port 23 on my laptop is stealth, probably always was.

---

