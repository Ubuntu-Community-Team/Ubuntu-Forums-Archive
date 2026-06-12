---
title: "gdebi and not software center."
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-20
Seeing the Software Center is being worked on, and I use the apt-get install to install most software, but I want to make the default program to start when installing a .deb file gdebi-gtk and not the Sofware Center, where do I make this change?

---

### Post by zika on 2011-12-20
> **irv said:**
> Seeing the Software Center is being worked on, and I use the apt-get install to install most software, but I want to make the default program to start when installing a .deb file gdebi-gtk and not the Sofware Center, where do I make this change?Find some .deb file. Open Nautilus in that folder or navigate there. Right click on that .deb and (in Properties, as far as I remember) choose gdebi-gtk as default...

---

### Post by irv on 2011-12-20
> **zika said:**
> Find some .deb file. Open Nautilus in that folder or navigate there. Right click on that .deb and (in Properties, as far as I remember) choose gdebi-gtk as default...

Thanks,
For the life of me I couldn't remember how to do this.
OK, now I have it set, but when I go to install a deb from the online Software Center [https://apps.ubuntu.com/cat/]("https://apps.ubuntu.com/cat/") and chose to install with gdebi-gtk it starts the apt gdebi-gtk but is blank. It looks like it is not working for installing from this website. It looks like I have to use the Software Center, but it is not working in 12.04 yet. I know I can install via the package manager, but I was trying to get this to work.
[ATTACH]209426[/ATTACH]   [ATTACH]209427[/ATTACH]

---

### Post by zika on 2011-12-20
> **irv said:**
> Thanks,
For the life of me I couldn't remember how to do this.
OK, now I have it set, but when I go to install a deb from the online Software Center [https://apps.ubuntu.com/cat/]("https://apps.ubuntu.com/cat/") and chose to install with gdebi-gtk it starts the apt gdebi-gtk but is blank. It looks like it is not working for installing from this website. It looks like I have to use the Software Center, but it is not working in 12.04 yet. I know I can install via the package manager, but I was trying to get this to work.
[ATTACH]209426[/ATTACH]   [ATTACH]209427[/ATTACH]Did You try with a .deb that You have locally...?
It seems to me that there is some step missed in this endeavor of Yours...
(browser-wise...)

---

### Post by irv on 2011-12-20
> **zika said:**
> Did You try with a .deb that You have locally...?
It seems to me that there is some step missed in this endeavor of Yours...
(browser-wise...)

Yes it works with a local deb file.
The steps to the online software center are simple.
1. go online [https://apps.ubuntu.com/cat/]("https://apps.ubuntu.com/cat/")
2. find the software you want to install.
3. install it.

When you selection the package, it ask for the application to use to install it. "software center", "gdebi-gtk". It should open with the package you have selected, but it doesn't.

---

### Post by mc4man on 2011-12-20
If you want to use gdebi then download the .deb, if you want to use that site then get S-C to behavior a little better. 
(if you ask it nicely S-C will work once per session

man gdebi
> DESCRIPTION
       gdebi  lets  you  _install local deb packages_ resolving and installing its dependencies. apt does the same, but
       only for remote (http, ftp) located packages.


---

### Post by kuvanito on 2011-12-20
i just did that,since the sofware center is acting up

sudo apt-get install gdebi

i now download the apps i need,right click on them and Open with GDebi Package Installer

---

### Post by jbicha on 2011-12-20
Just to repeat and clarify:

Software Center can install local downloaded .debs and remote from the repositories. gdebi only installs the downloaded .debs. The links at apps.ubuntu.com are actually just commands to pull from the repositories so gdebi won't work for those.

---

### Post by wolfen69 on 2011-12-20
```
sudo dpkg -i ubuntu.deb
```
is always reliable too. ;)

---

### Post by irv on 2011-12-21
> **jbicha said:**
> Just to repeat and clarify:

Software Center can install local downloaded .debs and remote from the repositories. gdebi only installs the downloaded .debs. The links at apps.ubuntu.com are actually just commands to pull from the repositories so gdebi won't work for those.

It's clear to me now. Thanks.

---

### Post by zika on 2011-12-21
> **jbicha said:**
> Just to repeat and clarify:

Software Center can install local downloaded .debs and remote from the repositories. gdebi only installs the downloaded .debs. The links at apps.ubuntu.com are actually just commands to pull from the repositories so gdebi won't work for those.That's why it works nice in Chrom{e,ium}... ;)

---

