---
title: "SSH Tunnels requires root for ports &lt; 1000. How to do it in Ubuntu?"
date: 2006-06-27
forum: Server Platforms
---

### Post by harisund on 2006-06-27
As you have already figured out from my question, I need to do a tunnelling to a prevliged port. sudo doesn't work (or can it be done using sudo in some way I am not aware of) or should I just have to create a root user?

Any help? Thnks ...

---

### Post by Ctrl+Alt+Del on 2006-06-27
the root user exists on your system, but its password is scrambled.
If you need a more permanent rootshell you can type 'sudo -s' to get it. If you need root enabled all you have to do is set its password by issuing 'sudo passwd root'

---

