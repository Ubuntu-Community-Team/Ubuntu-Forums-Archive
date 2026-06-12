---
title: "Adding a NTFS / FAT disk to share"
date: 2009-12-21
forum: Server Platforms
---

### Post by Karl Norway on 2009-12-21
Hi 

Is it possible to hang a USB disk (already congaing files and formatted as fat32) and mount it and share it?

---

### Post by HighCommander540 on 2009-12-21
> **Karl Norway said:**
> Hi 

Is it possible to hang a USB disk (already congaing files and formatted as fat32) and mount it and share it?

Yes, but it would be slower than hell. Just take the data off of it reformat and then add the files again.

---

### Post by Karl Norway on 2009-12-21
Ok but im using windows on two client stations. I have one ubuntu client box used as media PC

---

### Post by HighCommander540 on 2009-12-21
> **Karl Norway said:**
> Ok but im using windows on two client stations. I have one ubuntu client box used as media PC

Actually I apologize. I only read your title really without reading the rest of the post. FAT32 shouldn't be that big of a problem. Its readable, by most operating systems. You are just going to need to mount it and then use SAMBA to share it.

There are many tutorials on how to do both, all over.

Here if for the Samba part:
[http://tinyurl.com/y8opzfn]("http://tinyurl.com/y8opzfn")

Here is for mounting a drive:
[http://tinyurl.com/ybg6xuz]("http://tinyurl.com/ybg6xuz")

---

