---
title: "[SOLVED] Apache issues"
date: 2008-02-22
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-22
After loading the main page of a website but when I go to click on a link I get access denied and it will not load pictures, is there a problem with my html code or something wrong with apache?

---

### Post by faulkes on 2008-02-22
> **Holmes89 said:**
> After loading the main page of a website but when I go to click on a link I get access denied and it will not load pictures, is there a problem with my html code or something wrong with apache?

Check the /var/log/apache2/error_log (or custom log if you set one up)
and paste back the errors if any.

Faulkes

---

### Post by Holmes89 on 2008-02-22
(13)Permission denied: file persmissions deny server access: /var/www/website/site.html, referer: [http://192.168.0.100/](http://192.168.0.100/) (that is the local address that I'm attempting to use, note index.html works on local network)

the same line goes for the assets to the main page

oh and on a side note, does anyone know how to add an icon to a webpage?

---

### Post by Holmes89 on 2008-02-22
from what I can find it's a folder permissions issue but I don't know how to change folder permissions. Any ideas?

---

### Post by faulkes on 2008-02-22
> **Holmes89 said:**
> (13)Permission denied: file persmissions deny server access: /var/www/website/site.html, referer: [http://192.168.0.100/](http://192.168.0.100/) (that is the local address that I'm attempting to use, note index.html works on local network)

the same line goes for the assets to the main page


Check permissions on the files in website/ and the directory itself (website) to
ensure they are world readable.  That would appear to be the problem.

Faulkes

---

### Post by Holmes89 on 2008-02-22
Okay.... how do I do that? Sorry I'm new at command line.

---

### Post by faulkes on 2008-02-22
> **Holmes89 said:**
> Okay.... how do I do that? Sorry I'm new at command line.

```

cd /var/www
ls -l (look for the website directory and note it's permissions)
cd website
ls -l (look at the files and note there permissions)

```

For directory permissions, they should look like

```

drwxr-xr-x

```

for file permissions, they should look like

```

-rw-r--r--

```

If the furthest "r-x" isn't set for the directory, then yo have a problem.

If the furthest "r--" isn't set for the files, then you have a problem.

You can can the directory permissions to make them proper by:

```

chmod +rx website

```

and for the files

```

cd website
chmod +r <filename>

```

Faulkes

---

### Post by Holmes89 on 2008-02-22
hey thanks, that worked, now do I have to go through every file to do this? because I have a lot of assets in my assets folder and don't want to have to give them individual conditions, is there a way I can do it all at once?

---

### Post by Holmes89 on 2008-02-22
oh and what about php files? I have bblocked on my webpage how do I set permissions to all of those files?

---

### Post by kaginken on 2008-02-22
there's a few ways, depending on your circumstances.

If it's a bunch of files in one directory, just cd into the directory

cd <dir>

and change modifications on all files in it like so:

sudo chmod rw *

Hope that helps!

Rock on!

:guitar:

---

### Post by FakeOutdoorsman on 2008-02-23
kaginken's solution will work, and is right that there are many ways to do one thing in Linux.  This will find all folders and files in and under the current directory you are in and change them to a particular permission (755 for folders and 644 for files).  Read up on permissions / chmod before running this!

```
find . -type d -exec chmod 755 {} \; && find . -type f -exec chmod 664 {} \;
```

---

### Post by Holmes89 on 2008-02-24
Great that worked but just to remind people like me who are new at this you need to put a +rw to allow permissions and - to take them away

---

### Post by Holmes89 on 2008-02-24
oh this might sound stupid how do I change the little icon by the URL?

---

### Post by faulkes on 2008-02-25
Create a new favicon.ico file and place it in the DocumentRoot directory of your
website.

favicon.ico is a windows icon filetype, they can be created using gimp or
in general almost any modern graphics creation program.

Faulkes

---

