---
title: "Cryptkeeper has completely disappeared from Ubuntu 17.04"
date: 2017-06-14
forum: Security
---

### Post by ktc2 on 2017-06-14
I had cryptkeeper (file encryption program) installed up through Ubuntu 16.10. It worked fine. After upgrade to 17.04, it has completely disappeared. Can't find it through file search, or open through terminal. Luckily, I only lost a test file. 

Does anyone know how to bring it back, and make it work reliably again? I'd hate to get it back, use it for files that are actually important, then lose it again. 

Or, does anyone know of another file encryption program, as easy to install and use as cryptkeeper, that will work reliably on 17.04 and above? 

Many thanks, 

KTC

---

### Post by kurt18947 on 2017-06-14
There are security issues and it appears to be unmaintained so they're not getting fixed. Here's one article:

[https://bestsecuritysearch.com/bad-bug-discovered-cryptkeeper/](https://bestsecuritysearch.com/bad-bug-discovered-cryptkeeper/)

I used cryptkeeper because it was the only GUI app I've been able to find where I could encrypt a folder. I oftentimes don't want to encrypt my entire /home or entire disk. I've researched 7zip as an alternative and while it's far from perfect, one benefit is that 7zip is cross platform and as long as one encrypts the file names as well as the file contents and use a strong password, 7zip seems reasonably secure from what I've been able to determine.

---

### Post by ian-weisser on 2017-06-14
The reason why it was dropped from Debian (and Ubuntu): [https://bugs.debian.org/853725](https://bugs.debian.org/853725)

---

### Post by gordintoronto on 2017-06-15
I have access to a Cryptkeeper archive using SiriKali. Xubuntu 17.04

---

### Post by erinspice on 2017-11-06
Did you ever find the answer to this problem? After upgrading to 17.04, I no longer have access to the files I encrypted with cryptkeeper. How do I get my files back?

---

### Post by 1clue on 2017-11-06
> **erinspice said:**
> Did you ever find the answer to this problem? After upgrading to 17.04, I no longer have access to the files I encrypted with cryptkeeper. How do I get my files back?

I know nothing about cryptkeeper, but you would need access to:
[LIST=1]
[*]The encryption key(s) used by cryptkeeper
[*]The passwords for the keys.
[*]The encryption algorithms used.
[/LIST]

Cryptkeeper was nothing but a gui on an API which is almost certainly still supported by command-line tools. You will need to learn the command-line kung-fu to get your files back.

---

### Post by erinspice on 2017-11-06
I know exactly what cryptkeeper is. That's why I'm here. I don't "need to learn command-line kung-fu." I'm a software engineer and have been using Linux exclusively since 2000. I know my keys & passwords. I need info on how to find the data and decrypt it.

Maybe I'll just see if I can build cryptkeeper from source. Or at least read the source to get the answers to my questions.

---

### Post by 1clue on 2017-11-06
Sorry for the wrong assumptions. The typical Ubuntu user often seems somewhat akin to the typcial Mac user and often they don't know what a terminal is.

[https://ubuntuforums.org/showthread.php?t=1692173](https://ubuntuforums.org/showthread.php?t=1692173)

---

### Post by ian-weisser on 2017-11-06
One fairly easy answer is to spin up a 16.04 VM to recover the files, since cryptkeeper was dropped later.

---

### Post by privacydude on 2017-11-06
The bug report says "if used with current encfs". I don't have 16.04 or 16.10 to see what version that is exactly but my Raspberry Pi 3B running Beta6C (Ubuntu 18.04) of Privacy Enhanced Linux 64-bit is using version 1.9.2-2 and the laptop I'm writing this on (Ubuntu 17.04) is using encfs 1.9.1-4 so it has definitely been updated. I think the reason the front-end (cryptkeeper) isn't included any more is simply because it no longer compiles. Download the source and try it yourself.. maybe you'll have better luck than I did. Don't know if it's a fundamental change in the language, library backwards compatibility problem or what (sloppy code), but you can still use the old cryptkeeper 0.9.5-5.1 package with newer encfs. I used GDebi to install it and have had no package management problems whatsoever.

---

### Post by gordintoronto on 2017-11-06
Did you try Sirikali?

---

### Post by erinspice on 2017-12-03
Using encfs directly worked just fine for me.

> $ encfs -f encrypted_dir mounted_dir
$ fusermount -u mounted_dir

---

### Post by ian-weisser on 2017-12-03
Thanks for sharing a great solution!

---

