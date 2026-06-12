---
title: "ssh: issue when user's home directory  user is not in /home"
date: 2007-11-28
forum: Server Platforms
---

### Post by jmvidalvia on 2007-11-28
Hi everybody!
I am having following issue: when the user's home directory is not in /home, but in any other directory in the root, say /copies/user, then I can not avoit the password prompt when connecting with ssh.
I already generated the keys, uploaded to /copies/user/.ssh/authorized_keys, checked permnissions, etc. (I did it many times before). But there's no way to avoid typing the password.
Any clues?
Thanks a lot in advanced!

jm

---

### Post by netlogic on 2007-11-28
have you tried to edit your passwd file?
user1: x:1001:1001:,,,:/copies/user1:/bin/bash

---

### Post by jmvidalvia on 2007-11-28
Yes, yes. I already did it.
In fact, when I connect after typing the password I am located in the right directory (/copies/user).
The only problem seems to be avoiding the password prompt.
Thanks!

---

### Post by netlogic on 2007-11-28
post your  sshd_config file.
also, how did you add the public key to the authorized_keys? does user owns the folder and permission? the usually situation like this, it is a permission issue.
it should be looking for .ssh folder at the user's home directory and the user needs the full rights to the folder and files inside.

can you take a look at this?
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by jmvidalvia on 2007-11-28
Thanks again.
Permmisions:
```
server:/pcs/andrea.fernandez/.ssh# ls -la
total 20
drwx------  2 andrea.fernandez resa 4096 2007-11-28 18:58 .
drwxrwxr-x 10 andrea.fernandez root 4096 2007-11-28 18:58 ..
-rw-r--r--  1 andrea.fernandez resa  783 2007-11-28 18:51 authorized_keys
-rw-------  1 andrea.fernandez resa 1675 2007-11-28 18:52 id_rsa
-rw-r--r--  1 andrea.fernandez resa  405 2007-11-28 18:52 id_rsa.pub
server:/pcs/andrea.fernandez/.ssh# 
```

My sshd_config:
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
#PermitRootLogin yes 
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

```

How I did it?
I created the client keys in a different computer by:
```
$ssh-keygen -t rsa
```
I went to user's .ssh/ and edit+copy the content of /.ssh/id_rsa.pub file in server:/pcs/andrea.fernandez/.ssh/authorized_keys

Note: I have other users connecting with their /home directories with ssh with no troubles.

Thank you very much for your help!

---

### Post by craigp84 on 2007-11-28
I'm taking a wild guess, but maybe there's some kind of sanity check by default in sshd that prevents it looking anywhere other than a subdir of /home.

Try uncommenting this line in your sshd_config which would blast my theory out of the water -

```
AuthorizedKeysFile     %h/.ssh/authorized_keys
```

Secondly, try starting sshd with the -vvv option -

```

sudo kill `cat /var/run/sshd.pid`
sudo sshd -vvv

```

Also try turning on versbose output in the client -

```

ssh -vvv -l user hostname

```

hth,

-c

---

### Post by jmvidalvia on 2007-11-28
> **craigp84 said:**
> I'm taking a wild guess, but maybe there's some kind of sanity check by default in sshd that prevents it looking anywhere other than a subdir of /home.

Try uncommenting this line in your sshd_config which would blast my theory out of the water -

```
AuthorizedKeysFile     %h/.ssh/authorized_keys
```

**Done, no success,**

Secondly, try starting sshd with the -vvv option -

```

sudo kill `cat /var/run/sshd.pid`
sudo sshd -vvv

```

**Can I run this while using ssh?: I am now connecting from out of my office. I am afraid after first command I won't be able to connect again.**

Also try turning on versbose output in the client -

```

ssh -vvv -l user hostname

```

**Please, find below verbose output: it is very interesting!**

hth,

-c
**¿was  "hth,  -c" meaning something?**


verbose output:
```
jm@mypc:~$ ssh -vvv andrea.fernandez@serverip.com
OpenSSH_4.6p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to serverip.com [xx.xx.xx.xx] port 22.
debug1: Connection established.
debug1: identity file /home/jm/.ssh/identity type -1
debug3: Not a RSA1 key file /home/jm/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/jm/.ssh/id_rsa type 1
debug1: identity file /home/jm/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 120/256
debug2: bits set: 477/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/jm/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 4
debug3: check_host_in_hostfile: filename /home/jm/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'serverip.com' is known and matches the RSA host key.
debug1: Found key in /home/jm/.ssh/known_hosts:4
debug2: bits set: 522/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/jm/.ssh/identity ((nil))
debug2: key: /home/jm/.ssh/id_rsa (0x5555557b8220)
debug2: key: /home/jm/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jm/.ssh/identity
debug3: no such identity: /home/jm/.ssh/identity
debug1: Offering public key: /home/jm/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jm/.ssh/id_dsa
debug3: no such identity: /home/jm/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
andrea.fernandez@serverip.com's password: 

```

Thanks a lot!

PS: I modified every sensitive information here: hope not to forget anything...

---

### Post by jmvidalvia on 2007-11-28
I compared the debug with the one I amb getting with a different user that is able to connect:

This works:
```
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277

```

This doesn't work:
```
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jm/.ssh/id_dsa
debug3: no such identity: /home/jm/.ssh/id_dsa
debug2: we did not send a packet, disable method
```

:(
Thanks!

---

### Post by craigp84 on 2007-11-28
> Can I run this while using ssh?: I am now connecting from out of my office. I am afraid after first command I won't be able to connect again.

You're right to be afraid! Don't do this in this case :-) (you could nohup it in a subshell, but there's things can go wrong there).

> was "hth, -c" meaning something?

```
hth = Hope that helps
-c = Craig (my name!)
```

> 
ssh -vvv [email]andrea.fernandez@serverip.com[/email]
...
debug1: identity file /home/jm/.ssh/identity 

Now that's interesting! Can you run a -

```
getent passwd andrea.fernandez
```

Till we see what's going on there.

Also try -

```
ssh -vvv -l andrea.fernandez serverip.whatver
```



-c

---

### Post by jmvidalvia on 2007-11-28
> **craigp84 said:**
> You're right to be afraid! Don't do this in this case :-) (you could nohup it in a subshell, but there's things can go wrong there).



```
hth = Hope that helps
-c = Craig (my name!)
```
:)


Now that's interesting! Can you run a -

```
getent passwd andrea.fernandez
```
```
[B]andrea.fernandez@server:~$ getent passwd andrea.fernandez
andrea.fernandez:x:1001:1001::/pcs/andrea.fernandez:/bin/bash
andrea.fernandez@server:~$[/B] 

```

Till we see what's going on there.

Also try -

```
ssh -vvv -l andrea.fernandez serverip.whatver
```

**Here it goes:**

-c

```
jm@server:~$ ssh -vvv -l andrea.fernandez serverip.com
OpenSSH_4.6p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connection established.
debug1: identity file /home/jm/.ssh/identity type -1
debug3: Not a RSA1 key file /home/jm/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/jm/.ssh/id_rsa type 1
debug1: identity file /home/jm/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 522/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/jm/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 4
debug3: check_host_in_hostfile: filename /home/jm/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'serverip.com' is known and matches the RSA host key.
debug1: Found key in /home/jm/.ssh/known_hosts:4
debug2: bits set: 520/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/jm/.ssh/identity ((nil))
debug2: key: /home/jm/.ssh/id_rsa (0x5555557b81f0)
debug2: key: /home/jm/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jm/.ssh/identity
debug3: no such identity: /home/jm/.ssh/identity
debug1: Offering public key: /home/jm/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jm/.ssh/id_dsa
debug3: no such identity: /home/jm/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
andrea.fernandez@serverip,com's password: 

```

PS: the output looks very similar to the firs I already posted...

Thanks!

---

### Post by netlogic on 2007-11-28
From what I know, it shouldn't matter where the home directory is located. Long as the user's home folder contains your **.ssh** folder.
Your configuration looks fine to me.
Are you sure, your passwd file indicates that user's home directory is
**/copies/user**?

if you type, **env |grep -i home**
you get 
**HOME=/copies/user**?
Also, are you sure you are using the right key for that particular user? Did you accidentally got your public keys mixed up?

> /home/jm/.ssh/identity type -1
If your passwd file is pointing that particular user's home directory to /copies/user1, it should look under there, not in /home/xxxx
However, it seems like it is looking for it in that folder.

---

### Post by cherry316316 on 2007-11-29
where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

but its still not working. which IP address I am suppose to use.
also, when I open a website, which gives IP address, it shows my IP address as
127.XXX.XXX.XXX
which is different from 10.XXX.XXX.XXX which i get using “ifconfig”
Thanks

---

### Post by jmvidalvia on 2007-11-29
> **netlogic said:**
> From what I know, it shouldn't matter where the home directory is located. Long as the user's home folder contains your **.ssh** folder.
Your configuration looks fine to me.
Are you sure, your passwd file indicates that user's home directory is
**/copies/user**?
**Yes, totally sure**

if you type, **env |grep -i home**
you get 
**HOME=/copies/user**?

**Yes I do**

Also, are you sure you are using the right key for that particular user? Did you accidentally got your public keys mixed up?
**No, I didn't**

If your passwd file is pointing that particular user's home directory to /copies/user1, it should look under there, not in /home/xxxx
However, it seems like it is looking for it in that folder.

:(

---

### Post by jmvidalvia on 2007-11-29
> **cherry316316 said:**
> where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

but its still not working. which IP address I am suppose to use.
also, when I open a website, which gives IP address, it shows my IP address as
127.XXX.XXX.XXX
which is different from 10.XXX.XXX.XXX which i get using “ifconfig”
Thanks

I am afraid you mixed up your post...

---

### Post by jmvidalvia on 2008-01-24
Some weeks later...I solved it \\:D/
The reason was folder permisions: I gave too many permisions, and openssh needs some kind of restrictions.
I first thought there was a lack of permisions and the problem was the oposite.
Thanks everybody!

---

