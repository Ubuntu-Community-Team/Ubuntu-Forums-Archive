---
title: "request: Gnome Vazaar"
date: 2005-05-15
forum: Ubuntu Backports
---

### Post by 23meg on 2005-05-15
> GNOME Vazaar is an organizer for your items.

    * Classify your information in categories and subcategories.
    * MIMEs are autodetected and is able to handle text/html/images.
    * Other MIMEs are handled with its default application in GNOME.
    * Syntax highlighting is supported (gtksourceview).
    * One repository for all your items
    * Improved dialogs to add/edit items or (sub)categories 

from the descriptions and screenshots it seems like a possible alternative to kde's [basket](http://basket.kde.org), or maybe a nice complementary information management tool. no binary package is available, and i'm getting errors when i try to compile it..

here's the url: [http://www.kaskaras.net/vazaar/index.php](http://www.kaskaras.net/vazaar/index.php)

---

### Post by rwabel on 2005-05-15
[QUOTE=23meg]from the descriptions and screenshots it seems like a possible alternative to kde's [basket]("http://basket.kde.org"), or maybe a nice complementary information management tool. no binary package is available, and i'm getting errors when i try to compile it..

here's the url: [http://www.kaskaras.net/vazaar/index.php]("http://www.kaskaras.net/vazaar/index.php")[/QUOTE]
 what kind of error did you get when compiling?
I could compile it but I got an error when I start it up

 ```

```  vazaar: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory ```

``` 

I think it's because I don't have mozilla-gtkmozembed

---

### Post by 23meg on 2005-05-18
this is what i get:

> checking for libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 gnet-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gail... Package libgnome-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnome-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnome-2.0' found

configure: error: Library requirements (libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 gnet-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gail) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


---

### Post by rwabel on 2005-05-18
[QUOTE=23meg]this is what i get:[/QUOTE]
 you are missing several packages. 
Try to install:
 ```
 libgnome2-0
``` 

I don't know if you need the others too, try a bit with the missing packages. Maybe also some dev packages. And maybe I forgot to mention some.

 ```
 libgnomeui-0
libglade2-0
libxml2
gconf2
libglib2.0-0
libgnet2.0-0
libpango1.0-0
libgtksourceview1.0-0
```

good luck and let me know if it works or what error you still get

---

### Post by 23meg on 2005-05-18
i do have all those packages, but the problem is that the configure script can't find them. where can i set the PKG_CONFIG_PATH environment variable?

---

### Post by rwabel on 2005-05-18
[QUOTE=23meg]i do have all those packages, but the problem is that the configure script can't find them. where can i set the PKG_CONFIG_PATH environment variable?[/QUOTE]
 mhh strange..I have normally this errors when packages are missing. Sorry never played around with PKG_CONFIG_PATH

---

### Post by tread on 2005-05-18
If you are compiling stuff you need the dev packages .. like libgnome-2.0-dev
The exact name may vary .. search in synaptic.

---

### Post by rwabel on 2005-05-18
[QUOTE=tread]If you are compiling stuff you need the dev packages .. like libgnome-2.0-dev
The exact name may vary .. search in synaptic.[/QUOTE]
 right, I wasn't sure anymore if he needed the dev packages or not. I have them both. That's why I also wrote maybe he need the dev packages too. Thanks for pointing that out

---

### Post by tread on 2005-05-18
Sorry .. didn't read your post too carefully .. still groggy :)

---

### Post by rwabel on 2005-05-18
[QUOTE=tread]Sorry .. didn't read your post too carefully .. still groggy :)[/QUOTE]
 :)
btw can you start gnome vazaar?

I get this error message
```
 vazaar: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory 
```

---

### Post by dontodd on 2005-05-25
do a "locate libgtkembedmoz.so" I came up with

/usr/lib/mozilla-thunderbird/libgtkembedmoz.so
/usr/lib/mozilla/libgtkembedmoz.so
/usr/lib/mozilla-firefox/libgtkembedmoz.so

When I configured vazaar I did it with "--prefix=/usr" so I tried linking one of the libgtkmozembed's to /usr/lib:

sudo ln -s /usr/lib/mozilla/libgtkembedmoz.so /usr/lib/libgtkembedmoz.so

and now vazaar starts for me.

---

### Post by rwabel on 2005-05-25
[QUOTE=dontodd]do a "locate libgtkembedmoz.so" I came up with

/usr/lib/mozilla-thunderbird/libgtkembedmoz.so
/usr/lib/mozilla/libgtkembedmoz.so
/usr/lib/mozilla-firefox/libgtkembedmoz.so

When I configured vazaar I did it with "--prefix=/usr" so I tried linking one of the libgtkmozembed's to /usr/lib:

sudo ln -s /usr/lib/mozilla/libgtkembedmoz.so /usr/lib/libgtkembedmoz.so

and now vazaar starts for me.[/QUOTE]
 yes thanks for that tip. strange that one has to do that manually. does the quit button and preference button work for you?

---

### Post by 23meg on 2005-10-11
anyone successfully compiled Vazaar under Breezy?

---

### Post by KaSKAraS on 2005-10-23
Hi everybody!

I am the main (and the only at the moment) developer of Vazaar.
As I can read in the posts, a lot of people have many problems to compile it because of gtkmozembed library doesn't link with the program. 

Well, when I started to develop this program I had Debian Sarge and nobody had problems to compile it. Now, I have Ubuntu Breezy and I am upset because I have to make a link against libgtkmozembed (check this tip: [http://ubuntuforums.org/showthread.php?p=186023#post186023](http://ubuntuforums.org/showthread.php?p=186023#post186023) from dontodd). I don't know if it's a problem in vazaar (configure.in) or from ubuntu (i don't think so). Anyway, I have to check it. I'll add it to my TODO in my Vazaar :)

I didn't know basket but it seems a very nice app (but for kde). Both apps shares the same aims and philosophy (one repository many things).

At the moment, the development of vazaar is stopped until I study how implement some ideas and suggestions such as build an applet, a nautilus extension and improve many things. My laptop was broken all the summer and I don't have a lot of spare on my hands but I hope release a new version before christmas.

If you have any problem, suggestions, critic or code, let me know.

Best regards and enjoy Vazaar,
KaSKAraS

P.S.: the main page for Vazaar is [http://gnome-vazaar.software-libre.org](http://gnome-vazaar.software-libre.org) but sometimes I post news about it in my blog ([http://kaskaras.net](http://kaskaras.net))

---

### Post by 23meg on 2005-10-23
Very nice to see you posting here, and also to learn that you're looking into the Breezy compilation issue. I hope you sort out the problem and come up with a deb package soon; Vazaar looks like a very promising app. Keep up the good work.

edit: the URL on the forum link you gave looks incorrect.

---

### Post by KaSKAraS on 2005-12-19
Hi again!!

Yesterday I released a new version of Vazaar. Now, is a GNOME applet. It's was developed under Ubuntu 5.10 but I hope it works even in Debian Sarge (please, anybody can check it?)

At the moment there isn't debian package. I'd like the people test my program and give me thir feedback. You can download it from [http://www.kaskaras.net/vazaar](http://www.kaskaras.net/vazaar)

regards,
Tomas V.

[QUOTE=23meg]Very nice to see you posting here, and also to learn that you're looking into the Breezy compilation issue. I hope you sort out the problem and come up with a deb package soon; Vazaar looks like a very promising app. Keep up the good work.

edit: the URL on the forum link you gave looks incorrect.[/QUOTE]

---

### Post by benplaut on 2005-12-19
i'm getting the same thing 23meg was...

```

checking for PACKAGE... configure: error: Package requirements (libpanelapplet-2.0 libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gnet-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

i symlinked gtkmozembed as recommended by dontodd, but not doing anything different...

i have all the packages, and their dev packageds installed... any suggestions?

---

### Post by KaSKAraS on 2005-12-19
I think the problem is not gtkmozembed, now.

Which version of ubuntu are you using? Did you pass the '--prefix=/usr' to configure script? 

About my configure.in PACKAGE=$pkg_modules and 

pkg_modules="libpanelapplet-2.0 libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gnet-2.0"

With the next command you get the current version of your libraries:
pkg-config --modversion libpanelapplet-2.0 libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gnet-2.0 

In my system theses are:
libpanelapplet-2.0	2.12.1 
libgnome-2.0	2.12.0.1
libgnomeui-2.0	2.12.0
gtk+-2.0	2.8.6
libglade-2.0	2.5.1
libxml-2.0	2.6.21
gconf-2.0	2.12.0
glib-2.0	2.8.3
mozilla-gtkmozembed	1.7.12
pango	1.10.1
gtksourceview-1.0	1.4.2
gnet-2.0	2.0.7

It's possible some of theses libraries fail.

Sorry if I can't solve your problem. I'll be pleased to listen more suggestion about this topic. I'd like try to compile my application under Debian Sarge because I think Vazaar doesn't need the last version of theses libraries to compile and work fine.

regards,
Tomas

[QUOTE=benplaut]i'm getting the same thing 23meg was...

```

checking for PACKAGE... configure: error: Package requirements (libpanelapplet-2.0 libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gnet-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

i symlinked gtkmozembed as recommended by dontodd, but not doing anything different...

i have all the packages, and their dev packageds installed... any suggestions?[/QUOTE]

---

### Post by Knomefan on 2005-12-20
Hi, first off, looks like a great app.

But I'm having some problems getting it to work.
The first problem is that it depends on mozilla-dev, while stuff on breezy is normally compiled against firefox. However, simply installing mozilla-dev fixes this of course.

The other dependencies took some fuzzing around, as I wasn't sure which package provided which dependencies, but afaict all the needed dependencies are in breezy and it compiles fine.

However, once compiled and installed with checkinstall (I compiled it with --prefix=/usr), it gives me an error when I try to add it to the panel.
Now, I don't have any idea how to debug a panel applet, or simply see where it goes wrong, so if you could tell me how to do that, I'll gladly give you more detailed feedback.

---

### Post by jesusjimenez on 2005-12-22
Hi guys,
I'm a slackwarist, but I hope that the solution would work on Ubuntu too. I've had the same problems after installing vazaar - I could not add it to the panel. So, simply running /usr/libexec/vazaar from terminal gives you the error message saying that libgtkembedmoz.so was not located, or something like that. There are two possible solutions. 
Locate libgtkembedmoz.so and xpcom.so (should be in /usr/lib/firefox)
First is su && ln -s /usr/lib/firefox/libgtkembedmoz.so /usr/lib/libgtkembedmoz.so && ln -s /usr/lib/firefox/xpcom.so /usr/lib/xpcom.so && ldconfig
and the second is
su to root, edit /etc/ld.so.conf, add /usr/lib/firefox to /etc/ld.so.conf, save, run  ldconfig as root
Now you should be able to add vazaar to the panel.

---

### Post by Knomefan on 2005-12-22
Thanks a lot jesusjimenez, that did it.

After linking the libs to /usr/lib (note if anyone want to try it, you'll find them in /usr/lib/mozilla-firefox/ and the second lib is called libxpcom.so in ubuntu) vazaar finally works and I get to play around with it.

Thanks again, very much appreciated.

---

### Post by KaSKAraS on 2006-01-04
Well, I think I've found the solution to my big problem: link vazaar with mozilla without make any links with "ln" command

I've copied and modified specific parts from epiphany's configure.in and I've deleted the link to mozilla library. Also I've modified the Makefile.am in src/applet/Makefile.am to link with Mozilla and the autogen.sh file.

Before make a new release I'd like somebody check the program and tell me if it works (removing links to mozilla libraries -libgtkembedmoz.so and xpcom.so-).

Because of I can't connect to my ftp server I've attached the sources in this post. However, If you want debug the program you can use the next command:
```
./autogen.sh --prefix=/usr --with-debugging-output
```

and execute it with:
```
/usr/libexec/vazaar
```

After do that, launch the applet from GNOME panel:
```
Add to panel... -> Accesories -> Vazaar
```
Thank so much to everybody for your feedbacks.

---

### Post by Josip Lazic on 2006-01-07
[QUOTE=KaSKAraS]Because of I can't connect to my ftp server I've attached the sources in this post. However, If you want debug the program you can use the next command:
```
./autogen.sh --prefix=/usr --with-debugging-output --with-debug
```
[/QUOTE]


checking for PACKAGE... configure: error: Package requirements (libpanelapplet-2.0 libgnome-2.0 libgnomeui-2.0 gtk+-2.0 libglade-2.0 libxml-2.0 gconf-2.0 glib-2.0 mozilla-gtkmozembed pango gtksourceview-1.0 gnet-2.0) were not met.

I got this error, but I have installed devel packages. Can you make .deb package, because I would realy like to try Vazaar.

Thanks.

---

### Post by KaSKAraS on 2006-01-07
Hi Josip,

I have never made deb packages and I would be pleased if somebody could do it for me because at the moment I am concentrated on the code and I don't have enough spare time. Anyway, when I finish the next version (0.3) I am going to try make it by myself if nobody can.

I don't know which is the library that configure doesn't met. Check if you have all of them installed and, in special, the mozilla-dev library -I suppose you are using ubuntu-.

Another thing that I just to notice is the fact of vazaar doesn't compile when you pass the option '--with-debug' to the autogen or configure script. Anyway, If you don't get any error in the './configure --prefix=/usr' script you can build the executale and install the application.

Regards

---

### Post by brainkilla on 2006-01-08
You can make a .deb package with checkinstall (which is in the repos). After programme has compiled, instead of make install just type checkinstall, and you'll have a package in no time. Thanx for the app and the effort ;)

---

### Post by Josip Lazic on 2006-01-08
[QUOTE=brainkilla]You can make a .deb package with checkinstall (which is in the repos). After programme has compiled, instead of make install just type checkinstall, and you'll have a package in no time. Thanx for the app and the effort ;)[/QUOTE]

I know for checkinstall, but checkinstall does not handle the dependencies. Here is scool od making .deb packages [https://wiki.ubuntu.com/MOTU/School/2005-12-10](https://wiki.ubuntu.com/MOTU/School/2005-12-10)

---

### Post by Josip Lazic on 2006-01-08
[QUOTE=KaSKAraS]Hi Josip,

I have never made deb packages and I would be pleased if somebody could do it for me because at the moment I am concentrated on the code and I don't have enough spare time. Anyway, when I finish the next version (0.3) I am going to try make it by myself if nobody can.

I don't know which is the library that configure doesn't met. Check if you have all of them installed and, in special, the mozilla-dev library -I suppose you are using ubuntu-.

Another thing that I just to notice is the fact of vazaar doesn't compile when you pass the option '--with-debug' to the autogen or configure script. Anyway, If you don't get any error in the './configure --prefix=/usr' script you can build the executale and install the application.

Regards[/QUOTE]
I managed to compile and checkinstall Vazaar. Key is to edit configure and configure.in and remove mozilla-dev requirement on 22990 line, because i have firefox-dev, and i really dont want mozilla-dev to.

---

### Post by KaSKAraS on 2006-01-08
As far as I know, the 'configure' script is generated when you run ./autogen.sh (--options) using the info supplied by configure.in. You shouldn't edit any line in the configure script.

configure.in try to detect your gecko engine (GECKOS="firefox mozilla-firefox seamonkey mozilla thunderbird mozilla-thunderbird"). Running ./autogen.sh should be enough to detect if you have mozilla-dev or firefox-dev. All macros used to detect the current gecko comes from Epiphany web browser.  I couldn't find any better piece of code to detect them. Anyway, if you have any comments or suggestions about this issue, I would appreciate to hear from you because it is confused.

regards

---

### Post by ComplexNumber on 2006-12-31
**KaSKAraS**
i really like vazaar(version 0.3) and have used it previously in fedora core 5 where it worked perfectly. in fedora core 6, it crashes when i left-click on the vazaar applet. whats more, i uninstalled it using paco about an hour ago and its messed up my system (icons have disappeared from the main menu, no toolbar in gnome-terminal, no auto-repeat for the cursor, can't add windowlist applet back to my panel, can't add system monitor back to the panel, home folder icon has gone missing from my desktop, etc). i think the reason why is something to do with the files that are installed in /etc/gconf. it may well be paco that is partly to blame because, if an installation merely adds a line to a particular file, paco will just delete the whole file during an uninstallation rather than merely removing the added line.

---

