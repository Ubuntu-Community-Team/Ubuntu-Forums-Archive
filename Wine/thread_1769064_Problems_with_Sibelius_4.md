---
title: "Problems with Sibelius 4"
date: 2011-05-27
forum: Wine
---

### Post by RheaHS on 2011-05-27
Hi, I'm getting this error in the terminal, and can't work out what I need to do to fix these
```
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x1d4e90c, overlapped 0x1d4e8f0): stub
wine: configuration in '/home/rhea/.wine' has been updated.
fixme:exec:SHELL_execute flags ignored: 0x00000100
wine: cannot find L"C:\\windows\\system32\\Sibelius.exe"
rhea@rhea-desktop:~/.wine/drive_c/Program Files/Sibelius Software$ fixme:dbghelp:elf_search_auxv can't find symbol in module
wine: Unhandled exception 0xc000008d at address 0x68b633e9 (thread 0038), starting debugger...
fixme:dbghelp:elf_search_auxv can't find symbol in module

```

I've tried resetting Wine, the configuration files, purging it all. I have recently upgraded this PC, and I've had the program running before. Unfortuntely I can't access the old install to find out what is different.

---

### Post by bobwyajnr on 2011-05-30
> **RheaHS said:**
> Hi, I'm getting this error in the terminal, and can't work out what I need to do to fix these
```
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x1d4e90c, overlapped 0x1d4e8f0): stub
wine: configuration in '/home/rhea/.wine' has been updated.
fixme:exec:SHELL_execute flags ignored: 0x00000100
wine: cannot find L"C:\\windows\\system32\\Sibelius.exe"
rhea@rhea-desktop:~/.wine/drive_c/Program Files/Sibelius Software$ fixme:dbghelp:elf_search_auxv can't find symbol in module
wine: Unhandled exception 0xc000008d at address 0x68b633e9 (thread 0038), starting debugger...
fixme:dbghelp:elf_search_auxv can't find symbol in module

```

I've tried resetting Wine, the configuration files, purging it all. I have recently upgraded this PC, and I've had the program running before. Unfortuntely I can't access the old install to find out what is different.

+1 for actually posting some commandline output. Hint to everyone else!! :popcorn:

-1 for not actually giving the command you typed in - which (I'm afraid) is wrong! :(

The problem is indicated by:
```
wine: cannot find L"C:\\windows\\system32\\Sibelius.exe"
```
This means that Wine has looked in the current working folder for "Sibelius.exe" and has failed. The next place it looks is in the system folders. Once it fails this it has to give up!

Can you post the contents of the game directory:```
ls -al
```and post the command you actually using to run the game - exactly - copied over - **remember UNIX is case sensitive**!

Bob

---

