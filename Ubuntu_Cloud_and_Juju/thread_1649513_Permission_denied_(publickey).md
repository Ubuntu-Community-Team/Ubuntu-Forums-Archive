---
title: "Permission denied (publickey)"
date: 2010-12-20
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2010-12-20
I'm running a UEC base on 10.10.  The problem I'm having seems similar to others in the forum but so far I've been unable to resolve.  All looks good up until I try ssh'ng into a running instance.  Help would be appreciated, I have a feeling it's something simple.

Thanks in advance....

[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ pwd
/home/hoot/.euca
[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ euca-add-keypair mykey > mykey.priv
[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ chmod 600 mykey.priv 
[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ euca-run-instances emi-DD661064 -k mykey -t c1.medium
RESERVATION    r-260604A2    admin    admin-default
INSTANCE    i-549D09F2    emi-DD661064    0.0.0.0    0.0.0.0    pending    mykey    0        c1.medium    2010-12-20T15:36:27.466Z    atgcloud    eki-F36110CF    eri-07CB113B

[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ euca-describe-instances 
RESERVATION    r-260604A2    admin    default
INSTANCE    i-549D09F2    emi-DD661064    172.16.230.201    172.19.1.2    running    mykey    0        c1.medium    2010-12-20T15:36:27.466Z    atgcloud    eki-F36110CF    eri-07CB113B
RESERVATION    r-56820A22    admin    default
INSTANCE    i-4C5908FC    emi-DE301060    172.16.230.201    172.19.1.2    terminated    mykey    0        m1.small    2010-12-20T15:02:19.773Z    atgcloud    eki-F46610DD    eri-08DB114D

[EMAIL="hoot@cloud-master:%7E/.euca"]hoot@cloud-master:~/.euca[/EMAIL]$ ssh -vvv -i mykey.priv hoot@172.19.1.2
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 172.19.1.2 [172.19.1.2] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file mykey.priv.
debug3: key_read: missing whitespace
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
debug1: identity file mykey.priv type -1
debug1: identity file mykey.priv-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
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
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 108/256
debug2: bits set: 517/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host 172.19.1.2 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host 172.19.1.2
debug3: check_host_in_hostfile: host 172.19.1.2 filename /home/hoot/.ssh/known_hosts2
debug3: check_host_in_hostfile: host 172.19.1.2 filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: host 172.19.1.2 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: host 172.19.1.2 filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host 172.19.1.2
The authenticity of host '172.19.1.2 (172.19.1.2)' can't be established.
RSA key fingerprint is 4c:32:b6:d3:b6:27:0a:33:c2:b8:34:8f:ad:29:90:c3.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '172.19.1.2' (RSA) to the list of known hosts.
debug2: bits set: 501/1024
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
debug2: key: mykey.priv ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: mykey.priv
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by raymdt on 2010-12-20
Hey oldhoot,

1- Are you using images from ubuntu store?
    If yes, then try this to ssh into the instance

```


rm -rf ~/.ssh/known_hosts
ssh -i mykey.priv  **ubuntu**@172.19.***.***

```

2- Use the command  euca-get-console-output  i-*****  to check if there was some problems during instance startup

Regards

---

### Post by oldhoot on 2010-12-21
That was it, using ubuntu as user name.

Thank you!

---

### Post by raymdt on 2010-12-21
Nice to hear that everything is ok ;)

---

### Post by oldhoot on 2010-12-21
I seem to have spoken to soon.  There is something intermittent about my setup.  I've logged in twice with ubuntu as the user name but now I seem to be broken again as in getting the "Permission denied (publickey)."

---

### Post by raymdt on 2010-12-22
Hey,

you can terminate the instance or try again.

---

### Post by raymdt on 2010-12-22
Hey,

you can terminate the instance  or reboot it and try again.

---

### Post by Rusty au Lait on 2010-12-23
Remember. Each time you log into a new instance (even the same image) you re-create the keys on the instance. You must delete the original key from your known_keys file in the .ssh subdirectory. The key was created when you first logged into the original instance. raymdt suggestion to delete the entire file works (and it sounds like it worked for you), but I have several keys in the file I would like to keep. Using raymdt's login, if the problem is the keys then the failed login would tell you which line in the known_hosts file needs to be removed.

---

### Post by raymdt on 2010-12-23
Hi Rusty,
you're right ;)
He can delete the entire file if he works on a testsystem (What i suppose)
:)

---

### Post by Rusty au Lait on 2010-12-23
oldhoot

I found this link. At the bottom it mentions failures because the system they built the image on was encrypted.

[https://help.ubuntu.com/community/UEC/CreateYourImage](https://help.ubuntu.com/community/UEC/CreateYourImage)

Hi, raymdt

---

### Post by mcanonic on 2011-01-26
I had the same problem, and rebooting the machine and remove known_keys file did help me. Then, I found this thread:
[http://open.eucalyptus.com/forum/ubuntu-ec2-image-karmic-cant-ssh-permission-denied-publickey](http://open.eucalyptus.com/forum/ubuntu-ec2-image-karmic-cant-ssh-permission-denied-publickey)
where is suggested to add a line on eucalyptus-cc.conf file, and now it works.

Am I wordering if it is planned to include this new line in the next UEC release, since it seems a bug.

Thanks,
 Massimo

---

