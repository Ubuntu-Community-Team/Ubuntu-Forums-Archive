---
title: "Boot-Repair after wonderful windows 10 update"
date: 2015-08-01
forum: Ubuntu/Debian BASED
---

### Post by maciej19 on 2015-08-01
Hello,
I have 2 OS on my PC. Debian and windows.
After update my windows from 8.1 to 10, grub isnt working anymore. 
All i see is: 
"error: unknown filesystem
grub rescue> "
Command " ls " will give me partitions, but when i try to use "ls" on any of partitions i'm getting "error: unknown filesystem".

I can access only to windows using F12 key, and choosing Windows bootmenu.

So I tried to use "Boot-Repair". Ofcourse it didnt work...
paste.ubuntu.com/11981857

"[COLOR=#000000]The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode."

[/COLOR]And it is NOT in Legacy mode. Have checked by "msinfo32" in windows. It is UEFI.

Can anyone help me repair this bootmenu, please?
I need this debian to work :/

---

