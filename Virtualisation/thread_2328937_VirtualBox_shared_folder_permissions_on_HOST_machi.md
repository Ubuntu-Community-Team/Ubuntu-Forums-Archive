---
title: "VirtualBox shared folder permissions on HOST machine"
date: 2016-06-25
forum: Virtualisation
---

### Post by David_Woods on 2016-06-25
SO I have shared folders set up and it seems to be working but I'm having one problem.

When I create a new file in the shared folder using the guest OS, the file on the host OS is always has permissions set to 755. I need it to be 775. I can change it manually but is there a way I can get it to automatically be 775?

Thanks

---

### Post by MAFoElffen on 2016-06-26
How did you share the folder on your host? Just thinking if smb share through Samba... then smb.conf, etc... or through system/fs permssions of the folder as an inherited permssion.

What I would do first is check the Linux permssions of the folder
```

ls -ld /path/to/folder/

```
The reason you want to know that is because of permssion precedence: Linux (user>group>Other)  (local > Domain) > Filesystem > ShareType: In that order, the highest permission has to exist somewhere to the left, for it to exist to the right, meaning you can take away, but you cannot add to something that is not there.

So if the directory is rwxr-xr-x (755), then a default file created within would be same(by a user that had write permissions to that directory). if you manually set the directory permissions to 775, then the default permssions of file created within would be that permission. 

Does that make sense?

---

### Post by David_Woods on 2016-06-26
No that's not it. I'm sharing it through VirtualBox's internal folder sharing mechanism and the parent folder is 775. I think it might have to so with the umask that virtualbox is using. It seems it's not using the system default but I can't figure out how to change it.

---

### Post by Morbius1 on 2016-06-26
Is the guest OS Mint by any chance?

Your conjecture about the default umask may be correct but it's not with VBox. It's because the default umask that Mint inherits from Ubuntu ( 002 ) is overridden by it's mdm display manager of all things ( 022 ).

---

### Post by Habitual on 2016-06-26
**files** come up as 755?

---

