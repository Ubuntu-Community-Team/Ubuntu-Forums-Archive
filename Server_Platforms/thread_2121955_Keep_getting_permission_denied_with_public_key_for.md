---
title: "Keep getting permission denied with public key for ssh on server"
date: 2013-03-03
forum: Server Platforms
---

### Post by kanadaguy on 2013-03-03
Okay I have installed Ubuntu 11.10 and did the update, upgrade -y and dist-upgrade... I installed SSH with tasksel on install.. I confirmed with ps -A | grep ssh that it is indeed running... I have changed the permission of my authenticated.keys file as well as the .ssh directory... I have changed the sshd_config to only accept rsa public key and have uploaded it of course via scp id_rsa.pub sysop@ip addy:/home/sysop and cat it to the authenticated.keys ... I have done this setup many times however this time I keep getting issues with the public key.

I did a ssh -v sysop@ip so I could see what was going on and it keeps trying other auth methods and then spits out that error..I looked in the auth.log and it doesnt show anything useful... It just seems like it either isn't accepting keys over the network or isn't looking at the authenticated.keys files (yes my sshd_config file is pointing to the correct location)... Its driving me mad.. I am wondering if the updates caused this issue or if installing it via tasksel during install caused this I don't think I did either last time... 

Please if anyone has any help I would appricate it!!!!!!

---

### Post by kanadaguy on 2013-03-03
This is located on my local network and I can ping to the internet from this box so it isn't a hardware issue..

---

### Post by Cheesemill on 2013-03-03
I've never had to change the permissions on any of the files or make any configuration changes, I just generate a key on the client machine and then use the the ssh-copy-id command to copy the key to the correct location on the SSH server.

```
rob@raring:~$ ssh-keygen 
Generating public/private rsa key pair.
Enter file in which to save the key (/home/rob/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/rob/.ssh/id_rsa.
Your public key has been saved in /home/rob/.ssh/id_rsa.pub.
The key fingerprint is:
ce:fd:08:2e:5a:fe:16:93:d1:ab:57:87:f4:21:92:35 rob@raring
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|            E    |
|         . o .   |
|        . + o .  |
|        So + + . |
|       o+.. o o  |
|      . ++.. .   |
|     o..o..o     |
|    ...+o.. .    |
+-----------------+
rob@raring:~$ 
rob@raring:~$ 
rob@raring:~$ 
rob@raring:~$ ssh-copy-id rob@192.168.1.1
The authenticity of host '192.168.1.1 (192.168.1.1)' can't be established.
ECDSA key fingerprint is b4:f4:62:47:f4:7b:82:7a:f9:81:44:07:0c:31:bb:64.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.1' (ECDSA) to the list of known hosts.
rob@192.168.1.1's password: 
Now try logging into the machine, with "ssh 'rob@192.168.1.1'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

rob@raring:~$ 
rob@raring:~$ 
rob@raring:~$ 
rob@raring:~$ ssh rob@192.168.1.1
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Mar  3 22:35:06 GMT 2013

  System load:  0.35              Processes:           69
  Usage of /:   6.4% of 15.75GB   Users logged in:     0
  Memory usage: 1%                IP address for eth0: 192.168.1.1
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

11 packages can be updated.
11 updates are security updates.

rob@gateway:~$ 
```

All of my servers have had the SSH server installed with the tasksel screen during installation so I don't think that this is the problem.
If you can please post the full verbose output of the ssh command you are running it might help us diagnose the problem...
```
ssh -vvv sysop@ip
```

Just as a side note, now probably isn't the best time to be installing 11.10 as support for it runs out next month. After this no more security updates or bug fixes will be released and the repositories will be taken off-line.

---

### Post by kanadaguy on 2013-03-10
Thank you for your prompt response here is the following for the verbose of ssh:

```
SysOps-MacBook-Air:~ rico$ ssh -vvv -p50000 sysop@192.168.2.200
OpenSSH_5.9p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: /etc/ssh_config line 53: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.200 [192.168.2.200] port 50000.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/Users/rico/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /Users/rico/.ssh/id_rsa type 1
debug1: identity file /Users/rico/.ssh/id_rsa-cert type -1
debug1: identity file /Users/rico/.ssh/id_dsa type -1
debug1: identity file /Users/rico/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-3ubuntu1
debug1: match: OpenSSH_6.0p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [192.168.2.200]:50000
debug3: load_hostkeys: loading entries for host "[192.168.2.200]:50000" from file "/Users/rico/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 115/256
debug2: bits set: 482/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 06:6b:50:f4:a6:3f:30:16:50:ea:2b:ec:4b:20:fe:ea
debug3: put_host_port: [192.168.2.200]:50000
debug3: put_host_port: [192.168.2.200]:50000
debug3: load_hostkeys: loading entries for host "[192.168.2.200]:50000" from file "/Users/rico/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug3: load_hostkeys: loading entries for host "[192.168.2.200]:50000" from file "/Users/rico/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug1: checking without port identifier
debug3: load_hostkeys: loading entries for host "192.168.2.200" from file "/Users/rico/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /Users/rico/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.2.200' is known and matches the RSA host key.
debug1: Found key in /Users/rico/.ssh/known_hosts:1
debug1: found matching key w/out port
debug2: bits set: 510/1024
debug1: ssh_rsa_verify: signature correct
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
debug2: key: /Users/rico/.ssh/id_rsa (0x7fa3a241d0e0)
debug2: key: /Users/rico/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/rico/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /Users/rico/.ssh/id_dsa
debug3: no such identity: /Users/rico/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

Any ideas? Have anything to do with the RSA key not loading ..?

---

