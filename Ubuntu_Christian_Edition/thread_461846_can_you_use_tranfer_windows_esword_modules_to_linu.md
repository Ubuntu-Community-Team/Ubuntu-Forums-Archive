---
title: "can you use tranfer windows esword modules to linux? to use"
date: 2007-06-02
forum: Ubuntu Christian Edition
---

### Post by Jesus4life0412 on 2007-06-02
can you use tranfer windows esword modules to linux? to use

---

### Post by cantormath on 2007-06-02
what is esword suppose to do?

---

### Post by shane2peru on 2007-06-02
> **Jesus4life0412 said:**
> can you use tranfer windows esword modules to linux? to use

Yes you can.  In windows go to C:\Program Files\e-Sword\ and then copy all the .bbl .cmt .not .map .dct files and paste them into your e-Sword directory in Linux.  This will depend on which e-Sword that you have installed.  How did you install e-Sword?  with the Ubuntu CE version?  Did you install it on your own?  I can let you know where to put the files if you tell me how you installed it.  

Shane

---

### Post by Jesus4life0412 on 2007-06-02
i installed it on my own so i copy all modules or just certain ones?

---

### Post by shane2peru on 2007-06-02
> **Jesus4life0412 said:**
> i installed it on my own so i copy all modules or just certain ones?

I would backup before copying all of them (being every file in the e-Sword folder).  It may work, but it may not.  It doesn't hurt to copy all the .bbl (Bible modules)  .cmt (commentary files)  .dct (dictionary files)  .map (map files)  .not (note files)  .top (topic files).  That will save you a looot of installing if you have a lot of modules.  I keep a backup file of those files, so I can just put them in at any given moment.  If you need any more help just post back.

Shane

---

### Post by Jesus4life0412 on 2007-06-02
where do i put the modules  in linux?

---

### Post by shane2peru on 2007-06-02
> **Jesus4life0412 said:**
> where do i put the modules  in linux?

Using Nautilus (the file manager) you should be able to hit ctrl-H to see hidden files.  Go to your home directory and look for **.wine -> drive_c -> Program Files -> e-Sword** and you can put them all there.  If you are in the command line just type/paste:
```

cd ~/.wine/drive_c/Program\ Files/e-Sword/

```  and you will be in the right place.  

Shane

---

