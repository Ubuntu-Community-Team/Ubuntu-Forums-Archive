---
title: "[How To] Install E-Sword on Ubuntu 10.04 [Update]"
date: 2010-07-05
forum: Ubuntu Christian Edition
---

### Post by pavlovgg on 2010-07-05
[B]UPDATE: This guide should also work for the update of E-Sword (9.8.3)

[/B]Greetings!

After struggling myself with running E-Sword on a freshly installed *Ubuntu 10.04*, I finally managed to do it, and in a very simple way indeed. However, this might not work for everyone, but hopefully it will for most of you. 

With this method you will also be able to install add-ons to *E-Sword*: such as bibles, dictionaries, and so forth.

_**I. Obtaining the Necessary Files for Installation**_

**1.** Download newest version of *E-Sword* (**currently 9.8.3**) from [ the official site]("http://e-sword.net/downloads.html")

Download any bibles, dictionaries, etc, if you'd like.

**2.** Download _[mfc42.dll file]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html")_

**3.** Download and install ***Wine*** by going to *Terminal (Applications - Accessories - Terminal)* and write
```

[I]sudo apt-get install wine
sudo apt-get update
sudo apt-get upgrade[/I]
```[B]

4. [/B]After the Wine installation,  reboot (you can do it through Terminal by writing: ***sudo reboot***) and continue with the next step.

_**II. The Installation Process**_

**1.**Go to your *E-Sword* installation *.exe* that you've downloaded earlier, right click on it and go to *Properties -> Permission ->* set the ***Access*** on all points to ***Read and Write*,  **and turn on ***Allow executing file as program*, **and click Close. 

Right click the *.exe* again, and choose: ***Open with Wine ***

Install *E-Sword* on its default location. Once its done, go to the Desktop where the installation had made shortcut. Right click on it -> Properties -> Permission and set the ***Access*** on every point to ***Read and Write*, **as well as turning on ***Allow executing file as program*.** Now click Close

**2**. Go to the *mfc42.dll* file that you've downloaded earlier, right click it -> ***Copy***. Now go to* Places -> Home Folder*, and click ***Ctrl + H*** to bring the hidden folders, and search for ***.wine -> drive_c -> windows -> system32***, then *Paste* the *mfc42.dll* file inside (*right click on an empty space -> Paste*).
[U]
**III. Completion**[/U] 

**3. **Run *E-Sword* with *Wine* 

Additionally, you can now install any Bibles, Dictionaries, and so forth, if you would like to do so.

Hopefully it will work for you as it did for me and others.

Edit: It works for Ubuntu 10.10, and the new Wine 1.3 (Remember to re-add the repositories after you update Wine to 1.3).

---

### Post by david_kt on 2010-07-05
> **pavlovgg said:**
> Greetings!

After struggling myself of running ESword on a newly installed Ubuntu 10.04, I finally managed to do it, and in a very simple way indeed. However, this might not work for everyone, but hopefully it will. 

With this method you'll be also able to install add-ons to ESword, such as bibles, dictionaries, and so forth.

**I. Getting the files needed**

1. Download newest version of E-Sword (currently 9.6.0) from [ the official site](http://e-sword.net/downloads.html)

Download any bibles, dictionaries, etc, if you'd like.

2. Download _[mfc42.dll file]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html")_

3. Download and install Wine by going to Terminal (Applications - Accessories - Terminal) and write
```
 sudo apt-get install wine
sudo apt-get update
sudo apt-get upgrade
```After the Wine installation,  reboot (you can write in Terminal: sudo reboot) and continue with the next step.

**II. Installation**

1.Go to your ESword installation .exe that you've downloaded earlier, right click on it and go to Properties -> Permission -> set the **Access** on all points to **Read and Write,  **and turn on **Allow executing file as program, **and click Close. 

Right click the .exe again, and choose **Open with Wine **

Install E-Sword on its default location. Once its done, go to the desktop where the installation had made shortcut. Right click on it -> Properties -> Permission and set Access on every point to **Read and Write, **as well as turning on **Allow executing file as program.** Close

2. Go to the mfc42.dll file that you've downloaded earlier, right click it -> Copy. Now go to Places -> Home Folder, and click Ctrl + H and search for **.wine -> drive_c -> windows -> system32** and paste the mfc42.dll file inside. 

3. Run E-Sword with Wine

Hope it works for you

You could use e-sword installer:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

or from CE:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

replace sudo apt-get install ubuntu-ce with e-sword-installer if what you want is only e-sword.

DK

---

### Post by pavlovgg on 2010-07-06
Hi

I have tried with the installer as well, though I was receiving an error each time.

---

### Post by david_kt on 2010-07-06
> **pavlovgg said:**
> Hi

I have tried with the installer as well, though I was receiving an error each time.

What is the error?

DK

---

### Post by pavlovgg on 2010-07-06
> **david_kt said:**
> What is the error?

DK

Hi,

I won't be able to specifically check for it anymore since I've already installed the program, but it was similar to the one posted below, plus an additional error which, unfortunately, I cannot seem to remember exactly.


```
Esword_installer error: Note: command 'env WINEPREFIX=/home/user/.wine_Esword wine /home/user/.wineswordcache/setup951.exe' returned status 194. Aborting.
```

---

### Post by cwmoser on 2010-07-07
Pavlovgg, that was a very well written description of how to install E-Sword.  Not only did I successfully install E-Sword on both my desktop and laptop, I learned some new techniques I can use for other Linux use - i.e. Ctrl+H and setting access for opening with wine.  I did those functions a different and laborious way.

Thanks again for the good work.

Carl



> **pavlovgg said:**
> Greetings!

After struggling myself of running ESword on a newly installed Ubuntu 10.04, I finally managed to do it, and in a very simple way indeed. However, this might not work for everyone, but hopefully it will. 

With this method you'll be also able to install add-ons to ESword, such as bibles, dictionaries, and so forth.

**I. Getting the files needed**

1. Download newest version of E-Sword (currently 9.6.0) from [ the official site](http://e-sword.net/downloads.html)

Download any bibles, dictionaries, etc, if you'd like.

2. Download _[mfc42.dll file]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html")_

3. Download and install Wine by going to Terminal (Applications - Accessories - Terminal) and write
```
 sudo apt-get install wine
sudo apt-get update
sudo apt-get upgrade
```After the Wine installation,  reboot (you can write in Terminal: sudo reboot) and continue with the next step.

**II. Installation**

1.Go to your ESword installation .exe that you've downloaded earlier, right click on it and go to Properties -> Permission -> set the **Access** on all points to **Read and Write,  **and turn on **Allow executing file as program, **and click Close. 

Right click the .exe again, and choose **Open with Wine **

Install E-Sword on its default location. Once its done, go to the desktop where the installation had made shortcut. Right click on it -> Properties -> Permission and set Access on every point to **Read and Write, **as well as turning on **Allow executing file as program.** Close

2. Go to the mfc42.dll file that you've downloaded earlier, right click it -> Copy. Now go to Places -> Home Folder, and click Ctrl + H and search for **.wine -> drive_c -> windows -> system32** and paste the mfc42.dll file inside. 

3. Run E-Sword with Wine

Hope it works for you

---

### Post by pavlovgg on 2010-07-07
> **cwmoser said:**
> Pavlovgg, that was a very well written description of how to install E-Sword.  Not only did I successfully install E-Sword on both my desktop and laptop, I learned some new techniques I can use for other Linux use - i.e. Ctrl+H and setting access for opening with wine.  I did those functions a different and laborious way.

Thanks again for the good work.

Carl

You are most welcome.

---

### Post by felijay on 2010-07-08
That was very well written. I have followed your steps and have now installed Esword on my Ubuntu 10.04. Thaaaaaannnnnnkkkkkksssss!!!!

---

### Post by pavlovgg on 2010-07-11
> **felijay said:**
> That was very well written. I have followed your steps and have now installed Esword on my Ubuntu 10.04. Thaaaaaannnnnnkkkkkksssss!!!!

You're welcome.

---

### Post by okos on 2010-07-12
> **pavlovgg said:**
> Hi,

I won't be able to specifically check for it anymore since I've already installed the program, but it was similar to the one posted below, plus an additional error which, unfortunately, I cannot seem to remember exactly.


```
Esword_installer error: Note: command 'env WINEPREFIX=/home/user/.wine_Esword wine /home/user/.wineswordcache/setup951.exe' returned status 194. Aborting.
```

I got a similar error with Ubuntu 10.04.

---

### Post by okos on 2010-07-12
Thanks for the post. It worked for me and it is quite simple as in the KISS method. :)

I wanted to enable one esword install for multiple users.
I, the administrator, was thinking of adding sym links from my directory to /home. Create a group called esword, and change recursively users to esword.

Any other suggestions regarding adding an Icon to each user's desktop?

---

### Post by pavlovgg on 2010-07-12
> **okos said:**
> Thanks for the post. It worked for me and it is quite simple as in the KISS method. :)

I wanted to enable one esword install for multiple users.
I, the administrator, was thinking of adding sym links from my directory to /home. Create a group called esword, and change recursively users to esword.

Any other suggestions regarding adding an Icon to each user's desktop?

Your question seems beyond my humble knowledge, but one thing you could probably try is enter into */home/.wine/drive_c/program files/e-sword/* and ***right click*** on *e-sword.exe *and choose **Make Link**. Then, with the link being made, ***right click*** it -> choose ***Cut***, and ***Paste* **it at the Desktop of the user. Make sure the .exe is ***Executable ***(through ***right click -> Properties -> Permissions***). Then simply do so for each user.

---

### Post by i2amdavid on 2010-07-24
Hello, I followed your instructions and installed E sword in Ubuntu 10.4 Thanks. But I cannot load other Bibles or Commentaries. How do I do that?
Also on mu other machine UBUNTU 9.10. I managed to open E-Sword but not even KJV was opened. Help, an aged new Ubuntu fan.
i2amdavid

---

### Post by pavlovgg on 2010-07-27
> **i2amdavid said:**
> Hello, I followed your instructions and installed E sword in Ubuntu 10.4 Thanks. But I cannot load other Bibles or Commentaries. How do I do that?
Also on mu other machine UBUNTU 9.10. I managed to open E-Sword but not even KJV was opened. Help, an aged new Ubuntu fan.
i2amdavid

Hi

Simply download any Bibles or Commentaries .exe's on the desktop, ***right click them -> Properties -> Permissions ->*** and tick ***Allow Executing File as Program**. **Close***, ***right click*** the .exe again ->** *Open with Wine***, and then install the Bible/Commentary program. Then simply start E-Sword and the Bible/Commentary should now appear there.


About your second question regarding Ubuntu 9.10: I don't know. This guide is only for Ubuntu 10.04. Apologies

---

### Post by stlsaint on 2010-07-28
> **i2amdavid said:**
> Hello, I followed your instructions and installed E sword in Ubuntu 10.4 Thanks. But I cannot load other Bibles or Commentaries. How do I do that?
Also on mu other machine UBUNTU 9.10. I managed to open E-Sword but not even KJV was opened. Help, an aged new Ubuntu fan.
i2amdavid

Few questions to better help:
1. How did you install E-sword.
2. Are you running UCE?

---

### Post by i2amdavid on 2010-08-05
Thank you for the replies  I still cannot open other Bibles or commentaries. I am not running UCE, if I did does it mean a complete reinstall? 
David

---

### Post by jonathonblake on 2010-08-06
> **i2amdavid said:**
>  I am not running UCE, if I did does it mean a complete reinstall? 

I'm running e-Sword on a Zenix system. 

What I did was:
* Blow away WINE.
From the command line
```

ps -A | grep wine

```
For every line that is displayed run
```

kill -9 first_number_of_line

```
This is to terminate any wine sessions that are running.

then run
```

cd .\
ls -al | grep wine

```
The first line switches you to your home directory.
The second line is to display all of the wine directories you have.

[color=red]**Caution: doing this wrong will delete a lot more than you expect.**[/red]
For every directory that is listed, do the following
```

cd .wine
(use the name of directory, if it differs.)
(remember the "." that is part of the directory name.)

```

Before running the following command, make sure that you are in the correct directory.  
Double check, to be sure you are in the right directory.
```

rm -Riv *

```
This will display one file at a time, asking if you want to delete it.   If you are in a WINE directory, the answer is "y" (for yes).  If you are anywhere else, the answer is "n" (for no).

Once all of the appropriate directories have been deleted type
```

exit

```
That closes your command line session.
If it doesn't close, ignore any error message and repeat typing "exit", until it does close.

Start Synaptic Package Manager.
Search for "wine".
">Edit >Search >wine"

Mark for removal everything that that search marks as having been installed on your system.

When you've done that, click on the "apply" button.
When synaptic is finished, close it.

Log out of your account.
(On my laptop, I did a system reboot here.  That isn't necessary, but some people find it easier to reboot the system, than log out.)

Log back into your account.
Start synaptic.
search for "wine"
You should find "wine1.2".   Mark if for installation.
Hit the "apply" button.
When synaptic is finished, close it.

If you don't have a copy of mfc42.dll, you'll need to obtain a copy of it. (I don't know where on the net it can be found, but it is available.)

Open firefox or other web browser.
Go to "http://www.e-sword.net/downloads".
Download the current version of e-Sword.

After it has finished downloading, close firefox.
Locate the e-Sword file you just downloaded.
Click on it.
You should see "Open With Windows Program Loader" as an option. Click that one.  (On my system, it is the second option.  The first option is "Open with Archive Manager"  Selecting that option won't do anything useful.)

The installation process may complain about missing files.  Write down the name of all files it says are missing.

Find your copy of mfc42.dll. Click on it, selecting copy.
Switch to your Wine directory. Within it, switch to the Windows directory, then the System32 directory.  Paste your copy into that directory.

If the installation process complained about any other files being missing, find them, and throw them into the system32 directory.

Start e-Sword.

It should start and be ready to use within seconds.(sixty seconds at the absolute most.)
Make your normal configuration for e-Sword.

###

For the record, I don't use rm interactively.  OTOH, on more than one occasion, I have blown away my entire home directory, and all subdirectories --- including directories that were both soft linked, and hard linked to subdirectories in my home directory.   This is not something you want to experience.  Doing this is on a par with having two root canals on the same afternoon.

jonathon

---

### Post by i2amdavid on 2010-08-28
Thank you for your info, sorry for delay, but I will wait until I have some personal backup before trying it as it looks a bit scary.
David

---

### Post by ClrScr on 2010-08-30
Thanks for the Post. It works.

BUT!!!!!!!!

What I really want to do is to be able to do an offline installation, that is, on a PC that does not have access to the www.

Can someone please explain to me how to do that.
This will include how to 
Install Wine and E-Sword.

In theory it should be not that difficult

I tried doing the WINE thing from
[howto-install-wine-offline.html]("http://www.wine-reviews.net/wine-reviews/tips-n-tricks/howto-install-wine-offline.html")

And I finished the first step but due to my noobness I do not understand this:
```
apt-get -qq --print-uris install filezilla wine1.2 > apt_list
awk '{gsub("\x27", "", $0); print $1}' <> apt_list_new
```

I have no idea what it means or how to make it understand that I want to run E-Sword.

Why the offline installation?
I have to do this on a few different machines that do not have www and it will be MUCH quicker if I can just download all the stuff once and then install via terminal seeing that the connection is pretty slow, and sometimes off-site in the Bush (I am in Madagascar)

Thanks
God Bless
J

---

### Post by jonathonblake on 2010-08-30
> **ClrScr said:**
> 
What I really want to do is to be able to do an offline installation, that is, on a PC that does not have access to the www.


Download the appropriate WINE debs. 

Download the e-Sword executable.
Locate and download mfc42.dll.

Use gdebi to install the WINE debs.

To install e-Sword
```

Locate the e-Sword file you just downloaded.
Click on it.
You should see "Open With Windows Program Loader" as an option. Click that one. (On my system, it is the second option. The first option is "Open with Archive Manager" Selecting that option won't do anything useful.)

The installation process may complain about missing files. Write down the name of all files it says are missing.

Find your copy of mfc42.dll. Click on it, selecting copy.
Switch to your Wine directory. Within it, switch to the Windows directory, then the System32 directory. Paste your copy into that directory.

If the installation process complained about any other files being missing, find them, and throw them into the system32 directory.
Start e-Sword.

```

jonathon

---

### Post by ClrScr on 2010-08-30
> **jonathonblake said:**
> Download the appropriate WINE debs. 

Download the e-Sword executable.
Locate and download mfc42.dll.

Use gdebi to install the WINE debs.



jonathon

Thanks Jonathon, it looks easy. Hopefully it will be.

wrt to the WINE debs

Are they to be found on Sourceforge ie
[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign]("http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign")

[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/]("http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/")

Excuse me if I am stupid. I seem to think these are tarballs, but I do not know where to find the deb files. I do not see a link on the WINE site

thanks

---

### Post by crytek80 on 2010-09-12
I had tried for a long time.... it was wonderfully described,thanks a lot ...May HE Bless You.

---

### Post by david_kt on 2010-09-12
> **ClrScr said:**
> Thanks Jonathon, it looks easy. Hopefully it will be.

wrt to the WINE debs

Are they to be found on Sourceforge ie
[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign]("http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign")

[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/]("http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/")

Excuse me if I am stupid. I seem to think these are tarballs, but I do not know where to find the deb files. I do not see a link on the WINE site

thanks

To install wine, open terminal and:

```
sudo apt-get install wine
```

To use beta package, follow instruction on link below:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

DK

---

### Post by k3jsparks on 2010-09-20
Thanks! I found your advice very helpful. I love e-Sword and was thinking about switching back to Windows though I really did not want to. I knew there was a way to do it and I am glad you figured it out! Thanks alot!:KS

---

### Post by pavlovgg on 2010-10-14
You are most welcome.

---

### Post by pavlovgg on 2010-11-05
Note:

Guide ought to work for the new 9.7 version.

---

### Post by Deer Hunter on 2011-02-17
> **ClrScr said:**
> Thanks Jonathon, it looks easy. Hopefully it will be.

wrt to the WINE debs

Are they to be found on Sourceforge ie
[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign](http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2.sign)

[http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/](http://sourceforge.net/projects/wine/files/Source/wine-1.2.tar.bz2/)

Excuse me if I am stupid. I seem to think these are tarballs, but I do not know where to find the deb files. I do not see a link on the WINE site

thanks

Go to [www.winehq.org](www.winehq.org), and click the "Download" link, which should be just above middle left on the page.  From there, if you click on "Download Ubuntu Packages" you will get instructions on how to install the latest Wine on your machine. Hope that helps.

Back to the main topic, I sincerely thank you Pavlogg for making a simple and easy way to get e-Sword on my computer, it works beautifully. Using your instructions, I can install e-Sword not only on my Ubuntu 10.04, but also Linux Mint 9. It's great!

---

### Post by pavlovgg on 2011-02-19
> **Deer Hunter said:**
> Go to [www.winehq.org]("http://www.winehq.org"), and click the "Download" link, which should be just above middle left on the page.  From there, if you click on "Download Ubuntu Packages" you will get instructions on how to install the latest Wine on your machine. Hope that helps.

Back to the main topic, I sincerely thank you Pavlogg for making a simple and easy way to get e-Sword on my computer, it works beautifully. Using your instructions, I can install e-Sword not only on my Ubuntu 10.04, but also Linux Mint 9. It's great!


You are welcome. 

I would like to note that it still works with the updated version of E-Sword, the update Wine version, and with the updated Ubuntu 10.10. Remember to re-add the Wine repositories after you update Wine.

---

### Post by uboer on 2011-03-03
[@pavlovgg]("http://art.ubuntuforums.org/member.php?u=1103589")

Thank you very much for your great (simple and straight to the point) instructions.:D

I have followed other advices on other threads which did not work.

Newbies like me really appreciate clean comments!!!!

---

### Post by frank cox on 2011-03-21
Hi David - Jonathan:
Just in case there are others like me still struggling with Linux they  may have to open a terminal and do something like this {assuming the  esword files are on the desktop in a folder called esword}
cd /desktop
sudo chown username esword

That is what I had to do to get it to let me change the access to read write.

If there is an easier way please post it.

---

### Post by frank cox on 2011-03-21
actually sudo  chmod 777 /home/user/desktop/esword  would be easier I think

				Join Date: Jun 2010
 				 				 	  					Beans: 13 				
 			       Ubuntu 10.10 Maverick Meerkat

---

### Post by frank cox on 2011-03-21
The install worked beautifully. Have you solved the download from inside the program problem?
Thanks again!

---

### Post by frank cox on 2011-03-21
I spoke too soon-the program installed beautifully-the desktop launcher and the one in Applications worked. The programs works great but as I expected I could not download modules through the program . I assumed the launcher would work but I received these errors.
        [LEFT]When I tried to manually load a module I got :[/LEFT]
        [LEFT]The E-sword add-on cannot be installed because E-sword is not currently installed , or the currently installed version is older than version 9.0. [/LEFT]
        [LEFT]{It is 9.83}[/LEFT]
        [LEFT]/home/username/,wine_Esword wine /home/username/Desktop/esword/ante-nicene.exe&#8217; returned status 67. Aborting[/LEFT]

---

### Post by pavlovgg on 2011-03-24
I actually experience the same issue at the moment. Unfortunately, the author of E-Sword seems to have removed the modules from the site, and they can only be downloaded from within the program.

---

### Post by frank cox on 2011-03-25
Sorry I do not have time to look up the link right now but Jeff on the Puppy Linux forum somehow found the links that will allow you to download the links directly from any browser on any os.
Just search for how to install Esword or E-sword on Puppy Linux

---

### Post by david_kt on 2011-03-25
> **frank cox said:**
> Sorry I do not have time to look up the link right now but Jeff on the Puppy Linux forum somehow found the links that will allow you to download the links directly from any browser on any os.
Just search for how to install Esword or E-sword on Puppy Linux

You should use the installer at the first post of below thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

After that you could install addons from the installer.

DK

---

### Post by frank cox on 2011-03-26
Hi David:

   Unfortunately this is what happened when I used the installer.

From my last post:
                                                  I spoke too  soon-the program installed beautifully-the desktop launcher and the one  in Applications worked. The programs works great but as I expected I  could not download modules through the program . I assumed the launcher  would work but I received these errors.
        [LEFT]When I tried to manually load a module I got :[/LEFT]
        [LEFT]The  E-sword add-on cannot be installed because E-sword is not currently  installed , or the currently installed version is older than version  9.0. [/LEFT]
        [LEFT]{It is 9.83}

David I just wish everyone realised just how much you have done , it;s incredible. Thanks
[/LEFT]

---

### Post by frank cox on 2011-03-26
For those that are still having problems with the modules this is how you can get them from outside the program, I can't get them to load except in my older version -9.60.

[Bibles]("http://www.e-sword.net/bibles.html")- [www.e-sword.net/bibles.html](www.e-sword.net/bibles.html) 
[Commentaries]("http://www.e-sword.net/commentaries.html") - [www.e-sword.net/commentaries.html](www.e-sword.net/commentaries.html) 
[Dictionaries]("http://www.e-sword.net/dictionaries.html") - [www.e-sword.net/dictionaries.html](www.e-sword.net/dictionaries.html) 
[Devotions]("http://www.e-sword.net/devotions.html") -  [www.e-sword.net/devotions.html](www.e-sword.net/devotions.html) 
[Graphics]("http://www.e-sword.net/graphics.html") - [www.e-sword.net/graphics.html](www.e-sword.net/graphics.html) 
[Extras]("http://www.e-sword.net/extras.html") - [www.e-sword.net/extras.html](www.e-sword.net/extras.html)  [IMG]http://www.murga-linux.com/puppy/templates/subSilver/images/spacer.gif[/IMG]

---

### Post by jonathonblake on 2011-03-26
> **frank cox said:**
> For those that are still having problems with the modules this is how you can get them from outside the program,

To Frank's list add:

[LIST]
[*]Illustrations: [http://www.e-sword.net/illustrations.html](http://www.e-sword.net/illustrations.html)
[*]Recent Files: [http://www.e-sword.net/recent.html](http://www.e-sword.net/recent.html)
[/LIST]

I do not know the URL for the following resource types:
[LIST]
[*]Topical Files;
[*]Harmony Resources;
[/LIST]

The *Download Resource Manager* will display the official resources.  In some instances, it even downloads them. What I do not know, is what I did to trigger the download process.  :(

---

### Post by frank cox on 2011-03-26
Thanks

---

### Post by david_kt on 2011-03-27
> **frank cox said:**
> Hi David:

   Unfortunately this is what happened when I used the installer.

From my last post:
                                                  I spoke too  soon-the program installed beautifully-the desktop launcher and the one  in Applications worked. The programs works great but as I expected I  could not download modules through the program . I assumed the launcher  would work but I received these errors.
        [LEFT]When I tried to manually load a module I got :[/LEFT]
        [LEFT]The  E-sword add-on cannot be installed because E-sword is not currently  installed , or the currently installed version is older than version  9.0. [/LEFT]
        [LEFT]{It is 9.83}

David I just wish everyone realised just how much you have done , it;s incredible. Thanks
[/LEFT]

Please download the latest installer and install latest e-sword using that installer. After that choose addons listed in the installer. For latest e-sword, the manual download means addons downloaded using MS windows.

DK

---

### Post by frank cox on 2011-03-27
> **david_kt said:**
> Please download the latest installer and install latest e-sword using that installer. After that choose addons listed in the installer. For latest e-sword, the manual download means addons downloaded using MS windows.

DK


My bad, I guess I was using the old installer. Let me make sure I got this strait, if I download modules by using the links I provided or by using windows they will load through the new installer ,is that correct?

I am assuming the new installer is on the old thread?

By the way have you ever tried The Word ? I downloaded it the other day and it installed with one click. It seems to be in the same class with E-sword and will run all its modules as well. Haven't had time to test it thoroughly but so far so good.

Thanks again!

---

### Post by david_kt on 2011-03-27
> **frank cox said:**
> My bad, I guess I was using the old installer. Let me make sure I got this strait, if I download modules by using the links I provided or by using windows they will load through the new installer ,is that correct?

I am assuming the new installer is on the old thread?

By the way have you ever tried The Word ? I downloaded it the other day and it installed with one click. It seems to be in the same class with E-sword and will run all its modules as well. Haven't had time to test it thoroughly but so far so good.

Thanks again!

Yes, the new installer not using exe files anymore for addons, but bblx etc. Just see the first post I have put a change log there.

DK

---

### Post by frank cox on 2011-03-28
> **david_kt said:**
> Yes, the new installer not using exe files anymore for addons, but bblx etc. Just see the first post I have put a change log there.

DK

Thanks

---

### Post by nysnsweet on 2011-06-28
Ok I'm having issues... I have followed david's post to install e-sword here [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

But now, I can get e-sword to open, just bibles or tips.  I have downloaded more bibles, and its still the same...no bible texts.

What should i do?

---

### Post by david_kt on 2011-06-28
> **nysnsweet said:**
> Ok I'm having issues... I have followed david's post to install e-sword here [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

But now, I can get e-sword to open, just bibles or tips.  I have downloaded more bibles, and its still the same...no bible texts.

What should i do?

Did you use the installer? If not, try to use the installer. If yes, try reinstall using the installer, watch out for any error.

DK

---

### Post by nysnsweet on 2011-06-28
Sorry, I didnt mean to mistype my previous post...

E-sword can open up, but there are no bibles.  Also, the tip of the day is blank.  The different chapters show up on the left, but the text doesnt.  I downloaded a few bibles (the .exe files) but they still wouldn't load on E-sword.  I tried to reinstall the installer.  I ticked the manual setting when it asks what to install and the error message says:

Esword_installer error: Note: command 'env WINEPREFIX=/home/stephen/.wine_Esord wine /home/stephen/Desktop/e-Sword.desktop' returned status 193.  Aborting.

I also have Wine 1.0.1

---

### Post by david_kt on 2011-06-29
> **nysnsweet said:**
> Sorry, I didnt mean to mistype my previous post...

E-sword can open up, but there are no bibles.  Also, the tip of the day is blank.  The different chapters show up on the left, but the text doesnt.  I downloaded a few bibles (the .exe files) but they still wouldn't load on E-sword.  I tried to reinstall the installer.  I ticked the manual setting when it asks what to install and the error message says:

Esword_installer error: Note: command 'env WINEPREFIX=/home/stephen/.wine_Esord wine /home/stephen/Desktop/e-Sword.desktop' returned status 193.  Aborting.

I also have Wine 1.0.1

Please download the latest installer, and choose first option, not manual.

DK

---

### Post by frank cox on 2011-06-29
> **david_kt said:**
> Please download the latest installer, and choose first option, not manual.

DK

" I also have wine 1.01"

That may be your problem!

Here is a suggestion . Read the instructions on the Puppy Linux Forum.   The fellow who wrote those instructions, Jim 1911.  .works back and  forth with DavidKing  and others here.

The thread is here :
 [http://www.murga-linux.com/puppy/viewtopic.php?t=53250&sid=f4ec9ff9aa5dd603fd56490fb35f5b7]("http://www.murga-linux.com/puppy/viewtopic.php?t=53250&sid=f4ec9ff9aa5dd603fd56490fb35f5b7f")

.  Download [ e-Sword]("http://www.e-sword.net/downloads.html") installation files, setup972.exe plus any other desired modules.  [B]Unfortunately this link now just downloads e-Sword v9.8.2 and is no longer active to download modules, see EDIT below. 
[/B] 
3.  Before installation, two missing files, needed by e-Sword,[COLOR=darkred]MFC42.DLL[/COLOR] and [COLOR=darkred]msls31.dll[/COLOR]  must be located and copied to [COLOR=green]/root/.wine "C:\\windows\\system32\"[/COLOR], otherwise the installation file will not work properly.   
 
4.  Next in order for the graphics to work properly, use  Wine configuration (in console [COLOR=green]winecfg[/COLOR]) to set [COLOR=darkred]riched20.dll[/COLOR] and [COLOR=darkred]oleaut32.dll[/COLOR] to [COLOR=green]native[/COLOR].  Press the Libraries tab > type riched20.dll > press add >  press edit > choose Native (windows).  Do the same for oleaut32.dll.    
 
NOTE1:  Known problem, the e-Sword Graphics Viewer may not work with wine versions higher than 1.1.40-i486.pet.  
That sounds like one of your  your problems, That is way too old.[f]("http://www.murga-linux.com/puppy/viewtopic.php?t=53250&sid=f4ec9ff9aa5dd603fd56490fb35f5b7f")

Jim 1911  and David King are the salt of the earth and either will help you regardless of which distro you prefer.  Try reading the thread at Puppy Linux   and  be sure to remove wine 1.1 and install 1.39 , to 1.41 add the dll's etc.  If that does not work write Jim or David. If all else fails I could copy my  wine folder from my machine as well as the  esword desktop file etc.

Then there is plan C. There is a similar program called "The Word" which will play all of Eswords modules and is 100% compatible with wine ,. In other words it will install with no modifications s whatsoever. 


[http://www.theword.net/](http://www.theword.net/)

---

### Post by nysnsweet on 2011-07-05
Thank you Frank cox.  I started to get overwhelmed with the puppy forum and decided to upgrade wine first before doing anything else.  And that solved the problem easily! Thanks,

---

### Post by frank cox on 2011-07-06
u
It is sad that so many get caught up in the my distro is better than yours nonsense that drives people away from Linux.

I use which ever one seems to fit the circumstances the best.   Puppy is great for my ancient P4 on dialup at home . I prefer Lubuntu on my old tablet PC and  I use Mint at the office , Then there are numerous purpose built ones for gaming  with Game Puppy or Ultimate Ubuntu gamer edition and Puppy Linux for security camera systems.
Why would anyone limit themselves?

If I was going to suggest to someone not already a fan of Esword which one to use I would get them to try The Word. It is very good and installs with one click.

If you need a format convertor for audio video try this windows program [http://www.formatoz.com/download.html](http://www.formatoz.com/download.html)

When the format is finished you will get an error message saying the program needs to close.
Just ignore it if you're done or click on i if your not, either way it dose not do anything and your file will have converted just fine.

---

