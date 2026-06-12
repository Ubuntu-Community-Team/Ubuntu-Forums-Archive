---
title: "I've tried, and tried, and tried -- can't fix repository problem (error code 1)..."
date: 2007-04-02
forum: Repositories &amp; Backports
---

### Post by Phrawm48 on 2007-04-02
I've tried all the usual, "normal" fixes and can't get rid of this error.  Please read the entire post before suggesting the usual fixes.

Running Dapper, about five days ago I started receiving the following error message from Synaptic (line breaks added for readability:

> [http://archive.ubuntu.com/ubuntu/dists/]("http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:") [*line break added for redability*]
[dapper-updates/main/binary-i386/Packages.gz:]("http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:") [*line break added for redability*]
Sub-process gzip returned an error code (1)
As best I can tell, this is the line in my */etc/apt/sources.list* file (also attached)  that's producing the problem:

```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```If I view [COLOR=Blue]_**[the error message's URL]("http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz")**_[/COLOR] in my Web browser I get a big file that contains lots of these sorts of entries:

> Package: acpi-support
Priority: optional
Section: admin
Installed-Size: 724
Maintainer: Matthew Garrett <mjg59@srcf.ucam.org>
Architecture: i386
Version: 0.85
Depends: xset, laptop-mode-tools, acpid (>= 1.0.4-1ubuntu4), hdparm, lsb-base (>= 1.3-9ubuntu3), vbetool, radeontool, toshset, smartdimmer, finger, powermgmt-base, laptop-detect, dmidecode (>= 2.7-1)
Filename: pool/main/a/acpi-support/acpi-support_0.85_i386.deb
Size: 31120
MD5sum: d0585a982a4ccb7fdfae31281c0d49b0
SHA1: 3725b8631f7bb2958fd07568e83e11430961bb85
SHA256: 61b6481c9ec1b9913b9f41df4e889b663498973d6d22d999268851d3ff3f5cd7
Description: a collection of useful events for acpi
 The scripts included in acpi-support include events for lid closure
 and loss and gain of ac power. These are the only events that can be
 supported with any level of safety cross platform.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

* ...many more such entries...*
I've also tried using all of the following pages (and then some) to "reset" my repositories to putatively known-good values:[LIST]
[*][COLOR=Blue]**[my recommended Dapper sources.list]("http://www.ubuntuforums.org/showthread.php?t=185758")**[/COLOR]
[*][COLOR=Blue]**[Having (repository) troubles with your current Dapper sources.list ?]("http://ubuntuforums.org/showthread.php?t=234346")**[/COLOR]
[*][COLOR=Blue]**[Repo error: "Sub-process gzip returned an error code (1)"]("http://ubuntuforums.org/showthread.php?t=397725")**[/COLOR]
[*][COLOR=Blue][URL="http://www.psychocats.net/ubuntu/sources"][B]Enabling Extra Repositories
[/B][/URL][/COLOR][/LIST]But since all of these threads point to *deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted*, the error remains.

Long story short, I've tried all the usual steps and can't resolve this persistent "error 1".  Can anyone please suggest a "next highest" approach to clearing this error?

Cheers & thanks,
Ric

---

### Post by gborzi on 2007-04-02
Have you tried to use some mirror for the updates ? I mean, have you tried to use > deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
note the *it* before *archive*, it's the Italian mirror. The mirror's http addresses have the two-letter code of the country where they are located before *archive*.
Reading the gzip manpage I saw that the error "not in gzip format" means that the file is not gzipped, as if it gets gunzipped before reaching you system.

Hope this helps.

---

### Post by Phrawm48 on 2007-04-02
Giuseppe:

Grazi!  Using the following lines from my */etc/apt/sources.list* file, Synaptic runs without error (line numbers added to example for ease of reference):

> 
3
4 ## Major bug fix updates produced after the final release of the distribution.
5 ## OKAY -- Commenting out following line clears "gzip error 1" problem.  RBV, 2007-04-02
6 # deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
7 
8 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
9 ## Adding following line to test whether this Italian mirror reposoitory also produces an error.
10 deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
11
So commenting out line **6** clears the error, and the Italian mirror archive specified by line **10** runs without error.

OK -- Now what should I do?  Is the problem exclusively mine, or should someone be notified, or...?

Cheers & thanks 'gain,
Ric
SFO

---

### Post by gborzi on 2007-04-03
> **Phrawm48 said:**
> 

OK -- Now what should I do?  Is the problem exclusively mine, or should someone be notified, or...?



I cannot check if I have the same problem using the US repositories, because I'm using edgy, not dapper, so I can't say if it's only your problem. Have you searched the forums to see if some else has the same problem ? As for filing a bug report, the problem is that this is not a bug in a program, it is a "bug" in the repositories. I suggest you to register to launchpad and ask a question here [https://answers.launchpad.net/](https://answers.launchpad.net/) .

Regards.

---

### Post by oerd on 2007-04-07
This just solved my problem too. I am using the italian mirror now, and gzip can unzip packages file all right. Grazie mille, Giuseppe!
It would also be very normal for me to use the italian mirror since i **am** in Italy. :)

BTW, I had this problem in Edgy. And fixing the mirror site fixed it.

---

### Post by IanW on 2007-04-09
From what I've googled, this is generally caused by interweb connection problems (timeouts etc).
To fix it, try deleting the failed partial downloads by running:- 
```
sudo rm -v  /var/lib/apt/lists/partial/*
```
Then rerun the update.

---

### Post by Phrawm48 on 2007-04-09
Ian:

Thanks -- this is great information.

For what it's worth, my partial directory was empty, so I can only conclude that I have yt to isolate the cause of my problem.

I say "evidently" because I've left the "Italian Circumvention" in place on my computer.  Presumably at some point it too will malfunction at which point I'll try reverting...

Cheers & thanks,
Ric
SFO

---

### Post by gborzi on 2007-04-09
@IanW: thanks for the information.

@Phrawm48: I find the name "Italian Circumvention" for the workaround amusing. It sounds like the title of a movie.

---

