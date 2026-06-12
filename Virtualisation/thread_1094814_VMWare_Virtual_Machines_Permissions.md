---
title: "VMWare Virtual Machines Permissions"
date: 2009-03-13
forum: Virtualisation
---

### Post by RealG187 on 2009-03-13
I am trying to backup my Virtual Machines by copying the folders for them to a different drive but I get this error:

> [SIZE="5"]Error while copying "Virtual Machine.vmxf".[/SIZE]

There was an error copying the file into /home/mpg/Desktop/untitled folder.

Show more _d_etails
Error opening file: Permission denied

Before I ran Nautilus as root and it still didn't work until I changed the permissions, I did that but VMWare acts funny, I cannot make new harddisks and it says "datastore not found" if I am lucky I can make one but Windows setup says it cannot detect a harddrive, I made a new datastore but I cannot back it up, and I do not want to mess with the permissions again...

---

### Post by HermanAB on 2009-03-13
You now have some files that belong to root in your home directory, which is why VMware acts funny.

This will set all your user ownership back to what it should be:
$ sudo chown -R mpg:mpg /home/mpg

Cheers,

Herman

---

### Post by RealG187 on 2009-03-13
I am not sure  they are owned by root, because I get that error even as root.

---

### Post by jenkinbr on 2009-03-19
What do you see when you click the chevron next to "Show more details"?

---

### Post by RealG187 on 2009-03-19
It says:

Error opening file: Permission denied

---

