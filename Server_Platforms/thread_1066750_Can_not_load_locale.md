---
title: "Can not load locale"
date: 2009-02-11
forum: Server Platforms
---

### Post by hctopcu on 2009-02-11
I have a vBulletin forum. on my ubuntu 8.04
I try to display dates in my own language
When I try to change **locale** setting in language settings it says: ```
The locale 'tr_TR.UTF-8' could not be located on this server.
```
Then I tried this:
[PHP]a=setlocale(LC_ALL, 'tr_TR.UTF-8');
echo "'$a' ";
echo date(DATE_RFC822);[/PHP]
a is empty and locale doesn't work.
The output of 
> less /usr/share/i18n/SUPPORTED 
has both```
tr_TR.UTF-8 UTF-8
tr_TR ISO-8859-9
``` but neighter of them is working.
What is wrong? How can I do that?

---

### Post by hctopcu on 2009-02-11
I found it. I had to
>locale-gen tr_TR.UTF-8
to compile the locale I need
then run
>dpkg-reconfigure locales

---

### Post by orrie on 2009-02-12
You can also do it in this way:

Edit ~/.profile and add these lines:
```

LANG="tr_TR.UTF-8"
LC_ALL="tr_TR.UTF-8"

```

And then:
```

orrie@ubuntu ~ ;) sudo nano /var/lib/locales/supported.d/local

Add this line first (if it's not there):
tr_TR.UTF-8 UTF-8

```

After you've done that you can just run an sudo dpkg-reconfigure locales and it shall work.


I've just done this (with nb_NO.ISO-8859-1) to get standard keymap in the gnome-terminal (don't like UTF-8) and it worked very well.

---

