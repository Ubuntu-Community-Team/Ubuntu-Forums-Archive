---
title: "Executable .PNG files"
date: 2019-07-27
forum: Security
---

### Post by call-922 on 2019-07-27
All, I am relatively new to Ubuntu. I was poking around on my system with this command to find all executables:

sudo find / -printf "%M %p\n" | grep '\-..x..x..x' | grep -v /var/lib/docker/overlay2 | cut -c 12-

I noticed many .PNG files marked as executable. For example:

ls -l /var/lib/app-info/icons/ubuntu-bionic-updates-universe/64x64/

Is there a good reason why any .PNG should have a -rwxr-xr-x permission mask? I've read various articles about image files containing malicious payloads so this concerned me.

---

### Post by TheFu on 2019-07-28
If they truly are just image files, then it doesn't matter.  Use the 'file' command to see.  If they are scripts or compiled programs, then it could matter, if the file was invoked, somehow.

There is definitely a faster find command to locate files with execute permissions.  Getting a list of them all, then grep'n on the displayed permissions is terribly inefficient.
```
find . -type f -executable -print
```
or
```
find . -type f -perm +111 -print
```
No reason to look at directories and checking the permissions on files is very fast.  The -print will be the slowest part. Avoid using fancy formats in the printf ... printf is extremely slow - as all C programmers know why.
Those two find commands could return different solutions. There are subtle differences in the -perm vs -executable options.

> -rwxr-xr-x permission mask
That isn't a mask.  The mask for that would be 0022.  Unix systems actually use masks, so this is an important concept.

---

### Post by call-922 on 2019-07-28
Thank you for the clarifications. The larger context of the question was: why would a .PNG (or any non-executable) have the executable bit(s) set? I see the following distinct permissions for .PNG files on my system (Ubuntu 18.04.2 LTS):

-r--------
-r--r--r--
-rw-------
-rw-r--r--
-rw-rw-r--
-rwxrwxr-x
-rwxr-xr-x

Probably this falls into the category of: "it is what it is"

---

### Post by SeijiSensei on 2019-07-28
A lot of PNG files apparently ship with the execute bit turned on. For instance, all the files in /var/lib/app-info/icons/ubuntu-disco-universe/64x64/ on my machine have execute permissions. I don't see any good reason for this either, but I wouldn't worry about it. I'd be more concerned about files that arrive via email or perhaps over the web. I found this example of malware being hidden in PNGs, but the corrupted images alone could not install their payloads. Another program, delivered by email, was needed to launch the malware.

[https://securelist.com/png-embedded-malicious-payload-hidden-in-a-png-file/74297/](https://securelist.com/png-embedded-malicious-payload-hidden-in-a-png-file/74297/)

Also very few people write malware to attack Linux.

---

### Post by TheFu on 2019-07-28
I don't have that directory, so don't have that issue.
Whenever I see package-installed files with funky permissions, I figure it was caused by a lazy packaging team.  I usually see that with php webapps, not icons.  "How" it can happen, is left to your imagination, but I can think of at least 10 ways, most are not flattering towards the packaging team. Suppose the icons were created by someone using a non-Unix computer and copied into the packaging area by them using Samba.  Samba setups often will make any file executable because it is easier.  Or the file might have been copied off flash storage or NTFS, which might be mounted with execute permissions for all files, because it is easier. I used to package cross-platform commercial software in the 1990s and know that I took specific steps to ensure all file metadata and permissions were correct. 

An aside: Linux doesn't actually care about file extensions.  A few GUI programs might care and they are helpful for humans, but I don't trust extensions.  I trust what the '**file**' command says after it looks at the "magic header" for the file.

---

### Post by SeijiSensei on 2019-07-28
The file utility might have been deceived by the malware described in that article. Basically it was a legitimate PNG file that had the payload appended.  I believe it had the correct header.  As I said, it required another program to launch the malware; just viewing the file wouldn't have done it.

Icons in /usr/share/icons/hicolor have the correct 644 permissions.

---

### Post by call-922 on 2019-07-28
Thanks, all.

---

