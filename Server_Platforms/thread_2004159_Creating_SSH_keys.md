---
title: "Creating SSH keys"
date: 2012-06-15
forum: Server Platforms
---

### Post by thany on 2012-06-15
Every time I do this, I get stuck at creating and appending the SSH keys. In the [documentation]("https://help.ubuntu.com/12.04/serverguide/openssh-server.html#openssh-keys") it says I need to transfer it to the remote host. I don't have a remote host, I'm doing it *on* the server.

As a result, ssh-copy-id doesn't work (ERROR: No identities found) which is kind of understandable.

I can find on google how to do this locally, no problem. The problem is that the documentation assumes a single scenario where you're generating keys on a (ubuntu? linux?) client and transfer them to the server. My client happens to windows, so to keep things simple, I'm doing everything on the server.

Such a simple change in the scenario and half the documentation is unusable. Assuming that the client can do "ssh-keygen" is pretty wild for a documentation that is aimed to be simple. The documentation should include a scenario where you do everything on the server, so that appending the key public key involves nothing more than "cat id_rsa.pub >> ~/.ssh/authorized_keys" or something similar. Include that in the docs, and done.

Thanks :)

---

### Post by spynappels on 2012-06-15
Ok, so let me see if I have this right.

You have an Ubuntu server which you want to access from a Windows laptop/desktop using PuTTY and key authentication?

But you want to create the keys on the server and just transfer the private key to your laptop?

That is possible to do, although not the recommended way as it involves copying the secret key from one host to another, rather than the public one. There is a security risk there, but if you are happy to accept that, here are the steps you need.

add the public key to #/.ssh/authorized_keys for the account you will be connecting to the server as.

Take the private key and transfer it to your laptop in as secure a manner as you feel you need.

Load it into PuTTYGen to convert it from OpenSSH key to Pageant key format.

Use the resulting key to ssh to your server.

Of course these are only high level steps, but there will be plenty of help available online for each individual step.

A better way might be to generate the key on your laptop using PuTTYGen and pasting the public key into the authorized_keys file on the server through an established ssh session, simpler and probably quicker and definitely more sound from a security angle.

---

### Post by Habitual on 2012-06-15
> **spynappels said:**
> ...A better way might be to generate the key on your laptop using PuTTYGen and pasting the public key into the authorized_keys file on the server through an established ssh session...

+1  for simplicity and keeping Security intact. :)

---

