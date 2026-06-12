---
title: "Command to find available disk space"
date: 2007-12-26
forum: Server Platforms
---

### Post by frodemt on 2007-12-26
I am working on a program to manage slideshows from remote. I was wondering if I could get a output of disk space to a textfile like this:

Start of file
43
54
End of file

The first number is uded disk space and the second number is available disk space.

---

### Post by anubhavrocks on 2007-12-26
use the df command
```
df
```

---

### Post by frodemt on 2007-12-26
> **anubhavrocks said:**
> use the df command
```
df
```

yes, but how do I output to a file like I described?

---

### Post by HermanAB on 2007-12-26
df > filename

---

### Post by p_quarles on 2007-12-26
I thought the question was interesting, so I did some tinkering and found a partial solution. This will only output the *used* space on the filesystem, but it does so in exactly the format you're asking for:
```
sudo du -ahc | grep total > hd.info
```I use sudo here only because without it, the output of grep includes errors about not being able to access certain directories, and I didn't want those messages in the file. I'm sure there's another way to exclude those lines, though.

In any case, that's half of it. I assume it would also be possible to write a short script that would subtract this value from the total hard drive space, giving you the amount of free space.

Also, you can add lines to the end of the file by using ">>" instead of ">"

EDIT: To do this without root privileges, use "grep -s". That way, the error messages will not be sent to the text file. Of course, I'm doing this with my /home partition. Running this on a root-owned partition would require sudo or su.

---

### Post by burbankmarc on 2007-12-27
here's my solution:

```
df -h | grep /dev/sda3 | cut -d" " -f14 > disk.space && df -h | grep /dev/sda3 | cut -d" " -f16 >> disk.space

```

---

### Post by mmichalik on 2007-12-27
df -klh 

will give you your total size, space used, space available in megabytes as well as the mount points.  (but, granted, it won't put it out in the format you requested it to be in.  Next time, I should read the entire post.  DUH!)

---

### Post by xdice on 2007-12-27
> **frodemt said:**
> I am working on a program to manage slideshows from remote. I was wondering if I could get a output of disk space to a textfile like this:

Start of file
43
54
End of file

The first number is uded disk space and the second number is available disk space.

```
df -h | grep /dev/sda1 | awk '{ print $3"\n"$4 }' > sda1.diskspace
```

Output:
```

$ cat sda1.diskspace 
51M
910M

```

First number is used disk space, second number is available diskspace.

---

### Post by frodemt on 2007-12-27
> **xdice said:**
> ```
df -h | grep /dev/sda1 | awk '{ print $3"\n"$4 }' > sda1.diskspace
```

Output:
```

$ cat sda1.diskspace 
51M
910M

```

First number is used disk space, second number is available diskspace.

That is nearly perfect. How do I show it in GB?

---

### Post by p_quarles on 2007-12-27
> **frodemt said:**
> That is nearly perfect. How do I show it in GB?
The -h option in the df command will automatically choose GB or MB depending on the size of the drive.

---

### Post by frodemt on 2007-12-27
Nice! I will report back when I have testet this in my program. :-)

---

### Post by frodemt on 2007-12-27
[http://tviberg.gotdns.com/nettside/slideshow_linux_en.php](http://tviberg.gotdns.com/nettside/slideshow_linux_en.php)

You have to scroll down to the bottom of the page to see the features of the program :-)

What do you guys think?

My boss is pleased at least :lolflag:

---

### Post by frodemt on 2007-12-27
Suddently the script does not work anymore?

I get this when doing df -h:

```
root@reklame:/home/frodemt# df -h
Filesystem            Size Used Avail Use% Mounted on
varrun                139M  132K  139M   1% /var/run
varlock               139M     0  139M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                139M     0  139M   0% /dev/shm

```

I did run the backup-script from this guide: 

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Does anyone know why this might have happened?

---

### Post by frodemt on 2007-12-28
I used this backup command: 

tar cvpjf backup.tar.bz2 --exclude=/proc/* --exclude=/lost+found/* --exclude=/home/user/backup.tar.bz2 --exclude=/mnt/* --exclude=/sys/* --exclude=/home/user/presenter/* /

and to restore I used: 

tar xvpfj backup.tar.bz2 -C /

This is not going to mess up the system right?

---

### Post by ghostdog74 on 2007-12-29
> **xdice said:**
> ```
df -h | grep /dev/sda1 | awk '{ print $3"\n"$4 }' > sda1.diskspace
```

could be shorter, without the grep
```

df -h /dev/sda1 | awk 'NR>1{ print $3"\n"$4 }' 

```

---

### Post by frodemt on 2007-12-29
Ok, I got it to work now. Had to do it without the backslash in the command because my program did not support that letter :S.

Thanks for your help people!

---

