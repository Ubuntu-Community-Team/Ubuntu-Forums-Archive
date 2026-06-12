---
title: "Assistance with samba share permission - won't change from 755"
date: 2016-05-28
forum: Security
---

### Post by adrian91 on 2016-05-28
Hello,

I recently setup a server running ubuntu 16.04.  I have a NAS running samba that my ubuntu server is connecting to.  I have added a user to the NAS that the ubuntu server connects to just fine, but it can only read and execute.  I have other computers that have full read, write, and execute abilities, so I don't think it is a permissions problem with the NAS.  When I try to chmod the directories after they are mounted nothing changes - the permission stay at 755.  Any suggestions would be much appreciated.  Thanks.

---

### Post by bashiergui on 2016-05-28
Make sure it's not set to be immutable ```
sudo chattr -i path/to/file
```

---

### Post by adrian91 on 2016-05-28
Won't let me run the chattr -i command.  Just tells me "Inappropriate ioctl for device while reading flags on path/to/file"

ls-l yields
drwxr-xr-x though.  I think if it was immutable it would be something like -----i-----.  Either way, if the chattr command can't even try to read the flags, I don't see how it could have set the directory as immutable........  

Am I missing something else?  Thanks.

---

### Post by adrian91 on 2016-05-29
So I did a little more testing this morning.  Using the console, I used sudo to create a new blank file called test on my share located in mnt/Documents.  It wrote the fine just fine using sudo.  Won't do it as my regular user.  This leads me to believe there is an issue with the way my ubuntu client permissions are set up since it wrote fine as root to the server using the credentials I gave it.   Whenever I try to chmod 775 or 777 it looks like it takes, but when I do a ls-l it still gives me the 755 result like I showed above.  I don't get it.........

Any suggestions?

---

### Post by bashiergui on 2016-05-30
> **adrian91 said:**
> I recently setup a server running ubuntu 16.04.  I have a NAS running samba that my ubuntu server is connecting to.  I have added a user to the NAS that the ubuntu server connects to just fine, but it can only read and execute.  I have **other computers** that have full read, write, and execute abilities, so I don't think it is a permissions problem with the NAS.  When I try to chmod the directories after they are mounted nothing changes - the permission stay at 755.Are the other computers Windows?
Is the NAS formatted ntfs? Linux can't modify permissions in an ntfs file system.

---

