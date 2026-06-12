---
title: "Moving  files from Samba to Windows"
date: 2009-06-12
forum: Server Platforms
---

### Post by walteruy on 2009-06-12
Please Help. I have a Samba server with over 200 GB of files with different permissions of dozens of users. I need to copy it over to our Windows 2008 File Server. Samba is running ext3fs and the Windows is ntfs. Is there a way, or a third party tool that can migrate the data without losing all the file Permissions and ownerships and other attributes?  ANY help would be appreciated.

---

### Post by HermanAB on 2009-06-13
Howdy,

Ensure that the user UID and GID are the same on both servers, run ssh server on Linux then connect from 2008 to Linux with Filezilla and copy it with scp.

---

### Post by walteruy on 2009-06-14
"Ensure that the user UID and GID are the same on both servers, run ssh server on Linux then connect from 2008 to Linux with Filezilla and copy it with scp. "
 
Since the windows doesn't uses a UID/GID security, how can this be done? Is there a user mapping utillity that does this?
 
Thanks for any help

---

### Post by koenn on 2009-06-15
> **walteruy said:**
> "Ensure that the user UID and GID are the same on both servers, run ssh server on Linux then connect from 2008 to Linux with Filezilla and copy it with scp. "
 
Since the windows doesn't uses a UID/GID security, how can this be done? Is there a user mapping utillity that does this?
 
Thanks for any help
I was wondering the same.
Maybe there's something in "Unix Services for Windows" or whatever it is called today. 

Since you seem to be migrating from Unix/Linux to Windows, you probably should ask this in a Microsoft support channel :evil:

---

### Post by ntimperio on 2009-06-15
in the windows world xcopy can preserve permissions.  However, I've only used this to move files from windows to windows, not from samba to windows.

---

### Post by swerdna on 2009-06-15
NTFS as implemented with the ntfs-3g mount in Linux doesn't duplicate Linux permissions. It honours them artificially while the drive is mounted. By this I mean that when viewed from Linux, the Linux user sees and is obliged to honour whatever permissions were imposed (artificially) by the ntfs-3g mount command. But if viewed simultaneously from the windows computer there are no permissions except the native world-writeable ones.

I think the short answer to your original question is, unfortunately, "no".

---

### Post by walteruy on 2009-06-18
Thanks guys.  I am looking into icalcs to do this.  I will update you all on how it goes.  If anyone has any other ideas on the Samba side, please let me know!

---

