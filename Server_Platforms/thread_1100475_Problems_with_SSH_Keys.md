---
title: "Problems with SSH Keys"
date: 2009-03-19
forum: Server Platforms
---

### Post by rmccarri on 2009-03-19
Hi,
I have two server computers that I have setup to back up to each other over SSH using a cron job with RSYNC.  I put the id_rsa.pub keys in each computer's respective authorized_keys file.  One computer is able to properly ssh into the other without a password as expected.  However, the second computer is still prompted for a password when establishing an SSH connection.  I set everything up the same on both computers.

If I ssh with a -vv tag, everything is identical for both computers until here:

On the computer that is working:
```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp 0e:f5:ca:c3:a8:4c:e7:da:76:97:93:fa:bb:1c:17:5d
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
```

On the computer that isn't working:
```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password

```

Does anyone have any ideas that I could try?
Thanks!

---

### Post by rmccarri on 2009-03-19
Hi,
The problem was a permissions issue.  I had set my permissions in the folder to 700 and 600 for files. I changes it to 755 and 644 and everything works fine now.

---

