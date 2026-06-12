---
title: "Ubuntu's GPG 'use-agent' feature"
date: 2014-02-09
forum: Security
---

### Post by fugu2 on 2014-02-09
Okay I'm having a problem that hopefully someone here can help me with. I want to write a simple bash script to execute a
```
$ gpg --detach-sign --armor $1
```
command but it's being done in a gui environment (no commandline), which is okay except 
that it asks for a password from a prompt that looks similar to the prompt for gksu
and it caches the password after that for a really long time (IMO it is set way too long, and
 should probably be set to 0).  I looked into it and Ubuntu no longer uses the gnupg-agent 
daemon to handle gpg cacheing of passwords, but rather in the ~/.gnupg/gpg.conf file it 
makes reference to 'use-agent' and handles all of this internally. 

What I want is to be able to change something like  default-cache-ttl 1 for gpg signing with use-agent, 
without needing to install any extra packages.

---

### Post by fugu2 on 2014-02-15
bump.
I was just wondering if any one has had any experience with adjusting this feature in ubuntu. Do you even know where the config file is located? Is there a config file?

---

### Post by fugu2 on 2014-02-23
Is there anyone who knows how to contact the developer in charge of this feature, which is specific to Ubuntu?

---

### Post by cariboo on 2014-02-23
Try the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list.

---

### Post by fugu2 on 2014-02-26
> **cariboo907 said:**
> Try the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list.

Thank you very much, I will do that :)

---

