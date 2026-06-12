---
title: "[SOLVED] Debian pseudorandom number generator vulnerability fixed in xubuntu 8.04.1?"
date: 2008-07-17
forum: Security
---

### Post by TrombaMarina on 2008-07-17
I want to run a LiveCD of xubuntu to improve my security on untrusted PCs, but I am waiting until I can confirm that the openssl/Debian pseudorandom number generator issue has been patched.  I want secure SSL and I don't want to have to install the patch every time I boot from CD (not even sure if I can).  As far as I can tell, some other openssl vulnerabilities were patched in this release, but not the "big one".  Any information would be appreciated.

If not, when is such a release likely?  Is there an easy way to make my own "patched" bootable CD in the meantime?

---

### Post by kevdog on 2008-07-17
To the best of my knowledge it was patched 3 months ago.  With 8.04.1 release, it has definitely been patched.

---

### Post by TrombaMarina on 2008-07-18
First, thank you for your speedy reply.  It's so nice to have people out there trying to help other people.  It just makes me feel a little better about the human race.

I wasn't ignoring you by waiting so long to respond, just taking the time to do independent verification.  I burned a live CD of 8.04.1 and tried it out and generated a few keys with openssl and checked them with a perl script I found here:
[http://www.debian.org/security/2008/dsa-1571](http://www.debian.org/security/2008/dsa-1571)

Here were the commands I used:
[FONT="Courier New"]openssl genrsa mykey.rsa 1024[/FONT]
[FONT="Courier New"]perl dowkd.pl file ./mykey.rsa[/FONT]

I needed to write to a USB drive in order to execute these commands with a LiveCD.  I needed 30Meg for the Perl script and 30Meg free for the database the script generated in order to work.  At first I didn't have enough free space on the USB drive and the script just sat there with a message like "this could take a while".  After an hour I noticed there was no free space left on the drive, deleted some things, and it finished in about 30 seconds.

I ran these two commands a half-dozen times to make sure I hadn't generated an accidentally strong key (the docs say the database might not be complete).  I used 2048 as a key length for a few of them.  All of them checked out just fine, so you are absolutely correct!

I had thought that since the xubuntu image was called 8.04 for several months that meant it wasn't changing.  Was it?  Do they actually post new versions with the same version number with all the latest patches?  That would be really cool if they kept their ISO images updated, it's just not what I would have expected.  Anyway, the 8.04.1 image definitely seems to have the problem fixed.

-Glen

---

