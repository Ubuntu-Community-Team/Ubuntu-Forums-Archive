---
title: "ssh server &quot;Permission denied, please try again.&quot;"
date: 2010-02-20
forum: Server Platforms
---

### Post by kr0m3 on 2010-02-20
ok, i'm more than a little frustrated here;

**fresh** install of ubuntu karmic server.
**fresh, vanilla** install of openssh-server
attempt to connect either via standard ssh, linux client or puTTY win32 client system (both on local LAN)
[B][U]
first connect is great. connection established.[/U][/B]
*second* connection (via multiple clients) screams that:
"WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!"
and since I have strict checking, won't let me continue.
so, i do a little
```

rm ~/.ssh/known_hosts

```
to flush it out (i have backups, so what the hell).
then i try again:

i get the typical "Are you sure you want to continue connecting (yes/no)?"
and i say yes.
at which point, i offer the password for the username in question and it flat out refuses:
"Permission denied, please try again."

ok, so i have even gone as far as do a complete rip and replace of the ssh server and it's config files, however this continues to loop and repeat.

so, question one:
Why does my key change?

question two:
Why am i getting "permission denied" errors on subsequent connect

question three:
how the heck do i fix this?

thanks for any input...
~k

---

### Post by laytek on 2010-02-20
Can you post the relevant parts of /var/log/auth.log after you get the permission denied?

LayTek

---

### Post by kr0m3 on 2010-02-20
interesting...

so, i allowed a bit of time to pass (1 hour, maybe) before i came back to my client system to check on this thread (or to atttempt login to the server via ssh)...

i re-attempted to log into the server, because i'm stubborn, i guess, and it actually let me.

ok.  so i 'tail'd my auth.log, here is what i have:

> 
Feb 20 19:45:01 hostname sshd[3584]: pam_unix(sshd:session): session closed for user username
Feb 20 20:10:33 hostname sshd[3506]: pam_unix(sshd:session): session closed for user username
Feb 20 20:17:01 hostname CRON[4981]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 20 20:17:01 hostname CRON[4981]: pam_unix(cron:session): session closed for user root
Feb 20 21:17:01 hostname CRON[4985]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 20 21:17:01 hostname CRON[4985]: pam_unix(cron:session): session closed for user root
Feb 20 21:51:05 hostname sshd[4989]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
Feb 20 21:51:14 hostname sshd[4992]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
Feb 20 21:51:27 hostname sshd[4992]: Accepted password for username from remote_system port 46656 ssh2
Feb 20 21:51:27 hostname sshd[4992]: pam_unix(sshd:session): session opened for user username by (uid=0)



which doesn't seem to detail any logon failures, only successes.
however, it does mention the 'moduli' not existing...related?  wtf?  dunno yet.

i wonder if i have some sort of extended time-out issue?  i log out (or get kicked out, whatever) but the system won't let me back in until that clears?  that doesnt really make any sense though...  i can log into a system 500 times at once if i feel like it... so what the hell?

i also exited cleanly and came back in with no issues this time.
i doubt seriously that this is fixed...just...more complicated.

anyway, thoughts?
~k

---

### Post by cariboo on 2010-02-20
You can see the output of what is happening when you connect to your server by adding a couple of v's to the command:

```
ssh -vv user@server
```

---

### Post by kr0m3 on 2010-02-21
well,
frustratingly enough i can't reproduce the issue just yet.  i logged in this AM successfully, but when it happens again (dare i say "IF"?) i will post the relevant output here.
thanks for the tip...
~k

---

### Post by kr0m3 on 2010-02-21
ok, the plot thins.

it seems as though the ssh server only wants to accept my remote access from any given single system, not from multiple systems.  I have been able to log in all day from system A, but I went to system B and attempted to log in and received the "permission denied" error again.

Not sure what the hell THAT is all about, but i've posted the verbose output below.  

Any help is greatly appreciated
thnx!
~k

```


local_user@local_system:~$ ssh -vvv -l remote_user remote_system
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to remote_system [remote_system] port 22.
debug1: Connection established.
debug1: identity file /home/local_user/.ssh/identity type -1
debug1: identity file /home/local_user/.ssh/id_rsa type -1
debug1: identity file /home/local_user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
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
debug2: dh_gen_key: priv key bits set: 136/256
debug2: bits set: 500/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/local_user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'remote_system' is known and matches the RSA host key.
debug1: Found key in /home/local_user/.ssh/known_hosts:2
debug2: bits set: 508/1024
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
debug2: key: /home/local_user/.ssh/identity ((nil))
debug2: key: /home/local_user/.ssh/id_rsa ((nil))
debug2: key: /home/local_user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/local_user/.ssh/identity
debug3: no such identity: /home/local_user/.ssh/identity
debug1: Trying private key: /home/local_user/.ssh/id_rsa
debug3: no such identity: /home/local_user/.ssh/id_rsa
debug1: Trying private key: /home/local_user/.ssh/id_dsa
debug3: no such identity: /home/local_user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
remote_user@remote_system's password: 
debug3: packet_send2: adding 48 (len 70 padlen 10 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
remote_user@remote_system's password: 
debug3: packet_send2: adding 48 (len 70 padlen 10 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
remote_user@remote_system's password: 
debug3: packet_send2: adding 48 (len 70 padlen 10 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).



```

---

### Post by Iowan on 2010-02-21
> **kr0m3 said:**
> 
```

debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/local_user/.ssh/identity
debug3: no such identity: /home/local_user/.ssh/identity
debug1: Trying private key: /home/local_user/.ssh/id_rsa
debug3: no such identity: /home/local_user/.ssh/id_rsa
debug1: Trying private key: /home/local_user/.ssh/id_dsa
debug3: no such identity: /home/local_user/.ssh/id_dsa
debug2: we did not send a packet, disable method

```

Is "local_user" a valid user (on both systems)?

---

### Post by kr0m3 on 2010-02-21
yes and no.

there are actually three different systems in question, in addition to the server.

in the case of the verbose output above, the user does not.  however, i have received the same error when the user actually existed on both systems.  

thanks for the thought, but i am not aware that the server's user needs to exist remotely in any event...

im still open to ideas though...
~k

---

### Post by kr0m3 on 2010-02-21
and it gets weirder.

i was actually logged in via ssh when my connection died:

> Read from remote host 1.2.3.4: Connection reset by peer
Connection to 1.2.3.4 closed.


and when i attempted to log back in:

> 
WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.


now, i know that the obvious choice is that i have a malicious third party.  i really doubt that is the case for several reasons, not the least of which is that i just stood this server up and it is in a fairly secure environment.  add to that the logon issues that I am having from other client systems within the environment prior to getting this error while working remote and i really see a config issue here.

thoughts?
~k

---

### Post by stlsaint on 2010-02-21
would you feel comfortable posting your sshd_config from the server?
(if so please do). Also i would like to point out that i recommend that you use key authentication unless you plan to connect to the server from multiple clients outside lan. In which just make a really hard password!

---

### Post by kr0m3 on 2010-02-21
ok, i got it figured.
even though it makes me look like a moron, i figured I would post the solution here:

as i mentioned, i have multiple systems in a LAN configuration.  My servers have static IP addressing, my clients are on a separate vlan with DHCP addressing.  Just before I stood up this server, i modified my netchart to make room for the new server...

i duplicated an IP address.  amazing what a little packet trace will do for ya.

so, the ssh connection was a crap-shoot and i was playing havoc with my packet routing... and that was the core issue.  once again, the simple stuff reaches out to bite you.  

thanks for all the assists, peeps.

~k

---

### Post by cariboo on 2010-02-21
Glad to see you figured it out. I've done the same thing, giving two system on the network the same ip address, then spending a couple hours trying to troubleshoot problem.

---

### Post by gorgos on 2010-12-07
I had a similar issue today. All fixes didn't work, so I reinstalled openssh-server and that solved my problem.

---

