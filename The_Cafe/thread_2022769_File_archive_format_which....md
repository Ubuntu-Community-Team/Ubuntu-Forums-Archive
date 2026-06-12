---
title: "File archive format which..."
date: 2012-07-11
forum: The Cafe
---

### Post by pelerin21 on 2012-07-11
Hi,

I am using Peazip on Linux, and Peazip and 7zip both on Windows.

I need an archive file format which has these features:

-File name and encription
-Possible to add new files different than root directory

*7z does not support the second feature which I need: [http://code.google.com/p/peazip/issues/detail?id=59](http://code.google.com/p/peazip/issues/detail?id=59)

*Rar support all of them but rar compressions does not supporting by peazip or 7zip.

*Zip format supports the second feature but does not support the first.

For me, it is not important the level of compression. Does anybody know any archive format which I need?

Thank you!

---

### Post by juancarlospaco on 2012-07-11
make a .zip and then make a .7z of it.
.zip.7z

---

### Post by szymon_g on 2012-07-12
> **pelerin21 said:**
> Hi,
*Rar support all of them but rar compressions does not supporting by peazip or 7zip.


rar is well supported by 7 zip (at least at windows).

---

### Post by pelerin21 on 2012-07-12
> **szymon_g said:**
> rar is well supported by 7 zip (at least at windows).

Not with open source applications :/

---

### Post by Primefalcon on 2012-07-12
> **pelerin21 said:**
> Not with open source applications :/
```
sudo apt-get install rar
```
bang the fileroller will now understand rar files..... easy

by 7z is about the best format out there, I've done a lost of tests at max compression

gzip
zip
rar
7z

amongst tons of others and gzip and 7z usually come out on top with 7z having the edge in a lot of cases... I've usualy found both zip and rar to be pretty bad as compression goes....

you'll want to make sure that you read the man pages on 7z and gzip though to do maximum compression....

btw do your encryption separate after you've already zipped the file, I'd recommend gpg

---

### Post by pelerin21 on 2012-07-13
> **Primefalcon said:**
> ```
sudo apt-get install rar
```
bang the fileroller will now understand rar files..... easy


We were talked also for other OSes (especially for windows support with open source applications)

> **Primefalcon said:**
> ```
sudo apt-get install rar
```

by 7z is about the best format out there, I've done a lost of tests at max compression



They all say that 7z is one of the best but I could not understand yet why it does not support one of the simplest features which I write on my first message - second feature

> **Primefalcon said:**
> ```
sudo apt-get install rar
```

you'll want to make sure that you read the man pages on 7z and gzip though to do maximum compression....


I don't need compression too much for this situation (for now)

> **Primefalcon said:**
> ```
sudo apt-get install rar
```
btw do your encryption separate after you've already zipped the file, I'd recommend gpg

Ok I know gpg and other soluitons, but I really need an archive format because I am using this archive files on many different computers... So I need 7zip, Peazip or another archive tool which is isnatlled on many other computers...

---

### Post by Primefalcon on 2012-07-13
you know you can ue gpg on windows or mac as well? 

mac: [https://www.gpgtools.org/installer/index.html](https://www.gpgtools.org/installer/index.html) (havn't used but heard it's good)

windows can be handled with putty.... or if you want a gui gpg4win (used both with 0 issues)

really as are as encryption goes, you want proper open source encryption... whether you like open source or not... most security experts will tell you thats on thing you do want open source

---

### Post by pelerin21 on 2012-07-15
> **Primefalcon said:**
> you know you can ue gpg on windows or mac as well? 

mac: [https://www.gpgtools.org/installer/index.html](https://www.gpgtools.org/installer/index.html) (havn't used but heard it's good)

windows can be handled with putty.... or if you want a gui gpg4win (used both with 0 issues)

really as are as encryption goes, you want proper open source encryption... whether you like open source or not... most security experts will tell you thats on thing you do want open source

I always use my archived files to another computer. So I need an archive manager, because it is difficult to find gpg application or something. That's why I prefer archive formats.

But I still can not believe that 7z does not support that feature I want... :confused:

---

