---
title: "Why are my reverse SSH tunnels suddenly dying?"
date: 2009-10-15
forum: Server Platforms
---

### Post by chadjohnson on 2009-10-15
I have had persistent tunnels from all my client computers to my servers in place for about a year now. I've not updated my server or changed any configuration files--as far as I remember--for several months. Suddenly my tunnels stopped working for all of my client computers (I use a different port for each).

I use RSA keys. I've regenerated them multiple times on every computer.

I have a script run the following via a Cron job when it does not find "clients@my.hostname" in "ps aux" output:

```

    ssh -p 2222 -g -T -N -x -f -R 2223:localhost:22 clients@my.hostname

```

When I run this command manually with -vvv, I can ssh into the server then ssh into the forwarded port (ssh localhost -p 2223) just fine. After five minutes, however, it just hangs. I get the following output on the server with -vvv:

```

    chad@zeus:~$ ssh localhost -p 2223 -vvv
    OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
    debug1: Reading configuration data /etc/ssh/ssh_config
    debug1: Applying options for *
    debug2: ssh_connect: needpriv 0
    debug1: Connecting to localhost [127.0.0.1] port 2223.
    debug1: Connection established.
    debug1: identity file /home/chad/.ssh/identity type -1
    debug3: Not a RSA1 key file /home/chad/.ssh/id_rsa.
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
    debug1: identity file /home/chad/.ssh/id_rsa type 1
    debug1: identity file /home/chad/.ssh/id_dsa type -1

```

When I telnet to the port I get

```

    chad@zeus:~$ telnet localhost 2223
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.

```

Normally I get output output like "SSH-2.0-OpenSSH_4.3".

On the client side, where I initiated the tunnel (via ssh -p 2222 -g -T -N -x -f -R 2223:localhost:22 [email]clients@my.hostna[/email]me), I get the following verbose output:

```

    OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
    debug1: Reading configuration data /etc/ssh/ssh_config
    debug1: Applying options for *
    debug2: ssh_connect: needpriv 0
    debug1: Connecting to my.hostname [68.6.214.39] port 2222.
    debug1: Connection established.
    debug1: identity file /home/chad/.ssh/identity type -1
    debug3: Not a RSA1 key file /home/chad/.ssh/id_rsa.
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
    debug1: identity file /home/chad/.ssh/id_rsa type 1
    debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
    debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
    debug1: identity file /home/chad/.ssh/id_dsa type -1
    debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
    debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
    debug1: Enabling compatibility mode for protocol 2.0
    debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
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
    debug2: dh_gen_key: priv key bits set: 120/256
    debug2: bits set: 525/1024
    debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
    debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
    debug3: put_host_port: [68.6.214.39]:2222
    debug3: put_host_port: [my.hostname]:2222
    debug3: check_host_in_hostfile: filename /home/chad/.ssh/known_hosts
    debug3: check_host_in_hostfile: match line 3
    debug3: check_host_in_hostfile: filename /home/chad/.ssh/known_hosts
    debug3: check_host_in_hostfile: match line 2
    debug1: Host '[my.hostname]:2222' is known and matches the RSA host key.
    debug1: Found key in /home/chad/.ssh/known_hosts:3
    debug2: bits set: 534/1024
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
    debug2: key: /home/chad/.ssh/id_rsa (0xb9b96ad0)
    debug2: key: /home/chad/.ssh/identity ((nil))
    debug2: key: /home/chad/.ssh/id_dsa ((nil))
    debug1: Authentications that can continue: publickey,password
    debug3: start over, passed a different list publickey,password
    debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
    debug3: authmethod_lookup publickey
    debug3: remaining preferred: keyboard-interactive,password
    debug3: authmethod_is_enabled publickey
    debug1: Next authentication method: publickey
    debug1: Offering public key: /home/chad/.ssh/id_rsa
    debug3: send_pubkey_test
    debug2: we sent a publickey packet, wait for reply
    debug1: Server accepts key: pkalg ssh-rsa blen 277
    debug2: input_userauth_pk_ok: fp 14:ff:10:40:31:88:05:bc:46:73:91:ef:58:70:cc:78
    debug3: sign_and_send_pubkey
    debug1: Authentication succeeded (publickey).
    debug1: Remote connections from LOCALHOST:2223 forwarded to local address localhost:22
    debug1: Entering interactive session.
    debug1: remote forward success for: listen 2223, connect localhost:22
    debug1: All remote forwarding requests processed

```

Permissions for my .ssh directory and files are as follows:

```

    drwxr-xr-x  2 chad chad   4096 2009-10-15 00:03 .ssh

    -rw-r--r-- 1 chad chad  408 2009-10-15 00:03 authorized_keys
    -rw------- 1 chad chad 1675 2009-10-14 10:09 id_rsa
    -rw-r--r-- 1 chad chad  393 2009-10-14 10:09 id_rsa.pub
    -rw------- 1 chad chad 2210 2009-10-14 11:27 known_hosts

```

Furthermore, if I "killall ssh" on the client and then telnet to port 2223, I still get a response:

```

    chad@zeus:~$ telnet localhost 2223
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.

```

I am thoroughly confused. Any ideas why this is happening?

---

### Post by chadjohnson on 2009-10-15
Solved. Answer here: [http://serverfault.com/questions/75008/why-are-my-reverse-ssh-tunnels-suddenly-dying/75011#75011](http://serverfault.com/questions/75008/why-are-my-reverse-ssh-tunnels-suddenly-dying/75011#75011)

---

