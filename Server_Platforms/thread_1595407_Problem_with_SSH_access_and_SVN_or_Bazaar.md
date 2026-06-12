---
title: "Problem with SSH access and SVN or Bazaar"
date: 2010-10-13
forum: Server Platforms
---

### Post by lepre on 2010-10-13
Hi...i have been on this for a while but none seems to work.
I have a server with ssh access and svn on it.
I used it for some time with my user (which can sudo) on svn+ssh://
I was hopeful to enlarge access to 2 of my friends so i setup 2 new users and create a new group and put all our 3 users in it.
Now what i got is that the new users can get in ssh (shell) and sftp for example. But i can't connect with svn. I changed permission on all directories and files of the repository but none is working. I tried to setup a new repo with bazaar and the problem is the same so i guess it's in the ssh tunnel. The onbly one that is working is my username. I don't remember if somehow i added it to some list for ssh. 

If you have any pointer...

```


lepre@lepre:~$ ssh -l troi -v localhost
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/lepre/.ssh/identity type -1
debug1: identity file /home/lepre/.ssh/id_rsa type -1
debug1: identity file /home/lepre/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/lepre/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/lepre/.ssh/identity
debug1: Trying private key: /home/lepre/.ssh/id_rsa
debug1: Trying private key: /home/lepre/.ssh/id_dsa
debug1: Next authentication method: password
troi@localhost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux lepre 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Oct 13 14:49:50 CEST 2010

  System load:  0.01              Temperature:         38 C
  Usage of /:   51.7% of 9.39GB   Processes:           144
  Memory usage: 21%               Users logged in:     1
  Swap usage:   0%                IP address for eth1: 192.168.0.104

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Sat Oct  2 17:31:19 2010 from localhost
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to localhost closed.
Transferred: sent 1744, received 2632 bytes, in 0.7 seconds
Bytes per second: sent 2414.5, received 3643.9
debug1: Exit status 1

```

---

