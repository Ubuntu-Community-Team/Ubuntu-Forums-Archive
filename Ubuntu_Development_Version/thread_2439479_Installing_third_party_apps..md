---
title: "Installing third party apps."
date: 2020-03-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2020-03-28
Can no longer simply click on Google Chrome or GzDoom installer.  It opens to archive manager, so I changed it to Ubuntu software and it also fails.  In both cases I was able to install from terminal using dpkg.  Google Chrome works fine, but GzDoom has no sound and I cannot install the file [COLOR=#00000A][FONT=&quot]libsndio6.1.  Will this file be omitted from Ubuntu, or is there a workaround.

Henry[/FONT][/COLOR]

---

### Post by P-I H on 2020-03-28
Did you use Snap Store or Software?
Snap Store which replaces Software in the 20200327 iso will not install Chrome, but on my installation done today Software installs Chrome.

---

### Post by Hewjr100 on 2020-03-28
That is what I did, but it does not work for GzDoom because of one file not in the system:  [COLOR=#00000A][FONT=&quot]libsndio6.1.  I tried installing this file in the terminal and get the following message.

> [/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package libsndio6.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source



E: Package 'libsndio6.1' has no installation candidate[COLOR=#00000A][FONT=&quot]

FYI I did install ubuntu-restricted-extras and libdvdcss

Henry[/FONT][/COLOR]

---

### Post by mc4man on 2020-03-28
sndio in 20.04 is now @ libsndio7.0
So what ever you're trying to install needs to update to use that instead.

(- Or you can download libsndio6.1 from bionic and  maybe install it alongside, maybe not..

---

### Post by Hewjr100 on 2020-03-28
Will try

Henry

---

### Post by Hewjr100 on 2020-03-28
Well no luck, installed libsndio6.1 but still no sound.  Gonna wait untill GzDoom 4.4 comes out.

Henry

---

### Post by Hewjr100 on 2020-04-02
Just realized that Software is not installed.  Installed it and now I can install third party apps.

Henry

---

