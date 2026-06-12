---
title: "Can't access server"
date: 2008-12-23
forum: Server Platforms
---

### Post by gmalac on 2008-12-23
I sure changed nothing, certainly not my root password but I know there were updates recently (maybe login...??). Anyway and since this morning, I just can't access my server.

My server is a headless ubuntu-server 8.10 that I access via Putty, I also use Unison and FireFTP

Incredibly enough only FireFTP works (I can ftp the directories...) and that's using my usual id and pwd for root access!!!???!!!. 
I also use it as a LAMP server and I can access BackupPC, Ampache and Gallery2 but either PPHMyadmin nor Webmin though! 

Putty and unison won't work either. I can connect and give my username, but when I input the password I always have the error "Server unexpectedly closed network connection".

I connected keyboard, mouse and monitor to it and when I log in, as soon as I put the password I have an error message about /etc/postfix/main.cf not existing? I am stuck at the TTY login!

I have re-installed (after a complete apt-get remove --purge) both the openssh-server on the server and openssh-client on my desktop.

Any help would be hugely appreciated, thanks!

---

### Post by cariboo on 2008-12-23
The error messages you posted says you have a problem with Postfix, why would you reinstall openssh? If you can login to a terminal, stop Postfix, and see if you can login remotely. To stop postfix as a normal user at the prompt type:

```
sudo /etc/init.d/postfix stop
```

I'm not sure what the exact command is, as I don't have postfix installed, but that is where your problem is.

Jim

---

### Post by HermanAB on 2008-12-23
You can debug SSH problems with:
$ ssh -vvv user@serveripaddress

---

### Post by gmalac on 2008-12-24
> **cariboo907 said:**
> The error messages you posted says you have a problem with Postfix, why would you reinstall openssh? If you can login to a terminal, stop Postfix, and see if you can login remotely. To stop postfix as a normal user at the prompt type:

```
sudo /etc/init.d/postfix stop
```

I'm not sure what the exact command is, as I don't have postfix installed, but that is where your problem is.

Jim

Thank you Cariboo907 for that, problem is I can't log into the system in the first place! So how am I gonna use that command?

---

### Post by gmalac on 2008-12-24
> **HermanAB said:**
> You can debug SSH problems with:
$ ssh -vvv user@serveripaddress

Thank you HermanAB,

I quote the result here below. It's above my competences I'm afraid, don't see error messages though?

On purpose I enter a wrong password the first time. It asked for it again.
But as soon as I enter the wright one, the connection closes!?!

QUOTE:
guy@hp7670-ubuntu:~$ ssh -vvv guy@192.168.0.34
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.34 [192.168.0.34] port 22.
debug1: Connection established.
debug1: identity file /home/guy/.ssh/identity type -1
debug1: identity file /home/guy/.ssh/id_rsa type -1
debug1: identity file /home/guy/.ssh/id_dsa type -1
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
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 991/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/guy/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.0.34' is known and matches the RSA host key.
debug1: Found key in /home/guy/.ssh/known_hosts:1
debug2: bits set: 1000/2048
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
debug2: key: /home/guy/.ssh/identity ((nil))
debug2: key: /home/guy/.ssh/id_rsa ((nil))
debug2: key: /home/guy/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/guy/.ssh/identity
debug3: no such identity: /home/guy/.ssh/identity
debug1: Trying private key: /home/guy/.ssh/id_rsa
debug3: no such identity: /home/guy/.ssh/id_rsa
debug1: Trying private key: /home/guy/.ssh/id_dsa
debug3: no such identity: /home/guy/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
guy@192.168.0.34's password: 
debug3: packet_send2: adding 64 (len 48 padlen 16 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
guy@192.168.0.34's password: 
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
guy@192.168.0.34's password: 
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)
debug2: we sent a password packet, wait for reply
Connection closed by 192.168.0.34
guy@hp7670-ubuntu:~$ 

UNQUOTE:

---

### Post by HermanAB on 2008-12-24
OK, SSH says that your password is wrong.

Reboot and select Single User Mode (no password required in this mode), then change your password with the command:
$ passwd yourusername

Cheers,

Herman

---

### Post by gmalac on 2008-12-24
> **HermanAB said:**
> OK, SSH says that your password is wrong.

Reboot and select Single User Mode (no password required in this mode), then change your password with the command:
$ passwd yourusername

Cheers,

Herman

Thank you very much HermanAB,

Did what you proposed and came up with SEGMENTATION FAULT

Crazy eh?

I am despaired!

---

### Post by freerkkalsbeek on 2008-12-24
> **gmalac said:**
> Thank you very much HermanAB,

Did what you proposed and came up with SEGMENTATION FAULT

Crazy eh?

I am despaired!

If it is possible to boot the system in single user mode, than at least you have options to analyze what went wrong.
Are all filesystems mounted? Any full filesystems?
Check /var/log/syslog etc.
Maybe that will give you a clue.

SSH is running, so that's good. What is the default shell for your normal user?
Maybe add a temporary new user while in single user mode and then try loggin in as that user. This will show if it is related to this specific user, or a general login issue.

Have you been poking around with /etc/pam.d/*

Good luck, I know what you will be doing this Xmas ;)

Freerk

---

### Post by gmalac on 2008-12-25
>>I have a backup of /etc dir. Should I just restore it?<<

Well this one to be excluded. I tried via Backuppc to restore one file only, tar can't create file error!

Quote from auth.log
Dec 25 13:50:01 gateway CRON[4749]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 25 13:50:04 gateway CRON[4749]: pam_unix(cron:session): session closed for user root
Dec 25 13:53:03 gateway sshd[4838]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.33  user=guy
Dec 25 13:53:04 gateway sshd[4838]: Failed password for guy from 192.168.0.33 port 40053 ssh2
Dec 25 14:00:01 gateway CRON[4871]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 25 14:00:03 gateway CRON[4871]: pam_unix(cron:session): session closed for user root
Dec 25 14:09:01 gateway CRON[4985]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 25 14:09:01 gateway CRON[4985]: pam_unix(cron:session): session closed for user root
Dec 25 14:10:01 gateway CRON[5062]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 25 14:10:02 gateway CRON[5062]: pam_unix(cron:session): session closed for user root
UNQUOTE

I just don't know what to do!

---

### Post by gmalac on 2008-12-26
I guess I'll give up. I can't access the server, not an acceptable condition. 
I'll look around for an alternative.
Thanks for your help anyway!

---

