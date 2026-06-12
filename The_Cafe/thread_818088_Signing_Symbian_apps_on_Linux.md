---
title: "Signing Symbian apps on Linux?"
date: 2008-06-04
forum: The Cafe
---

### Post by infinitejones on 2008-06-04
Does anyone know if there's a Linux equivalent of things like GenialSIS, so I can sign unsigned Symbian apps for my mobile phone?

I tried GenialSIS under Wine but that doesn't seem to get very far...

---

### Post by celticbhoy on 2008-07-27
Did you get a solution InfinateJones ???

---

### Post by infinitejones on 2008-07-27
Nope! Although I think Nokia has bought Symbian and they're going to open the source so hopefully that will make it easier...

---

### Post by SammyBoy247 on 2008-08-06
This is a symbian SDK which also has a signing ap.
Just installing this now so I can't tell you anything more.

[http://www.martin.st/symbian/](http://www.martin.st/symbian/)

---

### Post by Jingo on 2008-10-16
Any news on this topic?

---

### Post by segalion on 2009-03-27
With same signsis.exe windows executable and the wine emulator:

Only execute:

wine signsis.exe input_filename_to_sign.sis output_filename_signed.sis certificate_file.cer certificate_file.key

you can make a bash signsis.sh file and asociate .sis file to be executed from gnome.

---

### Post by ProNux on 2009-06-06
In my case, I used my cellphone directly to sign symbian applications.  I use Freesigner.  Link below.

[http://www.symbian-freeware.com/download-freesigner.html](http://www.symbian-freeware.com/download-freesigner.html)

---

### Post by eigenein on 2010-06-19
There is Ensymble developer utilities for Symbian OS™ at [http://code.google.com/p/ensymble/](http://code.google.com/p/ensymble/) that may help. You can find it in repos: sudo apt-get install ensymble

---

### Post by ryu kun on 2010-09-06
Ensymble 0.28-1ubuntu1 in the repositories of 10.04 is [buggy]("https://bugs.launchpad.net/ubuntu/+source/ensymble/+bug/448665"). Therefore I used v0.29 however I could not sign by signsis command as I don't know passphrase of private key.

I suggest using [SisContent]("http://symbiandev.cdtools.net/siscontents.html") (a free Windows application) through Wine which works flawlessly.

---

