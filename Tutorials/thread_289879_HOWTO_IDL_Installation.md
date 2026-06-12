---
title: "HOWTO: IDL Installation"
date: 2006-10-31
forum: Tutorials
---

### Post by Bosonator on 2006-10-31
I recently purchased the IDL Student Edition data analysis software for my graduate physics studies. The software is good for scientific image manipulation and analysis, and is commonly used by astronomers and medical physicists, among others.

The software is officially supported only for RedHat Linux, but I was able to get it to run on Ubuntu Edgy using the following procedure:

1. *Install the Corn shell.*
The default terminal shell in Ubuntu is called "Bash" (Bourne Again Shell). The installation script for IDL, however, is written for "Csh" (the Corn Shell). Install this using apt-get.
```
sudo apt-get install csh
```

2. *Mount the installation media.* 
Just to be on the safe side, I unmounted the disk first, because Ubuntu typically automounts cdrom media, and you want to make sure the permissions are right.
```
sudo umount /media/cdrom0/ 
sudo mount -o ro -t iso9660 /dev/cdrom /media/cdrom0

```
(your devices and mount points might differ from mine. Name them accordingly)

3. Once the disk is mounted, start csh from a terminal using sudo.
```
sudo csh
```

4. You will now be running the installation script. On my machine, this command looks like this:
```
/media/cdrom0/xinstall.sh
```

5. The installation window pops up, and you have to answer a bunch of questions. When it asks you if you want it to create the symbolic links, tell it "yes".

6. You have IDL installed! Start it by issuing "idlde" from the command line.

---

### Post by ricardo_at on 2007-04-22
hi! :D
i follow your "wiki" but get a nice :

exec: 302: ./xinstall.linux.x86: Permission denied

and when i try to umount and then mount, console tell me about no unit in cdrom0.... but there is the cd :s

what do u think?

---

### Post by Bosonator on 2007-04-24
Hmmm.... I don't have any solutions right off the bat. I will soon be going through the install procedure again myself, though, so if this problem comes up for me, I'll let you know if I get around it. Tell me, though, are you using x86 Ubuntu or AMD64? And what version of Ubuntu?

---

### Post by Bosonator on 2007-04-24
Did you remember to follow the umounting/remounting procedure in step 2? It sounds like the cdrom isn't mounted by root.

---

### Post by jazpearson on 2007-09-18
thankyou for this...... i was having difficulty with the installation process.

mounting and unmounting the cdrom was what made the difference.

---

### Post by johnnycakes on 2008-01-25
Thanks a lot Bosonator... been fiddling with this for a while. Your post was spot on!

J.

---

### Post by SAR-winds on 2010-10-26
Thanks Bosonator,

I have just got installed IDL 6.0 on my UBANTU 10.10. 
Spent 5 min. Works just perfect. 
Best Regards

---

### Post by guillem_tell on 2012-11-06
I am trying to follow the wiki with Kubuntu 12.10 and IDL7.0

I am getting mad because I cannot mount the dvd drive usin the command line. Anyways, when the dvd is mounted and I try to execute csh or tcsh, I receive the following:

guillem@guillem-arbeit:~$ sudo mount -o ro -t iso9660 /dev/sr0 /media/IDL70
mount: /dev/sr0 already mounted or /media/IDL70 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/IDL70
guillem@guillem-arbeit:~$ sudo csh
guillem-arbeit:~# /media/IDL70/xinstall.sh
/media/IDL70/xinstall.sh: Command not found.
guillem-arbeit:~# 


I do not know what more to do...

---

### Post by guillem_tell on 2012-11-12
After installing tcsh and the 32 bit libraries (ia32) everything works fine on Kubuntu 12.10 64bit.

---

