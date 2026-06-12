---
title: "problem with ssh login"
date: 2008-04-26
forum: Security
---

### Post by tmilam on 2008-04-26
I used bastille this morning to improve the security of my ubuntu server. It's a great utility and I feel better about the security of my machine, but there's one problem I've encountered since using it...

Remote ssh logins do not work!

I checked my auth.log and something here looks odd to me....

```
vitriol@solstice:~$ sudo cat /var/log/auth.log | grep 'Apr 26 10:41'
Apr 26 10:41:34 solstice sshd[20086]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 26 10:41:34 solstice sshd[20086]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 26 10:41:34 solstice sshd[20086]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 26 10:41:37 solstice sshd[20086]: Accepted password for vitriol from 127.0.0.1 port 59737 ssh2
Apr 26 10:41:37 solstice sshd[20090]: pam_unix(sshd:session): session opened for user vitriol by (uid=0)
Apr 26 10:41:37 solstice sshd[20090]: fatal: setreuid 1000: Resource temporarily unavailable
Apr 26 10:41:37 solstice sshd[20090]: pam_unix(sshd:session): session closed for user vitriol

```

This is what happens when I try to log in via ssh:

```
vitriol@127.0.0.1's password: 
Connection to 127.0.0.1 closed by remote host.
Connection to 127.0.0.1 closed.

```

Any idea what happened and how this can be fixed?

---

### Post by Monicker on 2008-04-26
One way of securing ssh is to use the AllowUsers paramater in sshd_config.  When this is turned on, only specified users are allowed to connect via ssh.

Perhaps Bastille enabled that feature?

---

### Post by kevdog on 2008-04-26
Try to connect with the -vvv (3 v flags) to provide verbose output to give us something more to work with.

---

### Post by tmilam on 2008-04-26
> **Monicker said:**
> One way of securing ssh is to use the AllowUsers paramater in sshd_config.  When this is turned on, only specified users are allowed to connect via ssh.

Perhaps Bastille enabled that feature?

I checked sshd_config and AllowUsers is not present in my configuration file.

Here is the output of ssh with -vvv
```
vitriol@solstice:~$ !ssh
ssh -p 8024 127.0.0.1 -vvv
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 127.0.0.1 [127.0.0.1] port 8024.
debug1: Connection established.
debug1: identity file /home/vitriol/.ssh/identity type -1
debug1: identity file /home/vitriol/.ssh/id_rsa type -1
debug1: identity file /home/vitriol/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1
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
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 533/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: [127.0.0.1]:8024
debug3: put_host_port: [127.0.0.1]:8024
debug3: check_host_in_hostfile: filename /home/vitriol/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 5
debug1: Host '[127.0.0.1]:8024' is known and matches the RSA host key.
debug1: Found key in /home/vitriol/.ssh/known_hosts:5
debug2: bits set: 486/1024
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
debug2: key: /home/vitriol/.ssh/identity ((nil))
debug2: key: /home/vitriol/.ssh/id_rsa ((nil))
debug2: key: /home/vitriol/.ssh/id_dsa ((nil))
debug3: input_userauth_banner

***************************************************************************
                         
Any or all uses of this system and all files on this system may be 
intercepted, monitored, recorded, copied, audited, inspected, and 
disclosed to your employer, to authorized site, government, and law 
enforcement personnel, as well as authorized officials of government 
agencies, both domestic and foreign.  

By using this system, the user consents to such interception, monitoring, 
recording, copying, auditing, inspection, and disclosure at the 
discretion of such personnel or officials.  Unauthorized or improper use 
of this system may result in civil and criminal penalties and 
administrative or disciplinary action, as appropriate. By continuing to 
use this system you indicate your awareness of and consent to these terms 
and conditions of use. LOG OFF IMMEDIATELY if you do not agree to the 
conditions stated in this warning.  

****************************************************************************

debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/vitriol/.ssh/identity
debug3: no such identity: /home/vitriol/.ssh/identity
debug1: Trying private key: /home/vitriol/.ssh/id_rsa
debug3: no such identity: /home/vitriol/.ssh/id_rsa
debug1: Trying private key: /home/vitriol/.ssh/id_dsa
debug3: no such identity: /home/vitriol/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
vitriol@127.0.0.1's password: 
debug3: packet_send2: adding 64 (len 59 padlen 5 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t3 r-1 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host 127.0.0.1: Connection reset by peer
Connection to 127.0.0.1 closed.
debug1: Transferred: stdin 0, stdout 0, stderr 92 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 12402.3
debug1: Exit status -1
vitriol@solstice:~$ 

```

---

### Post by tmilam on 2008-04-26
I just tried reinstalling openssh-server and it's still broken :mad:

---

### Post by Monicker on 2008-04-26
Bump up the logging in sshd_config also. change "LogLevel INFO" to "LogLevel VERBOSE"

---

### Post by tmilam on 2008-04-26
In my original post I included my auth.log and it contained errors regarding PAM.

In /etc/ssh/sshd_config I changed 
```
UsePAM yes
```

to the following:
```
UsePAM no
```

After restarting sshd I'm able to log in and out without problems. I think bastille might have changed certain file permissions which influenced the way PAM interacts with openssh-server.

Hopefully I didn't just open up a security hole by disabling PAM in sshd....but I consider the problem 'solved' now and will mark the forum title post as such. 

Thanks for all of the help!

---

