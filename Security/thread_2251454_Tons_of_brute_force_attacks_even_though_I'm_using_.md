---
title: "Tons of brute force attacks even though I'm using SSH keys"
date: 2014-11-04
forum: Security
---

### Post by nicole9 on 2014-11-04
Hey everyone, 

I have a ton of these entries in auth.log:

```

Nov  4 09:41:30 svr sshd[6113]: User root from 117.21.226.103 not allowed because not listed in AllowUsers
Nov  4 09:41:30 svr sshd[6113]: input_userauth_request: invalid user root [preauth]
Nov  4 09:41:32 svr sshd[6113]: fatal: Read from socket failed: Connection reset by peer [preauth]

```

Here's my sshd_config which it *supposed* to be stopping password authentication and only accepting keys (which I've tested and is working for me):

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
AllowUsers myuser

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

I have modified iptables-multiport.conf with the following - which is *supposed* to block brute force attacks:

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified by Yaroslav Halchenko for multiport banning and Lukas Camenzind for persistent banning 
#
#
[Definition]
# Option:  actionstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD
#
actionstart = iptables -N fail2ban-<name>
              iptables -A fail2ban-<name> -j RETURN
              iptables -I INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
              # Load local list of offenders
              if [ -f /etc/fail2ban/ip.blacklist ]; then cat /etc/fail2ban/ip.blacklist | grep -e <name>$ | cut -d "," -s -f 1 | while read IP; do iptables -I fail2ban-<name> 1 -s $IP -j DROP; done; fi
# Option:  actionstop
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD
#
actionstop = iptables -D INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
             iptables -F fail2ban-<name>
             iptables -X fail2ban-<name>
# Option:  actioncheck
# Notes.:  command executed once before each actionban command
# Values:  CMD
#
actioncheck = iptables -n -L INPUT | grep -q fail2ban-<name>
# Option:  actionban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionban = if ! iptables -C fail2ban-<name> -s <ip> -j DROP; then iptables -I fail2ban-<name> 1 -s <ip> -j DROP; fi
            # Add offenders to local blacklist, if not already there
            if ! grep -Fxq '<ip>,<name>' /etc/fail2ban/ip.blacklist; then echo '<ip>,<name>' >> /etc/fail2ban/ip.blacklist; fi
# Option:  actionunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionunban = iptables -D fail2ban-<name> -s <ip> -j DROP
              # Disabled clearing out entry from ip.blacklist (somehow happens after each stop of fail2ban)
              # sed --in-place '/<ip>,<name>/d' /etc/fail2ban/ip.blacklist
[Init]
# Defaut name of the chain
#
name = default
# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ssh
# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp

```

I have no idea why these brute force attackers are still able to attempt their attacks. It's causing massive disk I/O load on my server. Can anyone help? I'm guessing it's something obvious!

Thank you in advance!!!

---

### Post by addison6 on 2014-11-04
I do recommend finding with google ssh hardening.

1) Change your port number and open it only for your IP addresses. Change your port number and drop all requests on 22.

2) Ban IP addresses for 1d minimum if 3 failed attempts with Fail2Ban

3) DROP IP addresses with IPTables, even using CIDR notation.

4) Find a tutorial with Google for using just SSH keys and disable console. The idea is connecting your remote with your putty without password. For this you needs SSH keys to be stored on both computers. Be careful with this because if you enable it and disable console and something goes wrong in configuration you won't be able to ssh your server. But it is a solid protection.

Such of attempts to connect on SSH port are normal. Important is intensity. Use a software to monitor your server in real time. My VPS has around 1 attempt/minute to SSH.

---

### Post by nicole9 on 2014-11-04
Thanks so much for your reply! 

I had actually followed a guide to help me set up SSH keys and disable password authentication. Given these log entries, do you think that it isn't working correctly?

---

### Post by Lars Noodén on 2014-11-04
Keys and disabling password authentications won't prevent others from trying to get in, though it will stop them from being able to get in.   From what you've posted above, you have done that.  

sshguard or fail2ban will stop the attempts by adding a blocking rule to iptables for you.  Once in the block list, their packets won't even reach your SSH service.  So the place to look now would be in the configuration for fail2ban or sshguard.

---

### Post by mastablasta on 2014-11-06
you need to configure fail2ban to block after lets say 3 attempts. if you are sure you can even block after 1 attempt. in fail2ban local.jail you specify the IP for which these rules do not apply (likely your LAN). 

then block for 60 days or just forever (the -1 switch).:twisted:

it did increase during and arorudn 1st November for me as well. however they seem to be decreasing again. only a few attempts and they get blocked anyway.

---

### Post by matt_symes on 2014-11-06
Hi

Unless you're in China, do yourself a favour and ban all IP addresses (the IP address block) from China at the firewall level for your SSH port. Some of then are notorious for banging on scanned SSH ports. They have scripts running 24/7. 

That'll quieten your logs.

Kind regards

---

### Post by sandyd on 2014-11-06
> **nicole9 said:**
> Hey everyone, 

I have a ton of these entries in auth.log:

```

Nov  4 09:41:30 svr sshd[6113]: User root from 117.21.226.103 not allowed because not listed in AllowUsers
Nov  4 09:41:30 svr sshd[6113]: input_userauth_request: invalid user root [preauth]
Nov  4 09:41:32 svr sshd[6113]: fatal: Read from socket failed: Connection reset by peer [preauth]

```

Here's my sshd_config which it *supposed* to be stopping password authentication and only accepting keys (which I've tested and is working for me):

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
AllowUsers myuser

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

I have modified iptables-multiport.conf with the following - which is *supposed* to block brute force attacks:

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified by Yaroslav Halchenko for multiport banning and Lukas Camenzind for persistent banning 
#
#
[Definition]
# Option:  actionstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD
#
actionstart = iptables -N fail2ban-<name>
              iptables -A fail2ban-<name> -j RETURN
              iptables -I INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
              # Load local list of offenders
              if [ -f /etc/fail2ban/ip.blacklist ]; then cat /etc/fail2ban/ip.blacklist | grep -e <name>$ | cut -d "," -s -f 1 | while read IP; do iptables -I fail2ban-<name> 1 -s $IP -j DROP; done; fi
# Option:  actionstop
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD
#
actionstop = iptables -D INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
             iptables -F fail2ban-<name>
             iptables -X fail2ban-<name>
# Option:  actioncheck
# Notes.:  command executed once before each actionban command
# Values:  CMD
#
actioncheck = iptables -n -L INPUT | grep -q fail2ban-<name>
# Option:  actionban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionban = if ! iptables -C fail2ban-<name> -s <ip> -j DROP; then iptables -I fail2ban-<name> 1 -s <ip> -j DROP; fi
            # Add offenders to local blacklist, if not already there
            if ! grep -Fxq '<ip>,<name>' /etc/fail2ban/ip.blacklist; then echo '<ip>,<name>' >> /etc/fail2ban/ip.blacklist; fi
# Option:  actionunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionunban = iptables -D fail2ban-<name> -s <ip> -j DROP
              # Disabled clearing out entry from ip.blacklist (somehow happens after each stop of fail2ban)
              # sed --in-place '/<ip>,<name>/d' /etc/fail2ban/ip.blacklist
[Init]
# Defaut name of the chain
#
name = default
# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ssh
# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp

```

I have no idea why these brute force attackers are still able to attempt their attacks. It's causing massive disk I/O load on my server. Can anyone help? I'm guessing it's something obvious!

Thank you in advance!!!

If you are finding it difficult to configure fail2ban (which should block an ip after X failed attempts), try [CSF/LFD]("http://configserver.com/cp/csf.html")

Side Note: If you want a to set "safe" ips where you wont be blocked by LFD, add the IPs/subnets in /etc/csf/csf.ignore

---

### Post by HermanAB on 2014-11-06
You don't really need fail2ban and suchlike.  A simple rate limiting rule in iptables will have the same effect, without the danger of accidentally locking yourself out, or getting hit by a script that adds the whole world to the ban list.

[http://www.rackaid.com/blog/how-to-block-ssh-brute-force-attacks/](http://www.rackaid.com/blog/how-to-block-ssh-brute-force-attacks/)

---

