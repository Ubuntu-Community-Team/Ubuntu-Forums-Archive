---
title: "How to let apache2 load specified header automatically?"
date: 2013-02-16
forum: Server Platforms
---

### Post by KooriNyann on 2013-02-16
I know i could add an code like this to let apache2 show a specified header file when display an folder of  website. 
```
HeaderName head.html
IndexIgnore head.html
```And all i need to do is put an head.html into that folder:

but when i mkdir a new folder, i have to put more and more head.html files into those new folders and the problem appeases:
> [COLOR=Red]**if my header file has a new version, I need to cp this new version into all folders i created before.**[/COLOR]
It is quite a very huge work for me...
i've try to use an ln command to make links into folders, but apache2 cannot recognize link files at all

so, my question is:
Is there any way to let apache2 load head.html file automatically?

---

### Post by KooriNyann on 2013-02-16
Oops... I've just solved this problem...
in mod_autoindex of Apache document, it says i can put the file into a specified folder such as .default then change the head file position into a absolute path.
So i can change my code into this:
```
HeaderName /.default/head.html
```
and then put an index.html file to make this folder not indexable.

I wish this could help others...

---

