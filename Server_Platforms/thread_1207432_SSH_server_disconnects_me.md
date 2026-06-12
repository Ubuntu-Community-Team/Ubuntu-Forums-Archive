---
title: "SSH server disconnects me"
date: 2009-07-08
forum: Server Platforms
---

### Post by tnek on 2009-07-08
Hi!

I have a problem with SSH. I connect from my Xubuntu 8.04 installation to my Ubuntu Server 8.04 installation using SSH.

It seems that I get disconnected after a while. I think it is when things are taking a long time to execute. One example is what just happened to me when I connected to my server cow to perform a command:
```
kent@cow:~$ diff -rq dir_a dir_b
Timeout, server not responding.

```

Here dir_a and dir_b are huge directories so it takes a while to compare them. At the same time they're identical (I'm just doing the diff to verify this) so no output is generated from the diff command. It seems I'm never able to finish the diff execution, as I get disconnected with the "Timeout, server not responding" option.

If I investigate further I see that I'm disconnected from the server after around 35 seconds:

```
kent@rat:~$ time sshcow "diff -qr external640/old_pig_farm/ old_pig_farm/"
Timeout, server not responding.

real    0m30.846s
user    0m0.024s
sys     0m0.004s
kent@rat:~$ time sshcow "diff -qr external640/old_pig_farm/ old_pig_farm/"
Timeout, server not responding.

real    0m32.247s
user    0m0.028s
sys     0m0.000s
kent@rat:~$ time sshcow "diff -qr external640/old_pig_farm/ old_pig_farm/"
Timeout, server not responding.

real    0m34.069s
user    0m0.028s
sys     0m0.008s
kent@rat:~$ time sshcow "diff -qr external640/old_pig_farm/ old_pig_farm/"
Timeout, server not responding.

real    0m31.699s
user    0m0.036s
sys     0m0.004s
kent@rat:~$ time sshcow "diff -qr external640/old_pig_farm/ old_pig_farm/"
Timeout, server not responding.

real    0m38.022s
user    0m0.032s
sys     0m0.008s

```

Here are the used configuration options on the server: (removes empty lines and comment lines)
```
kent@cow:~$ cat /etc/ssh/sshd_config | grep -v '^[ \t]*$\|^[ \t]*#'
Port 5261
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
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes
X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

```

Any suggestions?

---

### Post by drave99 on 2009-07-08
/etc/sshd_config has an IdleTimeout option

---

