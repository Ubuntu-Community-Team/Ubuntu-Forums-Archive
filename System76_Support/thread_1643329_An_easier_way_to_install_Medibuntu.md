---
title: "An easier way to install Medibuntu"
date: 2010-12-11
forum: System76 Support
---

### Post by HotShotDJ on 2010-12-11
I know this isn't really specific to System76.  I've written a simple BASH script to simplify installing Medibuntu repositories and getting libdvdcss2 and multimedia codecs installed.  When run, it will display a copyright/patent warning (taken from [HERE]("https://help.ubuntu.com/community/Medibuntu")), then it will install the Medibuntu repositories along with libdvdcss2.  Next, it detects the system's architecture and installs the appropriate multimedia codecs (w32codecs, w64codecs, or ppc-codecs).

What I wanted was an easier way to get these things up and running when installing Ubuntu (or helping others do it).  My experience is that new users have anxiety attacks when they see the long line of code given in most tutorials.  Perhaps it could be integrated into the System76 driver (I don't know the legal ramifications of doing so).

I've tested it on several systems, and it has worked for me.  If others can test and let me know if there are problems, I'd appreciate!  I hope this is useful to others.

---

### Post by tlroche on 2010-12-13
> **HotShotDJ said:**
> I've written a simple BASH script to simplify installing Medibuntu repositories and getting libdvdcss2 and multimedia codecs installed. [...] If others can test and let me know if there are problems, I'd appreciate!

I tested a variant on a star1 running lucid on which restricted formats had not yet gotten installed, and it produced the desired results (i.e. playing a DVD). FWIW the script below is the same as that HotShotDJ compressed above, except

[LIST]
[*]I'm listing inline, since IMHO this is not long enough to warrant compression and attachment
[*]I added a comment pointing to this thread
[*]s/apt-get/aptitude/g                           (I prefer aptitude)
[*]s/--yes/--assume-yes/g                         (both support '--assume-yes', only apt-get supports '--yes')
[*]s/--allow-unauthenticated/--allow-untrusted/g  (neither supports same syntax)
[/LIST]

```
#!/bin/bash
# adapted from http://ubuntuforums.org/showthread.php?t=1643329
# Medibuntu installation script
# Public Domain

# Patent and Copyright Warning
shopt -s nocasematch
echo
echo "This script will install the Medibuntu repository of packages that cannot be"
echo "included in the Ubuntu distribution for legal reasons (copyright, license,"
echo "patent, etc.)"
echo
echo "Patent and copyright laws operate differently depending on which country you"
echo "are in. Please obtain legal advice if you are unsure whether a particular"
echo "patent or restriction applies to a media format you wish to use in your country."
echo
read -p "Do you wish to continue? (Y/N): "

case $REPLY in
y|yes) # If Yes, Continue with script
  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo aptitude --quiet update && sudo aptitude --assume-yes --quiet --allow-untrusted install medibuntu-keyring && sudo aptitude --quiet update
  sudo aptitude --assume-yes install app-install-data-medibuntu apport-hooks-medibuntu && sudo aptitude --assume-yes --quiet dist-upgrade && sudo aptitude install libdvdcss2

# Detect Architecture and install appropriate software
  case `uname -m` in
  i?86|k7)
    sudo aptitude install w32codecs
    ;;
  x86_64)
    sudo aptitude install w64codecs
    ;;
  ppc|ppc64)
    sudo aptitude install ppc-codecs
    ;;
  *)
    echo
    echo "I can't find multimedia codecs for `uname -m`"
    ;;
  esac ;;
 
*) # If not Yes, terminate script
  echo "You must answer Yes to continue.  Terminating script"
  ;;
esac

```

FWIW, Tom Roche [Tom_Roche@pobox.com]

---

