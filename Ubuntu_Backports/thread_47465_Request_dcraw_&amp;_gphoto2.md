---
title: "Request: dcraw &amp; gphoto2"
date: 2005-07-08
forum: Ubuntu Backports
---

### Post by LagoniX on 2005-07-08
Can you please backport 
dcraw (7.17-1) and gphoto2 (2.1.5-4ubuntu2) ?

Both are in breezy.

I would be nice to get them backported, so I can begin use my Canon 350D under ubuntu.

---

### Post by Seth on 2005-07-08
[QUOTE=LagoniX]Can you please backport 
dcraw (7.17-1) and gphoto2 (2.1.5-4ubuntu2) ?

Both are in breezy.

I would be nice to get them backported, so I can begin use my Canon 350D under ubuntu.[/QUOTE]
 Doing these now.

---

### Post by Seth on 2005-07-08
Here's gphoto2...

[http://sethkinast.com/ubuntu/hoary/backports/gphoto2_2.1.6-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gphoto2_2.1.6-1~5.04ubp1_i386.deb)

---

### Post by Seth on 2005-07-08
and dcraw :)

[http://sethkinast.com/ubuntu/hoary/backports/dcraw_7.17-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/dcraw_7.17-1~5.04ubp1_i386.deb)

---

### Post by LagoniX on 2005-07-09
Great, I try them as soon as possible.
Thanks for the quick backport. :)

---

### Post by LagoniX on 2005-07-10
Hi Seth, 
I have tried gphoto and dcraw, but I forgot to add the libgphoto2 and libgphoto2-port0 packages to the request.

I also would like a backport of gimp-dcraw. (I can start a new thread for this package, if you want that )

---

### Post by Seth on 2005-07-10
No need; I will do them tonight when I have access to my desktop again (trying to sell the house today).

---

### Post by Seth on 2005-07-11
[QUOTE=Seth]No need; I will do them tonight when I have access to my desktop again (trying to sell the house today).[/QUOTE]
 Gimp-dcraw:
[http://sethkinast.com/ubuntu/hoary/backports/gimp-dcraw_1.21-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gimp-dcraw_1.21-1~5.04ubp1_i386.deb)

---

### Post by Seth on 2005-07-11
The libs failed to build so it looks like Hoary won't support them.

---

### Post by LagoniX on 2005-07-13
Hi Seth,
[QUOTE=Seth]The libs failed to build so it looks like Hoary won't support them.[/QUOTE]
Ok, but at least I can use my RAW files now.
Thanks for the help.

---

### Post by ulisse on 2005-08-23
Seth, I got the libs compiled from official sources (here: [http://sourceforge.net/project/showfiles.php?group_id=8874&release_id=337127](http://sourceforge.net/project/showfiles.php?group_id=8874&release_id=337127) ), but I can't package them in correct .debs... I'm only able to use checkinstall  :p 
Further I don't know how to pick up the libgphoto2.port0 from inside the other packages.

If you tell me what to do (without reading hundred pages of manual) I can try.

Or even better, if you want to give it another try by yourself and post the debs directly...  :grin: :-\"

By the way, my checkinstalled packages are [here](http://ulipo.altervista.org/debs/gphoto2/), if someone wants to mess up his system... USE AT YOUR OWN RISK!
My packages doesn't update the official ones, they installs to /usr/local/; if you want to use them you have to call the commands with /usr/local/bin/.

---

