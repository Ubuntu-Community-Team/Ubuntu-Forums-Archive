---
title: "How to write a batch file to copy files?"
date: 2008-02-17
forum: Windows
---

### Post by billdotson on 2008-02-17
I have a flash drive that I put a batch file on that when I run it it copies files from the hard drive to the flash drive.  Works fine, except depending on how many drives I have in the drive letter changes.

So what I want to know is how to write the batch file so that when I run it the script will automatically adjust and copy them to the right drive letter.  I would have searched myself, but I did not know a good set of search parameters.  Thanks.

---

### Post by pdub on 2008-02-17
I am going to assume you are running Windows since you are using batch files and drive letters. You said the batch file is on the USB drive so you could do something like this.

Lets say you are copying files from c:\data to the key and you want to put them into a folder called backup on the key.


copy c:\data\*.* \backup

or

xcopy  c:\data\*.* \backup /s/e

This way you don't really care what the drive letter is as long as you run the batch file from the key it should work.

---

### Post by billdotson on 2008-02-17
That works, thanks.

---

### Post by sayakb on 2008-02-18
You may also create a briefcase in your flash drive. Just press "Update" in the briefcase so that the files would be synced..

---

