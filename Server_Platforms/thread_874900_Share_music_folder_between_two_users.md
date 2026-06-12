---
title: "Share music folder between two users"
date: 2008-07-30
forum: Server Platforms
---

### Post by Yob on 2008-07-30
I've set up a ubuntu server running 8.04. 

It has a separate partition for all my data (pictures, music etc). I've mounted this partition in /mnt/store by adding it in my fstab and all is working well.

Now my brother wants access to this data so I've created an account for him on the system and he too can access it - however - he's on a windows system using winscp and he finds the whole thing a bit confusing. (He can't find the data since it's not in his home folder).

Can i make a folder in his home directory and have it display the contents of a folder on the mounted partition? Like a virtual directory of sorts...?

---

### Post by vanadium on 2008-07-30
If you move your brother also to linux, then he will be able to mount the remote directory wherever he wants in a variety of ways (sshfs, nfs,...). For access through a Windows system, I guess you are limited to sharing the folder on your server using samba.

---

### Post by Oldsoldier2003 on 2008-07-30
> **Yob said:**
> I've set up a ubuntu server running 8.04. 

It has a separate partition for all my data (pictures, music etc). I've mounted this partition in /mnt/store by adding it in my fstab and all is working well.

Now my brother wants access to this data so I've created an account for him on the system and he too can access it - however - he's on a windows system using winscp and he finds the whole thing a bit confusing. (He can't find the data since it's not in his home folder).

Can i make a folder in his home directory and have it display the contents of a folder on the mounted partition? Like a virtual directory of sorts...?

yes you can create a folder in his /home and link it. just make sure he has permissions in the target directory

---

### Post by ginjabunny on 2008-07-30
to access from windows you would have to install samba on your server and use it to share the folder aswell, then on windows you can create a shortcut to \\servername\sharename so when you click it you can see the contents.

that is putting it very simply

---

### Post by Yob on 2008-07-30
Thanks all.
Turned out I could simply do
```
sudo ln -s /mnt/store/Music
```
in my brothers home directory and all was as I wanted it.

---

