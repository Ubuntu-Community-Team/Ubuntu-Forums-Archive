---
title: "odd ssh question"
date: 2008-06-10
forum: Security
---

### Post by ASULutzy on 2008-06-10
So I've had an ssh server running on my home machine for a while now and recently I switched it over to not accept passwords and instead only utilize public/private key pairs. I'm pretty happy with it, in order to connect to my desktop from work I just type```
ssh -C my.ip.address.here
``` and it works perfectly.

Now what's bothering me is if I try to use Ubuntu's built in "Connect to server" feature (basically if I try to use nautilus instead of the command line), I can't seem to get it to work.

If I click places->Connect to Server... and select ssh from the dropdown and enter my ip address where it says server and click connect it says "Can't display location "sftp://my.ip.address/"   Permission Denined."

Likewise if I try to just type sftp://my.ip.address in nautilus it doesn't work either. And says Access was Denied...

I was chatting in #ubuntu and another user said his worked fine... I can't figure out why his nautilus integration works and mine doesn't! helps me! :P

edit: I'm hoping my placement of the thread in the security discussion was smart. I figured everyone who hangs out here has to be a total master of all that is ssh right? :lol:

edit2: Here's the contents of my /etc/ssh/sshd_config file```
ryan@ryan-desktop:~$ cat /etc/ssh/sshd_config
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

UsePAM no
```

The only things I changed to disallow passwords were UsePAM, PasswordAuthentication, and ChallengeResponseAuthentication, everything else is default.

---

### Post by HalPomeranz on 2008-06-10
Hmmm, works fine for me here as well (both with public-key-based authentication and with regular passwords).

The only thing I can think of is maybe you don't have SFTP enabled on your server at home.  Try this:

```

$ **grep sftp /etc/ssh/sshd_config**
Subsystem sftp /usr/lib/openssh/sftp-server

```

If your output doesn't look like what you see above, then that's your problem.  To enable SFTP on your server, put the "Subsystem ..." line you see above into your /etc/ssh/sshd_config file on your home server and restart the SSH server on that machine.

---

### Post by ASULutzy on 2008-06-10
> **HalPomeranz said:**
> Hmmm, works fine for me here as well (both with public-key-based authentication and with regular passwords).

The only thing I can think of is maybe you don't have SFTP enabled on your server at home.  Try this:

```

$ **grep sftp /etc/ssh/sshd_config**
Subsystem sftp /usr/lib/openssh/sftp-server

```

If your output doesn't look like what you see above, then that's your problem.  To enable SFTP on your server, put the "Subsystem ..." line you see above into your /etc/ssh/sshd_config file on your home server and restart the SSH server on that machine.
Thanks for the help, but that doesn't seem to be it. ```
ryan@lappy:~$ ssh -C my.home.ssh.ip
Last login: Tue Jun 10 14:13:38 2008 from my.work.ip
ryan@ryan-desktop:~$ grep sftp /etc/ssh/sshd_config
Subsystem sftp /usr/lib/openssh/sftp-server
```

edit: And note, it did work back when I allowed password connections to my ssh server.
Let me paste my sshd_config up in the original post, maybe someone will notice a problem with an option there.

---

### Post by HalPomeranz on 2008-06-10
Weird.  Your sshd_config looks fine to me.  Are you seeing anything in /var/log/auth.log on your home machine when you try to connect and fail?

I tried completely disabling password auth on one of my servers and I'm still able to connect fine using "Places -> Connect to server..."  So it's not a bug in the OS as far as I can tell.

---

### Post by ASULutzy on 2008-06-10
Nope, didn't see anything in the auth.log.

Maybe it's the configuration settings of my ssh client? But that doesn't make any sense really... Either way I'll paste that, maybe something is wrong there. ```
ryan@lappy:~$ cat /etc/ssh/ssh_config 

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```

edit: SWEET! fixed it! had to remove the comment from the location of my identity file. No clue why it was commented in the first place or why it worked in command line but not nautilus, but it's up now. Thanks a bunch!

---

