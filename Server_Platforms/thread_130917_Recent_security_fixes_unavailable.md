---
title: "Recent security fixes unavailable"
date: 2006-02-15
forum: Server Platforms
---

### Post by Jon V on 2006-02-15
Hi,

It seems that recent security updates, ie at least

[USN-249-1] xpdf/poppler/kpdf vulnerabilities   Martin Pitt   
[USN-250-1] Linux kernel vulnerability   Martin Pitt   
[USN-248-2] unzip regression fix   Marin Pitt

Are not available on security.ubuntu.com/

Is this known about / being fixed?

Jon

---

### Post by innate on 2006-02-15
Same problem here. Does anyone know more about this? Is it a real security update? It seems strange.

---

### Post by sal on 2006-02-16
im having the same problem with the updates.
i cant get them with apt-get or synaptic.

whats going on with this matter?

---

### Post by Jon V on 2006-02-16
[QUOTE=sal]im having the same problem with the updates.
i cant get them with apt-get or synaptic.

whats going on with this matter?[/QUOTE]

The problem appears to be that the gb.archive.ubuntu.com (of which security.ubuntu.com is an alias) repo isnt being updated.

I worked around this by adding the following to /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security universe multiverse

Jon

---

### Post by nocturn on 2006-02-16
confirmed here too.

---

### Post by sal on 2006-02-16
[QUOTE=Jon V]The problem appears to be that the gb.archive.ubuntu.com (of which security.ubuntu.com is an alias) repo isnt being updated.

I worked around this by adding the following to /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-security universe multiverse

Jon[/QUOTE]


thanks this worked. do you know when the problem you menten will be fixed?

---

### Post by nocturn on 2006-02-16
I'm on the be. mirrors, it seems they are not updated either

---

### Post by towsonu2003 on 2006-02-16
not using mirrors (archives.blabla), I have this as well. + my (kind of a duplicate) thread is here [http://ubuntuforums.org/showthread.php?t=131147](http://ubuntuforums.org/showthread.php?t=131147) (for reference purposes only)

---

### Post by innate on 2006-02-16
I sent an e-mail about this to Martin and these updates are now available from the standard update sources. I don't know if it is a coincidence or if Martin fixed it just now. \\:D/

---

### Post by Suzan on 2006-02-16
Really? I tried it and it doesn't work.

---

### Post by towsonu2003 on 2006-02-16
works for me as well. I'm not using any mirrors. 

The description of the kernel update is fishy.

---

