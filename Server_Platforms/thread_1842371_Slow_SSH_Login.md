---
title: "Slow SSH Login"
date: 2011-09-11
forum: Server Platforms
---

### Post by erik5678 on 2011-09-11
Hi!

I've been googling on this problem for a while now, but I have not found a solution that works.

The problem is that today all of a sudden the SSH login to my server is very slow. From the password prompt showing up immediately, it now takes about 12 seconds. No matter what computer I'm logging in from. There is no delay at all after the password is entered.

I tried verbose mode and it's getting stuck at "key: /Users/erik/.ssh/id_dsa (0x0)" for the 12 seconds I mentioned earlier.

I also have an AFP server set up that shows the exact same delay of about 12 seconds, starting today. It seems like it's an authtentication problem of some kind.

Does anyone know how to fix this?

EDIT: I just tried out the FTP server (Pureftpd with puredb authentication) and it also has this delay.

SSH connection log:
```

OpenSSH_5.6p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.10 [192.168.0.10] port 22.
debug1: Connection established.
debug1: identity file /Users/erik/.ssh/id_rsa type -1
debug1: identity file /Users/erik/.ssh/id_rsa-cert type -1
debug1: identity file /Users/erik/.ssh/id_dsa type -1
debug1: identity file /Users/erik/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.6
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 122/256
debug2: bits set: 522/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.10' is known and matches the RSA host key.
debug1: Found key in /Users/erik/.ssh/known_hosts:1
debug2: bits set: 532/1024
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
debug2: key: /Users/erik/.ssh/id_rsa (0x0)
debug2: key: /Users/erik/.ssh/id_dsa (0x0)

- Pause here for about 12 seconds -

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/erik/.ssh/id_rsa
debug1: Trying private key: /Users/erik/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
erik@192.168.0.10's password:

```

---

### Post by erik5678 on 2011-09-11
Okey, so I've found whats making it slow. It's the avahi-daemon. Now the question is how to fix it. Any ideas?

EDIT: Problem solved. It was a line in my avahi configuration file that was wrong. It did strangely work for a couple of days.

A line in the /etc/dnsswitch.conf that read "hosts: files mdns4_minimal  [NOTFOUND=return] dns mdns 4 mdns" was changed to "hosts: files dns" and  now it works again.

---

### Post by slavin on 2012-02-27
And when he says dnsswitch.conf.... he really means nsswitch.conf. :)

> **erik5678 said:**
> Okey, so I've found whats making it slow. It's the avahi-daemon. Now the question is how to fix it. Any ideas?

EDIT: Problem solved. It was a line in my avahi configuration file that was wrong. It did strangely work for a couple of days.

A line in the /etc/dnsswitch.conf that read "hosts: files mdns4_minimal  [NOTFOUND=return] dns mdns 4 mdns" was changed to "hosts: files dns" and  now it works again.

---

### Post by hawkmage on 2012-02-27
OK, that fits into what I was going to mention.

With ssh login being slow the first thing to check is name resolution on the server running the sshd.  Sshd will attempt to identify the incoming host and part of that is resolving the IP address of the incoming connection to a host name.  So if you have a slow reverse DNS IP to name look up then you will see a delay in the login.

---

### Post by rrsk on 2012-04-18
it really works..........thanks a lot.....

---

### Post by jjinco33 on 2012-09-19
This worked for me as well, changed the hosts line to "hosts:          files dns"  logged off and back in. Login prompt and response time was almost instant.

---

### Post by Orbitize on 2012-10-13
Thank you, the slow login prompt has been bothering me for a while!

---

### Post by keithbunt1 on 2012-11-08
Thanks for this!

Definitely worked on 12.10. Changed it, logged off, and saw a drastic immediately improvement!

Thanks
Keith

---

### Post by ReTheOff on 2013-05-16
Thanks!  Was so annoying.  Now if I can just get rid of all that banner info. :)

---

### Post by ReTheOff on 2013-05-16
A little off topic, but... Found my answer quick:

In /etc/pam.d/sshd , comment this line.
# Print the message of the day upon successful login.
#session    optional     pam_motd.so # [1]

Removing the cool stats banner upon login increased my login time greatly, along with the nsswitch.conf fix above.  I don't really care about all the stats on most of my systems.

---

### Post by samialqsaimi on 2013-11-03
Yes,as ReTheOff has written is correct.You have to comment these two lines ((# Print the message of the day upon successful login -  #session    optional     pam_motd.so # [1]
 )) ,this it will let you login in one second.Thanks

---

