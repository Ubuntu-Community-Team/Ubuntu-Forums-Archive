---
title: "Setting directory permissions in XP"
date: 2007-12-09
forum: Windows
---

### Post by Erdaron on 2007-12-09
How can I set security permissions for a folder so that a limited account user still has full access to it?

The folder in question is c:\mystuff, something I made so that I had one place that's easily accessible from different accounts.

My exact problem is this. I use Thunderbird, and put its profile data in a subfolder of c:/mystuff, then used the profile manager to point it to that folder for both the admin and limited accounts. Under admin, this works fine. Under limited, Thunderbird brings up an error message saying that browser's security component could not be started, and it is probably due to read/write permission settings on the folder containing profile data. In this state, Thunderbird cannot read any messages - every mail folder looks empty.

(I know a workaround would be to put the profile data in the limited account's documents folder, but I'd like to figure out the folder security settings instead.)

My system is a Windows XP Pro SP2.

Thanks in advance!

---

### Post by afljafa on 2007-12-09
Tools > Folder options > View > Advanved settings - Turn off simple file sharing.

You will gain fine grained control on all files and folders.

---

### Post by Erdaron on 2007-12-09
Bingo! Thanks!

I had to set both sharing and security access to full control, and now it works. Victory!

---

