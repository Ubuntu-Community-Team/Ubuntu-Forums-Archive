---
title: "Support for non-free Bible software"
date: 2007-05-03
forum: Ubuntu Christian Edition
---

### Post by naked on 2007-05-03
I'd like to see CE work with non-free software as well.  I use Bibleworks (6 and 7) and while 6 works ok, 7 has been difficult to install.  I an advocate for CrossOver Office, and so this is the method of installation I use.  But, support for Logos, Paratext, and other commercial programs that can aid people in their study and in the translation of the Word.

Not sure how possible this is, since these are programs you have to pay for, but maybe they would donate a copy to have them work properly in Linux?  Several friends who work with various companies for Bible translation have been trying desperately to get Paratext to work with some other small pieces of software to no avail.  I've also had no luck in with Paratext.

Any thoughts?

L

---

### Post by uconvert on 2007-07-12
AMEN! 

I have over $1000 invested in various Bible Study Programs and I would pay to have Bibleworks 7 successfully installed in Ubuntu!

Here's what works for me using Codeweaver Crossover 6.0 Professional - I have a separate ext3 partition for Crossover and Win Apps

Bible Companion Series Professional 2000 ( I use it for the Concordant Literal Version)(Must be installed in a Fat32 partition in a win98 bottle)

Bibleworks 5.0 (I installed in my Bible Companion win98 bottle but you have to install IE6 first so that it recognizes an HTML engine for internet updates).

Biblesoft PC Study Bible 3.1 (Install in a win98 bottle)

Interlinear Scripture Analyzer (Install in an xp bottle)

I have yet to find a glitch with this configuration!

---

### Post by jonathonblake on 2007-07-13
> **naked said:**
>  support for Logos, Paratext,

Getting Logos to run would be nice.  There are a couple of significant issues on the way. Internet Explorer 6.0 (or higher) is required.  Required RAM is going to be much closer to 4GB than their recommended 512 MB.  (They should have raised minimum to 512 and 2 GB recommended.)   

> have been trying desperately to get Paratext to work with some other small pieces of software to no avail.  I've also had no luck in with Paratext.

The stated minimum requirements for Paratext don't imply any issues in getting it to run on Linux.  (Win98 SE with 32 MB RAM.)  It might be easier to to include the functionality that Paratext has in Omega-T, rather than figure out why Paratext doesn't work in WINE. 

> Interlinear Scripture Analyzer 
Maybe an installer package could be created for it, the way that it was done for e-Sword.

I'm also wondering if these programs wouldn't require either an NTFS or a FAT32 partition rather than a "native" Linux partition. 

xan

jonathon

---

### Post by nymusicman on 2009-04-26
I've never used the big guys so I don't know what features I'm leaving out by recommending the following.

Good bible program for reading and dictionary work (at least for me) - xiphos (previously gnomesword2). 

Great bible program for searching is bibleanalyzer (although it does not yet work with jaunty and you have to go to the forums for the most up to date linux version which is equal by the way to the most up to date windows version.).

These are my linux recommendations. I know I said I don't know what features would be missing by using open source software but this is what I use anyway.

---

### Post by jonathonblake on 2009-04-27
> **nymusicman said:**
> I've never used the big guys

Take a look at what Libronix or Accordance offers in the way of resources.  There is a reason why Seminaries require one of those two programs. 

>  so I don't know what features I'm leaving out by recommending the following.

Missing tools include sentence diagramming, reverse interlinears, custom mapping, on the fly morphological analysis, sermon construction tools, lectionaries, etc, etc, etc.   

jonathon

---

### Post by ag65151 on 2009-04-29
> Missing tools include sentence diagramming, reverse interlinears, custom mapping, on the fly morphological analysis, sermon construction tools, lectionaries, etc, etc, etc.

Does anyone know of any Linux tools that do all this? I would love to be able to do this on my Linux box (especially sentence diagramming).

Thanks

---

### Post by jonathonblake on 2009-05-02
> **ag65151 said:**
> Does anyone know of any Linux tools that do all this? 

I've seen some on sourceforge, but they were half finished.

jonathon

---

### Post by refdoc on 2009-05-11
> Several friends who work with various companies for Bible translation have been trying desperately to get Paratext to work with some other small pieces of software to no avail. I've also had no luck in with Paratext.

1) I got paratext 6 to run kind of on Linux with Wine. Some error messages, but never crashing
2) Have a look at bibledit, which started out as paratext clone but is now much beyond that. I think in terms of features it is probably same/superior in some aspects + it is getting released every few weeks with more stuff.

New bibledit packages are in a ppa

[http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu)

---

### Post by DirkL on 2009-11-16
I, too, would dearly love to get Paratext 6 working under Ubuntu.

My current installation is Intrepid (standard version with Gnome) plus:
wine upgraded to current beta version from winehq
mono-runtime
winetricks mcv40

Paratext, Source Language Tools and the Paratext 6.1 upgrade have been installed.
Patatext comes up but can't display anything: error 445 (which I understand some
e-Sword users also encountered.)

---

### Post by jonathonblake on 2009-11-16
> **DirkL said:**
> I
Patatext comes up but can't display anything: error 445 (which I understand some  e-Sword users also encountered.)

Completely uninstall ParaText.  Then use the e-Sword installation script to install the program.  Treat it as if it was a manual resource for e-Sword.  

jonathon

---

### Post by DirkL on 2009-11-17
Since uninstalling Paratext via the uninstaller seems not to remove any files from .wine/drive_c, I move the old .wine.  After some experimentation, I have reduced installing e-Sword to the following steps:

1. Make sure wine and cabextract are installed.
2, Download winetricks and make it executable.  

Start with no ~/.wine directory.

3. winetricks msls31 riched20 vcrun6 corefonts
4. setup951.exe

I can now run e-Sword and make annotations with Rich Text enhancements (bold, italics, underline, colour)
which are saved automatically.

However, my expertise is not enough to follow the rest of Jonathan's hint.  I tried running the e-Sword installer again, but it can't see the Paratext installer.  Or should I supply PTW6.EXE to the installer?  I don't know how to do that either.

What I do know is that those winetricks are not enough to make Patatext display.

---

### Post by jonathonblake on 2009-11-17
> **DirkL said:**
> I tried running the e-Sword installer again, but it can't see the Paratext installer. 

The  third option in the list is "manual".  Check that, then start, and when it asks for the resource, select the paratext installer.

jonathon

---

### Post by david_kt on 2009-11-17
> **DirkL said:**
> Since uninstalling Paratext via the uninstaller seems not to remove any files from .wine/drive_c, I move the old .wine.  After some experimentation, I have reduced installing e-Sword to the following steps:

1. Make sure wine and cabextract are installed.
2, Download winetricks and make it executable.  

Start with no ~/.wine directory.

3. winetricks msls31 riched20 vcrun6 corefonts
4. setup951.exe

I can now run e-Sword and make annotations with Rich Text enhancements (bold, italics, underline, colour)
which are saved automatically.

However, my expertise is not enough to follow the rest of Jonathan's hint.  I tried running the e-Sword installer again, but it can't see the Paratext installer.  Or should I supply PTW6.EXE to the installer?  I don't know how to do that either.

What I do know is that those winetricks are not enough to make Patatext display.

Jonathan is talking about installer downloaded from below thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

But to use that installer, first you must install e-Sword using that installer, and then choose "manual" to install Paratext.

DK

---

### Post by steven_liauw on 2009-11-18
I have Bible Works 7, does anyone know whether I can install this into Ubuntu 9.10 using Wine? 

If some of you have succeeded, can you tell me which version of Wine to use?

Thanks

---

### Post by DirkL on 2009-11-19
[quote=david_kt;8334641]Jonathan is talking about installer downloaded from below thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

But to use that installer, first you must install e-Sword using that installer, and then choose "manual" to install Paratext.
-------------------------------------------------

I have spent a day on this, but let's forget the gory details.  Suffice to say that e-Sword installs painlessly every time but Paratext showed a wide variety of DLL load problems.  Maybe one should have an exact match on the Wine release instead of installing the latest version.  What combination of software worked?

Maybe one gory detail after all: every Paratext failed, I added the first missing DLL to be native in WINEDLLOVERRIDE, with WINEDLLPATH pointing to D:\windows\system32, and D: is a drive with a legal XP installation.  I didn't reinstall Paratext after each such increment, just tried running the binary.  I even made one experiment overriding every available DLL - not successful.

Actually, it should be a simple question of which DLL's to override.  After all, that is all that winetricks or its descendant e-sword-installer does. But finding that out by experiment has been heavy going.

Dirk

---

