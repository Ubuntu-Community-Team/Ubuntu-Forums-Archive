---
title: "PAM with SSH"
date: 2014-02-28
forum: Server Platforms
---

### Post by sniper8752 on 2014-02-28
I am trying to configure SSH to use PAM to limit logins to a group, such as sftpusers.  When I comment out the first block, it works fine logging in.  When I add the lines, and add the user to sftpusers, I get a fatal error from putty about a network error: software caused connection abort. Any ideas on how to fix this?

[ATTACH=CONFIG]250770[/ATTACH]

---

### Post by Lars Noodén on 2014-02-28
The normal way to limit logins to a group or groups would be to set that in [sshd_config](http://manpages.ubuntu.com/manpages/saucy/en/man5/sshd_config.5.html) either in a Match block or in the main body of the configuration file.

```

AllowGroups sftpusers 

```

Alternately, you can limit just the one group to just using SFTP and not otherwise able to log in.

```

Subsystem sftp internal-sftp

Match Group sftpusers
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

That will still allow people not in the group *sftpusers* to log in but force people in that group to only be able to use SFTP.

However, if you still wish to do it with PAM, there is probably a way.

---

### Post by steeldriver on 2014-02-28
... I noticed in the OP's screenshot there appears to be a small typo (upper case O in ForceCOmmand)

---

### Post by Lars Noodén on 2014-02-28
Oh.  I should have seen the screenshot.  But case should not matter, the configuration directives for sshd are case-insensitive.

---

### Post by sniper8752 on 2014-02-28
Here is a larger image of what I have in the sshd_config file.

[ATTACH=CONFIG]250774[/ATTACH]

---

### Post by Lars Noodén on 2014-03-01
In the larger image, I see that a 1 (one) has been substituted for an l (L).  It should be a [lower case L](http://manpages.ubuntu.com/manpages/saucy/en/man8/sftp-server.8.html)

```

Subssytem sftp internal-sftp -f AUTH -l VERBOSE

```

It's strange but no errors seem to show up in the logs when it is done with a 1.  I even tried logging to stderr in debug mode and nothing...

Anyway, try -l instead of -1

---

### Post by sniper8752 on 2014-03-02
I get this error: GnuTLS error -15: An unexpected TLS packet was received.

---

### Post by Lars Noodén on 2014-03-02
What does ssh or sftp when you try to connect using the -v or -vv options?

---

### Post by sniper8752 on 2014-03-02
When I use putty to login to a standard user account, it gives me the network error message.  When I login as root, or the admin account, it says access denied, as it should since I blocked root users from logging in.

---

### Post by Lars Noodén on 2014-03-03
Yes, I was thinking about what [ssh](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh.1.html)'s diagnostic messages say.  They will give much more info than what [PuTTY](http://manpages.ubuntu.com/manpages/saucy/en/man1/putty.1.html) says, I think.  A quick look through PuTTY's options didn't show me anything obvious in regards to debugging.  

Try opening a terminal and connecting using 'ssh -v' or 'ssh -vv'  That will give some information which may shed a light on the problem.

---

### Post by sniper8752 on 2014-03-03
Any way to do this from windows?

---

### Post by Lars Noodén on 2014-03-03
I wouldn't know.  I don't use it. 

Maybe if you have the server or a console on the server in front of you, you could launch a second instance of sshd and watch the debug info from it.  That might provide something.  

```

[s]/usr/sbin/sshd -p 2200 -d[/s]
sudo /usr/sbin/sshd -p 2200 -d

```

That will allow you to login, once, on port 2200 while sending all the debug info to stderr for you to read through.  Doing it that way leaves the 'original' sshd running so you can even do it remotely.

---

### Post by sniper8752 on 2014-03-03
So I tried connecting from windows, but didn't seem to get any other debug info.

---

### Post by Lars Noodén on 2014-03-03
I think I was able to duplicate your error on my system.  At least using your configuration as-is creates one.  

```

debug1: PAM: establishing credentials
bad ownership or modes for chroot directory "/home/foo"

```

Using [ChrootDirectory](http://manpages.ubuntu.com/manpages/saucy/en/man5/sshd_config.5.html) the target of the chroot, %h, has to be owned by root and not writeable by anyone else.  So if that is a user's home directory, then that home directory has to be 755 or 750 for root.  That creates some seconday logistical problems if the user also is expected to have a login shell, but if sticking with SFTP only then there is no problem.   

```

sudo chown root /home/foo
sudo chmod 755 /home/foo

```

---

### Post by Lars Noodén on 2014-03-03
> **sniper8752 said:**
> So I tried connecting from windows, but didn't seem to get any other debug info.

sshd needs to be launched as root to read the private host keys.  I should have mentioned it above, I'll edit it.

---

### Post by sniper8752 on 2014-03-03
> **Lars Noodén said:**
> I think I was able to duplicate your error on my system.  At least using your configuration as-is creates one.  

```

debug1: PAM: establishing credentials
bad ownership or modes for chroot directory "/home/foo"

```

Using [ChrootDirectory]("http://manpages.ubuntu.com/manpages/saucy/en/man5/sshd_config.5.html") the target of the chroot, %h, has to be owned by root and not writeable by anyone else.  So if that is a user's home directory, then that home directory has to be 755 or 750 for root.  That creates some seconday logistical problems if the user also is expected to have a login shell, but if sticking with SFTP only then there is no problem.   

```

sudo chown root /home/foo
sudo chmod 755 /home/foo

```

I am planning on having the user having a login.  I will see if I can get the config file posted on here somehow.

---

### Post by sniper8752 on 2014-03-04
Here is my sshd_config file:
```
# Package generated configuration file# See the sshd_config(5) manpage for details


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
AllowUsers bob admin
# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768


# Logging
SyslogFacility AUTH
LogLevel INFO


# Authentication:
LoginGraceTime 120
PermitRootLogin yes # changed this value to yes
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


X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


Subsystem sftp internal-sftp -f AUTH -l VERBOSE


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM yes # Started commenting out here
#AllowGroups sftpusers sftp
#Match Group sftpusers
#ChrootDirectory %h
#AllowTCPForwarding no
#ForceCOmmand internal-sftp

```

---

### Post by Lars Noodén on 2014-03-04
AllowUsers blocks subsequent use of AllowGroups, they don't mix.  It's not so clear in the documentation though.  

Can you describe the scenario(s) you wish to enable?

---

### Post by sniper8752 on 2014-03-04
What do you mean?  AllowUsers seems to work by itself.  
I would like to prevent root from being able to login directly, which I think would be a security feature.  Correct me if you don't think so.  I just think that they could use switchuser, or I think the command is, su.  but there will be other accounts that I would allow to have an account on the server, to be able to log on locally, as well as from afar to access documents, do work, or whatever the reason may be.

---

### Post by Lars Noodén on 2014-03-05
AllowUsers takes priority over AllowGroups.  Try them in a few permutations and see.

However, it is much simpler to prevent remote root logins.  Just set 

```

PermitRootLogin no

```

and that should do it.  Then to use root, they'll have to run either su or sudo, but that will at least give you a real login so that you know who to ask questions.

---

### Post by sniper8752 on 2014-03-05
I enabled pam, and the few lines that follow afterwards, and the root (admin) admin is not able to login, but the standard users get this error: network error: software caused connection abort.  how do i fix this so that standard users can ssh in?

---

### Post by steeldriver on 2014-03-05
If you don't mind having /home as the chroot (instead of /home/*user*) then this is what worked for me:

```

UsePAM yes

Match Group sftpusers
      ChrootDirectory /home
      ForceCommand internal-sftp

```

'Normal' users can still log in to their accounts, whereas any 'sftp-only' users are prevented from doing so by setting their login shells to /sbin/nologin (which is a symlink to /bin/false) 

```

$ getent group sftpusers
sftpusers:x:118:
$ getent passwd sftpuser1
sftpuser1:x:1003:118::/sftpuser1:/sbin/nologin

```

EDIT: even 'sftp-only' users need a valid login shell i.e. you need to add /sbin/nologin to the /etc/shells file (that's the reason for using a symlink i.e. it reserves /bin/false for accounts that are *really* permitted zero access - neither interactive login nor SFTP)

---

### Post by sniper8752 on 2014-03-05
I would only need it for users on the system, and they all need to be able to use the terminal.  They should be limited to their files (or home directories), so having one shared point may be an issue.  Is there any way around this?

---

### Post by sniper8752 on 2014-03-25
> **Lars Noodén said:**
> Yes, I was thinking about what [ssh]("http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh.1.html")'s diagnostic messages say.  They will give much more info than what [PuTTY]("http://manpages.ubuntu.com/manpages/saucy/en/man1/putty.1.html") says, I think.  A quick look through PuTTY's options didn't show me anything obvious in regards to debugging.  

Try opening a terminal and connecting using 'ssh -v' or 'ssh -vv'  That will give some information which may shed a light on the problem.
Not sure if this helps.... I added "-v" to ssh.
[ATTACH=CONFIG]251471[/ATTACH]

---

