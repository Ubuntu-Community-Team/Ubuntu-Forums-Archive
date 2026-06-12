---
title: "Can connect to server through nautilus, but not through terminal"
date: 2010-10-02
forum: Server Platforms
---

### Post by woodsonoversoul on 2010-10-02
Note: This is also posted in ABT, but I thought I might get more hits here...

As the title says, I can connect to a particular ubuntu server through nautilus (sftp) but not through terminal.

Not sure if it's using public or private key encryption, but I don't use a password to login. Any ideas?

---

### Post by BkkBonanza on 2010-10-02
sftp uses ssh for connecting and communicating.

So you should be able to login through terminal if you use ssh with same parameters. If no pwd then it must be configured for key authentication. That should also work in terminal as well since the same keys are available as in Nautilus.

In terminal type,

ssh user@server

with same user and server names as you used in Nautilus. 

It is possible at the server end it has been configured to only allow sftp for access. If that's the case then it won't allow general ssh access. This is a restriction imposed by the admin of the server.

---

