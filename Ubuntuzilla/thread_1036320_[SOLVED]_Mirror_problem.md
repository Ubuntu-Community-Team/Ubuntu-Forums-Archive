---
title: "[SOLVED] Mirror problem"
date: 2009-01-10
forum: Ubuntuzilla
---

### Post by Robbyx on 2009-01-10
Ubuntu 8.10 Intel 2 core 32 bit

I have not been able to get ubuntuzilla.py to work. It fails with the following report:

   >  Connecting to sunsite.rediris.es|130.206.1.5|:21... connected.
    Logging in as anonymous ... Logged in!
    ==> SYST ... done. ==> PWD ... done.
    ==> TYPE I ... done. ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-GB ... done.
    ==> SIZE thunderbird-2.0.0.19.tar.gz ... 11235715
    ==> PASV ... done. ==> REST 11235715 ... done.
    ==> RETR thunderbird-2.0.0.19.tar.gz ... done.
    thunderbird-2.0.0.19.tar.gz: Permission denied
    wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://sunsite.rediris.es/pub/mozilla.or](ftp://sunsite.rediris.es/pub/mozilla.or) ... .19.tar.gz
    Previous command has failed to complete successfully. Exiting.
    Process returned code 1
    Error downloading. Trying again, hoping for a different mirror.
    Download failed. This may be due to transient network problems, so try again later. Exiting.



This error message happens for each mirror it uses.

How do I install it manually without a script, but in such a way that it will be updated by the repository when its version is later than the one I am installing?

Alternatively is there a revised script.

Robin

---

### Post by blackdown on 2009-01-10
Visit [http://launchpad.net/ubuntu/+archivemirrors](http://launchpad.net/ubuntu/+archivemirrors) and edit your script with mirrors you whant.

---

### Post by nanotube on 2009-01-10
Hi,
first, ignore the post above, that lists the ubuntu repos mirrors, not mozilla mirrors.

second, try it again - i just tried a test run myself, everything worked, so maybe you had some network problems or something was up with the mirrors...

third, if it still fails, well, it's not possible to install it manually, and that you'll get updates from repos on top of it. even ubuntuzilla doesn't do it, it installs the mozilla version in parallel. 

please try again, see what happens, and post your full session output here, if it still doesn't work.

---

### Post by Robbyx on 2009-01-11
Thank you. I have just retried it and today it installed TB.

R

---

### Post by nanotube on 2009-01-11
excellent news. :)

---

