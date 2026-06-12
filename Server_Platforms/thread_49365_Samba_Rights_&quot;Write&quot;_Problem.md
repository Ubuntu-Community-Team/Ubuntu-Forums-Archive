---
title: "Samba Rights &quot;Write&quot; Problem"
date: 2005-07-16
forum: Server Platforms
---

### Post by kapkorn on 2005-07-16
Okay I have a Samba server set up using Ubuntu and I thought all was okay, I have set up on it 3 network users (just my 3 diff windows machines so i dont have to enter a passowrd, that way it syncs)


Anyhow whenever I move over data from Computer A (windows) to the samba server it goes okay, however Computer B (windows) cant write to that folder it created because samba automaticall makes it read only for the owner Computer A.


Is there a way to make it to where the folders and data create from Computer A can be written to and changed by Computer B?


I have them all in the same group as of now.

---

### Post by RastaMahata on 2005-07-16
[QUOTE=kapkorn]Okay I have a Samba server set up using Ubuntu and I thought all was okay, I have set up on it 3 network users (just my 3 diff windows machines so i dont have to enter a passowrd, that way it syncs)


Anyhow whenever I move over data from Computer A (windows) to the samba server it goes okay, however Computer B (windows) cant write to that folder it created because samba automaticall makes it read only for the owner Computer A.


Is there a way to make it to where the folders and data create from Computer A can be written to and changed by Computer B?


I have them all in the same group as of now.[/QUOTE]
 have you set the **security** option to **share** in /etc/samba/smb.conf?

---

### Post by kapkorn on 2005-07-16
[QUOTE=RastaMahata]have you set the **security** option to **share** in /etc/samba/smb.conf?[/QUOTE]


Would that still make it to where a password is still needed to get to the server? If so then that sounds good. I will try it and see what happens.

---

### Post by kapkorn on 2005-07-16
I tried it and when I create a directory in my share folder from my windows box it still locks it as Administrator as the owner, which is what I am trying to get around.


I want to be able to do all of my file stuff from each computer.

---

### Post by kapkorn on 2005-07-16
Hmm I am starting to think that maybe it has to do with my fstab file, I am sorry for all of the questions but I am pretty stuck. 


here is my file

The last line with the /home/antecserver/data is my drive with all the shares and that is all it contains.

I just feel as if I have something wrong here.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb1	/home/antecserver/data	ext3	defaults

```

---

