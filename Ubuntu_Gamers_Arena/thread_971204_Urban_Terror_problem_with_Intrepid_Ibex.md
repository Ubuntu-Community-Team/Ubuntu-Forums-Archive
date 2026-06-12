---
title: "Urban Terror problem with Intrepid Ibex"
date: 2008-11-04
forum: Ubuntu Gamers Arena
---

### Post by downisthenewup on 2008-11-04
Ever since I upgraded to 8.10, I get this error when trying to start up Urban Terror-

```
[/home/nico/Documents/Urban Terror/UrbanTerror/ioUrbanTerror.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/nico/Documents/Urban Terror/UrbanTerror/ioUrbanTerror.exe or
          /home/nico/Documents/Urban Terror/UrbanTerror/ioUrbanTerror.exe.zip, and cannot find /home/nico/Documents/Urban Terror/UrbanTerror/ioUrbanTerror.exe.ZIP, period.

```

---

### Post by littletinman on 2008-11-11
run it in wine. It should work fine. It did for me anyways.

---

### Post by rerendered3 on 2008-11-29
What architecture are you using?
In my case (32 bit) I got the *.i386 version and made a shell script to link to it

in my case:
Urbanesque.sh
```
cd .Games && cd UrbanTerror && ./ioUrbanTerror.1386
```

Then I just added an icon in the menu and linked it to ```
sh Urbanesque.sh
```

(I have no idea why I called it that)

All of that is a modified version of the 64 bit install guide in the Ubuntu Gamers Arena thanks to Artificial Intelligence.

That may or may not work for you, experiment around a little bit. Personally I would rather write a one-line shell script than mess with Wine.

---

