---
title: "Samba Shadow Copy"
date: 2009-06-28
forum: Server Platforms
---

### Post by chrisdeeley on 2009-06-28
I have shadow copy setup on Samba which works fine, except for the backups are not shown in date order in the windows shadow copy client.

[data]
path = /.server/data
guest ok = yes
browseable = yes
writeable = yes
vfs object = shadow_copy
shadow_copy:sort = desc
^ This line has no effect!

Has anyone else had this problem?

---

### Post by Vegan on 2009-06-28
I do not recommend using that shadow option. Its not useful for Windows clients and while harmless, you better of not using it if you want to be safe.

Windows backup uses a shadow copy of a NTFS disk. Its not intended for Linux ext3 et al based file systems.

So remove that line and leave well enough alone.

---

### Post by JonRohan on 2009-06-28
Perhaps something like rsnapshot would be better suited? What do you think Vegan?

---

