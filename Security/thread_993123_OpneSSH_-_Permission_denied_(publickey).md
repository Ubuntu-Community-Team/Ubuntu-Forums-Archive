---
title: "OpneSSH - Permission denied (publickey)"
date: 2008-11-25
forum: Security
---

### Post by Berduchwal on 2008-11-25
Hi
I am struggling to get passwordless authentication!

ssh -vvv HOST -i /home/sadmin1/.ssh/id_rsa
> 
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/sadmin1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Offering public key: /home/sadmin1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/sadmin1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Offering public key: /home/sadmin1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1


ls -l -a
> 
drwx------  2 sadmin1 sadmin1     4096 2008-11-25 15:55 .ssh
=======================
-rw-------  1 sadmin1 sadmin1  400 2008-11-25 15:54 authorized_keys
=======================
drwxr-xr-x   5 root root  4096 2008-11-21 14:10 home


nano /etc/ssh/sshd_config
> 
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
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      ~/.ssh/authorized_keys

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
ChallengeResponseAuthentication yes
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

UsePAM yes


I have tried: 
$ chmod go-w ~/
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/authorized_keys
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

I have done:
> ssh-copy-id -i ~/.ssh/id_rsa.pub username@hos

I do not know what else to do.
Any suggestions?

---

### Post by Dr Small on 2008-11-25
Please take a look at this guide:
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

---

### Post by Berduchwal on 2008-11-25
Thank you for your post!

I probably should have said this earlier but I have followed similar guide and done all of those steps.

Sadly it still does not work. That is why I posted -vvv output of ssh command so someone with bit more knowledge can help me :)

Websites I used are:
[http://codept.blogspot.com/2006/11/permission-denied-publickey.html]("http://codept.blogspot.com/2006/11/permission-denied-publickey.html")

[http://www.debianadmin.com/ssh-your-debian-servers-without-password.html]("http://www.debianadmin.com/ssh-your-debian-servers-without-password.html")

as well as Ubuntu advanced guide mentioned earlier.

---

### Post by keithweddell on 2008-11-25
From the output of ls -l-a, it looks as if you do not have a file /home/sadmin1/.ssh/id_rsa.  Have you created your pubkey pair?  Or am I looking at server instead of client?  

You may also want to try ssh USER@HOST

Keith

---

### Post by Berduchwal on 2008-11-25
Thank you for your post!

I have created pair, added public to the authorized_keys and placed the other in .ssh folder.

I also tried the ssh login@host

in ls output I only cut the relevant parts so this is not full listing.

---

### Post by keithweddell on 2008-11-25
Sorry.  Don't think I can suggest anything else useful.

Keith

---

### Post by bodhi.zazen on 2008-11-25
You have 2 files, id_rsa and id_rsa.pub

put id_rsa.pub on the server

cat id_rsa.pub > authorized_keys

Now take the id_rsa to the client

ssh user@server -i ~/.ssh/id_rsa

You *may* need to change 

> PermitEmptyPasswords no

to yes

---

### Post by kevdog on 2008-11-25
What happens if on the server you just do ssh localhost?

---

### Post by Rayve on 2009-11-09
> **bodhi.zazen said:**
> You have 2 files, id_rsa and id_rsa.pub

put id_rsa.pub on the server

cat id_rsa.pub > authorized_keys

Now take the id_rsa to the client

ssh user@server -i ~/.ssh/id_rsa

You *may* need to change 



to yes

I know this is an old thread, but I just wanted to say thanks!  It helped me finally be able to ssh into my desktop from my netbook.  :)

---

### Post by noway2 on 2009-11-09
I also ran into this problem once.  The cause (and resolution) was the permissions.  The key file was located in the .ssh folder under my user profile (not root) and the permissions did not give the non-root user account the ability to read the file.  Apparently this caused it to always issue the permission denied.

---

### Post by bodhi.zazen on 2009-11-09
> **noway2 said:**
> I also ran into this problem once.  The cause (and resolution) was the permissions.  The key file was located in the .ssh folder under my user profile (not root) and the permissions did not give the non-root user account the ability to read the file.  Apparently this caused it to always issue the permission denied.

Yes, the permissions of the key in ~/.ssh are critical.

I use 400

---

### Post by oldtiredandconfused on 2013-01-07
After much poking around solved the problem. 
My machine has two users me and scidb. If logged in as me I could ssh me@localhost just fine, but if I tried ssh scidb@localhost failed. If I logged in as scidb then it works as ssh scidb@localhost.

---

