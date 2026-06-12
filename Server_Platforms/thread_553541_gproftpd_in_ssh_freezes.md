---
title: "gproftpd in ssh freezes"
date: 2007-09-17
forum: Server Platforms
---

### Post by rbprogrammer on 2007-09-17
ok, so i need to set up an ftp quickly, and i have used gproftpd before and got it running within minutes.  but my problem now is that gproftpd locks up.  i can only access my server remotely because it is maybe 300 km away.

so i did the following commands to get a fresh grpoftpd install:
```

$ ssh -X myserver.net
$ sudo aptitude purge proftpd gproftpd
$ sudo aptitude install proftpd gproftpd
$ sudo gproftpd

```
then the "warning" screen pops up saying that the default proftpd config file is not as *featureful* as the one created by gproftpd, so i choose to create one.  but after i click "yes" (to overwrite the default config file) the program freezes.  

if i try to click the exit, i get the "terminate program" popup, i terminate grpoftpd, and start it up again.  i dont get the "warning" screen, but it still locks up... :confused:

is it a problem with gproftpd?? or using a graphical program with ssh??  i mean i tried letting the program for about an hour, but no luck.

i'm only using the GUI because i'm still not that good with config files, and i need the ftp up quickly

---

### Post by rbprogrammer on 2007-09-18
bump

---

