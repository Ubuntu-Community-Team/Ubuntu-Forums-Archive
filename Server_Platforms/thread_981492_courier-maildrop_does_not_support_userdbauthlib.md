---
title: "courier-maildrop does not support userdb/authlib"
date: 2008-11-13
forum: Server Platforms
---

### Post by degexte on 2008-11-13
Hi,

It seems that the intrepid ibex package of courier-maildrop no longer uses courier-authlib. I have checked and confirmed this with "ldd /usr/bin/maildrop.": it is not linked anymore to the relevant library.

You will notice this if you use a setup with virtual users, and configured courier's authentication mechanisms (like I did..). I used the userdb-variant, although I assume this affects other variants as well. 

The only way I got around this was to compile the courier-maildrop binary from the sources, with support for courier-authlib.

w/regards,

Gerrit

---

### Post by 3nt on 2008-12-13
Having just upgraded I was about to start tracking down why my imap server was no longer delivering mail. This shortcut that search. I am now going to have to download and compile the source. 
I can see no valid reason for removing the authlib from the comiled version. Its just tedious to have to manually install.

---

