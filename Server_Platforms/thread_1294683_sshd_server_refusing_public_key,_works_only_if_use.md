---
title: "sshd: server refusing public key, works only if user already logged in"
date: 2009-10-18
forum: Server Platforms
---

### Post by hnz_kkk on 2009-10-18
Hello,

I have configured ubuntu server 9.04 and tried to run ssh using public key authentication. I have generated the keys exactly as told by official documentation and moved private key to client side (putty 0.60 on windows). Also appended public key to authorized_keys2 file in ~/.ssh/ . The problem is that public key authentication works only if user of given name is already logged in the server having active session, but if logged out, it always fails with "server refused our key" message coming to the client.

Rights are 700 on ~/.ssh directory and 644 on authorized_keys2 file. Both dir and file have the right user:user as owner.

Any ideas why this setup fails in the logged off situation? I include my sshd_config file (only lines which are uncommented):

Port 2222
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys2
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM no

---

### Post by Lars Noodén on 2009-10-19
> **hnz_kkk said:**
> 
...
PubkeyAuthentication yes
**AuthorizedKeysFile .ssh/authorized_keys2**
IgnoreRhosts yes
...


The public key needs to be in the file names authorized_keys2, which you say you've done. 


Try following the failed login with more verbose feedback from ssh. 

e.g. ssh -v, or -vv or -vvv

Read line by line to see if further clues are given.

---

### Post by niroser on 2009-11-01
Hi,

Did you resolve this issue?
I am experiencing the exact problem.

I've changed the log to DEBUG3 and got the following, does it ring a bell to anybody?

First session:
Nov  1 09:13:51 srvjoss1 sshd[22826]: Failed none for joss from 192.168.0.186 port 54641 ssh2
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug3: mm_request_receive entering
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug3: monitor_read: checking request 21
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug3: mm_answer_keyallowed entering
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug3: mm_answer_keyallowed: key_from_blob: 0xb9491490
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: trying public key file /home/joss/.ssh/authorized_keys
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: restore_uid: 0/0
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: trying public key file /home/joss/.ssh/authorized_keys
Nov  1 09:13:51 srvjoss1 sshd[22826]: debug1: restore_uid: 0/0
Nov  1 09:13:51 srvjoss1 sshd[22826]: Failed publickey for joss from 192.168.0.186 port 54641 ssh2



Second session (while the first is still connected):
Nov  1 09:17:48 srvjoss1 sshd[22905]: Failed none for joss from 192.168.0.186 port 54642 ssh2
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_receive entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: monitor_read: checking request 21
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed: key_from_blob: 0xb8d89490
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: trying public key file /home/joss/.ssh/authorized_keys
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: fd 4 clearing O_NONBLOCK
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: checking '/home/joss/.ssh'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: checking '/home/joss'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: terminating check at '/home/joss'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: matching key found: file /home/joss/.ssh/authorized_keys, line 1
Nov  1 09:17:48 srvjoss1 sshd[22905]: Found matching RSA key: 7f:ed:87:8b:ad:f2:67:67:f7:62:5c:60:fc:e9:7e:fd
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: restore_uid: 0/0
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed: key 0xb8d89490 is allowed
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_send entering: type 22
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_receive entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: monitor_read: checking request 21
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed: key_from_blob: 0xb8d90b48
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: trying public key file /home/joss/.ssh/authorized_keys
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: fd 4 clearing O_NONBLOCK
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: checking '/home/joss/.ssh'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: checking '/home/joss'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: secure_filename: terminating check at '/home/joss'
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: matching key found: file /home/joss/.ssh/authorized_keys, line 1
Nov  1 09:17:48 srvjoss1 sshd[22905]: Found matching RSA key: 7f:ed:87:8b:ad:f2:67:67:f7:62:5c:60:fc:e9:7e:fd
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: restore_uid: 0/0
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyallowed: key 0xb8d90b48 is allowed
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_send entering: type 22
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_receive entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: monitor_read: checking request 23
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: ssh_rsa_verify: signature correct
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_answer_keyverify: key 0xb8d92930 signature verified
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_send entering: type 24
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_receive_expect entering: type 49
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_receive entering
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug1: do_pam_account: called
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: PAM: do_pam_account pam_acct_mgmt = 0 (Success)
Nov  1 09:17:48 srvjoss1 sshd[22905]: debug3: mm_request_send entering: type 50
Nov  1 09:17:48 srvjoss1 sshd[22905]: Accepted publickey for joss from 192.168.0.186 port 54642 ssh2

---

### Post by niroser on 2009-11-01
Hi,

Finally I know what is the issue.

my /home/user dir is encrypted and therefore ssh wasn't able to access it unless I am logged in.


at the moment I've moved the .ssh dir to a different location, although I wonder if someone have a solution for this.

---

