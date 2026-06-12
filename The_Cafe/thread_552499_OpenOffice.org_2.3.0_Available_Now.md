---
title: "OpenOffice.org 2.3.0 Available Now"
date: 2007-09-16
forum: The Cafe
---

### Post by chrome307 on 2007-09-16
Last night, Sun Microsystems released, very quietly, the next major version their free, open source, multiplatform and multilingual office suite, OpenOffice.org 2.3.0. There is no official announcement and the OpenOffice.org website still shows the 2.2.1 release for download, because version 2.3.0 was supposed to arrive on Monday, September 17. Still, the final builds can be found on FTP mirrors around the globe. 

This new version comes with a lot of bugfixes, improvements and new features for all OpenOffice.org components.

Among the features found in OpenOffice.org 2.3.0, we can confirm the presence of a new charting wizard and a new filter, part of OpenOffice.org Write component that will help you easily create Wiki pages. The components included in this release are:

**Writer** - a word processor you can use for anything from writing a quick letter to producing an entire book.
**Calc** - a powerful spreadsheet with all the tools you need to calculate, analyze, and present your data in numerical reports or sizzling graphics.
**Impress** - the fastest, most powerful way to create effective multimedia presentations.
**Draw** - lets you produce everything from simple diagrams to dynamic 3D illustrations.
**Base** - lets you manipulate databases seamlessly. Create and modify tables, forms, queries, and reports, all from within OpenOffice.org.
**Math** - lets you create mathematical equations with a graphic user interface or by directly typing your formulas into the equation editor.

OpenOffice.org is the easiest to use office suite, with a familiar look and feel. It's instantly usable by anyone who has worked with a competitive product. 

Moreover, OpenOffice.org reads all major competitors' files.
[B]
The next version, 2.3.1, of OpenOffice.org, is scheduled for release on December 4.

Until then, go and grab a copy of OpenOffice.org 2.3.0 for your Linux operating system from Softpedia.[/B]

```


http://linux.softpedia.com/get/Office/Office-Suites/OpenOffice-dot-org-253.shtml


```

---

### Post by Kingsley on 2007-09-16
Be prepared to be bombarded with questions on how to install this version.

---

### Post by matthewdhandley on 2007-09-16
I'll start ... Hey, how do you install this?

---

### Post by FuturePilot on 2007-09-16
I'll wait for Gutsy

---

### Post by Kingsley on 2007-09-16
Yeah, waiting for Gutsy is good because there are no cool changes in this version.

For those that want to install anyway:

```

tar xzvf OOo_2.3.0_LinuxIntel_install_en-US.tar.gz
cd OOG680_m5_native_packed-1_en-US.9221/
cd RPMS/
sudo apt-get install alien
sudo apt-get remove openoffice*
sudo alien --scripts --keep-version *.rpm
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

I know, it's a lot of commands :D.

---

### Post by Fbot1 on 2007-09-16
just looks like a release candidate to me:
[http://download.openoffice.org/680/index.html?intcmp=1235](http://download.openoffice.org/680/index.html?intcmp=1235)

---

### Post by stmiller on 2007-09-16
It's a stable final release. Just hasn't gotten around to update some info pages, and some mirrors.

[http://openofficeorg.secsup.org/stable/2.3.0/](http://openofficeorg.secsup.org/stable/2.3.0/)

---

### Post by Fbot1 on 2007-09-16
> **stmiller said:**
> It's a stable final release. Just hasn't gotten around to update some info pages, and some mirrors.

[http://openofficeorg.secsup.org/stable/2.3.0/](http://openofficeorg.secsup.org/stable/2.3.0/)

Hmm, that's weird.

---

### Post by mr.lee on 2007-09-17
How can this overcome mee...as new ubuntu user... I dunno if my complain is at the right topics or not, sorry if off topic.

Some bug happen at OO 2.2.0, and i dislike it, here it is:
1. In Spreadsheet, if I select the whole single Line (ex: from A1..A31002302 or whatever)...then while holding Shift Key, i press arrow down... the selection change to the only column A. I want to select the whole A1 to C342422 or else, but it can't. The solution is sucks...use my mouse from left to nowhere at the right of my table. Any better solution?

2. Still in spreadsheet, if i want to multiple selection the cells...it can't be copy/cut. So, if i want to pick some from my list to be copied on the next column...i have to pick it one by one, coz it's seperated (and not the way to be sorted).

3. Some formula (ex: Sum) it not calculate correctly. This one can kill me in front of my boss. Please, some mistakes from Sun's programmer can lead me to early retirement. 

4. If I select something at the first sheet, then I take a peek look to the other sheet at the same document, the selecttion is gone while i back to the first sheet.

If these annoying bug is can be corrected at 2.3.0...(especially number 3), the I'll kill my MS for good.
Sorry bout the English, i'm Indonesian.

Thx a lot.

---

### Post by slimdog360 on 2007-09-17
you're a bit late. It got it last week when it was released. Something on softpedia about it.

---

### Post by LookTJ on 2007-09-17
> **mr.lee said:**
> How can this overcome mee...as new ubuntu user... I dunno if my complain is at the right topics or not, sorry if off topic.

Some bug happen at OO 2.2.0, and i dislike it, here it is:
1. In Spreadsheet, if I select the whole single Line (ex: from A1..A31002302 or whatever)...then while holding Shift Key, i press arrow down... the selection change to the only column A. I want to select the whole A1 to C342422 or else, but it can't. The solution is sucks...use my mouse from left to nowhere at the right of my table. Any better solution?this is fixed in 2.3

> 2. Still in spreadsheet, if i want to multiple selection the cells...it can't be copy/cut. So, if i want to pick some from my list to be copied on the next column...i have to pick it one by one, coz it's seperated (and not the way to be sorted). don't understand this one. If I did understand it right, It would be No

> 3. Some formula (ex: Sum) it not calculate correctly. This one can kill me in front of my boss. Please, some mistakes from Sun's programmer can lead me to early retirement. fixed in 2.3

> 4. If I select something at the first sheet, then I take a peek look to the other sheet at the same document, the selecttion is gone while i back to the first sheet.fixed in 2.3

  

Yes I have the OO.o 2.3.0 stable release

---

### Post by mr.lee on 2007-09-17
> **Taylor said:**
> 
 don't understand this one. If I did understand it right, It would be No



Here i give some example:
A                     B
Andy
Boney
Charlie
Dorry
Edward

Then i want to select Andy and Boney and Edward, then copy it to column B,like this:
A                    B
Andy             Andy
Boney          Boney
Charlie
Dorry
Edward         Edward


It' can't be done in 2.2.0. Hopefully it's fixed in 2.3.0, since i didn't have extra time to follow up the What's new section from 2.3.0. Ok I'll download it. Thx God, and the Sun. :)

---

### Post by herbster on 2007-09-17
> **Kingsley said:**
> Yeah, waiting for Gutsy is good because there are no cool changes in this version.

For those that want to install anyway:

```

sudo apt-get remove openoffice*
```


When I do that, or even use openoffice.org*, I keep getting this:

```
bobby:~/Desktop/OOG680_m5_native_packed-1_en-US.9221/RPMS$ sudo apt-get remove openoffice.org*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org-base-2.3.0-9221.i586.rpm
```

But the file is right there. :confused:

---

### Post by Kingsley on 2007-09-17
> **herbster said:**
> When I do that, or even use openoffice.org*, I keep getting this:

```
bobby:~/Desktop/OOG680_m5_native_packed-1_en-US.9221/RPMS$ sudo apt-get remove openoffice.org*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org-base-2.3.0-9221.i586.rpm
```But the file is right there. :confused:
Open up another terminal and try the apt-get remove command again.

---

### Post by herbster on 2007-09-17
> **Kingsley said:**
> Open up another terminal and try the apt-get remove command again.

Oh poop, I just did "cd\" and it works... how did I miss that :D Thanks friend!

---

### Post by herbster on 2007-09-17
Okay, I installed it as per your instructions Kingsley, but I'm clicking on the gnome-panel menu shortcuts, nothing is happening. I hit ALT+F2, type openoff and it completes to "openoffice.org2.3" and I hit enter, nothing. I did it from terminal;

```
bobby:~/Desktop/OOG680_m5_native_packed-1_en-US.9221/RPMS/desktop-integration$ openoffice.org2.3
/etc/openoffice.org2.3/program/soffice.bin: error while loading shared libraries: libvcl680li.so: cannot open shared object file: No such file or directory
```

---

### Post by mr.lee on 2007-09-18
> **Taylor said:**
> this is fixed in 2.3

 don't understand this one. If I did understand it right, It would be No

 fixed in 2.3

fixed in 2.3

  

Yes I have the OO.o 2.3.0 stable release



Hey hey Taylor. Did u guarantee your word above? I've download it, I've install it (thanks to Kingsley and a clue from Herbster). But the whole thing did i complaining about is still the same.
 Oh man, did somebody could tell me the right place to complaining about? :(
Or, did somebody got a clue to fix it up, or set it up on the option or kind?

Thx a lot..
*Taking fire...need assistance! *

---

### Post by hyperair on 2007-09-18
To anyone having problems after the installation...

```

sudo ln -s /opt/openoffice.org-2.3/programs/soffice /usr/local/bin

```

That'll allow you to use soffice to open files.

---

### Post by LookTJ on 2007-09-20
> **mr.lee said:**
> Hey hey Taylor. Did u guarantee your word above? INo I didn't.

---

### Post by damonw5 on 2007-09-23
Seems like a .deb is out on the main oo.org site. Think it works on Ubuntu?
[URL="http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0"]
http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org(...)[/URL]

---

### Post by bruce89 on 2007-09-23
Gutsy has this by the way, there's probably nothing very interesting about it anyway.

---

### Post by Kimm on 2007-09-23
For a painless way to install this release, use RPM.

First, remove ubuntus build of OpenOffice using Synaptic (or your tool of preference).

Then download the RPM packages for OpenOffice and install:

```

cd <directory containing packages>
rpm --nodeps -i *rpm

```

Then find the debian-menus .deb and install it using dpkg.

The PRM-packages will install to /opt so your normal files wount be touched (so its no more dangerous than to first convert using alien, just more hassle-free)

---

### Post by reyfer on 2007-09-23
> **Kimm said:**
> For a painless way to install this release, use RPM.

First, remove ubuntus build of OpenOffice using Synaptic (or your tool of preference).

Then download the RPM packages for OpenOffice and install:

```

cd <directory containing packages>
rpm --nodeps -i *rpm

```

Then find the debian-menus .deb and install it using dpkg.

The PRM-packages will install to /opt so your normal files wount be touched (so its no more dangerous than to first convert using alien, just more hassle-free)I don't get it. Why do all that, when there's a .deb on OOo's site?

---

### Post by Hagar Delest on 2007-09-23
> **reyfer said:**
> I don't get it. Why do all that, when there's a .deb on OOo's site?
You're right, it's a new feature from this 2.3 release : also available in .debs.

---

### Post by the_darkside_986 on 2007-09-23
Can this one read MS Office 2007 files? It would be helpful to at least be able to read them as read-only. 

If not, I know how to unzip a office 2k7 file and read the XML files inside the unzipped archive. (Yes, the *.*x files are indeed zip folders.)

---

### Post by felipecerda on 2007-09-23
> **the_darkside_986 said:**
> Can this one read MS Office 2007 files? It would be helpful to at least be able to read them as read-only. 

If not, I know how to unzip a office 2k7 file and read the XML files inside the unzipped archive. (Yes, the *.*x files are indeed zip folders.)

I hope OO 2.3 reads y writes Office 2007 files... can anyone confirm this?

---

### Post by LookTJ on 2007-09-23
> **felipecerda said:**
> I hope OO 2.3 reads y writes Office 2007 files... can anyone confirm this?
I don't think it does. since I don't see a save option for docx.

---

### Post by Frak on 2007-09-23
> **damonw5 said:**
> Seems like a .deb is out on the main oo.org site. Think it works on Ubuntu?
[URL="http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0"]
http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org(...)[/URL]
If it doesn't, it can easily be converted into an Ubuntu Binary.

---

### Post by Frak on 2007-09-23
> **Taylor said:**
> I don't think it does. since I don't see a save option for docx.
I don't think it will. MS bragged about the open standard, but a 6000 page report that was badly made, and relies on non-open standards guarantees us that it will have to be reverse-engineered... again...

Plus, I don't think .docx even is the open standard they were talking about. MS for ya'

---

### Post by Depressed Man on 2007-09-24
> **reyfer said:**
> I don't get it. Why do all that, when there's a .deb on OOo's site?

Hmm, do I install all these debs? And if so is there a faster way? And what about the previous OpenOffice? Usually for Pidgin I have to remove the old packages before installing the new.

---

### Post by hyperair on 2007-09-25
There is a faster way.. upgrade to Gutsy xD But I really don't suggest it.

---

### Post by jnyabicha on 2007-10-13
Dear Ubuntu people,

I managed to install and have OpenOffice.org up and running on Edubuntu by following the following simple steps.

1 Install fakeroot, alien and rpm packages;

*sudo apt-get install fakeroot alien rpm*

2. Download OpenOffice.org 2.3 for Linux .

[I]I got it from [http://ftp-atl.osuosl.org/pub/openoffice/stable/2.3.0/](http://ftp-atl.osuosl.org/pub/openoffice/stable/2.3.0/)

I choose OOo_2.3.0_LinuxIntel_install_en-US.tar.gz package. 

If your Ubuntu Linux system have not Java Runtime Environment, you will need to get OOo_2.3.0_LinuxIntel_install_wJRE_en-US.tar.gz package. This is available in the same location
[/I]

3. Extract tarball file:

[I]tar zxvf OOo_2.3.0_LinuxIntel_install_en-US.tar.gz
[/I]

4. Now go to RPMS folder:

[I]cd OOG680_m5_native_packed-1_en-US.9221/RPMS/
[/I]

5. Convert rpm packages to deb packages:

[I]fakeroot alien -k --scripts *.rpm
[/I]

6. # Install converted deb packages.

[I]For GNOME users:

mv openoffice.org-kde-integration_2.3.0-9221_i386.deb ../
sudo dpkg -i *.deb

For KDE users:

mv openoffice.org-gnome-integration_2.3.0-9221_i386.deb ../
sudo dpkg -i *.deb
[/I]

The OpenOffice.org 2.3 will be installed to /opt/openoffice.org2.3/ folder.

To start OpenOffice.org 2.3, you can use the following command:

/opt/openoffice.org2.3/program/soffice

Any issues with the installation am ready to assist

---

### Post by hyperair on 2007-10-13
Actually there are DEBs wihch you can get from the openoffice web site you know, instead of using the RPMs. And also, you can just wait for Gutsy to come out, then upgrade, and there you have it =P

---

### Post by Frak on 2007-10-13
> **hyperair said:**
> Actually there are DEBs wihch you can get from the openoffice web site you know, instead of using the RPMs. And also, you can just wait for Gutsy to come out, then upgrade, and there you have it =P
Yep, Gutsy has it installed by default.

---

