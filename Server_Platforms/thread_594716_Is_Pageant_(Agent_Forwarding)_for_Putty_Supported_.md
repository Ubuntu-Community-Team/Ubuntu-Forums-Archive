---
title: "Is Pageant (Agent Forwarding) for Putty Supported on Ubuntu?"
date: 2007-10-28
forum: Server Platforms
---

### Post by mousepad on 2007-10-28
I've setup my ssh to login with keys and passphrase.  I would like to do away with passphrases by using agent forwarding.  Putty uses Pageant to store private keys, bu from all the tutorials I can find, it's a windows based feature (to add private keys).  I've also tried to use ssh-add (a different agent), but it has trouble recognizing my private key passphrase (made with putty).  I know the private key is working because I'm able to use use ssh without a password, just the phrase.  

What's the best way to do this?  Is there a putty pageant command line that I don't know about?  Thanks!

---

### Post by netlogic on 2007-10-30
[http://www.mtu.net/~engstrom/ssh-agent.php](http://www.mtu.net/~engstrom/ssh-agent.php)
this should help.

---

