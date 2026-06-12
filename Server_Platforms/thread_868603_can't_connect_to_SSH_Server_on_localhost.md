---
title: "can't connect to SSH Server on localhost"
date: 2008-07-24
forum: Server Platforms
---

### Post by sliorda on 2008-07-24
Hi.

I installed openssh-server on hardy, changed the port number on /etc/ssh/sshd_config and restarted the service. when trying to test it, i'm getting this:

```
$ ssh -p 22111 localhost -vvv
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22111.
debug1: Connection established.
debug1: identity file /home/lior/.ssh/identity type -1
debug1: identity file /home/lior/.ssh/id_rsa type -1
debug1: identity file /home/lior/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

I've found some topics related to this issue, but with no answers on how to solve it.

Can anyone help?

---

### Post by cariboo on 2008-07-24
Does it work if you use the default port?

Jim

---

### Post by pdwerryhouse on 2008-07-24
Take a look at the files /var/log/daemon.log and /var/log/auth.log and see if sshd is putting any errors in there...

---

### Post by sp0nge on 2008-07-24
I had a similar issue, I was attempting to change the port to a higher number but was unsuccessful to this point. 

Before going much further, I changed back to the default port and it worked- can you try the same?

---

### Post by sliorda on 2008-07-24
I changed the port number back to 22, and now it's working. Thanks.

Is there any firewall i'm not aware of? `ufw status` says it's disabled and iptables -L says I can accept all connections.

---

### Post by sp0nge on 2008-07-24
I'm not exactly sure what the malfunction is, but I'll be working on this on my end as well- if I get a solution I'll post it, as I really don't want to keep a common port accessible if possible.

---

### Post by sliorda on 2008-07-24
hi guys.

I opened a bug on launchpad. in my original post i changed the port number i used for privacy, but apparently the port number is very related to this problem.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/251620](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/251620)

thanks

---

### Post by Stoneface on 2008-08-20
I installed openssh client and server and tried to connect to a Ubuntu server from my ubuntu desktop for the first time instead of using Putty in Windows. So I am brand new to using openssh from the command line....
When I entered ```
ssh 111.111.1.1
``` (changed ip address)I received this error:```
Read from socket failed: Connection reset by peer
```

```
My sshd configuration file states:

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

Any ideas what this error means?

---

### Post by windependence on 2008-08-20
Format is ssh [email]user@xxx.xxx.xxx.xxx[/email]

You can do this right from the CLI. Not sure what you mean by ssh client?

-Tim

---

### Post by Stoneface on 2008-08-20
Well I tried user@ip address and @domain name., but I still get the error Read from socket failed: Connection reset by peer

---

### Post by MJN on 2008-08-20
Run ssh with logging enabled (-vvv as per the OP's output) as this may give some clues as to what's wrong.  Checking the logs at the server end is also wise.
 
Mathew

---

### Post by Stoneface on 2008-08-21
Well, maybe it has somehing to do with the open ssh upgrade I did yesterday(complete distro upgrade including open ssh upgrade). Somehow I do not have proper authority anymore. The auth log states error host key .... How can I adjust this in the ssh configuration?

---

### Post by Stoneface on 2008-08-25
Well apparently I am being blocked by the main server (did an nmap). I hope this will be settled soon. When it does I will double check the SSH connection through port 22 and let you know...

---

### Post by Stoneface on 2008-08-25
I did a new nmap after I gave the ICT dept. all the information to unblock the ports and this was the result:
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 4.6p1 Debian 5ubuntu0.5 (protocol 2.0)
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain
80/tcp   open  http        Apache httpd 2.2.4 ((Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e)
110/tcp  open  pop3        Courier pop3d
143/tcp  open  imap        Courier Imapd (released 2005)
443/tcp  open  http        Apache httpd 2.2.4 ((Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_ssl/2.2.4 OpenSSL/0.9.8e)
993/tcp  open  ssl/unknown
995/tcp  open  ssl/unknown
3128/tcp open  http-proxy  Squid webproxy 2.6.STABLE14
3306/tcp open  mysql       MySQL (unauthorized)

All necessary ports seem to be open, but I cannot SSH into the server. Connection is still reset by peer.... I just don't get it.

---

### Post by Stoneface on 2008-08-26
Well, I think the fact that I activated key authentication is the culprit:

jasper@jasper-laptop:~$ ssh [email]jasper@domain[/email] -vv
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx.x.xx [xxx.xxx.x.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/jasper/.ssh/identity type -1
debug1: identity file /home/jasper/.ssh/id_rsa type -1
debug1: identity file /home/jasper/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.5
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
 How do I get back to normal password authentication?

---

### Post by Stoneface on 2008-08-27
Anybody? Please? I still cannot access my server. getting pretty desperate:( I even uninstalled and installed openssh-server on my desktop and tried to reconnect, but I guess I is still a server related openssh issue:

```
jasper@jasper-laptop:~$ ssh jasper@xxx.xx.xxx -vv
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to www.xx.xxx [xxx.xxx.x.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/jasper/.ssh/identity type -1
debug1: identity file /home/jasper/.ssh/id_rsa type -1
debug1: identity file /home/jasper/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.5
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

---

### Post by Stoneface on 2008-08-27
Anybody?

---

### Post by windependence on 2008-08-27
Working on this...

How are you trying to acces the box, from another Linux box or from Windoze?

-Tim

---

### Post by Stoneface on 2008-08-28
From another linux (Ubuntu) laptop. When I restart ssh on the server it indicates that two hostkeys are blacklisted.... In auth.log there is a sshd error indicating a problem with the host key as well.
I just want to have normal password access. Maybe I need to remove the public and private key? Or remove openssh on the server and reinstall using:```
apt-get remove --purge openssh-server 
```? I just don't know. I am quite new to server maintenance and openssh...

---

### Post by Stoneface on 2008-08-28
I entered ```
sudo ssh-vulnkey -a
``` There appear to be two vulnerable keys in etc/ssh/ (public and private). How can I remove these?

---

### Post by windependence on 2008-08-28
Here is some information that should help:

[http://www.civicactions.com/blog/howto_secure_your_ssh_ssl_and_openvpn_keys_generated_on_debian_ubuntu_and_related_distributions](http://www.civicactions.com/blog/howto_secure_your_ssh_ssl_and_openvpn_keys_generated_on_debian_ubuntu_and_related_distributions)

[http://blog.niekie.com/2008/05/14/how-to-deal-with-the-recent-random-number-generator-bug-in-openssl-and-update-your-ssh-keys/](http://blog.niekie.com/2008/05/14/how-to-deal-with-the-recent-random-number-generator-bug-in-openssl-and-update-your-ssh-keys/)

-Tim

---

### Post by Stoneface on 2008-08-28
Well I completely removed the openssh-sever and purged all ssh files and did a reinstall. It is working again now!

---

### Post by windependence on 2008-08-28
Very cool! ;)

-Tim

---

