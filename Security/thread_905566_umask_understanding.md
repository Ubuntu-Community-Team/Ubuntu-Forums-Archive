---
title: "umask understanding"
date: 2008-08-30
forum: Security
---

### Post by Rany Albeg on 2008-08-30
Hi,

My access permissions to the folder 'Commands' and all its files are 755.
when i open a new file in this folder , its permissions are 644. 

I want to save time setting these permissions over and over again with 'chmod -R 755' ,  so i decided to use umask.

As i was told ,umask works a bit strange.
When you set a new value for umask it sets the default permission to be the difference between the current permission and the one you just determine.

In assumption that my current defaut permissions are 755 , i set the umask value to be 000 so that the default permissions will stay 755 , and so when i will open a new file or directory under the folder 'Commands' ,it will contain its main folder access permissions.

Seems i dont know how to use umask cuz i cant get it done.

Need some help,

Thanks.

---

### Post by Vivaldi Gloria on 2008-08-30
Subtract umask from 0777 to find permissions for directories and subtract from 0666 to find permissions for files (you write 0 for -1 if you get any).

umask 0022 = 755 for dirs & 644 for files.
umask 0000 = 777 for dirs & 666 for files.
umask 0027 = 750 for dirs & 640 for files.
umask 0077 = 700 for dirs & 600 for files 
umask 0007 = 770 for dirs & 660 for files 

Note that you cannot use umask to make new files executable.

---

### Post by Rany Albeg on 2008-08-30
Thanks i got it.
Have a nice day;)

---

### Post by Vivaldi Gloria on 2008-08-31
> **Rany Albeg said:**
> Thanks i got it.
Have a nice day;)

You're welcome mate. Have fun.

---

### Post by derekeverett on 2010-03-23
> **Vivaldi Gloria said:**
> Subtract umask from 0777 to find permissions for directories and subtract from 0666 to find permissions for files (you write 0 for -1 if you get any).

umask 0022 = 755 for dirs & 644 for files.
umask 0000 = 777 for dirs & 666 for files.
umask 0027 = 750 for dirs & 640 for files.
umask 0077 = 700 for dirs & 600 for files 
umask 0007 = 770 for dirs & 660 for files 

Note that you cannot use umask to make new files executable.

This helped me today.. so thank you!

---

### Post by immeëmosol on 2010-11-02
indeed very nice:
> **Vivaldi Gloria said:**
> [...]
umask 0022 = 755 for dirs & 644 for files.
umask 0000 = 777 for dirs & 666 for files.
umask 0027 = 750 for dirs & 640 for files.
umask 0077 = 700 for dirs & 600 for files 
umask 0007 = 770 for dirs & 660 for files 
[...]

for people coming across this post, pick the umask you like :
```

                  u   g   o        bit_values    chmod
umask 0077   >   rwx --- ---   >   700 600   >   u=rwX,go= 
umask 0007   >   rwx rwx ---   >   770 660   >   ug=rwX,o= 
umask 0027   >   rwx r-x ---   >   750 640   >   u=rwX,g=rX,o= 
umask 0022   >   rwx r-x r-x   >   755 644   >   u=rwX,go=rX 
umask 0002   >   rwx rwx r-x   >   775 664   >   ug=rwX,o=rX 
umask 0000   >   rwx rwx rwx   >   777 666   >   a=rwX 

u = user
g = group
o = other
a = all( user , group , other )

r = read
w = write
x = execute//read,
   using a capital x will make the chmod-program use it for directories only, e.g.:
chmod -R u=rwX,g=rX,o= ./
this command above will make
   the current directory and all it's files and subdirectories
      writable for their owner(s)(also: user),
      readable for their group(s) and
      inaccessible for all others


```

it's all about bits :p
can someone come up with a good use for :
umask 0770
?

---

