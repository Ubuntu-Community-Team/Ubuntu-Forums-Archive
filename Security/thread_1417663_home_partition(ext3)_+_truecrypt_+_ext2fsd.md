---
title: "/home partition(ext3) + truecrypt + ext2fsd"
date: 2010-02-27
forum: Security
---

### Post by mysticav on 2010-02-27
What I want to acomplish is this on a DUAL OS machine:


[LIST]
[*]Encrypt my /home partition. So, every time a log in to ubuntu, I must decrypt the /home partition before mount it.
[*]Access the /home partition from Windows using ext2fsd. Usually this is not a problem, but how ext2fsd will handle the encrypted partition ?
[/LIST]

The purpose of all this is to have a shared an encrypted partition between Windows & Ubuntu. So whether you login to ubuntu, or Windows, you could access same data. 


Any idea is most welcome.

---

### Post by NiGhtMarEs0nWax on 2010-02-27
Hey, I'm looking for something similar too. I know that Ubuntu _can_ use it's own form of encryption on your home directory and store it on a separate partition.

the only thing I was worried about with dual booting and full drive encryption is grub. does TrueCrypt just encrypt the partition? will grub still point to the 'boot sector' of that partition if its encrypted?

I'll be watching this thread with interest.

Thanks. :)


EDIT: oh and could you not just create an NTFS partition and set your home directory to that? that way you can still mount it with TrueCrypt no problem in Windows.

---

### Post by mysticav on 2010-02-28
What I have done so far is to encrypt an NTFS partition in Windows 7, then mount that partition in Ubuntu with no problem atl all. ( I can read + write). I haven't install any partitcular library in ubuntu for total access to NTFS. Seems that Ubuntu 9.10 Comes with full NTFS support out of the box.

I gave up with Ext3 on Windows 7 64 bit. I'll wait 'til they support the newest versions of Windows. 

I have tried all different libraries, including ext2fsd, ext2IFS and other less popular.

With ext2fsd I'm getting the "BAD_POOL_HEADER" BSOD (Blue Screen Of Death). This is a terrible bug. I have tried a patch they claim to fix this bug, but that patch uses an unsigned driver, and Windows 7 does not allow that. You need then, other hacks and everything becomes a mess.
 
With ext2IFS, you can't access because only supports inode 128 partitions.


Currently, I would like to know what could happen using a NTFS partition for /home
Can you still manage ACL permissions on that partition ?
IF different users have account on that /home directory, how can you restrict access one from each other?
Of course, they will share the say truecrypt password for mounting the partition, but they should  have access only to their directory. Ubuntu locks the users to their directory : /home/user/
I wonder how ubuntu handles it with truecrypt, because the decrypt process must happens before the OS attempts to asign the home directory for the user. 

Please any advice is most welcome, I'm relatively new to Linux/Ubuntu. Fortunately Ubuntu Users are one of the most friendly you can find..

---

### Post by sgosnell on 2010-02-28
The data partition/directory doesn't have to be mounted as /home to use it, it just has to be mounted.  You can set the permissions however you want.  In Windows, by default everyone can read and write to anywhere, so there isn't much protection, but you can limit it in Ubuntu.  In Ubuntu, one user can't write to another user's directories, and in fact you can prevent them from being read if you want.  

I would suggest trying mounting the Truecrypt volume as just another drive, not /home, and setting the proper permissions on each user's directories.  That should work in Ubuntu, but I'm not sure about Windows.  I think everyone can read and write everywhere, and I'm not sure you can prevent it.  I haven't dealt with Win7 or even Vista enough to know for sure, though.

---

### Post by NiGhtMarEs0nWax on 2010-03-03
> **mysticav said:**
> 
Currently, I would like to know what could happen using a NTFS partition for /home


i doubt there would be any problem, but encrypting the whole home directory is a different story.

> **mysticav said:**
> 
Can you still manage ACL permissions on that partition ?


yes, if it is mounted correctly. ACLs are specific to the operating system, so an ACL you enforce in windows will not apply to Linux. but you can set permissions for those same folder under Linux.  You will need to set /etc/fstab correctly. should look something like this.

```
/**location**/**of_partition** /mnt/**mount_point** ntfs-3g silent defaults,locale=en_GB.utf8 0 0
```

there are issues when mounting an NTFS encrypted volume with truecrypt, where you can't set permissions afaik, however, i'm sure there is a way to set mount options to allow it. best ask on the TrueCrypt forums.

> **mysticav said:**
> 
IF different users have account on that /home directory, how can you restrict access one from each other?


well inside the Home root directory there are profile folders, much like 'Documents and Settings'
you can just change the permissions to what is required, or leave as default. thing to get use to in linux is groups. admin/users/custom made groups etc. you can specify permissions for groups or individually for each account.

> **mysticav said:**
> 
Of course, they will share the say truecrypt password for mounting the partition, but they should  have access only to their directory. Ubuntu locks the users to their directory : /home/user/


you will need to set the permissions twice, one for each operating system. if you are  that paranoid you can set up a second encrypted container for your own files within the first, or a separate partition.

> **mysticav said:**
> 
I wonder how ubuntu handles it with truecrypt, because the decrypt process must happens before the OS attempts to asign the home directory for the user. 


that is a good point, there are a lot of hidden directories that applications require, the equivalent of application data in Windows. so I don't know if it would be more wise to just create two partitions, one for the shared encrypted partition for personal files, have it auto mount at boot and a second for the Home directory and Data.  You can then use Ubuntu's built in encryption that will decrypt the home folder when you log in to avoid unwanted access.

[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)

best ask on the TrueCrypt forums for the specifics, there might be a way to set your home folder as an encrypted TrueCrypt container and have it auto mount at login. i couldn't be sure.

remember that not only the encrypted file needs to be in ntfs but the whole partition. :)

---

