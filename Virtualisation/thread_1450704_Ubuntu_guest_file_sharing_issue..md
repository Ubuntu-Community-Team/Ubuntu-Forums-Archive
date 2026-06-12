---
title: "Ubuntu guest file sharing issue."
date: 2010-04-09
forum: Virtualisation
---

### Post by GARoss on 2010-04-09
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

Using the above tutorial I can share a file with my Mac host. But, I get an error when trying to make it mount automatically (mount -t vboxsf share /home/<username>/host) - *failed with the error: Invalid argument*.

The shared host folder is VB_Mac_Share & the mount point in Ubuntu is Community so in the terminal I typed in *sudo mount -t vboxsf VB_Mac_Share /home/george/Community*. 

Any ideas why this would be an *Invalid argument*?

---

### Post by dcstar on 2010-04-10
> **GARoss said:**
> [http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

Using the above tutorial I can share a file with my Mac host. But, I get an error when trying to make it mount automatically (mount -t vboxsf share /home/<username>/host) - *failed with the error: Invalid argument*.

The shared host folder is VB_Mac_Share & the mount point in Ubuntu is Community so in the terminal I typed in *sudo mount -t vboxsf VB_Mac_Share /home/george/Community*. 

Any ideas why this would be an *Invalid argument*?

And you are 100% sure that the "_" characters in the share name are legal?

---

