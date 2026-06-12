---
title: "There is no application installed for executable files"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bobman321123 on 2012-04-15
When I try to run an executable, it gives me the error...
```
Could not display"/home/josh/Applications/Sublime2/sublime_text".
There is not application installed for executable files.
Do you want to search for an application to open this file?
```

What's wrong with my computer? D:

---

### Post by dino99 on 2012-04-15
sublime_text should be sublime.txt to allow nautilus or gedit to open it

(by the way an "executable" is either .exe or .bin, but not txt) :lolflag:

---

### Post by bobman321123 on 2012-04-15
Sublime Text 2 (program): A program that works on Mac, Windows or Linux. (and has precompiled binary executables on all three) A text editor on steroids, capable of editing html, css, c++, php, cobalt, java, and many other languages.

---

### Post by dino99 on 2012-04-15
[http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html](http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html)

---

### Post by Mr. Picklesworth on 2012-04-15
You need to right click the file, go to Permissions, and check "Allow executing file as program." Now you can double click the file and it will open. Normally these things are stored in archives (with the executable bit set) or packages, so that's why you probably haven't bumped into this before.

Right now Nautilus uses the same dialog it uses for everything else when it can't run executable files, which is rather unhelpful. (Friction against making it helpful seems to be based on a deluded belief that it's better for security if we confuse people into doing something else).

Bug report on the issue, though I'm sure there's a much older one somewhere: [https://bugzilla.gnome.org/show_bug.cgi?id=604639](https://bugzilla.gnome.org/show_bug.cgi?id=604639)

---

### Post by mc4man on 2012-04-15
The history of the OP's issues with executables in his home dir. seems to be just going around in circles.
Maybe he should ck. whether he has messed that up in whole or in part

---

### Post by dcstar on 2012-04-16
> **bobman321123 said:**
> Sublime Text 2 (program): A program that works on Mac, Windows or Linux. (and has precompiled binary executables on all three) A text editor on steroids, capable of editing html, css, c++, php, cobalt, java, and many other languages.

And of course if you have a 64-bit system you **also** have the 64-bit version of this program, otherwise you are just wasting your time?

---

### Post by bobman321123 on 2012-04-16
> **dcstar said:**
> And of course if you have a 64-bit system you **also** have the 64-bit version of this program, otherwise you are just wasting your time?

Ok, to avoid old threads complicating this, let's get this straight.
1. I have 64bit linux and 64bit program.
2. It is indeed a program, and not a text file. 
3. This problem happens with both this program, and programs I try to compile myself.

---

### Post by thatguruguy on 2012-04-16
I just went [here]("http://www.sublimetext.com/2") and downloaded the program, and it runs without issue. As such, I'm having a hard time re-creating your problem.

Walk us step-by-step though what you've done to try to install, set up, and run the program.

---

### Post by bobman321123 on 2012-04-16
Ok, I downloaded a fresh copy just to test it out. 
Unpacked the .tar.gz
Double clicked the executable "sublime_text".
```
Could not display "/home/josh/Applications/Sublime Text 2/sublimt_text". There is no application installed for executable files. Do you want to search for an application to open this file?
```
*clicks no*
I go in properties and make sure it's able to be executed.
Double clicked
```
Could not display "/home/josh/Applications/Sublime Text 2/sublimt_text". There is no application installed for executable files. Do you want to search for an application to open this file?
```

---

### Post by oldos2er on 2012-04-16
Why not run it from the CLI? ```
cd "/home/josh/Applications/Sublime Text 2/"

./sublime_text
```

---

### Post by bobman321123 on 2012-04-18
When I try that, it tells me I don't have permission to run that file.
And when I use sudo, it just does nothing.

---

### Post by mc4man on 2012-04-18
go to system settings > users & create a new standard user. see if that user can run sublime text, ect.

---

### Post by bobman321123 on 2012-04-18
As a fresh new, just created user, (installed nothing, didn't so much as change the wallpaper), I got the same error message about no installed programs for executables.

---

### Post by cariboo on 2012-04-18
Could you open a terminal and run the following commands, and paste the output in your next post. cd into the directory where sublime_text is located and type the following command:

```
ls -l
```

and in the same directory:

```
./sublime_text
```

---

### Post by bobman321123 on 2012-04-18
```
josh@Nero:/mnt/data/Applications/Sublime Text 2$ ls -l
total 8388
drwxr-xr-x 7 josh josh    4096 Feb 21 18:59 Icon
drwxr-xr-x 2 josh josh    4096 Feb 21 18:59 lib
-rw-r--r-- 1 josh josh    4205 Feb 21 18:59 PackageSetup.py
drwxr-xr-x 2 josh josh    4096 Feb 21 18:59 Pristine Packages
-rw-r--r-- 1 josh josh   10560 Feb 21 18:59 sublime_plugin.py
-rwxr-xr-x 1 josh josh 8553432 Feb 21 18:59 sublime_text
josh@Nero:/mnt/data/Applications/Sublime Text 2$ ./sublime_text
bash: ./sublime_text: Permission denied
josh@Nero:/mnt/data/Applications/Sublime Text 2$ sudo ./sublime_text
[sudo] password for josh: 
josh@Nero:/mnt/data/Applications/Sublime Text 2$ 
```

---

### Post by Longinus00 on 2012-04-18
Is /mnt/data mounted noexec?

---

### Post by oldos2er on 2012-04-18
What file system is /mnt/data/ using?

---

### Post by bobman321123 on 2012-04-18
ext4, I believe...
Let me check something, and I'll get back to you.

---

### Post by bobman321123 on 2012-04-18
When I put the program in my home folder, it runs.
Why would a mounted drive stop me from executing?

---

### Post by oldos2er on 2012-04-18
Do you mount /mnt/data with fstab, or manually? If fstab, can you post its contents? ```
cat /etc/fstab
```

---

### Post by bobman321123 on 2012-04-18
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=240553a1-a638-4c00-b4d4-01ee9b235d9a   /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=e7cbcac5-9e26-4654-ae6f-6f7b228d6466 none swap sw 0 0
/dev/mapper/cryptswap1                      none         swap  sw                   0  0  
/dev/mapper/cryptswap2                      none         swap  sw                   0  0  
/dev/mapper/cryptswap3                      none         swap  sw                   0  0  
UUID=2f90e771-b0b5-463e-a864-f5cc45511b97 /mnt/data ext4 auto,users,rw,relatime 0 2

```

---

### Post by oldos2er on 2012-04-18
I wonder if you change the last line > UUID=2f90e771-b0b5-463e-a864-f5cc45511b97 /mnt/data ext4 auto,users,rw,relatime 0 2 to > UUID=2f90e771-b0b5-463e-a864-f5cc45511b97 /mnt/data ext4 defaults 0 2 if it would work. If you try this, please make a backup copy of fstab first.

---

### Post by bobman321123 on 2012-04-18
Thank you so much!
I think that did it :D

---

### Post by oldos2er on 2012-04-18
Well, that was a shot in the dark. Yay!  :)

---

