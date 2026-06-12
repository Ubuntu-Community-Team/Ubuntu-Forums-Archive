---
title: "Pocket Linux, Anybody???"
date: 2006-04-04
forum: The Cafe
---

### Post by jason.b.c on 2006-04-04
I downloaded a cool little floppy disk sized linux distro called **Pocket Linux** just to see whats it's like. Now on there website they recommend that you use something  like *Rawrite* to copy the image file to a 1.44mb floppy disk, the only thing is i can't figure out why when i type in the name of the image in rawrite it fails to work.

Now i've used rawrite before successfully, and i know _how_ to use it, I just don't understand why it won't work on this particular image file.

Here is the name of the image->       **image-2.51-fix-4.bin** 

Thats exactly how it looks.!   So as far as i understand thats how your supposed to type it in rawrite.:mad: 

I've tried **Rawrite.exe** and **Rawrite2.exe** neither one works.?:confused: 

Could someone please help me understand what i'm doing wrong.?:( 

     image-2.51-fix-4.bin is the latest version as far as i can tell.

---

### Post by John.Michael.Kane on 2006-04-04
**Removed Since It Was Not Needed!!!!!!!**

---

### Post by LKRaider on 2006-04-04
Try doing it from Linux using dd, like this:

```
dd if=<image file> of=/dev/fd0
```

---

### Post by jason.b.c on 2006-04-04
[QUOTE=LKRaider]Try doing it from Linux using dd, like this:

```
dd if=<image file> of=/dev/fd0
```[/QUOTE]


Oh i'm sorry, i'm not in Ubuntu right now.

I need to know how can i from windows.???

---

### Post by jason.b.c on 2006-04-11
:D  Well thats cool, I got it to work, It's really kinda useless though but i just wanted something else to mess around with.:) 

But now i've downloaded another one called **Minix 3 os** another linux distro. I burn't it successfully to a *CD-RW* and it boots up into the options screen if i leave the disk in my cd drive but i don't understand how to get it to startup.:confused:   It asks how i want to *login* so i type **Root** and press *enter* then i'm asked for a login name, i type my name, *enter*, then i'm asked for password but i can't type anything it wont let me.](*,) :mad: 

Any idea's????:confused: 

  :cool:  Here's where i found it:>            [www.minix3.org](www.minix3.org)

---

### Post by erikpiper on 2006-04-11
jason.b.c- this little bit of trivia might help you- in a linux terminal when a password is being entered, nothing will show up. Than way, nobody can see how long it is. Yes it being entered.

---

### Post by jason.b.c on 2006-04-11
[QUOTE=erikpiper]jason.b.c- this little bit of trivia might help you- in a linux terminal when a password is being entered, nothing will show up. Than way, nobody can see how long it is. Yes it being entered.[/QUOTE]


Oh Yea, hhhmmm, Well then why is it then after i type in the password and press *enter* nothing happens??  I mean the same words just pop up again and i have to start all over again.!:mad:       Why is that??         Please explain.:)

---

### Post by jason.b.c on 2006-04-12
*Bump*:(

---

### Post by briancurtin on 2006-04-12
[QUOTE=jason.b.c]Oh Yea, hhhmmm, Well then why is it then after i type in the password and press *enter* nothing happens??  I mean the same words just pop up again and i have to start all over again.!:mad:       Why is that??         Please explain.:)[/QUOTE]
caps lock?
num lock?
correct password?
etc...

---

### Post by jason.b.c on 2006-04-12
[QUOTE=briancurtin]caps lock?
num lock?
correct password?
etc...[/QUOTE]


> jason.b.c- this little bit of trivia might help you- in a linux terminal when a password is being entered, nothing will show up. Than way, nobody can see how long it is. Yes it being entered.



:mad:   Well crap, I give up then on this.    No matter what i try nothing seems to work.!:( :mad: 

Maybe it's busted.:confused:

---

### Post by 3rdalbum on 2006-04-13
Actually, Minix is Unix; not Linux. (Minix has been around longer than Linux... it was reportedly the reason why Linus started writing a kernel!)

---

