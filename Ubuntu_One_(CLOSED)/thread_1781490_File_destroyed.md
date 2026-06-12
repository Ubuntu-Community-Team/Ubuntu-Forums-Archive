---
title: "File destroyed"
date: 2011-06-13
forum: Ubuntu One (CLOSED)
---

### Post by pocklecod on 2011-06-13
I'm writing in a state of shock.

I just sat down at my desk to work on a file I've put the last several weeks into.  It is in a documents folder synced to Ubuntu One which I've been using for some time.  The file now has 0 bytes, and is totally empty.  It has been uploaded to the Ubuntu One system as a 0 byte file, and replaced on all my machines as a 0 byte file.

My document is destroyed.  I have a big part of it backed up on one of my machines through libreoffice, but I've lost a lot of it forever and have to recreate it.

Why would this happen?  What can be done about this?  There was absolutely no problem with the machine on which I last saved the file, there was no problem with the save....why did this happen....

---

### Post by pocklecod on 2011-06-13
I'm writing in a state of shock.

I just sat down at my desk to work on a file I've put the last several weeks into.  It is in a documents folder synced to Ubuntu One which I've been using for some time.  The file now has 0 bytes, and is totally empty.  It has been uploaded to the Ubuntu One system as a 0 byte file, and replaced on all my machines as a 0 byte file.

My document is destroyed.  I have a big part of it backed up on one of my machines through libreoffice, but I've lost a lot of it forever and have to recreate it.

Why would this happen?  What can be done about this?  There was absolutely no problem with the machine on which I last saved the file, there was no problem with the save....why did this happen....

---

### Post by doas777 on 2011-06-13
you can try running fsck on your disk to see if there is any filesystem damage, but I am inclined to blame ubuntuone. synching apps can do unexpected things at times.

---

### Post by Joe of loath on 2011-06-13
Sometimes these things just happen. Have you checked the web interface for Ubuntu One? I know dropbox saves revisions of files, so you can go back to an earlier one if necessary.

Also, back up back up back up! Write a bash script to rsync your important files and any changes to a backup folder, archive it to USB stick or CD regularly (Tape is preferable, but tape drives are expensive).

---

