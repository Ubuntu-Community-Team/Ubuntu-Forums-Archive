---
title: "running software straight from server"
date: 2010-11-05
forum: Server Platforms
---

### Post by chippanfat on 2010-11-05
whats the type of server/software that colleges/schools/uni's use to have all their software in one place and students connect to that server(s)? and is it available to use for ubuntu server? :) I'm running a file server using proftpd and a web server using apache2 so i know how to go setting them up basically

I want to be able to have all my software, for windows machines, mac, linux all available on one or multipul server to connect to from inside or outside of my network.

or even, have all my files, docs, ppt, etc on the local computer then access the software through the server.

is this possible with linux servers? and can someone give me a heads up.. I'm not sure where to start atm
I've tried looking for file servers but I just get ftp, or samba server tutorials.


Thankyou :)

---

### Post by lisati on 2010-11-06
[LTSP]("https://help.ubuntu.com/community/UbuntuLTSP") might be part of the answer you are looking for

---

### Post by AndersAA on 2010-11-06
Either LTSP setups, or virtual machine that you can connect to remotely.

Depends on your needs really.

---

### Post by HermanAB on 2010-11-06
Howdy,

You could just use straight NFS too.  Just mount a distant directory and run your programs from it.  It is really quite trivial once you figured out the one line of configuration required for NFS.  All other solutions are immensely complex in comparison.

---

### Post by chippanfat on 2010-11-10
Cool :)
Thanks for your replys guys :D

---

