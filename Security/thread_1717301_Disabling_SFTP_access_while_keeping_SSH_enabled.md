---
title: "Disabling SFTP access while keeping SSH enabled"
date: 2011-03-29
forum: Security
---

### Post by Daedalus_357 on 2011-03-29
right now i have vsftpd server installed for FTP access. I originally set it up for both FTP and SFTP, but found that SFTP disregarded any and all permission settings and user jailing that i had set up... so I am switching to just being standard FTP **(and please don't start posting about "oh you should switch back to SFTP" or questioning my decisions on it, it is *NOT* the topic of this thread!)**

so here is what's happening:

i've tried to disable SFTP in the sshd_config file, but i am still able to log into the ftp server under sftp through port 22 (which normally is ssh?) i've tried all kinds of things short of just blocking port 22, however I would prefer to be able to remote into my server via Putty (which has access restriction to ONLY allow my admin user account over ssh)...

Anyone got an idea of how to resolve this, because i can see this as a HUGE security risk to the server...

---

### Post by dacoolio on 2011-03-29
Rather than turning it off, why not just blacklist all IP addresses for SFTP? Since I'm really not sure how to disable SFTP alone.

---

### Post by njdove on 2011-03-29
You might consider OpenSSH's SFTP ChrootDirectory as explained in this post [http://ubuntuforums.org/showthread.php?p=6661058](http://ubuntuforums.org/showthread.php?p=6661058). You could thus retain the security of SSH while limiting the scope of file access.

---

### Post by bodhi.zazen on 2011-03-29
[http://www.cyberciti.biz/faq/rhel-centos-debian-unix-turnoff-sftp-server/](http://www.cyberciti.biz/faq/rhel-centos-debian-unix-turnoff-sftp-server/)

---

### Post by HermanAB on 2011-03-30
Howdy,

The very last line in /etc/ssh/sshd_config is the one that enables the SFTP feature.  Disable it and restart sshd.

---

### Post by Daedalus_357 on 2011-03-30
> **HermanAB said:**
> Howdy,

The very last line in /etc/ssh/sshd_config is the one that enables the SFTP feature.  Disable it and restart sshd.


This? :confused:
```
UsePAM yes
```That did nothing to disable it...

here is my sshd_config file:

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
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# Subsystem sftp /usr/lib/openssh/sftp-server

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

---

### Post by Daedalus_357 on 2011-03-30
> **dacoolio said:**
> Rather than turning it off, why not just blacklist all IP addresses for SFTP? Since I'm really not sure how to disable SFTP alone.
Unfortunately the issue with that is that my server is getting attacked at a rate of 150 attempts / day (over 20 or so IPs / day between ports FTP 21 and SSH 22). running a script to weed out all these addresses (especially per day) would not only exponentially increase the size of the "hosts.deny" file, but could potentially black-list one of my clients should their computer become compromised and attempt to brute force SFTP on 22. I would prefer to take the path of "most" resistance, but least effort. Disabling SFTP on port 22 would accomplish this without the need to blacklist hundreds of IPs (which i'm already doing for SSH on port 22 as it is... I just hit 200 individual IPs in a little under 6 days lol)

---

### Post by Doug S on 2011-03-30
No,
this Line:
 
Subsystem sftp /usr/lib/openssh/sftp-server
 
change it to this:
 
#Subsystem sftp /usr/lib/openssh/sftp-server
 
I tried it on my system with the expected result, that sftp became disabled.
I had assumed from your initial posting that you had tried this, as you mentioned disabling sftp in sshd_config.

---

### Post by Daedalus_357 on 2011-03-30
> **Doug S said:**
> No,
this Line:
 
Subsystem sftp /usr/lib/openssh/sftp-server
 
change it to this:
 
#Subsystem sftp /usr/lib/openssh/sftp-server
 
I tried it on my system with the expected result, that sftp became disabled.
I had assumed from your initial posting that you had tried this, as you mentioned disabling sftp in sshd_config.


Yes, I edited my previous comment to include a copy of my sshd_config file contents, you will see near the bottom that i have already commented it out... and sadly i'm still able to connect to my server via SFTP through filezilla...

"sftp://24.xxx.xxx.xx4" is what shows up in filezilla.

---

### Post by Daedalus_357 on 2011-03-30
> **Daedalus_357 said:**
> Yes, I edited my previous comment to include a copy of my sshd_config file contents, you will see near the bottom that i have already commented it out... and sadly i'm still able to connect to my server via SFTP through filezilla...

"sftp://24.xxx.xxx.xx4" is what shows up in filezilla.

I've also tried denying SFTP in ufw, but it only points to tcp port 115, yet filezilla uses port 22 for sftp so needless to say i'm utterly confused to say the least...

---

### Post by bodhi.zazen on 2011-03-30
You need to restart the ssh server after commenting out that line

```
sudo service ssh restart
```

Also you should use keys and disable password authentication.

---

### Post by Doug S on 2011-03-30
Disabling sftp via the ssh_config file will only disable the subsystem request for sftp. It will not prevent the sftp prgram from logging in via ssh to create the initial SSH link.

---

### Post by Daedalus_357 on 2011-03-31
> **Doug S said:**
> Disabling sftp via the ssh_config file will only disable the subsystem request for sftp. It will not prevent the sftp prgram from logging in via ssh to create the initial SSH link.

Figures... is there a way to prevent it, or am I basically screwed if I want to keep SSH open for remote administration?

---

### Post by Daedalus_357 on 2011-04-04
Bumping thread - no replies

---

### Post by bodhi.zazen on 2011-04-05
> **Daedalus_357 said:**
> Bumping thread - no replies

What is it you are wanting help with exactly ?

By disabling the sftp subsystem and restarting the ssh server you have effectively disables sftp. Sure a ssh connection may be opened with sftp connection attempts, but then the connection is closed.

Try it yourself :

```
sftp user@server -vvv
```

You will see a "ssh" connection is indeed started, indeed you enter your password or key, but then the connection is closed.

The output reads > subsystem request failed on channel 0

What is it you are wanting ?

---

