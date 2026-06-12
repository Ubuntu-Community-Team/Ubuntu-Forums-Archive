---
title: "local repository with deb downloaded from web"
date: 2011-01-10
forum: Server Platforms
---

### Post by magowiz82 on 2011-01-10
Hi,
I would like to set up a local repository, that serves my LAN, and store it packages I found on the web (using pkgs.org for example) , can you please link me a guide regarding this ?

---

### Post by Thirtysixway on 2011-01-11
> **magowiz82 said:**
> Hi,
I would like to set up a local repository, that serves my LAN, and store it packages I found on the web (using pkgs.org for example) , can you please link me a guide regarding this ?

[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)

---

### Post by magowiz82 on 2011-01-11
thank you!

---

### Post by magowiz82 on 2011-01-11
I set up mine local repo, but on each package I install from it I get :
```
WARNING: The following packages cannot be authenticated!
  minitube
```

Is there a way to avoid this ?

---

### Post by Thirtysixway on 2011-01-11
> **magowiz82 said:**
> I set up mine local repo, but on each package I install from it I get :
```
WARNING: The following packages cannot be authenticated!
  minitube
```

Is there a way to avoid this ?

Try running these commands
```

apt-get install debian-archive-keyring
apt-key update
apt-get update
apt-get upgrade

```
note that 2nd one is apt-key

---

### Post by magowiz82 on 2011-01-11
no luck.
I think that this link is a hint : [https://alioth.debian.org/docman/view.php/30039/3782/manual.html#signing](https://alioth.debian.org/docman/view.php/30039/3782/manual.html#signing) but I don't know how to create and use a gpg key to sign it.
How can I do?

---

### Post by magowiz82 on 2011-01-11
I solved generating a gpg key and including in conf/distributions a line like this :
```
SignWith: <key_id>
```

---

