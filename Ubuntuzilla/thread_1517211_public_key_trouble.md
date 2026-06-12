---
title: "public key trouble"
date: 2010-06-24
forum: Ubuntuzilla
---

### Post by the.phantom on 2010-06-24
i did the copy and paste one line installs all way on your post"
USING 10.04 using Ubuntu's firefox and t-bird
AND NOW I GET THIS ERROR

> W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

I READ ALL ON THAT PAGE I SWEAR AND  THIS IS THE ONE LINE I USED
per instructions

> echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null 

what did i do wrong or how do i get around the "no pubkey"

i know that firefox and t-bird have updates but none shown?

just a plain 32 bit system


thanks for the help

---

### Post by stlsaint on 2010-06-24
what are you trying to do...and why are you using /dev/null?

---

### Post by the.phantom on 2010-06-24
just following instructions
 from the site
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
that code should set up  so i can use the ubuntuzilla repros

and would be notified the usual way about updates with "update manager"

on  my old 7.10 system used the old way with deb and python and such but this way they say is faster
so trying to get it to work on my fresh install to stay current on firefox and t-bird.

the new way has been out for a while and wanted to be current on the way i did it and this way seems to be the cleanest way

as ubuntu has not updated firefox or thunderbird to the current version yet



OK i found out it uses the same key as the older way, tried that and still showing no updates for firefox or t-bird?

---

### Post by nanotube on 2010-06-25
apparently you haven't followed the instructions all the way through... the next command to run is (as shown on the site):
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

then, if you keep reading the instructions, you'll see that you should look for packages "firefox-mozilla-build" and "thunderbird-mozilla-build" rather than just plain 'firefox' and 'thunderbird'.

in other words... stopping reading the instructions half-way is not a recommended approach. :) please read until the end of the installation section.

---

### Post by nanotube on 2010-06-25
> **stlsaint said:**
> what are you trying to do...and why are you using /dev/null?

what's wrong with /dev/null? it's a perfectly good data sink...

---

### Post by the.phantom on 2010-06-25
I am very sorry !
 i had a senior moment last night
should have gone to bed before i started this project, won't happen again

read the instructions this morning and firefox and t-bird are updated !
thank you

---

### Post by nanotube on 2010-06-25
> **the.phantom said:**
> I am very sorry !
 i had a senior moment last night
should have gone to bed before i started this project, won't happen again

read the instructions this morning and firefox and t-bird are updated !
thank you

hehe good to hear it all worked out in the end :)

---

### Post by sjhaffner on 2010-09-26
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <*KEY NUMBER>*

---

