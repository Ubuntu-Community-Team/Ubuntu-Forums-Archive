---
title: "SCP problems"
date: 2010-03-01
forum: Server Platforms
---

### Post by kell05 on 2010-03-01
I have a sheevaplug and I am having a problem using scp to send files to it.  Sheeaplugs have a root user and for some reason I am only able to send files to root but not as anyother user.  Here is the verbose output from both runs:


First the unsuccessful version

scp -vp crontab_backup.txt james@192.168.0.60:~  > out1.txt
Executing: program /usr/bin/ssh host 192.168.0.60, user james, command scp -v -p -t ~
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.60 [192.168.0.60] port 22.
debug1: Connection established.
debug1: identity file /home/james/.ssh/identity type -1
debug1: identity file /home/james/.ssh/id_rsa type -1
debug1: identity file /home/james/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
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
debug1: Host '192.168.0.60' is known and matches the RSA host key.
debug1: Found key in /home/james/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/james/.ssh/identity
debug1: Trying private key: /home/james/.ssh/id_rsa
debug1: Trying private key: /home/james/.ssh/id_dsa
debug1: Next authentication method: password
james@192.168.0.60's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug1: Sending command: scp -v -p -t ~
           _ 
james@james-desktop:~$ debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0


second  successful version

scp -vp crontab_backup.txt root@192.168.0.60:~ 
Executing: program /usr/bin/ssh host 192.168.0.60, user root, command scp -v -p -t ~
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.60 [192.168.0.60] port 22.
debug1: Connection established.
debug1: identity file /home/james/.ssh/identity type -1
debug1: identity file /home/james/.ssh/id_rsa type -1
debug1: identity file /home/james/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
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
debug1: Host '192.168.0.60' is known and matches the RSA host key.
debug1: Found key in /home/james/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/james/.ssh/identity
debug1: Trying private key: /home/james/.ssh/id_rsa
debug1: Trying private key: /home/james/.ssh/id_dsa
debug1: Next authentication method: password
root@192.168.0.60's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug1: Sending command: scp -v -p -t ~
Sink: T1264464906 0 1267469698 0
Sending file modes: C0644 98 crontab_backup.txt
Sink: C0644 98 crontab_backup.txt
crontab_backup.txt                                                                                       100%   98     0.1KB/s   00:00    
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0

I am at a loss at why this is happening, especially the underscore at the unsuccessful attempt where the files should be sent.

---

### Post by kewlrichie on 2010-03-02
I'm not 100% on this one but I would try not to use the ~ for the home dir try using the full path like 
scp -vp crontab_backup.txt james@192.168.0.60:/home/james and see if that works

hmm I just realized that you used the same command for root also and it worked but are you root on the first box the files are coming from ? I would still try the full path and see what happens

---

