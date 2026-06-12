---
title: "ssh access to vm instance problem"
date: 2011-05-04
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-04
cloud@node:~$ cd /home/cloud/.euca/
[email]cloud@node:~/.euca[/email]$ . eucarc
[email]cloud@node:~/.euca[/email]$ euca-describe-availability-zones verbose
AVAILABILITYZONE    cluster1    10.1.1.222
AVAILABILITYZONE    |- vm types    free / max   cpu   ram  disk
AVAILABILITYZONE    |- m1.small    0002 / 0002   1    192     2
AVAILABILITYZONE    |- c1.medium    0002 / 0002   1    256     5
AVAILABILITYZONE    |- m1.large    0001 / 0001   2    512    10
AVAILABILITYZONE    |- m1.xlarge    0001 / 0001   2   1024    20
AVAILABILITYZONE    |- c1.xlarge    0000 / 0000   4   2048    20
[email]cloud@node:~/.euca[/email]$ euca-describe-images
IMAGE    eki-6E341ABC    lucid-20110421182259/lucid-server-uec-i386-vmlinuz-virtual.manifest.xml    admin    available    public        i386    kernel        
IMAGE    emi-210F15BA    lucid-20110421182259/lucid-server-uec-i386.img.manifest.xml    admin    available    public        i386    machine    eki-6E341ABC    
[email]cloud@node:~/.euca[/email]$ euca-run-instances emi-210F15BA -k mykey -t m1.large 
RESERVATION    r-454207A7    admin    admin-default
INSTANCE    i-4B5B08C0    emi-210F15BA    0.0.0.0    0.0.0.0    pending    mykey    0        m1.large    2011-05-04T09:06:23.194Z    cluster1    eki-6E341ABC    
[email]cloud@node:~/.euca[/email]$ euca-describe-instances 
RESERVATION    r-454207A7    admin    default
INSTANCE    i-4B5B08C0    emi-210F15BA    10.1.1.106    172.19.1.2    running    mykey    0        m1.large    2011-05-04T09:06:23.194Z    cluster1eki-6E341ABC    
[email]cloud@node:~/.euca[/email]$ ssh -v -i mykey.priv ubuntu@10.1.1.106
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.1.1.106 [10.1.1.106] port 22.
debug1: Connection established.
debug1: identity file mykey.priv type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
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
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ee:15:83:61:98:d5:7a:17:e9:0c:22:2d:03:17:08:68.
Please contact your system administrator.
Add correct host key in /home/cloud/.ssh/known_hosts to get rid of this message.
Offending key in /home/cloud/.ssh/known_hosts:1
RSA host key for 10.1.1.106 has changed and you have requested strict checking.
Host key verification failed.
[email]cloud@node:~/.euca[/email]$ cd ..
cloud@node:~$ cd .ssh/
[email]cloud@node:~/.ssh[/email]$ ls
known_hosts  mykey.priv
[email]cloud@node:~/.ssh[/email]$ rm known_hosts 
[email]cloud@node:~/.ssh[/email]$ ls
mykey.priv
[email]cloud@node:~/.ssh[/email]$ ssh -v -i mykey.priv ubuntu@10.1.1.106
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.1.1.106 [10.1.1.106] port 22.
debug1: Connection established.
debug1: identity file mykey.priv type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
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
The authenticity of host '10.1.1.106 (10.1.1.106)' can't be established.
RSA key fingerprint is ee:15:83:61:98:d5:7a:17:e9:0c:22:2d:03:17:08:68.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.1.1.106' (RSA) to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: mykey.priv
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key 'mykey.priv':                                       // here i have pressed enter key
debug1: No more authentication methods to try.
Permission denied (publickey).
[email]cloud@node:~/.ssh[/email]$

---

### Post by kim0 on 2011-05-06
your priv key seems to be password protected ? and you just pressed enter. Try entering the password, or generate a new key pair, euca-add-keypair the new key and try with that

---

