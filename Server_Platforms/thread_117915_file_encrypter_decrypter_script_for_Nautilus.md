---
title: "file encrypter decrypter script for Nautilus ????"
date: 2006-01-15
forum: Server Platforms
---

### Post by HJThis on 2006-01-15
Hello,To all

Hmm am i the only one having a problem with this great
script anyone at all please.

well here is what is going on i can right click & it
encrypts the file but it leave the un-encrypted
file intact it will not delete it.

& yes i have both options = yes

but it works when i decrypt the file

Thank you

---

### Post by HJThis on 2006-01-15
Hey,All

Well i will show you what i am trying to say
this is what happens when i right click & encrypt
you can see the Test file is stell there.

Thank you

---

### Post by robert_pectol on 2006-01-18
I assume you are referring to the file encrypter/decrypter for Nautilus, found in this thread:
[http://www.ubuntuforums.org/showthread.php?t=108513](http://www.ubuntuforums.org/showthread.php?t=108513)

Well, seeing that the original file name seems to have been altered (this is one of the things wipe does when it's securely deleting files, before actually deleting them), maybe wipe isn't completing its process (doubtful, but possible). Can you still access the original file when this happens? You may need to change the filename back to whatever it was originally before trying. I'm guessing that although the file may appear to still be there, it's contents will probably have been destroyed and will therefore be inaccessible, or that or your desktop/folder hasn't refreshed itself since the file deletion and you're looking at a 'phantom file' in which case it should disappear when you try to access it.

---

### Post by HJThis on 2006-01-18
Hello,robert_pectol

First thanks for your time on this
yes the original file name get's altered
but that's it i can stell open the file

& see what i placed in it i have done
a reboot thinking that once i am on the
desktop file would be gone but no go

but the odd thing is it will work when
i decrypt the file????

any help at all please

Thank you

---

### Post by robert_pectol on 2006-01-19
It seems your situation is unique.  Congratulations! :)  If you can still access the file after the operation completes, then wipe isn't doing it's job, for whatever reason.  I have never seen the problem you describe and therefore can't reproduce it for debugging.  What are the attributes of the file you are encrypting?  Are you the owner, etc?  Maybe wipe is having trouble wiping that file due to permissions, ownership, etc.  That's about all I can think of at the moment.  Oh, and the reason file deletion works on the encrypted file, when decrypting it, is that wipe is not used for deleting the encrypted file since it is already secure (it's encrypted).  It's merely deleted using conventional means.  Wipe is only used for securely deleting the original, un-encrypted file, after encryption.  But in your case, wipe doesn't seem to be working.  You could go to the command line and cd to your ~/Desktop and then try using wipe from the command line, to delete the file.  That way, you might get some feedback from wipe as it attempts to delete the file.  Hopefully it will give you some clues as to why, if it fails to delete it.  The command would be, "wipe ./name_of_file" once you are in your ~/Desktop dir.  Good luck.

---

