---
title: "Wine Christian Repository"
date: 2009-10-04
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-10-04
As suggested by Jereme, I am making wine Christian repository to install selected windows software that "just works", no tweaking needed. Below is the list of software as suggested by [cjm5229]("http://ubuntuforums.org/member.php?u=19461") 

[LIST=1]
[*]In the beginning was THE WORD. 
[http://www.theword.gr/index.php?](http://www.theword.gr/index.php?)
[*]The Unbound Bible, is also an excellent resource. It also has a little companion app called Bible Verse that is really nice. It displays random verses in a little window on your desktop. The transparent function doesn't quite work, it displays a gray box instead of a transparent background, but if you set the color of the background to something you like it is still very attractive.
[http://www.theword.gr/index.php?](http://www.theword.gr/index.php?)
[*]The Interlinear Scripture Analyzer installs and runs very well also, Here;
[http://www.scripture4all.org/](http://www.scripture4all.org/)
[*]Theophilos Bible Software This is a beautiful Application, and it is a free Download, however the modules are not free. For those who have to have software with the NIV or other commercial Bible versions, The modules are about the least expensive ones I have seen. One note though, before you run it the first time turn down your volume, it plays a very nice introduction tune and greeting, nice when your prepared for it.
[http://www.theophilos.sk/](http://www.theophilos.sk/)
[*]Not exactly Bible study, but if you are involved in Youth ministry or adult Sunday school this one could be very handy. Easy Sunday school planner:
[http://easy-sunday-school-planner.findmysoft.com/](http://easy-sunday-school-planner.findmysoft.com/)
[*]Virtual Rosary
[http://www.virtualrosary.org/](http://www.virtualrosary.org/)
[/LIST]

Please advise if you want additional software you use in windows to be included. But priority is given to software that just run, no tweaking needed.

DK

---

### Post by jonathonblake on 2009-10-06
> **david_kt said:**
> 
Please advise if you want additional software you use in windows to be included.

BibleMapper:  [http://www.biblemapper.com/](http://www.biblemapper.com/)

KoineWerks: [http://www.lexelsoftware.com/](http://www.lexelsoftware.com/)

You'll have to talk with with software owners, if you want to include them in downloadable package.

jonathon

---

### Post by david_kt on 2009-10-07
> **jonathonblake said:**
> BibleMapper:  [http://www.biblemapper.com/](http://www.biblemapper.com/)

KoineWerks: [http://www.lexelsoftware.com/](http://www.lexelsoftware.com/)

You'll have to talk with with software owners, if you want to include them in downloadable package.

jonathon

I have included both the above software in the wine christian repos. I did not ask any permission as it is just a script.

To install it:

```
sudo apt-get update
sudo apt-get dist-upgrade 
```

And then find the installer at Application >> System tool >> Wine Christian Repository

The Bible Mapper could launch normally, but it is quite slow.

DK

---

### Post by refdoc on 2009-10-07
Did you get it to work under wine?

It crashed on me routinely until I gave up

---

### Post by david_kt on 2009-10-07
> **refdoc said:**
> Did you get it to work under wine?

It crashed on me routinely until I gave up

Which software? Which version of wine were you using? Today I tried using wine 1.1.30, all the above software could run.

DK

---

### Post by bthudson23 on 2009-10-07
Thanks for all the hard work you've put into these. This is awesome. I'm a ubuntu ce newby so to speak. But I'm loving what I've seen so far. I have one question. I ran this to install the Sunday School planner and for some reason I can't type anything into it. It just beeps when I type. I've made sure that I have all the latest updates. Not sure if I missed something. 

Keep up the good work!

---

### Post by david_kt on 2009-10-08
> **bthudson23 said:**
> Thanks for all the hard work you've put into these. This is awesome. I'm a ubuntu ce newby so to speak. But I'm loving what I've seen so far. I have one question. I ran this to install the Sunday School planner and for some reason I can't type anything into it. It just beeps when I type. I've made sure that I have all the latest updates. Not sure if I missed something. 

Keep up the good work!

Thank you for your feedback. Previously it is reported run flawlessly on September 5th, 2008:

[http://ubuntuforums.org/showthread.php?t=911121&highlight=bible+software](http://ubuntuforums.org/showthread.php?t=911121&highlight=bible+software)

But looks like the one available now is new version which was release on  21 Oct 2008, and it is true we could not type anything to in the new version. I would try to solve this matter.

DK

---

### Post by david_kt on 2009-10-08
I have found out the problem with Sunday School planner is wine regression. When I downgrade to wine 1.0.1, Sunday School planner could run normally.

I will update the installer tomorrow to have two wine install at the same time. Sunday School planner will use wine 1.0.1 whereas others would still use the latest development wine. 

But you should only run 1 type of wine at one time. That means, when you launch Sunday School planner, you must make sure there is no other wine application running.
 
DK

---

### Post by david_kt on 2009-10-09
Now I have updated the Wine Christian Repository to solve Easy Sunday School Planner. Please do as follow:

```
sudo apt-get update
sudo apt-get upgrade
```

After that you could launch Wine Christian Repository and choose esp. After finish, please do not choose launch program. It is better to restart you computer before launching esp. This is to make sure there is no other wine running.

And do not run esp parallel with other wine program. The reason is that the script would install wine 1.0.1 and launch it to run esp

DK

---

### Post by mgc1952 on 2009-10-13
DK,

I just wanted to say that I was very pleasantly surprised to see this addition to CE.

I think the word is a great program. Trying to learn some Greek on my own I was excited to see ISA in the repo and Theophilos is a program I have used in the past.

I had been away from CE for awhile and was sad to see that CE had disappeared. Glad its back

Mark

---

### Post by stlsaint on 2009-10-15
i am unable to access the christian repos stated here...its not under my system tools menu...what am i missing?

---

### Post by david_kt on 2009-10-15
> **stlsaint said:**
> i am unable to access the christian repos stated here...its not under my system tools menu...what am i missing?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and you should have wine christian repos.

DK

---

### Post by stlsaint on 2009-10-16
i did and its not there...am i looking in the wrong place..i thought i was suppose to be in app>system tools> wine christian repos

did update and upgrade again and still nothing

---

### Post by david_kt on 2009-10-16
Give me the output of:

```
cat /etc/apt/sources.list.d/ubuntuce.list

```

DK

---

### Post by stlsaint on 2009-10-17
i dont have that in my sources.d dir...i only have two items in that dir!
1) crosswire-ppa.list
2) crosswire-ppa.list.backup

```
saint@saint-laptop:~$ cd /etc/apt/sources.list.d/ubuntuce.list
bash: cd: /etc/apt/sources.list.d/ubuntuce.list: No such file or directory
saint@saint-laptop:~$ cat /etc/apt/sources.list.d/ubuntuce.list
cat: /etc/apt/sources.list.d/ubuntuce.list: No such file or directory
saint@saint-laptop:~$ 
```

---

### Post by david_kt on 2009-10-17
> **stlsaint said:**
> i dont have that in my sources.d dir...i only have two items in that dir!
1) crosswire-ppa.list
2) crosswire-ppa.list.backup

```
saint@saint-laptop:~$ cd /etc/apt/sources.list.d/ubuntuce.list
bash: cd: /etc/apt/sources.list.d/ubuntuce.list: No such file or directory
saint@saint-laptop:~$ cat /etc/apt/sources.list.d/ubuntuce.list
cat: /etc/apt/sources.list.d/ubuntuce.list: No such file or directory
saint@saint-laptop:~$ 
```

Then follow the convert instruction to add the source list:

[http://www.ubuntuce.com/convert.htm](http://www.ubuntuce.com/convert.htm)

and then 

```
sudo apt-get dist-upgrade
```

DK

---

### Post by stlsaint on 2009-10-18
ok im doing it now but i wonder...why do i have to convert christian edition to christian edition! i mean i installed christian edition from livecd from actual iso!

---

### Post by stlsaint on 2009-10-18
hey...did as you said and i can see the repo now but when i try and install THE WORD thru the installer i get this:

```
Executing wine /home/saint/.winebiblecache/theword-setup-3.0-en.exe
wine: could not load L"Z:\\home\\saint\\.winebiblecache\\theword-setup-3.0-en.exe": Bad EXE format for 
Note: command 'wine /home/saint/.winebiblecache/theword-setup-3.0-en.exe' returned status 193.  Aborting.
```

---

### Post by david_kt on 2009-10-18
> **stlsaint said:**
> ok im doing it now but i wonder...why do i have to convert christian edition to christian edition! i mean i installed christian edition from livecd from actual iso!

That is because we move the repository after I release the beta iso. I hope to release production iso soon.

DK

---

### Post by david_kt on 2009-10-18
> **stlsaint said:**
> hey...did as you said and i can see the repo now but when i try and install THE WORD thru the installer i get this:

```
Executing wine /home/saint/.winebiblecache/theword-setup-3.0-en.exe
wine: could not load L"Z:\\home\\saint\\.winebiblecache\\theword-setup-3.0-en.exe": Bad EXE format for 
Note: command 'wine /home/saint/.winebiblecache/theword-setup-3.0-en.exe' returned status 193.  Aborting.
```

That is because default dansguardian setting is very restrictive. I have adjusted the default setting for ubuntu CE to loosen it a bit. Could you run dansguardian gui, and choose autoconfigure/reset dansguardian and tinyproxy.

After that launch wine christian repository and choose clear_cache, relaunch wine christian repository and choose the_word.

DK

---

### Post by stlsaint on 2009-10-18
@DK

Alright i did what you said and and started word and it downloading some stuff than the installer started but after choosing to install the main program if freezes on the install page on the gui. nothing happens and i let it run for quite some time! its probably something im missing but im not seeing it. :)

---

### Post by david_kt on 2009-10-18
> **stlsaint said:**
> @DK

Alright i did what you said and and started word and it downloading some stuff than the installer started but after choosing to install the main program if freezes on the install page on the gui. nothing happens and i let it run for quite some time! its probably something im missing but im not seeing it. :)

The latest wine (1.1.31) has regression, try to downgrade to lower version of wine for installation of the word. I will update the installer soon.

DK

---

### Post by stlsaint on 2009-10-18
> **david_kt said:**
> The latest wine (1.1.31) has regression, try to downgrade to lower version of wine for installation of the word. I will update the installer soon.

DK


sorry but i have never downgraded wine...not sure how?

---

### Post by david_kt on 2009-10-18
> **stlsaint said:**
> sorry but i have never downgraded wine...not sure how?

You could use synaptic, search wine and after that <ctrl> E, select lower wine version.

If that option not available, remove wine and download it manually from below:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

DK

---

### Post by shane2peru on 2009-10-19
I'm just curious, is the repo only for 32bit?  I don't seem to have it on my 64bit boxes.  More of a curiosity, than anything else.  

Shane

---

### Post by david_kt on 2009-10-19
> **shane2peru said:**
> I'm just curious, is the repo only for 32bit?  I don't seem to have it on my 64bit boxes.  More of a curiosity, than anything else.  

Shane

Try 
```
sudo apt-get dist-upgrade
```

If still not there, most likely it has old repository.

Check:

```
cat /etc/apt/sources.list.d/ubuntuce.list
```

If it is not there, follow:

[http://www.ubuntuce.com/convert.htm](http://www.ubuntuce.com/convert.htm)

and 

```
sudo apt-get dist-upgrade
```

DK

---

### Post by shane2peru on 2009-10-19
Ok, here is what I get: 
```

cat /etc/apt/sources.list.d/ubuntuce.list
deb http://ubuntuce.com/repos/Ubuntu_CE/ jaunty_amd/

# PPA for Crosswire Packaging Team

```
I really don't want to go through the convert thing again.  It tends to double my sources.  Not a big deal, just a minor annoyance.  Does the above mean I should have it?  If I'm not mistaken it should add some installers either in Accessories, or in System Tools in the menu?  I do have the e-Sword installer, but that is it.  Also the dist-upgrade says everything is up to date.  

Shane

---

### Post by david_kt on 2009-10-19
> **shane2peru said:**
> Ok, here is what I get: 
```

cat /etc/apt/sources.list.d/ubuntuce.list
deb http://ubuntuce.com/repos/Ubuntu_CE/ jaunty_amd/

# PPA for Crosswire Packaging Team

```
I really don't want to go through the convert thing again.  It tends to double my sources.  Not a big deal, just a minor annoyance.  Does the above mean I should have it?  If I'm not mistaken it should add some installers either in Accessories, or in System Tools in the menu?  I do have the e-Sword installer, but that is it.  Also the dist-upgrade says everything is up to date.  

Shane

Yes, you should have it in System Tools, below e-Sword installer. Have you done sudo apt-get update before sudo apt-get dist-upgrade? If yes, you could just check again

```
sudo apt-get install ubuntu-ce
```

In case it still fails (not sure why) do manual install, download it from below:

[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_amd/wine-christian-repos_1.1_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_amd/wine-christian-repos_1.1_all.deb)

DK

---

### Post by shane2peru on 2009-10-19
> **david_kt said:**
> Yes, you should have it in System Tools, below e-Sword installer. Have you done sudo apt-get update before sudo apt-get dist-upgrade? If yes, you could just check again

```
sudo apt-get install ubuntu-ce
```

DK

That did it.  I got it now.  Thanks.

Shane

---

### Post by shane2peru on 2009-10-20
WOW!  Very impressed with the wine Christian Repository.  Very nice.  Excellent way to offer those applications.

Shane

---

### Post by stlsaint on 2009-10-21
> **david_kt said:**
> You could use synaptic, search wine and after that <ctrl> E, select lower wine version.

If that option not available, remove wine and download it manually from below:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

DK


if i remove wine or force an older version i will also lose :
1)ubuntu ce
2)e-sword installer
3) wine christian repos

---

### Post by david_kt on 2009-10-21
> **stlsaint said:**
> if i remove wine or force an older version i will also lose :
1)ubuntu ce
2)e-sword installer
3) wine christian repos

Do not install wine older than 1.1.6. May be you could try 1.1.30. After that, followed by:

Lock Wine Version (to prevent automatic upgrade), and then:

```

sudo apt-get install ubuntu-ce
```

DK

---

### Post by stlsaint on 2009-11-12
i have downgraded my wine and cleared cache and i can still see the christian repo but installing The Word doesnt work. I was able to install something else from the repos but The Word just freezes at the install screen.

---

### Post by david_kt on 2009-11-12
> **stlsaint said:**
> i have downgraded my wine and cleared cache and i can still see the christian repo but installing The Word doesnt work. I was able to install something else from the repos but The Word just freezes at the install screen.

Downgraded to which version? Please help to try wine 1.0.1 as I want to make it default wine in Karmic. I will make a workaround for e-Sword to work with wine 1.0.1.

DK

---

### Post by Bill Farris on 2010-02-09
Hi
I just installed Wine Microsoft Windows Compatibility Layer (Beta Release) and when I did that I lost the Wine Christian Repository out of the System Tools on Ubuntu.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  Is there anything I can do to get it back?

---

### Post by david_kt on 2010-02-09
> **Bill Farris said:**
> Hi
I just installed Wine Microsoft Windows Compatibility Layer (Beta Release) and when I did that I lost the Wine Christian Repository out of the System Tools on Ubuntu.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  Is there anything I can do to get it back?

```
sudo apt-get install ubuntu-ce
```

or 

```
sudo apt-get install wine-christian-repos
```

If not successful, you have to remove additional repository you might just added (winehq).

DK

---

### Post by jonathonblake on 2010-02-10
> **jonathonblake said:**
> 

KoineWerks: [http://www.lexelsoftware.com/](http://www.lexelsoftware.com/)


The domain registration for this program has expired. 
Probably should be removed from the package.  :(

jonathon

---

### Post by aircooledbusnut on 2010-03-01
The word will not install through the repository.

Get this error: Bible_installer error: Note: command 'wget -nd --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://www.theword.gr/files/packages/en/theword-setup-3.0-en.exe](http://www.theword.gr/files/packages/en/theword-setup-3.0-en.exe)'  returned status 1.  Aborting

Then this error;
Bible_installer error: Note: command 'wine /home/mycomp/.winebiblecache/theword-setup-3.0-en.exe' returned status 2. Aborting

Basic same errors attempting install of Interlinear Scripture Analyzer

Bible Verse,Theophilos,Easy Sunday School Planner, and Virtual Rosary all installed with no issues.

---

### Post by david_kt on 2010-03-01
> **aircooledbusnut said:**
> The word will not install through the repository.

Get this error: Bible_installer error: Note: command 'wget -nd --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://www.theword.gr/files/packages/en/theword-setup-3.0-en.exe](http://www.theword.gr/files/packages/en/theword-setup-3.0-en.exe)'  returned status 1.  Aborting

Then this error;
Bible_installer error: Note: command 'wine /home/mycomp/.winebiblecache/theword-setup-3.0-en.exe' returned status 2. Aborting

Basic same errors attempting install of Interlinear Scripture Analyzer

Bible Verse,Theophilos,Easy Sunday School Planner, and Virtual Rosary all installed with no issues.

Thank you for your feedback. After I check, The Word has been upgraded to 3.1 version so as I need to update the installer as well as they remove 3.0 version from the web.

The same goes for Interlinear Scripture Analyzer, it has been upgraded from 2.1 version to 2.1.2. And 2.1 version has been removed from the web. I will update the installer soon.

DK

---

### Post by aircooledbusnut on 2010-03-01
Thanks David

---

### Post by david_kt on 2010-03-02
> **aircooledbusnut said:**
> Thanks David

It is done, please upgrade wine christian repos to use it. The update manager should prompt you automatically for this update. But if it is not, do:
```

sudo apt-get update
sudo apt-get upgrade

```
DK

---

### Post by aircooledbusnut on 2010-03-03
Thanks David,

The new Installer worked flawlessly.

Clint

---

### Post by fachex on 2010-05-05
Wine Christian Repository will not install in Lucid Lynx due to dependency problem with Wine. Any suggestion?
Fabian

---

### Post by david_kt on 2010-05-05
> **fachex said:**
> Wine Christian Repository will not install in Lucid Lynx due to dependency problem with Wine. Any suggestion?
Fabian

Which wine did you install? If you install wine 1.2, could you downgrade to wine 1.0.1 and try to install Wine Christian Repository again?

DK

---

### Post by andrew5859 on 2011-05-22
When I went to add the wine-christian-repos via sudo, I got this:  W: Failed to fetch [http://ppa.launchpad.net/wine-christian-repos/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/wine-christian-repos/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

what's up with this....is there something I'm missing...help

---

### Post by andrew5859 on 2011-05-22
Also...when I run the wine-christian repos link, I get this:  QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/andrew/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

what do I need to do to get this to work....can anyone help please, it would be greatly appreciated...God Bless

Andrew

---

### Post by andrew5859 on 2011-05-22
I have tried your instructions from below about dansguardian and wine-christian-repos cache clear.....I'm getting this when I open the christian repos:  Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

Where is the address to this or what is it and how can I insert this into the ibus file folder

---

### Post by andrew5859 on 2011-05-22
> **david_kt said:**
> Thank you for your feedback. After I check, The Word has been upgraded to 3.1 version so as I need to update the installer as well as they remove 3.0 version from the web.

The same goes for Interlinear Scripture Analyzer, it has been upgraded from 2.1 version to 2.1.2. And 2.1 version has been removed from the web. I will update the installer soon.

DK


I don't know if anyone has really been keeping track of this but, The Word is now in version 3.2.1.1167 so obviously no one is looking or working to keep current so everyone can download this from the Wine-Christian-Repositories.  I've left several comments on another thread to which nobody is really paying attention.  I know I sound a little impatient, but it just appears that either no one has any real answers or no specific (detailed) solution.

---

### Post by jonathonblake on 2011-05-22
> **andrew5859 said:**
>  so obviously no one is looking or working to keep current so everyone can download this from the Wine-Christian-Repositories.

Unless a program specifically allocates somebody to package it, and that individual keeps up with changes in the program, the version in the repository is going to be several versions behind the current version.

jonathon

---

### Post by andrew5859 on 2011-05-23
I have a question to anyone who can figure it out; when I open Wine Christian Repository....I get this output before anything I do:  Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

How do I get the ibus-daemon's address, or where do I get it or find it and where would I put it???

---

### Post by andrew5859 on 2011-05-23
OK....maybe we could disregard the former comment, I think I found an answer.  In package manager, type in the search bar; ibus, when it brings up a list, mark for installation; ibus, ibus-m17n, ibus-table, and for added measure, I added; ibus-qt4, ibus-gtk, python-ibus.  Though I'm not getting the previous connection error message, I still can't load the word 3.0....it's a bad .exe file, so you'll have to go to the website and download the 3.2.1.1167 version.....[http://www.theword.net/index.php?article.download&l=english](http://www.theword.net/index.php?article.download&l=english)

---

### Post by Archangelos on 2011-11-15
> **david_kt said:**
> That is because default dansguardian setting is very restrictive. I have adjusted the default setting for ubuntu CE to loosen it a bit. Could you run dansguardian gui, and choose autoconfigure/reset dansguardian and tinyproxy.

After that launch wine christian repository and choose clear_cache, relaunch wine christian repository and choose the_word.

DK

In short, you need to # out .exe (and any other desired download extension) in your dansguardian banned extension list through either DG GUI, or Webcontentcontrol.

Yes, I'm putting Wine Christian Repo on, but I still think it needs to be updated.

What do you say, david. How about an upgrade of the repo, eh? We would certainly enjoy it.

---

### Post by Archangelos on 2011-11-15
> **andrew5859 said:**
> OK....maybe we could disregard the former comment, I think I found an answer.  In package manager, type in the search bar; ibus, when it brings up a list, mark for installation; ibus, ibus-m17n, ibus-table, and for added measure, I added; ibus-qt4, ibus-gtk, python-ibus.  Though I'm not getting the previous connection error message, I still can't load the word 3.0....it's a bad .exe file, so you'll have to go to the website and download the 3.2.1.1167 version.....[http://www.theword.net/index.php?article.download&l=english](http://www.theword.net/index.php?article.download&l=english)

The url just needs to be changed in the script is all. I'll try to do that this week, it is a bad url and not functioning.

I said yesterday that I didn't want to get caught up in re-scripting this thing because I don't have time. I shouldn't have to do this.

David, we need an update, my brother. With all due respect.

---

### Post by jonathonblake on 2011-11-21
> **Archangelos said:**
> The url just needs to be changed in the script is all.

Do you have source code for the *Wine Christian Repository*?  If so, can you send me a copy of it?

jonathon

---

### Post by Anastasis on 2011-11-22
> **jonathonblake said:**
> Do you have source code for the *Wine Christian Repository*?  If so, can you send me a copy of it?

jonathon

 Yeah. I've got it. It's just a hacked Wine Tricks script is all. Pretty straight forward. It works for the job. Been hacking around on it for the last few days during breaks. I'll get it to you. Give me a day or two as my brain is fried between installing and testing distros right now.  Maybe I won't have to do anything on it now that david_kt is around.  It could be fully updated in like 4 hours or something if I (or somebody) would just sit down and punch the keys.

I'll freely give it to you because I really don't want to do it. I wear thick prescription glasses and can't see the screen half the time because of my eyes, especially if I'm tweaking out on drinking too much Pepsi Lite.

---

### Post by jonathonblake on 2011-11-23
> **Anastasis said:**
>  I wear thick prescription glasses and can't see the screen half the time because of my eyes,

The virtue or using Orca on Linux, and JAWS on Windows.

jonathon

---

