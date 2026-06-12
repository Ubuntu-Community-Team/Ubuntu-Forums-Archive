---
title: "Migration of SSH Keys"
date: 2009-12-04
forum: Server Platforms
---

### Post by vaguy02 on 2009-12-04
Everyone,

I recently upgraded my ssh server platform from Gentoo to Ubuntu 9.10 Server. I transfered all ssh keys to the correct locations, meaning into each user account ~/.ssh/authorized_keys, chown, then did a chmod 0600 on all keys. I'm attempting to use one of them to login to verify functionality, but every time I get the following messages under VERBOSE mode.

"Failed none for <user> from <ip> port 34496 ssh2"
"Failed publickey for <user> from <ip> port 34496 ssh2"

Anyone have any ideas? I know the keys work, because they did before....

---

### Post by BkkBonanza on 2009-12-04
Are you sure you copied the public keys and not the private keys to the server?

---

### Post by vaguy02 on 2009-12-04
Yep. I have both sets for each, each labeled <user>.private and <user>.public and I copied the public ones to the authorized_keys to each folder. 

Is there a way to check what the reason for the publickey failure was? I didn't see in the auth.log even with verbose on.

---

### Post by BkkBonanza on 2009-12-04
I think if you run ssh with -vv it gives even more verbose output. May help... I remember it spitting out a lot of info.

---

### Post by vaguy02 on 2009-12-04
I made new ssh keys and they worked. It's very strange. I guess I will just have to distribute new keys. Thanks.

---

