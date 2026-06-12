---
title: "From firestarter to ufw"
date: 2008-12-13
forum: Security
---

### Post by ooobooontooo on 2008-12-13
Hi,

I just recently transferred from firestarter to ufw. I was wondering if I took the right steps...

1. I first purged firestarter
```
sudo apt-get purge firestarter
```
2. I reset the rules
```
sudo iptables -F
sudo iptables -X
```
3. I set ufw's default to deny
```
sudo ufw default deny
```
4. I enables ufw
```
sudo ufw enable
```
5. I also enables logging
```
sudo ufw logging on
```
6. I check the status of ufw
```
sudo ufw status
```
It said firewall loaded

Is this all I need to do to ensure a safe firewall for both my wired ethernet and wireless? Also, where are the logs located? I'm kind of not sure because I looked at the iptables rules and there were a lot of allow's and deny's...

EDIT: I just tried GRC's Shields Up and apparently I failed because I replied back to a ping request...I'm assuming I should fix this...Anyone know how?

EDIT 2: I just learned you can look for the ufw logs in the syslog:
```
grep UFW /var/log/syslog
```

---

### Post by bodhi.zazen on 2008-12-14
Shields up scans your router.

For more info on UFW :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

