---
title: "tovid's makemenu and makexml missing?"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by pytheas22 on 2008-06-15
I installed tovid today to burn a video DVD.  I can encode my video file properly but can't make a menu or burn to DVD because the makemenu and makexml scripts don't seem to exist.

"locate makemenu" and "locate makexml" return nothing, so it looks like they're not on my system anywhere.  Under Gutsy, tovid worked fine.  I tried using both the Debian package from the Hardy repository and from the tovid website and have the same problem with both.

Any suggestions?

---

### Post by pytheas22 on 2008-06-16
Update: it turns out that the makemenu and makexml scripts do exist inside /usr/share/tovid (locate eventually found them; I guess they had not yet been added to its database when I tried yesterday), but if I just type "makemenu" on the command line the program isn't found.  I can run the scripts by providing the full path to them, and I imagine that if I copied them into /usr/bin they'd work normally, but I don't really care now that I know where they are.

I'm still wondering though why this happened and whether anyone else has had this problem.  I'm positive that on Gutsy makemenu and makexml were installed into my path by the tovid .deb.  Every guide I've seen for tovid assumes that makemenu and makexml are in the user's path.  If this was some mistake on the part of the Debian package, maybe we should get it fixed.  Otherwise it's going to confuse some people (note that the tovid GUI will also not work properly if it can't find makemenu and makexml in the user's path).

---

### Post by brcre on 2008-07-20
My brother and I have had the same problems.  With the information you provided in your post I was able to complete the last bit I needed to get it working.

Packages to add with Synaptic
tcl8.4
tcl8.4-dev
tcl8.4-doc
mencoder
spumux      <- Not found in Synaptic Package Manager
dvdauthor
gdvdauthor

Commands to run from the terminal
cd /usr/share/tovid
brcre@chimera:/usr/share/tovid$ sudo ln makemenu makexml /usr/bin
brcre@chimera:/usr/share/tovid$ which makemenu
/usr/bin/makemenu
brcre@chimera:/usr/share/tovid$ which makexml
/usr/bin/makexml

We've been using images2mpg to create videos from photos, so I'm not sure if that decreased the amount of packages I had to install at the point I was trying to get tovid to work, but it has now ran and produced the first DVD which appears to run on the Panasonic TV/DVD combo I have here in the room to test it on.

---

### Post by robertmf on 2008-07-24
> **pytheas22 said:**
> Update: it turns out that the makemenu and makexml scripts do exist inside /usr/share/tovid (locate eventually found them; I guess they had not yet been added to its database when I tried yesterday), but if I just type "makemenu" on the command line the program isn't found.  I can run the scripts by providing the full path to them, and I imagine that if I copied them into /usr/bin they'd work normally, but I don't really care now that I know where they are.

I'm still wondering though why this happened and whether anyone else has had this problem.  I'm positive that on Gutsy makemenu and makexml were installed into my path by the tovid .deb.  Every guide I've seen for tovid assumes that makemenu and makexml are in the user's path.  If this was some mistake on the part of the Debian package, maybe we should get it fixed.  Otherwise it's going to confuse some people (note that the tovid GUI will also not work properly if it can't find makemenu and makexml in the user's path).

Yes. 'Hardy' has the problemo. Must be a ?repository/install botch? with the tovid suite newly available in the repositories? 

The scripts are there in /usr/share/tovid/ but no PATH to makemenu, makexml, makedvd, makevcd.

---

### Post by pytheas22 on 2008-07-25
I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/tovid/+bug/252026") (probably should have done it a while ago), so hopefully this will be fixed.  If any of you other posters are using a 32-bit kernel, please say so (preferably on the launchpad page)--I'm on 64-bit, and it would be good to know whether this issue is unique to the amd64 package or not.

---

### Post by acreech on 2008-07-26
I added to the bug report my log file for makemenu.  I'm using a 64-bit system and have not got the tovid program to work yet.  My brother has on his 32-bit system.

---

### Post by brcre on 2008-07-26
With the instructions posted above I was able to get it to run on my 32-bit system.

---

### Post by Sikon on 2008-08-11
This is not a bug.

These utilities were diverted because they're low-level utilities and most users aren't interested in them. Moreover, the names are too generic, resulting in namespace pollution. "makemenu"? "makexml"?

---

### Post by tagra123 on 2008-08-12
Even if it's not a bug but you want them in /usr/bin then you can create symlinks

```
sudo ln -s /usr/share/tovid/makemenu /usr/bin/makemenu
sudo ln -s /usr/share/tovid/makexml /usr/bin/makexml
sudo ln -s /usr/share/tovid/makedvd /usr/bin/makedvd
sudo ln -s /usr/share/tovid/makevcd /usr/bin/makevcd
```

Now it will work without typing the full path

---

### Post by benpage26 on 2008-09-20
> **Sikon said:**
> This is not a bug.

These utilities were diverted because they're low-level utilities and most users aren't interested in them. Moreover, the names are too generic, resulting in namespace pollution. "makemenu"? "makexml"?

Maybe they should be renamed to "tovid-makemenu" and "tovid-makexml" in the package, this is the first place i 'looked' for the commands when they were not in my path.  I typed tovid and tried to use tab completion to find any related commands :D

---

### Post by Walter Melon on 2008-10-10
I had the same problem and I'm using a 32-bit system. I followed the instructions that tagra123 left and it works perfectly now.

---

### Post by labinnsw on 2009-02-24
> **brcre said:**
> My brother and I have had the same problems.  With the information you provided in your post I was able to complete the last bit I needed to get it working.

Packages to add with Synaptic
tcl8.4
tcl8.4-dev
tcl8.4-doc
mencoder
spumux      <- Not found in Synaptic Package Manager
dvdauthor
gdvdauthor

Commands to run from the terminal
cd /usr/share/tovid
brcre@chimera:/usr/share/tovid$ sudo ln makemenu makexml /usr/bin
brcre@chimera:/usr/share/tovid$ which makemenu
/usr/bin/makemenu
brcre@chimera:/usr/share/tovid$ which makexml
/usr/bin/makexml

We've been using images2mpg to create videos from photos, so I'm not sure if that decreased the amount of packages I had to install at the point I was trying to get tovid to work, but it has now ran and produced the first DVD which appears to run on the Panasonic TV/DVD combo I have here in the room to test it on.

Thanks a million for this post. Using it I was able to fix what was wrong with my installation of tovid, encode my images, make the menu and burn the DVD, all with the one application.

I am using Ubuntu 8.04.

Just one note. "spumux" is not necessary. It is not in Synaptic and I could not locate it. Since everything worked fine without it, I think it is safe to say mentioning it can only lead to unnecessary confusion.

You may also want to correct "gdvdauthor" which should actually be "qdvdauthor"

---

### Post by stoppage on 2010-05-10
> **brcre said:**
> My brother and I have had the same problems.  With the information you provided in your post I was able to complete the last bit I needed to get it working.

Packages to add with Synaptic
tcl8.4
tcl8.4-dev
tcl8.4-doc
mencoder
spumux      <- Not found in Synaptic Package Manager
dvdauthor
gdvdauthor

Commands to run from the terminal
cd /usr/share/tovid
brcre@chimera:/usr/share/tovid$ sudo ln makemenu makexml /usr/bin
brcre@chimera:/usr/share/tovid$ which makemenu
/usr/bin/makemenu
brcre@chimera:/usr/share/tovid$ which makexml
/usr/bin/makexml

We've been using images2mpg to create videos from photos, so I'm not sure if that decreased the amount of packages I had to install at the point I was trying to get tovid to work, but it has now ran and produced the first DVD which appears to run on the Panasonic TV/DVD combo I have here in the room to test it on.

Hi, I'm using TovidGui v. 0.31 on Ubuntu 8.04 to convert Xvid/avi to dvd.
I have what may be a similar problem....on creating menu I'm stuck on „Default“ font. So I downloaded and exercised (to /home folder) „ Anthony Thyssen's imagick_type_gen.pl script“ from the Tovid Wiki but font isn't seeing any more fonts as default. Then I came accross your entry and made links etc to makexml and makemenu. I'm still stuck on „Default“ font. Any help much appreciated

---

### Post by pytheas22 on 2010-05-10
> Hi, I'm using TovidGui v. 0.31 on Ubuntu 8.04 to convert Xvid/avi to dvd.
I have what may be a similar problem....on creating menu I'm stuck on „Default“ font. So I downloaded and exercised (to /home folder) „ Anthony Thyssen's imagick_type_gen.pl script“ from the Tovid Wiki but font isn't seeing any more fonts as default. Then I came accross your entry and made links etc to makexml and makemenu. I'm still stuck on „Default“ font. Any help much appreciated

Are you sure the imagick_type_gen.pl script ran properly?  What was the output it gave you?

---

### Post by stoppage on 2010-05-10
> **pytheas22 said:**
> Are you sure the imagick_type_gen.pl script ran properly?  What was the output it gave you?

It outputted a huge list of fonts
Excerpt...
NimbusRomanNo9 - Nimbus Roman No9 Regular - Nimbus Roman No9

BitstreamCharterI - Bitstream Charter Italic - Bitstream Charter

URWGothicDemi - URW Gothic Demi - URW Gothic

BitstreamCharterBI - Bitstream Charter Bold Italic - Bitstream Charter

CenturySchoolbookI - Century Schoolbook Italic - Century Schoolbook

NimbusMonoB - Nimbus Mono Bold - Nimbus Mono

URWPalladioBI - URW Palladio Bold Italic - URW Palladio

---

### Post by pytheas22 on 2010-05-12
Which command did you use to run the script?  Did you use the command suggested at [http://tovid.wikia.com/wiki/Makemenu](http://tovid.wikia.com/wiki/Makemenu) ?  From the output you mention, it sounds like you probably did something like:

```
imagick_type_gen.pl
```

instead of:

```
imagick_type_gen.pl > ~/.magick/type.xml
```

Apparently the redirect part is important.

---

### Post by stoppage on 2010-05-21
> **pytheas22 said:**
> Which command did you use to run the script?  Did you use the command suggested at [http://tovid.wikia.com/wiki/Makemenu](http://tovid.wikia.com/wiki/Makemenu) ?  From the output you mention, it sounds like you probably did something like:

```
imagick_type_gen.pl
```

instead of:

```
imagick_type_gen.pl > ~/.magick/type.xml
```

Apparently the redirect part is important.



A solution to the fonts problem found by gaspard.leon at [http://ubuntuforums.org/showthread.php?t=183936&highlight=fonts&page=48](http://ubuntuforums.org/showthread.php?t=183936&highlight=fonts&page=48)
Quote...&#8220;In the tovid scripts, replace convert -list type with convert -list font

if your version of ImageMagick has updated that feature as mine had...
(run those 2 commands in a shell to test)

i found that the following files had to change:
Code:
/usr/share/tovid/makemenu
/usr/share/python-support/tovid/libtovid/gui/configs.py&#8220;

---

