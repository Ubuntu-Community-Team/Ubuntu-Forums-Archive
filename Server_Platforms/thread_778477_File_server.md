---
title: "File server"
date: 2008-05-02
forum: Server Platforms
---

### Post by vkarthickeyan on 2008-05-02
Please give me your suggestion for implementing a file server in Linux. Following are my requirements 

1.	All my clients are login into the windows platform, they should automatically connect to their corresponding network share.
2.	Rights should be assigned for individual user & group 
3.	In the rights option user can able to read, write & append option but delete option should be controlled by administrator.
4. File screening option should be available.

Regards,
Karthick.V

---

### Post by duckville on 2008-05-02
I would assume you want to use a Samba server running Debian or Ubuntu.
you can set the valid users along with thier access rights.

What I don't understand is:
allow write access, but not delete...?
as far as I am aware in rwx (read, write, execute) w allows for files to be edited (also deleted).
Not sure how you're gonna get around that, maybe some else could help.
These links should give you a start:

[http://www.debianhelp.co.uk/samba.htm](http://www.debianhelp.co.uk/samba.htm)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by njparton on 2008-05-02
Check out openfiler and freenas as specific distros for this sort of thing (and there are others).
 
Openfiler is probably the one to go for.

---

### Post by tshrinivasan on 2008-05-02
In windows, there is some options like user can create and write files in a folder, but  can not delete files.

How to configure this in a samba share?

Is FreeNAS and OpenFiler give these options?

---

### Post by njparton on 2008-05-02
Openfiler is a lot more powerful than samba, I'd download their free user guide and have a read.

---

### Post by Deathrend on 2008-05-02
Sounds like your best bet would be a SAN LUN.  For the kind of permissions you want, you'll have to stick to NTFS, which means Linux is not the way to go for managing the files.

I've just started playing with a new build of 8.04 64bit server using iscsitarget (Apt package) which lets me use it as a SAN.

If you use Vista, it has the client portion of the iSCSI, from there you just need to set up the Target (The SAN).  OpenFiler and FreeNAS both can act as iSCSI SANs.  

Something to consider, OpenFiler is a lot more powerfull, however it's overly complicated.  It will work with ActiveDirectory but not /great/.  With my setup, your file systems reside in Linux, however are managed by Windows.

---

