---
title: "pdfEdit a Workable deb Package"
date: 2007-02-20
forum: Repositories &amp; Backports
---

### Post by ramjet_1953 on 2007-02-20
Hi, Guys!

I finally found a deb package for pdfEdit that works fine on my system, after trying several times (unsuccessfully) to "roll my own".

Here's the link:

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

Regards,
Roger 8)

---

### Post by os.getlogin on 2007-02-22
thanks for the heads-up.

do you know what deps are needed?  I the package installs fine with dpkg, but I get

> 
% pdfedit                                                                                                                                             
pdfedit: Symbol `_ZTI11QDragObject' has different size in shared object, consider re-linking
pdfedit: Symbol `_ZTI7QWidget' has different size in shared object, consider re-linking
zsh: segmentation fault (core dumped)  pdfedit


Nate

---

### Post by ramjet_1953 on 2007-02-23
I think if you make sure that all of the QT libraries are installed, all should go OK.

If you still have problems, get back to me and I'll pull out my notes and give you a list of all the dependancies.

Regards,
Roger :cool:

---

### Post by aysiu on 2007-03-26
FYI: I just tried an alien installation of the RPM at SourceForge.net, and it worked! ```
sudo apt-get update
sudo apt-get install alien
wget -c http://internap.dl.sourceforge.net/sourceforge/pdfedit/pdfedit-0.2.5-1.i386.rpm
sudo alien -iv pdfedit-0.2.5-1.i386.rpm
```

---

### Post by nsilva on 2007-03-31
I tried the alien installation, everything went smooth, except
when trying to run pdfedit I get the following error

> 
pdfedit: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by pdfedit)


I'm not able to find glibc with apt-get, what package should I install?

> 
nsilva@Typhon:/tmp$ psearch glibc
libnss-mdns - NSS module for Multicast DNS name resolution
linux-kernel-headers - Linux Kernel Headers for development
manpages-dev - Manual pages about using GNU/Linux for development
abicheck - binary compatibility checking tool
ja-trans - Japanese gettext message files
kmtrace - a KDE memory leak tracer
libdb1-compat - The Berkeley database routines [glibc 2.0/2.1 compatibility]
libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libgetopt-java - GNU getopt - Java port
libnss-ldap - NSS module for using LDAP as a naming service
libnss-pgsql1 - name service switch module using PostgreSQL
libstdc++2.10-glibc2.2 - The GNU stdc++ library
libuclibc-dev - A small implementation of the C library
libuclibc0 - A small implementation of the C library
linuxinfo - Displays extended system information
manpages-pl-dev - Polish man pages for developers
perdition-dev - Development libraries and headers for perdition
perdition-ldap - Library to allow perdition to access LDAP based popmaps
perdition-mysql - Library to allow perdition to access MySQL based popmaps
perdition-odbc - Library to allow perdition to access ODBC based popmaps
perdition-postgresql - Library to allow perdition to access PostgreSQL based popmaps
python-utmp - python module for working with utmp
glibc-doc - GNU C Library: Documentation
libc6 - GNU C Library: Shared libraries and Timezone data
libc6-pic - GNU C Library: PIC archive library
winbind - service to resolve user and group information from Windows NT servers
nsilva@Typhon:/tmp$    


---

### Post by BLTicklemonster on 2007-04-08
A pdf editor for linux. Well I'll be dog gone. Thanks!

---

### Post by FXWGBill on 2007-04-11
I have seen a few people, here lately, that have been looking for a PDF editing type program.  I found this particular 'post' through some searches and I am REALLY happy to say that this .deb works!  In Feisty!!  Had a couple problems trying to install pdfedit from src; had to install 'ant' and 'Apache FOP'  but I found this before I got that finished so....

Thought I would pass along my good fortune and bump this up; hopefully help other folks...

---

### Post by Billy McCann on 2007-04-14
> **ramjet_1953 said:**
> Hi, Guys!

I finally found a deb package for pdfEdit that works fine on my system, after trying several times (unsuccessfully) to "roll my own".

Here's the link:

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

Regards,
Roger 8)

Thanks!  Worked for me!

---

### Post by konungursvia on 2007-04-16
I can't install it in Dapper, it says libc6 dependency not satisfiable. Can I do some workaround?

---

### Post by aysiu on 2007-04-16
> **konungursvia said:**
> I can't install it in Dapper, it says libc6 dependency not satisfiable. Can I do some workaround?
Using both methods (.deb and .rpm with alien)?

More details here:
[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

---

### Post by konungursvia on 2007-04-16
Sorry aysiu, I don' t understand your post. Are you saying alien will manage my deps better than the debian package manager? :D

---

### Post by aysiu on 2007-04-16
> **konungursvia said:**
> Sorry aysiu, I don' t understand your post. Are you saying alien will manage my deps better than the debian package manager? :D
No. I'm saying there are two ways to install PDFedit.

One uses a .deb (the native Ubuntu format) that seems to be targeted specifically for later versions of Ubuntu (Edgy 6.10/Feisty 7.04).

The other uses the .rpm (a non-native format) available from the PDFedit website and then converts it (using alien) to a .deb file in order to install it.

Again, more details here:
[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

---

### Post by konungursvia on 2007-04-16
Thanks! But I'm not very smart... do you mean if I try the RPM instead it will install and run despite the dependency problem with libc6 on my dapper install? (I knew there were 2 ways to install, but thought running the app, not installing, was the problem with the dependencies.)

---

### Post by aysiu on 2007-04-16
> **konungursvia said:**
> Thanks! But I'm not very smart... do you mean if I try the RPM instead it will install and run despite the dependency problem with libc6 on my dapper install? (I knew there were 2 ways to install, but thought running the app, not installing, was the problem with the dependencies.)
I mean it's worth a shot. I don't know if you'll still have that dependency problem or not.

---

### Post by konungursvia on 2007-04-16
Can anyone offer a second opinion?

---

### Post by konungursvia on 2007-04-16
I mean, aren't dependencies based on installed programs, rather than barriers to installation methods? Don't I need to get the libc6 stuff installed, or removed, or replaced, rather than trying a different delivery method to my package of installed programs? The issues have confused me here.

---

### Post by BLTicklemonster on 2007-04-17
Have you tried it yet just to see if it works?


Anyway, I finally got off my duff and edited a pdf file. Sloooow, but it worked! Yay me.

---

### Post by konungursvia on 2007-04-17
Didn't work. After "install", i see
pdfedit: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by pdfedit)

---

### Post by konungursvia on 2007-04-17
> **BLTicklemonster said:**
>  I finally got off my duff and edited a pdf file. Sloooow, but it worked! Yay me. Gratz to you though. Luckily for me, I still have Acrobat Pro on my xp partition.

---

### Post by kagashe on 2007-05-06
Have you seen [this]("http://www.getdeb.net/app.php?name=PDF%20Editor")?

kagashe

---

### Post by Scunizi on 2007-05-06
Thanks Kagashi,  That's a great site.. I found a couple of things there I've been looking for.  I got PDFedit loaded and was able to load a file.. Then I found that I couldn't use my wacom tablet to manually draw on the doc... :(  but the rest of the features look promising.

---

### Post by FXWGBill on 2007-05-11
Another good proggy I found, will allow you to 'fill out' pdf forms and make notes on them, etc.  It is called flpsed  and here is the link:  [http://www.ecademix.com/JohannesHofmann/flpsed.html](http://www.ecademix.com/JohannesHofmann/flpsed.html)    It is also listed as a Debian package here:  [http://packages.debian.org/unstable/graphics/flpsed](http://packages.debian.org/unstable/graphics/flpsed)   With a little tinkering around I got both PDF  Editor and flpsed to work; a fantastic combination; no more need for XP!!  I love it!!

---

### Post by Tehas on 2007-06-04
Thanks for the info on PDF-Edit, it installed on Feisty using the alien directions.  I went for the newer release.  It seems to be very slow.  Once you enter text into the document, it takes several seconds for it to render the text and allow you to enter data in another location.

I then tried flpsed and it's working much better.   Thanks for the tip.

---

### Post by Meriwether on 2008-01-03
Hi, I've been trying to install pdfEdit in Ubuntu Dapper Drake, but when I download using .deb, I get an error message saying there is an unresolvable dependency problem with libc6. When I try with .rpm and alien, I get a message that :  /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by pdfedit). 

Apparently, pdfedit needs version 2.4 of libc6, which is not in the dapper repository. Because libc6 (or glibc) is a crucial component, does anyone know if there is another deb build of it around somewhere?

Thanks!

---

### Post by F-3582 on 2008-01-04
Tried backporting it youself with [Prevu]("https://wiki.ubuntu.com/Prevu")?

---

### Post by vgrisham on 2008-03-02
Okay, here's a dumb question. How do I execute it once it's installed. I tried running pdfedit from the command line, but nothing happened. The installation didn't create a launcher.

EDIT: Never mind. I found it in the Synaptic repository, installed it from there and it works fine.

---

### Post by Scunizi on 2008-03-02
The newest version coming out will fix a pretty big bug when trying to merge pages from a couple of different pdf's.  You might want to google the program, grab the source and compile it for your machine.  You'll be better off in the long run.  A frustration eliminator!

---

