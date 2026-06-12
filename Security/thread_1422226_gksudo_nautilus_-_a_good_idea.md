---
title: "gksudo nautilus - a good idea ?"
date: 2010-03-05
forum: Security
---

### Post by Kevbert on 2010-03-05
If I want to copy files (graphically) to a directory other than /home such as /lib/firmware I can use
```
gksudo nautilus
```
but is this a good idea ? The reason I ask is that I get a large number of messages displayed in terminal with browsing a number of directories:
```
$ gksudo nautilus

** (nautilus:6653): WARNING **: Unable to add monitor: Operation not supported
e' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(807): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind

Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName
Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName
Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName
Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName
Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName
Error: Could not parse ligature component "Iecyrillic" of "Iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "Iicyrillic" of "Iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "iecyrillic" of "iecyrillic_grave" in parseCharName
Error: Could not parse ligature component "iicyrillic" of "iicyrillic_grave" in parseCharName
Error: Could not parse ligature component "armenian" of "m_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_e_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_i_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "v_n_armenian" in parseCharName
Error: Could not parse ligature component "armenian" of "m_x_armenian" in parseCharName

--- Hash table keys for warning below:
--> file:///lib
--> file:///home/kevin
--> file:///lib/firmware
--> file:///
--> file:///home
--> file:///etc
--> file:///root

(nautilus:6653): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 7 elements at quit time (keys above)

(nautilus:6653): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 7 elements at quit time

```
Or is it that some of these messages are actually due to bugs ?
I can always use 
```
sudo cp -r * /lib/firmware 
``` instead. Please comment.

---

### Post by Pjotr123 on 2010-03-05
You can safely ignore those error codes; they are probably related to special fonts you are using. Anyhow, they won't interfere with Nautilus's root operations. :)

---

