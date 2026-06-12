---
title: "Error during installing firefox"
date: 2011-03-08
forum: Ubuntuzilla
---

### Post by Wolfcry on 2011-03-08
Running 64-bit system.

When I try installing firefox I get thiss error:


mikael@mikael-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.8.3

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1331, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 311, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 354, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 764, in install
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 956, in getLatestVersion
    self.releaseVersion = re.search(r'firefox\-(([0-9]+\.)+[0-9]+)',self.releaseVersion).group(1)
AttributeError: 'NoneType' object has no attribute 'group'


How do I fix this?

---

### Post by nanotube on 2011-03-08
Hi
The python script is really deprecated now, I suggest you use some other way to get firefox. I see that you're using 64bit, i suggest you try one of the other solutions suggested on [https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)

If you really want to use the script - mozilla recently changed their website layout a bit, so the script needs a one-line tweak to make it work again. But you really would be better off using one of the alternatives.

Also if you're running Lucid or later, the official repos should have the latest.

---

### Post by Wolfcry on 2011-03-08
Hmm. Ok. :)

I tried to install this to get FoxyTunes to work. It says that my version of Firefox doesn't support it ant that I should install the latest version in order to get it working.

I've tried a few different solutions, but none of them worked...

---

