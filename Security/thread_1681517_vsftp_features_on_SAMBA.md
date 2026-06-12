---
title: "vsftp features on SAMBA"
date: 2011-02-04
forum: Security
---

### Post by cifar24 on 2011-02-04
I am migrating a windows file server to Ubuntu. The server is assumed to be connected with virus infected windows workstations. I have created a shared folder which is writeable by the authorised Samba users. 

Some of the workstations on the LAN have a virus that creates un-necessary shortcuts (.lnk) files when a samba user clicks on a shared folder. Since the authorised user has write access, the virus is able to write the .exe file and create hundreds of .lnk files etc. 

I want to configure the linux file system in such a way that any file that is named *.exe can not be written into the shared folder. 

We can setup the VSFTP program to disallow certain extensions during the FTP. Can we do the same on Samba or in the Linux file system to disallow the files to be named *.exe? 

Since most of the windows virus are executable applications with .exe extension, not allowing an exe file in the shared samba folder will significantly add the security of a shared folder. Any help or suggestion would be highly appreciated.

---

### Post by CharlesA on 2011-02-04
As far as I know you can't do that. The best thing to do would be to clean all the workstations of this 'virus'

---

