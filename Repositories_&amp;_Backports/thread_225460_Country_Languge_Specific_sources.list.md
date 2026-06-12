---
title: "Country /Languge Specific sources.list"
date: 2006-07-29
forum: Repositories &amp; Backports
---

### Post by itKiwi on 2006-07-29
[FONT="Verdana"]I am working through the server installation described in [/FONT]
[FONT="Courier New"]http://www.howtoforge.com/perfect_setup_ubuntu_6.06[/FONT] 

[FONT="Verdana"]It's going slowly.  One thing I would like to understand is how the sources.list file is generated.  I have seen country (or language ?) specific versions with  “de” and “us”, and my own one is “it”.  How is this version “decided” ?  Is it because I am located in Italy, or because I downloaded the iso from an Italian mirror ?  Why are there these different versions ?  What difference does it make to the actual software loaded onto the computer ?  I don't want Italian software; I want English (or USA) !

If one of the packages “couldn't be found”, am I likely to find it in another language /country repository ?

Thanks for any help in understanding this better.[/FONT]

---

### Post by Jagot on 2006-07-29
All the ubuntu iso's are identical regardless of where you download them from.  I'm not 100% sure but I would assume it is set when you set your location for the time zone during set up or perhaps the language choice that the local repositories are established in your sources.list.

There is no difference to the software installed - the packages you downlaod however will come from a mirror server more local to you and thus you should get the packages faster than if you were installing from sources in the USA for example.

If a package is unavailable in the repository it is generally just because the server may be down for maintenance or there is some kind of a fault with it - this happens wherever you are.  You could try another local mirror if you like but it's probably just easier to wait a couple of hours until the repository is back online.

If you're really bothered about it you can alter your sources.list with non-region specific repositories:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by croak77 on 2006-07-29
During the installation you select your language and location. If you select English and USA you will can engish locales and USA mirror. Select the language you want and the closet mirror.

---

### Post by itKiwi on 2006-07-30
Thanks guys. This has helped a lot, specially the link to psychocats.

Ciao.

---

