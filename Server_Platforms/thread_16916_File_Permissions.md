---
title: "File Permissions"
date: 2005-02-24
forum: Server Platforms
---

### Post by Jesus Franco on 2005-02-24
Hello, I need help with settings a folder and all it's sub folders and files with the chmod of 777. Currently it is 555 Witch only grants me access to use and copy the files. These files are files copied over from my previous Windows installation. I need to edit some of these files. Anywho the folder is setup like this.

/home/jesus/Media Libary/(all the files in here)

The Windows drive was ntfs witch is why it kept the read only permissions after i copied it over to my linux drive. 

I copied them over in the terminal. I do feel comfortable with the terminal so any comands's would help. I'm done with windows forever    :-#

---

### Post by macewan on 2005-02-24
sudo chown -R jesus:jesus Media*
chmod -R +777 Media*

---

### Post by ow50 on 2005-02-24
If you want to set different permissions for files and directories you could use:
```
cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
find -type d -exec chmod 755 {} \;
find -type f -exec chmod 644 {} \;
```
That would mark jesus as the owner and set the default permissions the files (644) and directories (755).

---

### Post by goedson on 2005-02-25
[QUOTE=ow50]If you want to set different permissions for files and directories you could use:
```
cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
find -type d -exec chmod 755 {} \;
find -type f -exec chmod 644 {} \;
```
.[/QUOTE]

You could also do:
```

cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
chmod -R u=rwX,go=rX .

```

This would add execute permission only to directories, having the effect of the two find commands above.

---

### Post by Jesus Franco on 2005-02-25
Wow thaks alot. My pc is exactly the way I wanted it to be.
Lots of thanks to the comunity for all those how to's.  :smile:

---

### Post by brass on 2005-12-13
[QUOTE=goedson]You could also do:
```

cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
chmod -R u=rwX,go=rX .

```

This would add execute permission only to directories, having the effect of the two find commands above.[/QUOTE]
I have a fat32 partition that is mounted on /media/hda9.

The fstab says:
```
/dev/hda5           /media/hda9            vfat       rw,user       0       0
```

My user is 'jay' and is part of the group 'user', but I cannot write to that partition.  I cannot chown, or chmod.

```
sudo chown -R jay:jay *
``` returns the error ```
Operation not permitted
```  I can make directories with sudo, but for some reason I cannot change permissions or ownership.   Can anyone help me?

btw:  I am running Ubuntu 5.10 Breezy AMD 64.

---

### Post by LordHunter317 on 2005-12-13
**Never, ever, ever use 777.**   Just don't.  It's wrong, dangerous, and a source of trouble.  If you ever think you need to use 777 (or 666) for anything, stop a second and backup, as you likely made a mistake elsewhere.

As for you brass, you should change the options in fstab from rw,user to 'rw,uid=jay' to let you and just you access the files.

---

### Post by clappr on 2007-10-14
> **ow50 said:**
> If you want to set different permissions for files and directories you could use:
```
cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
find -type d -exec chmod 755 {} \;
find -type f -exec chmod 644 {} \;
```
That would mark jesus as the owner and set the default permissions the files (644) and directories (755).

I did this and now I can not log in with the exception of getting into the failsafe terminal... Help!!!

The message I get is:

(gnome-session:5271): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/richard/.gnome2/ ': Permission denied

---

### Post by koenn on 2007-10-14
did you actually do the ```
sudo chown -R jesus:jesus *
``` part ? with 'jesus" ?

---

### Post by clappr on 2007-10-14
no, I did richard:richard     

I applied the commands to /home/richard

so now I think I have changed the permissions of all the "." dot files in /home/richard

I now have startup problems where dot files are not being accessed or executed properly.

I need to know how to change them back to their original state.

---

### Post by clappr on 2007-10-14
> **goedson said:**
> You could also do:
```

cd '/home/jesus/Media Libary/'
sudo chown -R jesus:jesus *
chmod -R u=rwX,go=rX .

```

This would add execute permission only to directories, having the effect of the two find commands above.

I seemed to have fixed my problem...

I applied the code above relevant to my system like so:

cd /home/richard
sudo chown -R richard:richard .*
chmod -R u=rwX,go=rX

however I am wondering if the dot files in the above folder originally had only root permission?  perhaps someone can look in there /home/user/ folder at the hidden .dot folders and files and let me know if the permissions are root

---

### Post by freebeer on 2007-10-14
no.. they're owned by the user account.  This makes sense since, in a lot of cases, the . folders are configuration folders specific to the user, so they need permission to access and change their own configuration files specific to them.

---

### Post by ken123 on 2007-10-14
i have an FAT32 partition and i can do everything on it i want, except access the "my documents" folder that wax created by my windows partition. i can't change any permissions. i might be doing it wrong though. anyone got any suggestions to fix my problem?

---

### Post by goedson on 2007-10-14
> **clappr said:**
> I did this and now I can not log in with the exception of getting into the failsafe terminal... Help!!!

The message I get is:

(gnome-session:5271): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/richard/.gnome2/ ': Permission denied

Maybe you've changed ownership of the files to the wrong user. Try this:

```

cd /home/richard
chown -R richard .
chmod -R u+rwX .

```

This will give you ownership and write access to all your files.

---

