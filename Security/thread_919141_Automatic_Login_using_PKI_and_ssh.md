---
title: "Automatic Login using PKI and ssh"
date: 2008-09-13
forum: Security
---

### Post by bruparel on 2008-09-13
I am maintaining a Ruby on Rails applications and am responsible for four Ubuntu boxes: 2 staging for US and UK and 2 production for  US and UK.  I have set up PKI login by generating the public and private keys for my client machine (also an Ubuntu laptop) and copying (appending really) the public key to the .ssh/authorized_keys file on all the four servers.  It works fine on the three machines, i.e., I can get in without being asked for a password since I chose not to supply a password while creating keys.  On the fourth machine though, I am asked for the password even though I have copied the public key just like other three servers.  The servers are running Ubuntu 6.06 and my laptop has Ubuntu 7.10.
Any ideas on how to fix this would be most appreciated since I am in and out of the servers a lot and it is quite convenient not to have to type in the password.
Thanks.
Bharat

---

### Post by bruparel on 2008-09-13
I ran the ssh login command to log into remote system with the verbose (debug) flag as follows:

$ ssh -v username@remoteservername

I compared both this both on failing server and passing servers.  Here is the snippet of output where I get the failure:

debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/bruparel/.ssh/identity
debug1: Offering public key: /home/bruparel/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password

So the remote server fails to accept my public key whereas on the servers where it is successful, I see the following output:

debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/bruparel/.ssh/identity
debug1: Offering public key: /home/bruparel/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).

I do not know why the server is refusing to successfully decode the public key on the failing server.  I have compared the /etc/ssh/sshd_config files on both servers and they are identical.

---

