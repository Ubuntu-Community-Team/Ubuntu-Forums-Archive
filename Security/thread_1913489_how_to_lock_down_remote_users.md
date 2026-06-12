---
title: "how to lock down remote users?"
date: 2012-01-22
forum: Security
---

### Post by gian on 2012-01-22
hello All,

we are going to install Postgres based OpenERP, and the professionals who will do the support asked to be granted root access to our server.

They plan to support us from remote using an OpenVPN tunnel.

I am not paranoid, however I do not like to hand over the keys...

What could I propose them?

---

### Post by Lars Noodén on 2012-01-22
One way might be through sudo.  sudo can be use to grant very fine grained access.  It's possible that you could set up sudo to allow them to do what they need to and no more.  If it is a production server, it's not (I hope) going to be changing a lot and the functions they need will be well-known and clearly defined.  See [font=Courier New]cmnd_alias[/font] in [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)

---

### Post by gian on 2012-01-22
thanks for your kind reply.

I had thought so, but I can't figure which commands they shall need to execute.

Maybe I should ask THEM to prepare a modified sudoers file for my approval.

---

### Post by CharlesA on 2012-01-22
> **gian said:**
> thanks for your kind reply.

I had thought so, but I can't figure which commands they shall need to execute.

Maybe I should ask THEM to prepare a modified sudoers file for my approval.
That would be one idea.

I don't know why they would need root access to manage a db server unless they need to start/stop the service.

I would ask why they need root access in the first place.

---

### Post by Lars Noodén on 2012-01-23
I've been playing around with [script](http://manpages.ubuntu.com/manpages/oneiric/en/man1/script.1.html) a bit and it might be useful for logging.  You can using in sshd using the ForceCommand directive. That way you have log of what they were doing and have a better change at getting the changes and configurations documented.

---

