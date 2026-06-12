---
title: "How to create a user account with no privileges at all"
date: 2008-11-27
forum: Security
---

### Post by frankvw on 2008-11-27
I need to create a user account without any privileges at all, but to which it is possible to log in using SSH.

The idea is to set up a reverse SSH tunnel using a middleman host, so that from the server I can access systems (running Hardy Heron) that are behind a firewall. (Like so: [http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/))

This requires that the Ubuntu system behind the firewall log on to the server using SSH. That's all it takes: logging on via SSH. It doesn't take anything else, and for reasons of security I don't want anything else.

Using /bin/false as the shell doesn't work, because then logging on fails. Using /bin/bash is not secure. Surely there must be some middle ground here. :-)

Suggestions, anyone?

Thanks!

// Frank

---

### Post by hyper_ch on 2008-11-27
have a look at MySecureShell - maybe that has some functionality that can help you achieve what you want.

---

### Post by bodhi.zazen on 2008-11-27
> **frankvw said:**
> I need to create a user account without any privileges at all, but to which it is possible to log in using SSH.

The idea is to set up a reverse SSH tunnel using a middleman host, so that from the server I can access systems (running Hardy Heron) that are behind a firewall. (Like so: [http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/))

This requires that the Ubuntu system behind the firewall log on to the server using SSH. That's all it takes: logging on via SSH. It doesn't take anything else, and for reasons of security I don't want anything else.

Using /bin/false as the shell doesn't work, because then logging on fails. Using /bin/bash is not secure. Surely there must be some middle ground here. :-)

Suggestions, anyone?

Thanks!

// Frank

You can use rbash and ssh keys. I presume you are say forwarding a port ?

It is on my "to do" list to write a nice how-to rbash, but this should give you some ideas :

[http://blog.bodhizazen.net/?p=6](http://blog.bodhizazen.net/?p=6)

If you can be more specific I can perhaps give you better advice, but between rbash and ssh keys you should be good to go.

---

