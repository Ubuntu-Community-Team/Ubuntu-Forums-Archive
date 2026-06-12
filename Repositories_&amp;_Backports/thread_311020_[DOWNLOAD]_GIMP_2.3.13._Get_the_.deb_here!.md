---
title: "[DOWNLOAD] GIMP 2.3.13. Get the .deb here!"
date: 2006-12-02
forum: Repositories &amp; Backports
---

### Post by soc on 2006-12-02
**[COLOR="Red"]UPDATE: GIMP 2.3.16 available![/COLOR]**

**GIMP 2.3.16**
[INDENT]i386 (feisty, using madman's deb, thank you!)
[gimp-2.3_2.3.16-0madman2k1_i386.deb]("http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k1_i386.deb") MD5: 48944db4e6b180f1bde6feb7f5b1c754

amd64 (gutsy)
[gimp-2.3_2.3.16-1_amd64.deb]("http://www.pix-nw.de/_intern/soc/gimp-2.3_2.3.16-1_amd64.deb") MD5: 6974d02af6df26f5f4c8170e0020e7a8[/INDENT]

**Save-for-web plugin 0.9.0**
[INDENT]i386 (feisty)
[gimp-2.3-saveforweb_1:0.9.0-1_i386.deb]("http://pix-nw.de/_intern/soc/gimp-2.3-saveforweb_1:0.9.0-1_i386.deb")

amd64 (gutsy)
[gimp-2.3-saveforweb_1:0.9.0-1_amd64.deb]("http://pix-nw.de/_intern/soc/gimp-2.3-saveforweb_1:0.9.0-1_amd64.deb")[/INDENT]


It installs to /usr/local and won't overwrite your own installation of gimp 2.2. 
```
Building GIMP with prefix=/usr/local, datarootdir=${prefix}/share
Desktop files install into ${datarootdir}

Extra Binaries:
  gimp-console:        yes
  gimp-remote:         yes

Optional Features:
  D-Bus service:       yes

Optional Plug-Ins:
  Ascii Art:           no (AA library not found)
  Help Browser:        yes
  LCMS:                yes
  JPEG:                yes
  MNG:                 yes
  PDF:                 yes
  PNG:                 yes
  Print:               yes
  PSP:                 yes
  Python:              yes
  Script-Fu:           yes
  SVG:                 yes
  TIFF:                yes
  TWAIN (MacOS X):     no
  TWAIN (Win32):       no
  URI:                 yes (using gnome-vfs)
  Windows ICO          yes
  WMF:                 yes
  XJT:                 yes
  XPM:                 yes

Plug-In Features:
  EXIF support:        yes
  GNOME UI:            yes
  GNOME keyring:       yes

Optional Modules:
  ALSA (MIDI Input):   yes
  Linux Input:         yes (HAL support: yes)
  DirectInput (Win32): no
  Color Correction:    yes
  Soft Proof:          yes
```
I plan to build debs of gimp 2.3 for all future releases until version 2.4 is added to ubuntu, so stay tuned!

Please leave a comment!

bye
soc

If you get this error:```
This is a development version of GIMP.  Debug messages may appear here.
/usr/local/lib/gimp/2.0/plug-ins/webexport: error while loading shared libraries: libgimpconfig-2.0.so.0: cannot open shared object file: No such file or directory
```
Do the following to be able to use the Save-for-web plug-in:
```
sudo gedit /usr/local/bin/gimp-2.3.sh
```
Insert the following into the file:
```
PATH=/usr/local/bin:$PATH
export PATH
LD_LIBRARY_PATH=/usr/local/lib
export LD_LIBRARY_PATH
/usr/local/bin/gimp-2.3
```
Make gimp-2.3.sh executable and correct your menu-entry so that it points to /usr/local/bin/gimp-2.3.sh instead of /usr/local/bin/gimp-2.3.

That's it!

---

### Post by hikaricore on 2006-12-03
New splash screen is a plus.  =)

But what in the hell did they do to the icons?  It looks like KDE and BeOS had a baby iconset and named it Gimp.  Rofl.

Thanks for releasing this tho. :)

---

### Post by d3v1ant_0n3 on 2006-12-03
I tried building the newest build a week or so ago (2.3.13-7?) and it was unstable as hell. Never could be bothered building an older version. Really should have done. Loving some of the new filters etc. But dang, why no colors tab when you use brushes???

*EDIT* Sorry, forgot to say thanks.

THANK YOU!!!!:D:D:D

---

### Post by The Warlock on 2006-12-04
Cool, but can you make an x86_64 package?

---

### Post by wito123 on 2006-12-06
Hello,

I'm a spnaish Dapper User. I'd like to obtain an ubuntu dapper version of gimp 2.3.13. Will be posible?. I'm very interesting in the new color managements in gimp and gimp 2.3.13 have move one step more...

I have a web dedicated to Digital Photo (**[http://www.fotografiadigitalenlinux.com](http://www.fotografiadigitalenlinux.com)**)... in spanish. I've explain howto configure an ubuntu/linux machine for profesional photographers.

I've linked this page in it for Edgy users.

Thank's

---

### Post by JMO707 on 2006-12-19
Just what I was looking for. Thanks! =)

---

### Post by hikaricore on 2006-12-20
> **d3v1ant_0n3 said:**
> why no colors tab when you use brushes???


Aside from being afraid of the new buttons this is one of the things stopping me from using this version.  Color tabs are needed, I'm guessing this has something to do with the way this version was compiled?  Or it could just be a bug.

---

### Post by slimdog360 on 2006-12-23
cheers big ears

---

### Post by iceberg on 2006-12-27
Hello,

Thanks you very much for the package. God job.

---

### Post by tshirtz1013 on 2006-12-31
Failed to execute child process "gimp-remote-2.3" (File or directory could not be found)


-- I think it's great someone made a deb of this. But this is my problem when trying to run Gimp from the menu. Any suggestions ? all i did was install the package via the installer.

](*,)

---

### Post by _simon_ on 2006-12-31
> **tshirtz1013 said:**
> Failed to execute child process "gimp-remote-2.3" (File or directory could not be found)


-- I think it's great someone made a deb of this. But this is my problem when trying to run Gimp from the menu. Any suggestions ? all i did was install the package via the installer.

](*,)

I had that problem.

Point it at "gimp-2.3" instead.

---

### Post by Hairy_Palms on 2006-12-31
> **hikaricore said:**
> Aside from being afraid of the new buttons this is one of the things stopping me from using this version.  Color tabs are needed, I'm guessing this has something to do with the way this version was compiled?  Or it could just be a bug.

to sort this go to 
File->Preferances->Toolbox and tick the show background and foreground colours box

ive been using 2.3.13 since it came out and i personally prefer it the new way with a seperate colours box.
means i can put it in the other toolbox like this :)
[http://four.fsphost.com/hairypalms/gimp.png](http://four.fsphost.com/hairypalms/gimp.png)

and the new icon theme is tango, much more attractive than the old theme imo

---

### Post by _simon_ on 2007-01-03
Noticed something annoying, but not sure how to fix it.

With 2.2 if I right click on images and open with Gimp then they all open with one instance of Gimp. (This is opening one image at a time)

With 2.3 they all open in their own instance of Gimp. So if I open 3 images one at a time then I get 3 instances of Gimp running. If I select 3 images and open them in one go then they do open in one instance.

Is this something I've done wrong or is it because 2.3 isn't the final build?

Edit: Found the problem, it's the lack of gimp-remote.

Is this something you could build into your deb or is it not available?

---

### Post by justin_c18 on 2007-01-05
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by gimp-2.3)
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/lib/libgimpwidgets-2.0.so.0)
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/lib/libgimpthumb-2.0.so.0)
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/lib/libgimpmath-2.0.so.0)
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/lib/libgimpconfig-2.0.so.0)
gimp-2.3: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/lib/libgimpbase-2.0.so.0)


Never had this happen before, especially with a .deb since it resolves all depencies...
I can't find glibc 2.4 in the repos, only documentation, which is weird.

Any help would be appreciative.
Thanks, J

---

### Post by soc on 2007-01-24
I just uploaded gimp 2.3.14 deb-packages for i386 (edgy) and amd64 (feisty).

Have fun!

---

### Post by disturbedite on 2007-01-25
hi.  first post everyone.  i've been a member of the kubuntu forum for a while now, but thought i'd register here too.

anyway, i *don't* use gimp 2.2. so my question is, given that you've provided a deb package (thanks *SO *much btw) can i "redirect" gimp 2.3 to install where 2.2 (default) would normally install?  (i don't want to compile 2.3 since you've already done that).

i've created deb packages with checkinstall before, (as a matter of fact i maintain the ksmoothdock deb package), so i know how that works.

would it be possible to redirect gimp 2.3 to install in the default path(s) with checkinstall?

or would it be as simple as extracting the data package and renaming the folder structure then putting it back in the deb package?

---

### Post by iGama on 2007-01-25
Thanks for the update :)

---

### Post by iceberg on 2007-01-26
Thanks a lot SOC ! ;)

---

### Post by P_Badger on 2007-01-26
Thanks for 2.3.14, always appreciated, eh!

---

### Post by soc on 2007-01-27
@disturbedite

As far as I can tell, you will have to append an argument to ./configure to change the path.
That's it!

But I really don't understand why you want to break the FHS conventions?
What's the matter with /usr/local/?

---

### Post by disturbedite on 2007-01-27
> **soc said:**
> @disturbedite

As far as I can tell, you will have to append an argument to ./configure to change the path.
That's it!

But I really don't understand why you want to break the FHS conventions?
What's the matter with /usr/local/?

i said that i don't use gimp 2.2 and i thought you said it normally installed in a different place.  so i wanted 2.3 to install where 2.2. normally does.

please excuse my ignorance, but what is the fhs convention?  something to do with file structures?

if gimp 2.2 also installs in the same place, then just disregard my question, obviously...

---

### Post by MadMan2k on 2007-01-28
> **disturbedite said:**
> i said that i don't use gimp 2.2 and i thought you said it normally installed in a different place.  so i wanted 2.3 to install where 2.2. normally does.
this is possible, but it requires some work for the packager. I will look what I can do.

---

### Post by disturbedite on 2007-01-28
> **MadMan2k said:**
> this is possible, but it requires some work for the packager. I will look what I can do.

i'll take that as a yes to the question of whether or not 2.3.x installs in a different place than 2.2.x.

thanks so much btw!

EDIT:  @madman2k
is the deb package of 2.3.14 on your website this "modified" version you mentioned?
btw, i grabbed your deb package of zsnes 1.5, thanks!  version 1.51 has been released today. could you make a package of that please?  if you can, thanks!

---

### Post by rev_b on 2007-02-03
Very nice and flawless install, but how to integrate Xane in File -> Acquire as in 2.2?
Thanks.

---

### Post by gummibaerchen on 2007-02-05
Nice package, thanks :)

---

### Post by ayoli on 2007-02-12
i've grabbed it, thx to packager :)

---

### Post by MadMan2k on 2007-02-12
> **disturbedite said:**
> 
EDIT:  @madman2k
is the deb package of 2.3.14 on your website this "modified" version you mentioned?
btw, i grabbed your deb package of zsnes 1.5, thanks!  version 1.51 has been released today. could you make a package of that please?  if you can, thanks!
sry, for teh late reply - I've just seen that thread again...

my gimp 2.3.14 packages are pretty much the same like in this thread, except that they have some more features enabled...

here is zsnes 1.51: (feisty)
[http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb](http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb)

---

### Post by disturbedite on 2007-02-12
> **MadMan2k said:**
> sry, for teh late reply - I've just seen that thread again...

my gimp 2.3.14 packages are pretty much the same like in this thread, except that they have some more features enabled...

here is zsnes 1.51: (feisty)
[http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb](http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb)


so i noticed...i installed gimp 2.3.14 and zsnes 1.51 from your site.  i think i found it (since it wasn't posted on your home page) by changing the filename in the url.  thanks again!

---

### Post by el_itur on 2007-02-14
Great work. Just a request.
Could you pack the next relase (.15?) with save for web plugin
[http://registry.gimp.org/plugin?id=8799](http://registry.gimp.org/plugin?id=8799)

I'll love to have it but I'm to lazy to compile it myself, and since you are on the ride... :)

Again great work. There are so much things that I love of this version.

---

### Post by handaxe on 2007-02-25
thanks,

HA

---

### Post by Julz_ET on 2007-03-04
Makes my life easier, always wanted to try the dev release.

Thank You!:)

---

### Post by soc on 2007-03-10
OK, here we go:
I'm just uploading i386 and amd64 DEBs of GIMP 2.3.15, you should see the updated links in the first post in a few minutes :guitar:

---

### Post by MadMan2k on 2007-03-10
damn - you are always faster than me ^^

are you still building the packages with checkinstall? Since I like standard debian packages more I could give you my deb-sources so I wont have to complie it myself next time...

---

### Post by handaxe on 2007-03-10
Hi Soc,

Thanks for the contributions...

Server not playing nice - won't let me grab the file

HA

---

### Post by ayoli on 2007-03-11
2.3.15 version + save for the web plugin works nice, thanks for your contrib :)

---

### Post by soc on 2007-03-12
> **handaxe said:**
> Hi Soc,

Thanks for the contributions...

Server not playing nice - won't let me grab the file

HA

I fixed that, the file permissions were not set properly on the server.

Have fun!

---

### Post by -Syaoran- on 2007-03-12
When I start to download and it says open i click and its just goes back to open and it goes on and on how do I fix that?

---

### Post by handaxe on 2007-03-12
Does right mouse click, "save link as" give the same result?

HA

---

### Post by disturbedite on 2007-03-12
w00t!  thanks again for the update!  i didn't expect to find it this soon.

---

### Post by ernstblaauw on 2007-03-13
Thanks for the deb! 2.3.14 installed perfectly. However, when I try to install 2.3.15, I get the following error:
```
(Reading database ... 181571 files and directories currently installed.)
Preparing to replace gimp-2.3 2.3.14-1 (using .../gimp-2.3_2.3.15-1_i386.deb) ...
Unpacking replacement gimp-2.3 ...
dpkg: error processing /home/ernstblaauw/Desktop/Freeware-Linux/gimp-2.3_2.3.15-1_i386.deb (--install):
 trying to overwrite `/usr/lib/python2.4/site.pyo', which is also in package rhythmbox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```
Does someone know how to solve this problem? For the record, I installed Rhythmbox 0.9.8 by myself.

---

### Post by disturbedite on 2007-03-14
maybe try updating to python2.5?

---

### Post by ernstblaauw on 2007-03-18
I already got python2.5 installed (and also python2.4). I cannot remove python2.4; a lot of packages depend on them. I tried removing python2.5, but then, I get the same error message.
This means, I still did not succeed installing the latest GIMP :-(. Has anyone another tip or trick?

---

### Post by ilbozo on 2007-03-19
the feisty 64bit package works on edgy amd64 too

---

### Post by ayoli on 2007-03-20
> **ernstblaauw said:**
> I already got python2.5 installed (and also python2.4). I cannot remove python2.4; a lot of packages depend on them. I tried removing python2.5, but then, I get the same error message.
This means, I still did not succeed installing the latest GIMP :-(. Has anyone another tip or trick?
maybe you can try:
```
sudo dpkg -i gimp-2.3_2.3.15-1_i386.deb --force-all
```

---

### Post by ernstblaauw on 2007-03-21
> **ayoli said:**
> maybe you can try:
```
sudo dpkg -i gimp-2.3_2.3.15-1_i386.deb --force-all
```

That didn't work: I got the same error.  I had to change the command:
```
sudo dpkg -i --force-all gimp-2.3_2.3.15-1_i386.deb
```
Now, --force-all is at the correct place. It installed fine (of course, dpkg gave a warning. But as --force-all was enabled, it just continued installing). Thanks for your help!

---

### Post by ayoli on 2007-03-21
> **ernstblaauw said:**
> That didn't work: I got the same error.  I had to change the command:
```
sudo dpkg -i --force-all gimp-2.3_2.3.15-1_i386.deb
```
Now, --force-all is at the correct place. It installed fine (of course, dpkg gave a warning. But as --force-all was enabled, it just continued installing). Thanks for your help!
sorry for the wrong order, the force-all overwrote your site.pyo that was also installed by your self-made rythmbox package.
actually, a --force-overwrite would have been sufficient.

---

### Post by Patrick Urs on 2007-04-08
Thank you very much!

I've been meaning to download the source for a long time, and now I finally found a .deb!

And I'm glad that they finally intergrated the tango! icons.

---

### Post by IanW on 2007-04-09
FYI the ["gimp-2.3-saveforweb_1:0.2-1_i386.deb"]("http://pix-nw.de/_intern/soc/gimp-2.3-saveforweb_1:0.2-1_i386.deb") link in the first post is invalid. The good news is that your web server lands the user in the parent directory where I was able to select the current version instead ([gimp-2.3-saveforweb_1:0.8.1-1_i386.deb]("http://pix-nw.de/_intern/soc/gimp-2.3-saveforweb_1:0.8.1-1_i386.deb"))

---

### Post by neilrizo on 2007-04-09
I just installed 2.3.15 and it shows on the menu as "GNU Image Manipulation Program". As soon as I click on that a "Starting GNU Manipulation Program" notice appears but disappears soon after without loading the program.

What gives? I'm an ubuntu newbie, so I hope someone can help me with this.

Thanks.

---

### Post by freaks on 2007-04-17
hello,
i downloaded and installed gimp but i have this error, what can i do ?
nevertheless if i type : sudo gimp it's ok
```
 gimp

(gimp:6192): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:6192): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:6192): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:6192): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:6192): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:6192): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:6192): GLib-GObject-WARNING **: cannot register existing type `GimpParamRGB'

(gimp:6192): GLib-GObject-CRITICAL **: g_param_spec_internal: assertion `G_TYPE_IS_PARAM (param_type) && param_type != G_TYPE_PARAM' failed
Erreur de segmentation (core dumped)
gael@psylocke:~/Desktop$ sudo gimp
executable not found: '/usr/lib/gimp/2.0/plug-ins/ufraw-gimp'
executable not found: '/usr/lib/gimp/2.0/plug-ins/print'



```

---

### Post by QUASAR_FREAK on 2007-04-22
I just installed in feisty 32bits and works like a charm

Thank you for maintain this debs!!

---

### Post by PingunZ on 2007-04-23
Can you make a feisty x86 deb ?

Edit: my mistake, gimp 2.3 just isn't working yet here ( tried building from source .. )

Cheers

---

### Post by QUASAR_FREAK on 2007-04-23
> **PingunZ said:**
> Can you make a feisty x86 deb ?

Edit: my mistake, gimp 2.3 just isn't working yet here ( tried building from source .. )

Cheers

the edgy version worked for me in feisty too. try it.

---

### Post by eewald on 2007-04-25
can anybody please make GIMP 2.3.16 deb for download?

---

### Post by MadMan2k on 2007-04-25
[http://www.madman2k.net/comments/74](http://www.madman2k.net/comments/74)

---

### Post by ernstblaauw on 2007-04-26
> **MadMan2k said:**
> [http://www.madman2k.net/comments/74](http://www.madman2k.net/comments/74)

I'll wait for the AMD64 version, or is that one also available on your website?

---

### Post by episodic on 2007-04-26
It installed without a hitch. The only problem is where do I find it? I installed the new .16 version. It isn't under the menu at all???

Thanks so much for helping me find how to launch it.

---

### Post by soc on 2007-04-27
2.3.16 is available for am64, but it fails to build for i386 currently.
While I'm trying to fix that, use madman's package instead.

The amd64 package was built on gutsy, hope that won't cause problems ...


@MadMan2k:
Did you have problems building GIMP 2.3.16 on i386?

---

### Post by MadMan2k on 2007-04-27
no, it built cleanly. just wanted to have pygtk-dev over 2.3.15.

---

### Post by soc on 2007-04-28
Ok, can't figure out, why it doesn't work ...

May I link to your i386-Package on the front page or do you have only limited traffic?

---

### Post by MadMan2k on 2007-04-29
its hosted externally, so you are free to link it. :)

---

### Post by episodic on 2007-05-01
Hey there!

Thanks for the package. I filed a bug report with the gimp developers on your 2.3.16 build due to getting errors when opening certain jpegs with certain color profiles. Here was the response. It was evidently a build error - I thought you'd be interested. I have no clue how to fix it unfortuantly, but I thought I'd help this much. The error isn't a show stopper - just an annoyance.

Here is what the gimp dev said:


Sven Neumann changed:

           What    |Removed                     |Added
----------------------------------------------------------------------------
             Status|UNCONFIRMED                 |NEW
          Component|General                     |Plugins
     Ever Confirmed|0                           |1




------- Comment #1 from Sven Neumann  2007-05-01 21:12 UTC -------
You have built GIMP without the lcms plug-in. Well, we should probably handle
this case better and only display an error dialog once, if at all.



I looked in the apt repository and found the lcms plugin and dev code. I'm guessing if you got this package from synaptic and then built it this would not be a problem? I don't know. Anyway thanks!

---

### Post by soc on 2007-05-02
Which package was it?
Madman's or the one from me?

If it's the one I built it's a build-error for sure, because I enabled lcms when configuring ...

---

### Post by episodic on 2007-05-03
It was the package at the start of this thread.

---

### Post by mrgnash on 2007-05-05
Thanks! These development versions are great. I love that 16 **finally** allows you to scale brushes _up_ :popcorn:

---

### Post by MadMan2k on 2007-05-05
just looked at the build-log: it must ahve been my package - Im rebuilding it right now.

done rebuilding:
[http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k2_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k2_i386.deb)

---

### Post by redforce on 2007-05-05
Thanks for the packages! We have linked to them from [http://www.gimpusers.com/gimp-download.php](http://www.gimpusers.com/gimp-download.php)

---

### Post by episodic on 2007-05-05
> **MadMan2k said:**
> just looked at the build-log: it must ahve been my package - Im rebuilding it right now.

done rebuilding:
[http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k2_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.16-0madman2k2_i386.deb)

Hey guy - it is perfect now - much thanks and mad props!

---

### Post by Kevin_Jim on 2007-05-07
I'm getting this whenever i try to launch GIMP 2.3

> (gimp:5939): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:5939): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:5939): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:5939): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:5939): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:5939): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:5939): GLib-GObject-WARNING **: cannot register existing type `GimpParamRGB'

(gimp:5939): GLib-GObject-CRITICAL **: g_param_spec_internal: assertion `G_TYPE_IS_PARAM (param_type) && param_type != G_TYPE_PARAM' failed
Segmentation fault (core dumped)

---

### Post by Lucifiel on 2007-05-13
Hmmm... upon recommendation of another user, I installed Gimp 2.3.13 but it's a little sluggish on my pc. It takes about 3 to 4 seconds for certain options to respond, for certain windows to appear.

Any idea how to optimise it(without compiling and such since I'm a Linux newbie)? :) 

Otherwise, I guess I'll try and compile the deb for 2.2.14 since 2.2.13 keeps crashing whenever I save in .psd format.

Edit: Oh, I have 1 gb of ram and a AMD 64 3000+ processor.

---

### Post by adamJ5 on 2007-05-19
BUMPIDY! :) Could someone direct me to the Edgy .deb's? As usual, the libatk-1.0-0 dependency is missed in the Feisty .deb.


Thanks SOC

---

### Post by konungursvia on 2007-05-19
And what about dapper? Everything in GIMP ought to run here...  any debs that will work for us stability freaks?

---

### Post by MadMan2k on 2007-05-20
why would a stability freak want to use an unstable development version from an "untrusted" source?

---

### Post by ernstblaauw on 2007-05-28
2.3.17 has been released.
Download: [ftp://ftp.gimp.org/pub/gimp/v2.3/](ftp://ftp.gimp.org/pub/gimp/v2.3/)
Changelog:
> Changes in GIMP 2.3.17:
[list]   improved import of multi-page TIFF files
    [*] reduced rounding errors in Blur routines (core and plug-ins)
    [*] further improved parameter checks in the PDB
    [*] added support for loading .abr v2 Photoshop brushes
    [*] improved border behavior of the Blur tool
    [*] show the brush outline at the Clone tool's source position
    [*] added libgimpbase API to retrieve the user's Pictures folder
    [*] add a shortcut to the user's Pictures folder to the file-chooser dialog
    [*] improved the quality of the Motion Blur filter
    [*] save paths in TIFF files
    [*] let the Screenshot plug-in name the new layer after the window
    [*] use memory slices to reduce memory fragmentation
    [*] some code cleanup
    [*] lots of bug fixes[/list]

---

### Post by soc on 2007-05-28
2.3.17 seems to be quite buggy, so it's not sure at the moment if it will be worth the hassle ..

---

### Post by FerBatista on 2007-05-30
I've been trying the 2.3.16 but I'm having a problem with the color managent, it tells me there's a plugin (plugin-icc-profilie-aplly-rgb) missing. Where can I get this plugin?

BTW thanks for making this deb.

---

### Post by el_itur on 2007-05-30
> **FerBatista said:**
> I've been trying the 2.3.16 but I'm having a problem with the color managent, it tells me there's a plugin (plugin-icc-profilie-aplly-rgb) missing. Where can I get this plugin?

BTW thanks for making this deb.


Talking about color profiles, I was wandering trhough this-version-gimp's preference dialog and I've something I think is interesting (see screenie attached).
But anyhow. I con't manage to found a single icc file on my machine. Do you know how to use this feature?

---

### Post by ahmed_d on 2007-06-03
thanks man

---

### Post by P_Badger on 2007-06-08
Oo boy, 2.3.17 is the buggiest and most unstable release they've had in a while. I had to go back to 2.3.16 'cause gimp was crashing almost as often as Pixel image editor.

I hope 2.3.18 isn't as messed up.

---

### Post by CarpKing on 2007-06-12
GIMP 2.3.18 is out, and it seems they've fixed the bug from the last release.

---

### Post by kanamor on 2007-06-12
Hello, I have compiled the last version of Gimp, the 2.3.18, I have it installed in my pc thanks al make install, but after creating the package deb, me does not leave to install it. the error that gives is me: (in spanish sorry)

dpkg: error al procesar gimp_2.3.18-1_i386.deb (--install):
intentando sobreescribir `/usr/bin/strip', que está también en el paquete binutils
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
gimp_2.3.18-1_i386.deb

and sorry my bad English :-p 



Here I put you the link so that discharge it

[gimp_2.3.18-1_i386.deb](http://www.mediafire.com/?cjydxgmyj2y)

---

### Post by el_itur on 2007-06-12
> **kanamor said:**
> Hello, I have compiled the last version of Gimp, the 2.3.18, I have it installed in my pc thanks al make install, but after creating the package deb, me does not leave to install it. the error that gives is me: (in spanish sorry)

dpkg: error al procesar gimp_2.3.18-1_i386.deb (--install):
intentando sobreescribir `/usr/bin/strip', que está también en el paquete binutils
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
gimp_2.3.18-1_i386.deb

and sorry my bad English :-p 



Here I put you the link so that discharge it

[gimp_2.3.18-1_i386.deb](http://www.mediafire.com/?cjydxgmyj2y)

agregale el flag -f a la linea de dpkg. te quedará una cosa como:

$ sudo dpkg -f -i gimp_2.3.18-1_i386.deb

eso va a pisar cualquier configuración.

Suerte.

---

### Post by kanamor on 2007-06-12
muchas gracias el_itur, lo probaré.

---

### Post by el_itur on 2007-06-12
[offtopic]I realize later what I've done. Sorry to all of you. It was easier for me to respond him in Spanish, and for him to understand I think ;).[/offtopic]

---

### Post by ernstblaauw on 2007-06-15
Is the 64-bit build already available?

---

### Post by soc on 2007-06-15
It seems checkinstall was broken some time ago in Ubuntu ...
If kanamor would give me the details of his error, O could confirm that it's the same problem.

I'm looking into dh_make/debuild/pbuilder to provide deb-packages, but 2.3.18 won't compile on both gutsy/amd64 and feisty/i386 beacuse of a problem in pygimp. I have already spoken to the devs on #gimp, but by now we don't have a solution yet.

Currently I'm downloading the latest source from SVN and hope that it was a bug in GIMP and not in Ubuntu.

Stay tuned.

---

### Post by disturbedite on 2007-06-16
> **soc said:**
> It seems checkinstall was broken some time ago in Ubuntu ...
I'm looking into dh_make/debuild/pbuilder to provide deb-packages.

if you are able to debianize the source (assuming its not already), you could use the ```
dpkg-buildpackage -rfakeroot
``` method as well.

---

### Post by P_Badger on 2007-06-19
Since Madman2k hasn't posted a link here to Gimp 2.3.18 that he packaged and put up on his site, I figured I'd do it for him. ; ) I downloaded it yesterday, and so far it seems to work quite well. Thanks Madman!

[http://uploader.polorix.net//files/140/gimp-2.3_2.3.18-0madman2k1_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.18-0madman2k1_i386.deb)

---

### Post by ernstblaauw on 2007-06-19
> **P_Badger said:**
> Since Madman2k hasn't posted a link here to Gimp 2.3.18 that he packaged and put up on his site, I figured I'd do it for him. ; ) I downloaded it yesterday, and so far it seems to work quite well. Thanks Madman!

[http://uploader.polorix.net//files/140/gimp-2.3_2.3.18-0madman2k1_i386.deb](http://uploader.polorix.net//files/140/gimp-2.3_2.3.18-0madman2k1_i386.deb)

Do you also got the 64-bit version for us? :KS

---

### Post by P_Badger on 2007-06-19
> **ernstblaauw said:**
> Do you also got the 64-bit version for us? :KS

Erf, you'd have to ask one of the regular packagers, I'm just reposting what I've found.

---

### Post by mrfreddy on 2007-07-25
Gimp 2.3.19 is out at the ftp repository. I'd compile it but configure wants 
something later than Feisty unfortunately.

> checking for GTK+ - version >= 2.10.13... no

---

### Post by mrgnash on 2007-07-30
Yes, that's a real shame :( I was excited to trial it.

---

### Post by Smabbage on 2007-08-01
I agree.  If anyone has a compiled .deb of the new GIMP 2.3.19 please post a link.  We would love to try it out.  Thanks.

---

### Post by henriquemaia on 2007-08-02
> **Smabbage said:**
> I agree.  If anyone has a compiled .deb of the new GIMP 2.3.19 please post a link.  We would love to try it out.  Thanks.

I second this request. I would love to try the new version.

EDIT: I have installed version 2.3.16 and it&#8217;s running great. Thanks for that.

---

### Post by Evgeny on 2007-08-04
> **Smabbage said:**
> I agree.  If anyone has a compiled .deb of the new GIMP 2.3.19 please post a link.  We would love to try it out.  Thanks.

check on this: [buzz.ulx.ru/gimp.html]("http://buzz.ulx.ru/gimp.html")
gimp 2.3.19 and necessary libraries

---

### Post by ragingmon on 2007-08-11
hi.. anyone here have the Gimp 2.3.15 deb package for edgy?

I lost my deb package and can't find any Gimp 2.3.x deb package for edgy over the net.

---

### Post by kanamor on 2007-08-16
```
Building GIMP with prefix=/usr/local, datarootdir=${prefix}/share

Desktop files install into ${datarootdir}



Extra Binaries:

  gimp-console:        yes

  gimp-remote:         yes



Optional Features:

  D-Bus service:       yes



Optional Plug-Ins:

  Ascii Art:           yes

  Help Browser:        yes

  LCMS:                yes

  JPEG:                yes

  MNG:                 yes

  PDF:                 yes

  PNG:                 yes

  Print:               yes

  PSP:                 yes

  Python:              yes

  Script-Fu:           yes

  SVG:                 yes

  TIFF:                yes

  TWAIN (MacOS X):     no

  TWAIN (Win32):       no

  URI:                 yes (using gnome-vfs)

  Windows ICO          yes

  WMF:                 yes

  XJT:                 yes

  XPM:                 yes



Plug-In Features:

  EXIF support:        yes

  GNOME UI:            yes

  GNOME keyring:       yes



Optional Modules:

  ALSA (MIDI Input):   yes

  Linux Input:         yes (HAL support: yes)

  DirectInput (Win32): no

  Color Correction:    yes

  Soft Proof:          yes

```



[gimp-2.4.0_rc1-1_i386.deb](http://www.mediafire.com/?11dxnzdfo90)

---

### Post by ernstblaauw on 2007-08-16
Do you've got a 64-bit deb?

---

### Post by ragingmon on 2007-08-16
> **kanamor said:**
> 
[gimp-2.4.0_rc1-1_i386.deb](http://www.mediafire.com/?11dxnzdfo90)

I tried to install this on Ubuntu Edgy.

It says "All dependencies are satisfied" 
and when I install 
```
rage@rage:~/Desktop$ sudo dpkg -i gimp-2.4.0_rc1-1_i386.deb
(Reading database ... 121473 files and directories currently installed.)
Unpacking gimp-2.4.0 (from gimp-2.4.0_rc1-1_i386.deb) ...
dpkg: error processing gimp-2.4.0_rc1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/strip', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gimp-2.4.0_rc1-1_i386.deb
```

any help about this?

---

### Post by rev_b on 2007-08-17
> **ragingmon said:**
> I tried to install this on Ubuntu Edgy.

It says "All dependencies are satisfied" 
and when I install 
```
rage@rage:~/Desktop$ sudo dpkg -i gimp-2.4.0_rc1-1_i386.deb
(Reading database ... 121473 files and directories currently installed.)
Unpacking gimp-2.4.0 (from gimp-2.4.0_rc1-1_i386.deb) ...
dpkg: error processing gimp-2.4.0_rc1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/strip', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gimp-2.4.0_rc1-1_i386.deb
```

any help about this?

It happens here, also.

---

### Post by rev_b on 2007-08-17
Ok, I managed to install it using:

$ sudo dpkg -i --force-overwrite *.deb

But it still won't launch because it complains about Gtk+ too old.
I'll try to install Gtk+ 2.11 from [ftp://ftp.gimp.org/pub/gtk/2.11/](ftp://ftp.gimp.org/pub/gtk/2.11/)

---

### Post by kanamor on 2007-08-17
Oki, sorry all, i am packaging again the program, as soon as have I put him the new link.

---

### Post by kanamor on 2007-08-17
Here it is the final one, I expect that function well.

md5   76b08dd3ada4982b634029365f2790ec

[gimp_2.4.0-rc1-1_i386.deb](http://www.mediafire.com/?701hcxezxl5)

---

### Post by Tyl3r on 2007-08-17
Did you compile it on Gutsy?
Cause I know it can't be compiled on Feisty because it needs an updated version of gtk.

---

### Post by disturbedite on 2007-08-17
(the package in the post above) won't work on gutsy cuz of a dependency issue, but i grabbed the appropriate dependency and it won't install either:

disturbedite@disturbedite-desktop:~$ sudo dpkg -i '/mnt/storage/linuxsoftware/gimp_2.4.0-rc1-1_i386.deb'
(Reading database ... 320335 files and directories currently installed.)
Preparing to replace gimp 2.3.18-1ubuntu2 (using .../gimp_2.4.0-rc1-1_i386.deb) ...
Unpacking replacement gimp ...
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on libpoppler1-glib (>= 0.5.1); however:
  Package libpoppler1-glib is not installed.
dpkg: error processing gimp (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimp
disturbedite@disturbedite-desktop:~$ sudo dpkg -i '/mnt/storage/linuxsoftware/libpoppler1-glib_0.5.4-0ubuntu8.1_i386.deb'
Selecting previously deselected package libpoppler1-glib.
dpkg: regarding .../libpoppler1-glib_0.5.4-0ubuntu8.1_i386.deb containing libpoppler1-glib:
 libpoppler-glib1 conflicts with libpoppler1-glib
  libpoppler1-glib (version 0.5.4-0ubuntu8.1) is to be installed.
dpkg: error processing /mnt/storage/linuxsoftware/libpoppler1-glib_0.5.4-0ubuntu8.1_i386.deb (--install):
 conflicting packages - not installing libpoppler1-glib
Errors were encountered while processing:
 /mnt/storage/linuxsoftware/libpoppler1-glib_0.5.4-0ubuntu8.1_i386.deb

one gets the same exact problem when trying to install okular on gutsy (without kde4 installed apparently).  okular depends on *libpoppler1-qt4* but apparently something in kde3 (maybe kde3 itself) requires *libpoppler-qt4* and they conflict with eachother...

---

### Post by kanamor on 2007-08-17
> **Tyl3r said:**
> Did you compile it on Gutsy?
Cause I know it can't be compiled on Feisty because it needs an updated version of gtk.

Hello Tyl3r, no, im compile in Feisty, but with the last GTK version.

Right now I am packaging it again so that ask not dependences.  I am going to sleep already, that are the 05:10 (Madrid), when awake I put me the new package to see if functions you. 
sorry for my English 

Greetings

---

### Post by ragingmon on 2007-08-17
I'm using edgy. 

[COLOR="Red"]Error: Dependency is not satisfiable: libasound2[/COLOR]
```
rage@rage:~/Desktop$ sudo dpkg -i gimp_2.4.0-rc1-1_i386.deb
Password:
dpkg: status database area is locked by another process
rage@rage:~/Desktop$ sudo dpkg -i gimp_2.4.0-rc1-1_i386.deb
(Reading database ... 121466 files and directories currently installed.)
Preparing to replace gimp 2.2.13-1ubuntu3.3 (using gimp_2.4.0-rc1-1_i386.deb) ...
Unpacking replacement gimp ...
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on libasound2 (>> 1.0.12); however:
  Version of libasound2 on system is 1.0.11-7ubuntu3.
 gimp depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 gimp depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 gimp depends on libcairo2 (>= 1.4.0); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 gimp depends on libdbus-1-3 (>= 0.94); however:
  Version of libdbus-1-3 on system is 0.93-0ubuntu3.1.
 gimp depends on libdbus-glib-1-2 (>= 0.73); however:
  Version of libdbus-glib-1-2 on system is 0.71-1ubuntu1.
 gimp depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 gimp depends on libfreetype6 (>= 2.3.5); however:
  Version of libfreetype6 on system is 2.2.1-5ubuntu0.2.
 gimp depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 gimp depends on libgnome-keyring0 (>= 0.7.1); however:
  Version of libgnome-keyring0 on system is 0.6.0-0ubuntu2.
 gimp depends on libgnomeui-0 (>= 2.17.1); however:
  Version of libgnomeui-0 on system is 2.16.1-0ubuntu2.
 gimp depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Version of libgnomevfs2-0 on system is 2.16.1-0ubuntu7.
 gimp depends on libgtkhtml2-0 (>= 2.11.0+svn20061107); however:
  Version of libgtkhtml2-0 on system is 2.11.0-1build1.
 gimp depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 gimp depends on libpng12-0 (>= 1.2.13-4); however:
  Version of libpng12-0 on system is 1.2.8rel-5.1ubuntu0.2.
 gimp depends on libwmf0.2-7 (>= 0.2.8.4); however:
  Version of libwmf0.2-7 on system is 0.2.8.3-3.1ubuntu1.
 gimp depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
dpkg: error processing gimp (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimp
```


Is there a way that this can be installed in edgy?
or I'll just stick with gimp2.2?

---

### Post by kanamor on 2007-08-18
For all the ones that have problems of dependences with the other package.  I have not been able to verify if will function correctly, to notify if gives you problems please.

md5     fcfca6a550975b751a29ce369ac47928
[gimp_2.4.0-rc1-1_i386_without_depen.deb](http://www.mediafire.com/?fmn0t4doxxd)

---

### Post by mugginz on 2007-08-18
The 2.4.0-rc1 works great except for one thing, I'm not able to get it to work with a graphics tablet.  The version of Gimp that came with Fiesty did recognise it though.  Has the new version been built without this support?

Scratch that - The problem was caused by not building libgtk2 with the --with-xinput=yes option.

Now its working with pressure sensitivity again.

---

### Post by MadMan2k on 2007-08-18
gimp2.4 on gutsy:
[http://uploader.polorix.net//files/140/gimp-2.4rc1.tar](http://uploader.polorix.net//files/140/gimp-2.4rc1.tar)

---

### Post by disturbedite on 2007-08-18
i grabbed kanamor's new package (only cuz he posted it first) and it installed fine obviously and it appears to work fine on kubuntu gutsy.  thanks kanamor!

---

### Post by anasofiapaixao on 2007-08-18
I did the same but the one that checks for depencies complained about libfreetype6 not being a satisfiable dependency (of course installed and on the repos), and the other one gave this output when trying to run the GIMP:
```
sofia@sofia-laptop:~$ gimp
gimp: symbol lookup error: gimp: undefined symbol: g_once_init_enter_impl
```

And for all the googlers no, I didn't compile my own libglib or use some bizarre local package =)

---

### Post by lukk-pl on 2007-08-19
I have the same problem with lastest kanamor package - gimp_2.4.0-rc1-1_i386_without_depen.deb (Feisty)
*gimp: symbol lookup error: gimp: undefined symbol: g_once_init_enter_impl*

---

### Post by sebastjanp on 2007-08-22
Same error here. I'm running Feisty

---

### Post by andoty_jazz on 2007-08-24
1.) Got synonymous error with ***anasofiapaixao, lukk-pl, sebastjanp,***  when I ran it on a terminal. I am using Ubuntu 7.04 Feisty Fawn, 2.6.20-16-generic, i386 machine.

2.) One more thing, The Gimp icon on the **Applications->Graphics** was missing.

3.) ***kanamor*** please, please help us with your humble heart and advanced skills. 

To anyone who could help. Thanks in advance. 

Looking forward. :guitar:

---

### Post by andoty_jazz on 2007-08-25
Anyways, if there aren't updates on how to fix this issue. Ubuntu Feisty users, let's just down-grade to the stable one.

**sudo dpkg -i /var/cache/apt/archives/gimp_2.2.13-1ubuntu4.3_i386.deb**

P.S. Still craving for the rc1 of GIMP 2.4.

---

### Post by frychiko on 2007-08-25
The link for .deb for 2.3.16 is dead.

---

### Post by Zootropo on 2007-08-27
> **frychiko said:**
> The link for .deb for 2.3.16 is dead.

You can find the 2.3.18 version from madman2k at his website
[http://madman2k.net/comments/85](http://madman2k.net/comments/85)

---

### Post by redforce on 2007-08-31
Please can you try my GIMP 2.4-RC1 package for Ubuntu 7.04 AMD64:
[http://www.mediafire.com/?4mybtlybcb3](http://www.mediafire.com/?4mybtlybcb3)

If it works, I can make a i386 version, too.

---

### Post by andoty_jazz on 2007-08-31
> **redforce said:**
> Please can you try my GIMP 2.4-RC1 package for Ubuntu 7.04 AMD64:
[http://www.mediafire.com/?4mybtlybcb3](http://www.mediafire.com/?4mybtlybcb3)

If it works, I can make a i386 version, too.

Yes Sir. It would be of great pleasure if you could give us a link of your i386 version.

Thank you so very much in advance.!!!

Long live the **GIMP**

---

### Post by redforce on 2007-08-31
Here it is:
GIMP 2.4-RC1 for Ubuntu 7.04 i386
[http://www.mediafire.com/?azgb3390zsg](http://www.mediafire.com/?azgb3390zsg)

Please tell me if it works for you!

---

### Post by andoty_jazz on 2007-08-31
> **redforce said:**
> Here it is:
GIMP 2.4-RC1 for Ubuntu 7.04 i386
[http://www.mediafire.com/?azgb3390zsg](http://www.mediafire.com/?azgb3390zsg)

Please tell me if it works for you!

Thanks again and again.

Yes Sir. Will let you know  if it works.

---

### Post by redforce on 2007-08-31
I forgot to mention, you can start the gimp 2.4 with

/opt/gimp-2.4/bin/gimp-2.4

---

### Post by andoty_jazz on 2007-09-01
> **redforce said:**
> I forgot to mention, you can start the gimp 2.4 with

/opt/gimp-2.4/bin/gimp-2.4

Already installed it.

Works like a charm so far.

**1.)** All dependencies were satisfied.

**2.)** Ran in **/opt/gimp-2.4/bin/gimp-2.4** was really great and very fast load time.

**3.)** This one's rock. :guitar:

A warm of applause to **redforce**, you made my day Sir.

---

### Post by Ryupower on 2007-09-02
Very awesome! Thanks a lot! That way I don't have to go through those dependency pains. :P

Question: I read that Gimp 2.4 will also have a one-window interface, how can I have this done?

---

### Post by BigDXLT on 2007-09-04
> **redforce said:**
> Here it is:
GIMP 2.4-RC1 for Ubuntu 7.04 i386
[http://www.mediafire.com/?azgb3390zsg](http://www.mediafire.com/?azgb3390zsg)

Please tell me if it works for you!

Working for me so far!

---

### Post by MadMan2k on 2007-09-05
gimp 2.4rc2 for gutsy:
[http://uploader.polorix.net//files/140/gimp_2.4.0%7Erc2.tar](http://uploader.polorix.net//files/140/gimp_2.4.0%7Erc2.tar)

---

### Post by disturbedite on 2007-09-07
@ MadMan2k

may i ask why you're not producing deb archives any more?  i know one can still use the tar archives, but...

---

### Post by MadMan2k on 2007-09-07
I still produce debs, but when there are several of them, i tar them together so you can download them at once.

but those gimp debs just became obsolete since the official sync with debian happenened just a couple of hours after I upped them...

---

### Post by disturbedite on 2007-09-09
so i noticed...
thanks for the clarification.

---

### Post by DirtDawg on 2007-09-21
Thanks for the 2.4 package.

I'm trying to install the "save for web" plugin but when I use the ./configure command, it tries to build it for Gimp2.2. But the plugin needs at least version 2.3 to build.

Anyone know how to point the plugin to the 2.4 version? It would be appreciated.

Thanks

EDIT: YES! They got rid of that awful window that used to popup every time i used the eyedropper! It's like early Christmas around here. :)

---

### Post by MadMan2k on 2007-09-24
for gimp2.4rc3 on gutsy
```
deb http://ppa.launchpad.net/madman2k/ubuntu gutsy main restricted universe multiverse
```

---

### Post by redforce on 2007-09-24
GIMP 2.4 RC3 for Ubuntu 7.04 available [here](http://www.gimpusers.com/gimp-download.php)

---

### Post by zana_arg on 2007-10-04
Thak you very much, but whats the password to download it?

---

### Post by andoty_jazz on 2007-10-05
> **zana_arg said:**
> Thak you very much, but whats the password to download it?

After clicking/hitting the link that [redforce]("http://ubuntuforums.org/member.php?u=189271") had provided. Do as follows,

[IMG]http://img375.imageshack.us/img375/6060/ubuntuforumsgimpdebum3.png[/IMG]

and....

[IMG]http://img383.imageshack.us/img383/6628/clickhereoq4.png[/IMG].


I hope this could help.

Rock n' Roll.

---

### Post by NIBOGO on 2008-03-17
Someone can post a link to download a deb of save for web plugin for AMD64 , gimp 2.4???

---

### Post by DirtDawg on 2008-03-18
Does anyone happen to have the deb for 7.04 available still? I somehow missed it but would love 2.4 installed properly.

---

### Post by ayoli on 2008-03-18
> **NIBOGO said:**
> Someone can post a link to download a deb of save for web plugin for AMD64 , gimp 2.4???
I'm not sure you'll find a deb for this, but anyway, it isn't very hard to build. Grab the sources [here]("http://registry.gimp.org/node/33") do the usual :
```
./configure
make
sudo make install
```
If for some reason make install fails, just copy the built webexport file from the src dir to  /usr/lib/gimp/2.0/plug-ins/webexport (using sudo).
After next gimp start, you'll find it in the file menu.

---

### Post by ayoli on 2008-03-18
> **DirtDawg said:**
> Does anyone happen to have the deb for 7.04 available still? I somehow missed it but would love 2.4 installed properly.

I'm afraid that all the links that provided gimp2.4 for feisty are down/dead/removed.
It is somewhat difficult to build gimp on feisty since gimp2.4 needs a more recent gtk version than the gtk that comes with feisty.
Maybe it is a good reason to upgrade to gutsy ;)

---

### Post by DirtDawg on 2008-03-18
> **ayoli said:**
> I'm afraid that all the links that provided gimp2.4 for feisty are down/dead/removed.
It is somewhat difficult to build gimp on feisty since gimp2.4 needs a more recent gtk version than the gtk that comes with feisty.
Maybe it is a good reason to upgrade to gutsy ;)

Right. I have 2.4 "installed", I was hoping someone still had the original deb from the above link floating around. 

As far sas upgrading, I have a lot of cutstom built apps and settings, so I don't llike to change my os more than once a year or so. I know I could update without doing a clean reinstall, but I've read way too many horror stories to trust my install to that process. Hardy is close to release so I'll wait for that.

---

### Post by ayoli on 2008-03-18
> **DirtDawg said:**
> Right. I have 2.4 "installed", I was hoping someone still had the original deb from the above link floating around. 

As far sas upgrading, I have a lot of cutstom built apps and settings, so I don't llike to change my os more than once a year or so. I know I could update without doing a clean reinstall, but I've read way too many horror stories to trust my install to that process. Hardy is close to release so I'll wait for that.
That sounds reasonable indeed.

---

### Post by wraithofhate on 2011-05-13
> **redforce said:**
> Here it is:
GIMP 2.4-RC1 for Ubuntu 7.04 i386
[http://www.mediafire.com/?azgb3390zsg](http://www.mediafire.com/?azgb3390zsg)

Please tell me if it works for you!

This link does not lead to a download anymore.
Is there anyway someone could send me a link to the download?

---

### Post by jerrrys on 2011-05-13
?? [http://www.google.com/search?client=ubuntu&channel=fs&q=mediafire.com&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=mediafire.com&ie=utf-8&oe=utf-8) ??

---

