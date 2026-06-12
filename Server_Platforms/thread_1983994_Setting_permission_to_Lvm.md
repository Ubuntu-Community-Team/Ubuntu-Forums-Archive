---
title: "Setting permission to Lvm"
date: 2012-05-21
forum: Server Platforms
---

### Post by theluli on 2012-05-21
Hi

how can l give a full permission to a created lvm partition , which l have shared with samba ?

---

### Post by darkod on 2012-05-21
The LVM has a mount point, the same as with standard partition on a hdd.

You configure permissions, including samba permissions the same way as with hdd partitions. There is no difference.

Now, if the question is how to configure permissions in samba in general, that's different. Depends what exactly are you trying to achieve, you need to explain and someone with more experience can help you.

---

### Post by theluli on 2012-05-21
Hi 

Thanks for fast respond 

Ok l will try to give more details about my server and issue

l have ubuntu server 12.04 and l have setup 2 hdd's , on the first one l have personal data , l made mount , added to samba share with permission that need another system which is ( mint12 ) has full access , that is good ( required ) 
So than the second hdd , l have setup lvm , mount , fstab than mounted on mint12 , l can access hdd , l can create file , delete file , but when l try to transfer files from first hdd , is saying that l dont have permission ( when l create a folder , in the folder is showing a small locked ) that means that there is a problem with permission ?
And l checked both hdd's ( users ' rights' permission on samba ) they are the same 

l hope that you will understand , because my english is not so good

---

### Post by darkod on 2012-05-21
So, the mount point of the lvm is not included in any samba share?

You only have samba share for the first hdd.

---

### Post by theluli on 2012-05-21
everything is included , in samba share in fstab the same as the first hdd 
and also directory level are the same , with read and write ( guest, users,other ) are the same

---

### Post by darkod on 2012-05-21
Well, there must be some difference.

From the Mint12 machine, if you try to create a folder on the lvm samba share, does it have the lock symbol too or not? Just try to create a folder directly, not to copy something from the other share.

Also, it would be good if you post the /etc/samba/smb.conf of the server, and maybe the /etc/fstab from the Mint12 machine. Post them included on code tags (button # from the post toolbar).

---

### Post by theluli on 2012-05-21
Yes , when l create from the mint12 on lvm samba share l got the lock symbol

[Windows] - this is the first HDD

     Comment = Fajla te rendesishme
     path = /home/me /windows_share
     valid users = valid users = here is the user which l give permission
     writable = yes
     browseable = yes


[film] - this is second HDD - first partition

    Comment = filmat
    path = /home/me /film
    valid users = valid users
    writable = yes
    browseable = yes

[muzik] - second partition 

    comment = muzikat
    path = /home/me /muzik
    valid users = valid users
    writable = yes
    browseable = yes

[dokumenta] - third partition 

    comment = dokumentat
    path = /home/me /dokumenta
    valid users = valid users
    writable = yes
    browseable = yes

and this is on fstab on mint12

//ip-server/windows   /home/me /Windows  smbfs  credentials=/home/validusers/.creds  defaults 0       0
//ip-server/film      /home/me /Filma    smbfs  credentials=/home/validusers/.creds  defaults 0       0
//ip-server/muzik     /home/me /Muzik    smbfs  credentials=/home/validusers/.creds  defaults 0       0
//ip-server/dokumenta /home/me /Dokumenta smbfs credentials=/home/validusers/.creds  defaults 0       0

Here is setup

---

### Post by darkod on 2012-05-21
I am not an expert but I don't like it that your samba shares are actually within your /home/me folder.

Your Home is designed with your permissions in mind, and by default it blocks out other users. The samba shares do have option for other users but I think the permissions of the actual /home/me folder still apply. Samba can't overwrite them.

If this is only a server that needs to serve files to the network, it's much better all data to be in a neutral location, not in /home. For example, it can be in /data creating subfolders as you wish, like:
/data/documents
/data/music
/data/movies

The permissions on these folders need to be set depending how you want it. Accessible by all, or not.

Then the samba shares have this path, not /home/me...

Also with the fstab of Mint12 it seems you are trying to use the samba shares directly as Documents, Movies, etc in your Home folder. I'm not sure if it can work that way, looks like it could. But you can easily use another mount point outside /home/me, you will still have access to all data on the server. No need to insist on connecting it directly into Home.

If you want to do that I think you better do it with symlinks or similar.

---

### Post by theluli on 2012-05-21
Ok 

l will try to change , moving shares from my home 
But , maybe the problem is with mint12 , because l installed XP on virtual box , than l have mappet the share folder ( music and windows )  , than tried to copy and past , transfer files and in both it works

---

### Post by darkod on 2012-05-21
Could be. As I said, I don't like it that you are mounting the network shares inside your /home/me in Mint12 too.

I would use another mount point, not inside your home folder in Mint.

---

### Post by theluli on 2012-05-22
Hi

l made a setup in two linux machine one partition with /data/ and stile the same 
Let me ask you one question  , since l mounted /data/Windows on both system , how can redirect this to desktop mint12 , so l can go straight from desktop , because always l have to go /data/than Windows

---

### Post by darkod on 2012-05-22
I don't understand what you are trying to do/say.

What folder will open directly depends on how you define the samba share. If the share is path=/data then it will open the content of /data.

If you configure the share as /data/Windows it will open that directly.

This has something to do with security and permissions. I don't know how much security you want to implement, but have you tried with open permissions to all for a start?

On your data server it would be something like:

```
sudo chmod -R a+rw /data
```

That should change the permissions of /data to RW for all. I think the -R should change all subfolders too but I'm not sure.

Then all users should be able to read/write. You might also want to consider configuring the samba shares to accept all as guest, without the need to be authenticated user.

If that works, you can start closing down the access as you want.

---

### Post by theluli on 2012-05-24
hi

l tried everything but no success , maybe there is a problem with Lvm

---

