---
title: "How to mount encrypted directory"
date: 2014-08-31
forum: Security
---

### Post by ppks on 2014-08-31
I recently upgraded my ubuntu 12.04 to 14.04. I chose the option that saves the files but only upgrades the systems files. 

After the upgrade the disk space still shows the percentage used, which means the data was not erased.

However when I go to Computer/home/

I see the previous **12.04** folder(with old username) and the current updated **14.04** folder(with new username)

When I access the old folder, there is an Icon(Access your private Data.Desktop) that I could double click and a read me file with instructions on how
to mount the directory.

Although when I do nothing happens nor is any folder mounted.

I have tried browsing the folder and accessing the '**Access your pprivate Data.Desktop**' icon through '**sudo nautilus**'
I also run the ' **sudo ecryptfs-recover-private '** after a few prompts, this was the output;


[FONT=courier new][B]Inserted auth tok with sig [3b0b09e5e5418b4d] into the user session keyring
fopen: No such file or directory[/B][/FONT]


Does anyone know how to go about this?

Thanks

---

