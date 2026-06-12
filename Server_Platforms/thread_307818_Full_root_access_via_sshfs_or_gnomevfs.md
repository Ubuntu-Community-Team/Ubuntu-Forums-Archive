---
title: "Full root access via sshfs or gnomevfs ?"
date: 2006-11-27
forum: Server Platforms
---

### Post by alanfranz on 2006-11-27
Hello,
my remote Ubuntu Edgy server is set up correctly, and I can connect to it via standard ssh just fine. Since there's no root account in Ubuntu, when I connect via ssh I just do a 'sudo -i' or 'sudo -s' to gain a root shell.

That's fine and it works.

Now I've got an Ubuntu Edgy desktop installed here on my laptop. I'd like a graphical way of getting full access (e.g. root) to the remote server. I've tried with gnomevfs, and I can navigate correctly, but I just have normal user rights, and the same happens by using sshfs; I've found no way to tell such programs to execute a 'sudo -i' or 'sudo -s' once they log-in into the server (that would suffice!).

Any clue?

---

