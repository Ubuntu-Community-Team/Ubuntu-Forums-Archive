---
title: "Adding apt permissions only"
date: 2011-05-11
forum: Security
---

### Post by liverpoolfc on 2011-05-11
I'd like to give a user the rights to use apt (or Synaptic or Ubuntu Software Center) without giving them full sudo rights.  Is this possible?

---

### Post by Lars Noodén on 2011-05-12
> **liverpoolfc said:**
> I'd like to give a user the rights to use APT (or Synaptic or Ubuntu Software Center) without giving them full sudo rights.  Is this possible?

Yes.  That is what **sudo** is for.  Edit /etc/sudoers so that you give that group permission to run APT.

```

%maintainers ALL = (ALL) /usr/bin/apt-get update, /usr/bin/apt-get upgrade, /usr/bin/apt-get dist-upgrade

```

---

### Post by liverpoolfc on 2011-05-13
Thanks, that's what I was looking for.  I thought sudoers was just a list of users that could use sudo, I didn't realize it had that much detail

---

### Post by Lars Noodén on 2011-05-13
> **liverpoolfc said:**
>  I didn't realize it had that much detail

You can even get much more complex and add pattern matching.  **sudo** is a really very, very powerful tool.

If you want to see a little more, here is a [presentation on sudo](http://www.bsdly.net/~lars/Lectures/Network-2a-sudo.odp).

---

