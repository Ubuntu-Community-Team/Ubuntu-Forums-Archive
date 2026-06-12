---
title: "How To: Install LibreOffice"
date: 2010-09-29
forum: Tutorials
---

### Post by scouser73 on 2010-09-29
As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**[COLOR="Red"]**[/COLOR]** You can have LibreOffice sit along side OpenOffice, but if you want to remove OpenOffice entirely then enter the following command into Terminal **[COLOR="Red"]**[/COLOR]**

**> sudo apt-get remove openoffice*.***

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: **> sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb**

**5** - Then enter the following command into Terminal: **> sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.5-debian-menus_3.5.4-2_all.deb**

You have now successfully installed LibreOffice.

---

### Post by jillyronald on 2010-09-30
Ligre office is good to use and better than other office packages. Here very easy and step by step information with useful details. I hope every one gives positive replay.

---

### Post by Gordonbp531 on 2010-09-30
> **scouser73 said:**
> As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**[COLOR="Red"]**[/COLOR]** You can have LibreOffice sit along side OpenOffice, but if you want to remove OpenOffice entirely then enter the following command into Terminal **[COLOR="Red"]**[/COLOR]**

****

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: ****

**5** - Then enter the following command into Terminal: ****

You have now successfully installed LibreOffice.


Did all that - keeping Open Office but NO SIGN of Libreoffice anywhere in menus or anything.
What now?

---

### Post by Gordonbp531 on 2010-09-30
Cancel that - got the wrong version!"

---

### Post by fsando on 2010-09-30
[s]Can I have libreoffice and openoffice alongside each other? Or does libre office replace openoffice?[/s]

Reread the OP.

---

### Post by Mina Fouad on 2010-10-01
some thing wrong in your article.. 
the extracted file doesn't have DEPS but RPMS and all packages with extension .RPM 
is there any solution to make it work on my darling Ubuntu 
if the only solution is to convert them to .deb is there ant quick way to convert all of those packages.

---

### Post by Malta paul on 2010-10-01
Just download the .deb file either 32bit or 64bit from:
[http://download.documentfoundation.org/libreoffice/testing/](http://download.documentfoundation.org/libreoffice/testing/)
Then follow the instructions in first post.:)

---

### Post by Mina Fouad on 2010-10-01
> **Malta paul said:**
> Just download the .deb file either 32bit or 64bit from:
[http://download.documentfoundation.org/libreoffice/testing/](http://download.documentfoundation.org/libreoffice/testing/)
Then follow the instructions in first post.:)

[COLOR="DarkOrange"][COLOR="rgb(255, 140, 0)"][COLOR="Blue"][FONT="Comic Sans MS"]thanks a lot but now I have to download 143 MB again :([/FONT][/COLOR][/COLOR][/COLOR]

---

### Post by opodaniel on 2010-10-02
Does anyone know how to configure LibreOffice? I just need Calc and Write and don't need other packages.

---

### Post by fsando on 2010-10-02
> **opodaniel said:**
> Does anyone know how to configure LibreOffice? I just need Calc and Write and don't need other packages.

I think the best way is to first do a full install, trying to pick and choose from the debs will likely prove quite difficult. 

After installation they show up in synaptic, you can then deselect what you don't want. You won't save much, though, in terms of space and number of packages as the individual parts are closely integrated.

---

### Post by wdog on 2010-10-04
64bit
[http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz)
32bit
[http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86_install-deb_en-US.tar.gz)

---

### Post by zeroseven0183 on 2010-10-05
Tried installing it using the .deb file and also from the repositories but did not find any thing in my menu

---

### Post by Mi*6d@# on 2010-10-05
> **zeroseven0183 said:**
> Tried installing it using the .deb file and also from the repositories but did not find any thing in my menu
Install .deb file in the 'desktop-integration' folder

---

### Post by berman56 on 2010-10-11
Thank you scouser73.  Your instructions helped this novice user get libreoffice.

---

### Post by fsando on 2010-10-12
I'm on Ubuntu 10.04

In the formula editor I'm having the following problem:
Special characters and diacritical markers (like in bar,hat etc.) do not show. Instead there is a square i.e. the LibreOffice cannot find the relevant fonts.

I can, however, edit each single special character and change it to the correct font and character. The changes are apparently saved in the file  (I have found no way to make the diacritical markers reappear)

~/.libreofficeX/3/user/registrymodifications.xcu

A formula created in openoffice 3.2 will look correct until I open it where characters are then changed into squares.

A formula created in LibreOffice looks wrong until I open it where the squares are then changed into the correct characters

---

### Post by JoseArmandoJeronymo on 2010-10-12
Earlier this afternoon I installed LibreOffice following the instructions on this thread and tried it on a client analysis I am working in. Libre is very nice and I all but forgot I wasn't using OpenOffice!

P.S. Install was a breeze and did not conflict with OO.

---

### Post by DrAcid on 2010-10-13
Downloading 3.3beta2 as I post... thanx for the tip!
I was wondering how to get rid of oOO and install LibreOffice...

Does it integrate with menu? Will report after install. :)

* * * 

Downloaded - OK...
Installed - OK...
Menu Integrated - OK...
Conflicts with oOO - N/A...

Installs full pack into Office menu. Calc, Writer, Draw, Base, Math, Impress, PrinterAdmin...

if something happens, will report ;)

---

### Post by Hoopz on 2010-10-13
Thanks for putting this up.  I am liking libreoffice

---

### Post by roger_1960 on 2010-10-15
Hi

Note that in step 5 of post#1 the file name at the end of the command is now changed when using the latest deb download

> sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.3-debian-menus_3.3-1_all.deb

Works great!

---

### Post by DrAcid on 2010-10-21
Too bad, I got a bug. :( LibreOffice 3.3

When editing a formula, You sometimes need to enter a vector variable. You know, the variables with horizontal arrows on top of them?
Well, no matter how I try changing fonts for the formulas, the arrows won't show. An empty grey box instead... sits there staring at me...

the bug is easily reproduced. Just start LibreOffice Math, or insert a formula into Writer Document. then type "vec A".
It should render A with an arrow on top of it.... if it doesn't - U have the same bug.

I'm not very experienced in bug-reporting... Could someone explain how do I file a bug to TDF?
Or file the bug for me?

---

### Post by browsons on 2010-10-22
Gracias

---

### Post by lbradley on 2010-10-22
[QUOTE=scouser73;9906361]As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**[COLOR="Red"]**[/COLOR]** You can have LibreOffice sit along side OpenOffice, but if you want to remove OpenOffice entirely then enter the following command into Terminal **[COLOR="Red"]**[/COLOR]**

****

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: ****

**5** - Then enter the following command into Terminal: ****

---

### Post by lbradley on 2010-10-22
> **scouser73 said:**
> As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**[COLOR="Red"]**[/COLOR]** You can have LibreOffice sit along side OpenOffice, but if you want to remove OpenOffice entirely then enter the following command into Terminal **[COLOR="Red"]**[/COLOR]**

****

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: ****

**5** - Then enter the following command into Terminal: ****

You have now successfully installed LibreOffice.

(Mod Note: Fixed Quotes.)

---

### Post by lbradley on 2010-10-22
Command is outdated. Should be:

sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.3-debian-menus_3.3-1_all.deb

---

### Post by ashwinrao on 2010-10-23
Thanks for the guide! Now, I have Liberated Office :guitar:

---

### Post by fsando on 2010-10-23
> **DrAcid said:**
> Too bad, I got a bug. :( LibreOffice 3.3

When editing a formula, You sometimes need to enter a vector variable. You know, the variables with horizontal arrows on top of them?
Well, no matter how I try changing fonts for the formulas, the arrows won't show. An empty grey box instead... sits there staring at me...

the bug is easily reproduced. Just start LibreOffice Math, or insert a formula into Writer Document. then type "vec A".
It should render A with an arrow on top of it.... if it doesn't - U have the same bug.

I'm not very experienced in bug-reporting... Could someone explain how do I file a bug to TDF?
Or file the bug for me?

I reported it [already]("https://bugs.freedesktop.org/show_bug.cgi?id=30729"), it has high priority so expect it to be solved in the next release. This bug is widespread but I believe not on all platforms so it's likely not a major problem to solve.

To report bugs in LibreOffice:
[https://bugs.freedesktop.org/](https://bugs.freedesktop.org/)

---

### Post by Ancanus on 2010-10-24
> **fsando said:**
> I reported it [already]("https://bugs.freedesktop.org/show_bug.cgi?id=30729"), it has high priority so expect it to be solved in the next release.

Tough, the bug is still marked as NEEDINFO.

---

### Post by fsando on 2010-10-25
> **Ancanus said:**
> Tough, the bug is still marked as NEEDINFO.

Yes, it could mean that no one is working on it and so hasn't figured out exactly what information is needed or that they are testing for various possibilities and don't need outside input. They did ask for a screenshot which I provided and they haven't asked for anything since, as you can see, so I guess things are moving in the right direction.

---

### Post by Ancanus on 2010-10-29
> **fsando said:**
> Yes, it could mean that no one is working on it and so hasn't figured out exactly what information is needed or that they are testing for various possibilities and don't need outside input. They did ask for a screenshot which I provided and they haven't asked for anything since, as you can see, so I guess things are moving in the right direction.

You probably already figured this out, but for anyone else having issues with the symbols being displayed as squares, given that they installed LibreOffice over OpenOffice, this fixed it for me:


```
sudo cp /opt/libreoffice3/basis3.3/share/fonts/truetype/opens___.ttf /usr/share/fonts/truetype/openoffice/
```

---

### Post by fsando on 2010-10-30
> **Ancanus said:**
> You probably already figured this out, but for anyone else having issues with the symbols being displayed as squares, given that they installed LibreOffice over OpenOffice, this fixed it for me:


```
sudo cp /opt/libreoffice3/basis3.3/share/fonts/truetype/opens___.ttf /usr/share/fonts/truetype/openoffice/
```

If you have the old font in ~/.fonts this will as far as I can tell still be used in preference of the system wide one. So you most likely want to remove/replace it if it exists.

---

### Post by maria-n on 2010-11-05
Thanks! It worked flawless and fast!

For the download I used the above mentioned link: [http://download.documentfoundation.o...ffice/testing/](http://download.documentfoundation.o...ffice/testing/)
though I noticed you have to be a bit careful in selecting the proper file

---

### Post by hansheijmans on 2010-11-14
Does anyone know if LibreOffice 3.3 will replace OO 3.2 through Update Manager or apt-get automatically once it will be available in the repositories?

---

### Post by Stoneface on 2010-11-15
> **hansheijmans said:**
> Does anyone know if LibreOffice 3.3 will replace OO 3.2 through Update Manager or apt-get automatically once it will be available in the repositories?
I don't know. But I believe LibreOffice will be part of the next Ubuntu release and that people with current releases will just have to uninstall Open Office and install LibreOffice as soon as it becomes available.

---

### Post by fsando on 2010-11-15
> **Stoneface said:**
> I don't know. But I believe LibreOffice will be part of the next Ubuntu release and that people with current releases will just have to uninstall Open Office and install LibreOffice as soon as it becomes available.



Seems Mark Shuttleworth believes so too

[http://www.techdrivein.com/2010/09/future-ubuntu-releases-will-be-shipped.html](http://www.techdrivein.com/2010/09/future-ubuntu-releases-will-be-shipped.html)

Regarding uninstalling LO or Ooo, I have had some issues with LO beta crashing or not being able to open certain files so Im going to keep Ooo around for some time. Another issue has been fonts in LO's formula editor, the solution is simple and is to make sure that all old versions of opensymbol.ttf are replaced with the one that comes with LO, then logout - login.

---

### Post by BeachBuddah on 2010-11-27
Hi

I'm trying to install LibreOffice but I'm running into a problem.  When I type in Step 4 in Post 1 I get the following:

No packages found matching libobasis3.3-base_3.3.0-12_i386.deb.

I get that response for each of the 51 packages in the DEBS folder - which exists and HAS libobasis3.3-base_3,3,0-12_i386.deb. (As well as all the other packages.)

Huh?
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Any suggestions will be greatly appreciated...TIA

---

### Post by another_sam on 2010-11-27
Thank you.

---

### Post by maghoxfr on 2010-11-27
@BeachBuddahI followed the guide blindily but I realized that it was obvious that I should change some things (I use Ubuntu in spanish) and the name of the file in step 4 was different from the one I downloaded, but changing those little things made it for me. 

Great guide. Thanks

---

### Post by another_sam on 2011-01-06
useful!

please update last command to 3.3.0rc2. now is:
libreoffice3.3-debian-menus_3.3-4_all.deb

---

### Post by maghoxfr on 2011-01-06
There's actually a [libreoffice PPA]("https://launchpad.net/~libreoffice/+archive/ppa") now, I purged openoffice out of my system before installing libreoffice.

---

### Post by another_sam on 2011-01-06
ok I just wrote what maghoxfr wrote XD

---

### Post by zhanglini on 2011-01-12
A quick question ---- I am using OO right now, and if I delete OO and replace it with Lib O, would Lib O be able to inherit all the settings I have for OO?

---

### Post by maghoxfr on 2011-01-12
> **zhanglini said:**
> A quick question ---- I am using OO right now, and if I delete OO and replace it with Lib O, would Lib O be able to inherit all the settings I have for OO?

I don't think so, but I'm just thinking out loud. I installed it from the PPA and purged out open office so I wouldn't know.

---

### Post by zhanglini on 2011-01-12
> **maghoxfr said:**
> I don't think so, but I'm just thinking out loud. I installed it from the PPA and purged out open office so I wouldn't know.

Thanks, I'd hold off on installing LibO then.

---

### Post by maghoxfr on 2011-01-12
> **zhanglini said:**
> Thanks, I'd hold off on installing LibO then.

Don't take my word as an axiom though, do some more research! So far libreoffice is running great on my pc.

---

### Post by Noemie on 2011-01-13
Thank you for the easy-to-follow instructions! I managed to install Libreoffice!

---

### Post by gatorbrit on 2011-01-21
I've been using LO but when I read a word doc with the font "Times New Roman Bold" LO substitutes arial font instead.

I know that I have times new roman bold on my computer it is here.

```
/usr/share/fonts/truetype/msttcorefonts
```

How do I make LO "see" this font?

Thanks!

---

### Post by fsando on 2011-01-22
> **gatorbrit said:**
> I've been using LO but when I read a word doc with the font "Times New Roman Bold" LO substitutes arial font instead.

I know that I have times new roman bold on my computer it is here.

```
/usr/share/fonts/truetype/msttcorefonts
```

How do I make LO "see" this font?

Thanks!

It is not "a" font but a collections of fonts. As far as I can tell it contains the following fonts:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

On 10.04 the package is called "ttf-mscorefonts-installer" so it may not be exactly the same for you.

---

### Post by gatorbrit on 2011-01-22
> **fsando said:**
> It is not "a" font but a collections of fonts. As far as I can tell it contains the following fonts:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

On 10.04 the package is called "ttf-mscorefonts-installer" so it may not be exactly the same for you.


Yes, I have installed that font set.  My point, perhaps not clear in the original post, is that LO is seeing other fonts in that package but not those that include the font dressing in the title of the font.  For example Times new roman shows up, but times_new_roman_bold doesn't .  I can make times new roman "bold" if I need to, but the problem occurs when I import another document where someone has used one of these fonts that didnt show.

---

### Post by Tigerlinux on 2011-01-22
I just downloaded DEB files and installed.
It works fine.
Look like Ooo, no differences.

---

### Post by Tom 6 on 2011-03-10
Hi :)

I have heard that if you just remove OpenOffice instead of doing a Complete Removal then LibreOffice does pick up your old OOo settings.  I have not tried it myself but others have so i am not certain.

Also i thought LibreOffice was in the repos for Ubuntu 11.04 and 10.04.  I am in 10.10 right now and can't find it in Synaptic so perhaps LibreOffice is not in the rest just yet

Regards from
Tom :)

---

### Post by Old_Man_Unix on 2011-03-14
> **Tom 6 said:**
> Hi :)


Also i thought LibreOffice was in the repos for Ubuntu 11.04 and 10.04.  I am in 10.10 right now and can't find it in Synaptic so perhaps LibreOffice is not in the rest just yet

Regards from
Tom :)

Nope  - not in the regular repositories now - and may not ever be for 10.04 and 10.10 since the default installation for those was Open Office and the two don't play well together.

At this time, you have to add the *PPA for Libreoffice** to your Software Sources if you want to install it in 10.04 or 10.10 or if you are using an early release of 11.04.  For the regular 11.04 release, it will be part of the default installation and will of course be in the repository.  

I strongly suggest you install the application by adding the  PPA  rather than downloading the .deb package(s) from the website.  You will then get all the Libreoffice updates  automatically as part of your regular updating process.

Also, don't forget to install the **GNOME-integration** package as well.  It isn't installed automatically.   Also, if you need additional language packs, you should install those too.

I have not noticed any problems with the MS Core fonts.  I use the Liberation fonts for the most part.  But I had previously installed the  MS Core fonts package  because sometimes  I had needed Times Roman for legal/institutional reasons.  Libreoffice picked up those  with no problem.

***** The PPA for Libreoffice is: **'ppa:libreoffice/ppa'**

---

### Post by krish2011 on 2011-04-02
Thanks for the instructions. I am actually newbie to the ubuntu so i had downloaded the libreoffice 3.3.2 final [LibO_3.3.2_Linux_x86_install-rpm_en-US.tar.gz] that should I do to install this in my system?

---

### Post by maghoxfr on 2011-04-02
> **krish2011 said:**
> Thanks for the instructions. I am actually newbie to the ubuntu so i had downloaded the libreoffice 3.3.2 final [LibO_3.3.2_Linux_x86_install-rpm_en-US.tar.gz] that should I do to install this in my system?

Why not trying its PPA?

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```

---

### Post by john89521 on 2011-04-04
> **maghoxfr said:**
> Why not trying its PPA?

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```


Maghoxfr - the code worked perfectly! Thanks mucho.:)

---

### Post by maghoxfr on 2011-04-04
> **john89521 said:**
> Maghoxfr - the code worked perfectly! Thanks mucho.:)

Glad it helped. ;)

---

### Post by Port 80 on 2011-04-15
> **scouser73 said:**
> As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**[COLOR="Red"]**[/COLOR]** You can have LibreOffice sit along side OpenOffice, but if you want to remove OpenOffice entirely then enter the following command into Terminal **[COLOR="Red"]**[/COLOR]**

****

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: ****

**5** - Then enter the following command into Terminal: ****

You have now successfully installed LibreOffice.
NOTE: The above dpkg commands only do the first part of the installation process. To complete the process, you also need to install the desktop integration packages. To do this, change directory to the desktop-integration directory that is within the DEBS directory, using the following command:

cd desktop-integration

Now run the dpkg command again:

sudo dpkg -i *.deb

---

### Post by mahmudinashar on 2011-04-17
while removing OpenOffice,  the spellchecker and the language support package are also removed. You  can get these packages back by installing the following package. You  can replace &#8220;-en&#8221; with your language in the above command. ([here]("http://www.ubuntubuzz.com/2011/04/libreofiice-33-ppa-repository-install.html"))
[INDENT][COLOR=red][FONT=&quot]sudo apt-get install language-support-en[/FONT][/COLOR][/INDENT]

---

### Post by zhanglini on 2011-06-02
Ok, I have Libre on my USB flash system and tried it out a bit.  It seems all settings from OO are fine, except for macros in Spreadsheet.  They are not "transported" to Libre, so I copied the macros to a text file, then pasted over to the spreadsheet opened in Libre.

---

### Post by acraens on 2011-06-10
when i tried to install libreoffice using the PPA-methode i did get following read out in my terminal. I'm running on Maverick on an old Dell Latitude D505

Any suggestions?

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libobasis3.3-sdk : Depends: libobasis3.3-core01 but it is not installable
 libreoffice : Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~maverick1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: ttf-dejavu but it is not going to be installed
               Depends: ttf-sil-gentium-basic but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: liblucene2-java (>= 2.3.2) but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.2~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/PHP]

---

### Post by tredsyn on 2011-10-10
> **maghoxfr said:**
> Why not trying its PPA?

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```

I installed tango studio (based on Lucid Lynx 10.04) without OpenOffice or LibreOffice. Used the terminal to download libreoffice. This worked for me perfectly.

---

### Post by Tom 6 on 2011-10-11
Hi :)
The clue is in the error message.  It says 
"Try 'apt-get -f install' with no packages (or specify a solution)."

> **acraens said:**
> when i tried to install libreoffice using the PPA-methode i did get following read out in my terminal. I'm running on Maverick on an old Dell Latitude D505

Any suggestions?

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libobasis3.3-sdk : Depends: libobasis3.3-core01 but it is not installable
 libreoffice : Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~maverick1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: ttf-dejavu but it is not going to be installed
               Depends: ttf-sil-gentium-basic but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: liblucene2-java (>= 2.3.2) but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.2~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/PHP]

Of course check what that is likely to do.  All commands have a quick-help / cheat-sheet by using one of these tags "-h" or "--help".  Both usually work.  So try 

apt-get -h

and look for the line that describes what "-f" does.  In this particular case it says
"-f  Attempt to correct a system with broken dependencies in place"
which sounds great :)  So try doing as the error message says and run

sudo apt-get -f install

Mostly avoid using sudo as it can mess-up permissions and cause quite a lot of problems.  Just look at the mess Windows gets in and they tend to run as SuperUser all the time.  Hence their vulnerability to malware.  For installing software you really need to be SuperUser so the "sudo" bit at the front is important.  Unlike Windows you don't need to be SuperUser to run the program after it's installed.  
Regards from
Tom :)

---

