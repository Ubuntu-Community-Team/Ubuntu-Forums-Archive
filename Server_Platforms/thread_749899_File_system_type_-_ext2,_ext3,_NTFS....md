---
title: "File system type - ext2, ext3, NTFS..."
date: 2008-04-08
forum: Server Platforms
---

### Post by garfonzo on 2008-04-08
Here's a question...

If I set up a server running Ubuntu which acts as a file server, which file system should I use(question mark)
( my keyboard has fallen into french mode and I canèt fix it... so annoying, anyway)

I want the Windows machines on my network to have their "My Documents" folder mapped to a partition on the hard drive of my server. I know that the latest release of Ubuntu has, by default, the ability to read and write in the NTFS format. However, doesnèt Ubuntu by default use the ext2 or ext3 file system(question mark). 

If so (if I have ext2) is there ANY worry about Windows machines dropping files on the server's hard drive(question mark)

Cheers!

Garfonzo

---

### Post by ibutho on 2008-04-08
You can have your filesystem as ext3 or any other Linux filesystem and your Windows clients will still be able to access the files without any problems when using SAMBA. I would suggest you use ext3 instead of ext2 because ext3 because of the journalling features of ext3.

---

### Post by garfonzo on 2008-04-08
So, user A creates a new Excel file and saves it to the Server's hard drive which is using ext3. This is completely OK and is just as safe as having the Excel file saved to the Windows box's own local hard drive(question mark)

I have no idea what features exist for ext3. Ièll have to look into it...



this stupid french keyboard setting is really annoying! How are they supposed to write a question markÉÉÉÉÉÉ

---

### Post by ibutho on 2008-04-09
> **garfonzo said:**
> So, user A creates a new Excel file and saves it to the Server's hard drive which is using ext3. This is completely OK and is just as safe as having the Excel file saved to the Windows box's own local hard drive(question mark)...
Yes to all questions.

---

