---
title: "Delete files with | in filename (using Win10 bash)"
date: 2016-12-12
forum: Windows
---

### Post by cookie365 on 2016-12-12
Hello, although I'm using Ubuntu bash on Windows 10 I think this a general Ubuntu question.

A friend has a Windows 10 PC with a hard drive that has some files that he can't delete. He reckons at some time in the past the drive was in a Ubuntu PC and he thinks he saved some Firefox bookmarks to it as files.

The files all appear to have a vertical line | in the filenames. Four have colons, one doesn't. All have spaces.

UK keyboard.
When I'm in bash I get what appears to be an identical | by pressing Shift-\ near the bottom left, even though the key has ¦ printed on it.
Altgr-` at the top left gives ¦ even though the key has | printed on it.

I've installed bash on the computer and tried to delete the files from there, but with no luck.

I'm beginning to think it would be quicker to copy the terabyte or so of data he needs off the drive, format it, and copy it all back :(

Below is what I've tried.

They are in a folder called 1 within a folder called DeleteMe. There's another folder called 2 with identical files.

Can anyone help? Thanks :)

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ ls
ls: cannot access Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop: No such file or directory
ls: cannot access How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop: No such file or directory
Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop
Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop
Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop
Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop
How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ ls -b
ls: cannot access Acronis Disk Director 11 Home\: Changing from Demo to Full Version | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home\: Creating Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home\: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home\: Installation of a Demo Version | Knowledge Base.desktop: No such file or directory
ls: cannot access How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop: No such file or directory
Acronis\ Disk\ Director\ 11\ Home:\ Changing\ from\ Demo\ to\ Full\ Version\ |\ Knowledge\ Base.desktop
Acronis\ Disk\ Director\ 11\ Home:\ Creating\ Acronis\ Bootable\ Media\ |\ Knowledge\ Base.desktop
Acronis\ Disk\ Director\ 11\ Home:\ Creating\ WinPE-Based\ Acronis\ Bootable\ Media\ |\ Knowledge\ Base.desktop
Acronis\ Disk\ Director\ 11\ Home:\ Installation\ of\ a\ Demo\ Version\ |\ Knowledge\ Base.desktop
How\ to\ Delete\ an\ MBR\ Partition\ From\ a\ Hard\ Drive\ |\ eHow.com.desktop
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ rm Acronis\ Disk\ Director\ 11\ Home:\ Changing\ from\ Demo\ to\ Full\ Version\ |\ Knowledge\ Base.desktop
rm: cannot remove ‘Acronis Disk Director 11 Home: Changing from Demo to Full Version ’: No such file or directory
 Knowledge Base.desktop: command not found
```This was a direct copy and paste from the ls -b output.

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ ls -l
ls: cannot access Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop: No such file or directory
ls: cannot access How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop: No such file or directory
total 0
-????????? ? ? ? ?            ? Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop
-????????? ? ? ? ?            ? Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop
-????????? ? ? ? ?            ? Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop
-????????? ? ? ? ?            ? Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop
-????????? ? ? ? ?            ? How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ rm -v *
rm: cannot remove ‘Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop’: No such file or directory
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ cat -v
```(Cursor just blinked away for ages until I shut bash down and restarted)

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ sudo rm "Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop"
[sudo] password for dazzi:
rm: cannot remove ‘Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop’: No such file or directory
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ rm -rfv -- *
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ ls
ls: cannot access Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop: No such file or directory
ls: cannot access Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop: No such file or directory
ls: cannot access How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop: No such file or directory
Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop
Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop
Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop
Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop
How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop
```(I got no error from the rm command so hoped it had done the job. The ls proved it hadn't.

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ rm -i -- *
rm: cannot remove ‘Acronis Disk Director 11 Home: Changing from Demo to Full Version | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Creating Acronis Bootable Media | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Creating WinPE-Based Acronis Bootable Media | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘Acronis Disk Director 11 Home: Installation of a Demo Version | Knowledge Base.desktop’: No such file or directory
rm: cannot remove ‘How to Delete an MBR Partition From a Hard Drive | eHow.com.desktop’: No such file or directory
```

```
dazzi@DAZZIBOX:/mnt/e/DeleteMe/1$ rm "Acronis Disk Director 11 Home: Changing from Demo to Full Version \| Knowledge Base.desktop"
rm: cannot remove ‘Acronis Disk Director 11 Home: Changing from Demo to Full Version \\| Knowledge Base.desktop’: No such file or directory
```

---

### Post by QIII on 2016-12-12
Moved to Windows.

The support areas of the forum are for request for support for the official flavors of Ubuntu.

Cheers!

---

### Post by CharlesA on 2016-12-12
tab completion is probably going to be your friend.

```
rm -i A <TAB>
```

---

### Post by The Cog on 2016-12-12
I suspect that windows is the problem in that both '|' and ':' are illegal, so the file can't possibly exist. 
You might be able to boot a live Linux CD and use the file manager there to delete the files.

---

### Post by kpatz on 2016-12-12
Can you delete them from Windows Explorer or the Windows command prompt?

---

### Post by CharlesA on 2016-12-12
> **The Cog said:**
> I suspect that windows is the problem in that both '|' and ':' are illegal, so the file can't possibly exist. 
You might be able to boot a live Linux CD and use the file manager there to delete the files.

Probably right about that.

---

### Post by kpatz on 2016-12-12
Another thing to try is renaming the files in Windows Explorer to valid names and then try deleting them.

If that doesn't work, boot a Linux live CD, mount the disk and try deleting them from there.

---

### Post by cookie365 on 2016-12-13
Thank you everyone, renaming/deleting in Windows explorer didn't work, that was why I was trying bash  :)

Tab completion failed at the | - though not at the : which might be good news.

I'll try a live CD and report back.

---

### Post by vasa1 on 2016-12-13
Would enclosing these filenames in single quotes help?

---

### Post by cookie365 on 2016-12-13
> **The Cog said:**
> I suspect that windows is the problem in that both '|' and ':' are illegal, so the file can't possibly exist. 
You might be able to boot a live Linux CD and use the file manager there to delete the files.The live cD did the job. Deleted the folders and emptied trash using the Ubuntu gui with no fuss at all.

thank you for everyone's advice :)

---

