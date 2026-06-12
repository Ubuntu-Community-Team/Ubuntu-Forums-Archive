---
title: "HOWTO: Install F4L"
date: 2005-09-25
forum: Tutorials
---

### Post by picpak on 2005-09-25
I kind of stumbled onto this by accident...

Open up a terminal and run:

```
sudo apt-get install libstdc++5
```

Then run:

```
wget http://www.sonsuzdongu.com/paketler/f4lm_0.1-1_i386.deb
```

and then type:

```
sudo dpkg -i f4lm_0.1-1_i386.deb
```

To run, type

```
f4lm
```

If you want to make a shortcut:

```
sudo gedit /usr/share/applications/f4lm.desktop
```

Put in the new file:

```

[Desktop Entry]
Encoding=UTF-8
Name=F4L
GenericName=Flash for Linux
Comment=Make Flash movies in Linux
Exec=f4lm
Terminal=false
MultipleArgs=true
Type=Application
Categories=Application;Network

```

Enjoy :D

---

### Post by beercz on 2005-10-28
Thanks picpak

Worked flawlessly.

Appreciated it.

Ian

(Now if only I could sort out my power management issues ......)

---

### Post by drummer on 2005-10-28
What is it?? is it just like macromedia's flash player? does it make flash animations?

EDIT - nevermind, found out myself.. but is it a port of flash or something? or written from scratch.. the UI looks just like marcomedia's flash.

---

### Post by telmo on 2006-11-04
WOW!!! I've been looking everywhere for this? And now i can simply use it! OMG!!! I can't believe it!...

You rock! ;)

THX

---

### Post by telmo on 2006-11-04
Nop! Sorry... Actually, it stinks! It's like a fake version of Macromedia Flash, but it doesn't work at all... [-(

---

### Post by nevernamed on 2007-03-14
it worked nicely for me before, but then I upgraded to 6.10 and lost the install of f4l. Now when I try it it says:
>  Inconsistency detected by ld.so: dl-runtime.c: 77: _dl_fixup: Assertion `((reloc->r_info) & 0xff) == 7' failed!

How can I fix this?

---

### Post by elmagique on 2007-03-22
another thing you can do is just install the origional macromedia flash

[here is a tutorial]("http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/")


i found  it when i was looking for F4L and it's better i think

this version doesn't export to swf i've heard

---

### Post by Toxicity999 on 2007-03-22
All platinum: [http://appdb.winehq.org/appview.php?iVersionId=3673](http://appdb.winehq.org/appview.php?iVersionId=3673)

---

### Post by nevernamed on 2007-04-12
I've tried the wine installs before and they haven't really run the exe's properly that I've downloaded from the adobe website.
I also tried a reinstall of the software, but I still get the same error as before.
If anybody knows anything about the f4l problem could you please let me know?

Thanks.

---

### Post by Death_Sargent on 2007-06-12
The way to install real flash is anoying and expensive, why not figure out why this versino does not work. i mean its clear that at some point in time i did there must just be something different about our systems that causes this to fail

---

### Post by zeroprezens on 2007-12-05
it says it installed for me and everything but when i try to run from terminal it says this:

nick@nick-desktop:~$ f4lm
f4lm: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

help please? i followed commands exactly so i dont think i did something wrong..

---

### Post by stkrzysiak on 2008-01-28
I have the same error: 
[I]
f4lm: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/I]


anyone have any thoughts on this?  is f4l the only solution to edit flash videos on linux(aside from messing with a wine type install)?

---

### Post by stkrzysiak on 2008-01-28
> **zeroprezens said:**
> it says it installed for me and everything but when i try to run from terminal it says this:

nick@nick-desktop:~$ f4lm
f4lm: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

help please? i followed commands exactly so i dont think i did something wrong..


zero, the solution for me was to install that version of libstdc++

Try this at the command prompt: 
sudo apt-get install libstdc++5

---

### Post by CobaltSS on 2008-11-27
I'm running Hardy 32bit. The easiest thing for me was to download a f4l Fedora i386 rpm and convert it to deb. Just double click and install. type f4l from terminal or create a link. I have uploaded the deb file here....

[http://www.mediafire.com/?sharekey=28ede62fe0695bfed2db6fb9a8902bda](http://www.mediafire.com/?sharekey=28ede62fe0695bfed2db6fb9a8902bda)

hope this helps!

---

### Post by nevernamed on 2008-11-27
Dead thread. Thanks for the post though.

I'm sure it'll help people in the future.

---

### Post by CobaltSS on 2008-11-27
Ya, that's pretty much why I posted it because I kept getting directed to this thread when I was recently having the same problem. So this definately should help someone in the future.

---

### Post by pfennig59 on 2009-06-27
Yes, thanks, guys, it helped us today. :P

@[stkrzysiak]("http://ubuntuforums.org/member.php?u=475882")
> sudo apt-get install libstdc++5

this saved the day

-- 
pfennig59

---

### Post by Vistaus on 2009-06-27
I really hope somebody will grab the source code of F4L and continue the development of F4L. It's not in a bad condition and I'm sure this can be a nice alternative for Adobe Flash :)
Also, the language isn't too difficult since it is written in C++.

---

### Post by dannymichel on 2009-07-26
updated tutorial for jaunty x64?

---

### Post by brunoaco on 2009-09-08
the older version worked great for jaunty, but f4l is in version 0.2.1

i see no deb....


can you tell me how to install this new version?

thx

---

### Post by brunoaco on 2009-09-10
good news guys:

if you really want to develop using flash, the best solution i found is [wine-doors]("http://wddb.wine-doors.org/downloads") wich works as a repository and has macromedia flash 8 ready to install...

let me tell you, it works flawlessly
:cool:

---

### Post by pvhnl on 2009-09-19
I read the tutorial at page 1

The last setting:

quote"
Put in the new file:

[Desktop Entry]
Encoding=UTF-8

Name=F4L
GenericName=Flash for Linux
Comment=Make Flash movies in Linux
Exec=f4lm
Terminal=false
MultipleArgs=true
Type=Application
Categories=Application;Network
I do not understand.

In what file I do have to put the code above?

My problem:

I can start f4l but ubuntu(9.04) is showing me the terminal-window containing the following:
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty

after a second f4l is starting up.

After creating some text and boxes for testing I want tot export to flash.
using éxport movie'and &#7765;ublish' in the File-menu is not givving any reaction?

Please can you help me?

---

### Post by amine.hch on 2010-01-10
try :

[http://zvonsully.home.ro/Downloads/App/ … 3_i386.deb]("http://zvonsully.home.ro/Downloads/App/ … 3_i386.deb")
to create a lancer :

type : app
commande :/usr/local/bin/f4lm

---

### Post by picpak on 2010-01-10
Since that link doesn't work, try

[http://zvonsully.home.ro/Downloads/App/f4l_0.2BETA-3_i386.deb](http://zvonsully.home.ro/Downloads/App/f4l_0.2BETA-3_i386.deb)

---

### Post by amine.hch on 2010-01-10
[https://bugs.launchpad.net/ubuntu/+bug/195030](https://bugs.launchpad.net/ubuntu/+bug/195030)

---

### Post by amine.hch on 2010-01-13
or you can use **[COLOR="Red"]macromedia flash 8[/COLOR]** (windows application) but you must install first **wine**

---

### Post by gvkoeller on 2010-01-26
This is missing to install in Ubuntu 9.10 Karmic Koala:
[http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

just download, install, and the package f4l will work perfectly!

Thanks for this entry!

Best regards,
gvkoeller.

---

### Post by elektros75 on 2010-02-03
thanks!

it took a minute and a couple of tries, bt it worked, rock on

---

### Post by theophiles on 2010-03-05
> **gvkoeller said:**
> This is missing to install in Ubuntu 9.10 Karmic Koala:
[http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

just download, install, and the package f4l will work perfectly!

Thanks for this entry!

Best regards,
gvkoeller.
For folks who are trying to follow these posts as instructions.

In order install libstdc++5, I had to add this software source to my repositories:

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main

---

### Post by dannymichel on 2010-03-05
> **theophiles said:**
> For folks who are trying to follow these posts as instructions.

In order install libstdc++5, I had to add this software source to my repositories:

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny mainthanks

---

### Post by hansdevr on 2011-09-10
....anyone care to update on the install of F4L on Kubuntu 11.04?

The .deb package was not working and the original instructions (by the developer) suck...

---

