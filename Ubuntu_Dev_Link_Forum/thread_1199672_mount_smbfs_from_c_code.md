---
title: "mount smbfs from c code"
date: 2009-06-29
forum: Ubuntu Dev Link Forum
---

### Post by cmpn76 on 2009-06-29
Hi,
I've tried to run this simple (and probably incorrect) code

 int main()
{


int rtn= mount("//server/D", "/mnt/server_D",
                 "smbfs", MS_MANDLOCK,
                 "username=Administrator,password=password");
if (rtn!=0)
        perror("mount");
return rtn;
}

The results seems to be all the time

mount: Invalid argument

from dmesg I've got

smbfs: mount_data version 1919251317 is not supported

Googling for it I discovered that smbfs need to be installed and I did it, but the problem is still there.

if I tried the following CLI command

sudo mount -t smbfs -ousername=Administrator,password=password //server/D /mnt/server_D

Everything works fine. It seems that I've to tell my program to load/use smbfs module.

Any idea how to help me? 

Thanks in advance

---

### Post by WRDN on 2009-06-30
You are trying to call a system command but C thinks it is a method.

To call a system command, you can use code like this:

```

#include <stdlib.h>

int main()
{
    system("ls -a");
    return 0;
}

```

---

