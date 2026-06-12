---
title: "Request: Lyx 1.3.6"
date: 2005-07-27
forum: Ubuntu Backports
---

### Post by aledie on 2005-07-27
A new version of Lyx 1.3.6 has been releazed: [http://www.lyx.org/news.php3](http://www.lyx.org/news.php3)

Any chance to include it in Backports (preferably with qt-frontend). The version in Ubuntu repositories is 1.4.2, which is already 1.5 years old.

The tarball is here:
[ftp://ftp.lyx.org/pub/lyx/stable/lyx-1.3.6.tar.gz](ftp://ftp.lyx.org/pub/lyx/stable/lyx-1.3.6.tar.gz)

Fedora rpm:
[ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/lyx-1.3.6-1fc3_qt.i386.rpm](ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/lyx-1.3.6-1fc3_qt.i386.rpm)

---

### Post by kleeman on 2005-07-27
There is a code patch which enables debs to be built as well. 
[http://wiki.lyx.org/LyX/Linux](http://wiki.lyx.org/LyX/Linux)
If anyone does succeed in building the deb (my build failed for some reason) be sure to upload to help the lyx devs.

---

### Post by charlieg on 2005-07-27
Dude, look up.  You're supposed to stick these in the 'requests' sub-section these days. ;)

---

### Post by aledie on 2005-07-28
[QUOTE=kleeman]There is a code patch which enables debs to be built as well. 
[http://wiki.lyx.org/LyX/Linux](http://wiki.lyx.org/LyX/Linux)
If anyone does succeed in building the deb (my build failed for some reason) be sure to upload to help the lyx devs.[/QUOTE]

I've built the debs of both lyx 1.3.5 and 1.3.6 with checkinstall. The problem is, it cannot be installed, if you have previously tetex-extra installed, since lyx will try to install some fonts in /usr/share/texmf/fonts/type1/bluesky/cm, which are already there installed by tetex-extra. 

You can remove tetex-extra and install lyx, or you can install lyx with the option force "sudo dpkg -i --force-overwrite lyx-1.3.6-1.deb"

When ./configure you may need options --with-frontend=qt --with-qt-dir=/usr/share/qt3 --prefix=/usr

Excepting the tetex-extra problems above, lyx-1.3.6 works good with me.

---

### Post by jdong on 2005-07-28
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lyx](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lyx)

They're not in Breezy yet. Perhaps you should contact the MOTU team (#ubuntu-motu via xchat's Ubuntu servers) and ask for it.

---

### Post by aledie on 2005-07-28
Ok, I will

---

### Post by aledie on 2005-08-02
[QUOTE=kleeman]There is a code patch which enables debs to be built as well. 
[http://wiki.lyx.org/LyX/Linux](http://wiki.lyx.org/LyX/Linux)
If anyone does succeed in building the deb (my build failed for some reason) be sure to upload to help the lyx devs.[/QUOTE]

I finally have got the debs. Works great. Where do you want to get them?

---

### Post by kleeman on 2005-08-02
Yeah I got them to build today as well. They look like high quality debs to me as well (the deb building script was provided by the lyx developers). I have also notified the lyx mailing list as well as these have been often requested....

---

### Post by kleeman on 2005-08-03
If anyone wants these the lyx devs have put them here

[ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/](ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/)

There are four debs and I put up a README as well (be sure to read it  :) ).
Let me know if there are any problems
Backports guys: the script use to produce these can be found here

[http://wiki.lyx.org/LyX/Linux](http://wiki.lyx.org/LyX/Linux)

My impression is that they are of good quality....

---

### Post by Velvet Elvis on 2005-08-04
Thanks.  Seems to work fine here.

Does anyone know how to package extra LaTeX document classes?  I could use memoir but don't want to go screwing around with my TeX/LaTeX instalation as I know next to nothing about it.

---

### Post by kleeman on 2005-08-04
The memoir class (and beamer class) are in the new tetex release 3. This is at present in Debian experimental so is likely buggy. The lyx customization manual (accessible via help) has extensive instructions for manually installing these new classes in Chapter 5.
HTH

---

### Post by Velvet Elvis on 2005-08-05
Wow.  This is amazing.  Thanks.

Either the LyX documentation has drastically improved over the past couple years or  files got left out when I was building it under slackware in the past.  I've never seen either the extended features guide or the customization guide before.  Are they new?

---

### Post by kleeman on 2005-08-05
Yeah it's a great product hence my avatar ;-)

---

### Post by aledie on 2005-08-05
[QUOTE=kleeman]If anyone wants these the lyx devs have put them here

[ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/](ftp://ftp.lyx.org/pub/lyx/bin/1.3.6/)

There are four debs and I put up a README as well (be sure to read it  :) ).
Let me know if there are any problems
[/QUOTE]

Kleeman, Thank you for uploading the packages to lyx... If I knew, wouldnt waste time building my own packages:) 

> 
Backports guys: the script use to produce these can be found here
[http://wiki.lyx.org/LyX/Linux](http://wiki.lyx.org/LyX/Linux)

My impression is that they are of good quality...


Backports guys would not add them, since they are not in Breezy!!! As jdong said in the post above, we have to ask the MOTU guys about:
jdong: "They're not in Breezy yet. Perhaps you should contact the MOTU team (#ubuntu-motu via xchat's Ubuntu servers) and ask for it."

1. I did it, asked Motu-guys on xchat, one guy said, they would wait for appearing this packages in Debian and sinc them. I should ask debian lyx maintainer. 

2. I asked the debian lyx maintainers, they are working on it and would upload it once the bugs are mentioned for lyx on debian package site are checked to be fixed in the new lyx version. Maybe in couple of weeks it will be there in debian repository and then hopefully in Ubuntu universe. It can happen faster, if we help them to check the bugs mentioned for old debian package and make sure, which ones are already fixed and which ones still not.

3. One guy from Motu team also told me, they wouldn't mind to add lyx 1.3.6 to universe, if somebody builds packages and checks it with pbuilder and make sure it is "lintian-clean". After it got some good reviews it would be added. I am new to Linux. It would be great if you could make the part with pbuilder and lintian and contact the guys from MOTU on xchat and give them your packages for adding to Ubuntu.

---

### Post by kleeman on 2005-08-05
Hmmm I checked out lintian and the packages are not completely "lintian clean" The things that it complains about do not look serious but I did not write the script to produce these debs (the lyx guys did) so cannot fix this. I guess then it better to wait and if anyone wants them in the meantime they can be refered to the lyx site....

---

### Post by kleeman on 2005-08-05
Actually for a laugh I went in to my apt cache and whacked all my standard ubuntu packages with lintian and guess what? A whole bunch of them threw up worse problems than the 1.3.6 debs.... 

Example
lintian acroread:

W: acroread: description-synopsis-starts-with-a-capital-letter
W: acroread: binary-has-unneeded-section ./usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SearchFind.api .note
W: acroread: binary-has-unneeded-section ./usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SearchFind.api .comment
E: acroread: bad-version-number 7.0-0.9~5.04ubp2

Sounds like the motu guys are being a bit fussy....

---

### Post by aledie on 2005-08-06
[QUOTE=kleeman]Hmmm I checked out lintian and the packages are not completely "lintian clean" The things that it complains about do not look serious 
[/QUOTE]

Yes I also checked the packages for lintian. The most problems were with cm-fonts.  I described it above, when I tried to install it with checkinstall, I ahd same problem with the same fonts, tried to overwrite my tetex-extra (some stupid dependancy). All the rest seems not realy important, like wrong release definition or Description. I think this would be easy to fix.

> 
but I did not write the script to produce these debs (the lyx guys did) so cannot fix this. 

The script is actually not from the lyx guys but from the debian lyx maintainers. The lyx guy just copied the script from the 1.3.4 version of lyx at debian. He fixes the problems, arise when we try to make packages from the 1.3.6 tarball, and modifies the diff file. 

> 
I guess then it better to wait and if anyone wants them in the meantime they can be refered to the lyx site....

I think if we just wait, nothing will change. Therefore, any problem we get, we better report to the lyx guy, who put the diff script for making deb packages. He will change the diff file than. Also try to check if the old 1.3.4 bugs are still present in 1.3.6 and report to the debian lyx maintainers. 

The thing we want are lyx packages installable at any PC with any configuration, and not only ours. Otherwise the MOTU guys will never add lyx 1.3.6. 

Otherwise we will wonder for pretty long, why Fedora had 1.3.5 already long time ago, but we still have to use the buggy 1.3.4 and nobody cares about.

---

### Post by whu on 2005-09-09
Could you please don't forgot Lyx 1.3.6 within the breezy distro (specialy for AMD64 and QT)

---

### Post by kleeman on 2005-09-09
When Breezy goes final I will compile a new set of debs using the script mentioned above. I need it - I use this software nearly every day!

---

### Post by kleeman on 2005-09-09
I can do qt but amd64 is a bit hard as I have intel hardware. I can coach you on the script if you have amd64 if you like....

---

### Post by kleeman on 2005-09-10
Nevermind I just noticed that 1.3.6 has appeared in Breezy (10 Sep) which saves me some effort.

---

### Post by kleeman on 2005-09-10
I checked it on my Breezy partition and lyx-qt works PROVIDING you install the kubuntu desktop package. Without this the menus are black for some reason.

---

### Post by jdong on 2005-09-10
file a bug report then... there's a fighting chance that we can resolve that before breezy completely freezes over.

---

### Post by kleeman on 2005-09-11
OK John will do. I have lodged about 8 so far on Breezy and none have been fixed yet which is a bit discouraging given we are at preview stage. Maybe the next month will be spent on heavy bug fixing ;-) ;-)

---

### Post by whu on 2005-09-16
[QUOTE=kleeman]I can do qt but amd64 is a bit hard as I have intel hardware. I can coach you on the script if you have amd64 if you like....[/QUOTE]
After few days of intensive work, I come back to this forum for reading your comments. Great, thank you. I'am currently downloading Lyx 1.3.6 for installing on Intel (breezy without KDE but only few package for QT). 

Everything seems OK. I use this soft near every days too.

I will test it on AMD64 after hours on my own PC. Hopes its work. I wonder to improve my skill too. I will try to compile from the sources too... (following your advice) Maybe I will need your help, if you please ;). Have a nice day.

---

### Post by kleeman on 2005-09-16
1.3.6 is in Breezy btw.

---

### Post by Velvet Elvis on 2005-09-16
Thanks.

LyX was the reason I started using Linux in the first place.  I'm a philosophy student. 
Using MS's equation editor to do sybolic logic in papers was just too painful.

---

### Post by jdthood on 2005-10-10
[QUOTE=Velvet Elvis]
Does anyone know how to package extra LaTeX document classes?  I could use memoir but don't want to go screwing around with my TeX/LaTeX instalation as I know next to nothing about it.[/QUOTE]

You can put the classes under your home directory if you do not want to mess with the system files.

If you have ideas about this then please add them to:

     [http://bugzilla.ubuntu.com/show_bug.cgi?id=17474](http://bugzilla.ubuntu.com/show_bug.cgi?id=17474)

---

