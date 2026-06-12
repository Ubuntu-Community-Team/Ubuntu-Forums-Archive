---
title: "ssh_exchange_identification: read: Connection reset by peer"
date: 2014-04-23
forum: Server Platforms
---

### Post by bewareofthephog on 2014-04-23
I'm trying to setup Hadoop on my machine.  Everything has gone fine until I tried to start it.  It appears I have something going wrong with my ssh keys.

I created a new group called hadoop and a new user called hadoop.  I've chown'd my hadoop install to this user and group.

I then issued the following commands for this user.

```
[COLOR=#111111][FONT=monospace]ssh-keygen -t rsa -P ''
[/FONT][/COLOR][COLOR=#111111][FONT=monospace]cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys[/FONT][/COLOR]
```

Then I isse this command (from putty)

```

$ start-dfs.sh
14/04/23 21:21:45 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Starting namenodes on [localhost]
localhost: ssh_exchange_identification: read: Connection reset by peer
localhost: ssh_exchange_identification: read: Connection reset by peer
Starting secondary namenodes [0.0.0.0]
0.0.0.0: ssh_exchange_identification: read: Connection reset by peer
14/04/23 21:22:08 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable

```

At this point you should know I have a user setup with private/pub keys that I can login to from putty with NO problems at all.

So, after the problems above I tried this

```

ssh -v hduser@localhost
OpenSSH_6.2p2 Ubuntu-6ubuntu0.3, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/hadoop/.ssh/id_rsa type -1
debug1: identity file /home/hadoop/.ssh/id_rsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_dsa type -1
debug1: identity file /home/hadoop/.ssh/id_dsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.3
ssh_exchange_identification: read: Connection reset by peer

```

Then I chmod'd .ssh and all files inside of it to 777 just to see if that would make a difference even though the stack above doesn't hint at it, and surprise, no change.

I'm literally at a loss for ideas here.

Any help would be appreciated.

Oh yeah:
All this is done from putty with that account I mentioned above, when I need to use user "hadoop" I issue "sudo login hadoop" from the terminal.

---

### Post by bewareofthephog on 2014-04-23
Edit:
If I put the actual IP of the server into ssh hadoop@192.168.1.104

I get:

```

OpenSSH_6.2p2 Ubuntu-6ubuntu0.3, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.104 [192.168.1.104] port 22.
debug1: Connection established.
debug1: identity file /home/hadoop/.ssh/id_rsa type -1
debug1: identity file /home/hadoop/.ssh/id_rsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_dsa type -1
debug1: identity file /home/hadoop/.ssh/id_dsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.2p2 Ubuntu-6ubuntu0.3
debug1: match: OpenSSH_6.2p2 Ubuntu-6ubuntu0.3 pat OpenSSH*
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.104" from file "/home/hadoop/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/hadoop/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5-etm@openssh.com
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug2: mac_setup: found hmac-md5-etm@openssh.com
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA xx:xx:xx.....
debug3: load_hostkeys: loading entries for host "192.168.1.104" from file "/home/hadoop/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/hadoop/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.1.104' is known and matches the ECDSA host key.
debug1: Found key in /home/hadoop/.ssh/known_hosts:3
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/hadoop/.ssh/id_rsa ((nil)),
debug2: key: /home/hadoop/.ssh/id_dsa ((nil)),
debug2: key: /home/hadoop/.ssh/id_ecdsa ((nil)),
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/hadoop/.ssh/id_rsa
debug3: no such identity: /home/hadoop/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/hadoop/.ssh/id_dsa
debug3: no such identity: /home/hadoop/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/hadoop/.ssh/id_ecdsa
debug3: no such identity: /home/hadoop/.ssh/id_ecdsa: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Listing:
```

~/.ssh $ ls -al
total 24
drwxrwxrwx 2 hadoop hadoop 4096 Apr 23 21:34 .
drwxr-xr-x 6 hadoop hadoop 4096 Apr 23 21:33 ..
-rwxrwxrwx 1 hadoop hadoop  796 Apr 23 21:34 authorized_keys
-rwxrwxrwx 1 hadoop hadoop 1679 Apr 23 21:27 id_rsa
-rwxrwxrwx 1 hadoop hadoop  398 Apr 23 21:34 id_rsa.pub
-rwxrwxrwx 1 hadoop hadoop  222 Apr 23 21:28 known_hosts

```

---

### Post by papibe on 2014-04-23
Hi bewareofthephog.

ssh won't work properly unless the directory ~/.ssh and its contents have specific permissions.

Adjust your permissions:
```
chmod 600 ~/.ssh/*

chmod 700 ~/.ssh
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by bewareofthephog on 2014-04-23
Thanks papibe!  I've just done that but am still getting this

ssh_exchange_identification: read: Connection reset by peer

---

### Post by papibe on 2014-04-23
Sorry to hear that.

By any chance do you have an encrypted home partition?

Regards.

---

### Post by bewareofthephog on 2014-04-23
I don't remember setting that up honestly but ls -A /home shows .encryptfs so I guess so :)

---

### Post by papibe on 2014-04-23
If that's the case you can't read the .ssh directory before connecting (because it hasn't been decrypted yet).

Move it to something like /etc/ssh/yourusername and modify your /etc/ssh/sshd_config so that the the field 'AuthorizedKeysFile' points to the new location.

Let us know if you need more directions to do that.
Regards.

---

### Post by bewareofthephog on 2014-04-24
Thanks for the fast help!  Unfortunately after moving the keys to /etc/ssh/username, and setting the permissions to 700 and 600, then restarting ssh I'm still getting the same thing

 ```

$ start-dfs.sh
14/04/24 16:14:52 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Starting namenodes on [localhost]
localhost: ssh_exchange_identification: read: Connection reset by peer
localhost: ssh_exchange_identification: read: Connection reset by peer
Starting secondary namenodes [0.0.0.0]
0.0.0.0: ssh_exchange_identification: read: Connection reset by peer
14/04/24 16:15:15 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable

```

and

```

OpenSSH_6.2p2 Ubuntu-6ubuntu0.3, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/hadoop/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/hadoop/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/hadoop/.ssh/id_rsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_dsa type -1
debug1: identity file /home/hadoop/.ssh/id_dsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.3
ssh_exchange_identification: read: Connection reset by peer

```

---

### Post by bewareofthephog on 2014-04-24
I may have found the root of the problem, I had installed some software this week to help harden the security.  Anyway.... ssh hostname.local keeps getting added to /etc/hosts.deny even when I comment it out, I need to figure out what's going on there.

---

### Post by papibe on 2014-04-24
It looks like ssh is still looking for the files on the home directory:
```
...
debug3: Could not load "/home/hadoop/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/hadoop/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/hadoop/.ssh/id_rsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_dsa type -1
debug1: identity file /home/hadoop/.ssh/id_dsa-cert type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa type -1
debug1: identity file /home/hadoop/.ssh/id_ecdsa-cert type -1

```
Make sure your /etc/ssh/sshd_config has change the default from:
```
#AuthorizedKeysFile	%h/.ssh/authorized_keys
```
to
```
AuthorizedKeysFile	/etc/ssh/%u/authorized_keys
```
and the file is there:
```
ls /etc/ssh/youruser/authorized_keys
```
(replace ''youruser' for your actual user).

The permissions in this case are different:
```
chown -R youruser:youruser /etc/ssh/youruser

chmod 755 /etc/ssh/youruser

chmod 644 /etc/ssh/youruser/authorized_keys
```
Let us know if that makes a difference.
Regards.

---

### Post by bewareofthephog on 2014-04-24
I haven't tried what you've said above.  But after some digging, on the local machine I've found this

$ ssh localhost
$ ssh hadoop@localhost
$ ssh 127.0.0.1
$ ssh hadoop@127.0.0.1

All don't work

But, if I give the IP

$ ssh hadoop@192.168.1.100

Then it works.  I think I'll need to edit my hadoop scripts, but I don't know if "localhost" is hard coded anywhere or not.

---

### Post by bewareofthephog on 2014-04-24
Solved, I some how locked out localhost with denyhosts, had to get that sorted out, all is good.  Thanks for all of your help!

---

