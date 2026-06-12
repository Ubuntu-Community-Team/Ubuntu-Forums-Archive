---
title: "Sudo Allows Root Command Access Without Password"
date: 2008-05-05
forum: Security
---

### Post by Traumadog on 2008-05-05
Today, I noticed that the sudo command was granting me root command access without requesting  password verification.  Originally I assumed it was just an unexpired timestamp issue, but I found that this continued long past the expected (default?) 15 minute time frame.  I also tried "killing" the sudo session timestamp with both the -k and -K options, and I was still granted root access without password verification.  As you may expect, this has me somewhat concerned.  As best as I can ascertain, none the other regular users of the system have been granted root privileges, and I have no new, unauthorized, users that have suspiciously "appeared" on the system.  Further, I've not noticed any other strange or unexpected activity on the system.  Regular users when using the sudo command are challenged with a password prompt, are not allowed root command access, and the activity is reported to me via email as would be expected. 

My question is two fold.  First, how do I return sudo to the behavior of requiring password authorization to grant privileges, and second, what actions should I take to prevent this from occurring again?  

Any help will be greatly appreciated.

Thanks in advance!

Best wishes,

Traumadog.

---

### Post by p_quarles on 2008-05-06
What are the contents of /etc/sudoers?

---

### Post by Traumadog on 2008-05-06
The contents of my /etc/sudoers are as follows:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo'command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults       !lecture,tty_tickets,!fqdn

# User privilege specification
root   ALL=(ALL) ALL

#Members of the admin group may gain root privileges

%admin   ALL=(ALL) ALL
```

( The above was transcribed by me from the actual file.  I have not tried to alter the file on my system in any way from it's original settings. )

Thanks in advance for helping me with this! :)

---

### Post by cdenley on 2008-05-06
That sudoers file looks correct, so what you are experiencing doesn't make much sense. Post the output for these commands
```

alias
sudo -l
whoami
sudo -K
sudo whoami

```
For the last command, are you still not being prompted for a password?

---

### Post by Traumadog on 2008-05-06
> **cdenley said:**
> That sudoers file looks correct, so what you are experiencing doesn't make much sense. Post the output for these commands
```

alias
sudo -l
whoami
sudo -K
sudo whoami

```
For the last command, are you still not being prompted for a password?

Ok, here is the output from the above requested commands:

```
alias
alias ls='ls --color=auto'

sudo -l
user <my username> may run the following commands on this host:
(ALL) ALL

whoami
<returns my username>

sudo -K
<returned a standard system prompt.  No other response.>

sudo whoami
root
<There was no password prompt.>
```

Let me know what you think.

Thanks for your help! :-)

---

### Post by p_quarles on 2008-05-06
While I haven't experienced anything like this myself, I have to wonder if this is related to the recent update of sudo. Please post the output of the following:
```
apt-cache policy sudo
```

---

### Post by Traumadog on 2008-05-06
> **p_quarles said:**
> While I haven't experienced anything like this myself, I have to wonder if this is related to the recent update of sudo. Please post the output of the following:
```
apt-cache policy sudo
```

Ok, here's the output from the above request:

```
apt-cache policy sudo
Sudo:
  Installed:  1.6.8p12-1ubuntu6
  Candidate:  1.6.8p12-1ubuntu6
  Version table:
 xxx 1.6.8p12-ubuntu6 0
       500 cdrom://Ubuntu-Server 6.06.1_Dapper Drake_ - Release i386 (20060807.1)dapper/main Packages
       500 http://archive.ubuntu.com dapper/main Packages
       100 /var/lib/dpkg/status
```

Thanks for your help! :)

---

### Post by p_quarles on 2008-05-06
Hmm. I didn't realize you were using Ubuntu 6.06. How long has this system been installed? I assume from your first message that it was behaving correctly until just recently?

---

### Post by Traumadog on 2008-05-06
> **p_quarles said:**
> Hmm. I didn't realize you were using Ubuntu 6.06. How long has this system been installed? I assume from your first message that it was behaving correctly until just recently?

You're correct. This started yesterday evening (05 May 2008 ).  

I have been running the system since late December 2006.

---

### Post by wirelessmonkey on 2008-05-06
Take a look at /var/log/auth.log

When was the last time (according to logs) that you sudo'd?
If you feel comfortable doing so, post the last few dozen relevant lines.

---

### Post by Traumadog on 2008-05-07
> **wirelessmonkey said:**
> Take a look at /var/log/auth.log

When was the last time (according to logs) that you sudo'd?
If you feel comfortable doing so, post the last few dozen relevant lines.

Please find below the requested lines which have been extracted from my /var/log/auth.log file. The only change to the logs are the user names which have been altered.  Log entries which show <user name2>  being denied to run certain commands is not suspect because that was activity by me to see if users not in the admin group were challenged with a password prompt.  All other activity is mine as well.

Once again, thank you to everyone that is helping me with this.  :-)

```
May  2 07:27:27 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/update-manager
May  5 15:44:04 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/sbin/synaptic
May  5 15:47:31 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/update-manager
May  5 16:12:52 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name>/Downloads/DenyHosts-2.6 ; USER=root ; COMMAND=/usr/bin/python setup.py install
May  5 16:20:21 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/bin/cp denyhosts.cfg-dist denyhosts.cfg
May  5 16:35:35 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/usr/bin/nano denyhosts.cfg
May  5 16:36:21 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/usr/bin/nano denyhosts.cfg
May  5 16:37:26 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=list
May  5 16:39:56 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/nano /etc/sudoers
May  5 16:44:11 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/sbin/firestarter
May  5 16:46:33 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/users-admin
May  5 16:46:35 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/bin/sh -c env LANG="en_US.UTF-8" LANGUAGE="en" /usr/share/setup-tool-backends/scripts/users-conf &#8211;report
May  5 16:51:04 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/sbin/firestarter
May  5 16:53:01 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/disks-admin
May  5 16:53:02 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/bin/sh -c env LANG="en_US.UTF-8" LANGUAGE="en" /usr/share/setup-tool-backends/scripts/disks-conf --report
May  5 16:53:41 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/sbin/synaptic
May  5 16:54:03 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/services-admin
May  5 16:54:05 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/bin/sh -c env LANG="en_US.UTF-8" LANGUAGE="en" /usr/share/setup-tool-backends/scripts/services-conf --report
May  5 16:55:07 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/network-admin
May  5 16:55:08 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/bin/sh -c env LANG="en_US.UTF-8" LANGUAGE="en" /usr/share/setup-tool-backends/scripts/network-conf --report
May  5 16:58:49 Server1 sudo:    <user name> : TTY=unknown ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/time-admin
May  5 16:58:51 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/bin/sh -c env LANG="en_US.UTF-8" LANGUAGE="en" /usr/share/setup-tool-backends/scripts/time-conf --report
May  5 17:01:39 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/usr/bin/nano denyhosts.cfg
May  5 17:05:09 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/bin/cp daemon-control-dist daemon-control
May  5 17:06:34 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/usr/bin/nano daemon-control
5 17:13:12 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/bin/chown root daemon-control
May  5 17:13:34 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/usr/share/denyhosts ; USER=root ; COMMAND=/bin/chmod 700 daemon-control
May  5 17:15:04 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/bin/ln -s /usr/share/denyhosts/daemon-control denyhosts
May  5 17:15:49 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/sbin/update-rc.d denyhosts defaults
May  5 17:17:00 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/etc/init.d/denyhosts start
May  5 18:10:31 Server1 sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=pts/0 ruser= rhost=  user=<user name2>
May  5 18:11:05 Server1 sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=pts/0 ruser= rhost=  user=<user name2>
May  5 18:12:09 Server1 sudo:  <user name2> : command not allowed ; TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=list
May  5 18:36:36 Server1 sudo:  <user name2> : user NOT in sudoers ; TTY=pts/0 ; PWD=/ ; USER=root ; COMMAND=/bin/mkdir xfiles
May  6 08:04:13 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/nano /etc/sudoers
May  6 08:05:07 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/nano /etc/sudoers
May  6 12:41:32 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=list
May  6 12:44:11 Server1 sudo:    <user name> : TTY=pts/0 ; PWD=/home/users/<user name> ; USER=root ; COMMAND=/usr/bin/whoami

```

---

