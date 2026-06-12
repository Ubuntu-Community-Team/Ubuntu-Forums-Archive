---
title: "SSH and publickey authentication"
date: 2007-06-18
forum: Server Platforms
---

### Post by thornomad on 2007-06-18
Hi -

I have two users (one was what I chose when I installed Ubuntu, the other I added using "useradd").  I am using openssh-sever.

I want to use public/private key authentication.  For my "default" user, I installed in successfully.  And, when logging in, it works.  However, performing the EXACT SAME STEPS for my other user results in it not working.  It just gives me the password prompt and when I disable password login, I cannot login to user2.

I have tried creating my own .pub key for user2, as well as using the exact same one I used on user1.  Nothing is working.  Is there some group or setting that isn't allowing my user2 to do publickey authentication?  Why can user1 do it and user2 not with the exact same authorized_keys file?

Here is what I am doing on the client:

```
$ ssh-keygen -t rsa -b 2048
$ scp ~/.ssh/id_rsa.pub user1@192.168.0.200:
```

then on the server I am doing:

```
server-$ mkdir -p ~/.ssh
server-$ touch ~/.ssh/authorized_keys
server-$ cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
server-$ rm ~/id_rsa.pub 
```

It's not working.

Ideas?

---

### Post by carcioni on 2007-06-18
If you try to connect using ssh -v <user>@<xyz.com>, is there any more info in the verbose logging?

I expect it is something pretty basic that is not right, but I don't see it in the commands you are using, as they initially seem ok.

Cheers
D

---

### Post by turinglabs on 2007-06-18
Check the permissions on your authorized_keys file, it should be 0600 (I'm not sure why user1 would work with the same steps, perhaps the user's umask setting is different?). The '-v' is a good idea, you can get even more info with '-vv' or even '-vvv'. Also don't forget the private half of the key has to be indentical if you are trying to duplicate keys.

---

### Post by thornomad on 2007-06-18
> Check the permissions on your authorized_keys file, it should be 0600 (I'm not sure why user1 would work with the same steps, perhaps the user's umask setting is different?). The '-v' is a good idea, you can get even more info with '-vv' or even '-vvv'. Also don't forget the private half of the key has to be indentical if you are trying to duplicate keys.

Genius!  I am not there now, but I am certain this is it.  Just this morning I had changed my umask setting to allow for shared files in a group folder (changing it to 002) ... after I did this, I tried to setup user2... so it would make sense that it is not working ... I will check with the -v, -vv, or -vvv as well.  I didn't even think of that!

You guys are excellent!  Thank you!

---

### Post by thornomad on 2007-06-18
So I was really excited about thinking the read/write access would fix my problem -- however, it didn't: turns out both authorized_keys files (user1 & user2) have the save permissions.  So I got out a fresh macbook (which has never done anything with ssh and started again).  I followed the same steps for user1 and user2 (as I outlined in my first post).  Again, user1 worked and user2 didn't.  I find it very strange.

I ran them with the -vvv option and this is the difference; I don't understand what it means, but ... maybe someone else does.  There is a difference, obviously.  I have highlighted the different strings at the end of user2's output.  I will stress again, the only difference I know of between the two accounts is that one was created as a default account and the other was a useradd addition.  

user1 (am including a bit but cutting some):

```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/user1/.ssh/identity
debug3: no such identity: /Users/user1/.ssh/identity
debug1: Offering public key: /Users/user1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
[B][COLOR="Navy"]debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp 93:79:3a:df:2e:c4:ea:d2:d5:ea:4c:e0:79:d4:f5:dc
debug3: sign_and_send_pubkey
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/Users/user1/.ssh/id_rsa':[/COLOR][/B]
```

user2:

```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/user2/.ssh/identity
debug3: no such identity: /Users/user2/.ssh/identity
debug1: Offering public key: /Users/user2/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
[B][COLOR="DarkRed"]debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/user2/.ssh/id_dsa
debug3: no such identity: /Users/user2/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
user2@192.168.0.200 's password:[/COLOR][/B] 
```

Also I will include my /etc/ssh/sshd_config file for your review:

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
#PasswordAuthentication no

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server
#Subsystem sftp /usr/lib/openssh/libtrash-sftp-server

UsePAM yes
```

Any more ideas ?  Thanks.

---

### Post by thornomad on 2007-06-18
> **thornomad said:**
> Genius!  I am not there now, but I am certain this is it.  Just this morning I had changed my umask setting to allow for shared files in a group folder (changing it to 002) ... after I did this, I tried to setup user2... so it would make sense that it is not working ... I will check with the -v, -vv, or -vvv as well.  I didn't even think of that!

You guys are excellent!  Thank you!

It actually was permissions on the DIRECTORY ~/.ssh that was important; not the file.  I figured that out by looking at the /var/log/auth.log file.

Thanks again.

---

### Post by stedla on 2008-06-18
> **thornomad said:**
> It actually was permissions on the DIRECTORY ~/.ssh that was important; not the file.  I figured that out by looking at the /var/log/auth.log file.

Thanks again.


Make sure that the user is not locked on the other destination server. you can check this in /etc/shadow file

---

