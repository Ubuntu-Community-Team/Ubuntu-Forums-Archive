---
title: "Delete virus from windows using ubuntu"
date: 2009-08-06
forum: Security
---

### Post by frogchris on 2009-08-06
I got a virus on window vista. Avast didn't scan or try to find where it was. It keeps redirecting me to websites on internet explorer. Is there some way I can delete the virus using ubuntu? Or do I just need to install window again. I got the virus from downloading this torrent

---

### Post by upchucky on 2009-08-06
if you are dual booting, it is very easy to remove windows virus's from the non booted windows drive with ubuntu booted.
or if you have a live ubuntu cd, boot from it

either way ubuntu can read/write the windows ntfs partition.

google the virus

the results of the search should tell you which files the virus infests.

google to find copies of infected files

delete the infected files, making sure to note where in windows they originally resided.

replace the infected files with the ones you found.

reboot to windows, if all is well be happy.

post windows repair must do....
get free drive imaging software
make image of your now pristine windows drive
store image on removable media
when windows does what it is programmed to do, (that is catch virus's)
use stored image to fix windows, do not use windows built in restore, as i have seen it also rendered useless by malware.

doing the image solution as above will restore windows no matter how badly it self destructs or malware upsets it, and will only take about 20 minutes, instead of having to spend an entire weekend reinstalling windows and all your software.

it is best to have windows on it's own partition and not let any other software be installed to the windows partition, keep your personal files and programs on a separate partition as well, that way you will never lose any files, and have a much easier time fixing shattered windows.

---

### Post by frogchris on 2009-08-06
One of the main problem is that avast didn't tell me what the virus name was. Is there some way I can find out what it is?

---

### Post by frogchris on 2009-08-06
How do I find out what the virus name is?

---

### Post by philcamlin on 2009-08-06
follow this it helps me all the time 

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=PlayList&p=8AB8BFF28E616EF0&playnext=1&playnext_from=PL&index=58](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=PlayList&p=8AB8BFF28E616EF0&playnext=1&playnext_from=PL&index=58)

use the live cd !

---

### Post by beastrace91 on 2009-08-06
I'd also like to point out that avast! has a native Linux installer (and it works quite well) I've used it multiple times to scan/fix Windows system - give it a go.

~Jeff

---

### Post by upchucky on 2009-08-06
if windows is still bootable, get AVG free antivurus, or malwarebytes, either of those should find out the name of your virus, if the virus is stealthed then a bootable usb/floppy virus finder should be used, as a stealthed one can stay in any windows file that is in current use by the os, thus when windows is booted the virus can not be removed because the file is already opened.

if you do not know the virus name, how did you come to the conclusion you have a virus? this could be an important clue....
I suspect you have been duped into thinking you have a virus by a false scan from the link you mentioned.
if the link redirected you to a site that wants to scan your system for a sum of X dollars, it is a bogus site, they will take your money and run.

---

### Post by thomps on 2009-08-06
If you can boot into Windows and have internet access, this online scanner works pretty well and should be able to tell you the name of the virus.

[http://housecall.trendmicro.com/]("http://housecall.trendmicro.com/")

---

### Post by frogchris on 2009-08-07
I found out that it wasn't a virus just that my search engine has been hijacked. Do you know how I could fix this.

This is the website that hijacked me smartbizsearch.com

---

### Post by HermanAB on 2009-08-07
Go to Majorgeeks and search their site for Hijackthis.  Run it and remove the browser HBO related cruft that it sees.

---

