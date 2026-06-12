---
title: "accidentaly removed all the permission from /bin folder. root not abl to run any cmd"
date: 2009-10-14
forum: Security
---

### Post by viewguest on 2009-10-14
I have accidentally change the permission of /bin folder with chmod -rwx /bin
now i am not able to login with any user or fire any command. can not even change the permission of /bin folder as chmod command is not accessable .

Only hope is there is one session with which i have logged in, that is the only access i have.

Let me know if we can change the permission back.

your quick response will be appreciated.

---

### Post by jeremyswalker on 2009-10-14
Did you try to reboot and select the Recovery Mode option from the grub boot menu? If you do that, select to go to the root console. Once there, execute the following to return permissions back:
```
chmod 755 /bin
```

---

### Post by viewguest on 2009-10-14
actually no command which is there in bin is executable!!
it gives following error 

[COLOR=#000000][SIZE=3][root@10 /]# chmod 
-bash: /bin/chmod: Permission denied[/SIZE][/COLOR]

---

### Post by phillw on 2009-10-14
Use a 'Live' CD, drop down to terminal, do a ```
sudo fdisk -l
```to get your hard drives' name - navigate to the root directory on the hard drive
issue
```
sudo chmod 755 /bin 
```hopefully, that will get your bin directory back for you.

Phill.

---

### Post by jeremyswalker on 2009-10-14
Yeah, I don't know what I was thinking. You will probably have to use the LiveCD to fix it, as phillw said. However, once you figure out which partition your root filesystem is on, you need to mount it. For example, if it was on /dev/sda1, you would issue the following:
```
sudo mount /dev/sda1 /mnt/sda1
```
Of course, this is just an example. You will have to create the mount point if it doesn't exist.
Then, working off the example mount point, you would issue the following to change the permissions back:
```
sudo chmod 755 /mnt/sda1/bin
```

---

### Post by __p1n__ on 2009-10-14
There is another choice.

If you still have a session open then just write and compile your own fixup C program.  Note that the program will need uid=0 effective permissions to successfully update /bin.

Return values:

0 = success
-1 = failure
-2 = impossible failure

caveat: I didn't compile or test it so try it on a scratch machine first.

****************************************************************

#include <stdio.h>
#include <errno.h>
#include <sys/stat.h>

int main( int argnum, char **argv )
{
	int ret = -2;

	if((ret = chmod( "/bin", 0x00755 ))
		printf( "error %d\n", errno );
	

	exit( ret );
}

---

### Post by movieman on 2009-10-14
> **jeremyswalker said:**
> 
```
sudo chmod -R 755 /mnt/sda1/bin
```

Wouldn't that trash any setuid programs in /bin?

If the permissions are wrong on the /bin directory, then fixing that is easy. If they're wrong on the programs in the /bin directory then your simplest solution may be a reinstall to ensure that all files have the correct permissions.

---

### Post by __p1n__ on 2009-10-14
> **movieman said:**
> Wouldn't that trash any setuid programs in /bin?

If the permissions are wrong on the /bin directory, then fixing that is easy. If they're wrong on the programs in the /bin directory then your simplest solution may be a reinstall to ensure that all files have the correct permissions.

Yeah, the command in the original post only affected the /bin folder and not anything in it.  Consequently the recursive chmod command is inappropriate.

---

### Post by jeremyswalker on 2009-10-14
> **__p1n__ said:**
> Yeah, the command in the original post only affected the /bin folder and not anything in it.  Consequently the recursive chmod command is inappropriate.

LOL. I never caught that the first time I read it. Looking back at the original post, I agree the command should not need to be executed recursively. I have fixed my posts accordingly.

---

### Post by viewguest on 2009-10-15
hey guys thanks for ur response..
i hv booted from live cd.. n went into rescue mode

when i type command, it give following reponse
sh-3.2# [B]sudo mount /dev/sda2 /mnt/sda2 
sh: sudo: command not found

[/B]if i type foll command

sh-3.2# [B]mount /dev/sda2 /mnt/sda2
mount: mount point /mnt/sda2 does not exists[/B]

same with the cmd [B]mount /dev/sda1 /mnt/sda1
[/B]
and both sda2 n sda1 are there in dev folder[B].
[/B]

sa

---

### Post by viewguest on 2009-10-15
the system is on fedora 5..

---

### Post by jeremyswalker on 2009-10-15
> **viewguest said:**
> hey guys thanks for ur response..
i hv booted from live cd.. n went into rescue mode

when i type command, it give following reponse
sh-3.2# [B]sudo mount /dev/sda2 /mnt/sda2 
sh: sudo: command not found

[/B]

When you are in rescue mode, you are already the root user. "sudo" is not needed.

> **viewguest said:**
> if i type foll command

sh-3.2# [B]mount /dev/sda2 /mnt/sda2
mount: mount point /mnt/sda2 does not exists[/B]

same with the cmd [B]mount /dev/sda1 /mnt/sda1
[/B]
and both sda2 n sda1 are there in dev folder[B].
[/B]

Right. You will need to create the mount point. So, sticking to my example, we would create the mount point for /dev/sda2 like so:
```
mkdir -p /mnt/sda2
```
Once this is done, now we can mount your partition like:
```
mount /dev/sda2 /mnt/sda2
```

---

### Post by __p1n__ on 2009-10-15
You should check the permissions on the mount point /mnt/sda2 after you create it but before you mount /dev/sda2.  The permissions should be 7xx (where x is anything.)

---

