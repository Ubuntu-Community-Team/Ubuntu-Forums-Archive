---
title: "SSH: How to generate public key from private key?"
date: 2008-06-28
forum: Security
---

### Post by Westerberg on 2008-06-28
According to [_this_]("http://ubuntuforums.org/showthread.php?p=2288959#post2288959") thread, I should be able to generate a public key to match a private key I already have:

> If you didn't notice, it generated another public key.This is the same key as is on your computer, as you can always generate your public key from your private key (but not the other way around).

The author used something called puttygen.exe, which I assume is a windows program.  How would I do in Ubuntu what he did?

---

### Post by kevdog on 2008-06-28
Probably someone will beat me to this, but can I clarify one thing?  Do you want to generate putty keys or openssh keys?  The two are not interchangeable.  They both work with ssh, but you can't for example use putty private and openssh public keys together.  What client are you going to use to complete the ssh connection?

---

### Post by Westerberg on 2008-06-28
Nevermind.  I think I figured it out.  It's:
```
ssh-keygen -e
```

---

### Post by kevdog on 2008-06-28
ssh-keygen -e -- This would imply open-ssh keys and not putty keys -- just an FYI

---

### Post by MountainX on 2011-05-12
> **Westerberg said:**
> Nevermind.  I think I figured it out.  It's:
```
ssh-keygen -e
```

I don't think that's the option you want. (I realize the question is old, so this comment is really for new people seeing the question.)

The correct option would be 
```
ssh-keygen -y
```

---

