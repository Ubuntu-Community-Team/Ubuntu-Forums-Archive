---
title: "Help for PPTP VPN with no internet access"
date: 2013-08-25
forum: Server Platforms
---

### Post by zkvvoob on 2013-08-25
Hi guys,

I've followed this guide: [http://jesin.tk/setup-pptp-vpn-server-debian-ubuntu/](http://jesin.tk/setup-pptp-vpn-server-debian-ubuntu/) and added VPN capabilities to my Ubuntu 12.04 server which was initially configured for ISPConfig 3 and has been running web and mail servers flawlessly so far.

However, after completing the guide, I did manage to connect to the VPN, but my Windows 7 reported "No internet access" under the vpn connection. I suspect having set some rules for UFW, I might have screwed things up. Could you please help me sort this out and restore the internet access to those connected via VPN? I really need this!

Here's the list of IPTABLES:

```
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-dovecot-pop3imap  tcp  --  anywhere             anywhere             multiport dports pop3,pop3s,imap2,imaps
fail2ban-pureftpd  tcp  --  anywhere             anywhere             multiport dports ftp
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
DROP       tcp  --  anywhere             127.0.0.0/8
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  base-address.mcast.net/4  anywhere
PUB_IN     all  --  anywhere             anywhere
PUB_IN     all  --  anywhere             anywhere
PUB_IN     all  --  anywhere             anywhere
PUB_IN     all  --  anywhere             anywhere
PUB_IN     all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
DROP       all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
PUB_OUT    all  --  anywhere             anywhere
PUB_OUT    all  --  anywhere             anywhere
PUB_OUT    all  --  anywhere             anywhere
PUB_OUT    all  --  anywhere             anywhere
PUB_OUT    all  --  anywhere             anywhere


Chain INT_IN (0 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
DROP       all  --  anywhere             anywhere


Chain INT_OUT (0 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere


Chain PAROLE (16 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain PUB_IN (5 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:ftp-data
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:ftp
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:ssh
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:smtp
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:domain
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:http
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:pop3
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:imap2
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:https
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:imaps
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:pop3s
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:1723
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:mysql
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:http-alt
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:tproxy
PAROLE     tcp  --  anywhere             anywhere             tcp dpt:webmin
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:1723
DROP       icmp --  anywhere             anywhere
DROP       all  --  anywhere             anywhere


Chain PUB_OUT (5 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain fail2ban-dovecot-pop3imap (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain fail2ban-pureftpd (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain ufw-after-forward (0 references)
target     prot opt source               destination


Chain ufw-after-input (0 references)
target     prot opt source               destination


Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-after-logging-input (0 references)
target     prot opt source               destination


Chain ufw-after-logging-output (0 references)
target     prot opt source               destination


Chain ufw-after-output (0 references)
target     prot opt source               destination


Chain ufw-before-forward (0 references)
target     prot opt source               destination


Chain ufw-before-input (0 references)
target     prot opt source               destination


Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-before-logging-input (0 references)
target     prot opt source               destination


Chain ufw-before-logging-output (0 references)
target     prot opt source               destination


Chain ufw-before-output (0 references)
target     prot opt source               destination


Chain ufw-reject-forward (0 references)
target     prot opt source               destination


Chain ufw-reject-input (0 references)
target     prot opt source               destination


Chain ufw-reject-output (0 references)
target     prot opt source               destination


Chain ufw-track-input (0 references)
target     prot opt source               destination


Chain ufw-track-output (0 references)
target     prot opt source               destination



```

---

### Post by JohnyBeGood on 2014-04-12
I do understand that this thread is old but it came accross first when I was searching. I wanted to post what worked for me and might help others.

I had the same issue. VPN was connected but it showed in Win7 that there was no network access.I've followed [official ubuntu guide ]("https://help.ubuntu.com/community/PPTPServer")on how to setup PPTPServer but I did not finished last step because I have iptables disabled. Last step was:


[COLOR=#333333][FONT=Ubuntu]Add forward rule in iptables[/FONT][/COLOR]
# sudo nano /etc/rc.local[COLOR=#333333][FONT=Ubuntu]adding to the bottom just before the exit 0[/FONT][/COLOR]
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --syn -s 192.168.0.0/24 -j TCPMSS --set-mss 1356

After I added that and rebooted server next time I got connected I had internet!

[ATTACH=CONFIG]251979[/ATTACH][ATTACH=CONFIG]251980[/ATTACH]

---

