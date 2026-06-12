---
title: "using ubuntuzilla to install firefox/thunderbird betas?"
date: 2007-11-29
forum: Ubuntuzilla
---

### Post by asaturn on 2007-11-29
is this possible? (to use ubuntuzilla to install beta or pre-releases of mozilla software)?

---

### Post by nanotube on 2007-11-29
> **asaturn said:**
> is this possible? (to use ubuntuzilla to install beta or pre-releases of mozilla software)?

according to the dir listing on the releases server ([ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/))
firefox 3.0b1 is available on the releases server, so it is possible 

first step: since the beta is in tar.bz2 and not in tar.gz, you have to change line 658 of the ubuntuzilla.py script from 
```
self.packageFilename = self.options.package + "-" + self.releaseVersion + ".tar.gz"
```
to 
```
self.packageFilename = self.options.package + "-" + self.releaseVersion + ".tar.bz2"
```

and also change line 447 from
```
self.util.execSystemCommand(executionstring="sudo tar -C " + self.options.targetdir + " -xzf " + self.packageFilename)
```
to
```
self.util.execSystemCommand(executionstring="sudo tar -C " + self.options.targetdir + " -xjf " + self.packageFilename)
```

then, run 
```
ubuntuzilla.py -a install -p firefox
```
and when it asks you whether the latest version 2.0.0.10 is correct, say no, and enter version manually. 
enter 3.0b1 as the version.

that will install the beta. 

of course, since the update checker only checks for actual releases, you won't get the update notifications when new betas are released, you'll have to take care of keeping track of new betas manually.

as you might guess by now, this is not a "supported" operation, so the "at your own risk" disclaimer applies. :)

let me know how it goes - especially if you encounter any problems, but also just to report that everything went as planned. :)

---

### Post by bigern75 on 2007-12-01
even if you change those lines, it will not find [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/)

If I wanted to add that to the script, where at?
Line 193 maybe?

---

### Post by nanotube on 2007-12-01
> **bigern75 said:**
> even if you change those lines, it will not find [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/)

If I wanted to add that to the script, where at?
Line 193 maybe?

unfortunately, not that simple :)
193 is simply the default for the server config option - you don't even have to change it, as you can specify it as commandline arg. (there's a slight problem with that, though- i've been sloppy and hardcoded releases.mozilla.org in a few places throughout the code... but should be easy enough to search-replace and fix)

the problem is the path and filename details, which are different for the nightlies as well. 

here are the differences that i can spot off-hand.
the path for nightlies is ```
/pub/mozilla.org/<package>/nightly/<somedatestamp>/<package>-<version>.en-US.linux-i686.tar.bz
```

the releases path structure is as follows:
```
/pub/mozilla.org/<package>/releases/<version>/linux-i686/<localization>/package-version.tar.gz
```

so there'd have to be a few places to take care of all the path differences for the download, and also change filename structure

also have to cut out the localization selector (nigthlies are all en-US)

also cut out gpg sig verification, as these don't seem to exist for the nightlies

and create a parser somewhat similar to localization selector to allow you to select the nightly that you want (or auto-choose the latest).

so if you were to implement it, i'd suggest deriving a new subclass from the basic mozillainstaller, and coding in a separate "nightlyinstaller" with all that, it would be cleaner.

if you want to start on that, i'd be glad to help you out, and maybe add the changes to the official release when it's done. or you could wait and see if i get motivated enough to make it myself. :)

---

### Post by m10 on 2007-12-04
@nanotube
I  just wonted to let you know that such a feature would be much appreciated (at least from my side!) :)

---

### Post by nanotube on 2007-12-04
> **m10 said:**
> @nanotube
I  just wonted to let you know that such a feature would be much appreciated (at least from my side!) :)

heh, thanks for putting in your vote :)

---

