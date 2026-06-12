---
title: "FTP Server Setup W/Multiple Hard Drives"
date: 2008-11-09
forum: Server Platforms
---

### Post by metalguy639 on 2008-11-09
I've run a FTP server for many years on my windows box. I used Bulletproof G6 2.15 when I had my server set up on my windows PC. Now I'm using Ubuntu 8.10 and I need to have a FTP server that I can add accounts to that will work on multiple hard drives (my server is spread out via 4 hard drives). I've installed 2 ftp servers but neither has an interface on it like Bulletproof G6 where I can update stuff via the program and not in the terminal. I have a few things I need help with:

1. How do I configure the server to show my multiple hard drives (I actually do not have my ftp set up on just the drives but its setup on directories that are inside the drives)

2. Is it possible to get a ftp server that has an interface like Bulletproof G6 or am I stuck with using the terminal for everything :(

The 2 ftp servers I installed were ProFTP & vsftpd.

Thanks

---

### Post by Vegan on 2008-11-09
You could mount the disks under the root FTP directory. This would simplify the situation.

As for users, you have to use the terminal window.

We server uses do not use a GUI, why are using the desktop?

---

### Post by metalguy639 on 2008-11-09
> **Vegan said:**
> You could mount the disks under the root FTP directory. This would simplify the situation.

As for users, you have to use the terminal window.

We server uses do not use a GUI, why are using the desktop?

Ok great! Uhm how do I do that??? LOL

---

### Post by metalguy639 on 2008-11-10
Anyone?

---

