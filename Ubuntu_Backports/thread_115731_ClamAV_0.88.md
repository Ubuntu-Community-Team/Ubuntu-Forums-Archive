---
title: "ClamAV 0.88"
date: 2006-01-11
forum: Ubuntu Backports
---

### Post by Bachstudies on 2006-01-11
Any chance of updating ClamAV from 0.87-1 to 0.88? My freshclam app complains about being on functionality level 6 instead of 7. I know I shouldn't be too worried but I do receive a lot of windows attachments via email.

---

### Post by HJThis on 2006-01-14
Hello,All

Yes please do this update

Thank you

---

### Post by lotusleaf on 2006-01-15
bump - for a fresh and tasty clamAV version

---

### Post by dentaku65 on 2006-01-16
please update to 0.88 and.... hopefully fix the "log_daemon_msg" errors too ;)

---

### Post by siennalizard on 2006-01-17
Surely an update is now even more necessary, bearing in mind the new security exploit found in versions up to 0.87.1 (the Breezy default).

See [http://www.techworld.com/security/news/index.cfm?NewsID=5176&inkc=0](http://www.techworld.com/security/news/index.cfm?NewsID=5176&inkc=0)

I imagine the security team will get on to this, so a full backport may not be necessary.

J.

---

### Post by ameerirshad on 2006-01-18
I was about to post the same

> Secunia, which maintains a database of vulnerabilities, said the flaw was "highly critical". GNU/Linux vendors hurried to update their own implementations of ClamAV, with updates arriving from Mandriva, Gentoo, Suse, Trustix and others.

---

### Post by dentaku65 on 2006-01-18
at last I've downloaded the source and compiled by myself... :???:

---

### Post by ameerirshad on 2006-01-18
[quote=dentaku65]at last I've downloaded the source and compiled by myself... :???:[/quote]

Great when u know how to hack and compile..... but the "newbees" and others :???:

---

### Post by abandoned_hussam on 2006-01-19
[quote=ameerirshad]Great when u know how to hack and compile..... but the "newbees" and others :???:[/quote] There is no need to hack the software. All you should need to compile most software assuming you have the dependancies installed is :
./configure --prefix=/usr --sysconfdir=/etc && make && sudo make install

---

### Post by dpm on 2006-01-26
I second backporting ClamAV 0.88 too...

---

### Post by lotusleaf on 2006-01-29
bump - baby jesus DEMANDS it! :o

---

### Post by JGJones on 2006-01-30
[QUOTE=hussam]There is no need to hack the software. All you should need to compile most software assuming you have the dependancies installed is :
./configure --prefix=/usr --sysconfdir=/etc && make && sudo make install[/QUOTE]

I prefer to use sudo checkinstall rather than sudo make install

checkinstall is the same as make install but it make a deb file first before installing so that you can easily remove from Synaptic should the need arise or even upgrade with a deb file in future...just easier :)

Think you need to install checkinstall first though? sudo apt-get install checkinstall - yep that's the one.

Cheers

---

### Post by innate on 2006-02-11
(bump)

This solution is ugly. I have a number of things which depend on clamav, including clamsmtp. Also, Ubuntu's clamav is divided into clamav-daemon, clamav-freshclam and others, with programs depending on various parts of that. Also, there are users, groups and permissions that need to be created (e.g. the clamav user needs to be a member of the clamsmtp group and own several directories in var) -- these do not seem to happen correctly when I build it myself.

After trying some of the instructions above and seeing my system get progressively more hosed (such as the log_daemon_msg function in /lib/lsb/init-functions disappearing somehow), I restored from backup.

So I will keep using the old, unsafe, version of ClamAV for now.

---

### Post by microo on 2006-02-16
I've download the newest clamav 0.88 but from there how can i install it ? 
I have untar the file but from this point i don't know how to go further. 


Thank you :confused:

---

### Post by DeadEnd on 2006-02-16
Well as far as I can tell the manual instruction are way difficult for a noob like me and it really is ironic that an application I installed for security is actually making me insecure.

---

### Post by erdesc on 2006-02-16
Well, I did a backport that works ... This method isn't as clean as I would like to, it does the job anyway.

Here is how I did.

Fisrt, add the dapper source to the /etc/apt/source.list

```
deb-src http://fr.archive.ubuntu.com/ubuntu dapper universe main restricted multiverse
```

Then update the apt cache :

```
$ sudo apt-get update
```

As I'm a src member I downloaded the clamav sources in /usr/local/src
```
$ cd /usr/local/src ; apt-get source clamav
```

Then I get what I need to compile clamav :
```
$ sudo apt-get install build-essential
$ sudo apt-get build-dep clamav

```

Then got the debian source in order to avoid [this problem]("http://ubuntuforums.org/showthread.php?p=651722").
```
$ cd /usr/local/src ; mkdir debian ; cd debian
$ mkdir clamd ; cd clamd; wget http://ftp2.de.debian.org/debian-volatile/pool/volatile/main/c/clamav/clamav-daemon_0.88-0volatile1_i386.deb
$ cd ..; mkdir freshclam; cd freshclam ; wget http://ftp2.de.debian.org/debian-volatile/pool/volatile/main/c/clamav/clamav-freshclam_0.88-0volatile1_i386.deb
```

Extract the files from the debs :
```
$ cd /usr/local/src/debian/freshclam
$ ar -x clamav-freshclam_0.88-0volatile1_i386.deb
$ tar xvzf data.tar.gz
```

```
$ cd /usr/local/src/debian/clamd/
$ ar -x clamav-daemon_0.88-0volatile1_i386.deb
$ tar xvzf data.tar.gz
```

Get the init file that will work for freshclam and clamd (in order to avoid the LSB compatibility stuff).

for clamd this will be simple : just overwrite a file :
```
$ sudo cp /usr/local/src/debian/clamd/etc/init.d/clamav-daemon /usr/local/src/clamav-0.88/debian/clamav-daemon.init
```

for freshclam it just a bit harder :

- change the rules file - add a comment to line 81
```
#       perl -pe 's~#COMMON-FUNCTIONS#~qx{cat debian/common_functions}~eg' < debian/clamav-freshclam.init.in > debian/clamav-freshclam.init
```

- copy the file
```
 sudo  cp /usr/local/src/debian/freshclam/etc/init.d/clamav-freshclam /usr/local/src/clamav-0.88/debian/clamav-freshclam.init ; sudo chmod -x clamav-freshclam.init
```

Compile your debs : 
```
$ sudo -s; cd /usr/local/src/clamav-0.88/ ; dpkg-buildpackage ; exit

```


Then you should get backported debs.

Install :
```
sudo dpkg -i clamav_0.88-2_i386.deb clamav-base_0.88-2_all.deb clamav-daemon_0.88-2_i386.deb clamav-freshclam_0.88-2_i386.deb
```

If something looks wrong, just run a :
```
$ sudo apt-get -f install
```

I'm not too sure this is all complete , just hope this will help you.
The only thing I don't like is that if you make a debian/rules clean to compile all that again, it overwrites all this job.

---

### Post by NoNo_231 on 2006-03-15
Add
deb [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
deb-src [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
to the sources.list or in the synaptic repositories. Installed the new version and works fine. 

Dotdeb gives the latest mysql and php. However gives clamav too.

---

### Post by dcstar on 2006-04-02
[QUOTE=NoNo_231]Add
deb [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
deb-src [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
to the sources.list or in the synaptic repositories. Installed the new version and works fine. 

Dotdeb gives the latest mysql and php. However gives clamav too.[/QUOTE]
I had a library error with the packages from this repository.

Since the official Dapper release still seems a fair way away, it would be nice for an official backport of ClamAV 0.88 for the Breezy users.

---

### Post by NoNo_231 on 2006-04-06
Yes there is. It is libgmp3 and libgmp3c2. If you choose the one proposed (the first) the other (the second) will be removed, however it is not critical for the system. At least you can **check that before replacing** using synaptic.

However I second backporting ClamAV 0.88 too.

---

### Post by jdong on 2006-04-23
[https://launchpad.net/products/breezy-backports/+bug/40976](https://launchpad.net/products/breezy-backports/+bug/40976)

Working on it.

---

### Post by jdong on 2006-04-23
Approved; sent off to James for building.

---

