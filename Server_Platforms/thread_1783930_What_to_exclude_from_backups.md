---
title: "What to exclude from backups?"
date: 2011-06-16
forum: Server Platforms
---

### Post by PeterK2003 on 2011-06-16
I want to make a full backup of the system less any unnecessary files(cache, temp, bin files that are always installed with a new install, etc).

So far i am excluding:
/proc /lost+found /sys /mnt /media /dev

What else can i exclude?

Thanks,
Peter

---

### Post by jerrrys on 2011-06-16
don't forget "trash" / thumnails cache

---

### Post by PeterK2003 on 2011-06-16
also \CDROM i believe shoud be excluded

---

### Post by dFlyer on 2011-06-16
You might want to think about excluding firefox cache and if your using shotwell there cache can be fairly large.

---

### Post by PeterK2003 on 2011-06-16
How should i exclude Trash and thumbnails?

*/trash/* and */Thumbnails/*

---

### Post by BkkBonanza on 2011-06-16
If you don't want temp and bin files then also exclude,

/tmp
/bin
/usr
/boot
/lib

maybe 

/opt

You may find it easier to just include,

/home /etc /var

and exclude known cache files.

---

### Post by PeterK2003 on 2011-06-16
I don't know I kinda feel better about excluding rather than including.

How about sbin?

---

### Post by PeterK2003 on 2011-06-16
nevermind your right it will just be easier to include...Thanks

So just etc and var and home should do me?

This is a MYSQL, DNS, DHCP, APACHE box.

---

### Post by eric-yorba on 2011-06-16
The only thing you really need to backup is your home folder. Backing up program files is redundant, since they can be restored easily.

---

### Post by BkkBonanza on 2011-06-16
MySql usually stores data under /var by default so you'd want to be sure you cover that or wherever your data is. Also websites are often under /var/www. Obviously you'd want to make sure you get anything like that. 

DNS and DHCP configs along with MySql/Apache configs are generally under /etc as with other system configuration.

On a server you likely don't have much under /home but you will want anything there and you also probably want to include /root as well.

---

### Post by jerrrys on 2011-06-16
[COLOR=Red]BkkB[COLOR=Black]

Why backup the /root?  i ask because i am not...  should i be?
[/COLOR][/COLOR]

---

### Post by BkkBonanza on 2011-06-16
There isn't usually much in /root but it may have a few config settings related to shell use as root. If you didn't change anything there then it's likely not needed. I sometimes update the .bashrc to have some useful aliases and sometimes a few files (like .ssh stuff) may end up in there.

---

