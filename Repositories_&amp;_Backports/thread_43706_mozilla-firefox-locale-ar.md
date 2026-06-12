---
title: "mozilla-firefox-locale-ar ?"
date: 2005-06-22
forum: Repositories &amp; Backports
---

### Post by foxiness on 2005-06-22
mozilla-firefox-locale-ar 

i found this on debian but not on ubuntu can it add to ubuntu too 
[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mozilla-firefox-locale-ar&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mozilla-firefox-locale-ar&searchon=names&subword=1&version=stable&release=all)

thanks

---

### Post by SGC on 2005-06-22
Just download the package and install it with the following command:
dpkg -i mozilla-firefox-locale-ar_0.2-2_all.deb

---

### Post by foxiness on 2005-06-22
thanks for your help to install it 

but what i really want ,is to add this to ubuntu to easy to install for other like my frinds new to linux and coz ubuntu support other language other than arabic 

thank again

i'm happy to know there are frinds here :)

---

### Post by SGC on 2005-06-22
I f you want to to be able to install the package using apt-get or synaptic then do the following:
- add this line to /etc/apt/sources.list
```

deb http://http.us.debian.org/debian stable main contrib non-free

```
- from the terminal type this **sudo apt-get update** or open synaptic and hit the reload button.
- to install the package type the following comman
```

sudo apt-get install mozilla-firefox-locale-ar

```
- after installing the package remove the line that you add in the first step , since its a debian repository and if you don't remove it you will run into many problems and you will end up with broken packages
- after removing the line do **apt-get update**

As you see installing the package with dpkg is easier than going into this hassle.

[b]
Alternatevely you can download the xpi file from [Arabeyes](http://www.arabeyes.org/project.php?proj=Mozilla)  website , where you just click on the file in firefox and it will be installed. I didn't try it so I don't know it it will work or not
[/b]

---

### Post by foxiness on 2005-06-24
[QUOTE=SGC]I f you want to to be able to install the package using apt-get or synaptic then do the following:
- add this line to /etc/apt/sources.list
```

deb http://http.us.debian.org/debian stable main contrib non-free

```
- from the terminal type this **sudo apt-get update** or open synaptic and hit the reload button.
- to install the package type the following comman
```

sudo apt-get install mozilla-firefox-locale-ar

```
- after installing the package remove the line that you add in the first step , since its a debian repository and if you don't remove it you will run into many problems and you will end up with broken packages
- after removing the line do **apt-get update**

As you see installing the package with dpkg is easier than going into this hassle.

[b]
Alternatevely you can download the xpi file from [Arabeyes](http://www.arabeyes.org/project.php?proj=Mozilla)  website , where you just click on the file in firefox and it will be installed. I didn't try it so I don't know it it will work or not
[/b][/QUOTE]
 thanks for your support

and help ....

i will try this soon

---

