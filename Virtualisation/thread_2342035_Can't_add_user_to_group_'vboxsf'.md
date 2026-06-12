---
title: "Can't add user to group 'vboxsf'"
date: 2016-11-03
forum: Virtualisation
---

### Post by trumpet-st on 2016-11-03
Hello friendly Ubuntu fans!

Not sure if this is the best place to post this problem, but I am running Ubuntu 16.04 on Virtualbox on a Windows 10 host so posting this here:

I'm trying to share folders from the host to the guest, should be straightforward, but I can't successfully add the user I'm logged in as (meep) to the vboxsf group.  Instead, to access the shared folder, I have to sudo su to root and then I have full access.

Permissions of the shared folder are as expected:
meep@meep-VirtualBox:/media$ ls -al
total 12
drwxr-xr-x   4 root root   4096 Nov  3 09:55 .
drwxr-xr-x  24 root root   4096 Oct 20 13:25 ..
drwxr-x---+  2 root root   4096 Nov  3 09:56 meep
drwxrwx---   1 root vboxsf    0 Jan  1  1980 sf_G_DRIVE


To add meep to the group I've entered:

sudo usermod -a -G vboxsf meep

but I still don't get access to the shared folder.  Strangely though, I get the following responses from the 'groups' command:

meep@meep-VirtualBox:/media$ groups meep
meep : vboxsf adm cdrom sudo dip plugdev lpadmin sambashare libvirtd

but when I just enter:

meep@meep-VirtualBox:/media$ groups
meep adm cdrom sudo dip plugdev lpadmin sambashare libvirtd

so am I a member of vboxsf or not?

calling: 
meep@meep-VirtualBox:/media$ getent passwd |grep meep
meep:x:1000:999:Meep,,,:/home/meep:/bin/bash

would suggest there's just one user called 'meep' to me, but why is there capitalisation at the beginning of a Meep there?


I'm banging my head against my desk with this one.
Please help!

Gareth

---

### Post by steeldriver on 2016-11-03
Did you log out and back in (or at least start a new login shell, for example using
```

su - meep

```
or
```

bash -l

```

Group settings are only re-read on login.

The capitalized Meep in /etc/passwd is you GECOS full name [https://en.wikipedia.org/wiki/Gecos_field](https://en.wikipedia.org/wiki/Gecos_field)

---

### Post by trumpet-st on 2016-11-03
> **steeldriver said:**
> Did you log out and back in (or at least start a new login shell, for example using
```

su - meep

```
or
```

bash -l

```

Group settings are only re-read on login.

The capitalized Meep in /etc/passwd is you GECOS full name [https://en.wikipedia.org/wiki/Gecos_field](https://en.wikipedia.org/wiki/Gecos_field)

I didn't realise that!  I tried restarting a new shell and it still didn't work.  I've restarted the virtual machine and now everything works as it should.  The help page I was following didn't mention that!   Duh!

Thanks for the quick response!

Gareth

---

