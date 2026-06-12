---
title: "Drive F:????"
date: 2008-12-06
forum: Windows
---

### Post by theozzlives on 2008-12-06
I resized one of my partitions to make room for XP Pro SP2. When I installed Windows, it gave my partition the letter F: instead of C:. My DVD writer is drive D: like is should be, any ideas?

---

### Post by smoker on 2008-12-06
you can usually change the drive letter through 'disk management' in 'computer management' via 'admin tools' in the control panel. bear in mind any programmes you installed to F: won't work thereafter if you change the drive to C:

---

### Post by theozzlives on 2008-12-06
Disk Manager won't change the boot drive, but I know what your talking about. I thought I could fill in the missing letters by mounting my ext3 partitions using e2ifs, but it wont mount them cause I have 256 bit clusters instead of 128. Prolly something about me running Ubuntu 64.

---

### Post by scratman on 2008-12-06
Can you use Partition Magic or some other partition software to set the Windows partition as primary?

---

### Post by theozzlives on 2008-12-06
> **scratman said:**
> Can you use Partition Magic or some other partition software to set the Windows partition as primary?

the boot files look for Windows on drive f:

---

### Post by smoker on 2008-12-06
haven't tried this before, but it's from ms, so hopefully should work!
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;Q223188](http://support.microsoft.com/default.aspx?scid=kb;EN-US;Q223188)

---

### Post by theozzlives on 2008-12-06
> **smoker said:**
> haven't tried this before, but it's from ms, so hopefully should work!
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;Q223188](http://support.microsoft.com/default.aspx?scid=kb;EN-US;Q223188)


"Warning Do not use the procedure that is described in this article to change a drive on a computer where the drive letter has not changed. If you do so, you may not be able to start your operating system."

I'm not sure I wanna try that my NTDLR and boot.ini will still point to F:

---

### Post by gpsmikey on 2008-12-06
You may be "up the creek" a ways - that usually happens when the install finds something it assigns to C then puts your stuff in F - the downside of that (from the couple of times I have run into it) is that all your startup links, registry keys etc are now pointing at "F:" and it is a real pain to change it.

mikey

---

### Post by theozzlives on 2008-12-07
> **gpsmikey said:**
> You may be "up the creek" a ways - that usually happens when the install finds something it assigns to C then puts your stuff in F - the downside of that (from the couple of times I have run into it) is that all your startup links, registry keys etc are now pointing at "F:" and it is a real pain to change it.

mikey

I pretty much knew that, I just thought someone might have an idea.

---

