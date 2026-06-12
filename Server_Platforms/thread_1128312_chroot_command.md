---
title: "chroot command"
date: 2009-04-17
forum: Server Platforms
---

### Post by dustervoice on 2009-04-17
I have six users (u1, u2 ....u6) and i want to "jail" those users to a directory call jailhouse. what is syntax  to  accomplish this. this is what im typing but its not working.   chroot u1 u2 ...u6  /home/jailhouse

---

### Post by lensman3 on 2009-04-17
Use the "Iron Bars restricted Shell for Linux" found on SourceForge. Or the "rbash" -- restricted bash.  They might do what you want.  For "chroot" to work you have to add it to the login scripts and the bash startup scripts.

---

### Post by BkkBonanza on 2009-04-17
Don't give a userid with chroot. Type, **man chroot** to read the very brief manual on it. You simply give chroot the new root directory and optionally a command. By default it starts a shell but the shell has to exist in the new root. So if you want to chroot to /home/jailhouse you do,

**chroot /home/jailhouse**

But the expected shell must be there. So for example if your shell is given by /bin/bash then inside /home/jailhouse you need a copy of bash at **/home/jailhouse/bin/bash** then it can start up. Actually it needs several components to be present so using chroot isn't quite that simple. bash needs it's library files. So type **ldd /bin/bash** to see what other files you need to copy to the directory tree that will be the jail. Once the various files needed exist in the jail then the shell can start with root being that location.

Also note that if you don't copy the binaries for various commands you need then there is not much you can do in the jail. Even ls requires copying the /bin/ls file.

---

