---
title: "evdevkeymap works with VBoxSDL from terminal but not launcher"
date: 2011-03-11
forum: Virtualisation
---

### Post by isleshocky77 on 2011-03-11
When launching a Virtualbox Virtual Machine directly from the terminal command line using the following command everything works as expected, i.e. the arrow keys and windows key work correctly.

```

VBoxSDL --startvm 'Windows XP' --evdevkeymap

```

However, when I take this command and put it as a Menu Launcher Command it appears that "evdevkeymap" is no longer being recognized, i.e. the windows key does not work, the arrow keys don't do anything with exception to the down arrow acting as the windows key.

I've attempted switching the launcher around as much as possible with all the same results.

[LIST]
[*] One hyphen instead of two
[*] Type: Application
[*] Type: Application in Terminal
[*] --evdevkeymap before --startvm
[/LIST]

Host: 
Ubuntu 10.10
Linux sostrow-3510 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux
Virtual Box 3.1.8r61349

Guest: 
Windows XP with Guest Tools installed

---

