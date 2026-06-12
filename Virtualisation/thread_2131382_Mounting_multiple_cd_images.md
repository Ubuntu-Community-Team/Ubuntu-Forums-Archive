---
title: "Mounting multiple cd images"
date: 2013-04-01
forum: Virtualisation
---

### Post by wolf187 on 2013-04-01
Hello, I'm not sure if this is in the right area, I need to know how to mount multiple cd images,this is because the program I am installing needs CD 2 to copy data from, I tried AcetoneISO, Furius ISO mount with fuse and loop, and i even tried extracting the ISOs and putting them together inside one folder and then renaming the autorun.inf and autorun.exe but still nothing helps at all, is there another program that can do this, it's just that it loads CD 1 fine but asks for CD 2 eventhough I tried mounting it in various ways.

---

### Post by schragge on 2013-04-03
[uhelp]community/MountIso[/uhelp]

---

### Post by Habitual on 2013-04-03
```
    # mkdir -p /mnt/{1,2}
    # mount -o loop /path/to/file1.iso /mnt/1
    # mount -o loop /path/to/file2.iso /mnt/2
```

---

### Post by wolf187 on 2013-04-04
Thanks but none of those work with mounting the isos,it still cannot detect the second disc that is mounted.

---

### Post by Hexxus on 2013-04-05
Are you getting any type of an error?

---

