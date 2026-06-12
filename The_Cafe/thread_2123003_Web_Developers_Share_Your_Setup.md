---
title: "Web Developers: Share Your Setup"
date: 2013-03-06
forum: The Cafe
---

### Post by itrogers on 2013-03-06
Kind of new to Ubuntu and greatly testing the waters. I am dual booting with windows but I am forcing myself to use Ubuntu while I work on websites and such. If there are any others in the programming/web design/development field who care to share their setup/screenshots/etc it would be greatly appreciated. Goal: completely ditch Windows. Go!

---

### Post by pqwoerituytrueiwoq on 2013-03-06
if you need something from windows you can use [wine]("apt:wine") and run [notepad++]("http://notepad-plus-plus.org/"), but if you want something native try [geany]("apt:geany")
i also use [firebug](https://addons.mozilla.org/en-us/firefox/addon/firebug/) with firefox
i hard code all my css, js, php, and html
how i have my system set up:
[http://yourupload.com/file/506cb252d5b71014e060e91d0b2a1353](http://yourupload.com/file/506cb252d5b71014e060e91d0b2a1353)
trying to run heaven 3.0 while recording did not work very well, i was also making sure my OC was stable with mprime (prime95 for linux)

---

### Post by na5h on 2013-03-07
[Aptana Studio]("http://www.aptana.com/"), 'nuff said!

---

### Post by CharlesA on 2013-03-07
I used to use an Ubuntu box running Bluefish, but I've migrated over to my Win7 box running Dreamweaver...

Of course, with that being said, I am still hand coding my site. CSS, HTML and PHP included.

I am currently tempted to hook up a second monitor to my main desktop.

---

### Post by itrogers on 2013-03-07
> **na5h said:**
> [Aptana Studio]("http://www.aptana.com/"), 'nuff said!
I am definitely going to take a look at this and try it out. Looks great!

---

### Post by harx1337 on 2013-03-07
> **na5h said:**
> [Aptana Studio]("http://www.aptana.com/"), 'nuff said!

This is quality.

---

### Post by CharlesA on 2013-03-08
> **na5h said:**
> [Aptana Studio]("http://www.aptana.com/"), 'nuff said!

Wow, that is pretty sweet. Free too.

---

### Post by Mikeb85 on 2013-03-08
Emacs and a browser console...

---

### Post by bmeakings on 2013-03-08
When I was using Windows I used Notepad2 and thought things couldn't get  any better. Now, if you put me in front of a Windows machine to do web  developing I'd go insane :)

Geany is my weapon of choice. Some of its features I particularly like are:
- Save all button
- Can remove trailing and other superfluous white spaces when saving
- Can close tabs with middle click
- Colour picker. Invaluable when I'm doing CSS. No more opening up GIMP for its colour picker!

There's more features either built-in or via plugins like an FTP file viewer, HTML character code picker, etc. If you install Geany I recommend you also install the geany-plugins package.

Another decent web-focussed text editor is Bluefish. I used it for a while but didn't find it to my liking.

If you do a lot of file comparing, Meld is a great little tool for diff viewing. There's also an extension for Nautilus called nautilus-compare that lets you select two files, right-click and then launches Meld to quickly compare the files.

---

### Post by SeijiSensei on 2013-03-08
> **Mikeb85 said:**
> Emacs and a browser console...

I prefer jed because it's a bit more lightweight than emacs, but otherwise I'm with you.  A text editor and a browser is all I've ever used for a decade now.  Oh, and the psql PostgreSQL command-line client for interacting with the database backend.

---

### Post by MooseDog on 2013-03-10
Apache
MySQL
PHP

all installed locally for, well, local development :).

For coding:

SublimeText2, repeat SublimeText2.

screenshot:
[ATTACH=CONFIG]239997[/ATTACH]

---

### Post by mustang on 2013-03-10
netbeans

---

### Post by Christmas on 2013-03-10
I'm just doing basic web development. I'm using [Emacs]("http://www.gnu.org/software/emacs/") and [Kate]("http://kate-editor.org/") as editors, as all my HTML/CSS/PHP code is done by hand. Also, I have Apache installed and several other packages needed to run a local wordpress blog or similar, e.g. php5-mysql, libapache2-mod-php5.

---

### Post by mehaga on 2013-03-11
[Webstorm]("http://www.jetbrains.com/webstorm/")

---

### Post by na5h on 2013-03-12
> **MooseDog said:**
> Apache
MySQL
PHP

all installed locally for, well, local development :).

[XAMPP]("http://www.apachefriends.org/en/xampp.html") is a great, hassle-free solution for local development.

---

### Post by Gyokuro on 2013-03-12
> **SeijiSensei said:**
> I prefer jed because it's a bit more lightweight than emacs, but otherwise I'm with you.  A text editor and a browser is all I've ever used for a decade now.  Oh, and the psql PostgreSQL command-line client for interacting with the database backend.

Cool - also a person which feels at home with a shell and command line tools - I prefer vim :p

---

### Post by BrokenKingpin on 2013-03-12
MonoDevelop (or VS2012 in Windows) for Asp.net development.

---

### Post by Ctrl-Alt-F1 on 2013-03-23
> **mustang said:**
> netbeans
This.  It freaking pre-scans your files and gives you xhtml to css auto-complete or vice versa.  I use Netbeans with just a regular LAMP stack installed on my development machine.  I'm considering switching to PostgreSql though.

---

### Post by ade234uk on 2013-03-23
> **itrogers said:**
> Kind of new to Ubuntu and greatly testing the waters. I am dual booting with windows but I am forcing myself to use Ubuntu while I work on websites and such. If there are any others in the programming/web design/development field who care to share their setup/screenshots/etc it would be greatly appreciated. Goal: completely ditch Windows. Go!

I know its old, but if you are desperate you can run Dreamweaver 8, Photoshop 7 fine in Ubuntu. You just need to install Wine to begin with.
I think Photoshop CS works well too.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=183](http://appdb.winehq.org/objectManager.php?sClass=application&iId=183)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

---

### Post by Mr. Picklesworth on 2013-03-26
I use Sublime Text for pretty well everything, along with lessc whenever I can (should that count? I think it should). I use Bzr even if I'm the only person working on something. It keeps me focused, and it's useful to have a full history of changes.

I recently started using LXC, which is indispensable if you want to locally test server stuff in a clean environment. Just create a container, install whatever you want inside it, and start / stop the container as necessary.

The good part of Microsoft recently released a free VM image for testing IE7+, so I've been meaning to play with that. It looks really well put together:
http://www.modern.ie/en-us/virtualization-tools

---

