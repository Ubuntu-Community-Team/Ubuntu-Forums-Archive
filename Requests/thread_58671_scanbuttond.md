---
title: "scanbuttond"
date: 2005-08-21
forum: Requests
---

### Post by chaumurky on 2005-08-21
[http://scanbuttond.sourceforge.net/](http://scanbuttond.sourceforge.net/)

From the site:

*"Modern scanners usually have several front panel buttons which are intended to trigger certain actions like copying, faxing or mailing the scanned document. Unfortunately, the software which monitors the buttons and starts the appropriate programs is in most cases only available for a certain proprietary operating system. This project is an attempt to create a similar piece of software for Linux (and probably other Unix-like systems). This daemon queries the scanner button status several times per second. If it detects that a button is pressed, it runs a shell script which the button number is passed to as a command line argument. Because scanbuttond is accessing the scanner directly via libusb, there should be no conflicts with SANE or other scanner drivers: scanbuttond simply won't touch the scanner hardware while you are using SANE. This means that you can still scan even when running scanbuttond."*

I'd love to see this available for Ubuntu!

---

### Post by chaumurky on 2005-09-14
[QUOTE=chaumurky][http://scanbuttond.sourceforge.net/](http://scanbuttond.sourceforge.net/)

From the site:

*"Modern scanners usually have several front panel buttons which are intended to trigger certain actions like copying, faxing or mailing the scanned document. Unfortunately, the software which monitors the buttons and starts the appropriate programs is in most cases only available for a certain proprietary operating system. This project is an attempt to create a similar piece of software for Linux (and probably other Unix-like systems). This daemon queries the scanner button status several times per second. If it detects that a button is pressed, it runs a shell script which the button number is passed to as a command line argument. Because scanbuttond is accessing the scanner directly via libusb, there should be no conflicts with SANE or other scanner drivers: scanbuttond simply won't touch the scanner hardware while you are using SANE. This means that you can still scan even when running scanbuttond."*

I'd love to see this available for Ubuntu![/QUOTE]
 Not a popular idea? Or is there something similar already in Ubuntu? This could really be a WAF booster... ;-)

---

### Post by coolaj86 on 2005-10-14
you should be able to compile it for ubuntu without issue.

I'll try it tomorrow and get back to you on it. I'll see if I can't get the maintainer to post a binary version and we can get some betters documentation up (currently instructions on the Gentoo wiki should work for all distros).

[http://gentoo-wiki.com/index.php?title=HOWTO_Scanner_buttons_and_one-touch_scanning_with_Linux](http://gentoo-wiki.com/index.php?title=HOWTO_Scanner_buttons_and_one-touch_scanning_with_Linux)

---

### Post by chaumurky on 2005-10-14
[quote=coolaj86]you should be able to compile it for ubuntu without issue.

I'll try it tomorrow and get back to you on it. I'll see if I can't get the maintainer to post a binary version and we can get some betters documentation up (currently instructions on the Gentoo wiki should work for all distros).[/quote]

I got it going. Had some fun learning some things along the way. It would be great to have an easier install with a Ubuntu binary available. It's funny - with the script, you can make the button trigger anything!

---

### Post by coolaj86 on 2005-10-14
I figured out how to create .debs  for Ubuntu:
[https://wiki.ubuntu.com/CreateDebPackageHowto](https://wiki.ubuntu.com/CreateDebPackageHowto)

So I created one and posted the link for scanbuttond here:
[https://wiki.ubuntu.com/UserContributedDebs](https://wiki.ubuntu.com/UserContributedDebs)

---

### Post by chaumurky on 2005-10-14
I love this community!!

---

### Post by bwrutter on 2006-02-10
make sure the "libusb" is installed fully for this package to work.
with breezy I still had to do...

"apt-get install libusb-dev"

to get libmeta in /usr/local/lib/scanbuttond to load...

---

