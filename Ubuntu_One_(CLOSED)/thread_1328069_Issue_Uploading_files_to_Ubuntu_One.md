---
title: "Issue Uploading files to Ubuntu One?"
date: 2009-11-16
forum: Ubuntu One (CLOSED)
---

### Post by mustanglover32 on 2009-11-16
I have had a lot of problems uploading files to Ubuntu One.  All of these problems disappeared when I did one simple thing.

**I removed file spaces in the files I was trying to upload.**

That simple.
:D
Hope this helps somebody out there.




David

---

### Post by olalaaa on 2009-11-16
well, then how did you succeed to rename the folder "My Files" into "My_Files", "My-Files" or even "MyFiles" ?

I was not able to do that into my online webpage of U1....

---

### Post by mustanglover32 on 2009-11-23
> **olalaaa said:**
> well, then how did you succeed to rename the folder "My Files" into "My_Files", "My-Files" or even "MyFiles" ?

I was not able to do that into my online webpage of U1....

Just the files that you upload need to be space free.  The naming format of the online folder (My Files) bears no consequence on uploading files.

David

---

### Post by joshuahoover on 2009-11-24
> **mustanglover32 said:**
> I have had a lot of problems uploading files to Ubuntu One.  All of these problems disappeared when I did one simple thing.

**I removed file spaces in the files I was trying to upload.**

That simple.
:D
Hope this helps somebody out there.

David

This is very strange. You shouldn't have to remove spaces from filenames in Ubuntu One. Is it possible the file names had invalid UTF-8 characters in them? If you look at ~/.cache/ubuntuone/log/syncdaemon-exceptions.log files, do you see any errors there? 

Thank you,

Joshua

---

