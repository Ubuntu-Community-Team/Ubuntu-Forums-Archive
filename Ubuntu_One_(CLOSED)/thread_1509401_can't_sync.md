---
title: "can't sync"
date: 2010-06-14
forum: Ubuntu One (CLOSED)
---

### Post by luofeiyu on 2010-06-14
pt@pt-laptop:~$ u1sync  --action=sync
Directory not initialized; use --init [DIRECTORY] to initialize it.
pt@pt-laptop:~$ u1sync  --init  /home/Ubuntu One
Usage: u1sync [options] [DIRECTORY]
       u1sync --authorize [options]
       u1sync --list-shares [options]
       u1sync --init [--share=SHARE_UUID] [options] DIRECTORY
       u1sync --diff [--share=SHARE_UUID] [options] DIRECTORY

u1sync: error: Too many arguments

---

### Post by rtg on 2010-06-15
You don't really need to use u1sync to start syncing. In Lucid Lynx you only need to start ubuntuone-preferences from MeMenu and it should ask you to add your computer to the service.
Are you having some issues with such kind of authentication?

---

