---
title: "Slow ssh login to server"
date: 2009-05-19
forum: Server Platforms
---

### Post by jonathanmotes on 2009-05-19
When I try to ssh to my server (running Intrepid), it immediately asks for a password, but takes a long time (about 20 seconds) to connect after the password is entered. The length of time is comparable when on the local network (accessing through local ip) or connecting when off site.

I've tried everything on the internet that I can find, to no avail (UseDNS no, etc). I could be doing something wrong, however. I also am not sure what should be configured on the server side, and what should be configured on the ssh client. 

The login time seems to get longer every day (its been running for 112 days, and when I first installed Ubuntu it was much faster on the ssh connection). Also, trying to type once a connection has been made is becoming very slow *when off site*. I would hate to have to reboot to fix the issue. 

Could someone help please?

---

### Post by HermanAB on 2009-05-19
Howdy,

It is likely a PAM configuration problem.  Try to use verbose mode to see what is going on:

$ ssh -vvv user@server

---

### Post by heebus on 2009-05-19
When I experienced this problem it was slowing on the GSS API.  Run the above and determine where it slows.  

You can turn it off in /etc/ssh/ssh_config

---

### Post by jonathanmotes on 2009-05-19
Thanks for the responses everyone! I don't know much about this, so hopefully you all can help me figure it out.

In verbose mode:

Start (after entering ssh -vvv user@server):
```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to motes-server-01 [10.0.0.2] port 22.
debug1: Connection established.
debug1: identity file /home/jonathan/.ssh/identity type -1
debug3: Not a RSA1 key file /home/jonathan/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
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
debug1: identity file /home/jonathan/.ssh/id_rsa type 1
debug1: identity file /home/jonathan/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 123/256
debug2: bits set: 507/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/jonathan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 4
debug3: check_host_in_hostfile: filename /home/jonathan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'motes-server-01' is known and matches the RSA host key.
debug1: Found key in /home/jonathan/.ssh/known_hosts:4
debug2: bits set: 524/1024
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
debug2: key: /home/jonathan/.ssh/id_rsa (0xb7ffe640)
debug2: key: /home/jonathan/.ssh/identity ((nil))
debug2: key: /home/jonathan/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/jonathan/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jonathan/.ssh/identity
debug3: no such identity: /home/jonathan/.ssh/identity
debug1: Trying private key: /home/jonathan/.ssh/id_dsa
debug3: no such identity: /home/jonathan/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
motes@motes-server-01's password:

```


After I enter the password, it immediately shows this before waiting ~20 seconds:
```
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
```

After the wait, it "spits" this out:
```
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
```

Thanks!

---

### Post by jonathanmotes on 2009-05-19
> **heebus said:**
> When I experienced this problem it was slowing on the GSS API.  Run the above and determine where it slows.  

You can turn it off in /etc/ssh/ssh_config

Do I turn this off on the client or the server?

Thanks!

---

### Post by heebus on 2009-05-19
ssh_config = client
sshd_config = server

The change is in the client. That is who makes the request.

---

### Post by jonathanmotes on 2009-05-20
UPDATE:

I rebooted the server, and that fixed the issue. BUT, this is bad.... there should be better reasons to have to reboot.... :) 

I really wish someone had the answer here. In an uptime sense (and only in a uptime sense), this problem limits Linux and makes it appear to not be as good as a Windows server. Please, someone prove me wrong....

---

### Post by iissmart on 2009-06-02
I am also having a similar issue, but only when I log into my server via Putty on Windows, not when I log on through a Linux installation.

Putty will prompt for my username, I hit enter, then have to wait about ~20 seconds before it prompts for my password. After that, it logs in promptly, so the delay is between asking for my username and asking for my password. Is this similar to the other issue?

---

### Post by y@w on 2009-06-02
This is a slightly older thread but may still apply:
[http://ubuntuforums.org/showthread.php?t=361262](http://ubuntuforums.org/showthread.php?t=361262)

---

### Post by aebrett on 2010-02-10
I was having a similar issue, and tracked it down to the message of the day update scripts taking an age to complete. This was because I had mounted samba shares which were unavailable, causing timeouts when trying to get their disk usage. I've fixed it by manually hacking the script to ignore samba shares, details here: [http://bretts.org/wiki/Miscellaneous#ssh:_Slow_login](http://bretts.org/wiki/Miscellaneous#ssh:_Slow_login). A bug report has also been raised: [https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930](https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930).

---

### Post by pedemoz on 2010-05-14
> **aebrett said:**
> I was having a similar issue, and tracked it down to the message of the day update scripts taking an age to complete. This was because I had mounted samba shares which were unavailable, causing timeouts when trying to get their disk usage. I've fixed it by manually hacking the script to ignore samba shares, details here: [http://bretts.org/wiki/Miscellaneous#ssh:_Slow_login](http://bretts.org/wiki/Miscellaneous#ssh:_Slow_login). A bug report has also been raised: [https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930](https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/519930).

Thanks to aebrett!  I had exactly the same issue and his solution worked - check the Launchpad bug report and solution (or checkout Andrew's page for the same solution).

---

### Post by eltreno on 2010-08-02
I have been looking for a solution for this for ages as my host won't change the sshd_config files (shared host)
So UseDNS no isn't an option for me

anyway:

if you add 
hosts_ip_address  your_domain
to your /etc/hosts file the password prompt will display almost straight away

eg
123.123.123.123 example.com

---

