---
title: "SSH service always has to be restarted"
date: 2015-06-09
forum: Server Platforms
---

### Post by scojopa on 2015-06-09
Does anyone have any idea what is causing my SSH server to constantly need to be restarted. I have SSH setup, I can remote in. But after a few hours I get (public key) denied)

Then I restart the SSH service on the server - and then I can get in. Any insight on how to resolve this would be great. 

There are no current ssh sessions when this happens. 

Thanks,

Scopa

---

### Post by papibe on 2015-06-09
Hi scojopa.

Could be this [bug]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1254085"). If you are affected by this, reducing your MTU on the client works as suggested.

Hope it helps. Let us know how it goes, and if you need more directions with that.
Regards.

---

### Post by scojopa on 2015-06-18
Sorry for the long delay in replying - actually not sure what the issue is. 

I will get permission denied. Get on the machine locally, delete the contents of the authorized keys file. Enable password authentication in sshd_config. restart ssh
ssh-copy-id, I confirm that the authorized keys file is updated. I test ssh - I get in without a password. Cool it works. 
I update sshd_config with password authentication no - restart ssh
Then I get the error below:

Keep getting this error:

 Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: me@client
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/me/.ssh/id_rsa
debug1: Trying private key: /home/me/.ssh/id_dsa
debug1: Trying private key: /home/me/.ssh/id_ecdsa
debug1: Trying private key: /home/me/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by scojopa on 2015-06-18
The problem was my auth+keys file was in an encrypted home dir - moved it and everything works now.

---

### Post by papibe on 2015-06-18
I'm glad you solved your problem :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Best Regards.

---

