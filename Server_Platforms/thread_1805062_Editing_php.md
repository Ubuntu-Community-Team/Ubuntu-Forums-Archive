---
title: "Editing php?"
date: 2011-07-15
forum: Server Platforms
---

### Post by thobiasn on 2011-07-15
Hello, i was wondering if there is someway on my ubuntu server to create and edit .php files? Sorry if it is a nooby question. :)

---

### Post by ruffEdgz on 2011-07-15
If you just want to create a basic php file, you can do so by:
```

touch ./hello.php
vim ./hello.php

```
*NOTE* you can use whatever text editor you want.

Once the file is open, paste in this line of code to get you started:
```

<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>

```
This is a hello world example using php.

Save the file and you made yourself a php file.

Read more on php here: [http://www.w3schools.com/php/default.asp](http://www.w3schools.com/php/default.asp)

---

### Post by thobiasn on 2011-07-15
Thanks alot :D. Not to be a pain in the ***, but do you know if any php editors exist for the ubuntu server platform. Because i failed finding one.

---

### Post by xkaliburx on 2011-07-15
Are you talking GUI editor's or CLI?

As ruffEdgz said, vi, there is nano, etc.  If your talking GUI, you can download and use bluefish, NVU, as well as others, what type are you looking for?

---

### Post by bowens44 on 2011-07-15
> **thobiasn said:**
> Thanks alot :D. Not to be a pain in the ***, but do you know if any php editors exist for the ubuntu server platform. Because i failed finding one.

any text editor. php files are just plain text.

---

### Post by thobiasn on 2011-07-15
I was thinking about a CLI (no gui/shell right? im a noob at ubuntu :D) editor.

@bowens44
Yea but it would be awesome if a editor existed so i could get highlights and stuff.

---

### Post by xkaliburx on 2011-07-15
Right .

vi is a bit tough if you don't know the shortcut key's, nano is a bit more friendly but those are still both command line apps.  It's more just move with the keys, the basic;

^w is find
^k is cut
^u paste

Those are the 3 key ones I use.   ^o saves and ^x exits (prompts for save), but nano has been around for years and is really one of the easiest around (IMO)

---

### Post by thobiasn on 2011-07-15
cool thanks, helped alot :P

---

### Post by ruffEdgz on 2011-07-15
> **thobiasn said:**
> Thanks alot :D. Not to be a pain in the ***, but do you know if any php editors exist for the ubuntu server platform. Because i failed finding one.

If you are looking for a GUI based one: I use **vim-gnome**
```

sudo apt-get install vim-gnome

```

For the CLI when editing php or any other file: I use **vim**
```

sudo apt-get install vim vim-common

```

Cheers!

---

### Post by thobiasn on 2011-07-15
Thanks solved my problem! :D

---

### Post by Wim Sturkenboom on 2011-07-16
> **thobiasn said:**
> Thanks solved my problem! :D

It would be nice to know how ;) Did you follow the advise of one of the above posts, or did you find something on the web or .... ?

---

### Post by thobiasn on 2011-07-16
> It would be nice to know how  Did you follow the advise of one of the above posts, or did you find something on the web or .... ?

Yes i decided to use nano, because of the simplicity :D

> Right .

vi is a bit tough if you don't know the shortcut key's, nano is a bit more friendly but those are still both command line apps. It's more just move with the keys, the basic;

^w is find
^k is cut
^u paste

Those are the 3 key ones I use. ^o saves and ^x exits (prompts for save), but nano has been around for years and is really one of the easiest around (IMO)

---

### Post by linuxnizer on 2011-07-16
what's wrong with gedit :), nano is good

---

### Post by Wim Sturkenboom on 2011-07-16
> **linuxnizer said:**
> what's wrong with gedit :), nano is goodHow do you run gedit on a server without a X environment ?

---

### Post by linuxnizer on 2011-07-16
> **Wim Sturkenboom said:**
> How do you run gedit on a server without a X environment ?

I'm sure you know better :), either run gedit on the desktop and use ftp to haul the files in/out. OR, use ssh to tunnel the x windows session over to desktop.

OR

Use Notepad++ along the builtin FTP

---

### Post by xkaliburx on 2011-07-16
> I'm sure you know better , either run gedit on the desktop and use ftp to haul the files in/out. OR, use ssh to tunnel the x windows session over to desktop.

OR

Use Notepad++ along the builtin FTP


The OP was very clear after I asked;

> I was thinking about a CLI (no gui/shell right? im a noob at ubuntu ) editor.

So to say setup X on a server, or setup FTP, then do things, post back, etc. is not the right path, as if you are going to do that, the options to what do do become exponential!

---

