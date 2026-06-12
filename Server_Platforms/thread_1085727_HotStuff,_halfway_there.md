---
title: "HotStuff, halfway there"
date: 2009-03-03
forum: Server Platforms
---

### Post by Flimm on 2009-03-03
I'm trying to install [HotStuff](http://www.kstuff.org/projects/hotstuff) on my local server, for testing purposes. [My project](http://epidermis.tuxfamily.org) uses GHNS, so I thought I should see how HotStuff handles a GHNS repository and how it displays it.
So I downloaded the [tarball (version 0.9.3)](http://www.kstuff.org/projects/downloads/hotstuff-0.9.3.tar.gz). I read installation.txt, and it recommended installing the debian packages, but since hotstuff isn't in the repos, I built them myself, using:
```
dpkg-buildpackage -us -uc
```
The generated debs had one unmet dependency: libcgi-perl, so I simply removed that dependency by deleting it in control, and I rebuilt the deb files, and installed them.
I followed the [PostgreSQL](https://help.ubuntu.com/community/PostgreSQL) guide, and installed a new database using:
```
sudo -u postgres psql postgres
postgres=# ALTER USER postgres WITH ENCRYPTED PASSWORD 'test';
postgres=# \q
sudo -u postgres createdb mydb
```
I then installed a HotStuff installation, according to the instructions in installation.txt:
```
sudo hotstuff-siteadmin add ep
david@david-laptop:/usr/lib/cgi-bin$ sudo hotstuff-siteadmin add ep
Creation of GHNS repository ep
Database owner [ep]: postgres
Database name [ep]: ep
Database password: test
Adding configuration file for ep...
Adding database for ep...
ERROR:  role "postgres" already exists
Setting up database for ep...
Password for user postgres: 
NOTICE:  CREATE TABLE will create implicit sequence "directory_id_seq" for serial column "directory.id"
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
NOTICE:  CREATE TABLE will create implicit sequence "history_id_seq" for serial column "history.id"
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE

Done! GHNS repository ep is now ready to be used.
Do not forget to edit the configuration at /etc/hotstuff.d/ep.conf.

```
I checked /etc/hotstuff.d/ep.conf, but I didn't see anything I should change, since I'm only testing this stuff.
Next step:
```

% wget http://download.kde.org/khotnewstuff/wallpaper/wallpaper.xml
% # I edited wallpaper.xml so that I would have less wallpapers to download
% sudo hotstuff-scan -s wallpaper.xml -f -c /etc/hotstuff.d/ep.conf 
Too late for "-C" option at /usr/bin/hotstuff-scan line 1.

```
So I edited /usr/bin/hotstuff-scan and removed the -C switch from the first line, it's now:
#!/usr/bin/perl
I then got this error:
```
david@david-laptop:~$ sudo hotstuff-scan -s wallpaper.xml -f -c /etc/hotstuff.d/ep.conf 
?? mirror http://download.kde.org/khotnewstuff/wallpaper/downloads/100384-kubuntu-copia.jpg
// installed 100384-kubuntu-copia.jpg to /tmp/directory/3/100384-kubuntu-copia.jpg
?? mirror http://download.kde.org/khotnewstuff/wallpaper/previews/m100374-1.png
// installed m100374-1.png to /tmp/directory/3/m100374-1.png
?? mirror http://download.kde.org/khotnewstuff/wallpaper/downloads/100374-PCLinuxOSMinime.png
// installed 100374-PCLinuxOSMinime.png to /tmp/directory/3/100374-PCLinuxOSMinime.png
-- [add new] fatih :: esaret (:)
-- [add new] PCLinuxOS Minime :: timeth (v0.3:)
>> PCLinuxOS Minime
DBD::Pg::st execute failed: ERROR:  column "id" specified more than once
LINE 1: ...cence, author, rating, email, category, validity, id, meta_r...
                                                             ^ at /usr/bin/hotstuff-scan line 543.
>> fatih
DBD::Pg::st execute failed: ERROR:  column "id" specified more than once
LINE 1: ...cence, author, rating, email, category, validity, id, meta_r...
                                                             ^ at /usr/bin/hotstuff-scan line 543.

```
Any ideas? I'm totally new to PostgreSQL and Perl.

---

