---
title: "ssh/scp 'no such identity' missing files?"
date: 2013-05-15
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-05-15
anyone know what this is about?
```
chad@VirtualBox:~$ ssh 10.0.0.50
no such identity: /home/chad/.ssh/id_rsa: No such file or directory
no such identity: /home/chad/.ssh/id_dsa: No such file or directory
no such identity: /home/chad/.ssh/id_ecdsa: No such file or directory
chad@10.0.0.50's password: 

chad@VirtualBox:~$ scp 10.0.0.50:/usr/local/bin/screenfetch ./
no such identity: /home/chad/.ssh/id_rsa: No such file or directory
no such identity: /home/chad/.ssh/id_dsa: No such file or directory
no such identity: /home/chad/.ssh/id_ecdsa: No such file or directory
chad@10.0.0.50's password: 
screenfetch                                   100%  109KB 109.5KB/s   00:00    
chad@VirtualBox:~$ ./screenfetch 
                          ./+o+-
                  yyyyy- -yyyyyy+      chad@VirtualBox
               ://+//////-yyyyyyo      OS: Ubuntu 13.10 saucy
           .++ .:/++++++/-.+sss/`      Kernel: x86_64 Linux 3.9.0-2-generic
         .:++o:  /++++++++/:--:/-      Uptime: 2m
        o:+o+:++.`..```.-/oo+++++/     Packages: 1433
       .:+o:+o/.          `+sssoo+/    Shell: bash 4.2.45
  .++/+:+oo+o:`             /sssooo.   Resolution: 1024x768
 /+++//+:`oo+o               /::--:.   DE: XFCE4
 \+/+o+++`o++o               ++////.   WM: Xfwm4
  .++.o+++oo+:`             /dddhhh.   WM Theme: Albatross
       .+.o+oo:.          `oddhhhh+    GTK2 Theme: Albatross
        \+.++o+o``-````.:ohdhhhhh+     Icon Theme: elementary-xfce-dark
         `:o+++ `ohhhhhhhhyo++os:      Font: Droid Sans 10
           .o:`.syhhhhhhh/.oo++o`      CPU: AMD Phenom II X4 965 @ GHz
               /osyyyyyyo++ooo+++/     GPU: VirtualBox Graphics Adapter
                   ````` +oo+++o\:     RAM: 249MB / 2002MB
                          `oo++.
chad@VirtualBox:~$ ssh 10.0.0.50
no such identity: /home/chad/.ssh/id_rsa: No such file or directory
no such identity: /home/chad/.ssh/id_dsa: No such file or directory
no such identity: /home/chad/.ssh/id_ecdsa: No such file or directory
chad@10.0.0.50's password: 
Welcome to Ubuntu 13.04 (GNU/Linux 3.9.2-030902-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Wed May 15 21:53:48 2013 from virtualbox.local
 _________________________________________
/  The Priest's grey nimbus in a niche    \
| where he dressed discreetly. I will not |
| sleep here tonight. Home also I cannot  |
| go.                                     |
|                                         |
| A voice, sweetened and sustained,       |
| called to him from the sea. Turning the |
| curve he waved his hand. A sleek brown  |
| head, a seal's, far out on the water,   |
| round. Usurper.                         |
|                                         |
\ -- James Joyce, "Ulysses"               /
 -----------------------------------------
  \
   \
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
chad@M4A79XTD-EVO:~$
```

---

### Post by cariboo on 2013-05-15
Try:

```
ssh -vv user@server
```

to see what the output is.

---

### Post by pqwoerituytrueiwoq on 2013-05-15
Wow that is a lot of text @.@ I've seen more in log files but till that is a lot
```
chad@VirtualBox:~$ ssh -vv chad@10.0.0.50
OpenSSH_6.2p1 Debian-3, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.0.0.50 [10.0.0.50] port 22.
debug1: Connection established.
debug1: identity file /home/chad/.ssh/id_rsa type -1
debug1: identity file /home/chad/.ssh/id_rsa-cert type -1
debug1: identity file /home/chad/.ssh/id_dsa type -1
debug1: identity file /home/chad/.ssh/id_dsa-cert type -1
debug1: identity file /home/chad/.ssh/id_ecdsa type -1
debug1: identity file /home/chad/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p1 Debian-3
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.1p1 Debian-4
debug1: match: OpenSSH_6.1p1 Debian-4 pat OpenSSH*
debug2: fd 3 setting O_NONBLOCK
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
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: Server host key: ECDSA 3b:2f:bf:2a:e7:ca:26:03:0c:7f:63:a0:29:c8:7a:0f
debug1: Host '10.0.0.50' is known and matches the ECDSA host key.
debug1: Found key in /home/chad/.ssh/known_hosts:1
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
debug2: key: /home/chad/.ssh/id_rsa ((nil)), explicit
debug2: key: /home/chad/.ssh/id_dsa ((nil)), explicit
debug2: key: /home/chad/.ssh/id_ecdsa ((nil)), explicit
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/chad/.ssh/id_rsa
**no such identity: /home/chad/.ssh/id_rsa: No such file or directory**
debug1: Trying private key: /home/chad/.ssh/id_dsa
**no such identity: /home/chad/.ssh/id_dsa: No such file or directory**
debug1: Trying private key: /home/chad/.ssh/id_ecdsa
**no such identity: /home/chad/.ssh/id_ecdsa: No such file or directory**
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
chad@10.0.0.50's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to 10.0.0.50 ([10.0.0.50]:22).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 13.04 (GNU/Linux 3.9.2-030902-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Wed May 15 22:21:23 2013 from virtualbox.local
 ________________________________________
/ You have a will that can be influenced \
\ by all with whom you come in contact.  /
 ----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
chad@M4A79XTD-EVO:~$ exit
logout
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
Connection to 10.0.0.50 closed.
Transferred: sent 13272, received 16760 bytes, in 46.1 seconds
Bytes per second: sent 287.7, received 363.3
debug1: Exit status 0
chad@VirtualBox:~$ 
```

---

### Post by cariboo on 2013-05-15
It may be a permission issue with /home/user/.ssh, on my system that directory has permission of 700 and the permission of the files look like this:

[table="width: 500"]
[tr]
	[td]authorized_keys[/td]
	[td]777[/td]
[/tr]
[tr]
	[td]id_rsa[/td]
	[td]777[/td]
[/tr]
[tr]
	[td]id_rsa.pub[/td]
	[td]777[/td]
[/tr]
[/table]

(**Note:** just trying out the table function to see how it looks.)

---

### Post by pqwoerituytrueiwoq on 2013-05-15
the permissions match the ones on my raring install, only file i have in ~/.ssh is known_host on my raring and saucy install, the other 3 files were never created
i use ssh about every day, this is the 1st i have seen about these files

---

### Post by cariboo on 2013-05-15
I use key based password-less login when using ssh, so that's probably the difference, why it throws up and error message now, I'm not sure.

---

### Post by CharlesA on 2013-05-15
> **cariboo907 said:**
> I use key based password-less login when using ssh, so that's probably the difference, why it throws up and error message now, I'm not sure.

It's probably checking for them and not finding them. Dunno why it would throw an error though.

---

### Post by pqwoerituytrueiwoq on 2013-05-15
should i file a bug report?

i just type my password every time

---

### Post by cariboo on 2013-05-15
> **pqwoerituytrueiwoq said:**
> should i file a bug report?

i just type my password every time

I would, report it as a bug, if there has been a change in the way ssh works, the devs will let us know, especially if you mark it as a security problem.

---

### Post by P-I H on 2013-05-16
The behaviour is changed between my 13.04 and 13.10 installations on the same computer.

In 13.04 it only asks for password.

In 13.10 I get this message
```
p-i@pi-GA-990FXA-UD3-1310:~$ ssh -p xxxx p-i@a.b.c.d
no such identity: /home/p-i/.ssh/id_rsa: No such file or directory
no such identity: /home/p-i/.ssh/id_dsa: No such file or directory
no such identity: /home/p-i/.ssh/id_ecdsa: No such file or directory
p-i@a.b.c.d's password: 
```

in /home/Userid/.ssh there is only one file known_hosts

---

### Post by matt_symes on 2013-05-16
Hi

From man ssh

> 
~/.ssh/identity
     ~/.ssh/id_dsa
     ~/.ssh/id_ecdsa
     ~/.ssh/id_rsa
             Contains the private key for authentication.  These files contain sensitive data and should be readable by the user
             but not accessible by others (read/write/execute).  ssh will simply ignore a private key file if it is accessible by
             others.  It is possible to specify a passphrase when generating the key which will be used to encrypt the sensitive
             part of this file using 3DES.

     ~/.ssh/identity.pub
     ~/.ssh/id_dsa.pub
     ~/.ssh/id_ecdsa.pub
     ~/.ssh/id_rsa.pub
             Contains the public key for authentication.  These files are not sensitive and can (but need not) be readable by any&#8208;
             one.
```

matthew-S206:/home/matthew % ls -l .ssh/
total 16
-rw------- 1 matthew matthew  869 Jul 27  2012 config
-rw------- 1 matthew matthew 1675 Apr 19  2011 id_rsa
-rw-r--r-- 1 matthew matthew  404 Apr 19  2011 id_rsa.pub
-rw-r--r-- 1 matthew matthew  718 May  1 01:05 known_hosts
matthew-S206:/home/matthew % 
```

Maybe they've changed the wording of the warning ?

Kind regards

---

### Post by pqwoerituytrueiwoq on 2013-05-16
made a report
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1180834](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1180834)

---

### Post by CharlesA on 2013-05-16
It looks like they are just throwing messages around in case someone is wondering why pubkey auth isn't working. Just a guess, but it doesn't make any sense to me.

---

### Post by pqwoerituytrueiwoq on 2013-05-18
This appears to have been fixed, anyone able to confirm that
openssh-client version 1:6.2p2-1

---

### Post by P-I H on 2013-05-18
Yes it is fixed in my installation

---

### Post by filannim on 2013-05-22
I had the same problem (13.04) and I didn't manage to connect to my workstation.

I solved using:
```

$: ssh-keygen
$: ssh-keygen -t dsa
$: ssh-keygen -t ecdsa
```

Bye,
michele.

---

