---
title: "Printeranywhere for Linux"
date: 2007-08-08
forum: The Cafe
---

### Post by salefish on 2007-08-08
I would like to know if anyone has successfully gotten the program Printeranywhere to work on Ubuntu?
I gave Wine a shot , unsuccessfully, though my fault since I don't know what I'm doing. 
I am new to Ubuntu and Linux in general. I have installed it on my laptop and find it very easy to use, easier than Windows. Though I have been using the program Printeranywhere to print from my laptop on my home desktop. This program is absolutely essential to the productivity of my laptop.
If anyone has made it work or can give me a tutorial on how to make it work I would be very appreciative. 
BarrynTheresa at gmail

---

### Post by salefish on 2007-08-13
Well, I know some other people would like to use this program also. If you read this and would also like to be able to use the program Printeranywhere please post here, so I don't feel like a lone dog. 
I also would appreciate any comments at all, even if you just have an idea of where to start.

---

### Post by HermanAB on 2007-08-13
Well, you probably don't want that.

The combination of Samba and CUPS make any printer look like a networked postscript printer.  So if your printer is hooked to your Linux machine, then you can print from any Windows machine without installing a special driver.  Any postscript driver will work.  

I always use an Apple Laserwriter II driver in Windows, since it starts with 'a' which puts it at the top of the list and all versions of Windows has it.

'Hope that helps!

Herman

---

### Post by bwtranch on 2007-08-13
I have personally never heard of it. I'm off to googleit.

---

### Post by bwtranch on 2007-08-13
Looks a little too microsloppy to me :)

---

### Post by DoctorMO on 2007-08-13
Linux already contains all the tools needed to set this sort of thing up; if you want to use it over a local network you can use cups (I wouldn't use smb print sharing) cups comes with networking.

If you want to be able to send things to your home computer from your laptop via the internet then there are multiple ways to properly tie up your laptop to the internal network; and there are some nice tools in cups for putting in a one way printing queue to go over the internet.

The sort of it is: you don't need a new tool, the tools already exist; you just have to learn how to use them.

---

### Post by forrestcupp on 2007-08-13
But I think with Printer Anywhere you can print on any printer of any computer hooked up to the internet as long as they have the software installed.  You can't do that with CUPS and Samba.

---

### Post by salefish on 2007-08-14
First, thank y'all very much for the replies. 
Second, your absolutely correct, printeranywhere allows you to print from any computer with the software installed. I have 4 laptops, don't ask, and they all have the software and print on one desktop. I am going to attempt to set up the same thing using CUPS, hopefully I'm up to the task.
I will report back with the progress or lack of, wither way.

---

### Post by salefish on 2007-08-22
I have been researching cups, and like all things Linux there is very little literature. What is available is long winded and says very little of value.
From what i can tell it will do internet printing, but cup has to be installed on both units. Since I have a job, and am not an IT professional Linux is only a hobby and it takes me quit a while to get through all the literature it takes to implement  something.
  I will be back in another day or two with a progress  report.

---

