---
title: "Virtualizing existing XP Pro, using tutorial..."
date: 2008-06-17
forum: Virtualisation
---

### Post by Mecharuva on 2008-06-17
But, this line:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
```
Won't work.  I get:
```
VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  loadsyms <vmname>|<uuid> <symfile> [delta] [module] [module address]
      This will instruct DBGF to load the given symbolfile
      during initialization.

  unloadsyms <vmname>|<uuid> <symfile>
      Removes <symfile> from the list of symbol files that
      should be loaded during DBF initialization.

  setvdiuuid <filepath>
       Assigns a new UUID to the given VDI file. This way, multiple copies
       of VDI containers can be registered.

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Invalid command 'createrawvmdk'

```

I don't know what to do here, I'm still pretty n00b when it comes to Linux...

---

