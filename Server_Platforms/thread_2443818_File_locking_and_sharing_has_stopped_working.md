---
title: "File locking and sharing has stopped working"
date: 2020-05-20
forum: Server Platforms
---

### Post by jamarsh123 on 2020-05-20
I am running a small office network on an Ubuntu server 18.04 with Samba. Most of the regular computers are Ubuntu, with one 14.04, one 16.04, four Linux Mint 18.04. There are two Win 10 computers and one apple, hence the need for Samba. We also use Libreoffice extensively, particularly Calc and Write. This setup has been running for years, mostly problem free.
Recently, I noticed a problem with file locking. Previously, if a file was in use, the second user would be able to open the file read-only, or a copy of the file. Now, the second user sees a message that the file is corrupt and Libreoffice will attempt to recover the file. So the second user is unable to view the file. Since there are three layers involved, Ubuntu, Libreoffice or Samba I don't know where the problem lies. 


This is not an urgent issue, as we are able to continue operating. Still, it is irritating, and web research up to this point has not yielded any good clues. Any help would be appreciated.

---

### Post by LHammonds on 2020-05-20
When LibreOffice (or other office apps) opens a file for editing, they create hidden lock files.  The app itself knows if someone else has it open.  I am curious to know if you are using a wide-range of different versions of LibreOffice...such as one user with a current version of LibreOffice and the other trying to open it with an ancient version...which does not recognize the file properly and claims it is corrupt.

I noticed you listed some very old versions of operating systems so I wonder if LibreOffice has also slipped on the updates too.

If I were you, I'd get all of the free operating systems updated to the current release version AND get everyone on the same version of LibreOffice to reduce risk of compatibility issues.

LHammonds

---

### Post by jamarsh123 on 2020-05-28
Thank you for your reply. Your comments are helpful and lead me to suspect the problem lies with LibreOffice. I get your point about having all versions up to date, although I am reluctant to at the moment. However, in that vein, I did a small test when the office was closed. I used 2 computers with the exact same OS and version of LO. I opened an odt file on one computer and then tried to open the same file on another. "Due to an unexpected error" message still pops up.

---

### Post by LHammonds on 2020-05-29
Well, without access to the system or logs, the difference in LO version was my best guess.

Was the test on an existing file that has had problems before or did you create a new file and see if the problem persisted even with a previously error-free file?

Does the problem only happen to files being shared off the 18.04 server?  Can you test by making a share on a PC and seeing if you get the same results that way.

If problem is isolated to just the file server, maybe something is broken with the normal procedure for locking a file such as permissions problem for a temp location or space issue in a partition.

LHammonds

---

### Post by jamarsh123 on 2020-06-06
Well, I haven't yet tried creating a local share, but I do have some more info to report. I found some info regarding accessing 'remote files' via LibreOffice. I selected the 'Windows Share' option and filled the dialog box with Host (ip address of server), Share name, User and Password. After successfully connecting, I could see the new connection showing in the Ubuntu file manager under Network. It seems that all the security is working properly, and the computers are prevented from accessing shares if they are not part of the group. 

If I open LibreOffice files via this link, and then open the same file on another computer, also using the new link, the expected dialog box displays: 'Document is locked for editing by another user, To open a read-only copy of this document, click...', So all seems to work properly using the 'Remote Files' feature in LibreOffice. Despite the fact that using this service seems to be redundant, since all the shares are mounted via the fstab file, I would be willing to compromise and use this service. The only problem is that if the computer is restarted, all the links have to be reestablished. 

Could it be that this is some sort of bug that has appeared in the networking aspect of LibreOffice?

---

