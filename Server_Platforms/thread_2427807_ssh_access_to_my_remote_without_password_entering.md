---
title: "ssh access to my remote without password entering"
date: 2019-09-26
forum: Server Platforms
---

### Post by petrogromovo on 2019-09-26
Hello,
I need to make access with ssh to my remote Ubuntu 16 server(under Digital Ocean) with non root user
In /home/serge/.ssh/config of my local laptop I have :


```
Host bitbucket.org
    IdentityFile ~/.ssh/id_rsa
    Hostname bitbucket.org
    User git 
    
Host github.com
    IdentityFile ~/.ssh/id_rsa
    Hostname github.com
    User git 


    
Host laravelserver
    IdentityFile ~/.ssh/id_rsa
    HostName NNN.NN.NNN.N
    Port 22
    User lardeployer
    

```    
Now running in my local console :
```
$ ssh laravelserver 

```I have user passoword entrance prompt for lardeployer.    
lardeployer - is user on my remote server
Which steps have I to take ssh access without entering password for lardeployer ?


Thanks!

---

### Post by slickymaster on 2019-09-26
*Thread moved to **Server Platforms**.*

---

### Post by btindie on 2019-09-26
Have you added your public key (~/.ssh/id_rsa.pub) to *.ssh/authorized_keys* file on the **remote** server?

Make sure the permissions on the .ssh directory & *authorized_keys f*ile are correct or else it'll refuse to use it.

For your **local** *.ssh/config*, all you need is
```

Host laravelserver
    User lardeployer
    HostName 1.2.3.4

```
the other options are used by default.

If you run *ssh* with the '-v' it may give you a clue as to what's going on.
```

$ ssh -v laravelserver

```

---

### Post by petrogromovo on 2019-09-26
Yes, I have public key (~/.ssh/id_rsa.pub) and authorized_keys file on the remote server
Using command from my local server  
```
ssh [EMAIL="root@NN.NNN.NN"]root@NN.NNN.NN[/EMAIL].N

```I enter in console of the remote server and I have  :
```
root@nsn-do-lamp:~# cd ~/.ssh/
[EMAIL="root@nsn-do-lamp:~/.ssh"]root@nsn-do-lamp:~/.ssh[/EMAIL]# ls -la
total 28
drwx------  2 root root 4096 Mar  9  2019 .
drwx------ 10 root root 4096 Sep 26 12:56 ..
-rw-r--r--  1 root root  393 Oct  4  2018 authorized_keys
-rwx------  1 root root  182 Mar  9  2019 config
-rw-------  1 root root 1675 Feb 26  2019 id_rsa
-rw-r--r--  1 root root  398 Feb 26  2019 id_rsa.pub
-rw-r--r--  1 root root 2212 Sep 19 11:40 known_hosts

```file  authorized_keys has 1 record , used for login as root


```
[EMAIL="root@nsn-do-lamp:~/.ssh"]root@nsn-do-lamp:~/.ssh[/EMAIL]# sudo nano config
Host bitbucket.org
    IdentityFile ~/.ssh/id_rsa
    Hostname bitbucket.org
    User git

Host github.com
    IdentityFile ~/.ssh/id_rsa
    Hostname github.com
    User git


```

On my local laptop :
```
$ ssh -v laravelserver
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /home/serge/.ssh/config
debug1: /home/serge/.ssh/config line 12: Applying options for laravelserver
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to NN.NNN.NN.N [NN.NNN.NN.N] port 22.
debug1: Connection established.
debug1: identity file /home/serge/.ssh/id_rsa type 0
debug1: key_load_public: No such file or directory
debug1: identity file /home/serge/.ssh/id_rsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000
debug1: Authenticating to NN.NNN.NN.N:22 as 'lardeployer'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:Ec049DrZ66P6Ly5y/yiTGZcVssyQM60tBxE7ctIVe90
debug1: Host 'NN.NNN.NN.N' is known and matches the ECDSA host key.
debug1: Found key in /home/serge/.ssh/known_hosts:15
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:ET7yY2FSwpGCz4EC/yRvWwsmbQEDz4XsUfobn3TZHU4 /home/serge/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
[EMAIL="lardeployer@NN.NNN.NN"]lardeployer@NN.NNN.NN[/EMAIL].N's password: 

```

What esle I lack ?

---

### Post by btindie on 2019-09-26
It's failing because your public key isn't in the *authorized_keys* file for the user *lardeployer *or the permissions are in correct.
```

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:ET7yY2FSwpGCz4EC/yRvWwsmbQEDz4XsUfobn3TZHU4 /home/serge/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
lardeployer@NN.NNN.NN.N's password:

```
which is why it's then prompting for a password.

If you can access the **remote **server as root, type in the following and past the output
```

ls -la ~lardeployer/.ssh

```

It should look like:
```

drwx------  2 lardeployer lardeployer   4096 Sep 26 14:25 .
drwxr-xr-x 51 lardeployer lardeployer   4096 Sep 26 14:25 ..
-rw-------  1 lardeployer lardeployer    811 Nov 18  2016 authorized_keys

```
in terms of the ownership / permissions.

You need to have added you public key to the *lardeployer *users .ssh/authorized_keys file to connect as that user. What you showed is for root.
```

root@nsn-do-lamp:~# cd ~/.ssh/
root@nsn-do-lamp:~/.ssh# ls -la
total 28
drwx------  2 root root 4096 Mar  9  2019 .
drwx------ 10 root root 4096 Sep 26 12:56 ..
-rw-r--r--  1 root root  393 Oct  4  2018 authorized_keys
-rwx------  1 root root  182 Mar  9  2019 config
-rw-------  1 root root 1675 Feb 26  2019 id_rsa
-rw-r--r--  1 root root  398 Feb 26  2019 id_rsa.pub
-rw-r--r--  1 root root 2212 Sep 19 11:40 known_hosts

```

---

### Post by TheFu on 2019-09-27
To everyone still using RSA ssh-keys, please check that they are at least 2K, 4K is better, in length.
Or switch to using ed25519 keys.  RSA keys less than 2K are considered quite hackable.

The OP seems to have both setup on the client, with the , but ed25519 are being presented to the server.  At this point, using RSA should be used for devices that only support RSA, like some old routers.

---

