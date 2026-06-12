---
title: "upgrade on remote server to hardy broke scp."
date: 2008-06-13
forum: Server Platforms
---

### Post by wbrown on 2008-06-13
Greetings: 

In a cron job, I do a daily file backup from my TheLocalHost server to a remote server using the scp command.  The remote server was upgraded to hardy 8.04 and TheLocalHost server is running 7.04.  After the upgrade the file copy stopped working.  It turns out that I can still scp from the remote server to the local server.  Here is  some debug info I am hoping that might help someone on this forum help me troubleshoot a little further


When I run scp -v from  the remote server to the local server it works: 

bill@remote:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04.1
Codename:       hardy
bill@remote:~$ scp -v id_rsa.pub root@TheLocalHost:
Executing: program /usr/bin/ssh host TheLocalHost, user root, command scp -v -t .
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to TheLocalHost [TheLocalHost] port 22.
debug1: Connection established.
debug1: identity file /home/bill/.ssh/identity type -1
debug1: identity file /home/bill/.ssh/id_rsa type 1
debug1: identity file /home/bill/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.3p2 Debian-8ubuntu
1.4
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '208.70.151.57' is known and matches the RSA host key.
debug1: Found key in /home/bill/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/bill/.ssh/identity
debug1: Offering public key: /home/bill/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /home/bill/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: password
root@TheLocalHost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
[B]debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -t .
Sending file modes: C0644 394 id_rsa.pub
Sink: C0644 394 id_rsa.pub
id_rsa.pub                                              100%  394     0.4KB/s   00:00
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0[/B]
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.4 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0
bill@remote:~$


When I run scp -v from  the TheLocalHost server to the remote server it doesn't work: 

[email]root@TheLocalHost:/etc/cron.dail[/email]y# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
[email]root@TheLocalHost:/etc/cron.dail[/email]y# scp -v sa_rules_update.sh bill@remote:
Executing: program /usr/bin/ssh host remote, user bill, command scp -v -t
 .
OpenSSH_4.3p2 Debian-8ubuntu1.4, OpenSSL 0.9.8c 05 Sep 2006
debug1: Connecting to remote [remote] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1
.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'billbrown.homelinux.net' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
[B]debug1: Entering interactive session.
debug1: Sending command: scp -v -t .
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
bash: scp: command not found[/B]
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 127
lost connection
[email]root@remote:/etc/cron.dail[/email]y#


I do notice in the version that works, it looks like the /etc/environment is being utilized which adds the path.  I am not sure how to make this happen in the TheLocalHost version.  

Might anyone on this forum have some suggestion on what I should try next to fix this?  Should I try to load a different version of scp on the remote or TheLocalHost server?    

As a temporary workaround suggestion I received from a colleague, I have to use scp on the remote machine to pull the file from TheLocalHost server.   

Thanks for you help. 
Bill

---

