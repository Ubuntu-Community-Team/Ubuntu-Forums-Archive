---
title: "1 of 2 WS can't open a document on server"
date: 2008-03-17
forum: Server Platforms
---

### Post by rhardie on 2008-03-17
Problem:

We are unable to open a Word .docx file on a laptop connected to the server and we ARE able to open the same file from a second laptop.

We suspect it is a file rights issue but I don't know what to change.

This happened "suddenly", I am told.

Scenario:

Lap top A creates word document and stores on Linux server.  Laptop B can not open the file BUT it can see the file in the folder AND it can "edit" the file.  Double clicking to open the file results in an error that says "pathnam/file can not be found"

Laptop A is able to open the file.

Laptop B can create a Word.docx file in the exact same folder but when the file is closed and Laptop B attempts to open the file it just created, then it gets the same error as described above.

Exel files within the same folder behave normally and are accessable by laptop B.

All hardware and software on the network appears to work normally except this problem.

Configuration:

Server:  Ubuntu 7.10 LAMP with GUI; SAMBA
Network:  Ethernet; shared public folders and private folders on the Linux server
Laptops: Windows Vista; MS Office 2008

Notes:
User has no access to Linux server or server log in to modify folder settings.

User noted the server went to backup power (UPS) earlier in the day but didn't appear to experience power inturruptions to the server.

Thanks for any assistance.  :-)

---

### Post by Bubba64 on 2008-03-17
Open Office should open a  Microsoft word Doc If you cant open with it save it to your desktop and it should open in Open  Office or I suspect you can open it from the writer.

---

### Post by rhardie on 2008-03-19
The "we" part of my challenge insists upon Using Windows Vista on their laptop along with MS Office 2007.

The odd thing is that I can go to the laptop that can't open the Word document and actually "create" a Word document, close the document and attempt to re- open the just-created document and then I get the same error that the document can't be found.

I can see the document Icon, I can right click and "edit" the document and it opens and I can even print the document in the "edit" mode.  Just can't double click or "open" the document.

Weird.

---

### Post by rickyjones on 2008-03-19
Can you post your smb.conf file?

How are the laptops connecting to the server? Is it a mapped drive? How does this happen?

Can you post the exact error message(s) that you get on the laptops? What I mean is exactly what the pop-up box says, word for word.

Thanks,

-Richard

---

