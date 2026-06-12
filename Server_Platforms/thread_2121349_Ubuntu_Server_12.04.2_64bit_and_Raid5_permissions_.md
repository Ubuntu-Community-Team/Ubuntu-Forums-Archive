---
title: "Ubuntu Server 12.04.2 64bit and Raid5 permissions on samba share gone wrong"
date: 2013-03-01
forum: Server Platforms
---

### Post by omgubunt1 on 2013-03-01
Hello,
This is my first post on these forums and thanks for any help given.
I set up my server for my home needs with 4x2tb raid5 ext4.
All well and happy.
I format my raid5 ext4 and mounted it in my /home/name/Shares.
I edited fstab with uuid because it change name from /dev/md0 to /dev/md127 and i even tried to fix it by stop and re-assemble on next reboot my /dev/md0 likes to be called /dev/md127, weird? a bug? who knows :)
Anyway using uuid in fstab makes that problem go away so we come close to my real problem and the reason am here asking for help.
i must say i also have chmod -R myname:myname /home/name/Shares that fixed nothing.
Mounting the share on another pc i cannot use it.
Its read only. i cant create dir.
I have config samba to the most open up config ever, allowing rw to guest all users everything.
I just don't know what i am doing wrong.

I am putting here my fstab manual config i did:
UUID=74bf9e87-d0d2-4fc8-9201-af9bbf114657    /home/name/Shares    ext4    user,dev,noatime,users,suid,exec,nodiratime    0    2
Also my samba.conf
[http://paste.ubuntu.com/5577263/](http://paste.ubuntu.com/5577263/)

---

### Post by darkod on 2013-03-02
Why do you have all those options in fstab? I think some of them are limiting the access, like 'user', 'users', etc. Even if you want the share to be available only for your user, start with an open share first and then close it down so other people can't acces it.

Also, I don't think it's a good idea to put shares in your /home folder. Set it up on a neutral location, like /data or any other folder you create. The users home folders are strict with permissions. Even if you use the same username on the other pc it might not allow you to "peek" inside a users home folder.

If you want open access (permanently or for a start), in the smb.conf authentication section set security = share.

---

### Post by omgubunt1 on 2013-03-02
Thanks for your reply.
I follow your suggestion and moved mounted location and samba to /media/Shares but behavior is the same unfortunately.
Any other suggestions?

---

### Post by darkod on 2013-03-02
Did you try to set read/write permissions to all?
sudo chmod a+rw -R /media/Shares

The linux filesystem permissions are separate from the samba permissions. Also, try removing the 755 permissions in your share definition in smb.conf and restart samba after that. I think the 755 is read-only. For read/write it would be 777.

Are you accessing with the exact same username and password that exists on the server?

---

### Post by omgubunt1 on 2013-03-02
Thanks for your reply.
All i had to do is to change fstab with user,rw 0 2 nothing else and it seems to work.
Do you think i do what you suggested also? Is it still needed?
sudo chmod a+rw -R /media/Shares and change 755 permissions to 777 in samba.conf.
Thanks

---

### Post by darkod on 2013-03-02
If it works as it is for your user, leave it. The 755 will open it RW for you but RO for others. Don't bother with the chmod either, since it works for you. You might need to use it if you want other users to access the share(s).

---

### Post by omgubunt1 on 2013-03-03
I will begin loosing my mind :)
I restarted the server and problem is back.
I will try your solution eventually ;)

---

### Post by omgubunt1 on 2013-03-03
i did try your solution and here is the outcome.
Transmission writes to /media/Shares/complete and my adventure of weirdness and fighting with ubuntu permissions continues alas :(
When it writes a binary on root of /media/Shares/complete all ok when it writes to /complete/binary/binary.bin i cannot move/deleted etc i checked and all files belong to the same user me!
user: omgubunt1 group: omgubunt1
When i create a new folder on share :
User: nobody group: nogroup
Please someone help be with permissions on Ubuntu because am loosing my mind here.

---

### Post by darkod on 2013-03-03
Are you talking about permissions of ubuntu in general or the permissions of the files downloaded by transmission? The files downloaded by transmission will be owned by the transmission-daemon I think. I had the same problem when setting it up.

You have to set the umask in the /etc/transmission-daemon/settings.json file so that the downloaded files are not limited only to the transmission-daemon user. Make sure the settings.json file has a line saying:
"umask": 0,

If it doesn't and you need to edit it, stop the daemon first because if it's not stopped the change will be deleted. Stop the daemon, edit the settings.json, save and close it, start the daemon again.

---

### Post by omgubunt1 on 2013-03-03
My problem was with  the transmission permissions. Previously i had unmask from 18 ->2.After your recommendation i edit it to 0.
Thank you for your precious help Mr darkod. I will report back my progress.
Regards

---

