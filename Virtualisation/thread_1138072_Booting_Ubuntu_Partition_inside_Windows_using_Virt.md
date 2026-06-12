---
title: "Booting Ubuntu Partition inside Windows using VirtualBox"
date: 2009-04-26
forum: Virtualisation
---

### Post by Jexel on 2009-04-26
I've seen plenty of tutorials on google on how to boot an existing Windows Xp partition inside Ubuntu, however, I can't seem to find any information on the reverse.

I've read the guide [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883) and have attempted to create the vmdk file with success. However, when I try to load it in VB it gives me the error

```
Result Code: 
E_FAIL (0x80004005)
Component: 
HardDisk
Interface: 
IHardDisk {91648dc6-bb19-46bf-9e1c-4bf5b960c8e2}
Callee: 
IVirtualBox {779264f4-65ed-48ed-be39-518ca549e296}

```

I believe it may be todo with the vmdk file referencing the linux format of /dev/sda1 rather than the windows format of referencing partitions.

Does anyone have anyideas on how I can fix this problem?

Cheers.

---

### Post by Jexel on 2009-04-26
So I read the manual on "Using a raw host hard disk from a guest"

Here is what I did.

I identified the partitions I needed using the command:

```
VBoxManage.exe internalcommands listpartitions -rawdisk \\.\PhysicalDrive1
```

It gives me the result

```

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x07  0   /32 /33  1023/254/63        902023         2048
5       0x83  1023/254/63  1023/254/63         49677   1847346543
6       0x82  1023/254/63  1023/254/63          2164   1949086188

```

5 is the ext3 partition and 6 is the swap.

So I then proceeded to creating my vmdk file

```
VBoxManage.exe internalcommands createrawvmdk -filename "C:\path\ubuntu1.vmdk" -rawdisk \\.\PhysicalDrive1  -partitions 5,6 -register
```

I then assign the vmdk file to my VM and try starting it.

It gives me the error:

```
FATAL: INT18: BOOT FAILURE
```

Any ideas?

---

### Post by Jexel on 2009-04-28
nvm, forgot to mount grub iso

---

