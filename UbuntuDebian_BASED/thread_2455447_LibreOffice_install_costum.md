---
title: "LibreOffice install costum"
date: 2020-12-19
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2020-12-19
Have tried allot already but doesn't seem to do what i want, i'm trying to install the latest libreoffice on the terminal with full dutch support and also dutch spelling check however i first need to fully purge the old installation and i want to install only writer and calc nothing else. I'm on ubuntu > popOs latest.
Could anyone tell me the full way of doing this in the terminal?

---

### Post by Perfect Storm on 2020-12-20
Why not install synaptic to do the job?

---

### Post by Disabled20241022 on 2020-12-20
I like to not install other software to do other stuff, just wanne use the needed only and through the terminal

---

### Post by ajgreeny on 2020-12-20
I suggest you enable the LO-Fresh ppa which will give you version 7.0.4 at the moment.
It does not install any beta versions, only those that are the latest stable version so you should find it works very well.  I've been using it for a few years now with no problems so it's worth a try.

All instructions for enabling and using are at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by Disabled20241022 on 2021-01-24
Currently libroffice 7.0.3.1 in the english language is installed and i am looking for the dutch version UI, i managed to do it after sometime but the entire UI seems like windows 98, so i messed up somewhere.
Anybody out there that knows how to have everything in Dutch (netherlands)?

---

### Post by Hagar Delest on 2021-01-24
Why don't you use the download page from the LibreOffice site? It offers the possibility to get any native language you want (bottom of the green frame).
Use the 6.4.7 for a more stable version.
Better install all packages anyway. You may have to use one or another in the future. There is no point not installing all the suite. It won't spare much room on your HD.

---

### Post by Disabled20241022 on 2021-01-24
I don't like unneeded stuff on my laptop. isn't there a way to do this with the terminal?

---

### Post by Hagar Delest on 2021-01-24
Once you've downloaded and unzipped the tarball, delete the packages you don't want and install with the standard command line (dpkg -i *.deb).

---

### Post by ajgreeny on 2021-01-24
Sure you can use terminal.
Run command ```
sudo apt install libreoffice-writer libreoffice-calc
``` and just those two parts, plus other LO dependencies will be installed.

If you add the fresh PPA as I said in post #4 to get version 7.0.4 you can still do this, but I'm not sure about Dutch language from the PPA..

---

### Post by Disabled20241022 on 2021-01-24
No it is english.

---

### Post by Hagar Delest on 2021-01-24
So, what about trying the debs from the LO pages?

---

### Post by Disabled20241022 on 2021-01-24
Nope, doesn't do it.

---

### Post by Hagar Delest on 2021-01-24
What do you mean?
Have you found the nl package?

---

### Post by ajgreeny on 2021-01-24
Sorry, I assumed you would realise you need the specific language package, eg, ***libreoffice-l10n-nl*** for any particular language you wanted, and I apologise for not reading the full thread, just about you wanting only the two packages, writer and calc.

---

### Post by Disabled20241022 on 2021-02-01
Yes i only want the writer and calc of libroffice installed and it has to be in the dutch/netherlands language with the terminal but how?
I keep messing up my install with what i have tried so far.

---

### Post by Hagar Delest on 2021-02-01
You would install the whole thing, it would be lot more quicker...

---

### Post by CelticWarrior on 2021-02-01
> **Hagar Delest said:**
> You would install the whole thing, it would be lot more quicker...

Indeed.

And then make sure all the languages we need are actually installed. Not so easy in many distro to have multiple locales. dictionaries or whatnot but Ubuntu makes it as easy as it can be via Settings. Just select and apply each and any language you want and everything will be set for Libreoffice and other software.

---

