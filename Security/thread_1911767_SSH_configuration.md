---
title: "SSH configuration"
date: 2012-01-19
forum: Security
---

### Post by ray field on 2012-01-19
Until now, I've only used SSH on my desktop in order to allow my laptop to sync files via Unison.  My ~/.ssh folder contains 

```
known_hosts
.config
id.dsa.pub
id_dsa
```

I can't remember what I did, but I guess I generated the key pair on my laptop.

Now I want to configure SSH in order to use Drush to coordinate files on my website provider. The articles I see suggest using keygen to generate a key pair, of course.  If I do that, my id_dsa files won't change, but known_hosts will have the information from the remote webserver, is that correct? Will there be new files in ~/.ssh ?

Elementary questions, I know, just want to make sure.

---

### Post by Lars Noodén on 2012-01-19
> **ray field said:**
> ... The articles I see suggest using keygen to generate a key pair, of course.  If I do that, my id_dsa files won't change, but known_hosts will have the information from the remote webserver, is that correct? Will there be new files in ~/.ssh ?

They won't change unless you tell ssh-keygen to overwrite them.

[ssh-keygen](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keygen.1.html) has the -f option which will tell ssh-keygen where to place the keys once they are generated. 

e.g.
```

ssh-keygen -t rsa -b 2048 -f /home/rayfield/.ssh/drush_key_rsa

```

So you can put as many key pairs in .ssh as you need.  When using them you'll also have to refer to them explicitly.

```

ssh -i /home/rayfield/.ssh/drush_key_rsa *drush.example.org*

```

---

### Post by ray field on 2012-01-19
Naturally, when I got around to seeing how SSH access worked, it involves a password tied to my account -- in any case, thanks for the helpful reply, I'm always glad for more knowledge!

---

