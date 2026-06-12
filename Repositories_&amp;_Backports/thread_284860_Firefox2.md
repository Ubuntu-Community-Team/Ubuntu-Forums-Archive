---
title: "Firefox2"
date: 2006-10-26
forum: Repositories &amp; Backports
---

### Post by johnmd on 2006-10-26
Can anyone tell me when Firefox 2 will be on the repositiory and if it isn't can I install the version on the Firefor web site without messing everything up??
I'm running Ubuntu 6.06

John

---

### Post by tuxy on 2006-10-27
Yes u can download it from the firefox website & install it on Ubuntu6.06. It worked fine for me without any hassle. It even imports all your bookmarks. The only thing I found strange in Firefox 2.0 with Ubuntu DD is the fonts are a little bit different than they used to be in Firefox 1.5.

You also have to link the Firefox executable script with the one you have in PATH or else you will get the old one when you click the Firefox icon from the menu.

---

### Post by eyyuplu on 2006-10-27
> **tuxy said:**
> 

You also have to link the Firefox executable script with the one you have in PATH or else you will get the old one when you click the Firefox icon from the menu.
hi
how can &#305; do :link the Firefox executable script with the one you have in PATH or else you will get the old one when you click the Firefox icon from the menu.
&#305; want use firefox2 from desktop.but only &#305; can use /home/frefox.

---

### Post by tuxy on 2006-10-28
Try this:
ln -s /<where ever the firefox is installed>/firefox/firefox /usr/bin/firefox
or you can delete the old one from /usr/bin and try the above command.

---

### Post by TheForkOfJustice on 2006-10-28
Can't you just copy over the folder belonging to the 1.5.0.7 version and replace the files with the 2.0 version?

EDIT

And how do I install this darned thing?

---

### Post by eyyuplu on 2006-10-28
> **tuxy said:**
> Try this:
ln -s /<where ever the firefox is installed>/firefox/firefox /usr/bin/firefox
or you can delete the old one from /usr/bin and try the above command.
ok. &#305; will try this.but there is firefox(1.5.7) folder  in /usr/bin.(/usr/bin/firefox(1.5.7) ) .. am &#305; change this name?or change name firefox2.0 ( home/mmmtt/firefox/firefox)
 ls -s  /home/mmmtt/firefox/firefox2.0 /usr/bin/firefox2.0
(sorry my english not very well)

---

### Post by tuxy on 2006-10-28
remove the 'firefox ' in /usr/bin and execute the command which I given to you earlier.

---

### Post by Unicast on 2006-10-29
It is there isn't it?

This is my **sources.list** file:

```
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe 

deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 

## Ubuntu
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse 

## Updates
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse 

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 
```

Hope this helps. :D

---

### Post by aysiu on 2006-10-29
This script automates the whole process:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It downloads the latest Firefox, extracts it, gives it its own directory, symlinks it to /usr/bin/firefox and symlinks your plugins to the new Firefox you've just installed.

---

### Post by TheWizzard on 2006-10-29
> **aysiu said:**
> This script automates the whole process:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It downloads the latest Firefox, extracts it, gives it its own directory, symlinks it to /usr/bin/firefox and symlinks your plugins to the new Firefox you've just installed.

but does anyone know why ff 2.0 is not in the backport repos? :-k 
in an ideal situation i could be using dapper for 3 year while having the latest software...  at least, this is how it worked in red hat / fedora.

---

### Post by danhm on 2006-10-31
> **Unicast said:**
> It is there isn't it?

This is my **sources.list** file:

```
<sources> 
```

Hope this helps. :D

You're using Edgy, not Dapper. 



Anyway, I'd recommend installing [url=http://getswiftfox.com/], an optimized Firefox build (assuming they have your processor arch, which they probably do).

---

### Post by TheForkOfJustice on 2006-11-03
> **TheWizzard said:**
> but does anyone know why ff 2.0 is not in the backport repos? :-k 
in an ideal situation i could be using dapper for 3 year while having the latest software...  at least, this is how it worked in red hat / fedora.

Ubuntu's repositories are notoriously outdated. They need a team that keeps packages in the repos current but I think they are spending too much time on Edgy to pay much attention to Dapper's QC. probably why those bad updates happened a while back.

I should NOT be relying so much on Automatix when Azureus is in the repos. But the repos is out-dated and Automatix is current. The choice is clear.

The repos, IMHO, is what is keeping Ubuntu from being really dynamite.  It needs better (or ANY) management.

BTW, Automatix also has Swiftfox and the common Swiftfox plugins ;)

---

### Post by Efwis on 2006-11-04
> **aysiu said:**
> This script automates the whole process:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It downloads the latest Firefox, extracts it, gives it its own directory, symlinks it to /usr/bin/firefox and symlinks your plugins to the new Firefox you've just installed.
the only thing this script doesn't do is make FF2 the default browser, this can be handled by doing the following easy steps.

right click on your firefox browser icon, then choose properties,where the command is located click on the browse button and navigate to /opt/firefox/ and then choose firefox, so it should look like this after you choose it.

```
/opt/firefox/firefox
```

next start the browser from the icon you just changed, it will ask you if you want to make it your default browser, choose yes and everytime you open firefox it automatically opens it in FF2.

Hopefully they will get it in the repos soon so it will update the original FF throughout DD.

---

### Post by aysiu on 2006-11-05
If Firefox was already the default browser before you ran the script, it will be afterwards as well. The script symlinks the new Firefox to the /usr/bin/firefox path.

---

### Post by TheForkOfJustice on 2006-11-09
Honestly, it shouldn't be such a long process to add Firefox 2.

Should be a simple matter.

---

### Post by aysiu on 2006-11-09
> **TheForkOfJustice said:**
> Honestly, it shouldn't be such a long process to add Firefox 2.

Should be a simple matter. It is a simple matter--run the script.

---

### Post by TheWizzard on 2006-11-09
> **aysiu said:**
> It is a simple matter--run the script.

i tend to agree with TheForkOfJustice. FF2 should be included in the backports repo for dapper. 

btw is there a way to submit packages for the backports? i'm willing to make a FF2 package for the backports, but i can't find where to submit.

---

### Post by alienexplorers on 2006-11-13
I just did it the easy way. I downloaded firefox 2.0, bon echo 2.0, minefield 3.0a1 to the opt directory. I untared them to files named Firefox2, Bon Echo 2, and minefield3a1.  From there i went into each directory and ran ./firefox -profilemanager and set up each account it's own profile.  I then made launchers on the desktop to load the programs.  In the launchers I put /opt/firefox# -P "profile name".  I did this with all 3 builds and now have access to all of them.

---

### Post by savohead on 2006-11-13
yeah right, should be easier and in the repos, but i'm going to format and update to edgy, isn't version 2 already in edgy basic installation?! so, everybody update to edgy!!! eheh jokin'

---

### Post by TheWizzard on 2006-11-13
> **aysiu said:**
> It is a simple matter--run the script.

i didn't succeed in making a deb file. mozilla uses quite some non-standard stuff :confused: 

so i used aysiu's script and it worked like a charm :D

---

### Post by The Warlock on 2006-11-17
Firefox 2.0 is not in the Dapper backports for the same reason that FF1.5 was not in the Hoary backports. A whole bunch of packages depend on the rendering engine in FF1.5 and those would also need to be upgraded and at that point the backports repository really might as well be the Edgy repositories. If you want the latest version of FF, you need to either install it outside of the repositories, i.e. with the script posted earlier, or you need to upgrade to Edgy.

---

### Post by JohnPhys on 2006-11-25
Can anyone else confirm what Warlock is saying?  I remember FF 1.5 not being available in Breezy, but I wasn't aware of the reason for it.  

Are the devs looking at any way to put FF2 in the dapper backports or is not even a possibility?

---

