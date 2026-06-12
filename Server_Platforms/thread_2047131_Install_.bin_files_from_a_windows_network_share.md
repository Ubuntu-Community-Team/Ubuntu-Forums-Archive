---
title: "Install .bin files from a windows network share"
date: 2012-08-24
forum: Server Platforms
---

### Post by kunal_nba on 2012-08-24
Hi..

I have some .bin installation packages in a Windows network share.

I want to install this packages in a Ubuntu Server 12.04 with very little disk space, so I would like to install it directly from the Windows Network  share, Something like:

\\WinServerName\folder\Package.bin --mode text

Is it possible to do this? 

Thanks.

---

### Post by darkod on 2012-08-24
Depends. The .bin will have to be executable so it can start the installation but in windows the linux permissions are not used.

In any case, I don't think you can do it with //servername/sharename. You need to have it mounted first. If you don't mount this share permanently, you can mount it temporarily at /mnt for example, so the command to run the .bin would be something like:
/mnt/path/file.bin

However I doubt it will work directly from the windows share.

---

### Post by SeijiSensei on 2012-08-24
Write the files to a CD or USB pendrive and install them from there.

---

