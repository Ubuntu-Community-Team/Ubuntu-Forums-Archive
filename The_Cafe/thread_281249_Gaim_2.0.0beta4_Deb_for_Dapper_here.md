---
title: "Gaim 2.0.0beta4 Deb for Dapper here"
date: 2006-10-20
forum: The Cafe
---

### Post by SlugO on 2006-10-20
I noticed that there are only some debs for Edgy available on the forums so I decided to build the new 2.0 beta 4 version of Gaim from the source myself. Lots of new features, read about them on [Planet Gaim]("http://gaim.sourceforge.net/planet/").

It's made for i386 Dapper and has worked perfectly so far. I'm not an expert on making debs though so don't shoot me if it doesn't work so well for you ;)

It's built without any special parameters with the normal build-dep, ./configure, make, checkinstall thing. Had to change the version number a bit cos with the default it wanted to update back to the Ubuntu version.

You have to remove the old version of Gaim before installing this. Apparently the new beta uses a bit different location for installing and a changed package structure.

[gaim_2.0.0beta4_i386.zip]("http://www.snapdrive.net/files/103179/gaim_2.0.0beta4_i386.zip")
[Here's a mirror]("http://janno.ee/gaim/gaim_2.0.0beta4_i386.deb") that might be faster. Thanks for this one janno.


[SIZE="3"]**[EDIT Nov 15, Beta5]**[/SIZE]
Gaim 2.0 Beta 5 came out some days ago and it contains bug fixes. Users of old versions are encouraged to update. Once again all the other packages on the forums are for Edgy so I built the Beta 5 too :) After all, Dapper *is* a long term support version ;)

If you're updating from Beta 3 or older then follow the advice above and remove old Gaim packages first. Beta 4 doesn't have to be removed to install Beta 5.

[gaim_2.0beta5_dapper_i386.zip]("http://www.snapdrive.net/files/103179/gaim_2.0beta5_dapper_i386.zip")

[IMG]http://img243.imageshack.us/img243/310/gaim2b5vd1.png[/IMG]

---

### Post by madmetal on 2006-10-20
i just installed it and i works great!
thanx i will report any problems or bugs..(i hope none ;)  )

---

### Post by pay on 2006-10-20
checkinstall isn't always the best to use if you are sharing the deb files.

---

### Post by IYY on 2006-10-20
I don't dig the new highlighted group names. I preferred it all being one white window.

---

### Post by notarikon on 2006-10-20
Is it compiled with dbus enabled (for the popup notification windows)? No matter what I do or install I can't get that option when I compile (everything else works fine)

---

### Post by NewbieLearnLinux on 2006-10-20
Looks cool ! But can it use WebCamera like Kopete?

---

### Post by h84u on 2006-10-21
didn't work..

h84u@h84u:~/Desktop$ sudo dpkg -i gaim_2.0.0beta4_i386.deb
(Reading database ... 87060 files and directories currently installed.)
Preparing to replace gaim 1:1.9.99.is.2.0.0+beta3-1ubuntu1 (using gaim_2.0.0beta4_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim_2.0.0beta4_i386.deb (--install):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0beta4_i386.deb

---

### Post by SlugO on 2006-10-21
> **notarikon said:**
> Is it compiled with dbus enabled?Yeah, the About window says that D-BUS is enabled.

> **h84u said:**
> didn't work..I removed my 2.0 beta 3 before installing this since it warned me about the old version at the end of ./configure. I think you have to remove atleast gaim-data before installing. Apparently it installs it in a different location. Also I think the packages have changed a bit. Although there's only 1 deb in my zip the new beta 4 uses also the *libgaim* package which allows its core functionality to be used for example in gaim-text.

---

### Post by h84u on 2006-10-21
it works..thnx

---

### Post by hexion on 2006-10-21
> **h84u said:**
> didn't work..

h84u@h84u:~/Desktop$ sudo dpkg -i gaim_2.0.0beta4_i386.deb
(Reading database ... 87060 files and directories currently installed.)
Preparing to replace gaim 1:1.9.99.is.2.0.0+beta3-1ubuntu1 (using gaim_2.0.0beta4_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim_2.0.0beta4_i386.deb (--install):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0beta4_i386.deb

Uninstall gaim-data package and then install gaim beta 4. That should work

> sudo aptitude remove gaim-data
sudo dpkg -i gaim_2.0.0beta4_i386.deb


EDIT: Oops, duplicated info :mrgreen:

---

### Post by k@y@ on 2006-10-21
Thank you very much for this. I've tried to compile and install from the source code but couldn't do. Now i've just try your .deb file and see that it works. Really appreciate, thanks again...

---

### Post by iki488 on 2006-10-21
arff the link is down !!

---

### Post by janno on 2006-10-21
Yes, downloading was quite slow for me too for some reason, i mirrored it [here]("http://janno.ee/gaim/gaim_2.0.0beta4_i386.deb"), if it's ok.

---

### Post by mustang on 2006-10-21
Thanks. Works fine.

---

### Post by bonzodog on 2006-10-21
heh...I run Zenwalk, and one of our community just built this, and I am running it now...it's cool.

---

### Post by rocknrolf77 on 2006-10-21
The interface was much nicer now. Liked the new availability function much better now. thanks for the DEB. :)

---

### Post by Rackerz on 2006-10-21
Gaim doesn't have webcam capabilities does it?

---

### Post by WishMaster on 2006-10-21
the .deb works :) tnx

however, gaim still sucks. On the homepage, they said they would release within a week, it took them 10 days (instead of 7).
The only (noticable) change is the icon thing near the global status.
What happened to Google code of summer en MSNP13 ?

A deb for guifications would be nice too...

---

### Post by Foudre on 2006-10-22
> **SlugO said:**
> I noticed that there are only some debs for Edgy available on the forums so I decided to build the new 2.0 beta 4 version of Gaim from the source myself. Lots of new features, read about them on [Planet Gaim]("http://gaim.sourceforge.net/planet/").

It's made for i386 Dapper and has worked perfectly so far. I'm not an expert on making debs though so don't shoot me if it doesn't work so well for you ;)

It's built without any special parameters with the normal build-dep, ./configure, make, checkinstall thing. Had to change the version number a bit cos with the default it wanted to update back to the Ubuntu version.

You have to remove the old version of Gaim before installing this. Apparently the new beta uses a bit different location for installing and a changed package structure.

[gaim_2.0.0beta4_i386.zip]("http://www.snapdrive.net/files/103179/gaim_2.0.0beta4_i386.zip")
[Here's a mirror]("http://janno.ee/gaim/gaim_2.0.0beta4_i386.deb") that might be faster. Thanks for this one janno.

[IMG]http://img237.imageshack.us/img237/4770/gaimb4ll2.png[/IMG]

you realize that they have a dapper one one sourceforge already, unless you compiled that one, but it works fine on my dapper i386

---

### Post by SlugO on 2006-10-22
> **Foudre said:**
> you realize that they have a dapper one one sourceforge already, unless you compiled that one, but it works fine on my dapper i386Well there wasn't one when I made this package. Can you give a link to it? I can only find rpms and source from Gaim's SourceForge download page.

---

### Post by Bad Seed on 2006-10-22
> **janno said:**
> Yes, downloading was quite slow for me too for some reason, i mirrored it [here]("http://janno.ee/gaim/gaim_2.0.0beta4_i386.deb"), if it's ok.
Thanks for the mirror and the original poster for the package. I installed it with no issues on my Xubuntu Dapper :mrgreen:.

---

### Post by kcallis on 2006-10-22
Hmmm, it would seem that Gaim loade correctly, but I am still having the issue with being able to connect to Yahoo... Anyone know a trick to get Yahoo working correctly?

---

### Post by beercz on 2006-10-22
Thanks SlugO - just installed it and it works fine here.

Uninstalled Gaim 2.0 beta 3 first - just in case ;-)

Thanks again

---

### Post by Turbo Audi on 2006-10-23
hmmm my GAIM window does not look funky like the one in the screen shot...loving 2.0/4!

---

### Post by Bad Seed on 2006-10-24
> **kcallis said:**
> Hmmm, it would seem that Gaim loade correctly, but I am still having the issue with being able to connect to Yahoo... Anyone know a trick to get Yahoo working correctly?
I connect to Yahoo fine :-k (direct connection just in case). And Gaim 2 also has support for the Yahoo/MSN interoperability \\:D/

---

### Post by mrgnash on 2006-10-24
Thanks for the deb, it worked a treat :) But the previous version of guifications doesn't seem to be compatible... I miss it :(

---

### Post by drak0 on 2006-10-25
gaim-dev package?  I need this so I can compile plugins...

---

### Post by senzapadroni on 2006-10-25
Great work,
thanks Slug0 ;) ;)

---

### Post by em es on 2006-10-25
The .deb works fine. I didn't even have to deinstall the old version!

The new gaim is absoluitely cool. :)

---

### Post by maddbaron on 2006-10-25
does the new gaim support direct connects and webcams?

---

### Post by j-strap2 on 2006-10-26
> **drak0 said:**
> gaim-dev package?  I need this so I can compile plugins...

Yes, the gaim-dev package would help to get the gaim-OTR plugin compiled.

---

### Post by madmetal on 2006-10-26
when i transfer a file it doesnt show the transfer speed...
i have used gaim in eft and its ok..
not a serious problem but i have to say it..:-k

---

### Post by juantovarm on 2006-11-01
Works perfectly!!!!!!!!!!!!! Thanks a lot i was tired of using 1.5

Juan
[IMG]http://ubuntucounter.org/img/ubuntu-user2.php?user=8952[/IMG]

---

### Post by tsylverwind on 2006-11-03
Package looks pretty good.

Note to users, make sure to re-install ubuntu-desktop when/if it gets removed!!!

No .desktop file... no icon :( .
Snag /usr/share/applications/gaim.desktop from Dapper's package!

Files wind up in /usr/local .  Not a problem though.

No Bonjour support.  Bummer.

Thanks for the package!  Works quite well :) .

---

### Post by SlugO on 2006-11-15
Just posted Gaim 2.0 Beta 5 to this thread. So go get it if you're using Dapper :)

---

### Post by apelete on 2006-11-20
I get no sound with Beta 5...
In the sounds option all I have to chose between is "Console beep", "Command" or "No sound". Does anyone manage to get sound with beta 5 ? What choices do you have in the sound tab in preferences menu ?

---

### Post by alek66 on 2006-12-09
how about making a package for the ones (including me) that have amd64...?
alex

---

### Post by senzapadroni on 2006-12-09
> **apelete said:**
> I get no sound with Beta 5...
In the sounds option all I have to chose between is "Console beep", "Command" or "No sound". Does anyone manage to get sound with beta 5 ? What choices do you have in the sound tab in preferences menu ?

Choose **Command** and type in
```
esdplay %s
```

---

