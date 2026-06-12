---
title: "Update ubuntu without sudo permissions"
date: 2009-06-02
forum: Security
---

### Post by any.linux12 on 2009-06-02
Hi!

Is it possible to update the system without having sudo permissions? because I want to take the sudo rights from all users on my network but I don't want to go to them computers and type my password everytime they have an update.

Thanks

---

### Post by MichaelSammels on 2009-06-02
You would need to add your users to a group with sudo privelages, which is risky, since it basically gives them sudo rights.

---

### Post by HavocXphere on 2009-06-02
I think you can "give" certain apps sudo right using something called sudoers i.e. make it so that the app always has sudo rights. Not sure how it works though.

---

### Post by cdenley on 2009-06-02
To edit /etc/sudoers
```

sudo EDITOR=gedit visudo

```

To allow members of the group "users" to run apt-get
```

%users ALL=(ALL) /usr/bin/apt-get

```

To allow them to do this without a password
```

%users ALL=NOPASSWD: /usr/bin/apt-get

```

---

### Post by any.linux12 on 2009-06-02
> **cdenley said:**
> To edit /etc/sudoers
```

sudo EDITOR=gedit visudo

```

To allow members of the group "users" to run apt-get
```

%users ALL=(ALL) /usr/bin/apt-get

```

To allow them to do this without a password
```

%users ALL=NOPASSWD: /usr/bin/apt-get

```

Hey cool :D thanks a lot

I had to add this line:
%user ALL=NOPASSWD: /usr/sbin/synaptic

But your tip was very helpful and now I understand the system :D

sorry for my bad Japanese

---

