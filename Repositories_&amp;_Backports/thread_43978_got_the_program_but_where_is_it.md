---
title: "got the program but where is it?"
date: 2005-06-24
forum: Repositories &amp; Backports
---

### Post by ron126 on 2005-06-24
i apt-get for a program called 3dchess, after it has finished, i just don't know where is the program located.

So how do you find out the directory of the program that you have apt-get install it?

---

### Post by Digitallysick on 2005-06-24
i would think you could go to "find files" and search for it starting in the /

---

### Post by Xian on 2005-06-24
[QUOTE=ron126]i apt-get for a program called 3dchess, after it has finished, i just don't know where is the program located.[/QUOTE]
From the Main panel:

Applications > Debian > Games > Board > 3D Chess

---

### Post by ron126 on 2005-06-24
i don se any 'debian' in the 'applications' 

I have also search all the other tabs in 'applications' and still cant find the 3dchess.

please help.

---

### Post by alred on 2005-06-24
you may try this from the terminal :
> whereis 3dchess

---

### Post by ron126 on 2005-06-24
```
ronaldo@Ronaldo:~ $ whereis 3dchess
3dchess:
```

no, cant help.

---

### Post by alred on 2005-06-24
try
> whereis 3dc

or

> whereis 3Dc





PS :: [http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=3dchess&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=3dchess&version=hoary&arch=i386)

---

### Post by ron126 on 2005-06-24
yeah, i found it, thanks a lot alred, you're great

---

