---
title: "webcam support"
date: 2004-12-02
forum: The Cafe
---

### Post by ubuntu_demon on 2004-12-02
Hi,

I think ubuntu should have an instant messenger with webcam support in some future release. Also (less important) it would be nice if msn games were supported.

---

### Post by tnoflahc on 2005-07-31
look for dMSN or Mercury Messenger.  They're both the same thing, dMSN is the old name.  The only reason why I haven't completely switched over to Linux is because of the terrible IM webcam support; I happened upon Mercury when I was trying to find an MSN client with webcam support under Mac OS X.

---

### Post by RastaMahata on 2005-07-31
but mercury is java based, and that could mean "slow" (I say it could, because I haven't tried it).

Anyway, progress is being done in webcam support (google for gaim-vv), but I dont have a clue as far as MSN games go, although it would be very cool.

---

### Post by ubuntu_demon on 2005-08-01
[QUOTE=RastaMahata]but mercury is java based, and that could mean "slow" (I say it could, because I haven't tried it).

Anyway, progress is being done in webcam support (google for gaim-vv), but I dont have a clue as far as MSN games go, although it would be very cool.[/QUOTE]
 I know .. this is an old thread. But the point still stands ... in order to attract youth we need gaim-vv + games :)

---

### Post by High Roller on 2005-08-01
[QUOTE=ubuntu_demon]I know .. this is an old thread. But the point still stands ... in order to attract youth we need gaim-vv + games :)[/QUOTE]
 Has anyone tried using MSN Messenger 7 under Wine in Ubuntu?

Apparently they've got it somewhat working.

[http://wiki.winehq.org/MSN_Messenger_webcam_support](http://wiki.winehq.org/MSN_Messenger_webcam_support)

I might give it a try...  but I'm just curious if it's as easy as the above page
makes it out to be.

I hope KMess adds more bells and whistles though.  It seems like a really
nice app with a lot of potential.

---

### Post by quickblaine on 2006-08-09
so how do i install this gaim-vv thing then?

---

### Post by ubuntu_demon on 2006-08-09
> **quickblaine said:**
> so how do i install this gaim-vv thing then?
This is an old thread.

amsn has some webcam support. IMHO that's your best bet if you want to use your webcam using msn.

ekiga has webcam support. (ekiga is installed on default)

gaim-vv will be merged into gaim. I don't know when this will happen. Maybe [http://gaim.sourceforge.net](http://gaim.sourceforge.net) has some information.

Here's some information about webcam support in Ubuntu :
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Try ekiga and amsn. I don't know much more information. Search the forums if you want to know more.

Good luck!

---

### Post by Rackerz on 2006-08-09
I always use aMSN and if needs be Kopete. But aMSN is the closest looking to MSN Messenger so it's just about a must-use for me.

---

### Post by ubuntu_demon on 2006-08-09
> **Rackerz said:**
> I always use aMSN and if needs be Kopete. But aMSN is the closest looking to MSN Messenger so it's just about a must-use for me.
offtopic :
Personally I prefer gaim. For me webcam support isn't very important. But it is for some people.

---

### Post by Bezmotivnik on 2006-08-09
> **ubuntu_demon said:**
> offtopic :
Personally I prefer gaim. For me webcam support isn't very important. But it is for some people.
It's improving, but it's still poor.

In 5.04 I couldn't get webcams to work.  Now in 6.10 they work, but wierdness still pops up -- like the smaller picture option not showing a smaller picture but rather the upper-left quarter of the large picture.  Pretty funny. :rolleyes: 

Not that anyone wants to look at or IM me anyway, but you never know, someday I may actually have a friend somewhere! :-k

---

### Post by ubuntu_demon on 2006-08-09
> **Bezmotivnik said:**
> It's improving, but it's still poor.

In 5.04 I couldn't get webcams to work.  Now in 6.10 they work, but wierdness still pops up -- like the smaller picture option not showing a smaller picture but rather the upper-left quarter of the large picture.  Pretty funny. :rolleyes: 

Not that anyone wants to look at or IM me anyway, but you never know, someday I may actually have a friend somewhere! :-k

LOL:-D

---

### Post by ubuntu_demon on 2006-08-10
Kopete does work properly with my webcam while amsn doesn't (I haven't tested it yet but someone else has the same one).

---

### Post by ldcole on 2006-08-11
How did you get your webcam to work? I first downloaded easycam2 and tried that but got "Dependency is not satisfiable: camorama"

I then tried to download camorama and install it but of course I got "Dependency blah blah blah bonobo-activation"

So I went and downloaded and installed easycam 1.35. That installed but when I try to run it as root I get "n: creating symbolic link `/lib/modules/2.6.15-26-386/build/linux-headers-2.6.15-26-386' to `/usr/src/linux-headers-2.6.15-26-386': File exists
Failed to fetch [http://blognux.free.fr.debian/dists/unstable/Release.gpg](http://blognux.free.fr.debian/dists/unstable/Release.gpg) Could not resolve 'blognux.free.fr.debian'
Failed to fetch [http://blognux.free.fr.debian/dists/unstable/main/binary-i386/Packages.gz](http://blognux.free.fr.debian/dists/unstable/main/binary-i386/Packages.gz) Could not resolve 'blognux.free.fr.debian'
E: Some index files failed to download, they have been ignored, or old ones used instead.
/usr/bin/easycam: line 88: /root/Desktop/easycam: No such file or directory
/usr/bin/easycam: line 89: /root/Desktop/easycam: No such file or directory
/usr/bin/easycam: line 90: /root/Desktop/easycam: No such file or directory
/usr/bin/easycam: line 91: /root/Desktop/easycam: No such file or directory
chown: cannot access `/root/Desktop/easycam': No such file or directory
chmod: cannot access `/root/Desktop/easycam': No such file or directory"

When I run as a normal user I get

"ln: creating symbolic link `/lib/modules/2.6.15-26-386/build/linux-headers-2.6.15-26-386' to `/usr/src/linux-headers-2.6.15-26-386': File exists
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

It finds the camera, but it just doesn't run. :-k

---

### Post by nyxtwilight on 2008-07-28
sorry to bump an old thread but i know people are still looking for an im for linux with webcam support

i found one today called qnext. [www.qnext.com](www.qnext.com)
its in java n the only thing is u need a qnext account.
basically u download it and stuff and u make an account its really quite fast acctually n u can add accounts for msn, yahoo, aim, icq jabber. but u can only video conference with someone thats got a qnext account.

i havent acctually tested out the webcam bc i ant get mine to work. i tried the sound out today n my bf could hear me clearly but the sound comin back from him was hard to understand bc it kept going away n comin back. itd be good to have somene else try it out too. i know my connection is bad n im having problems with drivers on my comp.

hope that helps :)

---

### Post by poofyhairguy on 2008-07-28
> **nyxtwilight said:**
> sorry to bump an old thread but i know people are still looking for an im for linux with webcam support

i found one today called qnext. [www.qnext.com](www.qnext.com)
its in java n the only thing is u need a qnext account.
basically u download it and stuff and u make an account its really quite fast acctually n u can add accounts for msn, yahoo, aim, icq jabber. but u can only video conference with someone thats got a qnext account.

i havent acctually tested out the webcam bc i ant get mine to work. i tried the sound out today n my bf could hear me clearly but the sound comin back from him was hard to understand bc it kept going away n comin back. itd be good to have somene else try it out too. i know my connection is bad n im having problems with drivers on my comp.

hope that helps :)

Recently the Linux kernel has added much webcam support:

[http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams](http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams)

---

