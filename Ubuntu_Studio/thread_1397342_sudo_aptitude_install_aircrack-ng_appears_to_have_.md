---
title: "sudo aptitude install aircrack-ng appears to have ruined my Ardour installation!"
date: 2010-02-03
forum: Ubuntu Studio
---

### Post by fugazi32 on 2010-02-03
I was installing *sudo aptitude install aircrack-ng* but only noticed until after I'd given it the 'Y' go ahead that it has removed the following packages:

```
The following packages will be REMOVED:
  cdbs{u} dh-buildinfo{u} diffstat{u} fdupes{u} intltool{u} jackd{u} ladcca2{u} ladspa-sdk{u} libart-2.0-dev{u} libasound2-dev{u} 
  libatk1.0-dev{u} libaubio-dev{u} libaubio2{u} libaudclient1{u} libaudid3tag1{u} libbinio1ldbl{u} libboost-date-time-dev{u} 
  libboost-date-time1.34.1{u} libboost-dev{u} libboost-doc{u} libboost-filesystem-dev{u} libboost-filesystem1.34.1{u} 
  libboost-graph-dev{u} libboost-graph1.34.1{u} libboost-iostreams-dev{u} libboost-program-options-dev{u} 
  libboost-program-options1.34.1{u} libboost-python-dev{u} libboost-python1.34.1{u} libboost-regex-dev{u} libboost-regex1.34.1{u} 
  libboost-serialization-dev{u} libboost-serialization1.34.1{u} libboost-signals-dev{u} libboost-signals1.34.1{u} 
  libboost-test-dev{u} libboost-test1.34.1{u} libboost-thread-dev{u} libboost-thread1.34.1{u} libboost-wave-dev{u} 
  libboost-wave1.34.1{u} libcairomm-1.0-dev{u} libcddb2{u} libfftw3-dev{u} libfluidsynth1{u} libglade2-dev{u} libglademm-2.4-dev{u} 
  libglibmm-2.4-dev{u} libgnomecanvas2-dev{u} libgnomecanvasmm-2.6-1c2a{u} libgnomecanvasmm-2.6-dev{u} libgtk2.0-dev{u} 
  libgtkmm-2.4-dev{u} libjack-dev{u} liblo0-dev{u} liblo0ldbl{u} liblrdf0-dev{u} libmcs1{u} libmowgli1{u} libmp4v2-0{u} libmtp8{u} 
  libpangomm-1.4-dev{u} libraptor1-dev{u} libresid-builder0c2a{u} libsamplerate0-dev{u} libsidplay2{u} libsigc++-2.0-dev{u} 
  libsoundtouch1-dev{u} libxcomposite-dev{u} libxcursor-dev{u} libxdamage-dev{u} libxfixes-dev{u} libxinerama-dev{u} libxrandr-dev{u} 
  libxslt1-dev{u} linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} patchutils{u} python-dev{u} python-openssl{u} 
  python-pam{u} python-pyopenssl{u} python-serial{u} python-twisted{u} python-twisted-bin{u} python-twisted-conch{u} 
  python-twisted-core{u} python-twisted-lore{u} python-twisted-mail{u} python-twisted-names{u} python-twisted-news{u} 
  python-twisted-runner{u} python-twisted-web{u} python-twisted-words{u} qjackctl{u} quilt{u} scons{u} sharutils{u} 
  x11proto-composite-dev{u} x11proto-damage-dev{u} x11proto-fixes-dev{u} x11proto-randr-dev{u} x11proto-xinerama-dev{u}
```

It seems to have removed *jackd* and many other audio packages - why would it do this? I'm frustrated as to why it would need to remove JACK??!

Now when I try & run *ardour2* I get:

```
WARNING: Your system has a limit for maximum amount of locked memory!
         This might cause Ardour to run out of memory before your system runs
         out of memory. You can view the memory limit with 'ulimit -l', and it
         is normally controlled by /etc/security/limits.conf

/usr/local/lib/ardour2/ardour-2.7.1: error while loading shared libraries: liblo.so.0: cannot open shared object file: No such file or directory

```

Any help would be much appreciated!

---

### Post by fugazi32 on 2010-02-03
All sorted now, I re-installed all the packages. :)

---

