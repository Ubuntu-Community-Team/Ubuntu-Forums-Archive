---
title: "MD5 chechsum for files"
date: 2011-08-25
forum: Security
---

### Post by vagelism on 2011-08-25
Hello to all.
I am new to Ubuntu and I need to know how is possible to calculate a file's MD5 checksum. Is there also any gui interface?
Thank you!

---

### Post by dave01945 on 2011-08-25
in a terminal you can just type 

```
md5sum filename
```

if you have a text file with the correct md5sum in it you can use

```
md5sum -c filename.txt
```

also there is a nautilus script that will let you run it by right clicking here

[http://gnome-look.org/content/show.php/Hash+Checker+4.0.2?content=129309](http://gnome-look.org/content/show.php/Hash+Checker+4.0.2?content=129309)

hope that helps

---

### Post by soldersplash on 2011-08-25
Hi Vagelism,
Open up a terminal
    *Application > Accessories > Terminal*
in vanilla Ubuntu 10.04 LTS.

(Not sure were to find Terminal in later Unity type Ubuntu...)
Type md5sum followed by the /path/to/the/file/filename and hit enter..

So, for a file called minicom.log in my home directory:-

```
me@my-laptop:~$ md5sum minicom.log
d424730498927479d041382a4ec0c711  minicom.log
```

The longish alphanumeric string is the md5sum returned.

Hope that helps.

More info on using md5sum is available by typing ```
man md5sum
``` at the terminal command prompt. Or ```
md5sum --help
```

Not sure about a GUI front end.... Would need to dig...

All the best,
Daniel.

---

### Post by soldersplash on 2011-08-25
I must learn to type faster....

---

### Post by lovinglinux on 2011-08-25
I develop an add-on for Firefox that generate checksums and can do comparisons. See [https://addons.mozilla.org/en-US/firefox/addon/checkit/](https://addons.mozilla.org/en-US/firefox/addon/checkit/)

---

### Post by vagelism on 2011-08-25
Thanks to all for the advices!!

---

### Post by Sef on 2011-08-26
When doing an md5sum be sure and change to the directory where the file is stored. If you downloaded a file to the Downloads folder, do this in the terminal first:

```
cd ~/Downloads
```

Then do the md5sum

---

