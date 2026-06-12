---
title: "Cannot set CD file as 'executable' (read-only; (language program ) ). Help?"
date: 2011-03-24
forum: Wine
---

### Post by Moozillaaa on 2011-03-24
edit: 
little progress here...

From command prompt, change directory to CD drive, 
```
$ wine Instal32.exe
fixme:shell:Dde_OnRequest returning fake program groups list
fixme:heap: RtlCompactHeap (0x449000, 0x0) stub
```Help?

Neither of the 2 previous errors returns in google (one does, but only 1 instance ever; not applicable)

[B]edit: found scstub.exe, executed, solved.

Thank me SOOO much!!![/B]

---------------------------
I'm trying to run a language program that's on a CD. I have WINE installed, but I don't know what my error is exactly (I seem to be hanging at 2 different errors, depending on if I try front end or back end startup).

One approach is permission. I tried to mark as 'executable' the AUTORUN.INF file, but being on a CD, it's returning a read-only error.

The other error seems to be after I clicked on the .exe files (of the CD), and the return is, "cannot find zipfile directory".

Little help there please...

---

### Post by Moozillaaa on 2011-03-24
Solved!

---

