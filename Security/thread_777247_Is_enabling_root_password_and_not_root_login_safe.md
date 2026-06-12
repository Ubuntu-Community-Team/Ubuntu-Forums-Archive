---
title: "Is enabling root password and not root login safe?"
date: 2008-05-01
forum: Security
---

### Post by Fixman on 2008-05-01
I'm not asking if its easy to recover the password (actually, just knowing my password or root password I can recover the other), but if there a some risk at having a root account and NOT LETTING IT login from GDM (just using su).

---

### Post by cdenley on 2008-05-01
If there is any server running that can be used for root access, then yes. If somebody is trying to access your computer, they will probably try the root account first. I would definitely disable root logins for ssh.

Why not use "sudo -s"? You can even add this to your .bashrc if you're used to the su command.
```

alias su='sudo -s'

```

---

### Post by p_quarles on 2008-05-02
It's not officially supported by Ubuntu, but that is not (afaik) due to remote security concerns so much as it is to software patches (like the "recovery mode" login bypass) and compatibility with documentation.

While there is no real reason to set a password for root, doing so is not, in and of itself, a security risk. After all, most *nix systems ask you to set the root password during installation, including tinfoil hat OSes such as OpenBSD. 

Some things to keep in mind if you ever decide to do this:
1) Use a strong password.
2) Don't be surprised if single-user mode breaks
3) Don't run the system as root -- only applications that really, truly need to run as root.

---

