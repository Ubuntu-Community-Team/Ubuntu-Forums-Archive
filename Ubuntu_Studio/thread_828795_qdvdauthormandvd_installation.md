---
title: "qdvdauthor/mandvd installation"
date: 2008-06-14
forum: Ubuntu Studio
---

### Post by baz1979 on 2008-06-14
[FONT="Arial"]Hi All,

I'm trying to install qdvdauother/mandvd on hardy but running into problems.  When I do apt-get it comes back with a error message saying:[/FONT]

[FONT="System"]The following packages have unmet dependencies.
  qdvdauthor: Depends: dvd-slideshow but it is not going to be installed
              Depends: mjpegtools (>= 1.8.0) but it is not going to be installed
              Depends: videotrans but it is not going to be installed[/FONT]

[FONT="Arial"]So I try to install dvd-slideshow using apt-get as well, but then I get this:[/FONT]

[FONT="System"]The following packages have unmet dependencies.
  dvd-slideshow: Depends: mjpegtools (>= 1.8.0) but it is not going to be installed
E: Broken packages[/FONT]

[FONT="Arial"]
So Then I try to install mjpegtools using apt-get and again another error message[/FONT]:

[FONT="System"]The following packages have unmet dependencies.
  mjpegtools: Depends: libdirectfb-0.9-25 but it is not installable
              Depends: libmjpegtools0 (>= 1:1.8.0) but it is not going to be installed
              Depends: libquicktime0 (>= 0.9.10+debian) but it is not going to be installed
E: Broken packages[/FONT]

[FONT="Arial"]
I'v checked with the package manager and I have libdirectfb-1.0-0 installed as it is used by mplayer, virtualbox and a few others.  Any ideas of how to sort this out?

cheers[/FONT]

---

