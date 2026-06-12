---
title: "TTY/SSH logins timing out"
date: 2010-08-28
forum: Server Platforms
---

### Post by James Elliott on 2010-08-28
Hey there,

Have had issues with my 10.4 Server regularly. I believe it's something that I've done wrong in some of the hosts settings or the like. When I try and login to the server, especially on startup, I get messages saying the login attempt timed out after 60 seconds and when I login via ssh it boots me from the connection after about 60 seconds of trying to login.

It's after entering the password so it's something to do with authentication most likely. Any help would be appreciated. I think the issue is with my /etc/hosts file as I said before. Hostname is blackbox and it's only meant to be a local network server.


/etc/hosts file:

```
127.0.0.1       localhost.localdomain localhost
192.168.1.5     blackbox.localdomain blackbox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```/etc/resolv.conf file (added): 
```
nameserver 127.0.0.1
nameserver 192.168.1.5 #localhost
nameserver 192.168.1.1 #router
nameserver xxx.xx.xxx.xx #ISP1
nameserver xxx.xx.xxx.xx #ISP2
domain localdomain

```/etc/log/syslog file:
```
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'T.ARIN.NET/AAAA/IN': 2001:dc3::35#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'W.ARIN.NET/AAAA/IN': 2001:503:a83e::2:30#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'Y.ARIN.NET/AAAA/IN': 2001:503:231d::2:30#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'Z.ARIN.NET/AAAA/IN': 2001:500:13::108#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'Z.ARIN.NET/AAAA/IN': 2001:500:31::108#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving '65.1.168.192.in-addr.arpa/PTR/IN': 2001:500:13::63#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'm3.nstld.com/AAAA/IN': 2001:503:a83e::2:31#53
Aug 28 18:00:29 blackbox named[948]: error (network unreachable) resolving 'm3.nstld.com/AAAA/IN': 2001:503:83eb::2:31#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'T.ARIN.NET/A/IN': 2001:500:3::42#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:503:c27::2:30#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-2.iana.org/A/IN': 2001:503:c27::2:30#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/AAAA/IN': 2001:7fd::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-2.iana.org/AAAA/IN': 2001:7fd::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-2.iana.org/A/IN': 2001:7fd::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:500:b::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:500:e::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:500:40::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:500:c::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-1.iana.org/A/IN': 2001:500:48::1#53
Aug 28 18:00:30 blackbox named[948]: error (network unreachable) resolving 'blackhole-2.iana.org/AAAA/IN': 2001:500:f::1#53
Aug 28 18:00:31 blackbox named[948]: client 127.0.0.1#45155: RFC 1918 response from Internet for 65.1.168.192.in-addr.arpa
```/etc/log/auth.log file:

```
Aug 28 17:59:40 blackbox sshd[1094]: Server listening on :: port 22.
Aug 28 18:00:49 blackbox perl: pam_winbind(webmin:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'root')
Aug 28 18:00:51 blackbox webmin[1069]: Webmin starting

```/etc/log/debug.log file:

```
Aug 28 17:59:39 blackbox sshd[813]: Server listening on 0.0.0.0 port 22.
Aug 28 17:59:39 blackbox sshd[813]: Server listening on :: port 22.
Aug 28 17:59:40 blackbox sshd[813]: Received signal 15; terminating.
Aug 28 17:59:40 blackbox perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Aug 28 17:59:40 blackbox perl: pam_winbind(webmin:auth): getting password (0x00000388)
Aug 28 17:59:40 blackbox perl: pam_winbind(webmin:auth): pam_get_item returned a password
Aug 28 17:59:40 blackbox sshd[1094]: Server listening on 0.0.0.0 port 22.
Aug 28 17:59:40 blackbox sshd[1094]: Server listening on :: port 22.
Aug 28 18:00:49 blackbox perl: pam_winbind(webmin:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'root')
Aug 28 18:00:51 blackbox webmin[1069]: Webmin starting
```/etc/log/kern.log file is attatched.

---

### Post by Toz on 2010-08-28
Try adding:

UseDNS no

to your /etc/ssh/sshd_config file and restarting sshd (sudo /etc/init.d/ssh restart)

or...

adding the source ip (the ip of the computer that you are connecting from) to your /etc/hosts file.

/ToZ

---

### Post by James Elliott on 2010-08-28
> **Toz said:**
> Try adding:

UseDNS no

to your /etc/ssh/sshd_config file and restarting sshd (sudo /etc/init.d/ssh restart)

or...

adding the source ip (the ip of the computer that you are connecting from) to your /etc/hosts file.

/ToZ

I have tried this, it does not seem to resolve my issue. Some additional testing maybe in order for this, however it should be getting that information from the router. Also TTY is doing the same as SSH - I don't think TTY shells require SSH do they?

Thanks for your reply anyway.

Here is my resolv.conf also:

```
nameserver 127.0.0.1
nameserver 192.168.1.5 #localhost
nameserver 192.168.1.1 #router
nameserver xxx.xx.xxx.xx #ISP1
nameserver xxx.xx.xxx.xx #ISP2
domain localdomain

```It looks to me like it has something to do with PAM... attatchd PAM config files to the main post. Turning it off SEEMS to currently fix it.

---

### Post by BkkBonanza on 2010-08-28
Why do you have 127.0.0.1 as a nameserver in your resolv.conf?
Are you running a DNS server on localhost?
From your log messages it appears you have a lot of dns resolution errors. 
Also I see a PAM error listed there to do with winbind. Not sure if that's relevant but seems odd. I'm not familiar with the winbind module.

---

### Post by James Elliott on 2010-08-28
> **BkkBonaza said:**
> Why do you have 127.0.0.1 as a nameserver in your resolv.conf?
Are you running a DNS server on localhost?
From your log messages it appears you have a lot of dns resolution errors. 
Also I see a PAM error listed there to do with winbind. Not sure if that's relevant but seems odd. I'm not familiar with the winbind module.

Winbind is a part of Samba. And BIND9 is running on the localhost as the DNS. I'll try fiddling with those settings a bit in resolv.conf.. it's affecting all PAM authentication (like sudo).

I think I've fixed the issues with name resolution but will see once I rotate the logs and restart the system (BIND9 wasn't forwarding the DNS requests properly). It looks like it's not solved the PAM problem yet, so will take some more digging in the logs I'm guessing.

---

### Post by BkkBonanza on 2010-08-28
Ok. That makes more sense then.

Try using the most verbose option when you ssh.

ssh -vvv ...

Will give you heaps of output about what is happening during the login.
It sounds more likely to be a pam config problem than a hosts/resolv.conf issue.

---

### Post by James Elliott on 2010-08-29
> **BkkBonaza said:**
> Ok. That makes more sense then.

Try using the most verbose option when you ssh.

ssh -vvv ...

Will give you heaps of output about what is happening during the login.
It sounds more likely to be a pam config problem than a hosts/resolv.conf issue.

I'm thinking PAM as well though I'm not very familiar with PAM at all. Here is my SSH output from my login attempt:

 ```
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
  debug1: Reading configuration data /etc/ssh/ssh_config
  debug1: Applying options for *
  debug2: ssh_connect: needpriv 0
  debug1: Connecting to 192.168.1.5 [192.168.1.5] port 22.
  debug1: Connection established.
  debug1: identity file /home/james/.ssh/identity type -1
  debug1: identity file /home/james/.ssh/id_rsa type -1
  debug1: identity file /home/james/.ssh/id_dsa type -1
  debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
  debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
  debug1: Enabling compatibility mode for protocol 2.0
  debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
  debug2: fd 3 setting O_NONBLOCK
  debug1: SSH2_MSG_KEXINIT sent
  debug3: Wrote 792 bytes for a total of 831
  debug1: SSH2_MSG_KEXINIT received
  debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
  debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
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
  debug3: Wrote 24 bytes for a total of 855
  debug2: dh_gen_key: priv key bits set: 126/256
  debug2: bits set: 525/1024
  debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
  debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
  debug3: Wrote 144 bytes for a total of 999
  debug3: check_host_in_hostfile: filename /home/james/.ssh/known_hosts
  debug3: check_host_in_hostfile: match line 5
  debug1: Host '192.168.1.5' is known and matches the RSA host key.
  debug1: Found key in /home/james/.ssh/known_hosts:5
  debug2: bits set: 496/1024
  debug1: ssh_rsa_verify: signature correct
  debug2: kex_derive_keys
  debug2: set_newkeys: mode 1
  debug1: SSH2_MSG_NEWKEYS sent
  debug1: expecting SSH2_MSG_NEWKEYS
  debug3: Wrote 16 bytes for a total of 1015
  debug2: set_newkeys: mode 0
  debug1: SSH2_MSG_NEWKEYS received
  debug1: SSH2_MSG_SERVICE_REQUEST sent
  debug3: Wrote 48 bytes for a total of 1063
  debug2: service_accept: ssh-userauth
  debug1: SSH2_MSG_SERVICE_ACCEPT received
  debug2: key: /home/james/.ssh/identity ((nil))
  debug2: key: /home/james/.ssh/id_rsa ((nil))
  debug2: key: /home/james/.ssh/id_dsa ((nil))
  debug3: Wrote 64 bytes for a total of 1127
  debug1: Authentications that can continue: publickey,password
  debug3: start over, passed a different list publickey,password
  debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
  debug3: authmethod_lookup publickey
  debug3: remaining preferred: keyboard-interactive,password
  debug3: authmethod_is_enabled publickey
  debug1: Next authentication method: publickey
  debug1: Trying private key: /home/james/.ssh/identity
  debug3: no such identity: /home/james/.ssh/identity
  debug1: Trying private key: /home/james/.ssh/id_rsa
  debug3: no such identity: /home/james/.ssh/id_rsa
  debug1: Trying private key: /home/james/.ssh/id_dsa
  debug3: no such identity: /home/james/.ssh/id_dsa
  debug2: we did not send a packet, disable method
  debug3: authmethod_lookup password
  debug3: remaining preferred: ,password
  debug3: authmethod_is_enabled password
  debug1: Next authentication method: password
  james@192.168.1.5's password:
  debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)
  debug2: we sent a password packet, wait for reply
  debug3: Wrote 144 bytes for a total of 1271
  Connection closed by 192.168.1.5
   
```

---

### Post by BkkBonanza on 2010-08-29
That looks typical. It looks like it just doesn't like your password. Not much else disclosed there. I would say either the password is wrong/altered or something in pam is having trouble with it.

If it is using winbind and samba then it may be trying to check the password against a windows (or other machine) domain controller. I'm really not familiar with that stuff. Best I could offer there is to disable/remove Samba for now and see how it behaves. Maybe some misconfiguration in there is affecting how authentication is handled by pam.

---

### Post by .ubik on 2010-08-30
Hello! Just want to say that I'm having the same trouble with TTY logins, but I don't SSH to the server very often so I can't say if it has the same problem there. It takes about 2-3 timed out logins after a server reboot before it will let me in, or i can just wait for ~180 seconds before I attempt login. I haven't found anything in the logs so far that will give me a hint to where the problem is, but I thought it might be dmraid before i saw this post.

---

### Post by abix_adam_pl on 2010-08-30
I had similar problems and in my case the MTU in ethernet was set to 576, and MTU in vpn was set to 1500. Check your network configuration, show output of ifconfig.

Adam

---

### Post by James Elliott on 2010-08-31
My issue was with PAM & Samba, Samba was encouraging PAM to login to the localdomain Domain which was failing. Someone decided to mess with the server and set it up as a Domain Controller.

To fix this I obviuosly went to the Samba configuration and disabled these options (it doesn't need to be a domain controller). Thanks for all the suggestions and help.

My problem is **SOLVED**.

> **.ubik said:**
> Hello! Just want to say that I'm having the same  trouble with TTY logins, but I don't SSH to the server very often so I  can't say if it has the same problem there. It takes about 2-3 timed out  logins after a server reboot before it will let me in, or i can just  wait for ~180 seconds before I attempt login. I haven't found anything  in the logs so far that will give me a hint to where the problem is, but  I thought it might be dmraid before i saw this post.

If your having this problem it could be that Samba is trying to be a Domain Controller (that's not resolving). I'm sure if you've setup Samba to be a Domain Controller you can't connect to the Domain from Windows systems as well. Hence you need to either fix the Domain issue, or just turn those options off in /etc/samba/smb.conf (domain logins = no, domain master = no).

---

### Post by upengan78 on 2010-10-26
Hello James,

I can see that issue is SOLVED for you. I want to thank you for creating this thread. I was lately having exactly the same issue. SSH or console login for local as well as smb/ldap users was not working for like first 8-10 minutes after the system was up. 

System will either boot off either type of users or wait a long time. If I wait for 10-15 minutes and try the login, then it will work right away.

I am running SAMBA and need to run it as domain Master and allow domain logins. That's the whole purpose of this box in my case. 

Issue as rightly pointed out by you seems to PAM. Poking around in /etc/pam.d revealed that both 'login' as well as 'sshd' files @ /etc/pam.d use "@include common-account"

Contents of common-account (before modification)
```
# here are the per-package modules (the "Primary" block)
account    [success=3 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=2 new_authtok_reqd=done default=ignore]    pam_winbind.so 
account    [success=1 default=ignore]    pam_ldap.so 
# here's the fallback if no module succeeds
account    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```I only modified second line in above file,
```
account    [success=2 new_authtok_reqd=done default=ignore]    pam_winbind.so 
```to
```
account    [success=2 new_authtok_reqd=done authinfo_unavail=die]    pam_winbind.so
```rebooted system and tried to login through console /ssh and it works right away, no delays what so ever. 

I agree this may not be the solution to this problem however people having similar environment can definitely consider this procedure if it helps as it can be annoying to wait for 10-15 minutes. :)

Anyone has any suggestions over the PAM config please feel free to reply to this thread.

My system is 10.04 Ubuntu and fully patched.


**EDIT : **

I think what really solved me the issue was not the PAM config but below command. Don't really need to edit PAM configuration.
```
update-rc.d ssh defaults
```Now funny thing is that even though there were no rc scripts for ssh, ssh daemon always started on its own when system was booted. May be it's the way in 10.04 , all services in /etc/init/.. will start by default.

Update-rc command made links, as below 
```
update-rc.d: warning: ssh stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 Adding system startup for /etc/init.d/ssh ...
   /etc/rc0.d/K20ssh -> ../init.d/ssh
   /etc/rc1.d/K20ssh -> ../init.d/ssh
   /etc/rc6.d/K20ssh -> ../init.d/ssh
   /etc/rc2.d/S20ssh -> ../init.d/ssh
   /etc/rc3.d/S20ssh -> ../init.d/ssh
   /etc/rc4.d/S20ssh -> ../init.d/ssh
   /etc/rc5.d/S20ssh -> ../init.d/ssh
```So now I am thinking it is the order in which ldap/ssh/samba(winbind) services get started on ubuntu 10.04

```
/etc/rc2.d# ls -al | egrep 'lapd|ssh|winbind'
lrwxrwxrwx   1 root root   15 2010-08-03 11:58 S19slapd -> ../init.d/slapd
lrwxrwxrwx   1 root root   13 2010-10-26 16:44 S20ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   17 2010-08-02 16:46 S20winbind -> ../init.d/winbind

```
Thanks

---

