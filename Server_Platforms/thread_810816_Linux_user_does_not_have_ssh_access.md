---
title: "Linux user does not have ssh access"
date: 2008-05-28
forum: Server Platforms
---

### Post by awarberg on 2008-05-28
Hi

I'm running a Hardy server. I created myself as the sudo user during installation and added another user to the system. 

This user is denied when logging in via ssh even though he is using the correct username / password combination.

Which group should I put him in to give him ssh login rights?

The system is pretty plain ubuntu server, didn't make many configuration changes. Only thing I can think of messing up his login rights is that he is using a samba share I set up.

Thanks for your help.

Kind regards
Andreas

---

### Post by The Devil Is A Squirrel on 2008-05-28
> Allowed and Denied Users and Groups

You may use certain directives in your /etc/ssh/sshd_config file to allow, or deny login with ssh by certain users, or groups. This ability provides more fine-grained control over who has access to your Ubuntu computer(s) via ssh.

For example, if you wished to allow only the users jhendrix, and svaughan to login via ssh, you could use the AllowUsers directive in your /etc/ssh/sshd_config file as such:

AllowUsers jhendrix svaughan

[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

Hope that helps.

---

### Post by awarberg on 2008-05-29
OK I created a group called users. Then set this group as the default group for the other user and myself.

I issued sudo /etc/init.d/ssh restart and tried to login as him. I could still login as myself, however.

Here is my /etc/ssh/sshd_config:
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
AllowGroups users

```

Here are my user account and his:
```

awa:x:1000:100:My Name,,,:/home/awa:/bin/bash
kwa:x:1001:100:His Name:/home/kwa:/bin/sh

```

And the group I created:
```

users:x:100:

```

I don't understand why *I* am allowed to login while he is not. There my be some default group or setting that enables this.

Regards, Andreas

---

### Post by The Devil Is A Squirrel on 2008-05-29
Hmmm...did you try to allow specifically the two users and not the group? IMHO anyway better if you don't plan to administer more than 10 users...

And please disable root logins.
```
PermitRootLogin no
```

---

### Post by awarberg on 2008-05-29
Aha! I found a solution. It appears that the UNIX password was not synchronized with the samba password, which caused Access Denied messages for the other user.

When I created him I used:
```

$ sudo useradd kwa
$ sudo smbpasswd -a kwa

```

and gave him his code, which he was able to browse samba shares with.

It is my impression samba should synchronize the UNIX and smb passwords since I have this in my /etc/samba/smb.conf:
```

   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

```

Apparently something went wrong and the UNIX password was never set since I only used smbpasswd.

The conclusion is that I must now maintain user accounts in 3 different places: UNIX, samba and ppp. *Sigh* good thing I only have few users - this won't scale well.

Anyways I have restored /etc/ssh/sshd_config to its original configuration, restarted sshd and both accounts can login via ssh now.

Andreas

---

### Post by The Devil Is A Squirrel on 2008-05-29
I'm glad you found the solution. If your server is accessable from the internet, please consider to disable root logins nonetheless.

---

### Post by awarberg on 2008-05-29
I did that just now, thanks.

---

### Post by gtdaqua on 2008-05-29
opening ssh over internet could still be vulnerable for brute force attacks. Install 'denyhosts' to lockout IP addresses that brute force on your ssh.

---

### Post by The Devil Is A Squirrel on 2008-05-29
> **gtdaqua said:**
> opening ssh over internet could still be vulnerable for brute force attacks. Install 'denyhosts' to lockout IP addresses that brute force on your ssh.

Thanks for that, I didn't like fail2ban but this looks promissing.

---

### Post by gtdaqua on 2008-05-29
its handy and its scalable.

```

sudo apt-get install denyhosts

```

Then create a dummy file  "/etc/hosts.deny".

Then don't forget to configure the /etc/denyhosts.conf - read through the file and you will know what to do. Just setup SMTP settings for email reports.  

AND restart the denyhosts daemon.

```

sudo /etc/init.d/denyhosts restart

```

Can't believe it is that simple!

In a day you will find that IPs have been added to the /etc/hosts.deny file that have been probing ssh ports on your box.

---

### Post by The Devil Is A Squirrel on 2008-05-29
So far I did this:

```
#Block too many pings
-A INPUT -p icmp -m limit --limit 5/minute -j ACCEPT
-A INPUT -p icmp -j DROP

#Block too many SSH connections
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 240 --hitcount 3 --name DEFAULT --rsource -j DROP 
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name DEFAULT --rsource 
```

---

### Post by awarberg on 2008-05-29
Did you put this in /etc/denyhosts.conf?

---

### Post by The Devil Is A Squirrel on 2008-05-29
> **awarberg said:**
> Did you put this in /etc/denyhosts.conf?

Of course not, that's in my iptables.conf.

---

### Post by awarberg on 2008-05-29
Hmm I can't find this one:

```

awa@srv:~$ sudo updatedb
[sudo] password for awa:
awa@srv:~$ locate iptables.conf
awa@srv:~$

```

What am I missing here? :confused:

---

### Post by The Devil Is A Squirrel on 2008-05-29
Not so sure anymore, but I guess I stored my iptable entries in a .conf file (saved by shutdown/restart) and loaded it from there by booting the system. At least my Debian box lost its settings during shutdown/reboot. Don't know how this works in Ubuntu...

There you go: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by gtdaqua on 2008-05-29
Iptables may be too advanced(!) denyhosts is simple to setup.

---

### Post by The Devil Is A Squirrel on 2008-05-29
Might be. I included a script, which shows me how many attempts with which user and IP address was made. Does denyhost such statistical/report stuff too?

---

### Post by gtdaqua on 2008-05-29
the "hosts.deny" file shows only the service and IP blocked. Does not show the number of attempts made.  This is the output of one of my hosts.deny file:

> 
sshd: 59.106.12.179
sshd: 125.69.89.123
sshd: 202.102.245.121
sshd: 58.211.58.3
sshd: 222.234.3.202
sshd: 123.100.248.72
sshd: 121.8.104.3
sshd: 211.245.159.231
sshd: 122.53.243.73
sshd: 59.163.42.197
sshd: 124.42.41.6
sshd: 125.46.37.160
sshd: 60.248.155.1
sshd: 121.18.18.37


But do you really want to know the number of times an attempt was made? Denyhosts blocks after 5 consecutive attempts by default. You can block other services too.

---

