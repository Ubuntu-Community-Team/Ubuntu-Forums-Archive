---
title: "Problem installing Hydra 5.8"
date: 2010-10-22
forum: Security
---

### Post by PhyroX on 2010-10-22
Hi guys, I have a problem installing THC Hydra, I've search and only found people with the exact same problem... without answer so here I go.       >    hydra-ssh2.o: In function `start_ssh2': hydra-ssh2.c:(.text+0xba): undefined reference to `ssh_auth_list' hydra-ssh2.c:(.text+0x225): undefined reference to `ssh_options_set' hydra-ssh2.c:(.text+0x23e): undefined reference to `ssh_options_set' hydra-ssh2.c:(.text+0x25d): undefined reference to `ssh_options_set' hydra-ssh2.c:(.text+0x27a): undefined reference to `ssh_options_set' hydra-ssh2.c:(.text+0x297): undefined reference to `ssh_options_set' collect2: ld returned 1 exit status make: *** [hydra] Error 1       Everything is OK except that. I have the lib, ./compile do fine but make give me that, and I don't know exactly how to fix it.  Any ideas?   Thanks  Running BT4 R1, 2.6.34

---

