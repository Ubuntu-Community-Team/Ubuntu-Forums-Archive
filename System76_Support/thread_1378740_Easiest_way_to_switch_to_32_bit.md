---
title: "Easiest way to switch to 32 bit?"
date: 2010-01-11
forum: System76 Support
---

### Post by Ian9056 on 2010-01-11
I have a Pangolin running 64-bit Intrepid that I would like to install 32-bit Karmic on. I realize that this will take a fresh install, but I'm trying to make this as painless as possible, in the sense that I'd like to have basically all of the same packages as I currently do in 32 bit form, all the sam config files, etc.

Additionally, I'm really only vaguely familiar with partitions, but do know that System76 set up a separate home partition; how relevant is that when I'm doing a fresh install?

In case anyone's wondering why I'd do this, I've just had too much trouble with Java applets in 64 bit.

---

### Post by betrunkenaffe on 2010-01-12
When you install the 32 bit one, all the packages should still be available from the repository that you had access to before. Only format / and don't touch /home and most of your personal settings should be saved.

I don't know if there would be any conflict however if you did, you'd obviously have to overwrite your /home as well.

What problems? I haven't had a single issue with java and have been using 64 bit for a year now.

---

### Post by marshmallow1304 on 2010-01-12
The only thing I could think of would be if you had the 64-bit alpha Flash in ~/.mozilla/plugins you would need to delete it and install the 32-bit version.

---

### Post by underquark on 2010-01-12
Why do you want to put 32-bit on?  Is there something specific that stops you using 64-bit or that won't work with 64-bit?

---

### Post by thomasaaron on 2010-01-12
> **Ian9056 said:**
> Additionally, I'm really only vaguely familiar with partitions, but do know that System76 set up a separate home partition; how relevant is that when I'm doing a fresh install?


A separate home partition isn't necessary, but it will make re-installs easier should you have to perform one.

---

### Post by Ian9056 on 2010-01-12
> **betrunkenaffe said:**
> 
What problems? I haven't had a single issue with java and have been using 64 bit for a year now.

I've had a lot of issues with Processing, kind of an extension of Java (not sure if they bill themselves as a framework/environment/etc, it's extra libraries for visualization). 

Processing itself works fine for a little while, but if you run an applet 3 or 4 times sometimes the screen scrambles in the computer totally locks up. This happens almost immediately if you view a sketch on [www.openprocessing.org](www.openprocessing.org) and scroll down to view the source code. This is all on Sun's 64 bit Java version; I didn't have any luck at all with icedtea.

I'm going to upgrade to 64-bit Karmic today and mess around a bit, but I think I'll try to make the switch to 32 if I can't get it sorted out.

---

### Post by miniyak on 2010-01-12
ive found 32bit to be noticeably more slow on my panp5
though it should be noted that I was using a slower 5500rpm drive when I was testing it out.

I will also add that the most painless way to test out something new is to have second 2.5 sata drive to do the testing. Also if you get and enclosure for ether your old or the new drive its possible to boot ubuntu that was installed internally, externally over usb. (easy as hooking up the drive) The speed suffers but not as much as one would think. I have still yet to test eSata but hopefully Ill get the cable in the mail soon.

You can install externally but...**_MAKE SURE_** you write grub to the external disk... by default ubiquity is stupid and will write to the local disc **even** if your installing **externally**. Writing over the grub your using for the sake of an external drive isn't fun... trust me

---

