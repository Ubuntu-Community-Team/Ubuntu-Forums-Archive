---
title: "Completely Stumped: rsnapshot backup"
date: 2009-02-03
forum: Server Platforms
---

### Post by Rhiknow on 2009-02-03
Greetings,

I was wondering if anyone could help? (been having a bad day...) So here it goes.

I've got this setup:

(desktop) ---c1--- (machineA) ---c2--- (machineB)

c1 is connection 1 (ports 22, 80 & 443 open)
c2 is connection 2 (ports 22, 80 & 443 open)

Basically I want to backup machineB onto my desktop (which has lots of RAID arrays) every day using rsnapshot

I've setup a tunnel on desktop as follows:
`ssh -L 9999:machineB:22 userA@machineA`

This works fine -- no passwords and public/private key encryption.

I can even do:
`ssh -l userB -p 9999 machineB`
and get a direct, passwordless connection to machineB> from a Desktop terminal.

It's when I run 
`sudo /usr/bin/rsnaphot daily`

It keeps prompting me for a password!!!

I'm sure I've configured rsnapshot correctly (and yes, rsync is given the switch to get it to operate over port 22, not port 873)

I can also connect to the following servers just fine (i.e. without using passwords):
desktop> ssh userA@machineA
and:
machineA> ssh userB@machineB

I've looked at the verbose output but can't seem to be able to figure anything out...

> 
sudo /usr/bin/rsnapshot hourly
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 9999.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug3: Not a RSA1 key file /root/.ssh/id_rsa.
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
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
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
debug2: dh_gen_key: priv key bits set: 121/256
debug2: bits set: 523/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: [127.0.0.1]:9999
debug3: put_host_port: [localhost]:9999
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '[localhost]:9999' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug2: bits set: 507/1024
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
debug2: key: /root/.ssh/identity ((nil))
debug2: key: /root/.ssh/id_rsa (0x7fbb95fc54e0)
debug2: key: /root/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug3: no such identity: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
bckp@localhost's password:


I have the following line in my rsnapshot.conf file:
backup      bckp@localhost:/home/       serverB/        rsync_short_args=-azv     (yes, I've double checked the tabs...)

If I change this line to the simpler:
backup       bckp@serverA:/home/       serverA/       rsync_short_args=-azv     (yes, I've changed back the ssh_args from -p 9999 to -p 22)

What's this "root" business? I'm completely stumped...

I've even appended Desktop's /root/.ssh/id_rsa.pub to machineB's /home/bckp/.ssh/authorized_keys

Any insight would be much appreciated.

---

### Post by HermanAB on 2009-02-04
For whatever reason, the key file is schkrewed up:
debug1: identity file /root/.ssh/identity type -1
debug3: Not a RSA1 key file /root/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'

You should generate new keys and use scp to copy the public key over to the distant machine.

Cheers,

Herman

---

### Post by Rhiknow on 2009-02-04
> **HermanAB said:**
> For whatever reason, the key file is schkrewed up:
debug1: identity file /root/.ssh/identity type -1
debug3: Not a RSA1 key file /root/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'

You should generate new keys and use scp to copy the public key over to the distant machine.

Cheers,

Herman

Hi Herman,

Thanks for the message. I can see it's doing something in /root/.ssh/... alright, the problem is, which root is it referring to?! Desktop's, machineA's or machineB's? I never specified root anywhere -- I use user0 on laptop, userA on machineA and userb on machineB. It seems rsnapshot keeps on defaulting to root user? I don't want any backup system running through root! (although I have given userB (i.e. bckp) full passwordless sudo permissions (with huge restriction on the program types they're allowed run).

---

### Post by Rhiknow on 2009-02-04
Problem solved:

It looks for /root/.ssh/id_rsa by default

Need to tell it to look for /home/desktop_user/.ssh/id_rsa

Therefore, add the following line to /etc/rsnapshot.conf:

ssh_args<TAB>-p<SPACE>9999<SPACE>-i<SPACE>/home/hynese/.ssh/id_rsa<SPACE>-vvv

, where -p specifies the port number (9999 is an ssh tunnel direct to machineB), -i is the key (this would default to /root/.ssh otherwise!) and -vvv gives full verbosity on the output (i.e. lots of info/error messages!)

It's amazing what a good night's sleep can do!

---

