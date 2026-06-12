---
title: "Help Making an ISO image for Virtualbox"
date: 2007-11-05
forum: Virtualisation
---

### Post by GNUoob on 2007-11-05
Hello all,

I installed Virtualbox and now wanted to install xp inside of that.

I got virtual running and all but am having difficulty with the cdrom reading when trying to install xp on/in it.

so i figured if i could mount an .iso of my cdrom it would avoid the issues i was having.

so that in mind how do i create one?

i googled "create an iso from a cd in linux" and got a bunch of cryptic posts. none of which help me because i don't understand their vague dialog. 

anyone care to help me out in creating one? i cant seem to figure out where ubuntu has my dvd and burner mounted.

how do i figure out where it lists them? i right clicked them in my desktop and it showed them as ...
Location: computer:///

so what does that mean??? 

i just wanted to make an iso and it would seem that i am clueless as to what i need to do.

HELP PLEASE

Thank you in advance

---

### Post by GNUoob on 2007-11-05
dave@Redbuntu:~$ sudo umount /dev/cdrom1 
[sudo] password for dave:
umount: /dev/cdrom1: not mounted
dave@Redbuntu:~$ dd if=/dev/cdrom1 of=file.iso bs=1024
dd: opening `/dev/cdrom1': No medium found
dave@Redbuntu:~$ dd if=/dev/cdrom2 of=file.iso bs=1024
dd: opening `/dev/cdrom2': No such file or directory
dave@Redbuntu:~$
dave@Redbuntu:~$ ls /dev/cdr*
/dev/cdrom1  /dev/cdrw1
dave@Redbuntu:~$ 


My DVD is im guessing is the /dev/cdrom1 and not the cdrw1

---

### Post by BennBuntu on 2007-11-05
My best bet,

install mkisofs
```
sudo apt-get install mkisofs
```

then, depending what your cdrom is called in /media/

```
mkisofs -o xp.iso /media/cdrom/
```

this should spit out a file called xp.iso in you home folder. Now add that to your virtualbox disc images with the manager and you can mount it in your machines.
edit: this assumes your cd is mounted, I think it has to be

---

### Post by dpar on 2007-11-06
I have 2 cdroms and when I had a similar problem with virtualbox I found that I was using the wrong cdrom. Picked the right one and everything went good.:lolflag:

I don't know if thats your problem, but thought I'd throw it in.:)

---

### Post by GNUoob on 2007-11-06
> **BennBuntu said:**
> My best bet,

install mkisofs
```
sudo apt-get install mkisofs
```

then, depending what your cdrom is called in /media/

```
mkisofs -o xp.iso /media/cdrom/
```

this should spit out a file called xp.iso in you home folder. Now add that to your virtualbox disc images with the manager and you can mount it in your machines.
edit: this assumes your cd is mounted, I think it has to be




dave@Redbuntu:~$ sudo apt-get install mkisofs
[sudo] password for dave:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mkisofs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
dave@Redbuntu:~$ mkisofs -o xp.iso /media/cdrom0 
Setting input-charset to 'UTF-8' from locale.
Unknown file type (unallocated) /media/cdrom0/.. - ignoring and continuing.
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 68
Path table size(bytes): 10
Max brk space used 0
174 extents written (0 MB)
dave@Redbuntu:~$ 


thanks but its not working :(

---

### Post by GNUoob on 2007-11-07
anyone?

---

### Post by Rhubarb on 2007-11-07
```
sudo aptitude install gnomebaker
```
That will install GnomeBaker, it's in your Applications --> Sound & Video --> CD/DVD writer GnomeBaker

From there just copy a CD, and tell it to output to an iso.
Super easy to do :)

---

### Post by GNUoob on 2007-11-07
This isnt working for me :(

[http://cid-b8f2dc6b322f04d0.skydrive.live.com/self.aspx/Ubuntu%20Screenshots/snapshot2.png](http://cid-b8f2dc6b322f04d0.skydrive.live.com/self.aspx/Ubuntu%20Screenshots/snapshot2.png)

---

### Post by Jose Catre-Vandis on 2007-11-07
> **BennBuntu said:**
> My best bet,

install mkisofs
```
sudo apt-get install mkisofs
```

then, depending what your cdrom is called in /media/

```
mkisofs -o xp.iso /media/cdrom/
```

this should spit out a file called xp.iso in you home folder. Now add that to your virtualbox disc images with the manager and you can mount it in your machines.
edit: this assumes your cd is mounted, I think it has to be

You need to unmount the cdrom first before you try to make the iso. Anbd just to be sure find out where your cdrom is.

Do as follows in a terminal:

```
cat /etc/fstab
```
and look for the entry for a cdrom something like /media/cdrom0
if you have more than one cdrom drive find out by trial and errror which one you want.

next unmount the cdrom
```
sudo umount /media/cdrom0
```

then run the make iso command:

```
dd if=/dev/cdrom0 of=file.iso bs=1024/
```

works every time for me

---

### Post by GNUoob on 2007-11-07
[http://gnuoob.googlepages.com/snapshot4.png](http://gnuoob.googlepages.com/snapshot4.png)

that is what i get when i try what you said

---

### Post by julian67 on 2007-11-07
```
dd if=/dev/cdrom0 of=file.iso
```

don't worry about the bs=1024

---

### Post by GNUoob on 2007-11-08
That worked,

thank you.

:popcorn:

---

### Post by Jose Catre-Vandis on 2007-11-09
Hoorah !   :)

---

### Post by WernerBrandt on 2007-11-12
Easier (?) way:

Put the CD/DVD in your drive, open the browser (places -> computer)
right click on the mounted (! :) ) CD drive image icon, select **"copy disc" **
Select (click) in the new window next to the drive on the drop down menu -> **"file image" ** click **"Write" **

and select location where you want it.
(As you can see by then, its already an ISO file)

---

