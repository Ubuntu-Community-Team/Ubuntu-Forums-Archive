---
title: "Howto: Access Linux partition from another Linux machine?"
date: 2010-01-18
forum: Security
---

### Post by Martin Lam on 2010-01-18
Hi,

I have installed an Ubuntu server and it running OK.  Before making it a production server, I want to make sure one day if the OS corrupts accidentally, I can still access the users' files on the hard disk.  

I burned a Ubuntu desktop live CD, and booted it with this machine.  There are 2 hard disks on the server, both could be mounted automatically.  However, I can only access some folders like lost+found.  

The questions are: 

1. how can I access the other folders, given I have the root password of the server.  

2. is there a way to access all folders without knowing the users + passwords?  

Thanks! 

Martin

---

### Post by Cheesemill on 2010-01-18
Just hit ALT+F2 from the Live CD and enter:
```
gksudo nautilus
```
This will give you full access to all of the files.

You don't need any of the passwords for the server, you can access the files without them.

---

### Post by Martin Lam on 2010-01-20
> **Cheesemill said:**
> Just hit ALT+F2 from the Live CD and enter:
```
gksudo nautilus
```
This will give you full access to all of the files.

You don't need any of the passwords for the server, you can access the files without them.

Hi Cheesemill,

Thanks.

I tried this.  But there was no difference - it could only see and access the public folders / files.  

Regards,
Martin

---

### Post by _H3MLOCK on 2010-01-21
How are you connected to the server? ssh? ftp? telnet?

---

### Post by Martin Lam on 2010-01-21
> **_H3MLOCK said:**
> How are you connected to the server? ssh? ftp? telnet?

Hi _H3MLOCK,

Thanks.

I was physically accessible to the server.  I booted it with a Ubuntu Desktop Live CD.   

The server itself is working fine if I boot it normally from the hard drive.  

I am practicing that, in the case the server's OS has crashed one day in the future by accident, how can I access and rescue my data on the server?

Regards,
Martin

---

### Post by _H3MLOCK on 2010-01-21
I see what you mean now. If, for whatever reason, the server crashes. You insert the LiveCD, boot into live mode and then open the terminal and run 

 sudo mount /dev/sda<whatever number the partition is> /mnt1

that will mount the filesystem on that sda into the /mnt1 folder... (using sudo ensures root access). You won't need any server passwords to do this, and this is scary for corporate/enterprise servers who want data super-secure. In that case I would recommend a crypto_luks filesystem using LVM partitioning. 

Alternatively you should be able to mount it under 'Places' and access all the files

---

### Post by mrhellboy86 on 2010-01-21
In windows if you install your windows on an NTFS partition 
you can not access the Documents folder of other users 
I personally don't install Windows on NTFS
does anybody know if ubuntu can come into that folders?
it is actually a problem if you loss your windows
and you have not access to User's folders

---

### Post by Martin Lam on 2010-01-21
Hi Cheesemaill and _H3MLOCK,

I know the cause of the problem now.  The Live Linux CD I used - Ubuntu Desktop 9, does not recognize my logical volumes on /dev/mapper/, while it is OK for a normal ext3 /dev.

I used another Live CD, SystemRescueCD, it worked perfectly.

Thank you guys!

Martin :)

---

### Post by cariboo on 2010-01-21
> **mrhellboy86 said:**
> In windows if you install your windows on an NTFS partition 
you can not access the Documents folder of other users 
I personally don't install Windows on NTFS
does anybody know if ubuntu can come into that folders?
it is actually a problem if you loss your windows
and you have not access to User's folders

You have to specifically set whether a users directories cannot be accessed by other users. You can find the setting in the user control panel.

If you don't use NTFS when installing Windows, are you still using vfat? In my opinion, that isn't a very good idea, as you are limited to files < 4Gb, and vfat is much more susceptible to file corruption.

---

### Post by mrhellboy86 on 2010-01-22
> **cariboo907 said:**
> You have to specifically set whether a users directories cannot be accessed by other users. You can find the setting in the user control panel.

If you don't use NTFS when installing Windows, are you still using vfat? In my opinion, that isn't a very good idea, as you are limited to files < 4Gb, and vfat is much more susceptible to file corruption.
do you know what exactly I shall do?
I went to control panel > User accounts on windows xp sp2 but there is not such an option about it

---

### Post by cariboo on 2010-01-22
I guess I was wrong about where I saw the setting, I have a couple of customers with Dell systems, and the setting was right in the user control panel.

On my OEM XP Pro install there isn't such a setting, But if you click on a folder , and select sharing, there is a setting in that window to set a directory as private. See the screenshot.

---

