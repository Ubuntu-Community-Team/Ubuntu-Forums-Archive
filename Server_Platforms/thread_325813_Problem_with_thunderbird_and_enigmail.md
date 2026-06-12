---
title: "Problem with thunderbird and enigmail"
date: 2006-12-26
forum: Server Platforms
---

### Post by Karbonik on 2006-12-26
Suddenly I'm trying to send with the same settings I know worked, and I get this message when trying to decrypt.  I ran this test using 3 different POP3 email address under the same instance of TBird.


gpg command line and output:
/usr/bin/gpg --charset utf8  --batch --no-tty --no-auto-check-trustdb --status-fd 2 --keyserver-options auto-key-retrieve --keyserver ldap://certserver.pgp.com, subkeys.pgp.net, random.sks.keyserver.penguin.de, pgp.mit.edu -d --passphrase-fd 0 --no-use-agent 
usage: gpg [options] [filename]


Seconds previous to this I made sure to upload all my public keys to 
pgp.mit.edu
subkeys.pgp.net
random.sks.keyserver.penguin.de
(For some reason, I have not been able to upload to ldap://certserver.pgp.com)


thunderbird 1.5.0.8 (20061115)
enigmail 0.94.0.0 (20060728) 
Ubunutu Edgy Kernel 2.6.17-10-generic
KDE 3.5.5

I've also tried to install Kgpg to see what;s going on with my GPG, with no luck - I am getting the impression that when the latest update to the 2.6.17-10-generic kernel is buggy - as soon as I installed it I started getting other problems too, such as my time-consumingly configured xorg.conf suddenly only displayed the left 4cm of the main toolbar on my primary screen.

I'm debating whether Edgy is worth it, and switching back to dapper, but I for damn sure don't want to have to use Windows in order to be able to send private email!

---

### Post by Karbonik on 2007-01-01
After talking with Kitche on Freenode #ubuntu (Thanks for your patience) who suggested that the configuration was all wrong (because gpg should have no charset), I:

purged Enigmail support thru both Adept and from the extensions manager in Thunderbird, then tried reinstalling enigmail by manual .xpi install = didn't work

deleted and restored from my backup ~/.mozilla-thunderbird/ = didn't work

purged/reinstalled gpg, and copied my home directory .gpg folder backup. = didn't work

Finally, I deleted ~/.gpg folder, started the program again, and imported my secring.asc and pubring.asc from the backup files = Success!

Hope this will help someone.

---

### Post by redr on 2007-09-14
I tried that deleting ~/.gnupg and importing back the keys.
But no success, still getting same error.
any other idea?
TIA,

---

### Post by pirxx on 2007-09-30
I had the same problem with Evolution. This tip helped me to solve the problem, a very serious problem in a production environment. I deleted .gnupg and brought the keys back from backup. Problem solved. You are a genius! You rock :guitar: 

Thank you very much!

---

