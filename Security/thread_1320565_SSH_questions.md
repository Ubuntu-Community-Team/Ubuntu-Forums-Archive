---
title: "SSH questions"
date: 2009-11-09
forum: Security
---

### Post by Rayve on 2009-11-09
Okay, so I've done a bunch of reading today to get my SSH set up, in order to be able to connect to my desktop through my netbook, and I have it working, except I have to allow Passwords.  I'd like to remove the passwords and just use the RSA authentication / pubkey authentication, if possible.

I tried adding denyhosts and fail2ban, but then I couldn't connect at all, so I will do more reading and enable them later.

Also, if I have a VPN, do I need to do a VPN bridge or something else?  The [https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer) was admittedly confusing for me.

Here is my /etc/ssh/sshd_config on my desktop, the server:

```

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
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```I've made sure there are no entries in my /etc/hosts.deny file - would adding a line to /etc/hosts.allow help?

Still learning all this SSH stuff, so please be gentle.  :)  Thanks!

ETA: When the passwords are enabled, I can ssh in with my netbook just fine.  When I turn  PasswordAuthentication to NO (as it is now), it goes all the way through the attempt (sending publickey packets) and then says "Permission denied (publickey)".

---

### Post by bodhi.zazen on 2009-11-09
You need to ssh in using a key.

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by Rayve on 2009-11-09
Sorry, I'm a bit confused - do I do this on my desktop (server) or on my netbook (client)?

> 
If you can log in to a computer over SSH using a password, you can transfer your RSA key by doing the following from your own computer: 

ssh-copy-id <username>@<host>Where <username> and <host> should be replaced by your username and the name of the computer you're transferring your key to. 
You can make sure this worked by doing: 

ssh <username>@<host>You should be prompted for the passphrase for your key: 
  Enter passphrase for key '/home/<user>/.ssh/id_rsa':
  
Enter your passphrase, and provided *host* is configured to allow key-based logins, you should then be logged in as usual. 


---

### Post by bodhi.zazen on 2009-11-09
> **Rayve said:**
> Sorry, I'm a bit confused - do I do this on my desktop (server) or on my netbook (client)?

Both

You can make the keys on the client (netbook) and transfer the key to the server (desktop).

When you make a key, there are two files. One file key stays on the client, the key.pub goes on the server in authorized keys.

---

### Post by BQAggie2006 on 2009-11-09
Not sure if you came across this, but it does a good job describing how to generate and upload keys.

[https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

Though I would change the type from dsa to rsa

---

### Post by Rayve on 2009-11-09
Thank you for the reply, except now I'm getting a Permission denied error when I try to do ssh-copy-id, it says denied to ~/.ssh/authorized_keys.

I did sudo chmod 700 ~/.ssh temporarily so I could make/copy keys, but no luck.

---

### Post by BQAggie2006 on 2009-11-09
Have you tried running the command with sudo?

---

### Post by Rayve on 2009-11-10
Yep, here's what I got, from my desktop:

```

candice@candice-desktop:~$ sudo ssh-copy-id <netbook user and server>
[sudo] password for candice: 
The authenticity of host '<netbook>' can't be established.
RSA key fingerprint is <fingerprint>
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '<netbook>' (RSA) to the list of known hosts.
<netbook>'s password: 
bash: .ssh/authorized_keys: Permission denied

```

ETA: Okay, I changed it to 777 real quick, then I was able to ssh in from my netbook and move the keys over to my desktop - and I see it now, in ~/.ssh/authorized_keys in my desktop.

I changed ~/.ssh back to 400, all good.

But the moment I change "no" on the passwordauthentication, I get the "Permission denied (publickey)" again from my netbook.

---

### Post by Lars Noodén on 2009-11-10
> **Rayve said:**
> Yep, here's what I got, from my desktop:


ETA: Okay, I changed it to 777 real quick, then I was able to ssh in from my netbook and move the keys over to my desktop - and I see it now, in ~/.ssh/authorized_keys in my desktop.

I changed ~/.ssh back to 400, all good.

But the moment I change "no" on the passwordauthentication, I get the "Permission denied (publickey)" again from my netbook.

Don't turn off PasswordAuthentication until you have the keys working.  You need to be able to log in.

As far as the permissions go, ~/.ssh should be **0700**, not 0400.  0400 will deny access  The files inside ~/.ssh should be **0600**, so you can read and write them.

```

# fix the directory permissions
chmod u=rwx,g=,o= ~/.ssh/

# fix the file permissions
chmod u=rw,g=,o= ~/.ssh/*

```

---

