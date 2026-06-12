---
title: "ssh key login not working on new server"
date: 2008-06-18
forum: Server Platforms
---

### Post by chamstar on 2008-06-18
I have previously setup public/private key login on my server (Ubuntu) and it works great. I recently got access to a new server (Ubuntu) but I only get password login. I am using on Ubuntu client side.

I have copied up my public key and added it to ~/.ssh/authorized_keys

I have a co-worker who logins in with Putty on Windows and his key works fine.

Below is the verbose output of ssh client (I've masked the username and domain to protect the innocent!):

USERNAME@kun:~/Desktop$ ssh -v cmb
OpenSSH_4.3p2 Debian-8ubuntu1.4, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /home/USERNAME/.ssh/config
debug1: Applying options for cmb
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to DOMAIN [IPADDRESS] port 22.
debug1: Connection established.
debug1: identity file /home/USERNAME/.ssh/identity type -1
debug1: identity file /home/USERNAME/.ssh/id_rsa type 1
debug1: identity file /home/USERNAME/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.1
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.4
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'DOMAIN' is known and matches the RSA host key.
debug1: Found key in /home/USERNAME/.ssh/known_hosts:42
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/USERNAME/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/USERNAME/.ssh/identity
debug1: Trying private key: /home/USERNAME/.ssh/id_dsa
debug1: Next authentication method: password
USERNAME@DOMAIN's password: 


Any help would be great, Cham.

---

### Post by HalPomeranz on 2008-06-18
The first thing to check is the permissions on your homedir, ~/.ssh dir, and
authorized_keys file on the remote system.  Make sure neither directory is group/world writable.  Make sure the authorized_keys file is mode 600 (this is more restrictive than you need, but still a good idea).

Failing that, it may you generated your key before the Debian OpenSSH vulnerability debacle, and your key may be being blacklisted by the remote server.  Make sure you've updated your SSH packages on your local system and make a new key.  For more info see:  [http://ubuntuforums.org/showthread.php?t=793517](http://ubuntuforums.org/showthread.php?t=793517)

---

### Post by chamstar on 2008-06-19
Thanks for the reply, I checked the permissions and they seem okay.

The .ssh directories on the server are both drwx------

Also the authorized_keys permissions are the same on both servers:

Non-working server:
-rw------- 1 cham cham  780 Jun 18 13:31 authorized_keys

Working server:
-rw------- 1 cham users  390 Jun 21  2007 authorized_keys

The only difference being the group, I changed the group to be users but it had no effect.

Any ideas as to what else I can check?

Thanks again, Cham.

---

### Post by chamstar on 2008-06-19
Okay this was due to a comprised key. I used the ssh-vulnkey to confirm this... I had to install 'openssh-blacklist' before running ssh-vulnkey. I generated a new key and uploaded to the server and all is good again.

By the way if your connecting from a desktop I highly recommend Seahorse to generate and manage your keys.

Cheers Cham.

---

