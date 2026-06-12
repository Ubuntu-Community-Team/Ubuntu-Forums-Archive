---
title: "[SOLVED] SSH Keypair problem"
date: 2008-09-06
forum: Server Platforms
---

### Post by Dr Small on 2008-09-06
I want to turn PasswordAuthentication off on my server, but in doing so, no one can connect over SFTP without entering a password.

So I plan to give every user a ssh key, (on our local network) and ran into a problem.

I created a ssh key on my sister's computer, and then transported the public ssh key to her account on the server by using:
```
ssh-copy-id -i ~/.ssh/id_dsa.pub firefoxwiz@mycroft
```

I entered the password, everything went A-OK. I can see from another SSH session that the .ssh directory was created and chmod'ed to 700, the authorized_key file in .ssh/ was created and chmod'ed to 600 and contains her SSH key.

I then set PasswordAuthentication to 'no', restart the SSH server, and she gets this error:
```
Permission denied (publickey).
```

Enabling -vvv gives me this:
```
debug2: key: /home/firefoxwiz/.ssh/identity ((nil))
debug2: key: /home/firefoxwiz/.ssh/id_rsa ((nil))
debug2: key: /home/firefoxwiz/.ssh/id_dsa (0x80054638)
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/firefoxwiz/.ssh/identity
debug3: no such identity: /home/firefoxwiz/.ssh/identity
debug1: Trying private key: /home/firefoxwiz/.ssh/id_rsa
debug3: no such identity: /home/firefoxwiz/.ssh/id_rsa
debug1: Offering public key: /home/firefoxwiz/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

I am at a loss as to what to do. The permissions match that of mine on my system, and I really can't find the problem.

Anyone have some suggestions?
Dr Small

---

### Post by souki on 2008-09-06
hello,

check the /var/log/auth.log file on the server side
post your sshd_config file here

---

### Post by Dr Small on 2008-09-06
As for as the auth.log spilling out any errors, it isn't for PublicKeyAuth.

Here is /etc/ssh/sshd_config:
```
drsmall@mycroft:~$ cat /etc/ssh/sshd_config 
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
PasswordAuthentication no

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
Banner /etc/issue

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
IgnoreUserKnownHosts no
```

---

### Post by souki on 2008-09-06
I don't see any problem with your setup
are you sure about your keys ?

---

### Post by Dr Small on 2008-09-06
> **souki said:**
> I don't see any problem with your setup
are you sure about your keys ?
I'm absolutely positive. I have added the public key from my sister's computer to my authorized_keys on my system, (not the server), and it works just fine. That's why I am stumped.

---

### Post by Dr Small on 2008-09-07
Hey, I read logwatch this morning, and found this:
```
 Public key a7:5a:d2:01:5e:86:80:2e:7d:86:70:64:a1:e3:e7:8e blacklisted (see
ssh-vulnkey(1)) : 23 time(s)

```

Would that have something to do with it? And if it does, how would I go about fixing it?

Thanks,
Dr Small

---

### Post by Dr Small on 2008-09-08
I got it fixed. The key apparently was one of the blacklisted keys since she was still running an older version of openssl. So, I totally removed openssh-server, deleted everything out of /etc/ssh, reinstalled openssh-server, deleted her keys, regenerated her keys, copied the public key to the server, and wahlah!

Finally, it works :)
Dr Small

---

