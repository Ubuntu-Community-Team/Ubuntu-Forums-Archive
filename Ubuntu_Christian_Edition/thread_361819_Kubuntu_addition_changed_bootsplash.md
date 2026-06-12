---
title: "Kubuntu addition changed bootsplash ??"
date: 2007-02-14
forum: Ubuntu Christian Edition
---

### Post by glenn69 on 2007-02-14
I have been running CE and decided to add the kde desktop by : sudo aptitude install kubuntu-desktop.

Now, when I boot up the starting screen (I believe it is the bootsplash) displays kubuntu rather than ubuntu Christian Edition.

How do I set it back to the CE splash ?

---

### Post by aysiu on 2007-02-14
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by glenn69 on 2007-02-15
OK, that worked to change bootsplash to standard ubuntu.  What I really want to do is change it back to the Ubuntu Christian Editiion bootsplash.

How would I do that ?

---

### Post by mhancoc7 on 2007-02-16
> **glenn69 said:**
> OK, that worked to change bootsplash to standard ubuntu.  What I really want to do is change it back to the Ubuntu Christian Editiion bootsplash.

How would I do that ?

You could run the upgrade_me script. It should adjust the bootsplash back to the original Ubuntu CE one.

[www.mirror.christianubuntu.com](www.mirror.christianubuntu.com)

Jereme

---

### Post by montgoej on 2007-02-16
If you don't wanna download/install the whole script just download the attached file, open a terminal and navigate to wherever you downloaded it, then type:
```

tar -xvf usplash-theme-ubuntu-ce.so.tar.gz
sudo cp -f "usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-theme-ubuntu-ce.so"
sudo ln -sf "/usr/lib/usplash/usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-artwork.so"
sudo update-initramfs -u

```

~Jordan Montgomery

---

### Post by glenn69 on 2007-02-17
Thanks Jordan,

I ran the following 2 lines of your script :

sudo ln -sf "/usr/lib/usplash/usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-artwork.so"
sudo update-initramfs -u

However, in the spirit of learning linux......what exactly did those 2 lines accomplish.  I can see the first line creates some sort of a link, but why?
Second line...I'm clueless.

Thanks

---

### Post by mysticrider92 on 2007-02-18
> **glenn69 said:**
> Thanks Jordan,

I ran the following 2 lines of your script :

sudo ln -sf "/usr/lib/usplash/usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-artwork.so"
sudo update-initramfs -u

However, in the spirit of learning linux......what exactly did those 2 lines accomplish.  I can see the first line creates some sort of a link, but why?
Second line...I'm clueless.

I am not completely sure about the first one, but I think that it is kind of tricking init to load a different splash screen. The second code tells it to update the initramfs, which is one of the two first files loaded on boot (initrd and vmlinuz). It basically puts all necessary files to boot into RAM, including modules (aka, drivers) and scripts to start various processes and your bootsplash.

---

### Post by montgoej on 2007-02-18
> **glenn69 said:**
> Thanks Jordan,

I ran the following 2 lines of your script :

sudo ln -sf "/usr/lib/usplash/usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-artwork.so"
sudo update-initramfs -u

However, in the spirit of learning linux......what exactly did those 2 lines accomplish.  I can see the first line creates some sort of a link, but why?
Second line...I'm clueless.

Thanks
tar -xvf usplash-theme-ubuntu-ce.so.tar.gz

sudo cp -f "usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-theme-ubuntu-ce.so"

sudo ln -sf "/usr/lib/usplash/usplash-theme-ubuntu-ce.so" "/usr/lib/usplash/usplash-artwork.so"

sudo update-initramfs -u

First line unpacks the .tar.gz archive.  Second line copies the file to /usr.lib.usplash. Third line makes a  link between /usr/lib/usplash/usplash-theme-ubuntu-ce.so and /usr/lib/usplash/usplash-artwork.so. Fourth line updates initram and makes it use the Ubuntu CE splash screen. 

~Jordan Montgomery

---

### Post by Jimmy_r on 2007-02-19
I can add that at least from edgy and forward, it is recommended to use update-alternatives to switch between usplash themes:```
 sudo update-alternatives --config usplash-artwork.so
```
If you have changed the symlinks manually, this might not work unless you do a 
```
sudo ln -sf /etc/alternatives/usplash-artwork.so /usr/lib/usplash/usplash-artwork.so
``` first.

---

### Post by oceanspray on 2007-02-20
> **aysiu said:**
> [http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

Had the same problem, thanks for the link!

---

