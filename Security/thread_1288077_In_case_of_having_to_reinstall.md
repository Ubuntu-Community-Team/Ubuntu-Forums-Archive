---
title: "In case of having to reinstall"
date: 2009-10-10
forum: Security
---

### Post by sopadeajo on 2009-10-10
I read a thread where LovigLinux said that we all should have a kind of short (marking) backup file that i call synaptic-backup in our home folder, obtained this way:

dpkg --get-selections > ~/synaptic-backup


In case of reinstall:

 1) update completely with Update Manager. (important to do it as the first step)
If this is not done a lot of problems and incompatibilities will raise if you import your old home folder configured for recent versions.

2) It is not necessary to have your home folder situated in a different partition than the root, so that it will not be formatted when reinstalling. Just keep a copy of your home folder in a removable device and copy it back on your file system once reinstalled and after updating. (remember to update first).

3) In a Terminal run:

sudo dpkg --set-selections < synaptic-backup

LovingLinux added  this line : && sudo apt-get dselect-upgrade

I am not sure it is necessary (hope LovingLInux read this and tell us).

It will install all the programs you installed with synaptic or with Terminal automatically all in a row.

And that's all. 
You're reinstalled in the same conditions as before including Firefox bookmarks and Firefox add-ons.

---

