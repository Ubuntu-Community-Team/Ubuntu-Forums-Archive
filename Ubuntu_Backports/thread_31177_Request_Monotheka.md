---
title: "Request: Monotheka"
date: 2005-05-02
forum: Ubuntu Backports
---

### Post by A-star on 2005-05-02
Monotheka is a (yet!) simple application to organize and keep track of your movie catalogue. It runs on Linux platform using the GTK toolkit. It's designed to be simple and GNOME / HIG compliant. It's written in Mono. It's free.

[http://monotheka.enove.pl/](http://monotheka.enove.pl/)

Thanks a lot
Kind regards
A-star

---

### Post by A-star on 2005-05-19
bumping this request

---

### Post by ubuntu_demon on 2005-05-21
[QUOTE=A-star]bumping this request[/QUOTE]
 those features rock :
[http://monotheka.enove.pl/index.php?page=features](http://monotheka.enove.pl/index.php?page=features)

IMDBGet - to auto-fill movie data from IMDB (by title)

But this is needed :
MONO >= 1.0.6 (MONO 1.1.x strongly recommended)

mono 1.0.5-1 is in universe right now  so unless mono is backported from breezy this won't work

---

### Post by ubuntu_demon on 2005-06-03
I just compiled it. It's a nice program. One big thing missing is imdb ratings.(and he's going to implement it!)

You got to have mono installed (backported). Also install the package sqlite. Edit monoboil.conf and remove "sqlite-2.8". After this do just :

$ ./configure
$ make
$ sudo make install

---

### Post by jdong on 2005-06-03
Try to get it into Sid or Universe... That's the best way :)

---

### Post by infinito on 2005-06-03
If you like Monotheka, you should try **GCFilms** ([http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)).
It's a movie catalogue, but it has more plugins for importing data form the net than Monotheka. Right now it supports gettinf info from these websites:

- English: Amazon, DVDZone2.com, IMDB
- French: Alapage.com, Allocine.fr, Amazon.fr, Animeka.com, CinemaClock.com, Cinemotions.com, DVDFr.com, DVDPost.be, MonsiuerCinema.com, Movieclub.fr
- Spanish: CulturaliaNet.com
- German: Amazon.de
- Dutch: MovieClubNL
- Italian: FilmUp

It's written in Perl-gtk2, so you don't need Mono. 
Doesn't need SQL databases.
Exports movie list to XML, web page, CSV, SQL and .tar.gz
Imports movie list from AntMovieCatalog, CSV and DVDProfiler.
Supported languages: English, Spanish, French, Italian
Has support for Skins.

You have to try it! [http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)

---

### Post by ubuntu_demon on 2005-06-04
[QUOTE=infinito]If you like Monotheka, you should try **GCFilms** ([http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)).
It's a movie catalogue, but it has more plugins for importing data form the net than Monotheka. Right now it supports gettinf info from these websites:

- English: Amazon, DVDZone2.com, IMDB
- French: Alapage.com, Allocine.fr, Amazon.fr, Animeka.com, CinemaClock.com, Cinemotions.com, DVDFr.com, DVDPost.be, MonsiuerCinema.com, Movieclub.fr
- Spanish: CulturaliaNet.com
- German: Amazon.de
- Dutch: MovieClubNL
- Italian: FilmUp

It's written in Perl-gtk2, so you don't need Mono. 
Doesn't need SQL databases.
Exports movie list to XML, web page, CSV, SQL and .tar.gz
Imports movie list from AntMovieCatalog, CSV and DVDProfiler.
Supported languages: English, Spanish, French, Italian
Has support for Skins.

You have to try it! [http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)[/QUOTE]
 thnx I checked it out. It looks nice.

But it can't get ivideo/audio format nformation from files like monotheka can. Also monotheka has plans for a Beagle backend/filter.

---

### Post by ubuntu_demon on 2005-06-04
[QUOTE=jdong]Try to get it into Sid or Universe... That's the best way :)[/QUOTE]
 I know ... since there is no deb.

I just wanted to tell you guys about my experiences ;)

---

### Post by A-star on 2005-06-06
To install monotheka see this how-to
[http://www.ubuntuforums.org/showthread.php?t=36688](http://www.ubuntuforums.org/showthread.php?t=36688)

---

### Post by JDay on 2005-06-20
So, could we get GCfilms in extras? Version 5.1 was just released. Source tarball is on the site and deb package data is in the cvs: [http://cvs.gna.org/viewcvs/gcfilms/gcfilms/packages/debian/](http://cvs.gna.org/viewcvs/gcfilms/gcfilms/packages/debian/)

Edit: Or, if that isn't sufficient you can contact "Dab", who does the Debian packaging.

---

### Post by nehalem on 2005-06-21
I was really excited about this app too.  I think I'll try to install it.

---

### Post by graabein on 2005-06-21
sign me up for both monotheka and gcfilms in universe and/or backports!

---

### Post by sapo on 2005-06-21
gcfilms is great! with that borrower function i ll never lose a cd again :D

man.. it really rox!

[[IMG]http://img250.echo.cx/img250/3248/gcfilms8ic.th.jpg[/IMG]](http://img250.echo.cx/my.php?image=gcfilms8ic.jpg)

it even generate a html page with my movies:

[http://xgn.no-ip.org:1000/movies.html](http://xgn.no-ip.org:1000/movies.html)

---

### Post by infinito on 2005-06-23
Look at this thread if you want to install GCfilms on Ubuntu:
[HOWTO: Install GCfilms (movie collection management)](http://www.ubuntuforums.org/showthread.php?t=43872)

---

