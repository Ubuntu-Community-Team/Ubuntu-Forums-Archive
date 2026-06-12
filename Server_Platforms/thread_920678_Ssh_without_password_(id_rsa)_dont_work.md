---
title: "Ssh without password (id_rsa) dont work"
date: 2008-09-15
forum: Server Platforms
---

### Post by pc-cito on 2008-09-15
Hi all.

I'm under Ubuntu server 8.04 and Open-ssh 4.7p1

I need to connect via ssh two servers: S1 to S2

Now what i do:

S1: ssh-keygen -t rsa
S2: mkdir .ssh
S1: cat .ssh/id_rsa.pub | ssh user@S2 'cat >> .ssh/authorized_keys'
S2: chmod 644 .ssh/authorized_keys

This dont works, if i try to connect S1 to S2 always ask me for a password.

Here is my S2 sshd_config

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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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

UsePAM yes


```

I edit PermitEmptyPasswords to yes, and dont work.

I uncomment #AuthorizedKeysFile     %h/.ssh/authorized_keys but dont works too.

Always when i made a change, i restart sshd

I made everything in [https://help.ubuntu.com/community/AdvancedOpenSSH#Troubleshooting](https://help.ubuntu.com/community/AdvancedOpenSSH#Troubleshooting) and nothing to do.

Previusly, i use Debian etch and i havent any problem with it; now i use S1 (Debian) and S2 (ubuntu)

I unistall openssh-server in S2 and nothing.

I dont know what to do now

---

### Post by kevdog on 2008-09-15
I would trying going to S2, and see if you can connect to itself using only keys in question:

ssh localhost

You could also debug the output using the 

ssh -vvv <complete here>

3 v's = verbose output

---

### Post by pqrs541 on 2008-09-16
You just might be a Red Neck if You've ever used lard in bed. Your home has more miles on it than your car.[world of warcraft](http://www.mmoinn.com)There is a stuffed possum anywhere in your house.[cheap wow gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)[wow power leveling](http://www.mmoinn.com) [power leveling](http://www.mmoinn.com)

---

### Post by wayover13 on 2010-12-06
> Another thing you can try is setting StrictMode No in your sshd_config file, this disables Strict modes on directories.

Found at [http://www.linuxquestions.org/questions/linux-networking-3/ssh-public-key-authentication-205137/](http://www.linuxquestions.org/questions/linux-networking-3/ssh-public-key-authentication-205137/) . Solved my problem.

James

---

### Post by cacycleworks on 2011-12-09
This issue was really stumping me and I didn't want to just arbitrarily turn off strict mode.

Turns out I had user home directories chmod 775 and they must not be group writable. Ah, OK, I agree with this. :) And that was my fix.

Thanks,
Chris

---

### Post by hawkmage on 2011-12-09
The StrictModes requires that the ~/.ssh permissions to not include write to group or other and the ~/.ssh/authorixes_keys should not be readable or writable by group or other.  

The permission on your home directory should not matter at all.

---

### Post by cacycleworks on 2011-12-12
Not wanting to argue, but my experience conflicts with that. ~shrugs~ It works now, so I'm happy...

I'm not intimate with it, but do fresh install with 10.04.3 current ISO with no other changes. This lone change allowed me to log into our work server (4 disk hardware RAID) which is 10.04 server with as few changes as possible.

Thanks,
Chris

---

