---
title: "how auto mounting gpt 6TB HDD at boot?"
date: 2018-09-03
forum: Server Platforms
---

### Post by subzeroevil on 2018-09-03
Having Issue doing its my first HDD that is more then 2TB and having a little issue trying to mount it. Used parted and formatted and  put ext4  sdd1. All other HDD i put it in fstab ( since it was 2TB) does not seem to work. 

So far i have in fstab.

UUID=a18cd4dc-02ea-4d73-9b82-9039185eb263 /media/Media5 ext4 defaults,uid=113,gid=119,windows_names,locale=en_US.utf8  0 0

when booting  saying

[ATTACH=CONFIG]280956[/ATTACH]

see 'systemctl status media-Media5.mount' for details.

so i check it out  and it has.

[ATTACH=CONFIG]280957[/ATTACH]


 if anyone can help  thanks.

---

### Post by darkod on 2018-09-03
Did you notice where it says "Unrecognized uid=113 value or missing"?

Does that user ID exist?

---

### Post by subzeroevil on 2018-09-03
yes it [COLOR=#000000]exist.  its on my other mounts. removed some stuff ended up with this.

 [/COLOR][COLOR=#000000]UUID=a18cd4dc-02ea-4d73-9b82-9039185eb263 /media/Media5 ext4 defaults 00 [/COLOR]

[COLOR=#000000]worked!!!!! had to do set uid and group. and other settings but good.  here me looking for a bigger issue  then i had (tunnel vision).[/COLOR]
[COLOR=#000000]gpt must have different options in fstab.

Thanks   Darko[/COLOR]

---

### Post by oldfred on 2018-09-03
It looks like you were using parameters for NTFS mount.
And maybe mixed up uid & fmask & dmask settings?

I still use this example as templates for HDD mounts, but somewhat different for SSD mounts.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

