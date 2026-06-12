---
title: "Firefox 24 ESR?"
date: 2014-04-27
forum: Ubuntuzilla
---

### Post by Previous1 on 2014-04-27
I haven't found an earlier request on this. Would it be possible to add Firefox 24 ESR to the Ubuntuzilla repository? It might help in case of problems with release versions (crashing), and is an easy way out for those that don't like Australis (and its new addon interface) in the coming 29 release.  Regards

---

### Post by nanotube on 2014-04-27
Hi,
Thanks for your suggestion, but that is not currently planned. My guess is that there's probably very little demand for ESRs via ubuntuzilla.

---

### Post by Previous1 on 2014-04-28
Well there's quite a few people having crashes with FF 25+ (at least over at the Mint forums). Either  way I've tried to make my own ESR deb with [mozillapackager]("http://sourceforge.net/p/ubuntuzilla/mozillapackager/ci/master/tree/"). When asking for a version I said **latest-esr** ; it downloaded but I had to add the **15A0A4BC** gpg key (public key not found).

During extraction I got the following error:

```
Verifying checksum

firefox-24.4.0esr.tar.bz2: goed
[sudo] password for alad: 

Extracting archive

Creating Applications menu item for Firefox.

dpkg-deb: error: parsing file 'debian/DEBIAN/control' near line 2 package 'firefox-mozilla-build':
 error in 'Version' field string 'latest-esr-0ubuntu1': version number does not start with digit
dpkg-deb --build debian /media/data/Downloads/ubuntuzilla-mozillapackager-9d31da2c64f5041a4954f6c8f9ccce97b600a84d
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "mozillapackager.py", line 737, in <module>
    bs.start()
  File "mozillapackager.py", line 243, in start
    fi.start()
  File "mozillapackager.py", line 304, in start
    self.createDeb()
  File "mozillapackager.py", line 549, in createDeb
    self.util.execSystemCommand('dpkg-deb --build debian ' + self.options.debdir)
  File "mozillapackager.py", line 149, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
```
Same when I tried "latest".

---

### Post by nanotube on 2014-04-28
You should give the numeric version, since that version also goes into the debian package discription, which has to start with a number. Try entering 24.4.0esr

The package will build and will be installable with no problem... but if you are using a current ubuntuzilla build, you'd probably have to force it to downgrade...

---

### Post by Previous1 on 2014-04-28
Great, that worked. Thanks! :mrgreen:

For installation, I had to remove hunspell-en-us. I also managed to break things because I had Iceweasel (from Debian) installed ... both it and the mozilla build had a diversion to /usr/bin/firefox, resulting in a dpkg-divert error. Fixed with dpkg -r iceweasel

Cheers

---

### Post by Previous1 on 2014-04-28
after the dpkg-divert error I saw a new launcher in the xfce bar, I thought it didn't matter. But after reboot my indicator icons (network manager etc) went missing... 

edit: solved by deleting the xfce4 folders in ~/.local and ~/.config. Odd

---

### Post by nanotube on 2014-04-29
Glad it all worked out. :)
Generally though, if you just want to install it for yourself on your local box, it's probably easiest to just grab the tar.gz from mozilla, extract in your ~/bin directory, then run from there, and not even bother with the .deb packaging.
For extra goodness, I'd then place a symlink to firefox directly in ~/bin, and prepend ~/bin to your PATH. Then your default firefox will be the esr, and it'll just reside in your home directory under ~/bin
You can then use the built-in firefox updater for future updates.

---

