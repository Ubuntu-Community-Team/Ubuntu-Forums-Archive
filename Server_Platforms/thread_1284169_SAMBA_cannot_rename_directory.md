---
title: "SAMBA cannot rename directory"
date: 2009-10-06
forum: Server Platforms
---

### Post by EnderEd on 2009-10-06
My Ubuntu-Samba network share is acting oddly since upgrading to 9.04.

It seems my two XP boxes can do anything to files (add/delete/copy/move/rename,etc.), but can only add/delete directories. If I try to rename/move a directory, I get a Windows "Access is denied" error.

I literally copied the previous smb.conf to the new server install. Can someone help me troubleshoot?

Thanks,

--EdB

---

### Post by fjgaude on 2009-10-06
You have used this command:

```
sudo smbpasswd -a <id-name>
```

in Linux?

Also in Windows you have declared the vaious folders as 'share'?

---

### Post by trinikrono on 2009-10-06
What i found to do was just to add the line
readonly = no
to the share in the smb.conf then i could rename folders with no problems.

---

### Post by fjgaude on 2009-10-06
Wow, we learn something new everyday, eh?

---

