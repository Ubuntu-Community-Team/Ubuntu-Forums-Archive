---
title: "SSH: Permission denied (publickey)"
date: 2014-01-26
forum: Security
---

### Post by WilliamMiller54 on 2014-01-26
Thank you for your help in advance. I have been working on this for weeks, and pretty frustrated. This is my current status, but have done a lot of research, and tried a lot of tweaks. 

Issue: Permission denied (publickey) , 
[LIST]
[*]Client Ubuntu 13.10 | Server Ubuntu 12.04
[*]Used following for reference: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[*]Was working with old keys, but did a client reload and hasn't worked since. Could not connect using old keys
[*]Generated new keys and manually added them to the authorized_keys on the server, connected once, but on Client reboot could not connect again with new keys. 
[*]Last kicker was that a reboot removed the authorized_keys file on the client. I recreated it, and added the private key
[/LIST]

.ssh
```

-rw------- 1 xxxUName xxxUName 1766 Jan 25 16:36 authorized_keys
-rw-r--r-- 1 xxxUName xxxUName  619 Jan 24 16:37 known_hosts
-rw------- 1 xxxUName xxxUName 1766 Jan 24 15:42 ServerName_id3
-rw-r--r-- 1 xxxUName xxxUName  399 Jan 24 15:42 ServerName_id3.pub

```

Current Issue:
```

xxxUName@clientName:~/.ssh$ ssh -vvv xxxUName@192.xx.xx.xx
OpenSSH_6.2p2 Ubuntu-6ubuntu0.1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.xx.xx.xx [192.xx.xx.xx] port 22.
debug1: Connection established.
debug1: identity file /home/xxxUName/.ssh/id_rsa type -1
debug1: identity file /home/xxxUName/.ssh/id_rsa-cert type -1
debug1: identity file /home/xxxUName/.ssh/id_dsa type -1
debug1: identity file /home/xxxUName/.ssh/id_dsa-cert type -1
debug1: identity file /home/xxxUName/.ssh/id_ecdsa type -1
debug1: identity file /home/xxxUName/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.1 pat OpenSSH_5*
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.xx.xx.xx" from file "/home/xxxUName/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/xxxUName/.ssh/known_hosts:1
debug3: load_hostkeys: found key type RSA in file /home/xxxUName/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 2 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss
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
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA ea:bf:60:43:09:b4:49:a5:a3:fd:b3:f4:06:eb:67:f4
debug3: load_hostkeys: loading entries for host "192.xx.xx.xx" from file "/home/xxxUName/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/xxxUName/.ssh/known_hosts:1
debug3: load_hostkeys: found key type RSA in file /home/xxxUName/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 2 keys
debug1: Host '192.xx.xx.xx' is known and matches the ECDSA host key.
debug1: Found key in /home/xxxUName/.ssh/known_hosts:1
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
debug2: key: ServerName_id3 (0x7f9027eb72f0),
debug2: key: xxxUName@clientName (0x7f9027eb7440),
debug2: key: /home/xxxUName/.ssh/id_rsa ((nil)),
debug2: key: /home/xxxUName/.ssh/id_dsa ((nil)),
debug2: key: /home/xxxUName/.ssh/id_ecdsa ((nil)),
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: ServerName_id3
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: xxxUName@clientName
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/xxxUName/.ssh/id_rsa
debug3: no such identity: /home/xxxUName/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/xxxUName/.ssh/id_dsa
debug3: no such identity: /home/xxxUName/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/xxxUName/.ssh/id_ecdsa
debug3: no such identity: /home/xxxUName/.ssh/id_ecdsa: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by ubudog on 2014-01-26
> debug3: no such identity: /home/xxxUName/.ssh/id_rsa: No such file or directory

Make sure that you have your private key in .ssh.

---

### Post by WilliamMiller54 on 2014-01-26
> **ubudog said:**
> Make sure that you have your private key in .ssh.

Thanks ubudog, 

I have both my Pub and Private key in the ~/.ssh directory as shown below. My authorized_keys file is a duplicate of my Private key "ServerName_id3"

```

-rw------- 1 xxxUName xxxUName 1766 Jan 25 16:36 authorized_keys
-rw-r--r-- 1 xxxUName xxxUName  619 Jan 24 16:37 known_hosts
-rw------- 1 xxxUName xxxUName 1766 Jan 24 15:42 ServerName_id3
-rw-r--r-- 1 xxxUName xxxUName  399 Jan 24 15:42 ServerName_id3.pub

```

---

### Post by CharlesA on 2014-01-26
You should be putting the public key into authorized_keys, not the private key.

If you have a server with the correct keys, you can use ssh-copy-id to add the proper keys to authorized_keys automagically.

---

### Post by 1clue on 2014-01-26
I also don't think ssh keys are portable.  When you reloaded your system the system generated new server keys.  I can't say for sure though, and don't feel like looking it up.  I'm lazy today.  :)

Anyway, make sure your $HOME is chmod 700, and are you using a DSA key or an RSA key?  DSA goes to authorized_keys2.  I use DSA.

You need to delete your whole .ssh directory and start over.  The private key needs to never leave the system it was generated on or it is considered compromised.  The public key crosses the net, the private one is protected.

This isn't strictly required but IMO your .ssh directory should be chmod 700 too.  Nobody else has any business poking around in there.

---

### Post by 1clue on 2014-01-26
So here's what I'd do:
```

rm -rf .ssh
ssh-keygen -t dsa
scp .ssh/id_dsa.pub you@<remote-host-name-or-ip>:
ssh you@<remote-host-name-or-ip>
mkdir .ssh
mv id_dsa.pub .ssh/authorized_keys2
# You also want to delete your existing key for this host
exit
#now from your local machine again:
ssh you@<remote-host-name-or-ip>
# and you should be in without a password if you have a stock setup there.

```

---

### Post by CharlesA on 2014-01-26
> **1clue said:**
> I also don't think ssh keys are portable.  When you reloaded your system the system generated new server keys.  I can't say for sure though, and don't feel like looking it up.  I'm lazy today.  :) 

They are portable, but you need to be using the correct key. :)

---

### Post by 1clue on 2014-01-26
OK cool, I've never tried to move one because I thought they were somehow tied to the host key.  :)

---

### Post by cariboo on 2014-01-27
Running a development version, I do re-installs fairly often, I do weekly backups of my home directory, when I do a new installation, I just restore the relevant directories back to /home/cariboo, in my case.

---

### Post by WilliamMiller54 on 2014-01-27
> **CharlesA said:**
> You should be putting the public key into authorized_keys, not the private key.

If you have a server with the correct keys, you can use ssh-copy-id to add the proper keys to authorized_keys automagically.

Thank you CharlesA, 

I replaced the Authorized_key with the Public key but still have the issue 

```

xxxUName@clientName:~/.ssh$ ssh -vvv xxxUName@192.
OpenSSH_6.2p2 Ubuntu-6ubuntu0.1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname 192.: Name or service not known
xxxUName@clientName:~/.ssh$ ssh -vvv xxxUName@192.168.123.106
OpenSSH_6.2p2 Ubuntu-6ubuntu0.1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.123.106 [192.168.123.106] port 22.
debug1: Connection established.
debug1: identity file /home/xxxUName/.ssh/id_rsa type -1
debug1: identity file /home/xxxUName/.ssh/id_rsa-cert type -1
debug1: identity file /home/xxxUName/.ssh/id_dsa type -1
debug1: identity file /home/xxxUName/.ssh/id_dsa-cert type -1
debug1: identity file /home/xxxUName/.ssh/id_ecdsa type -1
debug1: identity file /home/xxxUName/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.1 pat OpenSSH_5*
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.123.106" from file "/home/xxxUName/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/xxxUName/.ssh/known_hosts:1
debug3: load_hostkeys: found key type RSA in file /home/xxxUName/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 2 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss
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
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA ea:bf:60:43:09:b4:49:a5:a3:fd:b3:f4:06:eb:67:f4
debug3: load_hostkeys: loading entries for host "192.168.123.106" from file "/home/xxxUName/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/xxxUName/.ssh/known_hosts:1
debug3: load_hostkeys: found key type RSA in file /home/xxxUName/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 2 keys
debug1: Host '192.168.123.106' is known and matches the ECDSA host key.
debug1: Found key in /home/xxxUName/.ssh/known_hosts:1
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
debug2: key: ServerName_id3 (0x7ff16a5012f0),
debug2: key: xxxUName@clientName (0x7ff16a501440),
debug2: key: /home/xxxUName/.ssh/id_rsa ((nil)),
debug2: key: /home/xxxUName/.ssh/id_dsa ((nil)),
debug2: key: /home/xxxUName/.ssh/id_ecdsa ((nil)),
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: ServerName_id3
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: xxxUName@clientName
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/xxxUName/.ssh/id_rsa
debug3: no such identity: /home/xxxUName/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/xxxUName/.ssh/id_dsa
debug3: no such identity: /home/xxxUName/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/xxxUName/.ssh/id_ecdsa
debug3: no such identity: /home/xxxUName/.ssh/id_ecdsa: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by WilliamMiller54 on 2014-01-27
> **1clue said:**
> I also don't think ssh keys are portable.  When you reloaded your system the system generated new server keys.  I can't say for sure though, and don't feel like looking it up.  I'm lazy today.  :)

Anyway, make sure your $HOME is chmod 700, and are you using a DSA key or an RSA key?  DSA goes to authorized_keys2.  I use DSA.

You need to delete your whole .ssh directory and start over.  The private key needs to never leave the system it was generated on or it is considered compromised.  The public key crosses the net, the private one is protected.

This isn't strictly required but IMO your .ssh directory should be chmod 700 too.  Nobody else has any business poking around in there.

Thank you 1Clue, This is my "do-over" actually. I removed and recreated all the keys.

---

### Post by WilliamMiller54 on 2014-01-27
> **CharlesA said:**
> They are portable, but you need to be using the correct key. :)

CharlesA, 
How do you add the Public key to the Authorized_Keys file? Maybe I am doing that wrong?

---

### Post by 1clue on 2014-01-27
My second post on this thread shows the commands I use to authorize and test.

---

### Post by sh4d0w808 on 2014-01-27
On the server:

cat yourpubkey.file >> ~/.ssh/authorized_keys

This will append your public key file to authorized_keys.

---

### Post by CharlesA on 2014-01-27
Yo need to specify what private key you want to use like this:

```
ssh **-i /path/to/privatekey** -vvv xxxUName@192.xx.xx.xx
```

Or you could just cheat and create a config file in .ssh/
[http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/](http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/)

---

### Post by WilliamMiller54 on 2014-01-27
> **sh4d0w808 said:**
> On the server:

cat yourpubkey.file >> ~/.ssh/authorized_keys

This will append your public key file to authorized_keys.

sh4d0w808, I am pretty sure that my Server \ Destination host has the public key in it already. I will double check when I get home to access 

> **CharlesA said:**
> Yo need to specify what private key you want to use like this:

```
ssh **-i /path/to/privatekey** -vvv xxxUName@192.xx.xx.xx
```

Or you could just cheat and create a config file in .ssh/
[http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/](http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/)

CharlesA, Thank you. Right now I can not ssh to the server specifically referencing the server using the -i param. I will test again once I get home.

Can you confirm my understanding
[LIST]
[*]On the client side, the private and public keys should be stored in the ~/.ssh/ directory
[*]On the client side, the public key should be stored in the ~/.ssh/authorized_key file
[*]On the server | Destination side, the public key should be added to the ~/.ssh/authorized_key file
[*]On the server | Destination side, I can copy the public key from the client to the server using [ssh-copy-id <username>@<host>]
[*]On the server | Destination side, I can manually copy the public key from the client to the server and use [cat yourpubkey.file >> ~/.ssh/authorized_keys ]
[*]On the server | Destination side, I can have multiple public keys listed in the authorized_keys file
[/LIST]

thank you for your time and help

---

### Post by CharlesA on 2014-01-27
> **WilliamMiller54 said:**
> 
CharlesA, Thank you. Right now I can not ssh to the server specifically referencing the server using the -i param. I will test again once I get home.

Can you confirm my understanding
[LIST]
[*]On the client side, the private and public keys should be stored in the ~/.ssh/ directory
[*]On the client side, the public key should be stored in the ~/.ssh/authorized_key file
[*]On the server | Destination side, the public key should be added to the ~/.ssh/authorized_key file
[*]On the server | Destination side, I can copy the public key from the client to the server using [ssh-copy-id <username>@<host>]
[*]On the server | Destination side, I can manually copy the public key from the client to the server and use [cat yourpubkey.file >> ~/.ssh/authorized_keys ]
[*]On the server | Destination side, I can have multiple public keys listed in the authorized_keys file
[/LIST]

thank you for your time and help

You only need the private and public keys on the client side. They can sit in ~/.ssh and the public key should not be in ~/.ssh/authorized_keys
Everything else is correct. I've used ssh-copy-id user@host if I need to add the keys to a server, but if I'm doing an install, I'll just copy the public key over and add it to authorized_keys.

---

### Post by 1clue on 2014-01-27
On the server side, you only need the server key which is automatically generated and resides in /etc/ssh.
There is no need for a personal key to be generated on the server.  One could call it a security risk.
On the client, the private and public keys reside in ~/.ssh
On the server the public key FROM THE CLIENT goes into ~/.ssh/authorized_keys (rsa) or ~/.ssh/authorized_keys2 (dsa)

---

### Post by Lars Noodén on 2014-01-27
All the key types can go in *authorized_keys* the other file, [authorized_keys2, has been deprecated](http://www.openssh.org/txt/release-3.0) for a while.  The upcoming 6.5 will also allow [Ed25519](https://lists.mindrot.org/pipermail/openssh-unix-dev/2014-January/031987.html) keys, not just RSA, DSA and ECDSA.

---

### Post by WilliamMiller54 on 2014-01-27
> **CharlesA said:**
> You only need the private and public keys on the client side. They can sit in ~/.ssh and the public key should not be in ~/.ssh/authorized_keys
Everything else is correct. I've used ssh-copy-id user@host if I need to add the keys to a server, but if I'm doing an install, I'll just copy the public key over and add it to authorized_keys.

CharlesA, 1clue, Lars, 
    Thank you for your help. I think I am half way there.

[LIST=1]
[*]I removed the authorized_keys file from the source client system
[*]Both public and private keys are in the ~/.ssh folder in the source client system
[*]I replaced the server ~/.ssh/authorized_keys with the Public key by coping the public key to the server, removing the existing authorized_keys file, and coping the public key to authorized_keys
[/LIST]

[LIST]
[*]If I change the authorized_keys files "644" to "600" I can not connect. I have to keep permissions at "644"
[*]it takes about 30 seconds to connect, but is very quick after connected
[/LIST]

**_Issues: Now I can connect via a command line, but I can not RDP into the server using Remmina I get the following errors_**
[LIST]
[*]IF I select "SSH Authentication: Public Key (Automatic)" i receive the following error: SSH automatic public key authentication failed: No public key matched
```

[SSH] libssh 0.5.2 (c) 2003-2010 Aris Adamantiadis (aris@0xbadc0de.be) Distributed under the LGPL, please refer to COPYING file for information about your rights, using threading threads_noop
[SSH] Socket connection callback: 1 (0)
[SSH] SSH server banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] Analyzing banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] We are talking to an OpenSSH client version: 5.9 (50900)
[SSH] Error : Access denied. Authentication that can continue: publickey
[SSH] Trying to authenticate with SSH agent keys as user: xxxUserName
[SSH] Trying identity xxxUserName@client
[SSH] Error : Access denied. Authentication that can continue: publickey
[SSH] Error : No public key matched

```
[*]IF I select "SSH Authentication: Identify File > PrivateKey", I am prompted for the key password, and I receive the following error: SSH public key authentication failed: Access denied. Authentication that can continue: publickey
```

[SSH] libssh 0.5.2 (c) 2003-2010 Aris Adamantiadis (aris@0xbadc0de.be) Distributed under the LGPL, please refer to COPYING file for information about your rights, using threading threads_noop
[SSH] Socket connection callback: 1 (0)
[SSH] SSH server banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] Analyzing banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] We are talking to an OpenSSH client version: 5.9 (50900)
[SSH] Trying to open /home/xxxUserName/.ssh/clientRSAKey_id3
[SSH] Trying to read /home/xxxUserName/.ssh/clientRSAKey_id3, passphase=true, authcb=false
[SSH] Error : Parsing private key /home/xxxUserName/.ssh/clientRSAKey_id3: error:0906A068:lib(9):func(106):reason(104)
[SSH] Trying to open /home/xxxUserName/.ssh/clientRSAKey_id3
[SSH] Trying to read /home/xxxUserName/.ssh/clientRSAKey_id3, passphase=true, authcb=false
[SSH] Error : Access denied. Authentication that can continue: publickey

```
[*]IF I select "SSH Authentication: Identify File > PublicKey", SSH public key authentication failed: Public key file doesn't exist
```

[SSH] libssh 0.5.2 (c) 2003-2010 Aris Adamantiadis (aris@0xbadc0de.be) Distributed under the LGPL, please refer to COPYING file for information about your rights, using threading threads_noop
[SSH] Socket connection callback: 1 (0)
[SSH] SSH server banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] Analyzing banner: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
[SSH] We are talking to an OpenSSH client version: 5.9 (50900)
[SSH] Error : Public key file doesn't exist

```
[/LIST]

Is there something wrong with my keys? Is there a configuration that I am missing. 

Server Files
```

xxxUserName@server:~$ ls -l ~/.ssh/
total 12
-rw-r--r-- 1 root root 399 Jan 27 16:25 authorized_keys
-rw------- 1 root root 399 Jan 24 15:49 authorized_keys_Backup
-rw-r--r-- 1 root root 399 Jan 24 15:48 clientRSAKey_id3.pub

```

Client Files
```

xxxUserName@client:~/.ssh$ ls -l
total 12
-rw-r--r-- 1 xxxUserName xxxUserName  619 Jan 24 16:37 known_hosts
-rw------- 1 xxxUserName xxxUserName 1766 Jan 24 15:42 clientRSAKey_id3
-rw-r--r-- 1 xxxUserName xxxUserName  399 Jan 24 15:42 clientRSAKey_id3.pub

xxxUserName@client:~/.ssh$ ssh -v xxxUserName@192.168.123.106
OpenSSH_6.2p2 Ubuntu-6ubuntu0.1, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.123.106 [192.168.123.106] port 22.
debug1: Connection established.
debug1: identity file /home/xxxUserName/.ssh/id_rsa type -1
debug1: identity file /home/xxxUserName/.ssh/id_rsa-cert type -1
debug1: identity file /home/xxxUserName/.ssh/id_dsa type -1
debug1: identity file /home/xxxUserName/.ssh/id_dsa-cert type -1
debug1: identity file /home/xxxUserName/.ssh/id_ecdsa type -1
debug1: identity file /home/xxxUserName/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p2 Ubuntu-6ubuntu0.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.1 pat OpenSSH_5*
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA ea:bf:60:43:09:b4:49:a5:a3:fd:b3:f4:06:eb:67:f4
debug1: Host '192.168.x.x' is known and matches the ECDSA host key.
debug1: Found key in /home/xxxUserName/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: xxxUserName@client
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: Authentication succeeded (publickey).
Authenticated to 192.168.123.106 ([192.168.123.106]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-53-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Mon Jan 27 17:17:19 2014 from client.local



```

Thank you

---

### Post by CharlesA on 2014-01-27
> **WilliamMiller54 said:**
> 
[LIST]
[*]If I change the authorized_keys files "644" to "600" I can not connect. I have to keep permissions at "644"
[*]it takes about 30 seconds to connect, but is very quick after connected
[/LIST]


authorized_keys needs to be world readable, because it is owned by the user, so that's fine.

As far as the delay, is that between the time you enter the username and password or before the logon prompt?

I've had a delay after login while processes are running, but if the delay is priory to actually logging in, it might be either slow name resolution or a slow network.

---

### Post by WilliamMiller54 on 2014-01-27
> **CharlesA said:**
> authorized_keys needs to be world readable, because it is owned by the user, so that's fine.

As far as the delay, is that between the time you enter the username and password or before the logon prompt?

I've had a delay after login while processes are running, but if the delay is priory to actually logging in, it might be either slow name resolution or a slow network.

Thanks CharlesA, 
It takes about 30 seconds before the password prompt. It is working, so I wont look a gift horse in the mouth.

Any idea why I can not SSH through the Remmina RDP client?

---

### Post by CharlesA on 2014-01-27
I haven't used Remmina before, but if I need to access something via VNC or RDP, I usually establish the SSH connection first then use [noparse]localhost:port[/noparse] number to connect to the service.

The server could be doing a DNS lookup of the client, but I'm not really sure if that would cause the delay or not.

---

### Post by sh4d0w808 on 2014-01-28
On the clientside, you need permission 600 on .ssh directory in your home.

---

### Post by WilliamMiller54 on 2014-01-28
> **CharlesA said:**
> I haven't used Remmina before, but if I need to access something via VNC or RDP, I usually establish the SSH connection first then use [noparse]localhost:port[/noparse] number to connect to the service.

The server could be doing a DNS lookup of the client, but I'm not really sure if that would cause the delay or not.

CharlesA, 
Can you please elaborate on that? You open a SSH connection via Terminal (port 22) and then point your RDP client to "localhost:22" ???

---

### Post by CharlesA on 2014-01-28
> **WilliamMiller54 said:**
> CharlesA, 
Can you please elaborate on that? You open a SSH connection via Terminal (port 22) and then point your RDP client to "localhost:22" ???

Sorta. SSH -L 9001 192.168.1.1:3389

Connect to localhost:9001

---

### Post by WilliamMiller54 on 2014-01-28
> **CharlesA said:**
> Sorta. SSH -L 9001 192.168.1.1:3389

Connect to localhost:9001

Thank you CharlesA, you have been a huge help. This has been a big learning experience for me. Thank you

---

### Post by CharlesA on 2014-01-28
If you want more info about how to configure sshd, check out this page:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

