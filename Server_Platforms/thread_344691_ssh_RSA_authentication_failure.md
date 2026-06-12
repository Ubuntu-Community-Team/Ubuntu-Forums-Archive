---
title: "ssh RSA authentication failure"
date: 2007-01-23
forum: Server Platforms
---

### Post by prkfriryce on 2007-01-23
I am using an ssh pub key on two remote servers to allow ssh session without authentication. Both servers have the same id_rsa.pub copied from the host into the remote servers ~user/.ssh/authorized_keys. There is no passphrase for this key either. 

The problem is that I am able to ssh into one remote server without a password prompt while the other server attempts to read the rsa key, but continues onto the password prompt.

Both remote servers have identical ssh_config, sshd_config, authorized_keys, and known_hosts files. V. OpenSSH_3.4p1, SSH protocols 1.5/2.0, OpenSS

Both ssh outputs are identical up to this point:

GOOD

```
debug1: authentications that can continue: publickey,password,keyboard-interactive
debug1: next auth method to try is publickey
debug1: try pubkey: /identity-test/id_rsa
debug1: input_userauth_pk_ok: pkalg ssh-rsa blen 149 lastkey 63950 hint 0
debug1: read PEM private key done: type RSA
debug1: ssh-userauth2 successful: method publickey
debug1: fd 6 setting O_NONBLOCK
``` 

BAD

```
debug1: authentications that can continue: publickey,password,keyboard-interactive
debug1: next auth method to try is publickey
debug1: try pubkey: /identity-test/id_rsa
debug1: authentications that can continue: publickey,password,keyboard-interactive
debug1: next auth method to try is keyboard-interactive
debug1: authentications that can continue: publickey,password,keyboard-interactive
debug1: next auth method to try is password
```

Any ideas?

---

### Post by elst on 2007-01-24
The public key file that doesn't work may be corrupt. It's worth double-checking the permissions as well - OpenSSH looks at the permissions on ~/.ssh/ to make sure that it's secure.  I'm actually slightly surprised by the OpenSSH version number - IIRC, Debian stable has 3.8p1, and Edgy has 4.3p2.

---

### Post by prkfriryce on 2007-01-24
> **elst said:**
> The public key file that doesn't work may be corrupt. It's worth double-checking the permissions as well - OpenSSH looks at the permissions on ~/.ssh/ to make sure that it's secure.  I'm actually slightly surprised by the OpenSSH version number - IIRC, Debian stable has 3.8p1, and Edgy has 4.3p2.

Yeah i was on Solaris 8, but i figured i'd give it a shot in the sercurity category.  

After going as far as double checking PAM modules confs, I did a simple ls -ld on the user's #HOME dir and found that the server not allowing access was 0775 instead of 0755. A quick chmod and I was good to go. 

thanks for trying anyway.

---

