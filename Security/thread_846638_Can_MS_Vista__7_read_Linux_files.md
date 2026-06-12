---
title: "Can MS Vista / 7 read Linux files?"
date: 2008-07-01
forum: Security
---

### Post by Beowulf.1000 on 2008-07-01
I do not want Microsoft to be able to read my Linux files. It just plain bothers me on principle, and it is only going to get worse from what I hear with the upcoming MS Windows 7 and its integration in CPU chips, etc.. So if I have a dual boot system, Windows and [Ubuntu 8.10] Linux, when booting into Windows would the Windows operating system be able to scan my Linux data files? Or should I have to have a Linux-only system to avoid any Microsoft scanning of my files?

I am thinking mostly about music files, Microsoft misinterpreting what is legal and not, with all the funky DRM digital rights management coming soon to a CPU chip and Microsoft operating system like MS Vista or the just announced next version -- Microsoft 7. I have ripped songs off my CDs that I own, I do not want MS doing funking stuff with my song files, or reporting me for music I own. Then there is the whole issue of videos (which I own legally but might want to watch off my hard drive/DVD occassionally) and DRM and libdvdcss; I just would rather keep MS OS from even seeing my stuff. But I do not think encryption would help because then I could not play my music etc on the fly with xmms or amarok, etc.

---

### Post by Biochem on 2008-07-01
First Windows can't read Linux file system by default, you have to install special driver for that. So unless MS changes it's approach you have a first layer aof security.

If you are paranoid you could put your music in an encrypted volume or partition. That way nobody will be able to scan your file unless they know the key. And contrary to you belief, encrytion with TrueCrypt, dm-crypt or encfs will allow you access your files on the fly once unlock. So amarock will have access to them.

---

### Post by Beowulf.1000 on 2008-07-01
So I would have to unlock an encrypted partition after booting into linux to play music, then lock again before exiting, to be secure from Windows reading the files if I were to reboot into Windows without relocking the linux partition? (I am assuming Windows 7 or Windows 8 might implement a way to read Linux partitions, it seems a logical next step. But that would really seem to open a legal quagmire-- one operating system snooping on another and perhaps causing havoc).

> **Biochem said:**
> ... And contrary to you belief, encrytion with TrueCrypt, dm-crypt or encfs will allow you access your files on the fly once unlock. So amarock will have access to them.

---

### Post by Beowulf.1000 on 2008-07-01
Okay I feel a bit stupid even asking this, but if Ubuntu were installed alongside Windows using the option to install Ubuntu "within" Windows, where Ubuntu uses the NTFS filesystem, am I correct (duh) in assuming the Windows OS would have full ability to keep track of what was on the Ubuntu "filesystem"/OS? (since Ubuntu uses the NTFS filesystem in such a case)

> **Biochem said:**
> First Windows can't read Linux file system by default, you have to install special driver for that. So unless MS changes it's approach you have a first layer aof security.....[cut]

---

### Post by thschiavo on 2008-07-01
Isn't it because Ubuntu, as a Linux, use ext2(3) ([http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)) as partition for it's filesystem? :confused: I didn't understand if the Ubuntu do use NTFS filesystem in your case... Is it? Is it possible?

Windows can't read it, instead in during the install the Installer could write it. I use a really good program for WinXP when I want to see Ubuntu's filesystem, but I don't have the program's name right here.

---

### Post by hyper_ch on 2008-07-02
(1) linux cannot be installed onto ntfs as permissions are one of the basic things that's required in linux

(2) you can access ext2/3 partitions from windows use the ext2/3 drivers from [http://www.fs-driver.org](http://www.fs-driver.org)

(3) linux can access ntfs partitions and read/write to them with ntfs-3g

(4) if you fully encrypt the linux install, then windows can't access it... at least not the files within... but it can delete of course the whole partitions

---

### Post by Beowulf.1000 on 2008-07-02
Respectfully I have to tell you that is incorrect. Ubuntu now has an install option to install Ubuntu within the NTFS Windows filesystem. I have done it, I know it can be done. (I also found it impossible to then get rid of grub, I had to use the rescue disk that came with my laptop, so beware). Put an Ubuntu 8.04 Desktop live CD into a CD drive while booted into Windows, you will see that new install option that I have never seen in any previous version of Ubuntu let alone any version of Linux distro.

The Ubuntu system (root, users, home, etc) install (into Windows option, not a normal install) all goes into an NTFS filesystem folder on the Windows drive, there is no ext3 or ext2 utilized, no partitioning of any drives is done. But that tells me that if that install option is used, being on NTFS and in a folder on the C: drive and inside Windows (Vista in this case), it seems logical that the Windows operating could if it wanted to peruse the Linux files on that NTFS filesystem and Windows folder. 

[QUOTE=hyper_ch;5303058](1) linux cannot be installed onto ntfs as permissions are one of the basic things that's required in linux...

---

### Post by hyper_ch on 2008-07-02
> **Beowulf.1000 said:**
> Respectfully I have to tell you that is incorrect. Ubuntu now has an install option to install Ubuntu within the NTFS Windows filesystem.
You create a file that uses internally an ext3 system... it's basically like virtualization BUT it is not installing ubuntu onto an ntfs system ;9

Besides that thing is called wubi and it has been around at least since 7.10 - just not integrated into the desktop cd

---

### Post by Beowulf.1000 on 2008-07-02
So the wubi method, even thought installed into MS Windows' NTFS system, (1) uses some virtual ext3 filesystem? and (2) could not be read by MS Windows when booted into MS Windows? 

It just seems odd, I guess I do not understand wubi, that even though wubi installed Linux exists on an 'NTFS system' as a folder in Windows, Windows could not read it when booted into windows? (but for that matter, it still seems to me all it would take is a future version of Windows to integrate an ext3 file reading tool in the Win OS to keep an eye on what is in that wubi Linux system (meaning maybe the only way to really keep Windows from prying at my Linux system is to just never boot into Windows, never have Windows even on a computer alongside Linux?)

> **hyper_ch said:**
> You create a file that uses internally an ext3 system... it's basically like virtualization BUT it is not installing ubuntu onto an ntfs system ;9 Besides that thing is called wubi and it has been around at least since 7.10 - just not integrated into the desktop cd

---

### Post by The Cog on 2008-07-02
As it happens, both my PC and my USB backup drive are formatted with JFS rather than EXT2/3. I think at the back of my mind, one of the thoughts in favour of this decision was the knowledge that no JFS driver exists for windows. Another peverse reason was that JFS was mentioned in the SCO lawsuit as particularly causing them anguish. It also seems to perform very well - I'm happy with it.

---

### Post by Gamma746 on 2008-07-03
The most secure solution would probably be to install Windows in a virtual machine under Ubuntu.  (Other than not using Windows at all, that is.)

---

### Post by Beowulf.1000 on 2008-07-03
Interesting. Well, I have Ubuntu installed now on one drive, Vista on its original. Now I am on a quest to keep Windows' prying eyes now and in the future off my linux system, just a matter of principle.  I need to make a post about this on ubuntu forums soon, seek some on the fly encryption like truecrypt, hoping something like that can encrypt but also allow easy access to data files even by applications like Openoffice, etc.

> **The Cog said:**
> As it happens, both my PC and my USB backup drive are formatted with JFS rather than EXT2/3. I think at the back of my mind, one of the thoughts in favour of this decision was the knowledge that no JFS driver exists for windows. Another peverse reason was that JFS was mentioned in the SCO lawsuit as particularly causing them anguish. It also seems to perform very well - I'm happy with it.

---

