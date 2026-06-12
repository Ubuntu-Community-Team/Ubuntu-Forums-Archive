---
title: "Problem with SSH: Custom key name"
date: 2009-03-09
forum: Security
---

### Post by germ65 on 2009-03-09
Hello,
  I hope I am posting in the right forum...

I am trying to setup public key authentication for my Linux box. I have followed the instructions and generated the public/private key pair. But, when prompted for a file name, I chose

~/.ssh/gecko_dsa  

instead of the default

~/.ssh/id_dsa

Why? Because I have more than one computer, and I want to put all my public keys into a folder and I want to give them a name that tells me the host name (gecko is my Linux computer name) WITHOUT having to open the public key file. 

Now, I correctly copy and add the public key to the authorized_keys on my iMac. But when I connect, I still get asked for the password. 

Running the ssh command with the -v option, I can see what's I think is going on. Here's the last few lines:
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/davide/.ssh/identity
debug1: Trying private key: /Users/davide/.ssh/id_rsa
debug1: Trying private key: /Users/davide/.ssh/id_dsa
debug1: Next authentication method: password

So, is the Linux box trying to look for the id_dsa file, but fails because the file is actually gecko_dsa?

That's what I first thought. But then, I generated another key leaving the default file name unchanged. 

Now, I get one step further, but I STILL get asked for a password:

debug1: Next authentication method: publickey
debug1: Trying private key: /Users/davide/.ssh/identity
debug1: Trying private key: /Users/davide/.ssh/id_rsa
debug1: Offering public key: /Users/davide/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password


I would really like to know why....I have spent the past two hours looking at documentation and online, with no success.

---

### Post by ushills on 2009-03-09
You can specify the key name with the -i option

In your case:

```
ssh server -i gecko_dsa -p 80
```

if this fails specify the path

```
ssh server -i ~/.ssh/gecko_dsa -p 80
```

---

### Post by germ65 on 2009-03-09
Now with triple verbose option:


debug2: key: /Users/davide/.ssh/identity (0x0)
debug2: key: /Users/davide/.ssh/id_rsa (0x0)
debug2: key: /Users/davide/.ssh/id_dsa (0x101890)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/davide/.ssh/identity
debug3: no such identity: /Users/davide/.ssh/identity
debug1: Trying private key: /Users/davide/.ssh/id_rsa
debug3: no such identity: /Users/davide/.ssh/id_rsa
debug1: Offering public key: /Users/davide/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
**debug2: we did not send a packet, disable method**
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password


For some reason, this isn't working still...

---

### Post by ushills on 2009-03-09
Can you look at my guide here

[http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html](http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html)

and check you have set permission correctly (it will not work otherwise) and correctly copied public key to the server.

PS the port should be 22 by default, I would suggest you only change it later.

---

### Post by apmcd47 on 2009-03-09
> **germ65 said:**
> Hello,
  I hope I am posting in the right forum...

I am trying to setup public key authentication for my Linux box. I have followed the instructions and generated the public/private key pair. But, when prompted for a file name, I chose

~/.ssh/gecko_dsa  

instead of the default

~/.ssh/id_dsa

Why? Because I have more than one computer, and I want to put all my public keys into a folder and I want to give them a name that tells me the host name (gecko is my Linux computer name) WITHOUT having to open the public key file. 

While this will not fix your problem, I should point out that the pub file, once copied t another computer, can be renamed. Once you copy the contents of the file into the authorized_keys file you don't even need the file! I do suggest that the name of the computer is appended to the end of the key for future reference.

If you insist on using a private key file with a different name you can add it to your ~/.ssh/config file.

Andrew

---

### Post by germ65 on 2009-03-09
> **ushills said:**
> Can you look at my guide here

[http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html](http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html)

and check you have set permission correctly (it will not work otherwise) and correctly copied public key to the server.

PS the port should be 22 by default, I would suggest you only change it later.

Permissions are as follows.

On the Linux box:
~/.ssh                         700
~/.ssh/id_dsa            600
~/.ssh/id_dsa.pub    644

On the iMac:
~/.ssh                         700
~/authorized_keys    640   (I changed this to 600, with the same result)

Never changed the default port from 22. Of course, logging in with password works perfectly. I am just about totally mystified by this one.

---

### Post by germ65 on 2009-03-09
> **apmcd47 said:**
> While this will not fix your problem, I should point out that the pub file, once copied t another computer, can be renamed. Once you copy the contents of the file into the authorized_keys file you don't even need the file! I do suggest that the name of the computer is appended to the end of the key for future reference.

If you insist on using a private key file with a different name you can add it to your ~/.ssh/config file.

Andrew

Thanks for pointing out that only the public key needs to be renamed. In fact, the private key probably will stay forever in its host's .ssh directory.

---

### Post by ushills on 2009-03-10
if you renam the private key to id_dsa does it work then.  If not then it is not the key name giving problems.

The -i option allows you to specify the identity file (private key) to be used the only other thing i can think of is are you using the correct login name again this can be specified with the -l name option.

try renaming the private key first though as this will show where the problem lies.

---

### Post by ushills on 2009-03-10
Also try this:

On the remote computer, ensure that the /etc/ssh/sshd_config contains the following lines, and that they are uncommented; 


```
PubkeyAuthentication yes
RSAAuthentication yes
```

If not, add them, or uncomment them, restart the sshd, and try logging in again. If you get the passphrase prompt now, then congratulations, you're logging in with a key!

---

### Post by germ65 on 2009-03-10
> **ushills said:**
> if you renam the private key to id_dsa does it work then.  If not then it is not the key name giving problems.

The -i option allows you to specify the identity file (private key) to be used the only other thing i can think of is are you using the correct login name again this can be specified with the -l name option.

try renaming the private key first though as this will show where the problem lies.


As you can read in the OP, I also tried leaving the default key name. Still does not work.

---

### Post by germ65 on 2009-03-10
> **ushills said:**
> Also try this:

On the remote computer, ensure that the /etc/ssh/sshd_config contains the following lines, and that they are uncommented; 


```
PubkeyAuthentication yes
RSAAuthentication yes
```

If not, add them, or uncomment them, restart the sshd, and try logging in again. If you get the passphrase prompt now, then congratulations, you're logging in with a key!

Yes, yes. Here's my sshd_config file:

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

---

### Post by bodhi.zazen on 2009-03-10
Comments :

Name of key does not matter. Personally I name each key so I know where it goes ;)

Second, you probably do not want to allow root logins, so change 

> PermitRootLogin yes

to

```
PermitRootLogin no
```

And last you need to allow keys :twisted;

So uncomment this line :

> #AuthorizedKeysFile	%h/.ssh/authorized_keys

to:

```
AuthorizedKeysFile	%h/.ssh/authorized_keys
```

You then need to copy the *.pub to ~/.ssh/authorized_keys (on the server)

---

### Post by germ65 on 2009-03-10
> **bodhi.zazen said:**
> Comments :

Name of key does not matter. Personally I name each key so I know where it goes ;)

Second, you probably do not want to allow root logins, so change 



to

```
PermitRootLogin no
```

And last you need to allow keys :twisted;

So uncomment this line :



to:

```
AuthorizedKeysFile	%h/.ssh/authorized_keys
```

You then need to copy the *.pub to ~/.ssh/authorized_keys (on the server)


OK, I made the changes you suggested to the sshd_config file, then restarted the ssh daemon.

STILL NO SUCCESS......

---

