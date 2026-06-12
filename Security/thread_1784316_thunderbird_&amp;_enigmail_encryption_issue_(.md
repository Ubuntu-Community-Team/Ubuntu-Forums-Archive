---
title: "thunderbird &amp; enigmail encryption issue :("
date: 2011-06-16
forum: Security
---

### Post by awesometastic on 2011-06-16
Hello

I configured gpg, gpa, enigmail, and thunderbird to run on my ubuntu 11.04 setup.  I set up a key pair, and everything worked perfectly.  The next day, after typing in the correct private key password, the following error message appeared:

/usr/bin/gpg
gpg: /home/wes/.gnupg/gpg.conf:6: argument not expected
gpg: /home/wes/.gnupg/gpg.conf:7: invalid option

I have tried repeatedly, and the same message pops up.  If I copy the same encrypted text to gpa and use the same password, the text decrypts without a hitch.  

If I type:  gpg    in the terminal, the same message appears:

wes@wes-Gateway:~$ gpg
gpg: /home/wes/.gnupg/gpg.conf:6: argument not expected
gpg: /home/wes/.gnupg/gpg.conf:7: invalid option

How do I fix this? :confused:

(did i post this in the correct  forum?)

---

### Post by awesometastic on 2011-06-16
I went through the enigmail setup wizard in thunderbird, and another error popped up:

Error - encryption command failed
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --with-fingerprint --fixed-list-mode --with-colons --list-secret-keys
gpg: /home/wes/.gnupg/gpg.conf:6: argument not expected
gpg: /home/wes/.gnupg/gpg.conf:7: invalid option


I think that something is wrong with my central installation of gpg

---

### Post by spynappels on 2011-06-17
It looks like there is an error in the GPG configuration file.

If you look at the file it mentions gpg.conf and look specifically at lines 6 and 7, is there a typo or wrong parameter in there?

It is kind of difficult to troubleshoot without seeing the conf file, and you probably do not want to post it here, but if you tell us what those lines are supposed to do, we may be able to give some suggestions.

---

### Post by Sergio.G on 2011-06-18
Check the permission to the .gnupg directory and the files inside, your user should be the owner

Also you might want to try to use Seahorse to generate a new set of key as a test, you'll find it (i think) in: 

Application Menu >> Accessories >> Passwords and Encryption Keys

Seahorse is the default Ubuntu keyring application, once there click new and select PGP Key and click Continue, 
fill in the blanks and select the options that suits you the best and generate, you can omit the upload to server part, 
now you have to import the complete key to enigmail.

If you were able to create the key using Seahorse then continue reading.


Export or Save Private Key:
In Seahorse, to save your complete key, give a right click on the key, then select properties and go to the detail tab, 
click on export complete key, save it with a name you can identify, it is your complete private key and now you can import it to enigmail.
(Remember this is your private key and you should NOT give private keys to anyone)


Export or save Public Key:
Give a right click on the key, select export. Save it with a name you remember to differentiate it from the private key.  


In Thunderbird select OpenPGP, then Key Management and from the menu select File, Import Keys from file, 
and select your private key (this is to save it in enigmail keyring)

If it works then something was or is wrong in the enigmail key generation  

Hope I can be any help.
Cheers!

---

### Post by panda84 on 2011-11-09
[https://bugzilla.redhat.com/show_bug.cgi?id=630249#c8](https://bugzilla.redhat.com/show_bug.cgi?id=630249#c8)
[https://bugs.kde.org/show_bug.cgi?id=226630#c4](https://bugs.kde.org/show_bug.cgi?id=226630#c4)

---

