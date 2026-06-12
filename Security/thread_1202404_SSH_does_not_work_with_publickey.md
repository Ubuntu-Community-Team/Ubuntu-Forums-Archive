---
title: "SSH does not work with publickey"
date: 2009-07-02
forum: Security
---

### Post by Shungo73 on 2009-07-02
Hi guys,

i have installed Ubuntustudio 9.04 on my computer which works usually pretty fine, unless SSH.

SSH won't be able to establish a connection to our server with a key.

Error message: 

Agent admitted failure to sign using the key.
Permission denied (publickey).


When using the same key on Ubuntustudio 8.04 it is working pretty fine, SSH can be establish to the same server.


Does anybody know what is wrong here???

Thanks in advance
Shungo

---

### Post by HermanAB on 2009-07-02
ssh -vvv user@server

---

### Post by Shungo73 on 2009-07-03
Hi Hermann,

here is the requested output. I really wonder why it does not work on this platform as they key is working pretty fine with Ubuntustudio 8.04 and also on Windows with SecureCRT and so on, but not Ubuntustudio 9.04

Many thanks, hope you can tell me what's wrong here.

Bye
Shungo


```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to worker.de.colt.net [217.110.35.27] port 22.
debug1: Connection established.
debug1: identity file /home/ddietz/.ssh/identity type -1
debug1: identity file /home/ddietz/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/ddietz/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/ddietz/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1 Debian-8.sarge.6
debug1: match: OpenSSH_3.8.1p1 Debian-8.sarge.6 pat OpenSSH_3.*
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
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
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 520/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'worker.de.colt.net' is known and matches the DSA host key.
debug1: Found key in /home/ddietz/.ssh/known_hosts:1
debug2: bits set: 519/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ddietz/.ssh/id_dsa (0xb9263898)
debug2: key: /home/ddietz/.ssh/identity ((nil))
debug2: key: /home/ddietz/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/ddietz/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-dss blen 434
debug2: input_userauth_pk_ok: fp 4d:5e:b9:29:bb:3c:5e:ef:ea:a9:3b:a0:62:e9:eb:6f
debug3: sign_and_send_pubkey
Agent admitted failure to sign using the key.
debug1: Trying private key: /home/ddietz/.ssh/identity
debug3: no such identity: /home/ddietz/.ssh/identity
debug1: Trying private key: /home/ddietz/.ssh/id_rsa
debug3: no such identity: /home/ddietz/.ssh/id_rsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
ddietz@test:~$ 

```

---

### Post by Shungo73 on 2009-07-03
and that's the logging on Ubuntustudio 8.04


```
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to worker.de.colt.net [217.110.35.27] port 22.
debug1: Connection established.
debug1: identity file /home/ddietz/.ssh/identity type -1
debug1: identity file /home/ddietz/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/ddietz/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/ddietz/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1 Debian-8.sarge.6
debug1: match: OpenSSH_3.8.1p1 Debian-8.sarge.6 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
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
debug2: dh_gen_key: priv key bits set: 141/256
debug2: bits set: 527/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host worker.de.colt.net
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /home/ddietz/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 1 for host worker.de.colt.net
The authenticity of host 'worker.de.colt.net (217.110.35.27)' can't be established.
DSA key fingerprint is bd:d3:03:59:be:a3:ea:d3:52:d7:e8:42:3f:7f:10:9a.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'worker.de.colt.net' (DSA) to the list of known hosts.
debug2: bits set: 518/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ddietz/.ssh/id_dsa (0xb8391820)
debug2: key: /home/ddietz/.ssh/identity ((nil))
debug2: key: /home/ddietz/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/ddietz/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-dss blen 434
debug2: input_userauth_pk_ok: fp 4d:5e:b9:29:bb:3c:5e:ef:ea:a9:3b:a0:62:e9:eb:6f
debug3: sign_and_send_pubkey
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = de_DE.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug3: Ignored env OLDPWD
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 131072
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
```

---

### Post by HermanAB on 2009-07-03
Howdy,

I would generate a new key pair on the client and upload the public key to the server since it complains about the key file format white space, so something is corrupted in there.  Don't re-use keys since it makes it hard to revoke them.

You can also run the ssh daemon with debug enabled for more information:
# killall sshd
# sshd -d

Then when you try to log in, it will spit out some info as to what is happening.  Of course to do that you need to have the two machines right next to each other.

---

### Post by bodhi.zazen on 2009-07-03
It appears your key is corrupt.

Open the key and make sure it is in the proper format.

The key should be all on one line.

If the private key is OK, then check the public key (on the server), in 

~/.ssh/authorized_keys

---

### Post by Mister.Vash on 2009-07-04
The keys are not corrupted - what the ssh client does initially is to first check to see if it is an RSA key, which works with SSH Protocol 1 and Protocol 2, and if it is not an RSA key, it then checks to see if it is a DSA key which is SSH  Protocol 2 only.  The initial messages from the verbose logging are only indicating that it is not an RSA key and the logs later indicate that it does correctly see it as a DSA key. Which is this line:
> debug1: identity file /home/ddietz/.ssh/id_dsa **type 2**


The actual error that is it spitting back on the failed one is this line:
> Agent admitted failure to sign using the key.

I would recommend trying the solution in this launchpad bug thread and see if that works for you:
[https://bugs.launchpad.net/ubuntu/%2Bsource/openssh/%2Bbug/201786](https://bugs.launchpad.net/ubuntu/%2Bsource/openssh/%2Bbug/201786)

Regards

---

### Post by Shungo73 on 2009-07-06
Hi All,

i could solve the issue by typing "ssh-add" first so the ssh agent asked me for the passphrase and stored it. Anytime i will now log into the server it works without asking for the passphrase, untill a reboot of my pc.

Thanks
Shungo

---

### Post by xealitz on 2011-12-24
> **Shungo73 said:**
> 
Error message: 

Agent admitted failure to sign using the key.
Permission denied (publickey).


I had been receiving the same error on Ubuntu 10.10
(OpenSSH_5.5p1 Debian-4ubuntu6, OpenSSL 0.9.8o 01 Jun 2010)
and this pal's advi&#1089;e helped me:
[http://www.baptiste-wicht.com/2010/07/tip-how-to-solve-agent-admitted-failure-to-sign-using-the-key-error/](http://www.baptiste-wicht.com/2010/07/tip-how-to-solve-agent-admitted-failure-to-sign-using-the-key-error/)

**Logout and login again - that's all advise.**

Hope it'll help somebody. (and hope it's better to have the tip in this thread)

PS just as in the "IT crowd" :)

---

