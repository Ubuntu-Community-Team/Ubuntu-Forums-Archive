---
title: "setting up samba"
date: 2005-06-28
forum: Server Platforms
---

### Post by Rule on 2005-06-28
hey guys I have been following this guide 

[http://www.ubuntuforums.org/showthread.php?t=26438](http://www.ubuntuforums.org/showthread.php?t=26438)

but I keep getting an error saying (smbfs)

25332: Connection to smb_srv failed
SMB connection failed

im sure this is correct

```
sudo mount -t smbfs -o username=samba,password=<password>,uid='whoami',gid'whoami',fmask=000,dmask=000 //smb_srv/samba /home/samba/Network/
``` 


EDIT: after following the first part I tried what it said about how to access it it in windows and it doesn't work. (just thought I should add this in :D)

TIA
Rule  :smile:

---

### Post by LordHunter317 on 2005-06-28
Those should be backticks (`) for whoami instead of single quotes (').

---

### Post by Rule on 2005-06-28
ahh ok :D

well I changed them but I stille get the SMB Connecion failed :s

---

