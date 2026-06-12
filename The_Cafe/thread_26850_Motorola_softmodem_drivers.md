---
title: "Motorola softmodem drivers"
date: 2005-04-14
forum: The Cafe
---

### Post by SilvioTO on 2005-04-14
I find this page on motorola site...
[http://www.motorola.com/softmodem/driver.htm](http://www.motorola.com/softmodem/driver.htm)

Don't find any .deb packages... anyone to able convert .rpm to .deb? or try to make this experiment?
My friend have a pci modem 56k motorola and I like to work in ubuntu hoary.

For example, I tryed to unpack an rpm packages downloaded from site, and, in a tmp directory is, I think, useful files and libs, but I don't know where put it.

Experts, lets go!!  :-P

---

### Post by p!=f on 2005-04-14
You can always use alien to convert RPM, TGZ, etc. packages to DEB ones but it may not work if you install them then.
```

sudo alien -d <some_package.rpm>

```

---

