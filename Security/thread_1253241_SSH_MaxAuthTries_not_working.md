---
title: "SSH MaxAuthTries not working?"
date: 2009-08-29
forum: Security
---

### Post by televisi on 2009-08-29
Hi All,
It seems my MaxAuthTries doesn't work as I expected?

My understanding is, this attribute limits amount of password keyed (or in my case security key for my public key) when connecting to my SSH server.

Below is my sshd_config:
```
Port 1000
AddressFamily any
AuthorizedKeysFile %h/.ssh/authorized_keys
AllowTcpForwarding no
Banner /etc/ssh/banner
ChallengeResponseAuthentication no
ciphers aes256-cbc
ClientAliveCountMax 2
ClientAliveInterval 2
Compression delayed
GSSAPIAuthentication no
HostbasedAuthentication no
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
IgnoreRhosts yes
IgnoreUserKnownHosts yes
KeyRegenerationInterval 3600
**LoginGraceTime 15s**
LogLevel VERBOSE
**MaxAuthTries 6**
PasswordAuthentication no
PermitEmptyPasswords no
PermitRootLogin no
PrintMotd yes
Protocol 2
PubKeyAuthentication yes
RhostsRSAAuthentication no
RSAAuthentication yes
ServerKeyBits 1024
StrictModes yes
SyslogFacility AUTH
UsePrivilegeSeparation yes
TCPKeepAlive yes
X11Forwarding no
MaxStartups 3:50:10

```The only one that stopping people login to my SSH server is that LoginGraceTime which is 15 seconds, after that period, the person is disconnected; but seems I able to key-in more than 3x of wrong passwords within that 15 seconds window...

Any help would be great, thanks!!

---

### Post by bodhi.zazen on 2009-08-31
> PasswordAuthentication noThis option does not work for keys.

Enable password login and re-try =)

Of course now that you see how it works, I advise you stay with keys =)

---

### Post by eldragon on 2009-08-31
install and configure fail2ban to monitor your auth log file.

it will make iptables drop ssh connections from ips trying to bruteforce your box.

---

### Post by televisi on 2009-08-31
Ah interesting, so in this case if I use normal password (without public-private key) I can limit the amount of password keyed during login.
But when I use pub-priv key, I can't...

The only thing that limit both of them is the LoginGraceTime timeout...

> **bodhi.zazen said:**
> 
Enable password login and re-try =)

Of course now that you see how it works, I advise you stay with keys =)

Thanks for this, I will check fail2ban later...
> **eldragon said:**
> install and configure fail2ban to monitor your auth log file.

it will make iptables drop ssh connections from ips trying to bruteforce your box.

---

