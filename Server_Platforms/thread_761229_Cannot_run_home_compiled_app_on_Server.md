---
title: "Cannot run home compiled app on Server"
date: 2008-04-21
forum: Server Platforms
---

### Post by mdr on 2008-04-21
Hope someone can poiint out the obvious to me as at the moment I am stumped.

I have my own home-grown fortran scientific application.  

This runs fine on desktop ubuntu on the command line.  Will not execute on Ubuntu Server at all.

Just returns with a bash error   No such file or directory.  Same permissions and everything as per desktop.

thought it may be apparmor - but disabling that makes no difference.

any ideas anyone ?

cheers
Mark

---

### Post by ikonia on 2008-04-21
show us the command your using to run it, 
show us an ls -la $path/to/executable on it
show us a pwd and id just before you run it

---

### Post by mdr on 2008-04-21
Well the command is

./appname.bin

the file is in a dir on /home
I usually run it as a sym link from the data dir I am using.  but even running it directory of the bin location makes no odds.

also makes no odds if the user is a plain user or root.
All this runs fine on a desktop install.  just not on a server install.

as I write this the light bulb goes off - may know what the issue is.
libraries. :oops:
- need to check when I get back to work.

---

### Post by koenn on 2008-04-21
could be the server is missing certain file sthe application expects, but in that case the error would more likely come from the app, not from the shell. 

I'm with ikonia on this one : show us real commands and real output, otherwise this is just a guessing game.

---

### Post by HermanAB on 2008-04-21
Here you go:
$ man ldd

Ldd can tell you what you are missing.

Cheers,

Herman

---

### Post by mdr on 2008-05-08
ok - hair was offically torn out.

Solved so far
needed ia32-libs 

AARRRRRRGGGGHHH  !!!!!  hard to keep track of everything sometimes.

thanks to all who replied anyway.

---

