---
title: "cant scp with server shell  /bin/rssh , but can with /bin/sh"
date: 2011-04-08
forum: Server Platforms
---

### Post by pdc124 on 2011-04-08
Ime setting up rssh to automatically rsync backup  stuff from my hosting server 
Ive added a user , and given them a home directory 
ive installed rssh
ive setup public/private key authentication 

Im testing it from within my LAN 

when the server shell is /bin/sh , passwordless scp file tansfer works, but when the shell is /bin/rssh , it asks me for a password

> $ cat /etc/rssh.conf | grep -v '#'
logfacility = LOG_USER 
allowscp
allowrsync
umask = 022
if the server config is this 

> $ cat /etc/passwd | grep remot
remoteBackup:x:1004:1003::/home/remoteBackup:/bin/sh
server2@server2:~$ 
i can 
> nine@nine:~$ scp -P22 -i /tmp/rem_b_id_rsa /tmp/file remoteBackup@server:/home/remoteBackup
file                                                                                  100%    7     0.0KB/s   00:00    
nine@nine:~$ 
if i change it to 
> $ cat /etc/passwd | grep remot
remoteBackup:x:1004:1003::/home/remoteBackup:/bin/rssh
server2@server2:~$ 
I get 
> nine@nine:~$ scp -P22 -v -i /tmp/rem_b_id_rsa /tmp/file remoteBackup@server2:/home/remoteBackup
Executing: program /usr/bin/ssh host server2, user remoteBackup, command scp -v -t /home/remoteBackup
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Applying options for server2
debug1: Connecting to server2 [192.168.2.20] port 22.
debug1: Connection established.
debug1: identity file /tmp/rem_b_id_rsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu5
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server2' is known and matches the RSA host key.
debug1: Found key in /home/nine/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: [email]nine@nine.home.nw[/email]
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /tmp/rem_b_id_rsa
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
remoteBackup@server2's password: 



where is the problem ?

---

