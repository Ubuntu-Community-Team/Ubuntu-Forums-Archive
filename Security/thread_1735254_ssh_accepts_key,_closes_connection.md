---
title: "ssh accepts key, closes connection"
date: 2011-04-21
forum: Security
---

### Post by tribalvibes on 2011-04-21
Trying to log into server--two accounts with identical authorized_keys file in ~/user/.ssh
First user account ssh user1@host works fine.  Second one, get Connection closed by server.
ssh -vv ends in:

debug1: Authentications that can continue: publickey
debug1: Offering public key: /Users/usr/.ssh/key
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp 2c:bc:47:91:24:1b:3d:45:ee:c2:d5:b0:ca:ca:65:bd
Connection closed by 175.10.14.3

Any idea what's going on? This may not be an sshd problem at all--might be acct config for user2. Where could I look to fix this?  This is unfortunately impeding a capistrano deploy. 

Thanks!
tv/

---

