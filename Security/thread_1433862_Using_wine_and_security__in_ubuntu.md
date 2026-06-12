---
title: "Using wine and security  in ubuntu"
date: 2010-03-19
forum: Security
---

### Post by shaun67 on 2010-03-19
Hi i have installed ubuntu as my os and have just installed wine ..is there a way to make wine more secure in ubuntu ..can anything in wine get into ubuntu ??:D

---

### Post by cdenley on 2010-03-19
> **shaun67 said:**
> Hi i have installed ubuntu as my os and have just installed wine ..is there a way to make wine more secure in ubuntu ..can anything in wine get into ubuntu ??:D

By default, applications run with wine have access to your entire filesystem as the user it is running as. I would suggest you change this using the "Drives" tab you can access with the "winecfg" command. The less wine can access, the better.

---

### Post by shaun67 on 2010-03-19
> **cdenley said:**
> By default, applications run with wine have access to your entire filesystem as the user it is running as. I would suggest you change this using the "Drives" tab you can access with the "winecfg" command. The less wine can access, the better.

Hi thanks how do i go about doing this as i am new to using ubuntu ..any how to's ? thanks

---

### Post by anoop999 on 2010-03-19
Use the command **winecfg**

This will bring up a Wine configuration dialog box from which you can choose which directories Wine is allowed to see (see screenshot).

---

### Post by shaun67 on 2010-03-19
> **anoop999 said:**
> Use the command **winecfg**

This will bring up a Wine configuration dialog box from which you can choose which directories Wine is allowed to see (see screenshot).

Hi sorry to be a pain ..i used the command line and it comes up ,my drives just say c and z which do i need to deny access ..sorry for sounding dumb  but if i don't ask then i don't know. p.s what do i do do i remove that drive or what lol if you could just let me know please ..much appreciated.

Thanks again:D

---

### Post by shaun67 on 2010-03-20
Can someone please tell me how i deny wine access to my full system  ..the drives that come up are c and z drives  ..which drive do i deny and how to .

Thanks

---

### Post by shaun67 on 2010-03-20
> **anoop999 said:**
> Use the command **winecfg**

This will bring up a Wine configuration dialog box from which you can choose which directories Wine is allowed to see (see screenshot).


what do i need to do once i get this dialog box up ?  surly someone can put me out of my misery :o

---

### Post by cdenley on 2010-03-20
Each drive letter is mapped to a directory in the filesystem. If a directory is mapped to a drive letter, then wine can access it. I'm guessing the Z drive is mapped to the root filesystem (/). Is that correct? If so, wine can access the root (or entire) filesystem. Create a directory where wine applications can read/write files, such as a directory called "wine" in your home directory. Then change the mapping for the "Z" drive so it is mapped to the "wine" directory you just created. Now wine can no longer access your root filesystem. Simple.

---

### Post by shaun67 on 2010-03-21
> **cdenley said:**
> Each drive letter is mapped to a directory in the filesystem. If a directory is mapped to a drive letter, then wine can access it. I'm guessing the Z drive is mapped to the root filesystem (/). Is that correct? If so, wine can access the root (or entire) filesystem. Create a directory where wine applications can read/write files, such as a directory called "wine" in your home directory. Then change the mapping for the "Z" drive so it is mapped to the "wine" directory you just created. Now wine can no longer access your root filesystem. Simple.


Hi thanks for the info..could anyone tell me that this is right what i have done (i'm a nebie to ubuntu and still trying to find my way around). I opened up  configure wine which brings up the wine configuration window ..i then clicked on drives..There it showed me C drive and z drive.

I then clicked on add and then typed in the box wine and then clicked apply ..this then showed me drive D with the title wine on that drive.I then clicked on drive z and typed in wine and clicked apply so now it says under drives -

C: ../drive_ c
D:  /wine
Z:  /wine    

Is this  now correct.

Thanks

---

### Post by cdenley on 2010-03-21
That works wine, assuming /wine is a directory you can read and write to. Personally, I would've created it in my home directory, as I suggested. A little redundant to have two drives mapped to the same directory, but whatever.

---

