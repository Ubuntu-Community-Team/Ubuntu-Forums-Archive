---
title: "Not enough disk space in wine folder"
date: 2009-07-29
forum: Wine
---

### Post by M03BIUS on 2009-07-29
Hi, my home directory and my wine folder reside on my root partition(this probably shouldn't be this way...) but anyway... how do I point the wine folder to install programs onto my 63GB ext3 file partition instead of my root directory? This is how it's setup

10GB root
4GB swap
63GB ext3

I manually formated my Ubuntu because I am in a triple boot environment and I think I formated Ubuntu wrong... I am not sure... but how do I make it to where all my files go to my 63GB instead of defaulting to the /root all the time. Do I have to reformat?  

Thank you for your help and for reading my noob post.

---

### Post by NoReflex on 2009-07-29
Hello!

You can go to Start Menu -> Wine -> Configure Wine -> Drives.
Here you can add drives to Wine - for example map D: to a folder on the 63 GB partition.

Best wishes,
NoReflex

---

### Post by M03BIUS on 2009-07-29
I got it to work, thanks.

---

### Post by Keith Fox on 2010-01-10
I also have this problem saying I don't have enough space. I have plenty of space though. I went to configure Wine and auto detect drives... still didn't work. check the screenshot.

---

