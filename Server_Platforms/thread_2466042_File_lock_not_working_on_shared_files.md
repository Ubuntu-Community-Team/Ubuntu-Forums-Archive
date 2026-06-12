---
title: "File lock not working on shared files"
date: 2021-08-18
forum: Server Platforms
---

### Post by krillian on 2021-08-18
Hi,

Have the following problem that I am trying to solve, any help would be very much appreciated.

Have a Linux machine with an SMB file server sharing standard office documents. Users connect to it via Windows machines. When they open a file on their Windows machine, the file on the server does NOT get locked. So if another user opens the same file on their machine, they will essentially be able to edit the file simultaneously. I need to stop them from doing that. The file should only be editable by one user at a time.
On a windows server this is not an issue, file is locked when it is opened and unlocked when it is closed.
How can I achieve the same result with a Linux server?
 
Thank you very much in advance!

---

### Post by LHammonds on 2021-08-18
Doesn't MS Office create lock files in the same folder with a similar filename so that if anyone tries to open the same file, Office notices that file and warns the end-user the file is locked?

Are those files not allowed to be created?

LHammonds

---

### Post by krillian on 2021-08-18
I will check and get back to you!

---

### Post by Doug S on 2021-08-18
I tried your situation, as a test. I have this file on my 20.04 test server:

```
-rw-rwxr--+  1 doug doug   22582 Jun 29 16:48  bla6.xlsx
```

I opened that file using my Windows 10 computer and Excel, which created this file:

```
-rw-r--r--   1 doug doug     165 Aug 18 11:27 '~$bla6.xlsx'
```

I then went to my wife's windows 10 computer, mapped the network drive, and tried to open the same file with Excel and got the normal "The file is already opened for editing by someone else. Do you want to open it as read only" or similar.

---

### Post by krillian on 2021-08-20
Thank you for that, could you please let me know the permissions of the directory that that excel file is in?

---

### Post by krillian on 2021-08-20
Right, so sharing the folder with correct permissions now. Opening a file on a Win7 machine and trying to open on another, everything as it should be, file is a read only mode. The ~$ gets created as it should.

However if I try top open the same file from a 3rd Linux machine it gives no errors (assuming that's a LibreOffice issue?) but if I change the file on a Linux machine it won't let me save it, sharing violation.

Second however is that if I first open the file on a Linux machine and then on a Windows one, the Windows machine seems oblivious to the fact that the file is already locked. Looking at the directory, the same ~$ type file does not get created when opening the file on Linux with LibreOffice. Perhaps this is a LibreOffice option that I need to enable somewhere?

Update:
LibreOffice seems to create a file .~lock. is there a way to make LibreOffice and MSOffice use the same lock file? Can't imagine I am the first person with this problem :)

---

### Post by TheFu on 2021-08-20
> **krillian said:**
>  
Update:
LibreOffice seems to create a file .~lock. is there a way to make LibreOffice and MSOffice use the same lock file? Can't imagine I am the first person with this problem :)

Why not have MSOffice create the correct lock filename for LibreOffice?  Just depends on one's perspective, I suppose.

Workplaces usually standardize on 1 productivity suite, so it isn't usually an issue. LibreOffice is available for MS-Windows platforms, BTW.

I don't think the OS-level locking that Linux can use maps to what Samba does, BTW.

---

### Post by krillian on 2021-08-23
Either way way would be fine TBH :) 

Is there a standard way to lock office related files while sharing? Or not set standard exists?

---

### Post by TheFu on 2021-08-23
Typically in Linux, there isn't file locking so the last person to write to the file wins.  That's the expected behavior unless the admin sets up something different. File locking system calls exist and it is up to the application to choose to use those or not.  Every application can do it different or not at all. It is something the application development team handles, not the OS or file system.

This is just another reason why Unix people are so big with automatic, daily, versioned, backups.

In 25 yrs working on teams, I think people editing the same file at the same time has caused collisions maybe 5 times.  When I worked on project teams, we'd all view the same file concurrently, but there was 1 editor in charge who would say "I've written the updates, reload" on the conference calls.  Abuword (a Linux word processor) had concurrent editing features for 20+ yrs.  We'd use that in my Linux teams.

If I were working projects today with a team needing to edit the same file, I'd setup LibreOffice online [https://wiki.documentfoundation.org/Development/LibreOffice_Online](https://wiki.documentfoundation.org/Development/LibreOffice_Online).  There are a number of different ways to get that working.  I'd probably add it to our nextcloud installation. [https://wiki.documentfoundation.org/Development/LibreOffice_Online#Integrations](https://wiki.documentfoundation.org/Development/LibreOffice_Online#Integrations)  Is isn't a 1-click install, but I can't imagine it take THAT much more. Nextcloud modules are fairly easy to add. [https://apps.nextcloud.com/apps/richdocuments](https://apps.nextcloud.com/apps/richdocuments)

If you think about all the different storage possibilities on Linux, you can understand why end-user applications really can't be trusted to handle file locking.  There's nfs, cifs, smb, sshfs, webdav, and probably 15 others.  They each have different capabilities around locking.

---

### Post by krillian on 2021-08-24
Thank you very much for the detailed response, I will give LibreOffice online a try!

---

