---
title: "Cross-platform hidden files???"
date: 2010-10-24
forum: Security
---

### Post by snakeman21 on 2010-10-24
I'm sure most of you know that making a file or folder hidden is simple in the Linux world:  Add a period (.) before the name.  However, if you were to save such a file or directory to a flash drive, it would only be hidden on Linux systems.  If you plug the flash drive into a Windows machine, Windows will happily show the file.  Is there a way to make cross-platform hidden files?

---

### Post by WinstonChurchill on 2010-10-26
> **snakeman21 said:**
> I'm sure most of you know that making a file or folder hidden is simple in the Linux world:  Add a period (.) before the name.  However, if you were to save such a file or directory to a flash drive, it would only be hidden on Linux systems.  If you plug the flash drive into a Windows machine, Windows will happily show the file.  Is there a way to make cross-platform hidden files?Format the USB drive as FAT/NTFS. Then create the file/folder(s) you want named '.FileName' in Linux (Windows doesn't like naming files without any characters before the dot - probably left over from the good old 8.3 DOS days...). Then, in Windows, use the 'ATTRIB +SH [filename]' command - that will make it hidden unless the user has "Show protected operating system files" checked in Windows (Linux doesn't care about Windows file attributes, but will hide it by virtue of the dot-prefix).

**Edit: **Remember there is nothing secure about hidden files at all - the only reason to hide files is to keep things you don't usually care about from cluttering up your directory listings.

---

### Post by endotherm on 2010-10-26
> **snakeman21 said:**
> I'm sure most of you know that making a file or folder hidden is simple in the Linux world:  Add a period (.) before the name.  However, if you were to save such a file or directory to a flash drive, it would only be hidden on Linux systems.  If you plug the flash drive into a Windows machine, Windows will happily show the file.  Is there a way to make cross-platform hidden files?
short answer, no with a but, long answer yes with an if...
Winstons idea should work fine as long as windows and linux are all you use, and your linux distro honors the FAT/NTFS request that the file be hidden.

---

### Post by snakeman21 on 2010-10-26
Thanks guys.  And I wasn't asking for security purposes, I was simply curious as to if it could be done.  I was annoyed that if I plug any of my flash drives into a windows machine, the .trash folder always appears.  It's not really important enough to matter, though.

---

### Post by bodhi.zazen on 2010-10-26
> **snakeman21 said:**
> Thanks guys.  And I wasn't asking for security purposes, I was simply curious as to if it could be done.  I was annoyed that if I plug any of my flash drives into a windows machine, the .trash folder always appears.  It's not really important enough to matter, though.

As has been pointed out , there is no simple answer.

On the windows side, mark the .trash directory (folder) as hidden.

---

