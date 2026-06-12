---
title: "Issues kickstarting lucid"
date: 2010-05-01
forum: Server Platforms
---

### Post by csargiso on 2010-05-01
I have the following kickstart [http://pastebin.com/PtQnuwj5](http://pastebin.com/PtQnuwj5)

This works fine for kickseeding Ubuntu hardy machines, but when being used with Lucid it complains that the kickstart file is corrupt and contains the following in /var/lib/preseed/log

```

d-i netcfg/choose_interface select eth0
d-i debconf/priority select critical
d-i preseed/url string http://installer/path/to/kickstart
auth --useshadow --enablemd5
bootloader --location=mbr --append acpi=force pci=nommconf noirqpoll
clearpart --all --initlabel
text
Syntax error: unable to determine template owner

```

Does anyone have any indicators as to what would cause this?

---

