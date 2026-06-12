---
title: "How to use GIMP 2.8 on Lucid 10.04.4 LTS"
date: 2012-05-18
forum: Tutorials
---

### Post by shreepads on 2012-05-18
Hi

This post is for people who
- Are excited about all the features on the new GIMP 2.8 and want to upgrade to it
- But want to stick to the Ubunutu Lucid 10.04.4 LTS as it's rock solid, unsoiled by Unity and supported for another year
- Don't want to go the whole hog and install/ upgrade GIMP and all the other dependencies, risking breaking their system
- Have limited experience with compiling apps, but know about installing stuff from the standard repositories and tinkering with the terminal

So a pretty small subset I guess! But anyway...

Firstly, most of the credit for this info goes to facebook.com/andrea.roscioli for his install script, which I found [here]("http://rubensa.wordpress.com/2012/05/08/script-to-compile-and-install-gimp-2-8-on-ubuntu-10-04-lts-lucid/"). I've just tweaked it a bit and tried to make it easier for noobs like me.

So let's begin.

**_Prerequisites:_**

You need to install a few things, but these are all from the standard Lucid repositories so there is very little chance this will break anything. From the terminal do:

```
sudo apt-get build-dep gimp
sudo apt-get install git-core
sudo apt-get install libtool
```

There are a few optional bits that you could install from Synaptic Package Manager. You can leave these out if you wish but they provide a few necessary capabilities to GIMP:
[LIST]
[*]libbz2-dev: Compression
[*]libjasper-dev: JPEG 2000 format support
[*]libgs-dev: Ghostscript, for PDF support
[*]libcurl4-gnutls-dev, libgudev-1.0-dev: Damned if I know what they are for
[/LIST]

Also, check if your system already has these as well from the standard Lucid reporsitories: pkg-config, intltool, fontconfig, libfreetype6

In addition I already have a bunch of things already installed which may not be installed on your system (can think of exiftool and the latest RawTherapee build for example) so you may have to come back and install a few more dependencies depending on what GIMP compilation reports (towards the end).


**_Preparation:_**

From now onwards you can perform the rest of the update without ever using sudo/ admin privileges, ensuring that the rest of the steps will not break any other existing applications.

- Create a folder structure to hold the GIMP 2.8 code and build in a folder on which you have free read, write, execute privileges. I've created the following under my home folder:

```
/home/user/Gimp
--> Gimp2.8
----> src
----> build
```

- I'll reference these in the rest of the notes, just change to suit your folder structure wherever appropriate.

- Download the following source files from the locations given. If you have an alternate trusted source please feel free to use that.

[LIST]
[*]gimp-2.8.0.tar.bz2 from gimp.org or mirrors
[*]gegl-0.2.0.tar.bz2 from [ftp://ftp.gimp.org/pub/gegl/0.2](ftp://ftp.gimp.org/pub/gegl/0.2)
[*]babl-0.1.10.tar.bz2 from [ftp://ftp.gimp.org/pub/babl/0.1/](ftp://ftp.gimp.org/pub/babl/0.1/)
[*]gtk+-2.24.10.tar.xz from [ftp://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/](ftp://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/)
[*]glib-2.31.18.tar.xz from [ftp://ftp.gnome.org/pub/gnome/sources/glib/2.31/](ftp://ftp.gnome.org/pub/gnome/sources/glib/2.31/)
[*]gdk-pixbuf-2.24.1.tar.xz from [ftp://ftp.gnome.org/pub/gnome/sources/gdk-pixbuf/2.24/](ftp://ftp.gnome.org/pub/gnome/sources/gdk-pixbuf/2.24/)
[*]pango-1.29.5.tar.xz from [ftp://ftp.gnome.org/pub/gnome/sources/pango/1.29/](ftp://ftp.gnome.org/pub/gnome/sources/pango/1.29/)
[*]cairo-1.10.2.tar.gz from [http://cairographics.org/releases/](http://cairographics.org/releases/)
[*]pixman-0.24.4.tar.gz from [http://cairographics.org/releases/](http://cairographics.org/releases/)
[*]atk-2.3.95.tar.xz from [ftp://ftp.gnome.org//pub/gnome/sources/atk/2.3](ftp://ftp.gnome.org//pub/gnome/sources/atk/2.3)
[/LIST]

- Optionally, you can also download these, if you want support for SVG format files (I needed it so I did)

[LIST]
[*]librsvg-2.36.1.tar.xz  from [ftp://ftp.gnome.org/pub/gnome/sources/librsvg/2.36/](ftp://ftp.gnome.org/pub/gnome/sources/librsvg/2.36/)
[*]libcroco-0.6.5.tar.xz  from [ftp://ftp.gnome.org/pub/gnome/sources/libcroco/0.6/](ftp://ftp.gnome.org/pub/gnome/sources/libcroco/0.6/)
[*]gobject-introspection-1.31.22.tar.xz   from  [ftp://ftp.gnome.org/pub/gnome/sources/gobject-introspection/1.31/](ftp://ftp.gnome.org/pub/gnome/sources/gobject-introspection/1.31/)
[/LIST]

- Copy/ move all these files to the Gimp2.8 src directory (/home/user/Gimp/Gimp2.8/src for me)

- Open the src folder, select all the downloaded files, right click and select 'Extract Here' from the context menu. This will unzip all the files in the src folder creating new sub-folders for each package with the appropriate package name, for example "/home/user/Gimp/Gimp2.8/src/gimp-2.8.0/"


**_Compile and Install:_**

 - Next we need to compile all the source files downloaded and extracted in the src subdirectory. All of these will be installed in the build subdirectory, leaving the rest of the system untouched

- Open a new terminal window and issue the following commands (replace the folder names with your folder structure created as above)

```
export PKG_CONFIG_PATH=/home/user/Gimp/Gimp2.8/build/lib/pkgconfig
export LD_LIBRARY_PATH=/home/user/Gimp/Gimp2.8/build/lib
```

- Note that these environment variables only hold for the given terminal session you've started, if you take a break, close it and start a new session you will need to issue these commands again.

- Navigate to you src directory, for me that's done using

```
cd /home/user/Gimp/Gimp2.8/src
```

- First we will compile the BABL package, located in the babl-0.1.10 subfolder under src. For this execute the following commands from the same terminal window, change the folder after "--prefix" as necessary.

```
cd babl-0.1.10
./autogen.sh --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3
```

- A few notes on the above
[LIST]
[*]The second command (autogen.sh) may generate errors indicating that one or the other dependency/ package is missing. I think we've covered all the dependencies but if that happens, ask Google with the error message. 
[*]If the autogen.sh command completes without any errors, the remaining 2 should go thru fine as well. In the unlikely event that you face an error with make or make install, you will need to explore the interwebs a bit more.
[*]The make and make install commands are followed by "-j3". The number 3 is the number of cores on your system (as reported by System Monitor) you want to use for compiling + 1. I have a Core2 Duo and don't want to browse/ play a video during this so have set it to 2+1=3. If you're unsure, leave the "-j3" bit out from the command.
[/LIST]

- Assuming you completed the BABL install fine, you need to compile (from src folder) and install (in build folder) all the other downloaded packages, in the following order (from the same terminal window). Note that the second command for all of these (configure) is different from the one for BABL (autogen.sh) but it plays the same role so you can apply the notes above for the BABL install to all of these.

```
cd ../glib-2.31.18/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../gegl-0.2.0/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../atk-2.3.95/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../pango-1.29.5/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../gdk-pixbuf-2.24.1/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../pixman-0.24.4/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../cairo-1.10.2/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../gtk+-2.24.10/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3
```

- Optionally, for SVG support, you also need to do the following. Note that the configure command for librsvg is slightly different.

```
cd ../libcroco-0.6.5/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../gobject-introspection-1.31.22/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
make -j3
make install -j3

cd ../librsvg-2.36.1/
./configure --prefix=/home/user/Gimp/Gimp2.8/build --disable-introspection
make -j3
make install -j3
```

- Assuming all of this goes thru and you succesfully navigate any errors that come up, you are ready to compile and install GIMP 2.8! Issue the following commands (from the same terminal window) and be a little patient...

```
cd ../gimp-2.8.0/
./configure --prefix=/home/user/Gimp/Gimp2.8/build
```

- Once the configure command finishes (assuming all mandatory dependencies are met, if not search) it will produce a summary of all the Optional features/ plug-ins/ modules that are available (or not). Have a look see if anything you must have is missing, if so a search is in order!

- The main thing you should see missing is WebKit. GIMP 2.8 needs WebKit 1.6.1 or above, but Lucid 10.04.4 has 1.2.7. Installing the latest Webkit can break stuff and compiling it is another whole post by itself so I'll leave it as-is. I didn't bother as you only lose the online help integration from within GIMP 2.8. You can always access the online help from your browser anyway so it's not a big loss.

- Assuming you got all your must-have features/ modules/ plug-ins supported, you can then do the following and go grab a drink.

```
make -j3
make install -j3
```

- Assuming you see no errors, you're done!!!


**_Running GIMP 2.8_**

- Without closing the terminal used all this while, go to the bin folder under the build subdirectory. For me that's done by

```
cd /home/user/Gimp/Gimp2.8/build/bin
```

- And then run it by crossing your fingers and running the command

```
./gimp-2.8
```

- Run through a few basic open image, edit and save commands. Note the output in the terminal, it will help you solve any problems you come across. I didn't get any so far :-). And exit

- To make this a bit easier to run, I've created a small text file in my home directory "/home/user/" called gimp28.sh, which contains the following shell script. (Remember to run chmod +x gimp28.sh after creating it, so that it has execute capability)

```
#!/bin/sh
export LD_LIBRARY_PATH=/home/user/Gimp/Gimp2.8/build/lib:$LD_LIBRARY_PATH 
/home/user/Gimp/Gimp2.8/build/bin/gimp-2.8
exit 0
```

- Next I dragged the existing GIMP shortcut from the top left menu tree onto the desktop, right clicked on it and selected "Properties", where I changed the following and clicked 'OK'
[LIST]
[*]The Name to "GIMP 2.8"
[*]The Command to "/home/user/gimp28.sh"
[/LIST]

- Now I just double click this shortcut to use GIMP 2.8!!
):P

---

### Post by shreepads on 2012-05-23
Even after setting Edit -> Preferences -> Help System -> Help Browser to "Web browser" it still doesn't open up the online help in the browser (Firefox in my case) complaining about missing GVFS backend components.

This despite the fact that the "configure" command while compiling gimp-2.8.0 produced the output:

```
Optional Plug-Ins:
...
  URI:                 yes (using GIO/GVfs)
```

So I just

[LIST]
[*]Downloaded gimp-help-2.6.0-html-en.tar.bz2 from [ftp://ftp.gimp.org/pub/gimp/help/](ftp://ftp.gimp.org/pub/gimp/help/). Help files in other languages can be downloaded as well.
[*]Created a subfolder 'help' under /home/user/Gimp/Gimp2.8/build/share/gimp/2.0
[*]Extracted the contents of gimp-help-2.6.0-html-en.tar.bz2 into the new /home/user/Gimp/Gimp2.8/build/share/gimp/2.0/help folder
[*]Moved the "en" folder under gimp-help-2/html (created as subfolders in the help folder) up to the help folder. So you should see /home/user/Gimp/Gimp2.8/build/share/gimp/2.0/help/en folder containing "index.html" and all the other help files. If your language is say French then you should see index.html in /home/user/Gimp/Gimp2.8/build/share/gimp/2.0/help/fr
[*]Started GIMP 2.8 and under Edit -> Preferences -> Help System I set
[/LIST]
[INDENT][LIST]
[*]User Manual: "Use a locally installed copy". A little message below this should state "There's a local installation of the user manual."
[*]Help Browser to "Web browser"
[/LIST][/INDENT]

In case the little message says there is no local installation of the user manual then check that the Language selected under Edit -> Preferences -> Interface -> Language, matches with the language of the help files you downloaded.

---

### Post by otto06217 on 2012-05-23
Nice, nice, nice!!!

Subsequent it give me some hope for building my Gimp standalone package for older Ubuntu Distros: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone](https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone)

'til then

Otto

---

### Post by OGpmpdog on 2012-05-23
OP,

Thanks for sharing your knowledge.  However, this tutorial seems to be a lot of work for software that will be at EOL in less than 1 year.

There are alternatives - such as Cinnamon, XFCE,and Gnome3(new and classic) - beyond Unity in 12.04, which is almost 5 years before EOL.

In 12.04, Gimp 2.8 can be installed with 3 terminal commands:

sudo add-apt-repository ppa: otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

Peace.

---

### Post by shreepads on 2012-05-23
> **otto06217 said:**
> Nice, nice, nice!!!

Subsequent it give me some hope for building my Gimp standalone package for older Ubuntu Distros: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone](https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone)

'til then

Otto

Thanks! For most people, your PPA will be a lot useful than this loooong list of instructions :-)

---

### Post by shreepads on 2012-05-23
> **OGpmpdog said:**
> OP,

Thanks for sharing your knowledge.  However, this tutorial seems to be a lot of work for software that will be at EOL in less than 1 year.

There are alternatives - such as Cinnamon, XFCE,and Gnome3(new and classic) - beyond Unity in 12.04, which is almost 5 years before EOL.

In 12.04, Gimp 2.8 can be installed with 3 terminal commands:

sudo add-apt-repository ppa: otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

Peace.

Well I did say it will only be useful for a small subset of people :-).

But seriously, I think it will be some time before 12.04 will be usable and stable enough for all. I tried the LiveCD/DVD/USB and it just refused to work with my graphics card (see [here]("http://ubuntuforums.org/showthread.php?t=1971029")).

BTW re the PPA mentioned in your post, see post just above yours from the PPA's author. He is trying to build a similar PPA for Lucid as well, which would make this long list of instructions redundant!

---

### Post by otto06217 on 2012-05-24
> **shreepads said:**
> Well I did say it will only be useful for a small subset of people :-).

But seriously, I think it will be some time before 12.04 will be usable and stable enough for all. I tried the LiveCD/DVD/USB and it just refused to work with my graphics card (see [here]("http://ubuntuforums.org/showthread.php?t=1971029")).

BTW re the PPA mentioned in your post, see post just above yours from the PPA's author. He is trying to build a similar PPA for Lucid as well, which would make this long list of instructions redundant!

My approach is to passing by the dependency nightmare in older Ubuntus.
By the way if you're interested supporting me any help are welcome.

On the other hand I'm using Kubuntu 12.04 as an early adopter without any serious problems. It's a Compaq Presario CQ60 with a GeForce 8200M G and 4 GB RAM.

I'll do my very best. I hope I'm ready with my dependency-nightmare-passing-by-and-totally-wasting-disk-space-standalone-version in the next 2 weeks.

Cheers and greetings from good old Germany. [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by otto06217 on 2012-05-24
Have I told you lately that I had more than 30000 downloads with my PPA?

Ok, it's probably less than the amount of poor sucker applicants for facebook shares.:p

BTW: I'm looking forward to Gimp 2.9 with its legendary 16bit color space for RAW photographs. Rumors: It will be done after the summer and in 2012.

OK

Cheers

---

### Post by shreepads on 2012-05-24
> **otto06217 said:**
> 
By the way if you're interested supporting me any help are welcome.


Sure what do you need? But I should tell you that I don't know much about compiling and packaging... And I just have one desktop system which I use on a daily basis for all work (no VMs) so I'm a LITTLE conservative about tweaking it...

> **otto06217 said:**
> Have I told you lately that I had more than 30000 downloads with my PPA?

Ok, it's probably less than the amount of poor sucker applicants for facebook shares.:p

BTW: I'm looking forward to Gimp 2.9 with its legendary 16bit color space for RAW photographs. Rumors: It will be done after the summer and in 2012.

OK

Cheers

Good stuff! Yup looking fwd to full 16 bit compatibility DSLR -> RawTherapee -> GIMP...

---

### Post by itzco on 2012-06-15
Hi Otto,

I tried to use the ppa in Lucid, and it shows an error, not found. 

I googled it and saw many people found the same problem, is there any way to get it?

Thanks by the way!

---

### Post by Wolfgang.Klein on 2012-06-27
shreepads: I followed your instruction and needless to say that they worked out perfectly. Many thanks for your effort! :)

If I find the time I will try to write a shell script that will do all necessary steps automatically. I will provide this script here for downloading. Maybe I'll get it done this weekend.

There's just one thing I would like to chance but I am not very good at this kind of stuff: can the building  procedure be changed to that effect that the resulting executable will be a staticaly linked binary that can be installed in /usr/local or in /opt using apt?

---

### Post by 42dorian on 2012-07-05
> **otto06217 said:**
> Nice, nice, nice!!!

Subsequent it give me some hope for building my Gimp standalone package for older Ubuntu Distros: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone](https://launchpad.net/~otto-kesselgulasch/+archive/gimp-standalone)

'til then

Otto

Any chance of this for Natty?  It's newer than 10.04.4, but it's at the limit for my video card's compatibility to the Ubuntu release cycle.  I use Xubuntu.

I have just managed to get it (GIMP 2.8 ) running using WINE instead of the long instructions.  The requirements were giving me a headache.  So, I do have it running in 11.04, but it would be nice if it was a PPA.

Not much love for the older systems anymore!  There was a time when Linux was friendly to older systems.

---

### Post by shreepads on 2012-07-10
> **Wolfgang.Klein said:**
> shreepads: I followed your instruction and needless to say that they worked out perfectly. Many thanks for your effort! :)

If I find the time I will try to write a shell script that will do all necessary steps automatically. I will provide this script here for downloading. Maybe I'll get it done this weekend.

There's just one thing I would like to chance but I am not very good at this kind of stuff: can the building  procedure be changed to that effect that the resulting executable will be a staticaly linked binary that can be installed in /usr/local or in /opt using apt?

Glad someone found it useful!

I'm not sure I understand your question re statically linked library in /usr/local or /opt. Do you want to do a full install? I'm not sure I'd recommend that, too many dependency packages need to be upgraded, which may break the system.

Sorry, but am quite new to this compile and install business!

---

### Post by miskopo on 2012-07-23
Thank you very much, it works :)
The interface is little bit ugly due the GTK+ version, but I don't mind. It works :))

---

### Post by dertom on 2012-07-23
Wow, thx so much! Actually I just installed 10.04 (after kicking 12.04) and since I'm doing a new setup from scratch I thought let's see about gimp2.8. Reading the INSTALL-file (and about all that dependencies...) let me decide to use the default gimp2.6(?) from the repository when I stumbled over your tutorial.

I have to say, perfect step by step copy and past tutorial. Better is just not possible.

Thx so much and keep on rocking,...

---

### Post by leemaster81 on 2012-08-09
Ran into a few problems... But after installing needed packages everything compiled and installed and I now have Gimp 2.8 installed on Lucid. Thank you!

-lmgh81

---

### Post by denUil on 2012-08-15
When trying to compile GTK+ I keep on getting this error:
$>./configure --prefix=/home/robin/Gimp/Gimp2.8/build/
...
$>make -j2
...
/usr/share/gir-1.0/GdkPixbuf-2.0.gir: Incompatible version 1.0 (supported: 1.2)
make[4]: *** [Gdk-2.0.gir] Error 1
make[4]: Leaving directory `/home/robin/Gimp/Gimp2.8/src/gtk+-2.24.10/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/robin/Gimp/Gimp2.8/src/gtk+-2.24.10/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/robin/Gimp/Gimp2.8/src/gtk+-2.24.10/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robin/Gimp/Gimp2.8/src/gtk+-2.24.10'
make: *** [all] Error 2

I've been googling but I can't find the solution...

Thanks a lot,
Robin



EDIT-----
Gave it a new try today, clean directories. Then it worked fine. Great tutorial!

---

### Post by innactpro on 2012-08-16
Thank you very much.

While configuring gobject-introspection, I had errors for flex and bison, quickly remedied through Synaptic.

I have not had a chance to deal with:

```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
While parsing XMP metadata:
Error on line 14 char 1: End of element <xmpMM:DerivedFrom> not expected in
this context

Metadata parasite seems to be corrupt
^C./gimp-2.8: terminated: Interrupt
/home/user/Gimp/Gimp2.8/build/lib/gimp/2.0/plug-ins/script-fu terminated:
Interrupt
user@user:~/Gimp/Gimp2.8/build/bin$ ./gimp-2.8
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
While parsing XMP metadata:
Error on line 14 char 1: End of element <xmpMM:DerivedFrom> not expected in
this context

Metadata parasite seems to be corrupt
Gtk-Message: Failed to load module "canberra-gtk-module"
```

Though I will be looking into it as soon as I get the chance.

Despite this however, gimp works fine, so far.

---

### Post by miskopo on 2012-08-25
Hi, I've created precompiled package with your instruction, it should works, it has 130 downloads and nobody has complained yet :lolflag:

Here is the link [http://sourceforge.net/projects/gimp28/files/](http://sourceforge.net/projects/gimp28/files/)

Enjoy it (if it doesn't work, please warn me) :KS

---

### Post by jimstar79 on 2012-09-10
Hi Guys, 

I've got to admit I freaked out a bit trying to follow the original instructions so I tried to use Otto's PPA and the package from Miskopo. 

Otto's PPA hasn't upgraded Gimp from 2.7 to 2.8 for me. 

Miskopo - when I try and install your package I keep getting: Gimp/Gimp2.8/build/bin/gimp-2.8: not found

I have placed the files in the home folder. Any further advice would be appreciated. 

Gimp is an amazing piece of software. 2.7 has everything for me but it crashes when I try and use fonts selection. I love the new single window mode and that's why I don't want to go back to 2.6.9.

Thanks in advance for any help!!

---

### Post by shreepads on 2012-09-11
> **jimstar79 said:**
> 

Otto's PPA hasn't upgraded Gimp from 2.7 to 2.8 for me. 



AFAIK Otto hasn't built the complete Lucid standalone Gimp 2.8 PPA as yet so I wouldn't expect that to work.

Hopefully miskopo can help resolve your problem...

Else you could take the easy way out :lolflag: and follow the original instructions!

OT, have been test driving Precise for a while now, very smooth looking but a few problems lurking around... (NVidia graphics/ shutdown problems/ silly global app menu that only appears on mouseover/ app launch bar doubling up for app switching - not very well I might add)...

---

### Post by jimstar79 on 2012-09-11
Hi Shreepads!

I have already started trying to compile from you original instructions. I have also found these instructions:

[https://alancads.wordpress.com/2012/08/22/compiling-gimp-2-8-0-in-ubuntu-10-04/](https://alancads.wordpress.com/2012/08/22/compiling-gimp-2-8-0-in-ubuntu-10-04/)

Maybe you could take a look at these and let me know what you think of them?

I know that you have spent a lot of time and effort working on this - I have seen your name around the interweb. 

If I can't manage to get this to work I am considering installing 12.04 alongside 10.04, because 10.04 is absolutely rock solid apart from Gimp. What do you think of this idea? Ingenious? Stupid?

Will let you know how my efforts work out. 

cheers man

---

### Post by jimstar79 on 2012-09-11
well, that was shortlived!

ran into the same problem as yesterday:

install: error: cannot install `libgthread-2.0.la' to a directory not ending in /home/star-12/Gimp/Gimp2.8/src/build/lib

---

### Post by jimstar79 on 2012-09-11
Shreepads [anybody], 

I followed all the instructions from the orginal work which you based yours on - and everything worked! Right up the important part at the end then I get this simple but obstructive piece of info:

./gimp-2.8.0: No such file or directory

How can it not have been created after everything I have already done?

Is there a quick fix to get around this as I have spent hours sitting here compiling the whole thing from source?

Any help will be really appreciated!

---

### Post by jimstar79 on 2012-09-11
Cyber High-Five, Shreepads, and a massive cybe hug!!!

Managed to get it working, had to rely a lot on what you made and the one from the original source!!

Now to give it a nice theme and a launcher!!

wonderful, thanks so much for your tutorial!!

ps: if you are seeing a lot of permission denied's coming up, one must go into gksu nautilus and change the permissions of the specific folders. Hope it's ok to make a suggestion like that? Should these folders then be resigned as Root?

---

### Post by jimstar79 on 2012-09-11
Apologies for hijacking this thread. 

I am stuck trying to create a launcher for Gimp 2.8. I have tried using the steps mentioned in the tutorial but it really doesn't seem to work. I've never had to create a launcher before!

Any tips on how to change the Gimp theme, it reminds me of my old photoshop running on Wine, apart from the great features that is!

Peace and Gimp everybody!

---

### Post by jimstar79 on 2012-09-11
Ok guys, 

(Working in Ubuntu 10.04)

this is what I have done to create a launcher.

It is different to Shreepads as I followed slighly different instructions which used /opt and /tmp folders. 

Here we go:

I created a text file with gedit and inserted the following:

#! /bin/sh
export LD_LIBRARY_PATH=/opt/Gimp/Gimp2.8/build/lib:$LD_LIBRARY_PATH 
/opt/gimp-2.8/bin/gimp-2.8
exit 0

and saved it as gimp28.sh in my home/user folder.

I then made this file executable by using chmod +x gimp28.sh

Following this I opened preferences > main menu > and created a new item

name: Gimp 2.8
Command: /opt/gimp-2.8/bin/gimp-2.8

You can also add an icon if you like. 

I hope this helps. 

Good night and good luck

Thanks again to shreepad and also andrea roscioli!!

---

### Post by shreepads on 2012-09-12
Excellent! Sorry I couldn't help when you were stuck earlier, was fiddling around in Precise trying to get shutdown working properly...

---

### Post by Bucky Ball on 2012-09-12
*Thread moved to **Tutorials & Tips**.*

---

### Post by jimstar79 on 2012-09-12
I'm back - because I am so excited about having Gimp 2.8 on Ubuntu 10.04 - to share what I did to change the theme of Gimp. I think it ends up looking like your systems theme. 

I used Andrea Roscioli's [slightly edited] method: 

" Since we use a different version of GTK + for gimp 2.8, gimp will look "ugly".

We will have to copy...

the engines of /usr/lib/gtk-2.0/2.10.0/engines to /opt/gimp-2.8/lib/gtk-2.0/2.10.0/engines

the theme from /usr/share/themes to / opt/gimp-2.8/share/themes theme

and icons that use of /usr/share/icons to /opt/gimp-2.8/share/icons."

For Roscioli's complet guide go here:

[https://rubensa.wordpress.com/2012/05/08/script-to-compile-and-install-gimp-2-8-on-ubuntu-10-04-lts-lucid/](https://rubensa.wordpress.com/2012/05/08/script-to-compile-and-install-gimp-2-8-on-ubuntu-10-04-lts-lucid/) 


Grazie!!

---

### Post by jimstar79 on 2012-09-12
> **shreepads said:**
> Excellent! Sorry I couldn't help when you were stuck earlier, was fiddling around in Precise trying to get shutdown working properly...

Man, I think you have done enough for me - thanks for your tutorial and link to Roscioli's work!

It is also possible to install G'mic for 2.8 on 10.04.

G'mic can be found here: [http://sourceforge.net/projects/gmic/files/](http://sourceforge.net/projects/gmic/files/) 
and installed in .gimp2-8/plug-ins in your home folder. (Using ctrl+h to reveal hidden folders).

You can also copy over all brushes, gradients, palettes, etc. from Gimp 2.6/2.7 folders into their corresponding folders in 2.8.

Which basically makes Gimp2.8 complete on my system now. 

I'm so happy!

---

### Post by Bucky Ball on 2012-09-12
This is all great. But why? Cos 10.04 is rock solid for you? Good that you'all have this working but 10.04 LTS will be out of support next April.

Anyone installed the getdeb repo? That will give you the latest regardless of what release you are using.

---

### Post by shreepads on 2012-09-12
> **Bucky Ball said:**
> This is all great. But why? Cos 10.04 is rock solid for you? Good that you'all have this working but 10.04 LTS will be out of support next April.


I'm sure everyone has heard/ said this many times on these forums, but Gnome 2 on 10.04 is very usable and rock stable as a Desktop. 

Ideally I would have moved to 12.04.1 by now, but Unity is definitely an acquired taste and many things are going wrong during my test drive currently in progress...

By Apr 2013 we'll all either learn to live with 12.04 (maybe by installing XFCE/ Cinnamon on top) or move off to another distro.

---

### Post by Bucky Ball on 2012-09-12
Understood. Can't stand Unity myself but have been an Xubuntu/Xfce fan for ages so not an issue. Currently Xubuntu 12.04 LTS but got into it with xfce4 as my DE on a regular Ubuntu 8.04 LTS install. Found I liked that better than Gnome (and definitely Unity).

---

### Post by Andrew_P on 2012-09-14
> **OGpmpdog said:**
> However, this tutorial seems to be a lot of work for software that will be at EOL in less than 1 year.

End of support is not the same as end of life:  Products can have useful life for many years after official support ends.  For example, I'm still running an old 150 MHz Pentium II machine with Windows 98SE on it for certain things where there is just no adequate replacement with later hardware and operating systems.

This is typical in both businesses and in government/military.  I've worked for suppliers to the military, and a 10-year useful life was both a design requirement and contractual requirement.  Sometimes so much effort is put into setting up and validating mission-critical systems that upgrading can't be justified until the old system can no longer be economically supported.

---

### Post by shreepads on 2012-09-22
Gimp 2.8.2 was released a little while back. 

From gimp.org
> Most notorious bugs fixed are: not being able to remember JPEG saving options, slow canvas redraw, not showing page setup options on Windows. There's also a workaround for the bug that used to cause showing incorrect file size values on Windows. For the complete list of changes please see the [NEWS]("http://git.gnome.org/browse/gimp/plain/NEWS?h=gimp-2-8") file.

To upgrade
- Download gimp-2.8.2.tar.bz2
- Copy to old 'src' directory (hope you didn't delete it!)
- Right-click, 'Extract Here'
- Open terminal

```

$ cd ~/Gimp/Gimp2.8/src/gimp-2.8.2

$ export PKG_CONFIG_PATH=/home/user/Gimp/Gimp2.8/build/lib/pkgconfig

$ export LD_LIBRARY_PATH=/home/user/Gimp/Gimp2.8/build/lib

$ ./configure --prefix=/home/user/Gimp/Gimp2.8/build

$ make -j3

$ make install -j3
```

That's it, your old shortcut to gimp 2.8.0 will now open 2.8.2

---

### Post by vermontbear on 2012-09-30
Thank you, thank you and thank you.  First to "shreepads" for his, pardon the pun, "Lucid" instructions on how to compile and install Gimp 2.8 on Ubuntu 10.04.  Second to "Bucky Ball" for his sly remark about not liking Unity. The gist of most of the comments on this forum tend toward reinforcing the party line. At one point I was wondering if Mark Shuttleworth had sent out some directive that nobody with forum authority would be allowed to contradict said party line. The conventional wisdom everywhere seems to be that "the desktop is dead." Yeah, well that can become a self-fulfilling prophesy. Or as John Luc Picard says, "Make it so."   For a rather large group of people in the world, it is not so, will not be so, should not be so.  Thirdly to Andrew_P for noting that products may have a useful life well after their "official" support ends. I mean, heck, I still use Lotus Ami Pro for the word processor of choice on "virtually" all my in-house Windows-based machines.  I joined this forum back in June of 2009.  Since I haven't logged in for "a while," I noted couple weeks back that I had been unceremoniously erased. Oh well. Re-join.  I've been working with Ubuntu systems since Dapper.  Probably the best experience I've had installing from beta and going forward was Hardy.  Lucid took two months after its release to settle down and fly right.  "Precise" (and I sometime shudder when I say that -- like what the heck is there in the release that even remotely may be categorized by the word, "precise?" I might think of it as the Atrocious Anteater, Noxious Numbat, Flukey Farrow, Erratic Echidna.. okay, you get the idea), has taken almost five months since the release to sort out difficulties.    I have to say that since we now have Serivce Pack 1 out (borrowing a phrase from Microsoft), the disto has settled down considerably.    I'm running two primary test installations, one with Mint/Mate, the other with Ubuntu/Mate.  I like the Compiz cube.  I like the Emerald Themes I have collected and tweaked over the years.  I'm a tad loathe to give all of it up for something that doesn't work properly. Lucid with Gnome 2 is indeed "rock solid." But I'm happy to say that Ubuntu 12.04.1 + Mate 1.4 is almost there. Three weeks back, it wasn't even close, but with the ton of updates Ubuntu has shoveled in since, the setup is pretty stable. Okay, it's very, very nearly "rock solid."   Mint/Mate lags behind, but that is to be expected.  I do want to thank whomever is responsible for shoring up the underpinnings of Ubuntu 12.04 so as not to sabotage a Gnome2 fork like Mate.  I appreciate the good work. So will a couple of my clients whose systems I will be updating next month. Keep it up (and don't screw it up).  I'm actually becoming guardedly optimistic.  VB

---

### Post by vermontbear on 2012-09-30
Love the way your online editor takes plain text and turns it into one blob of HTML even though HTML is supposedly turned off.  Ah well, it's a Microsoft thing.  We always know better than you do what you were trying to do, so we're going to change it.

Cheers.

---

### Post by I_can_see_the_light on 2012-11-01
Excellent thread! Regarding the online help, I found that you can copy the contents of ```
/usr/lib/gio/modules
``` into ```
/path/to/gimp2.8/build/lib/gio/modules
```

---

### Post by magicalplug on 2012-11-06
I've spent the best part of an afternoon trying to get this to work and just can't :(

Would someone be so kind as to provide a precompiled amd64 version of Gimp 2.8.2 that can be run on Lucid 64-bit?

I would be so grateful.

---

### Post by menth1979 on 2012-12-11
Thank you for the guide!
I have some minor issues though:
- If you have a tablet you have to configure gtk+ with --with-xinput option, anyway sometimes the input freezes and you have to raise the stylus for a sec in order to have the pointer back.
- For me it's impossible to open or save a JPEG file. It says "Wrong JPEG library version: library is 62, caller expects 80"

---

### Post by Bucky Ball on 2012-12-11
[B][I]Thread Closed

Reason:[/I][/B] Necromancy. Old thread put to bed. Please post a new thread with a descriptive title in the appropriate forum for the best chance of help rather than posting forty posts deep on an old thread. 

Not much chance of help here.

---

