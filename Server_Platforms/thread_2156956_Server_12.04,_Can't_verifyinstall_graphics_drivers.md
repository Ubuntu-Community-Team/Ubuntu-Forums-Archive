---
title: "Server 12.04, Can't verify/install graphics drivers, don't know how."
date: 2013-06-23
forum: Server Platforms
---

### Post by JamesDonaldChilds on 2013-06-23
I HAVE Google'd this and was unable to turn up anything to verifying the drivers are installed and how to install the drivers if they are not. I know this sounds weird but there is a program that requires me to select a GPU core to run and I want to make sure it runs as good as possible. Any help appreciated.

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]JamesDonaldChilds;
To see what is going on with graphics:
[/COLOR]```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

Post the output back here in the event you require interpretation of the results.
[INDENT=2]
just try'n to help

[/INDENT]

---

