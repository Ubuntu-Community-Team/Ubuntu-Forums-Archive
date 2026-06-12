---
title: "Utility to log Ubuntu/Windows usage"
date: 2010-10-07
forum: The Cafe
---

### Post by Nickedynick on 2010-10-07
I've had a brief search, and as far as I know there isn't something for this, but I thought I'd ask you lot here just in case.

Basically, I'd like to know how often I select Ubuntu/Windows to log in to from my GRUB menu. I'm not really bothered how the data is represented, but I thought it'd be interesting to find out just how much I use Windows nowadays. Presumably it's fairly easy to implement, and I'm sure I could write something to do it myself, but I thought I'd see if others have seen anything like this first.

---

### Post by rhcm123 on 2010-10-07
Not exactly a techincal fix, but a post-it and a pen would work :)

In all seriousness though, there probably isn't a solution. GRUB resides in a very small section of your HDD called the MBR (master boot record), and I don't think it has the capability to write to one of your partitions.

---

### Post by lisati on 2010-10-07
I'd envisage a small script or program that gets called from each of the OSes and that writes a log entry to a place that's accessible from your reporting system. It would be something that the each OS takes care of rather than from within grub. 

Link and/or volunteer to write the program needed..... :D

---

### Post by rhcm123 on 2010-10-07
> **lisati said:**
> I'd envisage a small script or program that gets called from each of the OSes and that writes a log entry to a place that's accessible from your reporting system. It would be something that the each OS takes care of rather than from within grub. 

Link and/or volunteer to write the program needed..... :D

For linux, you could add these lines to /etc/rc.local, a script that runs once per boot, I use it in my server to mount my floppy disk (that for some reason doesnt mount on boot?)

```

echo Ubuntu Loaded at: >> /public/directory/here
date >> /public/directory/here

```

that would insert the time ubuntu booted to whatever file you want

---

### Post by Nickedynick on 2010-10-09
Right, after brushing up on my C++ I did it myself! Not a fantastic implementation, but I've got a program running on each at startup which saves the OS and a timestamp to a .csv file in my Dropbox.

If anyone wants to have a look / try what I've done then I'm more than happy to share :)

---

### Post by rhcm123 on 2010-10-11
impressive, i would have just gone with the post-its :)

do you have a program to count them as well?

---

### Post by Nickedynick on 2010-10-12
Yeah, but I'm far too good at losing post-its :D

It's being output as a .csv file, so atm I'm using Excel/Calc, a column of if statements and a couple of summations to work it out.

---

### Post by Ctrl-Alt-F1 on 2010-10-12
> **Nickedynick said:**
> Yeah, but I'm far too good at losing post-its :D

It's being output as a .csv file, so atm I'm using Excel/Calc, a column of if statements and a couple of summations to work it out.
Very smooth.  I wouldn't have even thought to use a speadsheet!

---

### Post by Nickedynick on 2010-10-12
Thanks! :) It's a slightly convoluted setup (I'm sure there's a simpler way), but it seems to work. I just knocked up an import function into a separate .ods file, so I don't need to touch the data file any more. At the moment it's Ubuntu 11 - 4 Windows :P

---

