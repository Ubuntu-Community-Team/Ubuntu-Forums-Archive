---
title: "Ubuntu firewall or blocked ports?"
date: 2005-11-07
forum: Server Platforms
---

### Post by ShawnMilo on 2005-11-07
I am trying to use port forwarding in Ubuntu Server, but my SSH client keeps telling me that the attempt to forward the ports is being rejected.

I have tried multiple applications on my Ubuntu server, including squid and tinyproxy, so I know that the problem isn't with the proxy server application I'm using. Ubuntu is blocking these ports.

Does anyone know how or where firewall or port blocking rules are defined in Ubuntu Server?

Details:
Server: Ubuntu server. I have no problem getting an SSH session into this machine.

Client: Putty on Windows.

User: Me. I have successfully done everything I'm trying to do here on a Debian box, with both tinyproxy and Squid. The only difference here is Ubuntu instead of Debian, so it's something with Ubuntu's setup.

Thank you,
Shawn Milo

---

### Post by dbott67 on 2005-11-07
Just a few questions first:

What is th IP address of the server and of your PC?  Are they both on the same subnet?

Did you enable the firewall?  If you're unsure, try downloading 'firestarter' from Synaptic (to act as a GUI front-end) and then disable the firewall from there.  Or just try flushing the iptables (I think it's 'iptables -F' --- check the man file to be sure).

[EDIT] I just re-read your post: the firewall is 'iptables' and you can run it from the command line.  As metioned, check the man pages for all the gory details.  An easier method is to download 'firestarter' from Synaptic, which is a GUI front-end.  Download it and you should be able to enable/disable until your heart's content.[/EDIT]

-Dave

---

### Post by LordHunter317 on 2005-11-07
> **ShawnMilo]Does anyone know how or where firewall or port blocking rules are defined in Ubuntu Server?[/quote]There aren't any OOB.  At most, they could have made an sshd_config change (post it), but there' said:**
> The only difference here is Ubuntu instead of Debian, so it's something with Ubuntu's setup.No, I don't believe that's the case.  In any case, why did you start a new thread?

---

### Post by ShawnMilo on 2005-11-07
I started a new thread because people kept asking off-topic questions assuming that I was mis-configuring squid or something. I know that the problem lies elsewhere. I thought it would be better to re-word the question.

Here are the results of iptables -L:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I then ran iptables -F, but no change occurred -- the output of iptables -L looks the same.

Here is my sshd config file. I have made no edits to it other than to have it listen on port 443.

Thanks,
Shawn


# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 443
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


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by LordHunter317 on 2005-11-07
[QUOTE=ShawnMilo]I started a new thread because people kept asking off-topic questions assuming that I was mis-configuring squid or something.[/quote]No, that's not the case.  You haven't shown it's the case until you post the configuration.  Which would be prudent to do so, just in case.  You could be right, but there's a multiude of errors that could be there.  In any case, it was hardly offtopic.

Ok, now post the exact SSH command you're running, and any relevant errosr in the log file.  You may want to run sshd in debug mode, and post the output here.

---

