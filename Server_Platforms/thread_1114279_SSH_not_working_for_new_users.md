---
title: "SSH not working for new users"
date: 2009-04-02
forum: Server Platforms
---

### Post by nutsmuggler on 2009-04-02
Hello folks.
I had to reinstall apache2 after messing up too much with its configuration. Thanks to a backup, I managed to restore every aspect of my previous setup, virtualhosts included. Yet now I cannot ssh into the server except that for one user (the one given to me by the hosting company). Before reinstalling I had a 'deploy' user which could authenticate with a RSA key, now I cannot even login properly.
I tried to delete and recreate the user, but the problem persists. I also tried to create another user, but the problem is still there.
For the chronicle, there's another error message which wasn't there before, when I restart apache:

```
[Thu Apr 02 21:15:42 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

```

I don't think the two issues are related, but whi knows...
Any suggestion?
Cheers,
Davide

---

### Post by kanikilu on 2009-04-02
I would probably check the sshd config (/etc/ssh/sshd_config), perhaps PasswordAuthentication is disallowed?

---

### Post by nutsmuggler on 2009-04-02
I checked, the directive is commented, so it''s set to yes by default. I also tried to uncomment it, no change. The strange thing is that the predefined user works well, while the other 2 users I created cannot ssh into the server. I get 
```
Permission denied (publickey,password)
```
but I am sure the password is right.
Any other idea?
Thanks in advance,
Davide

---

### Post by HermanAB on 2009-04-02
Here is the secret to SSH debug bliss:
$ ssh -vvv user@server

then read the error messages carefully.

Chances are that you need to add a .ssh directory or make it private:
$ cd
$ mkdir .ssh
$ chmod 700 .ssh

SSH is very pernickety about permissions.

---

### Post by nutsmuggler on 2009-04-03
Thanks Herman.
I tried to make an .ssh directory as you suggested,and to give it the right permissions: no change. Then I tried blissful debugging, and here's the output (with some obfuscation on my username and server IP):

```

debug2: key: /Users/-myusername-/.ssh/identity (0x0)
debug2: key: /Users/-myusername-/.ssh/id_rsa (0x0)
debug2: key: /Users/-myusername-/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/-myusername-/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/-myusername-/.ssh/identity
debug3: no such identity: /Users/-myusername-/.ssh/identity
debug1: Trying private key: /Users/-myusername-/.ssh/id_rsa
debug3: no such identity: /Users/-myusername-/.ssh/id_rsa
debug1: Trying private key: /Users/-myusername-/.ssh/id_dsa
debug3: no such identity: /Users/-myusername-/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
test@IPNUMBER's password: 
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
test@IPNUMBER's password: 
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
test@IPNUMBER's password: 
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```

Again, the weird thing is that one user can ssh, the other don't. I have insepcted sshd_config, there are no user or group directives.
Thanks again for your attention, any help is appreciated,
Davide

---

### Post by hyper_ch on 2009-04-03
what shell do those new users have in /etc/passwd ?

---

### Post by nutsmuggler on 2009-04-03
Problem eventually solved.
Herman's suggestion about the .ssh directory missing was right, but I had to destroy the user and recreate it to get it working.
Thanks you all user for you great feedback!
Davide

---

### Post by kevpatts on 2012-01-05
Just thought I'd put a comment on this cause I found I had similar issues but a different solution. The problem for me was that I had set up the users without passwords, so they has no entries in /etc/passwd and so they had no default shell to log into.

Setting user passwords fixed the issue.

---

### Post by Habitual on 2012-01-05
> **kevpatts said:**
> Just thought I'd put a comment on this cause I found I had similar issues but a different solution. The problem for me was that I had set up the users without passwords, so they has no entries in /etc/passwd and so they had no default shell to log into.

Setting user passwords fixed the issue.

Seen this behavior before also.
+1

---

