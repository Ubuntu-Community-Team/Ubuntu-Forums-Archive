---
title: "Samba share not mounting via fstab"
date: 2007-04-03
forum: Server Platforms
---

### Post by tatster on 2007-04-03
Hi,

I have Edgy server, and an Edgy desktop.   Samba is running on the server and I am trying to mount this share at bootup on the desktop.

I can mount manually using:
```
sudo mount //192.168.0.253/media /media/media -t cifs -o username=anthony,password=blanked,dmask=777,fmask=777

```

But when I put the following in my /etc/fstab and reboot the mount doesn't seem to work.
```
//192.168.0.253/media    /media/media cifs  credentials=/root/.smbcredentials    0    0
```

/root/.smbcredentials
contains:
username=anthony
password=blanked

I have got these instructions from Ubuntuguide.org [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite")

Please can anyone help?

Tat.

---

### Post by erwall on 2007-04-03
I'm no wiz but try this:

aptitude install smbfs

and in your fstab:


//192.168.0.253/media     /media/media     smbfs      credentials=/root/.smbcredentials,dmask=777,fmask=777     0     0

test by doing

sudo umount -a
sudo mount -a

---

### Post by huygens on 2007-04-03
Tatster
you should try to mount manually the device and see for any error code, assuming you have your /etc/fstab with the options to mount your CIFS share:
```
sudo mount /media/media
```You should check the output of this command. If it is silent, it probably has worked, check by doing:
```
ls /media/media
```For your information, I just tried using CIFS and it worked. Here is my list of command:
```
sudo apt-get install smbfs
sudo mkdir /mnt/share
sudo mount -t cifs //host2/share /mnt/share -o user=huygens,domain=lan
ls /mnt/share
sudo umount /mnt/share
sudo vi /etc/host2-cred
```(for your info, when doing ls /mnt/share I saw the file in my shared directory on host2. in addition workgroup or domain are the same thing for my network)
In /etc/host2-cred I have written:
```
username=huygens
password=huygens
```Then I saved the file and did:
```
sudo chmod 0400 /etc/host2-cred
sudo vi /etc/fstab
```In fstab, I have written (added a new line at the end):
```
//host2/share /mnt/share cifs credentials=/etc/host2-cred,domain=lan 0 0
```I saved the file, and tested it:
```
sudo mount /mnt/share
ls /mnt/share
sudo umount /mnt/share
```I had the same result with the ls command as before.

Perhaps you are able to see what step I have done differently than you. But those above do work :-)

PS: if your shared folder has a space in its name, it is not a problem for Samba, but the syntax is a bit particular. I would advise that you read this post in this case: [http://ubuntuforums.org/showthread.php?p=1440697#post1440697](http://ubuntuforums.org/showthread.php?p=1440697#post1440697)

---

### Post by tatster on 2007-04-04
Huygens,

You're a star.

The only thing that I can see is that you had the credentials file in a different location.

I re-created the line that you had entered and now it works perfectly.

Thanks for your help.

Tat.

---

### Post by huygens on 2007-04-04
You are welcome :-) I'm happy it is solved.

What you could do is mark this thread as solved. On your first and initial post, there is an edit option. Select it and then you will see a button named "Go advanced" just above the edit button. Select "Go advanced". There you will see that you can check a box to tell that the thread is resolved.

---

### Post by meatballhat on 2007-05-08
/me showers praise on huygens, too :) 
yaaaaaay!

---

### Post by gonzalov on 2007-05-09
Hey! Thanks for this directions! I'd like to add a little...

After doing what's written here I was able to connect correctly, but was having trouble shutting down Ubuntu. Something about "CFS server did not respond to" some command (didn't write down the problem).

This seems to have been solved by using fs type "smbfs" instead of "cifs". When using cifs I had a "cifsoplockd" and a "cifsnotify" processes running, and when using smbfs I have other related processes. Don't know what's the difference, but I can shut down properly now.

Also you might like to look into the "uid" and "gid" options when mounting: it forces a specific user and group ownership for your connected drive. At least, I needed it, as server is Mandriva and client is Ubuntu: Mandriva places users starting at UID 500 and Ubuntu at UID=1000, so there was some strange permission problem.

Great help, as always, on this forums!

---

