---
title: "Compiling and packaging a new version of a library"
date: 2006-08-02
forum: Repositories &amp; Backports
---

### Post by thomas.hood on 2006-08-02
Hello packaging gurus,

Firstly just to say I've ploughed through the following, so I'm not being lazy :-)
[https://help.ubuntu.com/ubuntu/packagingguide/C/index.html]("https://help.ubuntu.com/ubuntu/packagingguide/C/index.html")
[http://www.tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/]("http://www.tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/")
[http://www.debian.org/doc/maint-guide/]("http://www.debian.org/doc/maint-guide/")

I'm somewhat wiser, but pretty confused. What I want to do is relatively simple but I'm unsure of how to proceed. I need to build some .debs of a selection of libraries (libjack, jackd, libraw1394, libiec61883, libavc1394) that are already in the dapper binary repositories, but from the latest SVN versions.

The libraries work fine by apt-get install'ing the binary repository versions and then compiling the SVN sources and installing over the top like so:

$ autoreconf -f -i -s
$ ./configure --prefix=/usr
$ make
$ sudo make install

I do this so that apt knows these programs are installed for other apps that depend on them.

Obviously making debs would be a far more sensible approach, not least because there seems to be some odd naming convention stuff going on. (i.e. all the libjack stuff gets called libjack0.100.0-0.so etc, whereas installing from source just calls the files libjack.so etc.)

The sensible approach would appear to be to copy the method that the package maintainers used when building these libraries and just use the SVN source and update the version numbers in the control file. BUT... I can't figure out how to do this as there don't seem to be any source packages for the aforementioned libraries, and I'm unlikely to come up with a correct (matching) set of build rules etc. on my own...

If someone has gone to the trouble of creating binary debs, why don't the put the source packages up? As I understand it, you have to create the source packages first anyhow... ](*,)

Am I missing something really obvious here? 

Thanks,

Tom

P.S. Specifically I need [Freebob]("http://freebob.sourceforge.net/index.php/Main_Page")which is a Firewire soundcard driver library which utilises the Jack audio connection kit.

P.P.S. I know quite a few people are interested in having a set of ubuntu debs (which I'm happy to host) for this, so you'd be helping the multitude :-)

---

### Post by libertyforever on 2006-08-31
I am looking to install FreeBob myself since I also want firewire support for a Presonus Firebox.  (I'm a newbie.)  Have you had any more success?  I am hoping someone will post the magic answer.  ;)

---

### Post by libertyforever on 2006-09-15
I got the newest version of Jack installed, version 0.101.1.  Now, in order to get FreeBob, I need to get libiec61883 version 1.1.0 or newer installed first.  The newest version at [http://www.linux1394.org/](http://www.linux1394.org/) is version 1.0.0.  Does anyone know where to get version 1.1.0 or newer??? ](*,)

---

