---
title: "Install on debian"
date: 2009-06-20
forum: Ubuntuzilla
---

### Post by renji3 on 2009-06-20
Is it possible to use ubuntuzilla on Debian?

I've installed the .deb file on Debian 5.0.1 (32bit). But since firefox is not available on debian repositories, the script doesn't find the package and stops running at that step. The following is the output I get when running the script:

[COLOR=RoyalBlue]Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

apt-cache --names-only search '^firefox$' | grep '^firefox'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
apt-cache --names-only search '^mozilla-firefox$' | grep '^mozilla-firefox'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Unable to the repository package name for firefox. Please look it up in your package manager and enter it manually here: [/COLOR]

[COLOR=Black]I've tried by pasting the original tar.gz downloaded from firefox homepage (in the /tmp folder), but still no luck. Any ideas would be appreciated :-)[/COLOR]

---

### Post by kerry_s on 2009-06-20
> Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

kinda tells you right there.

down load it unpack it, move it where you want and create the firefox link in /usr/bin
or just set it up right in your home folder, i would do it in home.

---

### Post by nanotube on 2009-06-24
Hi
well, it may be possible to modify the script to work on debian... but it's probably too much trouble. just follow the advice of kerry_s, and get it manually. :)

---

