---
title: "Wine or Crossover Office for clueless newbie"
date: 2005-04-11
forum: The Cafe
---

### Post by muzza on 2005-04-11
I have a couple of windoze programs that are stopping me from going 100% to Linux.  I downloaded wine and installed it - I ran it - didn't know what I was doing - downloaded and printed almost the entire wine instructions - Huh??

There doesn't seem to be a page that tells you how to actually install and use a windoze program in wine.

Lots and lots of configurations and more configurations, but no 'how to use wine'!

I've heard that Crossover Office is easier for commandlinephobes.

I've searched the websites for both Wine and Crossover Office to find which Windoze progs will run on each program.  Wine's list is much longer.  There are thousands of programs listed on the Crossover Office site, but most of them are marked 'untested'.

I thought Crossover Office was basically a gui for wine?  If a program works in Wine, surely it will work in crossoveroffice?

An example would be Powertabs v1.7

---

### Post by connellr on 2005-04-11
I deffinatly recomend Crossover Office (cxoffice).  I have tried many times to convert from Windows to Linux and always failed until I got Crossover Office.  

I've got the following programs installed using cxoffice:
- Internet Explorer 6 (Only for pages that absolutly require it)
- Quicken 2004
- Microsoft Office
- All of the fonts I had in windows (had to copy some over manually rather than install)

Everything is launched easily if you install KDE (kubuntu) it will even add a section to your K-menu called "Windows Applications" that has all the windows installed apps for easy launching.  

If your in doubt [download the demo version](http://www.codeweavers.com/products/download_trial/), and try it for the 30 free days... well worth the $35 or whatever if you ask me!

PS > In regards to the "untested" applications, click on any of them and each app has its own mini forum where users talk about how it works, and any challanges in getting it to work. 

PPS > Crossover office isn't JUST a gui for Wine, but it is powered by Wine (they've added enhancements to Wine).  That said if the program works in Wine its a pretty sure bet that it will work in Crossover.

PPPS > No, I dont work for CodeWeavers, just a big fan ;)

---

### Post by emperor on 2005-04-12
One CX4.2 tester rated Powertabs v1.7 as Bronze which means it basicly runs in Crossover Office. At wineHQ, Powertabs v1.7 is rated as high as silver which is a good sign it will work for you in Linux.

I say try out the CX4.2 Demo, give it a test drive!

I might install Powertabs v1.7 myself as I play the guitar a bit!

Win4Lin will have another release of WinPro out later this month that will let you install WinXP in linux. I have Win2000 running in Linux as well as CX4.2. By the end of the year, you should be able to install 90-95% of Windows programs in Linux using Crossover Office 5.x (future release)! At least that is the goal and it looks to be possible too!

---

### Post by crane on 2005-04-12
I'm not familiar with crossover. I use open pffice for anything office related.

Wine is very simple though. If you have it installed and want to install something just put the the word wine before it ( you may need to use sudo as well)

Example

# sudo wine /media.cdrom0/setup.exe

hope this help. I haven't looked into it but I would check around before installing MS Office with wine. Just to prepar yourself for any conflicts that may arise.

Good Luck!!

---

### Post by darkoptix on 2005-04-12
I would also recommend cxoffice, because I am a fan of it too. I could never get Qwix working in wine very well(xbox dvd ripping/xiso creater program - one the things I need windows for :( ) When I tried in cxoffice, it worked flawlessly. It's simple and easy to use too btw. Try the trial out.

---

### Post by professor_chaos on 2005-04-12
Yes, I'm very happy with cxoffice. I wouldn't have been able to switch entirely over to Linux without it (and wine) to run M$acess at work. 

Also give xwine a shot. Same thing as wine, with a graphical interface.

Good luck, I was just like you, and had a hard time switching over to linux because of one or two programs, but with the help of these programs, windoze is history.

---

### Post by muzza on 2005-04-16
Well, I downloaded CrossoverOffice and powertabs doesn't work.  Well it does work to a degree.  You can create a powertabs file and save it, but if you try to open a file, powertabs crashes.

I can't find wine anymore.  I reinstalled Ubuntu last week and I think I forgot to save the installer - cause it aint on my 'pooter anymore.

If an app doesn't work in CXOffice, one would assume that it also wouldn't work in wine.  Is this the case?

---

### Post by emperor on 2005-04-16
You may need to add a few real DLL's from windows to get it to work properly.
see this link: [http://appdb.winehq.org/appview.php?versionId=2784](http://appdb.winehq.org/appview.php?versionId=2784)

---

### Post by JGJones on 2005-04-16
Without knocking CrossOver Office - I've heard good things about it, but not having a credit card I could not purchase it so I looked for a free alternative. I would recommend you use WineTools - completely free and runs MS Office 97 to XP very well (I haven't had any problem with it) 

It will completely set up your Wine for you, including the download of IE6 (works), Outlook Express, Media Player 6.4, fonts, system files and so on. Then it allows you to install software such as MS Office.

It then place scripts to automatically do all the wine stuff to load up the MS programs. I do this for MS Word and MS Excel (mostly for this - OpenOffice and others just can't match Excel yet really to be frank)

And it's all free.

BUT not ideal for a newbie...cos you can get it via the resposity BUT that doesn't work. Took a bit of work before I got mine to work - the problem is WineTools work with a older version of Wine (October 2004 version) and although it could with newer version it's not tested. So had to download old version, install it myself and WineTools from resposity and it works very well.

Save me money too and I'm able to use my MS Office CD's (well they cost a lot, might as well carry on using the Office 2000 rather than switching to OpenOffice :))

And no need to copy DLL's (I haven't needed to) I do highly recommend WineTools for those that don't mind doing the work themselves to get a older version of Wine instead of using Synaptic/apt-get

---

### Post by t0dzilla on 2005-04-17
wow... what can i say?

i downloaded winetool, extracted it, cd to directory, and try install.sh

returns install.sh: command not found. yet, a simple ls clearly shows install.sh in the directory  (winetools-211jo)
i tried with/without issuing sudo... no love.
has anyone else run into any similar problems? i'm relatively new to linux again... hehe.

thanx in advance

---

### Post by TravisNewman on 2005-04-17
did you ./install.sh? the dot and the slash are important.

Also, is install.sh executable? try chmod 744 install.sh

---

### Post by Azmodan on 2005-04-17
[QUOTE=JGJones]Without knocking CrossOver Office - I've heard good things about it, but not having a credit card I could not purchase it so I looked for a free alternative. I would recommend you use WineTools - completely free and runs MS Office 97 to XP very well (I haven't had any problem with it) [/QUOTE]

I emailed their sale dept and asked if they would accept a check or money order. They said that they prefer credit cards but money orders are fine. They just take a bit longer to proceed compared to credit cards that are pretty much instant. Mail your money order at :

CodeWeavers, Inc.
2356 University Ave W, Suite 420
St. Paul, MN  55114

Add $ 7.95 if you want them to ship you a CD (opposed to download only), available only with the professional version. Don't forget to include your name and e-mail address so they can set up an account for you to download the app and it's updates.

As far as I understood, CodeWeaver takes the instable Wine and stabilize it. Much like what Ubuntu is doing to Debian Unstable. And they add pretty GUI utilities.

---

### Post by t0dzilla on 2005-04-17
oh, thank you so much for the tip, PanickedThumb... btw, i used to have a copy of Thumb Wars, and shall never forget how damned funny it was.

unfortunately, though, the ./install.sh still returns a command not found error...

so i dunno... guess i'll just nurse this headache and get some (more) sleep.
thanx again, and may the farce be with you...

oh, yeah... the chmod tip returns a no such file or directory error. weird.

---

### Post by TravisNewman on 2005-04-17
uh... hmm.

"sh install.sh" might be what you need. Are you sure you're in the right directory?

And yes, Thumb Wars is fantastic-- though I like th Blair Thumb Project the best out of all of them.

---

### Post by t0dzilla on 2005-04-18
ok... here's a good laugh for you. i opened a terminal, opened nautilus, typed sudo in the terminal then dragged the install.sh (from the nautilus window) into the terminal, hit enter, put in the password, and voila! "installing winetools into /usr/local/winetools. not sure if it actually worked, but that's the most progress i've made so far... all those years of using mac os's has really paid off! hehe

thanx again for all the help. i'll keep you posted as to the progrees  (or lack thereof.)

---

### Post by plockery on 2005-04-19
[QUOTE=JGJones]

BUT not ideal for a newbie...cos you can get it via the resposity BUT that doesn't work. Took a bit of work before I got mine to work - the problem is WineTools work with a older version of Wine (October 2004 version) and although it could with newer version it's not tested. So had to download old version, install it myself and WineTools from resposity and it works very well.[/QUOTE]

Can you give me a blow by blow command line install for this process.
I have downloaded the recommended 2004 version of wine.
Unpacked it  and did a ./configure.
Returned an error of no c compiler.
Installed gcc3.3 via synaptic, but still the same error.
This is true whether sudo or not.

How did you install the 2004 version?
And then winetools?

More detail would be very helpful to us newbies!!

---

### Post by plockery on 2005-04-19
Some more information.

I have installed winetools with ./install.sh - no problem.

But wine 20041019 was still a problem.

Found that ./configure  and 'make depend && make' completed once I installed gcc (rather than gcc-3.3), flex, bison and xlibs-dev and dependency packages.
So I now have both winetools and wine 20041019 installed.

However, when i run wt2 (either as sudo or not) it returns these two lines:

found gettext in /usr/bin
Browser is /usr/bin/firefox.

But then a window comes up saying that no version of wine is installed.

Does this mean that wine is not installed in the directory it is looking for, defined where?

My wine is in /home/peter/Wine-20041019/wine-20041019.

How do i correct this?

---

