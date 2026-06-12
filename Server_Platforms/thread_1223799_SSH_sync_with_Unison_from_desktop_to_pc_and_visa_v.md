---
title: "SSH sync with Unison from desktop to pc and visa versa"
date: 2009-07-26
forum: Server Platforms
---

### Post by rubenverweij on 2009-07-26
Hi all,
I want to synchronize my Thunderbird and Firefox profiles over ssh between my desktop pc and laptop using ssh. I tried to configure the desktop as ssh server, but so far I have no succes. I want to use an RSA key to login, but I keep getting the message "Permission denied (publickey)." when I try to test the server by using this command: "ssh -p 666 user@localhost". The private and public key are in the default .ssh directory. I have chmodded the directory to 700 and the authorized_keys file to 600. Now I'm stuck as I keep getting this message. If anyone has an idea I would appreciate it.
Thanks in advance!
Ruben

PS: Here is the sshd_config:
```

Port 66
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication no
KerberosAuthentication no
X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM no
AllowUsers user
```

---

### Post by fjgaude on 2009-07-26
Do you have SSH installed at bother sites?

---

### Post by rubenverweij on 2009-07-27
Thanks for your reply. Well, I was just testing from the local "server" machine, hence the localhost. That didn't even work, so I didn't bother to test remote login from my laptop.

---

### Post by jhannah on 2009-07-27
Not sure if it was just a typo, but are you connecting to port 66 or port 666, and does that match your sshd_config's Port directive? Considering you are actually getting a SSH protocol error back, I don't expect that is the case however.

Also, is your private key chmodded to 600? SSH is pretty picky about permissions but you can usually get a log message out of /var/log/auth.log (or, sometimes, /var/log/messages) if you are hitting a problem with permissions.

If that doesn't show anything meaningful, you might want to explicitly specify the identity file to ssh using the -i argument.

Let me know if you find anything interesting in the log files.

---

### Post by rubenverweij on 2009-07-27
Thanks! The logs do show something meaningful:
```
sshd[5718]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
```
I'm not sure how to fix this however... any ideas?

---

