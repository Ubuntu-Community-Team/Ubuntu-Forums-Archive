---
title: "GCC compile errors in Simscan"
date: 2010-01-18
forum: Server Platforms
---

### Post by killer50stang on 2010-01-18
I get the following error when I try and "make" complile simscan.  I beleive this is an Gcc issue?  Any ideas?


/usr/include/bits/fcntl2.h:51: error: call to â€˜__open_missing_modeâ€™ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [simscanmk.o] Error 1
make[2]: Leaving directory `/root/simscan-1.4.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/simscan-1.4.0'
make: *** [all] Error 2
]0;root@Qmail-Server: ~/simscan-1.4.0root@Qmail-Server:~/simscan-1.4.0# 
[Kroot@Qmail-Server:~/simscan-1.4.0# /usr/include/bits/fcntl2.h:51: error: call to â__open_missing_modeâ declared with attribute error: open with O_CREA        
                                   T in second argument needs 3 arguments
bash: /usr/include/bits/fcntl2.h:51:: No such file or directory
]0;root@Qmail-Server: ~/simscan-1.4.0root@Qmail-Server:~/simscan-1.4.0# make[2]: *** [simscanmk.o] Error 1
make[2]: Leaving directory `/root/simscan-1.4.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/simscan-1.4.0'
make: *** [all] Error 2
make[2]:: command not found
]0;root@Qmail-Server: ~/simscan-1.4.0root@Qmail-Server:~/simscan-1.4.0# make[2]: Leaving directory `/root/simscan-1.4.0'
> make[1]: *** [all-recursive] Error 1
> make[1]: Leaving directory `/root/simscan-1.4.0'
> make: *** [all] Error 2
>

---

### Post by kiranmurari on 2010-01-19
Hi,


Can you specify which version of gcc you are using?
Even I encountered the same error with gcc-4.4.1.
   	

Regards,
Kiran

---

### Post by killer50stang on 2010-01-19
gcc version 4.4.1 

any ideas?  I need to get this working

---

### Post by kiranmurari on 2010-01-19
[FONT=Verdana]Hi,[/FONT]
[FONT=Verdana]   You can try to downgrade the gcc version to 4.1[/FONT][FONT=Verdana]
[/FONT]```
# sudo apt-get install gcc-4.1
```[FONT=Verdana]
[/FONT][FONT=Verdana]  Now you have two versions of gcc installed on your machine and the gcc version is still 4.4.1.
[/FONT]```
# gcc --version
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

# cd /usr/bin
# ls -l | grep gcc
-rwxr-xr-x 1 root   root        428 2006-05-07 14:58 c89-gcc
-rwxr-xr-x 1 root   root        451 2006-05-07 14:57 c99-gcc
lrwxrwxrwx 1 root   root         16 2010-01-20 02:17 gcc -> gcc-4.4  --- Current version of gcc
-rwxr-xr-x 1 root   root     200068 2009-08-27 17:37 gcc-4.1
-rwxr-xr-x 1 root   root     220484 2010-01-10 21:26 gcc-4.4
-rwxr-xr-x 1 root   root      16288 2009-08-27 17:33 gccbug-4.1
lrwxrwxrwx 1 root   root          7 2010-01-07 19:32 i486-linux-gnu-gcc -> gcc-4.4
lrwxrwxrwx 1 root   root          7 2010-01-20 02:16 i486-linux-gnu-gcc-4.1 -> gcc-4.1
lrwxrwxrwx 1 root   root          7 2010-01-20 01:56 i486-linux-gnu-gcc-4.4 -> gcc-4.4
 
```[FONT=Verdana]Change the symlink of gcc from gcc-4.4 to gcc-4.1
[/FONT]```
# ln -sf gcc-4.1 gcc
# gcc --version
gcc (GCC) 4.1.3 20080704 (prerelease) (Ubuntu 4.1.2-27ubuntu1)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 
```[FONT=Verdana]
Issue the following commands:
[/FONT]```
# make clean
# make
```[FONT=Verdana]
[/FONT][FONT=Verdana]I did not face any problem compiling simscan this way.[/FONT]

[FONT=Verdana]Let me know if you face any issues[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by killer50stang on 2010-01-19
wow!  that worked!  perhaps a bug?  Thanks

---

