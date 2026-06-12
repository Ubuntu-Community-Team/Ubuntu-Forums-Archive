---
title: "Update Manager errors"
date: 2011-06-25
forum: System76 Support
---

### Post by DNAtsol1 on 2011-06-25
Finally had a second to look into why I haven't been able to download software from the software centre before I even got to trying to solve that problem I found I have not been updating. 

I ran update manager and got the following:
_______________________________________
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
______________________________________________

A little help on how I get update manager back online would be most appreciated. 

Thanks
DNAtsol

Running 11.04
64-bit, lemur laptop

---

### Post by jerrrys on 2011-06-26
i have had success in the pass by renaming the file and see if it will regenerate the correct file.  i have found if they regenerate, that the problem usually will be solved.

---

### Post by Rubi1200 on 2011-06-26
The following commands should solve the problem:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by DNAtsol1 on 2011-06-26
Thanks Rubi1200. 

Those little commands not only seemed to solve my update problem but also by inability to access the software centre.

All is now well in Lemurland :P

DNAtsol

---

### Post by Rubi1200 on 2011-06-27
Excellent! I am really pleased you got this sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

