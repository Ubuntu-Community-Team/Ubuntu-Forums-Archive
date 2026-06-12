---
title: "Whitelisting IP with UFW"
date: 2012-04-15
forum: Security
---

### Post by kkruecke on 2012-04-15
I need to whitelist Cloudflare's IP address. According to the instructions at [http://support.cloudflare.com/kb/troubleshooting/how-do-i-whitelist-cloudflares-ip-addresses-in-iptables]("http://support.cloudflare.com/kb/troubleshooting/how-do-i-whitelist-cloudflares-ip-addresses-in-iptables")

> You should insert the rules for tcp on top of the INPUT chain (for an already running firewall), and should have it accept before it gets to any other rules:
```

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 204.93.240.0/24

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 204.93.177.0/24

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 199.27.128.0/21

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 173.245.48.0/20

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 103.22.200.0/22

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 141.101.64.0/18

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 190.93.240.0/20

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 2606:4700::/32

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 2803:f800::/32

/sbin/iptables -I INPUT -j ACCEPT -p tcp --dport 80 -s 2400:cb00::/32

```
> Note: This applies to iptables only and does not consider any other firewalls you are using.

Do I need to alter /etc/ufw/before.rules? I looked at it, but I can't say I understand where or how to add these rules to it.

---

### Post by kkruecke on 2012-04-15
I did this
```

sudo ufw default deny
# Whitelist Cloudflare's IPs
sudo ufw allow from 204.93.240.0/24
sudo ufw allow from 204.93.177.0/24
sudo ufw allow from 199.27.128.0/21
sudo ufw allow from 173.245.48.0/20
sudo ufw allow from 103.22.200.0/22
sudo ufw allow from 141.101.64.0/18
sudo ufw allow from 108.162.192.0/18
sudo ufw allow from 190.93.240.0/20
sudo ufw allow from 2400:CB00:/32
sudo ufw allow from 2606:4700:/32
sudo ufw allow from 2803:f800:/32
sudo ufw allow http
sudo ufw allow https
sudo ufw allow ssh
sudo ufw allow 3306

```

But it didn't like these commands
```

sudo ufw allow from 2400:CB00:/32
sudo ufw allow from 2606:4700:/32
sudo ufw allow from 2803:f800:/32

```
What exactly is this range?

---

### Post by darkod on 2012-04-15
That is a range in IPv6 format, the new format going into service.

I am not sure if ufw accepts ipv6 by default. Look for any settings in /etc/default/ufw and /etc/ufw/sysctl.conf.

---

### Post by kkruecke on 2012-04-15
Thanks for the reply. Now, that I supposedly have whitelisted cloudflare, a ssh connection takes forever to initiate: the password prompt used to be immediate, now, with ufw rules above, it takes like 45 seconds before the ssh password prompt appears.

---

### Post by kevdog on 2012-04-16
Check the logs to see what packets your firewall is dropping.  This may give you a clue why the delay.

---

