---
title: "chmod on several files with spaces in name"
date: 2011-07-20
forum: Server Platforms
---

### Post by Fodox on 2011-07-20
hello

I don't know how to fix this command:

```
sudo chmod 700 * 
```

when in the folder some files have the space character in the name. I have this error (sorry, italian version):

```
chmod: opzione non valida -- " "
```

translated is 'invalid option'. I have to chmod any single file with "", but it takes too much time...

thank you

---

### Post by SlugSlug on 2011-07-20
maybe cd ..
chmod 700 dir/  -R

---

### Post by Lars Noodén on 2011-07-20
I'm unable to duplicate your error.  What version of Ubuntu are you running?  Have you tried this variant?

sudo chmod 0700 ./*

---

### Post by Fodox on 2011-07-20
> **SlugSlug said:**
> maybe cd ..
chmod 700 dir/  -R

ok, also:

```
chmod 700 ./ -R
```

without exit from the folder. 
But in this way I chmod all files and subfolders too; if I want only files?

thank you

---

### Post by Fodox on 2011-07-20
> **Lars Noodén said:**
> I'm unable to duplicate your error.  What version of Ubuntu are you running?  Have you tried this variant?

sudo chmod 0700 ./*

bingo, now I have what I wanted. My distro is ubuntu server 10.4 lts.

---

