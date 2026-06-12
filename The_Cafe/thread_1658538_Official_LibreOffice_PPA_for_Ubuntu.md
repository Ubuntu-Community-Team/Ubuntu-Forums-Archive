---
title: "Official LibreOffice PPA for Ubuntu"
date: 2011-01-02
forum: The Cafe
---

### Post by Starks on 2011-01-02
It was worth the wait.

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by areteichi on 2011-01-02
Just to let people know, this PPA replaces OpenOffice. It doesn't allow you to have both installed at once. I did it and LibreOffice seems to be working pretty much the same way as OpenOffice was.

---

### Post by zeroseven0183 on 2011-01-02
And if somehow you don't like the way it looks like, install libreoffice-gtk.

---

### Post by Kalimol on 2011-01-02
I installed it, rolled it back. = P I kind of wish I'd come in to see that there was a fix for it using that ... *hideous* Win95-looking default skin I also get for Wine apps. (What *is* that, anyway?)

It's funny, because I'd installed LibreOffice from debs before the PPA, and it didn't replace OOo, and it included the GTK integration....

---

### Post by cariboo on 2011-01-02
Is it just me, or does LibreOffice load a lot quicker than OpenOffice?

---

### Post by areteichi on 2011-01-02
> **Kalimol said:**
> I installed it, rolled it back. = P I kind of wish I'd come in to see that there was a fix for it using that ... *hideous* Win95-looking default skin I also get for Wine apps. (What *is* that, anyway?)

It's funny, because I'd installed LibreOffice from debs before the PPA, and it didn't replace OOo, and it included the GTK integration....

I don't know what you missed. As zeroseven0183 wrote above, libreoffice-gtk and libreoffice-gnome will set the looks to Gnome just like in OpenOffice. You just need to install them manually.

---

### Post by marl30 on 2011-01-02
> **Kalimol said:**
> I installed it, rolled it back. = P I kind of wish I'd come in to see that there was a fix for it using that ... *hideous* Win95-looking default skin I also get for Wine apps. (What *is* that, anyway?)

It's funny, because I'd installed LibreOffice from debs before the PPA, and it didn't replace OOo, and it included the GTK integration....

Yeah, I noticed that too. Integration with Gnome/KDE didn't install automatically. I had to search for it in Synaptic and install it and it went back to looking like OOO. 

It opened faster than OOO for sure. :)

---

### Post by Spr0k3t on 2011-01-02
I'm happy the PPA is finally available for this.  The speed improvement is definitely noticeable... even on SSD drives.

---

### Post by MonolithImmortal on 2011-01-02
> **cariboo907 said:**
> Is it just me, or does LibreOffice load a lot quicker than OpenOffice?

It's not just you.

---

### Post by NightwishFan on 2011-01-02
I am certainly trying this. :)

---

### Post by Kalimol on 2011-01-03
> I don't know what you missed. As zeroseven0183 wrote above, libreoffice-gtk and libreoffice-gnome will set the looks to Gnome just like in OpenOffice. You just need to install them manually.

Which, as I said, I didn't know. Anyway, I switched it back up again after I found out. My loading splash is uglier and I see it for a shorter period of time now, like the rest of you. = )

---

### Post by MooPi on 2011-01-03
> **cariboo907 said:**
> Is it just me, or does LibreOffice load a lot quicker than OpenOffice?
Lots faster and less overhead as well. I don'
t see my memory usage spike as much. I've install Libre Office on three computers using the .rpm packages and converting them via alien. Has been working swell without adding a new source for apt-get.

---

### Post by areteichi on 2011-01-03
I like the improvements they made on the print menu. 8)
It's a bit laggy but I think the changes are in the right direction.

---

### Post by Toxicbits on 2011-01-04
I have a question of basic understanding regarding the UI. GIMP, based on gtk looks fine under KDE, doesnt it? And even though KDE apps dont look native under Gnome, at least they dont look like Windows, either. So what is LibreOffice using that makes it look so weird without the integration package? Cause even if that is installed, LO still looks a bit off. Why?

---

### Post by earthpigg on 2011-01-04
What predictions do folks have for when LibreOffice will find it's way into Ubuntu's default repos?

---

### Post by sdowney717 on 2011-01-04
add the ppa, then updates will show up

scott@scott-desktop:~$ sudo add-apt-repository ppa:libreoffice/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 36E81C9267FD1383FCC4490983FBA1751378B444
gpg: requesting key 1378B444 from hkp server keyserver.ubuntu.com
gpg: key 1378B444: public key "Launchpad PPA for LibreOffice Packaging" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

run synaptic, do a reload
select libreoffice and the gnome stuff.

---

### Post by bailout on 2011-01-04
Are there any major bugs or disadvantages with this version? I see that on the LibreOffice website they are warning that it isn't a final release and shouldn't be used for production use.

---

### Post by NightwishFan on 2011-01-04
I am sure it has some, however I have used it in the production of Severed Fifth's Fanzine. Worked out fine.

---

### Post by nah40 on 2011-01-04
I installed it, and now have no spell check in Writer or Evolution.

---

### Post by sdowney717 on 2011-01-04
I installed and after reading your comment, just tested writer, and I have spell check working.
If you mean, you type a word and it is misspelled, underlined in red, right click and gives you word options.

---

### Post by nah40 on 2011-01-04
no red underline.
no dictionary, greyed out.

---

### Post by nah40 on 2011-01-04
no red underline.
no words in dictionary, blank.

---

### Post by BigCityCat on 2011-01-04
getting an installation error.

E: /var/cache/apt/archives/libreoffice-common_1%3a3.3.0~rc2-3lucid1_all.deb: trying to overwrite '/etc/bash_completion.d/ooffice.sh', which is also in package openoffice.org-common 1

---

### Post by Ric_NYC on 2011-01-04
It starts in seconds.

---

### Post by KingYaba on 2011-01-05
Mmmm well I downloaded the tar.gz file from their site a few days ago. Like the post above me said: it sure does load faster.

---

### Post by sdowney717 on 2011-01-05
here is a screen shot proving the spell check can work.

did you install from the PPA? Something like this I would uninstall with purge and reinstall.

---

### Post by sdowney717 on 2011-01-05
is spell check option enabled?
it says you can get dictionaries online.

---

### Post by Toxicbits on 2011-01-05
Just add a package like "libreoffice-l10n-de" for a localized UI and spellcheck from the USC.
To get a localized help add "libreoffice-help-de". Just replace de with your language

---

### Post by Quadunit404 on 2011-01-05
I've got a question about this PPA.

Does it include the 64-bit debs for LibreOffice? As much as I'd like a PPA for LibO to keep my current LibO installation up-to-date without me needing to run the ./update script or download about 300 megs of debs, I would like to know if it contains 64-bit binaries for us 64-bit users.

I assume that it does as there are 64-bit debs in the Document Foundation package mirror.

---

### Post by Z-D on 2011-01-05
> **BigCityCat said:**
> getting an installation error.
You haven't completely removed openoffice.org before installing libreoffice, and now you package is corrupted. In order to solve the issue, you have to manually purge the offending package, that is openoffice.org-common. Use the following command:
```
sudo dpkg --purge openoffice.org-common
```dpkg might fail due to dependent packages. If so, remove  dependent packages first. After that you can complete the libreoffice installation, and remove all  openoffice.org leftovers using the command
```
sudo apt-get purge openoffice*
```

---

### Post by Toxicbits on 2011-01-05
A bit off topic: Why dont they add a "purge" button to the USC? I personally dont want all these configfiles flying around.

---

### Post by BigCityCat on 2011-01-05
> **Z-D said:**
> You haven't completely removed openoffice.org before installing libreoffice, and now you package is corrupted. In order to solve the issue, you have to manually purge the offending package, that is openoffice.org-common. Use the following command:
```
sudo dpkg --purge openoffice.org-common
```dpkg might fail due to dependent packages. If so, remove  dependent packages first. After that you can complete the libreoffice installation, and remove all  openoffice.org leftovers using the command
```
sudo apt-get purge openoffice*
```

Thanks ZD!

---

### Post by NCLI on 2011-01-05
> **Toxicbits said:**
> A bit off topic: Why dont they add a "purge" button to the USC? I personally dont want all these configfiles flying around.
Because they don't take up much space, are hidden from ordinary users, and it generally gives a better impression to the user when he reinstalls an application to find that it still works just like before he uninstalled it.

---

### Post by CarpKing on 2011-01-06
> **Quadunit404 said:**
> I've got a question about this PPA.

Does it include the 64-bit debs for LibreOffice? As much as I'd like a PPA for LibO to keep my current LibO installation up-to-date without me needing to run the ./update script or download about 300 megs of debs, I would like to know if it contains 64-bit binaries for us 64-bit users.

I assume that it does as there are 64-bit debs in the Document Foundation package mirror.

I would like to know this as well.

---

### Post by marl30 on 2011-01-06
> **CarpKing said:**
> I would like to know this as well.

Yes. I have it stalled on 64 bit.

---

### Post by CarpKing on 2011-01-07
Any simple way to get separate launchers for the different programs? :/

---

### Post by NCLI on 2011-01-07
> **CarpKing said:**
> Any simple way to get separate launchers for the different programs? :/

The different launchers should all be in /usr/share/applications.

---

### Post by CarpKing on 2011-01-07
Haha!  I thought I'd be clever and tell apt to install libreoffice-gtk so it would drag the rest in as dependencies.  It uninstalled openoffice, but only brought in libreoffice-core!  Installing the rest as we speak.

---

### Post by SoFl W on 2011-01-07
I have always had trouble printing envelopes with OO, I am sure it isn't just an OO issue, probably a printer settings as well, but still it never goes well.  Has anybody noticed improvements with envelope printing in LibreOffice?  Will it print US postal bar codes? I had to download a separate font for the U.S. postal codes.

---

### Post by Quadunit404 on 2011-01-09
Just removed LibreOffice that I installed via packages and reinstalled from the official PPA. Takes *slightly* longer to start up (not that it took that long for me to begin with) but when it loads stuff, it's a whole lot faster. It just feels snappier in general.

---

### Post by gfajdi on 2011-01-10
> **nah40 said:**
> no red underline.
no dictionary, greyed out.

I have the same problem.  No Slovenian spellchecker.

---

### Post by gfajdi on 2011-01-11
> **gfajdi said:**
> I have the same problem.  No Slovenian spellchecker.

When I press F7 I get the "spellchecking complete" message and  when I press OK the windows closes. How can I install Slovenian dictionary?

---

### Post by texla on 2011-01-11
Found this tip to get Spellcheck working:

"sudo apt-get  install libreoffice libreoffice-gtk aspell' to reinstall. Don't forget  aspell or the spell check won't work"

 and also this tip to get it to open lightning fast:" after going to Tools -> Options ->  Java and unchecking the "Use  Java runtime environment" my ooo writing starts in 1.5 seconds"

above tips came from here: 
[http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/](http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/)

I'm so glad to start working with Libreoffice - It looks great with a dark color theme I use right out of the box - open office was horrible for that - hope this keeps getting better.... :P

EDIT:

Spellcheck is now AWOL again - I am researching ways to get it working again... ughh...

---

### Post by areteichi on 2011-01-13
I'm not sure if anyone else experiences this problem but the settings often get reverted back to default after a few days. This is very odd indeed...

Like the arrangement of toolbar buttons, the icon theme, and the general settings get lost after a while and go back to the default preferences. This is pretty irritating. I don't think this is happening because of the document-specific settings, as these are general settings and are independent of the particular file I open.

---

### Post by SoFl W on 2011-01-15
> **cariboo907 said:**
> Is it just me, or does LibreOffice load a lot quicker than OpenOffice?
Yes, I installed this on my old laptop which I use for testing things before I try or use them on my desktop.  I think LO loads faster on my old laptop than OO loads on my newer desktop.

> **sdowney717 said:**
> select libreoffice and the gnome stuff.
I am glad you posted the "gnome stuff" comment, it stuck out when I was looking through all the install choices, I might have missed it if you didn't post that little bit of text.  I am sure it made things easier.

> **nah40 said:**
> I installed it, and now have no spell check in Writer or Evolution.
Spell check worked for me using the above method.  (English-US)

---

