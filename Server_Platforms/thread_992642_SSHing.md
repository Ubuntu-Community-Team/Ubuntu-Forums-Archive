---
title: "SSHing"
date: 2008-11-24
forum: Server Platforms
---

### Post by quikone8 on 2008-11-24
I have bee trying various ways to control my server remotely.  I have tried remote desktop to no avail, the system will not accept a password.  All I get is a black screen and no activity.  I have also tried to terminal in with SSH which get me the following activity;

ssh [email]name@domain.com[/email]
[email]name@domain.com[/email]'s password:
Permission denied, please try again

which I try three times then I get;

Permission denied (publickey,password,keyboard-interactive).

I have tried many of the suggestions in the forum and google short of reinstalling open ssh, any ideas?

---

### Post by __Ryan__ on 2008-11-24
When you are logged on to your server try opening an shh connection to itself. This should tell you if it is a configuration problem or a network issue.

---

### Post by quikone8 on 2008-11-25
Thanks for the reply, I will be back in the office in about 18 hours, I will give it a try.  Thanks for the reply.  Also I have got a post under virtualization that I would sure appreciate some help with.  A short explanation is; I am trying to get a mail server and a web server to play nice together and am not having much luck.

Thanks,

Ron

the title of the post is; linux/version.h

---

### Post by cmittle on 2008-11-25
Maybe this is a silly question, but have you forwarded the port (22 is default) on your router (assuming you have a router between the modem and your home server)??

---

### Post by volker48 on 2008-11-25
> **quikone8 said:**
> I have also tried to terminal in with SSH which get me the following activity;

ssh [email]name@domain.com[/email]
[email]name@domain.com[/email]'s password:
Permission denied, please try again

which I try three times then I get;

Permission denied (publickey,password,keyboard-interactive).

I have tried many of the suggestions in the forum and google short of reinstalling open ssh, any ideas?

What SSH client are you using to try and connect? Are you connecting from inside your network or outside? Based on the activity you are getting it would seem like you are getting to the server but are having issues with authenticating your username and/or password. This document was helpful when I was setting up my server [https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html). I would double check your /etc/ssh/sshd.conf file to make sure everything is ok there first.

As a side note, I would definitely change the port to something other than 22 and also disable password authentication and switch to a PKI setup. I had my server running on port 22 and had ip addresses from China, North Korea, and eastern Europe trying to hack into my server. Here is a good link for configuring passswordless authentication [http://www.ibm.com/developerworks/library/l-keyc.html](http://www.ibm.com/developerworks/library/l-keyc.html), but certainly get password authentication working first.

---

### Post by spiderbatdad on 2008-11-25
> **quikone8 said:**
> I have bee trying various ways to control my server remotely.  I have tried remote desktop to no avail, the system will not accept a password.  All I get is a black screen and no activity.  I have also tried to terminal in with SSH which get me the following activity;

ssh [email]name@domain.com[/email]
[email]name@domain.com[/email]'s password:
Permission denied, please try again

which I try three times then I get;

Permission denied (publickey,password,keyboard-interactive).

I have tried many of the suggestions in the forum and google short of reinstalling open ssh, any ideas?

Looks like you need to configure /etc/ssh/sshd_config
consider options like:
```
# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes
[B]
RSAAuthentication no
PubkeyAuthentication no
#AuthorizedKeysFile	%h/.ssh/authorized_keys[/B]

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
[B]PasswordAuthentication yes
[/B]
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

**UsePAM yes**

``` shown in bold above. Or you will have to create the public and private keys on each machine respectively.

---

### Post by quikone8 on 2008-11-25
Okay I have tried all the above including completely removing SSH from the server.  I have also tried to ssh into the server while sitting in front of it, I still get the same results.:confused:

BTW; I have used putty, terminal and konsole.

Another question, Where is the config file picking up the password for verification?

---

### Post by amac777 on 2008-11-25
If you post your /etc/ssh/sshd_config file here we can look at it to see if there are any obvious problems.

---

### Post by volker48 on 2008-11-25
Passwords are usually stored in /etc/passwd or /etc/shadow, but if you try and login with the same user and password you use to access the server I can't see why it isn't working.

---

### Post by quikone8 on 2008-11-25
> **amac777 said:**
> If you post your /etc/ssh/sshd_config file here we can look at it to see if there are any obvious problems.

Thanks, Here it is;

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 3535
Port 8080
Port 443
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation no	

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin yes
StrictModes no

#RSAAuthentication no	
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts no	

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

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

---

### Post by spiderbatdad on 2008-11-25
the name and password are valid user accounts. Are you sure you are using the correct command? ssh user@computer  (only on local networks)

locally i only use ssh user@machine  where that might be "ssh bob@bob-latop, but outside the local network i would use "ssh bob:192.168.1.100@66.255.46.48

try the gui for kicks: Applications>>Places>>Connect to Server
You should only need the server name and user name. Make sure you get the computer name correct.

Edit: missed your config post. I see what I believe are some problems you are having.```
# What ports, IPs and protocols we listen for
**Port 22**
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation** yes**

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin yes
StrictModes** yes**

``` some suggestions shown in bold.

---

### Post by amac777 on 2008-11-25
I didn't see any "problems" with your config file, but something is strange because your config file shows that the sshd is listening on these three non-standard ports:

> # What ports, IPs and protocols we listen for
Port 3535
Port 8080
Port 443

But the way you said you attempted to connect in your initial post was "ssh [email]name@domain.com[/email]", which would try to use the standard port (22) only.

With the above config file, your original attempt to connect on port 22 should have resulted in a "connection refused" message instead of letting you try to login.... But clearly that is not what happened, so something is weird.

I'm not sure why you would seem to connect to a server on port 22 when there should be nothing listening there... this seems to indicate you are trying to connect to the wrong computer.... Are you running the sshd server from within a virtualized environment? That might explain it.

Anyway, the way you should connect to those ports is:

ssh -p 443 [email]name@domain.com[/email]

Or, if you want to try it locally from the server:

ssh -p 443 name@localhost

---

### Post by quikone8 on 2008-11-26
> **amac777 said:**
> I didn't see any "problems" with your config file, but something is strange because your config file shows that the sshd is listening on these three non-standard ports:



But the way you said you attempted to connect in your initial post was "ssh [email]name@domain.com[/email]", which would try to use the standard port (22) only.

With the above config file, your original attempt to connect on port 22 should have resulted in a "connection refused" message instead of letting you try to login.... But clearly that is not what happened, so something is weird.

I'm not sure why you would seem to connect to a server on port 22 when there should be nothing listening there... this seems to indicate you are trying to connect to the wrong computer.... Are you running the sshd server from within a virtualized environment? That might explain it.

Anyway, the way you should connect to those ports is:

ssh -p 443 [email]name@domain.com[/email]

Or, if you want to try it locally from the server:

ssh -p 443 name@localhost

I finally got it to respond on port 443, I tried 3535 and 8080 but no response.

So the syntax that was finally successful was

ssh -p 443 [email]me@myserver.com[/email]  it asked for a password and actually let me in.  Now I need to find out why port 22 does'nt work.

---

### Post by amac777 on 2008-11-26
If you want it to work on the normal port, edit your sshd config file to include port 22 and then restart sshd. (sudo /etc/init.d/sshd restart)

Maybe ports 3535 and 8080 don't work because there is already another service using those ports?

To see what programs are listening on which ports use:

```
sudo netstat -tlpn
```

---

