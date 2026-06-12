---
title: "pam_unix(sshd:auth): conversation failed"
date: 2009-02-21
forum: Security
---

### Post by kraigge on 2009-02-21
When a user enters a wrong password, it takes over 2 minutes to get the login screen back. I am using Ubuntu 8.04 with thin clients using ltsp over the lan.
Here is the output from the auth.log

Feb 21 13:24:31 edvs sshd[28103]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.102.103  user=ecorpsys
Feb 21 13:24:33 edvs sshd[28096]: error: PAM: Authentication failure for ecorpsys from 192.168.102.103
Feb 21 13:25:01 edvs CRON[28120]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 21 13:25:01 edvs CRON[28120]: pam_unix(cron:session): session closed for user root
Feb 21 13:26:26 edvs sshd[28108]: pam_unix(sshd:auth): conversation failed
Feb 21 13:26:26 edvs sshd[28108]: pam_unix(sshd:auth): auth could not identify password for [ecorpsys]
Feb 21 13:26:26 edvs sshd[28108]: error: ssh_msg_send: write
Feb 21 13:26:36 edvs sshd[28181]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.102.103  user=ecorpsys
Feb 21 13:26:38 edvs sshd[28171]: error: PAM: Authentication failure for ecorpsys from 192.168.102.103
Feb 21 13:26:38 edvs sshd[28183]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.102.103  user=ecorpsys
Feb 21 13:26:40 edvs sshd[28171]: error: PAM: Authentication failure for ecorpsys from 192.168.102.103
Feb 21 13:26:40 edvs sshd[28184]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.102.103  user=ecorpsys
Feb 21 13:26:42 edvs sshd[28171]: error: PAM: Authentication failure for ecorpsys from 192.168.102.103
Feb 21 13:26:42 edvs sshd[28171]: Failed keyboard-interactive/pam for ecorpsys from 192.168.102.103 port 54295 ssh2
Feb 21 13:26:42 edvs sshd[28171]: Failed password for ecorpsys from 192.168.102.103 port 54295 ssh2
Feb 21 13:26:42 edvs last message repeated 2 times

Why is there a 2 minute interval between the initial authentication failure and the "conversation failed" message? This is very irritating as this is an elementary school and students do type in the wrong password.
Thanks
Kraig

---

### Post by bradcan on 2009-02-24
This is usually a DNS issue. Your SSH server is trying to reverse DNS (find a name from an IP address) and it can't. Because there is no internal DNS, the SSH server is probably going to your ISPs DNS which knows nothing of your internal m/c names!

There are several solutions, the one that suits you best depends on how your clients get their IP addresses and how the SSH servers' name resolution file, /etc/resolv.conf, is configured.

Unfortunately I can't give you a definitive answer without knowing a lot more about your network. You should probably ask your LEA IT support team for help. If all else fails try reading [The Linux Network Howto]("http://tldp.org/HOWTO/NET3-4-HOWTO.html") Sorry this document probably says far more than you need to know and far less than what you wanted to know! But it's where we all started to learn networking fundementals. Or Google ssh slow will get you some more clues. ;)

---

### Post by kraigge on 2009-03-16
Thank you for your reply. I was distracted by other problems which is why it took awhile to get back to this one. My resolv.conf file only has the dns of our provider. I have set up the server as a dns server and placed the server address in the resolv.conf file. I will be onsite tomorrow to see if this fixes the problem and will let you know. 
I figured that since we were dealing with ip addresses that we didn't need dns. What was it in the information I provided that tip'd you that it might be a dns problem? I'm just trying to learn these fun things. 
Thanks
Kraig

---

### Post by kraigge on 2009-03-27
I really appreciate you help. Here is what happened.

Ok, I finally got around to setting up my server as a dns server and set up my resolv.conf accordingly on the server and my thin clients. But I am still getting a two minute delay before I get the login screen back. 
Let me tell you a little more about my network:
eth0 192.168.101.1 connects non-lab slim clients
eth1 192.168.102.1 connects all lab slim clients
eth2 192.168.1.1 connects my windows and wireless machines
eth3 23.249.202.182 connects to time warner
eth4 192.168.5.1 connects to the win2003 server. 

My ssh server has 5 internet nics. 
I am quite familiar with networking and ip, but I am very new to ltsp. The thin clients get their boot and image from the server and of course their ip address etc., then use ssh to connect to the server. What I am not sure of is how they get their host name. When I use ctr alt f1 and sign in as root and type hostname, I get edvs which is the hostname of the server. 

Here is the resolv.conf for the ssh server:
nameserver 127.0.0.1
naneserver 68.105.28.11
nameserver 192.168.1.1
nameserver 192.168.101.1
nameserver 192.168.102.1

dhcpd.conf
option domain-name-servers 192.168.101.1


Does this help you any?
Thanks
Kraig

---

### Post by albinootje on 2009-03-27
> **kraigge said:**
>  dhcpd.conf
option domain-name-servers 192.168.101.1


Did you set up a caching nameserver ?
[https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html)
That one should included the hostnames with the corresponding ip addresses that they will get.

I assume that your dhcp-server can provide the hostname corresponding on the MAC-addresses of the clients.
Here's an example :
([http://www.linuxhelp.net/guides/dhcp/](http://www.linuxhelp.net/guides/dhcp/))
```

# Assign a static IP to atlantis.linuxhelp.ca
host atlantis {
  hardware ethernet 00:45:40:10:FE:12;
  fixed-address 10.1.1.20;
}

```
The /etc/resolv.conf on the dns-server is not important, but the resulting /etc/resolv.conf on the clients is.
The clients should have your local "caching nameserver" as first nameserver in /etc/resolv.conf and your local DNS-server should have all the hostnames included in the DNS configuration, and have that working properly.

Test it by doing :
```

host hostname_of_some_client ip_address_of_your_local_DNS_server

```

---

