---
title: "Trying to use apt-cacher to port apps to a Laptop"
date: 2007-04-02
forum: Repositories &amp; Backports
---

### Post by LaurelLynn on 2007-04-02
I have a slow dial-up connection, but I would like my laptop to have the same applications as my desktop. I have been trying to setup apt-cacher to make my already download apps available over my LAN.

I can log into the apt-cacher server and get its webpage at ¨[http://192.168.0.3:3142/¨](http://192.168.0.3:3142/¨).

Synaptic however fails reporting ¨Could not download all repository indexes¨

I changed all the ¨sources.list¨ entries from:

[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)...

to 

[http://192.168.0.3:3142/us.archive.ubuntu.com/](http://192.168.0.3:3142/us.archive.ubuntu.com/)...

But, apt-cacher´s report  page is reporting ¨Cache Misses¨ as ¨588 (100%)¨.

Seems to me the connection goes through, but source names somehow don´t match?

Anyone have a idea what I could be doing wrong?

Laurel Lynn :(

---

### Post by PointSource on 2007-04-03
This isn't the way you are doing it, but I configured my own local repository following this guide:

[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

---

### Post by LaurelLynn on 2007-04-03
Thanks PointSource!

That guide is the clearest explaination of how repositories work that I´ve seen so far. I think I will use the trivial repository method from now on.

I believe I have figured out what went wrong with apt-cacher. At some point during the process of getting the connection properly configured, the cache got flushed. It´s empty now:(

Live and learn.

Laurel Lynn ;)

---

### Post by LaurelLynn on 2007-04-03
Found my ¨debs¨! \\:D/   apt-cacher had cleared out the normal cache and moved everything to its own.

Followed PointSources advice and did the following:

mkdir ~/repository
mkdir ~/repository/binary
mkdir ~/repository/source

cp *.deb ~/repository/binary
cd ~/repository

dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
dpkg-scansources source /dev/null | gzip -9c > source/Sources.gz

cat >binary/Release
Archive: unstable
Component: Cache4-3-7
Origin: Laurels
Lablel: Laurels Debian repository
Architecture: i386
^D

Then I copied the Release file to source changing ¨i386¨ to ¨source¨.

Just to see if it would work I put everything on a memory stick.
On the client I saved the sources.list file and made a new one
with two entries:

deb file::///media/usbdisk/repository binary/
deb-src file::///media/usbdisk/repository source/

Fired up synaptic and everything was there. :popcorn: 

Now I´ll just point all my clients to my new server repository. Tack an rsync and the two dpkg-scans onto my update cron job. That way the clients can update without ever needing to see the internet. With the memory stick I can put all my downloads in my purse and take them anywhere.

Laurel Lynn :wink:

---

