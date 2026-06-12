---
title: "SSH with multiple machines to server"
date: 2014-09-15
forum: Security
---

### Post by scojopa on 2014-09-15
I have ssh installed and connecting via public key - 

If I want to add a second client to be able to connect - how do I configure this? I tried to generate a new key for the second machine but get permission denied when attempting to copy it via ssh-copy-id

Can someone please point me in the right direction? I was thinking I should copy the private key from my first client that can connect - but was reading this is poor practice. 

Thanks,

---

### Post by Lars Noodén on 2014-09-15
You're on the right track creating a second key pair for the second client.  In principle it is best to have each client+account with its own key pair.

You only need to add the public key to the server and that can be done manually if necessary: log into the server, open ~/.ssh/authorized_keys with a text editor (e.g. nano), add the new *public* key on a line of its own -- making sure that it is whole and unbroken on that single line.  

What was the exact error message that ssh-copy-id gave and how did you invoke it?

---

### Post by scojopa on 2014-09-15
Exact message was permission denied  - assuming because it was trying to authenticate with original keys and that wont work. 

So I copy the new public key and append it to 'authorized keys' file on server?

---

### Post by Lars Noodén on 2014-09-15
> **scojopa said:**
> So I copy the new public key and append it to 'authorized keys' file on server?

Yes.  The *authorized_keys* file is a simple list of public keys, one per line.  The exact format is described in the manual page for [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) and can accept a few options, in its own section, including locking the key to a specific program or script.

---

