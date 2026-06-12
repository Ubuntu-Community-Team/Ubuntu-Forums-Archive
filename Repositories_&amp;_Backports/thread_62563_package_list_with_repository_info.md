---
title: "package list with repository info"
date: 2005-09-05
forum: Repositories &amp; Backports
---

### Post by Mayday on 2005-09-05
Anyone know how to produce a list of installed packages that includes
information from what repository packages was installed?  ](*,) 

TIA

---

### Post by Swerver on 2005-09-12
I would like to know if there is a switch or a way to get this information as well.

---

### Post by agm642 on 2005-09-13
I can't find one... I looked everywhere I could think about, but it doesn't seem to store repository information at all. :(

---

### Post by dangman4ever on 2005-09-16
I had the same problem too but I found a solution! Here's what you do:

Go to your Filesystem. Go to folder 'var' then 'backups'. look for a file called "_dpkg.status.0_" 

It should be a text file. If there isn't a text file by that name, there should also be a few gzip archives that have that name but with additional numbers. _dpkg.status.1.g_z is the second latest one after dpkg.status.0.

Anyway after finding _dpkg.status.0_, copy it, paste it into your home folder and rename it _status_. 

After that, go back to the File system again.

Go to "var", then "lib" then "dkpg"

Once you're in dkpg, place the _status_ file in there and you're done! Your repositories and installed files are now restored.

You might have to chmod the folder dkpg rwx to get it working again.

---

