---
title: "passwordless ssh fails"
date: 2010-01-11
forum: Security
---

### Post by bobdobbs on 2010-01-11
Hi all.

I am trying to set up passwordless ssh sessions between two computers. Both are running koala.

I am following the tutorial on this page:
[http://blogs.translucentcode.org/mick/archives/000230.html](http://blogs.translucentcode.org/mick/archives/000230.html)

I get up to the step 7: attempting to log in to the remote host via ssh. I am first asked for the passphrase. Then I am prompted for my password on the remote computer. So, my attempt to use the public key fails.

This is the output of ssh -v me@remote
```

: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: me@endorra (0x1381c08)
debug2: key: /home/me/.ssh/identity (0x13804f0)
debug2: key: /home/me/.ssh/identity ((nil))
debug2: key: /home/me/.ssh/id_rsa ((nil))
debug2: key: /home/me/.ssh/id_dsa (0x137ab80)
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: me@endorra
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /home/me/.ssh/identity
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/me/.ssh/identity
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/me/.ssh/identity':
debug1: read PEM private key done: type DSA
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/me/.ssh/id_rsa
debug1: Offering public key: /home/me/.ssh/id_dsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
me@remote's password:

```

local perms:
```

drwxr-xr-x   2 me me      4096 2010-01-11 22:00 .ssh
-rw-r--r-- 1 me me 605 2010-01-11 21:59 .ssh/authorized_keys

```

remote perms
```

drwx------   2 me me    4096 2010-01-11 21:52 .ssh

```

I'm guessing that this is a permissions issue, but I can't figure it out.

Where am I going wrong here ?

---

### Post by noway2 on 2010-01-11
I can't access the howto you reference at the moment (blocked due to being a "blog" site).  Normally, using public key authentication with ssh is pretty straight forward.  
1 - Create an RSA key set
2 - upload the public key to the server and place in the authorized keys folder
3 - keep the private key in your .ssh folder.
4 - make sure key authentication is enabled in the server ssh configuration

One typical 'gotcha' is that some ssh clients, such as putty, require their keys to be in a custom format.  You may have a problem there.  See the log entry below.  It appears that the key may be in a format that the client you are using doesn't understand.

debug1: Trying private key: /home/me/.ssh/identity
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/me/.ssh/identity':
debug1: read PEM private key done: type DSA

---

### Post by barnex on 2010-01-11
If you prefer clicking through a really simple keypair setup, use seahorse:

[http://www.debianadmin.com/ssh-key-authentication-using-seahorse-gui.html](http://www.debianadmin.com/ssh-key-authentication-using-seahorse-gui.html)

This allowed me to set up a keypair in a matter of seconds.
Note: obviously, you'll want to enter an empty passphrase for your keypair, since you want passwordless ssh.

---

### Post by cariboo on 2010-01-11
Here's a link to the Ubuntu specific [howto]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). It looks like there are way to many steps in the howto the op linked to.

---

### Post by BkkBonanza on 2010-01-11
It looks like from above you are using the file "identity". At least it appears to be prompting for a passphrase for that file only.

If so then that is usually a version 1 protocol file. Make sure the server has not denied version 1 by having the "Protocol 2" directive in sshd_config. This would all be a mistake as version 1 is considered weak and you're better off generating a new version 2 key. If you already did that then you likely should remove the identity file so it defaults to using id_rsa instead.

---

### Post by bodhi.zazen on 2010-01-11
> **cariboo907 said:**
> Here's a link to the Ubuntu specific [howto]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). It looks like there are way to many steps in the howto the op linked to.

+1 , I am sorry, but that blog entry is horrible. Certainly not very clear and certainly NOT the "shortest possible" method.

I can do all this with 4 commands

ssh-keygen
ssh-copy-id
ssh-add
ssh user@server

The blog entry uses 10 commands, on two systems no less, and a whole section about modifying .bashrc, which is not necessary on Ubuntu.

Make a key.

Transfer it using the ssh-copy-id command

add the key to RAM with ssh-agent

```
ssh-add ~/.ssh/key_name
```

Then 

ssh user@server

---

### Post by bobdobbs on 2010-01-13
> **bodhi.zazen said:**
> +1 , I am sorry, but that blog entry is horrible. Certainly not very clear and certainly NOT the "shortest possible" method.

I can do all this with 4 commands

ssh-keygen
ssh-copy-id
ssh-add
ssh user@server

The blog entry uses 10 commands, on two systems no less, and a whole section about modifying .bashrc, which is not necessary on Ubuntu.

Make a key.

Transfer it using the ssh-copy-id command

add the key to RAM with ssh-agent

```
ssh-add ~/.ssh/key_name
```

Then 

ssh user@server


Hi.
This all goes smoothly on one of the two hosts that I'm setting up. On Host A I simply followed your pattern, and I now have passwordless ssh to host B.

However, on host B, when I try to connect to host A, I am still being asked for a login password.

---

### Post by bodhi.zazen on 2010-01-14
> **bobdobbs said:**
> Hi.
This all goes smoothly on one of the two hosts that I'm setting up. On Host A I simply followed your pattern, and I now have passwordless ssh to host B.

However, on host B, when I try to connect to host A, I am still being asked for a login password.

OK, on host A you already have your key and key.pub ?

I assume your key on host A is in ~/.ssh so 

```
cd ~/.ssh
cat key.pub > authorized_keys
```

Or you can, on host A, ssh-copy-id user@localhost

Then transfer the key (not key.pub) to host B , again in ~/.ssh

---

