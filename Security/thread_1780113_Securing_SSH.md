---
title: "Securing SSH"
date: 2011-06-11
forum: Security
---

### Post by CVGH on 2011-06-11
I've just started using SSH and Vino and want to make sure I'm secure.

This is what I did:

1] Router forwards from port xxxx to 22
2] SSH uses RSA keys
3] sshd_config:
    ```
# Package generated configuration file # See the sshd_config(5) manpage for details 
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
LogLevel VERBOSE 

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

```4] SSH tunnels to Vino
5] UFW set limit on port 22

Other than denyhosts or fail2ban, anything else I need to do?

Thanks!

---

### Post by spiky001 on 2011-06-11
You could change the ssh port number 22 is the default number something higher will help

---

### Post by CVGH on 2011-06-11
> **spiky001 said:**
> You could change the ssh port number 22 is the default number something higher will help
Right, but if you scan my IP from the 'net, you would find that 22 is closed.....
I've set the port forwarding on my router to forward any SSH coming in on port xxx to 22.

---

### Post by bodhi.zazen on 2011-06-12
> **spiky001 said:**
> You could change the ssh port number 22 is the default number something higher will help

changing the default port quiets the logs, but does next to nothing to increase security.

Use keys and disable password authentication.

---

### Post by Hackuin on 2011-06-12
> **CVGH said:**
> Right, but if you scan my IP from the 'net, you would find that 22 is closed.....
I've set the port forwarding on my router to forward any SSH coming in on port xxx to 22.
Never under-estimate a port scanner.
If we scan your machine, with version() detection, it happily shows on what port you are running SSH.

A simple Nmap scan like, "nmap  -A -T4 p 1-65535 yourmachine" will tell, which port you are running SSH.

---

### Post by CVGH on 2011-06-12
> **Hackuin said:**
> Never under-estimate a port scanner.
If we scan your machine, with version() detection, it happily shows on what port you are running SSH.

A simple Nmap scan like, "nmap  -A -T4 p 1-65535 yourmachine" will tell, which port you are running SSH.

Yeah, but I'm hoping most script kiddies won't bother looking that far....

I think I'm ok with passwords off and keys.

Thanks!!

---

### Post by bodhi.zazen on 2011-06-12
> **CVGH said:**
> Yeah, but I'm hoping most script kiddies won't bother looking that far....

I think I'm ok with passwords off and keys.

Thanks!!

The will not , but script kiddies are a minor nuance and will only harm you if you use weak passwords. Do not get me wrong, if they get in they can do a bit of harm.

However, you easily defeat them by using keys and disabling passwords, which is a heck of a lot more security then security through obscurity (changing the port).

---

