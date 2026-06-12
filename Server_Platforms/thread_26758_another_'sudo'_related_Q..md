---
title: "another 'sudo' related Q."
date: 2005-04-13
forum: Server Platforms
---

### Post by rich.bae on 2005-04-13
Hi there.
 
This can be a stupid Q but I can't help it.

How can I change permission of root made directory which have root-only permission.
Yeah, I know about sudo. 
so I tried like this 

#sudo chmod 777 <somewhere>

but, It didn't work.
Why?

Please tell me how and why. 

Thanks 

P.S. If you can, Please let me know document that I have to read about it.

---

### Post by bored2k on 2005-04-13
> If you want to transfer ownership of a whole section of a tree, you can use:

chown -R user.group /path/to/subtree

-R means "recursive." 

For more information, check out these two great wikis:


[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
[http://wiki.linuxquestions.org/wiki/Chown](http://wiki.linuxquestions.org/wiki/Chown)

---

### Post by rich.bae on 2005-04-13
Thanks bored2k

I want to aplogyze :-)

I had have to say that
I want to change permission of FAT32 mounted directory
from root only writing permission to everybody can read+write permission.
it means every normal root permission directory permission can be changed,
but permission of FAT32 mounted directory can not be changed.

Thank you.

- Rich bae

---

### Post by Fab on 2005-04-14
[QUOTE=rich.bae]Thanks bored2k

I want to aplogyze :-)

I had have to say that
I want to change permission of FAT32 mounted directory
from root only writing permission to everybody can read+write permission.
it means every normal root permission directory permission can be changed,
but permission of FAT32 mounted directory can not be changed.

Thank you.

- Rich bae[/QUOTE]
 youll need to edit your /etc/fstab to add/change the umask setting for that mounted partition (if its automounted in fstab)
if you manually mount it everytime, youll need to adjust your mount command
there are pretty many tutorials for this out there, search for fstab vfat, howto mount, ...

---

