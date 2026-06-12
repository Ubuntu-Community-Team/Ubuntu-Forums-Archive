---
title: "UEC SSH Permission denied (public key.)"
date: 2011-02-12
forum: Server Platforms
---

### Post by mdenhartog on 2011-02-12
Hi all, 

I have setup a Ubuntu Enterprise Cloud with version 10.10. I have already seen a lot of threads regarding same problem and I have already tried a lot to solve it but so far no solution yet.

I installed the Enterprise Cloud with the help of [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) The cloud is running fine and I downloaded the image Ubuntu 9.10 - Karmic Koala (amd64) from the store. I am able to run this image but I can't ssh to the image. 

The output I have from ssh is :

OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.180 [192.168.0.180] port 22.
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
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
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
debug2: dh_gen_key: priv key bits set: 151/256
debug2: bits set: 536/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host 192.168.0.180 filename /home/cloudadmin/.ssh/known_hosts
debug3: check_host_in_hostfile: host 192.168.0.180 filename /home/cloudadmin/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.0.180' is known and matches the RSA host key.
debug1: Found key in /home/cloudadmin/.ssh/known_hosts:1
debug2: bits set: 485/1024
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

The lines that below I don't understand. I created mykey.priv as described in the UEC CDInstall manual but I think it is the reason why I am not able to connect but I am not sure of that

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

I have checked my .ssh permissions and these seems oke. 

Does anyone have an idea how to solve this problem because I am :confused:

Thanks

---

### Post by slimjim1520 on 2011-02-12
When you too change the password of the user 'eucalyptus' on the computer you are trying to connect to. exchange keys and then change it again.

check out
[http://cssoss.files.wordpress.com/2010/11/eucalyptus-beginners-guide-uec-edition1-1.pdf]("http://cssoss.wordpress.com/2010/11/11/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-10-10-eucalyptus-2-0-image-management/")

this helped me alot when testing eucalyptus.

*edity changed link

---

### Post by hawkmage on 2011-02-12
What does your private and public key look like is it like this:

Private Key:
```
-----BEGIN RSA PRIVATE KEY-----
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
-----END RSA PRIVATE KEY-----
```

And the Public Key:
```
ssh-rsa XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX user@host
```

---

### Post by mdenhartog on 2011-02-13
Hi Hawkmage,

Yes my keys looks like you have posted. I am confused why ssh tells me that it isn't a real RSA key.

Marco

---

### Post by CharlesA on 2011-02-13
Are you telling ssh what key to use when connecting?

Try this:

```
ssh -i /path/to/privatekey user@host
```

If that doesn't work, try generating the key again with this:

```
ssh-keygen
```

---

### Post by mdenhartog on 2011-02-13
Hi all,

Yes my keys looks like you have posted. I am confused why ssh tells me that it isn't a real RSA key.

In the nc.log on the node I find this line :

[Sun Feb 13 20:02:57 2011][006957][EUCAINFO  ] adding key/tmp/sckey.Q5K68n to the root file system at /var/lib/eucalyptus/instances//admin/i-4286081B/disk using (//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap)
[Sun Feb 13 20:02:57 2011][006957][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap 32256 /var/lib/eucalyptus/instances//admin/i-4286081B/disk /tmp/sckey.Q5K68n]

It looks like my key is automatically injected in the image from the store (as expected)

In my console output of the running instance I see the following output :

 * Setting preliminary keymap...                                                ec2: Generating public/private rsa key pair.
ec2: Your identification has been saved in /etc/ssh/ssh_host_rsa_key.
ec2: Your public key has been saved in /etc/ssh/ssh_host_rsa_key.pub.
ec2: The key fingerprint is:
ec2: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ec2: The key's randomart image is:
ec2: +--[ RSA 2048]----+
ec2: |            .    |
ec2: |           . .   |
ec2: |          . .    |
ec2: |     . . . . .   |
ec2: |    + + S E o .  |
ec2: |   . + + . @ .   |
ec2: |    . o . o +    |
ec2: |     . .   . =   |
ec2: |            =    |
ec2: +-----------------+
ec2: Generating public/private dsa key pair.
ec2: Your identification has been saved in /etc/ssh/ssh_host_dsa_key.
ec2: Your public key has been saved in /etc/ssh/ssh_host_dsa_key.pub.
ec2: The key fingerprint is:
ec2: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ec2: The key's randomart image is:
ec2: +--[ DSA 1024]----+
ec2: |         . .o    |
ec2: |      . o... o   |
ec2: |     o + .+ o    |
ec2: |    o  +E .*     |
ec2: |     o.+Soo o    |
ec2: |    . .. . .     |
ec2: |        +        |
ec2: |       . .       |
ec2: |                 |
ec2: +-----------------+
ec2:
ec2:
ec2: #############################################################
ec2: -----BEGIN SSH HOST KEY FINGERPRINTS-----
ec2: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ec2: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ec2: -----END SSH HOST KEY FINGERPRINTS-----
ec2: #############################################################

Everything tells me that it should work but damn it don't and I can't get my fingers on it.

@CharlesA yes I am telling ssh what key to use.
ssh -i ~/.euca/mykey.priv [email]ubuntu@xxx.xxx.xxx.xxx[/email]

That should do the trick for an image from the UEC store.


Marco

---

### Post by BradBrand on 2011-05-12
I had the same problem, and suspecting it was a problem with the keypair exchange, I de-registered the node and re-registered it.

# euca_conf --deregister-nodes 192.168.1.130
# euca_conf --register-nodes 192.168.1.130

I also re-ran euca_conf --setup, although that was probably unnecessary.

I then re-ran euca-run-instances and ssh -i ~/.euca/mykey.priv ubuntu@192.168.1.222 worked for me.

Take care,
brad

---

### Post by hedge.hog on 2012-01-30
@mdenhartog,

To avoid this error, you should `chmod 0600 /path/to/key.pem`

HTH?

---

