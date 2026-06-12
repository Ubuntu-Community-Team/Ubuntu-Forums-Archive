---
title: "SSH error: Could not load host key."
date: 2012-10-15
forum: Server Platforms
---

### Post by eng30312 on 2012-10-15
I am trying to break free of MS server and become proficient with Linux, and I've been doing pretty well so far, but this error has me stumped.  I have searched high and low for a fix to this error, and while I have found many fixes, they simply aren't working for me.  I keep running up against the same problem.  OpenSSH reports "Could not load host key".  WHY?

I am running 10.04 LTS and installed OpenSSH.
Here is my sshd_config file ```
 cat /etc/ssh/sshd_config

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 1031
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/dino_pub
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel DEBUG3

# Authentication:
LoginGraceTime 120
PermitRootLogin no
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

Here is the auth.log file ```
 cat /var/log/auth.log | grep sshd

Oct 15 16:38:17 dino sshd[2310]: debug3: fd 4 is not O_NONBLOCK
Oct 15 16:38:17 dino sshd[2310]: debug1: Forked child 2394.
Oct 15 16:38:17 dino sshd[2310]: debug3: send_rexec_state: entering fd = 7 config len 654
Oct 15 16:38:17 dino sshd[2310]: debug3: ssh_msg_send: type 0
Oct 15 16:38:17 dino sshd[2310]: debug3: send_rexec_state: done
Oct 15 16:38:17 dino sshd[2394]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Oct 15 16:38:17 dino sshd[2394]: error: Could not load host key: /etc/ssh/dino_pub
Oct 15 16:38:17 dino sshd[2394]: debug1: inetd sockets after dupping: 3, 3
Oct 15 16:38:17 dino sshd[2394]: Connection from 127.0.0.1 port 46272
Oct 15 16:38:17 dino sshd[2394]: debug1: Client protocol version 2.0; client software version OpenSSH_5.3p1 Debian-3ubuntu7
Oct 15 16:38:17 dino sshd[2394]: debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
Oct 15 16:38:17 dino sshd[2394]: debug1: Enabling compatibility mode for protocol 2.0
Oct 15 16:38:17 dino sshd[2394]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
Oct 15 16:38:17 dino sshd[2394]: debug2: fd 3 setting O_NONBLOCK
Oct 15 16:38:17 dino sshd[2394]: debug2: Network child is on pid 2395
Oct 15 16:38:17 dino sshd[2394]: debug3: preauth child monitor started
Oct 15 16:38:17 dino sshd[2394]: debug3: mm_request_receive entering
Oct 15 16:38:17 dino sshd[2394]: debug1: do_cleanup
Oct 15 16:38:17 dino sshd[2394]: debug3: PAM: sshpam_thread_cleanup entering 
```

Here are the premissions for the relevent directories ```
 ls -l /etc/ssh
-rw------- 1 root root    393 2012-10-15 16:15 dino_pub

ls -l ~/.ssh
-rw------- 1 daniel daniel 1675 2012-10-15 16:17 dino_private
-rw------- 1 daniel daniel  274 2012-10-15 09:50 known_hosts 
```

Any help is greatly appreciated.

---

### Post by drmrgd on 2012-10-15
I might be missing something here as I'm a bit new at this myself.  But, since I just set up a new SSH instance yesterday and it's fresh in my head, I'll give it a go.  

First, this is the best resource for how to set this up that I've found so far (or at least what guided me the last couple times I did it);

[http://wiki.centos.org/HowTos/Network/SecuringSSH](http://wiki.centos.org/HowTos/Network/SecuringSSH)

I think what you're missing is to comment out the AuthorizedKeysFile line in your configuration.  Then, you need to run ssh-keygen -t rsa on your client computer, copy the one that ends in .pub to the server and add that to a file called ~/.ssh/authorized_keys.  It does not look like that file exists yet on your server (which is normal if this is the first key to be added).  So, you can just create the file and copy in the .pub key from the client.  Or more simply (assuming your public key is called dino.pub):

```
cat dino.pub >> authorized_keys
```

Once you've added the text from dino.pub into authorized keys, you can delete it as you don't really need it.

Then just restart your SSH daemon and you should be good to go.

Hope that helps!

---

### Post by Cheesemill on 2012-10-15
You can also get more information by using the verbose switch with ssh:
```
ssh -v user@host
```

If that doesn't give you enough information you can use more v's:
```
ssh -vvv user@host
```

---

### Post by eng30312 on 2012-10-16
Thanks, but this is one of the many things I already tried and it didn't work.

> **drmrgd said:**
> I might be missing something here as I'm a bit new at this myself.  But, since I just set up a new SSH instance yesterday and it's fresh in my head, I'll give it a go.  

First, this is the best resource for how to set this up that I've found so far (or at least what guided me the last couple times I did it);

[http://wiki.centos.org/HowTos/Network/SecuringSSH](http://wiki.centos.org/HowTos/Network/SecuringSSH)

I think what you're missing is to comment out the AuthorizedKeysFile line in your configuration.  Then, you need to run ssh-keygen -t rsa on your client computer, copy the one that ends in .pub to the server and add that to a file called ~/.ssh/authorized_keys.  It does not look like that file exists yet on your server (which is normal if this is the first key to be added).  So, you can just create the file and copy in the .pub key from the client.  Or more simply (assuming your public key is called dino.pub):

```
cat dino.pub >> authorized_keys
```

Once you've added the text from dino.pub into authorized keys, you can delete it as you don't really need it.

Then just restart your SSH daemon and you should be good to go.

Hope that helps!

---

### Post by Alekz_ on 2012-10-16
Did you try to generate new keys e restart ssh server?

It probably will solve you issue..

EDIT
Another thing..

Why is this line commented out
> #AuthorizedKeysFile	%h/.ssh/authorized_keys

---

### Post by eng30312 on 2012-10-16
Yep, probably about a dozen times.  This is why I'm so stumped.

[UOTE=Alekz_;12299296]Did you try to generate new keys e restart ssh server?

It probably will solve you issue..[/QUOTE]

---

### Post by steeldriver on 2012-10-16
I'm not an SSH expert but it seems to me you are maybe mixing up the HostKey mechanism and the PublicKey mechanism?

You appear to have an earlier version than me, but afaik the HostKey in /etc/ssh needs to point to the **host's private key**, and the corresponding public key portion is what gets written to the client's known_hosts file the first time you make a connection to a 'new' host. These should be generated one time when the package is installed/configured. For example my /etc/ssh looks like

```
$ ls -l /etc/ssh
total 160
-rw-r--r-- 1 root root 125749 Apr  2  2012 moduli
-rw-r--r-- 1 root root   1669 Apr  2  2012 ssh_config
-rw-r--r-- 1 root root   2489 Oct  6 13:02 sshd_config
-rw------- 1 root root    668 Oct  6 13:02 ssh_host_dsa_key
-rw-r--r-- 1 root root    599 Oct  6 13:02 ssh_host_dsa_key.pub
-rw------- 1 root root    227 Oct  6 13:02 ssh_host_ecdsa_key
-rw-r--r-- 1 root root    171 Oct  6 13:02 ssh_host_ecdsa_key.pub
[COLOR=Red]-rw------- 1 root root   1675 Oct  6 13:02 ssh_host_rsa_key
-rw-r--r-- 1 root root    391 Oct  6 13:02 ssh_host_rsa_key.pub[/COLOR]
-rw-r--r-- 1 root root    302 Jan 10  2011 ssh_import_id
```The key pair that you generate as a user is for public key authentication from the client (i.e. private key belongs to client and public key goes on the remote host in the user's ~/.ssh/authorized_keys)

---

### Post by Alekz_ on 2012-10-16
Well.. All points to wrong key.. 

I'd try "again":

> ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_rsa_key

Of course.. You changed the key file name.. So, change command either!

And you won't use DSA? Only RSA? I saw that your sshd_config doen't have a HostKey for DSA..

---

