---
title: "GIMP 2.3.9 Unstable"
date: 2006-06-07
forum: The Cafe
---

### Post by roderikk on 2006-06-07
Hi!

Did anyone already try the new GIMP 2.3.9? I am really keen on trying all the new features and checking for bugs, but as a (relative) noob I haven't got a clue on how to install it. Did anyone build a deb file?

Thanks.

---

### Post by kaamos on 2006-06-07
Just a minute, I'll try building one..

---

### Post by cbudden on 2006-06-07
Same here.

---

### Post by kaamos on 2006-06-07
```
Building GIMP with prefix=/usr/local
Desktop files install into ${datarootdir}

Extra Binaries:
  gimp-console:      yes
  gimp-remote:       yes

Optional Plug-Ins:
  Ascii Art:         yes
  Help Browser:      yes
  Gimp-Print:        no
  GNOME Print:       yes
  JPEG:              yes
  MNG:               yes
  PDF:               yes
  PNG:               yes
  PSP:               yes
  SVG:               yes
  TIFF:              yes
  MacOS X TWAIN:     no
  URI:               yes (using gnome-vfs)
  Win Print:         no
  Win Snap:          no
  WMF:               yes
  XJT:               yes
  XPM:               yes

Plug-In Features:
  EXIF support:      yes
  GNOME UI:          yes
  GNOME keyring:     yes

Optional Modules:
  ALSA (MIDI Input): yes
  Linux Input:       yes
  Color Correction:  yes
  Soft Proof:        yes

```

It is in /usr/local so the package can be installed at the same time with the ubuntu default gimp. Use /usr/local/bin/gimp-2.3 to start the program.

[gimp 2.3.9 for i386](http://users.tkk.fi/~alaisi/ubuntu/gimp-2.3.9_i386.deb) (packaged with checkinstall)
[source](ftp://ftp.funet.fi/pub/sci/graphics/packages/gimp/gimp/v2.3/gimp-2.3.9.tar.bz2)

---

### Post by roderikk on 2006-06-07
Wow! Thanks for the help.

I've just tried it out for a few minutes and it really seems more responsive. Also the USM filter seems to go a lot faster. They are really doing a good job. =D> 

Back to some more testing ;-).

Thanks again! In the future I will just have to learn how to create my own deb files. Is there a step by step instruction somewhere on how to do this?

---

### Post by Kimm on 2006-06-07
generaly you can use checkinstall (allows for a clean uninstall of your localy build programs, and to easly spread your builds)

it can be installed from the repos:

sudo apt-get install checkinstall

to use checkinstall you must first configure and compile the program.

cd <directory where the source is>
./configure
make
checkinstall

make will build the package and checkinstall will install it and create a package from it.

There are other, more complicated ways. But this works unless your running a distro of your own.

---

### Post by roderikk on 2006-06-07
[QUOTE=Kimm]cd <directory where the source is>
./configure
make
checkinstall[/QUOTE]

That sounds easy enough! However, do I need any libraries/dependencies to do make? I can remember once trying this and getting errors that I somehow missed a C++ compiler :roll: . I guess I need a little more practice/help ;-).

---

### Post by JimmyJazz on 2006-06-07
[http://jimmyjazz.homeip.net:808/debs/](http://jimmyjazz.homeip.net:808/debs/)

(click on Gimp)

heres the deb (i386)

---

### Post by SlugO on 2006-06-07
Thanks for the debs, I'm using the one from Kaamos and it works great :)
Just one annoying thing: the toolbar windows are always on top with no way of changing it :???: Is there an option to change this in GIMP's settings? Went over them many times... And no, always on top isn't ticked in the windows' right button menu.

---

### Post by MetalMusicAddict on 2006-06-07
Thank you kaamos. Do you think this is stable enough to use full time? If so how can I change the right-click options to point to 2.3?

---

### Post by Jucato on 2006-06-07
Hmm... will installing this have any adverse effect on some of Dapper's dependencies? Does it need some new packages/library versions to be installed? Or do I need to install Ubuntu's GIMP from the repositories first?

Sorry for the questions. I had a very nasty experience in Breezy when I tried to install a version of GIMP that was more recent than the one in the repositories. It needed some new lib packages which destroyed the dependencies on my system. Granted I took the .debs from Debian. :D

PS. I've never had any success in using checkinstall. It always gives me an error message. Anyway, I just keep the folder where I extracted the source code and just "make uninstall" when I don't need the app anymore. Or will that still leave some things lying around?

---

### Post by kaamos on 2006-06-08
[QUOTE=Fenyx]Hmm... will installing this have any adverse effect on some of Dapper's dependencies? Does it need some new packages/library versions to be installed? Or do I need to install Ubuntu's GIMP from the repositories first?[/QUOTE]

The package itself does not have any dependencies, but it probably won't wont if have not installed (you can just install to get the dependencies and then remove) gimp from the repos.

[quote=roderikk]
That sounds easy enough! However, do I need any libraries/dependencies to do make? I can remember once trying this and getting errors that I somehow missed a C++ compiler . I guess I need a little more practice/help .[/quote]

You need to have the package "build essential" installed before you can compile. In this case it is also very simple to get the other dependencies just with
```
sudo apt-get build-dep gimp
```

---

### Post by Jucato on 2006-06-08
Sorry to get back so late. I have GIMP 2.2.11 installed (the one from the repositories). Would that be enough to successfully install 2.3.9?

Lastly, if I were to uninstall it, what command would I use? I can't use sudo dpkg -r gimp, right?

Thanks!

---

### Post by roderikk on 2006-06-08
[QUOTE=kaamos]You need to have the package "build essential" installed before you can compile. In this case it is also very simple to get the other dependencies just with
```
sudo apt-get build-dep gimp
```[/QUOTE]

As you can see on [this thread]("http://www.ubuntuforums.org/showthread.php?t=191522") I am having a bit more problems with trying your method... I can't seem to get past the 'make' step... But that might also have to do something with the program I am installing.

Thanks again for packaging the gimp 2.3.9. I tried it a bit more and am really pleased with how everything works. It starts up really fast, has some really nice feature (try the extract from background feature, it is so cool!) and is a major improvement over 2.2.11. I haven't yet had any crashes or anything (touch wood).

---

### Post by Enigmatic on 2006-06-10
I don't know if I'm missing something, but the new print function doesn't give me any options. Before it was great, you had full control over printout size, position, orientation etc etc.

---

### Post by kaamos on 2006-06-10
[QUOTE=Enigmatic]I don't know if I'm missing something, but the new print function doesn't give me any options. Before it was great, you had full control over printout size, position, orientation etc etc.[/QUOTE]

If you are using the deb I posted, that would be my bad. I did not notice to check for that when compiling and used gnome-print (that sucks) instead of gimp-print..

---

### Post by Kimm on 2006-06-10
I compiled Gimp 2.3.9 here, and its pretty stable.

But I dont like the new interface... the tool windows are allways ontop (sometimes when the image is big, its gets behind those windows) and they made a new, separate window for color selection...

---

### Post by SlugO on 2006-07-07
Has anyone managed to build Gimp 2.3.10? There's apparently a vulnerability in the way 2.3.9 handles xcf files.

---

### Post by hellmet on 2006-07-08
well, i cud not make out any differences with the older
version in those few seconds i had a look at it!!

---

### Post by henriquemaia on 2006-07-10
Anyone to make a amd64 deb?

---

