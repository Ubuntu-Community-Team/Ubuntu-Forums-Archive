---
title: "GNU Image Manipulation Program Removal"
date: 2021-03-31
forum: Ubuntu/Debian BASED
---

### Post by artist-wavenet on 2021-03-31
In my Ubuntu 18.04's Dash menu there are two GIMP installations that show up. Here are the details that show when these two launchers are edited:
> GNU Image Manipulation Program 2.10.20
env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/gimp-simosx_gimp.desktop /snap/bin/gimp-simosx.gimp %U

GNU Image Manipulation Program 2.10.22
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@

The version numbers in the names was inserted by myself so I can tell them apart.

I strongly suspect version 2.10.20 was installed with a snap command. Version 2.10.22 was installed using the Software Center. I need to remove version 2.10.20. The command:
> sudo snap remove gimp

 does not work. Nor does:
> sudo apt-get remove gimp


How then is version 2.10.20 removed?

---

### Post by deadflowr on 2021-03-31
```
snap list
```
looks like a specific version.
Regular snap version should just be gimp_gimp.desktop.
Yours show as gimp-simosx.gimp.desktop.
So the above command should output the exact version name.

I would guess it's called gimp_simosx

---

### Post by ajgreeny on 2021-03-31
I do not use snaps at all and have removed snapd so can not search for gimp snap version but you can run command ```
snap list
``` to see what snaps are installed.

The list should include ***gimp*** which may be known by a name and if that is different from just ***gimp*** you will need to use command ```
sudo snap remove ***name-of gimp***
```

EDIT:
Too slow; beaten to it by deadflowr

---

### Post by artist-wavenet on 2021-03-31
I had already done the command:
```

sudo snap remove gimp_simosx
```
No version of gimp appears in response to the command "snap list". Yet version 2.10.20 remains in the Dash menu.

---

### Post by vanadium on 2021-04-02
First one should be removable by "snap remove gimp-simosx", second one by "flatpak remove org.gimp.GIMP".

---

