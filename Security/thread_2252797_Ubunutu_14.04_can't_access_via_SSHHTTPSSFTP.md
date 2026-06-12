---
title: "Ubunutu 14.04 can't access via SSH\HTTPS\SFTP"
date: 2014-11-14
forum: Security
---

### Post by joe146 on 2014-11-14
I posted this at [https://askubuntu.com/questions/549655/ubunutu-14-04-cant-access-via-ssh-https](https://askubuntu.com/questions/549655/ubunutu-14-04-cant-access-via-ssh-https), but hoping maybe I can get something responses here. 

I can't seem to access my ubuntu 14.04 server via SSH, HTTPS, or SFTP recently. Not sure what changed. I'm still able to access it via http and locally. I tried reinstalling the ssh server and regenarating a new rsa key. I suspect the issue has to do with the the crypto since ssh, https, and sftp are using those mechanism. Any clues? I'm kind of stump.

I tried disabling apparmor and ufw is disabled.

---

### Post by Lars Noodén on 2014-11-14
What is the status of the SSH (SFTP) server?

```

service ssh status

```

If it's running, what is in /etc/ssh/sshd_config?

If it is not running then what happens when you launch it manually in debug mode, the wall of text it produces, if gone through step by step, might give a clue.

```

/usr/sbin/sshd -ddd

```

---

### Post by steeldriver on 2014-11-14
What is the exact error when you try to connect? Have you tried invoking the ssh *client* with verbosity turned up (-v or -vv or -vvv)?

In a comment on your own askubuntu post you said

> I can ssh into localhost on the machine locally

which suggests it is either a firewall or a port forwarding issue. Are you running any kind of flood control (such as fail2ban) in addition to ufw?

---

### Post by joe146 on 2014-11-14
SSh is defintely running. 

I get the following:

```
ssh start/running, process 874
```

Here's the config for sshd from a server that's identical. 

```

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes



```

I don't have fail2ban installed. I checked iptables and disabled it and also ran iptables -F and it still doesn't help.

When I try to access the server through SSH or SFTP, I don't even get a warning or anything. When I browse its https address, it just time-out. I can browse it at its http address.


The system, a VM, was Vmotion yesterday. That's when I noticed that issue started occuring. I had the system Vmotion back to its original host, but it still doesn't seem to help. I have another VM that's running nearly an identical setup, and it doesn't exhibit this issue. Is there a way to reset the underlying security mechanism used by SSH, SFTP, and HTTPS? 

Thanks for the suggestions BTW.

---

### Post by Lars Noodén on 2014-11-14
> **joe146 said:**
> Is there a way to reset the underlying security mechanism used by SSH, SFTP, and HTTPS?

HTTPS and SSH are quite different and unrelated.  However, you mention that the system is running in a VM.  That is probably where the problem lies.  How are you forwarding ports from the host to the guest?

---

### Post by joe146 on 2014-11-14
Well, I just decided to completely shut down the VM and then start it back up. After doing so, I am now able to access it through SSH\SFTP\HTTPS. I guess shutting it down cleared out some sort of temp files on the host or something... Anyways, thanks for the help!

---

