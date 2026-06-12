---
title: "new guy - advice please!   (permissions)"
date: 2008-06-23
forum: Security
---

### Post by eotakos on 2008-06-23
Hello,

i've been playing around with ubuntu for quite a while but it's been about a month since i've damped windows and i'm pretty excited about it.

Until today i was confident that the permission stuff would be pretty much configured by default but to my surprise i realized that my home folder was available for everyone to read. then i changed the permissions to none for group and others and i sudenly couldn't login the gnome. i fixed that by restoring the group permissions... so what is the logic of this thing anyway...?

another issue i have is with my ntfs partitions which are not mounted until i open them from the places menu for the first time in a session. I don't have any problem with that - i actualy like it but i can't find how to control who's reading the partitions after they are mounted. To the point when a partition is still not mounted during a session, the target directory in /media doesn't exist. It is created along with the mount process; so, i tried to create another directory(the same name) - prior to mount - and give it the permissions i want, but again it will create it's own directory like i did nothing...

thaks for your time in advance

---

### Post by syncrondi on 2008-06-23
> **eotakos said:**
> 
i've been playing around with ubuntu for quite a while but it's been about a month since i've damped windows and i'm pretty excited about it.

Nice. :)

> **eotakos said:**
> 
Until today i was confident that the permission stuff would be pretty much configured by default but to my surprise i realized that my home folder was available for everyone to read. then i changed the permissions to none for group and others and i sudenly couldn't login the gnome. i fixed that by restoring the group permissions... so what is the logic of this thing anyway...?

If you're a member of the group listed, then you won't have permissions on the directory if you remove them for the group as far as I understand.

---

### Post by ad_267 on 2008-06-23
By default other users have read access to other home directories but not write access. You can just remove the read access from other users.

---

### Post by eotakos on 2008-06-23
Thanks!

...what about the other thing - do you know which file controls the easy-mount buttons on the "place" menu? maybe from there i could set the mount permissions...

---

### Post by ad_267 on 2008-06-23
The file that controls the mounting of drives automatically is /etc/fstab. If you do a search for that you should find some good explanations of how to edit it. I'm not sure if there's a way to edit how a drive is mounted when you click on it in the places menu.

---

### Post by eotakos on 2008-06-24
actually the fstab file doesn't say anything about the ntfs's. It includes info for the ext3, the swap, cds and floppy. The mtab file includes stuff for the ntfs's only after they're mounted.

Anyway after i finish my exams i'll transfer everything important in the ext3 partition - this is only temporary.

thank you all for the responces

---

### Post by ad_267 on 2008-06-24
> **eotakos said:**
> actually the fstab file doesn't say anything about the ntfs's. It includes info for the ext3, the swap, cds and floppy. The mtab file includes stuff for the ntfs's only after they're mounted.

Anyway after i finish my exams i'll transfer everything important in the ext3 partition - this is only temporary.

thank you all for the responces

Yeah that's the reason you have to click on them to mount them, because they're not in /etc/fstab. If you set them up in there then you won't have to do that and you can set the file permissions. Sorry if I didn't make that clear.

---

### Post by eotakos on 2008-06-24
there is nothing to be sorry about - you just got me to realize that i prefer setting my own permissions to manual mount. That sure sounds more secure...

here you go - another "thanks" to your pile

---

### Post by ad_267 on 2008-06-24
Haha cheers. These should explain how to mount those partitions with the permissions you want: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131), [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by cdenley on 2008-06-24
If you want to change the mount options used when a filesystem is mounted from the "places" menu...
```

gconf-editor /system/storage/default_options

```

If you want to change the default permissions for new files, you want to change the umask. I think the correct way is to edit the last line of /etc/profile. If you want files to be read by only the user who creates them, use this line
```

umask 077

```

---

### Post by eotakos on 2008-06-24
thanks for the tip

---

