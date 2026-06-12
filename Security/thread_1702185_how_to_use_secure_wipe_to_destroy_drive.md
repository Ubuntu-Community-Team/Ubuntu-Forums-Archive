---
title: "how to use secure wipe to destroy drive"
date: 2011-03-07
forum: Security
---

### Post by asdfghjkl67 on 2011-03-07
Hi 

I need someone to tell me the command in secure wipe needed to kill all data 

dban will not boot up for me

---

### Post by Soul-Sing on 2011-03-07
> **asdfghjkl67 said:**
> Hi 

I need someone to tell me the command in secure wipe needed to kill all data 

dban will not boot up for me

Encrypt all data.

---

### Post by Kirboosy on 2011-03-07
[COLOR=Red][SIZE=4]THIS WILL WIPE EVERYTHING OFF THE DRIVE! MAKE SURE YOU WANT TO DO THIS BEFORE YOU RUN THE COMMAND[/SIZE][/COLOR]

Pop in a liveCD of Ubuntu and run the command in terminal. (Note * You may have to adjust the /dev/sda to fit your hard drive That way you don't wipe out the wrong drive.)

```
dd if=/dev/random of=/dev/sda
```

Hope that helps.

~Caboose

---

### Post by rookcifer on 2011-03-07
> **Caboose885 said:**
> [COLOR=Red][SIZE=4]THIS WILL WIPE EVERYTHING OFF THE DRIVE! MAKE SURE YOU WANT TO DO THIS BEFORE YOU RUN THE COMMAND[/SIZE][/COLOR]

Pop in a liveCD of Ubuntu and run the command in terminal. (Note * You may have to adjust the /dev/sda to fit your hard drive That way you don't wipe out the wrong drive.)

```
dd if=/dev/**random** of=/dev/sda
```

~Caboose

If he does that he will be waiting until the sun burns out.  Better is to do:

```
dd if=/dev/zero of=/dev/sda
```

Much faster and just as effective.

---

### Post by Kirboosy on 2011-03-07
True. Forgot about the zero folder. Use the zero method instead.

---

### Post by tubbygweilo on 2011-03-07
> **asdfghjkl67 said:**
> Hi 

I need someone to tell me the command in secure wipe needed to kill all data 

dban will not boot up for me

May I suggest that if DBAN does not boot then you may have a bad disk so is it possible to burn another via the DBAN [site]("http://www.dban.org/download")? 

**Deleting / erasing / wiping a disk may take some time!**

---

### Post by Sef on 2011-03-07
Quote:
Originally Posted by asdfghjkl67  
Hi 

I need someone to tell me the command in secure wipe needed to kill all data 

dban will not boot up for me
May I suggest that if DBAN does not boot then you may have a bad disk so is it possible to burn another via the DBAN site? 

Deleting / erasing / wiping a disk may take some time!> 

+1. Sometimes the cd disk itself is the problem and not the hardware.(Sometimes a few of them may be bad

---

### Post by dirty_harry on 2011-03-08
best way to kill data on a drive

[http://www.youtube.com/watch?v=Tcfgy6sEkzQ#t=54m01s](http://www.youtube.com/watch?v=Tcfgy6sEkzQ#t=54m01s)

---

