---
title: "Install more modules [PHP]."
date: 2006-04-22
forum: Server Platforms
---

### Post by Nordoelum on 2006-04-22
Greeting,

Just wonder how I could install more modules from the php tarball?

I know I use the ```
./configure
``` command, but I have allready compiled it. And wondered if I could use something like ```
./configure --with-out-php --with-gd
``` 
In other words, how do I only install GD library? And/or other modules without compiling the php package again.. Like gettext, etc.

Ayy answear is appreciated :D

---

### Post by fdoving on 2006-04-22
I recommend using the packages from the repositories.

```

apt-get install libgd2-xpm

```

To include -dev headers:
```

apt-get install libgd2-xpm-dev

```


- Frode

---

### Post by Nordoelum on 2006-04-22
Thank you for answearing :D

Will the PHP version I have compiled using the GD library version? I am trying a testing of Gallery2.

Ed1t: [removed]
Ed2t: Missreaded the gallery2 config.

---

### Post by Nordoelum on 2006-04-25
Is it safe to compile PHP again when it is installed allready? Will it detect the version I have installed, and if there is some things that is changed, it will replace?

---

### Post by Nordoelum on 2006-04-25
[QUOTE=fdoving]I recommend using the packages from the repositories.

```

apt-get install libgd2-xpm

```

To include -dev headers:
```

apt-get install libgd2-xpm-dev

```


- Frode[/QUOTE]
I allready had the latest version.

---

### Post by fdoving on 2006-04-26
I would recommend to use the packages of php from the repositories. Unless you have very specific needs.

You can pass --enable-gd (or something) to configure while compiling PHP, to enable it. Reading INSTALL or README in the PHP source will probably give you more detailed information.


- Frode

---

### Post by Nordoelum on 2006-04-26
I got to run with GD Library though... Thanks anyway :D

---

