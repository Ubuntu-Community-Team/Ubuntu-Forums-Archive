---
title: "fail2ban freezes sending e-mails."
date: 2015-05-13
forum: Server Platforms
---

### Post by craig-5 on 2015-05-13
Like every server admin should do, I installed fail2ban on my Ubuntu server to protect against brute forces.
However, it freezes on sending me e-mails.

If I restart the fail2ban service, all the queued up e-mails begin flooding into my inbox, then after a while it's back to square one.

I've looked at the log file and I am unsure what any of this means:

```
2015-05-13 23:36:34,034 fail2ban.action         [11284]: ERROR   iptables -D INPUT -p tcp -m multiport --dports ssh -j f2b-sshd
iptables -F f2b-sshd
iptables -X f2b-sshd -- stdout: b''
2015-05-13 23:36:34,035 fail2ban.action         [11284]: ERROR   iptables -D INPUT -p tcp -m multiport --dports ssh -j f2b-sshd
iptables -F f2b-sshd
iptables -X f2b-sshd -- stderr: b'iptables: Too many links.\n'
2015-05-13 23:36:34,035 fail2ban.action         [11284]: ERROR   iptables -D INPUT -p tcp -m multiport --dports ssh -j f2b-sshd
iptables -F f2b-sshd
iptables -X f2b-sshd -- returned 1
2015-05-13 23:36:34,035 fail2ban.actions        [11284]: ERROR   Failed to stop jail 'sshd' action 'iptables-multiport': Error stopping action
2015-05-13 23:36:34,036 fail2ban.jail           [11284]: INFO    Jail 'sshd' stopped
2015-05-13 23:36:34,052 fail2ban.server         [11284]: INFO    Exiting Fail2ban
2015-05-13 23:36:34,571 fail2ban.server         [10833]: INFO    Changed logging target to /var/log/fail2ban.log for Fail2ban v0.9.1
2015-05-13 23:36:34,575 fail2ban.database       [10833]: INFO    Connected to fail2ban persistent database '/var/lib/fail2ban/fail2ban.sqlite3'
2015-05-13 23:36:34,584 fail2ban.jail           [10833]: INFO    Creating new jail 'sshd'
2015-05-13 23:36:34,644 fail2ban.jail           [10833]: INFO    Jail 'sshd' uses pyinotify
2015-05-13 23:36:34,670 fail2ban.filter         [10833]: INFO    Set jail log file encoding to UTF-8
2015-05-13 23:36:34,676 fail2ban.jail           [10833]: INFO    Initiated 'pyinotify' backend
2015-05-13 23:36:34,691 fail2ban.filter         [10833]: INFO    Set maxRetry = 6
2015-05-13 23:36:34,693 fail2ban.filter         [10833]: INFO    Set findtime = 600
2015-05-13 23:36:34,694 fail2ban.filter         [10833]: INFO    Set jail log file encoding to UTF-8
2015-05-13 23:36:34,709 fail2ban.filter         [10833]: INFO    Added logfile = /var/log/auth.log
2015-05-13 23:36:34,718 fail2ban.actions        [10833]: INFO    Set banTime = 2592000
2015-05-13 23:36:34,720 fail2ban.filter         [10833]: INFO    Set maxlines = 10
2015-05-13 23:36:34,846 fail2ban.server         [10833]: INFO    Jail sshd is not a JournalFilter instance
2015-05-13 23:36:34,882 fail2ban.jail           [10833]: INFO    Jail 'sshd' started
2015-05-13 23:36:35,724 fail2ban.actions        [10833]: NOTICE  [sshd] Ban 107.190.208.26
2015-05-13 23:36:36,344 fail2ban.actions        [10833]: NOTICE  [sshd] Ban 115.239.248.69
2015-05-13 23:36:36,765 fail2ban.actions        [10833]: NOTICE  [sshd] Ban 162.250.188.49
2015-05-13 23:36:37,491 fail2ban.actions        [10833]: NOTICE  [sshd] Ban 180.150.230.214
2015-05-13 23:36:38,083 fail2ban.server         [10833]: INFO    Stopping all jails
2015-05-13 23:36:38,118 fail2ban.actions        [10833]: NOTICE  [sshd] Unban 107.190.208.26
2015-05-13 23:36:38,330 fail2ban.actions        [10833]: NOTICE  [sshd] Unban 115.239.248.69
2015-05-13 23:36:38,541 fail2ban.actions        [10833]: NOTICE  [sshd] Unban 162.250.188.49
2015-05-13 23:36:38,753 fail2ban.actions        [10833]: NOTICE  [sshd] Unban 180.150.230.214
```

---

### Post by Habitual on 2015-05-14
post the output of 
```
sudo iptables -nL
``` please.
[COLOR=#ff0000]NOTE: May need sanitizing[/COLOR] of sensitive IP(s) (yours, not theirs)

---

### Post by craig-5 on 2015-05-14
This is the exact output of that command, Habitual.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
DROP       all  --  0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Chain f2b-sshd (5 references)
target     prot opt source               destination
REJECT     all  --  91.74.99.226         0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  65.182.50.6          0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  61.174.49.106        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  61.174.49.105        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  61.160.215.103       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  61.160.215.102       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  60.8.151.51          0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  59.63.192.198        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  59.47.0.152          0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.211.166       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.211.155       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.72        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.71        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.70        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.69        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.68        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.67        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.205.66        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.72        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.52        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.46        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.37        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.36        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.248       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.245       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.241       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.239       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.226       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.225       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.204.213       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.199.49        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  58.218.199.195       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  45.59.141.12         0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.197        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.196        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.194        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.185        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.183        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.182        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.180        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.179        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.174        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.173        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.171        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.168        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.166        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.163        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.161        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.160        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.159        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.155        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.154        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.151        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.150        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.146        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.145        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.143        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.135        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.134        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  43.229.52.132        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.89.166.12        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.58.207       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.58.206       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.34.66        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.238       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.237       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.236       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.235       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.234       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.231       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.230       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.229       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.228       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.225       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.223       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.222       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.221       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.220       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.219       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.218       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.209       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.198       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.136       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.135       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.134       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.21.133       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.160.52       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.160.51       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.160.50       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.160.49       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.160.48       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  222.186.134.79       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.235.189.249      0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.98       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.81       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.66       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.4        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.30       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.29       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.229.166.28       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.203.3.18         0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  221.203.3.117        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.111.118       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.111.117       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.111.116       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.111.110       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.111.107       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.109.62        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.87.109.60        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.65.30.73         0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.65.30.23         0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  218.65.30.107        0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  182.100.67.115       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  182.100.67.112       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  182.100.67.102       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  180.150.230.214      0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  162.250.188.49       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  115.239.248.69       0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  107.190.208.26       0.0.0.0/0            reject-with icmp-port-unreachable
RETURN     all  --  0.0.0.0/0            0.0.0.0/0
```

---

### Post by Habitual on 2015-05-14
and tell us more about this "mail server".
Who hosts it? Where is it?

---

### Post by craig-5 on 2015-05-14
It uses the sendmail package on the same server as the fail2ban package. It just sends an e-mail to my mail server that a friend owns.

---

### Post by TheFu on 2015-05-15
> **craig-5 said:**
> It uses the sendmail package on the same server as the fail2ban package. It just sends an e-mail to my mail server that a friend owns.

sendmail is fairly complicated. Any reason you selected that over postfix?

If the server is really busy, email is turned off. This is a "feature" as I understand it that has been around a very long time in all MTAs.

---

### Post by craig-5 on 2015-05-15
It had worked flawlessly before. But I had to do a server reinstall due to a problem, and it started doing this.

---

### Post by Habitual on 2015-05-15
How many active jails do you have?

---

### Post by craig-5 on 2015-05-15
Just the one, I think. The sshd one?

---

### Post by Habitual on 2015-05-18
sshd  protection is, or used to be the only jail that worked out of the box (upon installation, and starting of the service).
You should check your local logs (like /var/log/fail2ban.log) for any indicators of what is going on with the mail.
Also, can you post the appropriate section for [sshd]  from /etc/fail2ban/jail.conf?

Sanitize your email target if you do.

---

