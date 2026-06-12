---
title: "samba permission: 700 -&gt; other users can delete my files!"
date: 2009-01-16
forum: Server Platforms
---

### Post by effepi on 2009-01-16
hi everyone,
i want to set up a samba share in which I have 2 users called "gianni" and "utente1"
I want that every user can create files but not delete other people's files.

here is my conf:

[gianni-pub]
        comment = bla bla
        path = /home/gianni/Scrivania/share-gianni
        browseable = yes
        writeable = yes
        user = gianni, utente1
        create mask = 0700
        directory mask = 0700

so, if gianni creates a file, I get:
root@me:/home/gianni/Scrivania/share-gianni# ls -al
...
-rwx------ 1 gianni gianni   22 2009-01-16 20:53 file.txt

so, ONLY gianni has permission to delete that file, right?
but if "utente1" logs in using samba, he can't read the file but he can delete it!
what's wrong?

regards,
fabio

---

### Post by lykwydchykyn on 2009-01-16
utente1 has write permissions on the folder, so that user can delete files from the folder.  Think of it like this:  a file's presence in the folder is an attribute of the folder.  If you have write permissions to the folder, you can remove its contents.

On the other hand, if you take away utente1's write permissions to the folder, utente1 cannot create files in the folder.  

The solution is to use a little known permission setting called the "sticky bit".  From the man page of chmod: 
> 
When the sticky bit is set on a directory, files in that directory may be unlinked or renamed only by root or their owner. Without the sticky bit, anyone able to write to the directory can delete or rename files. The sticky bit is commonly found on directories, such as /tmp, that are world-writable. 


To set the sticky bit on the directory, the command is:
```

chmod +t /home/gianni/Scrivania/share-gianni

```

---

### Post by effepi on 2009-01-16
yessssssssssss it works!
you are great,man!
thanks a lot!!!!!!!!
:guitar:

---

