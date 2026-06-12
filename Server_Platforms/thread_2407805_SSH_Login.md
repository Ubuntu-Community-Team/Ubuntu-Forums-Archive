---
title: "SSH Login"
date: 2018-12-09
forum: Server Platforms
---

### Post by sniper8752 on 2018-12-09
I am trying to login to my server via ssh, but am getting this error message:

```
...debug1: Host '192.168.2.2' is known and matches the ECDSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug1: SSH2_MSG_SERVICE_ACCEPT received


debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:[random chars] /home/user/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Trying private key: /home/user/.ssh/id_ecdsa
debug1: Trying private key: /home/user/.ssh/id_ed25519
debug1: No more authentication methods to try.
user@192.168.2.2: Permission denied (publickey).
```

I had to turn password authentication to yes, then copy my public key, then turned it back off.

---

### Post by btindie on 2018-12-10
The ssh server probably doesn't like your public key file.

It should be stored in *.ssh/authorized_keys* and make sure the permissions on it are 0600.

```
chmod 0600 ~/.ssh/authorized_keys
```

---

### Post by sniper8752 on 2018-12-15
Unfortunately that didn't work.  I do see my public key in the authorized keys file on the server.

---

### Post by sniper8752 on 2019-01-01
Should the owners be user:user?

---

### Post by howefield on 2019-01-01
Thread moved to the "*Server Platforms*" forum, see if yo have better luck here.

---

### Post by TheFu on 2019-01-08
Could a prior ssh-key be conflicting with the new key?  Just edit the client-side knownhosts file, line 1. Delete it.
Then use ssh-copy-id to push a fresh public key to the remote system.  ssh-copy-id does the right thing - doesn't screw up permissions or ownership or break the line-wrap needed.

---

