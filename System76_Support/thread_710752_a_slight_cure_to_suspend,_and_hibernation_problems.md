---
title: "a slight cure to suspend, and hibernation problems!"
date: 2008-02-28
forum: System76 Support
---

### Post by kevin11951 on 2008-02-28
Ok, if this has been talked about, or is common knowledge please excuse my ignorance.

If you enter:

```
gksudo gedit /etc/default/acpi-support
```

and amend

STOP_SERVICES=""

as

STOP_SERVICES="networking"

it seems to make it so that networking (ie. wireless) works after hibernation, and suspend!

p.s. for typo reasons (just in case), here is the original how to: [http://ubuntuforums.org/showpost.php?p=4346978&postcount=7](http://ubuntuforums.org/showpost.php?p=4346978&postcount=7)

---

### Post by steveneddy on 2008-02-28
My suspend works great with 5 second wake ups, but I would like to get hibernate working.

---

