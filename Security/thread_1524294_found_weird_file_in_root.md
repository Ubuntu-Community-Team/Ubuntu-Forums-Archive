---
title: "found weird file in root"
date: 2010-07-05
forum: Security
---

### Post by macfuel on 2010-07-05
hi new to forum 
running Karmic 9.10 found weird file in root directory ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S<¶Àéºÿÿþé?&´?ú?j?Ò?o??f??&´?ú???f?&´

ls -l returns 
rnet@rnet-desktop:/$ ls -l
total 100
drwxr-xr-x   2 root root  4096 2010-05-26 18:48 bin
drwxr-xr-x   3 root root  4096 2010-06-05 07:05 boot
lrwxrwxrwx   1 root root    11 2010-05-26 18:05 cdrom -> media/cdrom
drwxr-xr-x  16 root root  3760 2010-07-04 20:23 dev
drwxr-xr-x 143 root root 12288 2010-07-04 20:22 etc
drwxr-xr-x   3 root root  4096 2010-05-26 18:16 home
lrwxrwxrwx   1 root root    33 2010-06-05 07:05 initrd.img -> boot/initrd.img-2.6.31-22-generic
lrwxrwxrwx   1 root root    33 2010-05-26 18:54 initrd.img.old -> boot/initrd.img-2.6.31-21-generic
drwxr-xr-x  18 root root 12288 2010-06-22 10:52 lib
drwx------   2 root root 16384 2010-05-26 18:05 lost+found
drwxr-xr-x   4 root root  4096 2010-06-05 23:32 media
drwxr-xr-x   2 root root  4096 2009-10-19 17:04 mnt
drwxr-xr-x   3 root root  4096 2010-06-05 22:07 opt
dr-xr-xr-x 175 root root     0 2010-07-04 20:23 proc
drwx------  11 root root  4096 2010-07-04 21:33 root
drwxr-xr-x   2 root root  4096 2010-05-26 22:17 sbin
drwxr-xr-x   2 root root  4096 2009-10-19 16:05 selinux
drwxr-xr-x   2 root root  4096 2009-10-28 13:55 srv
drwxr-xr-x  12 root root     0 2010-07-04 20:23 sys
drwxr-xr-x   2 root root  4096 2010-07-04 21:45 test
drwxrwxrwt  12 root root  4096 2010-07-04 21:42 tmp
drwxr-xr-x  11 root root  4096 2010-05-26 21:53 usr
drwxr-xr-x  16 root root  4096 2010-06-06 00:09 var
lrwxrwxrwx   1 root root    30 2010-06-05 07:05 vmlinuz -> boot/vmlinuz-2.6.31-22-generic
lrwxrwxrwx   1 root root    30 2010-05-26 18:54 vmlinuz.old -> boot/vmlinuz-2.6.31-21-generic
-rw-r--r--   1 root root   540 2010-07-02 23:45 ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S<¶Àéºÿÿþé?&´?ú?j?Ò?o??f??&´?ú???f?&´

tried to remove file no luck  " sudo rm -rf "file name""  returned 

rnet@rnet-desktop:/$ rm -rf ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S<¶Àéºÿÿþé?&´?ú?j?Ò?o??f??&´?ú???f?&´
[1] 2857
[2] 2858
[3] 2859
bash: ¶Àéºÿÿþé?: No such file or directory
´?ú?j?Ò?o??f??: command not found
´: command not found
´?ú???f?: command not found
[1]   Exit 1                  rm -rf ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S < ¶Àéºÿÿþé?
[2]-  Exit 127                ´?ú?j?Ò?o??f??


any help?

R

---

### Post by teejaybee on 2010-07-05
I'd check out the contents before you nuke it, just in case it's something nasty instead of something created by pasting crazy stuff to the console accidentally.

Either escape all the crazy characters, or put the whole filename inside quotes to delete it.

---

### Post by macfuel on 2010-07-05
> **teejaybee said:**
> I'd check out the contents before you nuke it, just in case it's something nasty instead of something created by pasting crazy stuff to the console accidentally.

Either escape all the crazy characters, or put the whole filename inside quotes to delete it.
  
tried to cat file name 

rnet@rnet-desktop:/$ cat ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S<¶Àéºÿÿþé?&´?ú?j?Ò?o??f??&´?ú???f?&´
[1] 2999
[2] 3000
[3] 3001
bash: ¶Àéºÿÿþé?: No such file or directory
´: command not found
[1]   Exit 1                  cat ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S < ¶Àéºÿÿþé?
rnet@rnet-desktop:/$ ´?ú???f?: command not found
´?ú?j?Ò?o??f??: command not found
?o??f??&´?ú???f?&´È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S<¶Àéºÿÿþé?&´?ú?j?Ò?
[4] 3006
[5] 3007
[6] 3008
bash: ¶Àéºÿÿþé?: No such file or directory
´?ú???f?: command not found
[2]   Exit 127                ´?ú?j?Ò?o??f??
[3]   Exit 127                ´?ú???f?
´: command not found
[2]   Exit 127                ´?ú?j?Ò?o??f??
[3]   Exit 127                ´?ú???f?
[2]   Exit 127                ´?ú?j?Ò?o??f??
[3]   Exit 127                ´?ú???f?
[4]   Exit 1                  cat ?v?ÿÿÿ6é?f°E?@È??fÿÿþ?é8¤EÇÿÿþ??Mtv?S < ¶Àéºÿÿþé?
[6]+  Exit 127                ´?ú???f?
rnet@rnet-desktop:/$ ´?ú?j?Ò?o??f??: command not found
[2]   Exit 127                ´?ú?j?Ò?o??f??
[3]   Exit 127                ´?ú???f?

[5]+  Exit 127                ´?ú?j?Ò?o??f??


not sure why i would want to keep it?

---

### Post by renkinjutsu on 2010-07-05
Don't paste the name directly into the terminal, use the tab autocomplete to scroll through the filenames until you reach that nasty name.. The linux shells do a very good job with autocomplete.. i can handle filenames in chinese and japanese even though they show up as squares in the terminal.. all thanks to autocomplete

---

### Post by alarme on 2010-07-05
This filename contains special and non-printable characters.
You must escape some of the characters of this filename

The more easy way is:

cd /

BE CAREFUL BEFORE HIT ENTER. Type rm ? and inmediately (no spaces) hit TAB key. Bash autocomplete the filename, escaping automatically the characters needed, displaying some like this:

rm \?v\?ÿÿÿ6é\?f°E\?\@È\?\?fÿÿþ\?é8¤EÇÿÿþ\?\?Mtv\?S\<¶Àéºÿÿþé\?\&´\? 

now, hit ENTER.

---

### Post by macfuel on 2010-07-05
> **renkinjutsu said:**
> Don't paste the name directly into the terminal, use the tab autocomplete to scroll through the filenames until you reach that nasty name.. The linux shells do a very good job with autocomplete.. i can handle filenames in chinese and japanese even though they show up as squares in the terminal.. all thanks to autocomplete

Ok not sure how to do this 
I can tab to scroll and find file name but not able to select or type first letter "box character" so that I can tab autocomplete

---

### Post by teejaybee on 2010-07-05
The contents of the file may let you know if your system has been compromised?

And on the flip side, it could just be some random file that you've accidentally created by pasting stuff from the clipboard in the wrong place or a program has malfunctioned and created it.

Either way, i'd be checking what's in the file for hints as to what made the file.

---

### Post by teejaybee on 2010-07-05
P.S:

rm -i

Is your friend when deleting strange filenames from the root directory :)

---

### Post by macfuel on 2010-07-05
> **alarme said:**
> This filename contains special and non-printable characters.
You must escape some of the characters of this filename

The more easy way is:

cd /

BE CAREFUL BEFORE HIT ENTER. Type rm ? and inmediately (no spaces) hit TAB key. Bash autocomplete the filename, escaping automatically the characters needed, displaying some like this:

rm \?v\?ÿÿÿ6é\?f°E\?\@È\?\?fÿÿþ\?é8¤EÇÿÿþ\?\?Mtv\?S\<¶Àéºÿÿþé\?\&´\? 

now, hit ENTER.
tried this to no avail  tab autocomplete will not work

---

### Post by teejaybee on 2010-07-05
Try rm -i \?v* and only answer yes for the file you wish to delete.

---

### Post by macfuel on 2010-07-05
> **teejaybee said:**
> The contents of the file may let you know if your system has been compromised?

And on the flip side, it could just be some random file that you've accidentally created by pasting stuff from the clipboard in the wrong place or a program has malfunctioned and created it.

Either way, i'd be checking what's in the file for hints as to what made the file.

Yes i agree I tryed to open with cat to no avail
at this point tryed to remove and open with no luck

---

### Post by macfuel on 2010-07-05
> **teejaybee said:**
> Try rm -i \?v* and only answer yes for the file you wish to delete.


this is what i got back

rnet@rnet-desktop:~$ sudo rm -i \?v*
[sudo] password for rnet: 
rm: cannot remove `?v*': No such file or directory

---

### Post by teejaybee on 2010-07-05
Probably a stupid question, but did you change directory to / before you did that?

Otherwise it would be sudo rm -i /\?v*

---

### Post by macfuel on 2010-07-05
> **teejaybee said:**
> Try rm -i \?v* and only answer yes for the file you wish to delete.

rnet@rnet-desktop:~$ sudo rm -i \?v*
[sudo] password for rnet: 
rm: cannot remove `?v*': No such file or directory


no luck

---

### Post by macfuel on 2010-07-05
> **teejaybee said:**
> Probably a stupid question, but did you change directory to / before you did that?

Otherwise it would be sudo rm -i /\?v*
yes in root directory and tried rm -i /\?*

seams like virus or somthing ugly and ideas how to look in it be for i trash it ?

---

### Post by teejaybee on 2010-07-05
Are you in the terminal or have you got X fired up?

If X is working, and you're using the Gnome version of Ubuntu, go to Places on the menu bar, go to your home directory, use the UP arrow graphical icon to navigate back to the root folder, then see if you can right click on that file there and open with gvim or a text editor.

If you have any other unusual activity you've noticed on the PC it might be time to take a closer look at your system to ensure your machine hasn't been compromised. If you suspect it has, copy all the files and documents you need to a CD or USB drive and reinstall with the latest version of Ubuntu, and before you do any web browsing or email reading use the Update Manager to upgrade all the packages to their latest stable versions.

Once again, the file may have been created accidentally or by a program malfunction, but it always pays to do a decent check of your system after events like this, even if only for the practice :)

---

### Post by macfuel on 2010-07-05
that worked used gedit here is content    still can not delete

EÆ¬EÇ&#381;EÇ°E‹°E‰0Èƒ„5&#8364;}ƒ„7&#8364;}ƒè$4‰$DÇ
$DÇÿÿÿO&#339;€ÿÿü&#339;…&&#381;ƒÿÿüÍ„¶Ò„vÿÿýËéÿÿüh…À…ÿþäèÇ$T‰$DÇ$DÇ$D‰ÿÿÿX•ØEÿÿÿX…««óüÿÿÿX&#339;€ÜEÇ ¹À1ØEÇÿÿüÂ…À…`˜¡ÿÿþ7ûƒÿÿþÖé&#382;ÿÿý:…`œ:ÿÿÿO•¶EÆ¬EÇ&#381;EÇ°E‹°E‰0Èƒ„5&#8364;}ƒ„7&#8364;}ƒè$4‰$DÇ
$DÇÿÿÿO&#339;€ÿÿü&#339;…&&#381;ƒÿÿüÍ„¶Ò„vÿÿýËéÿÿüh…À…ÿþäèÇ$T‰$DÇ$DÇ$D‰ÿÿÿX•ØEÿÿÿX…««óüÿÿÿX&#339;€ÜEÇ ¹À1ØEÇÿÿüÂ…À…`˜¡ÿÿþ7ûƒÿÿþÖé&#382;ÿÿý:…`œ:ÿÿÿO•¶EÆ¬EÇ&#381;EÇ°E‹°E‰0Èƒ„5&#8364;}ƒ„7&#8364;}ƒè$4‰$DÇ
$DÇÿÿÿO&#339;€ÿÿü&#339;…&&#381;ƒÿÿüÍ„¶Ò„vÿÿýËéÿÿüh…À…ÿþäèÇ$T‰$DÇ$DÇ$D‰ÿÿÿX•ØEÿÿÿX…««óüÿÿÿX&#339;€ÜEÇ ¹À1ØEÇÿÿüÂ…À…`˜¡ÿÿþ7ûƒÿÿþÖé&#382;ÿÿý:…`œ:ÿÿÿO•¶

---

### Post by teejaybee on 2010-07-05
Hard to say what that would be. Looks like something repeating.

If you feel confident doing so, try from a terminal in X:

gksu nautilus

then find the file and try to delete it that way.

I'd still suggest taking a peek around your system just to make sure nothing untoward has happened.

Good luck.

---

### Post by renkinjutsu on 2010-07-05
```
cd /
ls \  # and press tab to see if it works
```
if it works, then replace 'ls' with 'rm'

---

