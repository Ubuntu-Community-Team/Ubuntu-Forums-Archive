---
title: "Script to remove Kubuntu or Xubuntu in full"
date: 2006-04-10
forum: The Cafe
---

### Post by JimmyJazz on 2006-04-10
I noticed several people asking how to remove KDE or XFCE completly from their installs, well this script does just that very quickly and easy.

***NOW IT ASK YOU BEFORE DESTROYING YOUR SYSTEM***

[B]WARNING!!!
THIS SCRIPT IS NOT TESTED UNDER ALL CONDITIONS AND YOUR RESULTS MAY VARY.[/B]

I have only tested it to remove xubuntu but it should work fine with kubuntu as well.

You must have meta packages **ubuntu-desktop** and either **kubuntu-desktop** or **xubuntu-desktop**.

**HOW TO USE:**

**download... **[http://jimmyjazz.homeip.net:808/debuntu.tar.gz]("http://jimmyjazz.homeip.net:808/debuntu.tar.gz") 

tar xvf /home/james/Desktop/debuntu.tar.gz

cd ./debuntu

**to remove kubuntu...**

./removekubuntu.py

**to remove xubuntu... (tested and works well)**

./removexubuntu.py

(please note that the above two commands will remove the respected meta packages only after comparing them to the standard ubuntu-desktop package, hence reverting you back to the standard gnome desktop, I will fix this to allow for other desktop packages at a later time)

[B]
to remove ubuntu Gnome version(yikes)... (a very bad idea!)[/B]

./removegubuntu.py

anyways try it out and leave comments if it works well for you (or doesn't)

**UPDATE***

added "removegubuntu.py" to remove Gnome version of ubuntu (not really a great idea if you ask me)

[B]8-29-2006: Added even more safety precautions to the scripts, they should be safe for most all users now.  Also I removed the gnome version removal script for the time being.
[/B]

[B]4-14-2006: Made scripts much safer by allowing apt to ask before removing packages, all the scripts are now mostly safe to use (as long as you have some small idea what you are doing). 
[/B]

---

### Post by eriefisher on 2006-04-10
What about ./removeubuntu.py  Will this work too?

eriefisher

---

### Post by bjweeks on 2006-04-10
[QUOTE=eriefisher]What about ./removeubuntu.py  Will this work too?

eriefisher[/QUOTE]

No as he didnt make a ubuntu removeing script as i can see.

---

### Post by JimmyJazz on 2006-04-10
[QUOTE=eriefisher]What about ./removeubuntu.py  Will this work too?

eriefisher[/QUOTE]

someday perhaps, someday.

---

### Post by JimmyJazz on 2006-04-10
[QUOTE=eriefisher]What about ./removeubuntu.py  Will this work too?

eriefisher[/QUOTE]

actually I just updated the package with a new script called removegubuntu.py to remove the gnome ubuntu packages
try it at your own risk...
./removegubuntu.py

---

### Post by Thiago on 2006-04-10
work with xubuntu here :)

thanks J

---

### Post by JimmyJazz on 2006-04-12
[QUOTE=Thiago]work with xubuntu here :)

thanks J[/QUOTE]

excellent, has anyone tried it with kubuntu?

---

### Post by Caligula on 2006-04-13
Shit!
I tried to remove KDE with it, it removed all the Gnome stuff!!
half my system is gone!

what do i do now???

should I reinstall ubuntu?

---

### Post by Caligula on 2006-04-13
fortunately, I left the terminal before it deleted EVERYTHING...
so I have the synaptics, I'm in the process of downloading Gnome again now...

This was **very** unsuccesfull...
you did it the other way round or something...

---

### Post by jrib on 2006-04-13
maybe I can suggest a '-s' argument for the script so that it only show what packages it would remove and testers will be more willing to try it :)

---

### Post by Caligula on 2006-04-13
I downloaded Gnome again, but some of the things are not working...
And I'm still stuck with all the KDE stuff...

What do i do now?
I think I'll just get the ubuntu CD and install it all again...

---

### Post by JimmyJazz on 2006-04-14
[QUOTE=Caligula]I downloaded Gnome again, but some of the things are not working...
And I'm still stuck with all the KDE stuff...

What do i do now?
I think I'll just get the ubuntu CD and install it all again...[/QUOTE]


oh crap sorry to hear about this problem I actually discovered it myself today.  You can actually just "sudo apt-get install ubuntu-desktop" it should reinstall everything back to normal.

---

### Post by JimmyJazz on 2006-04-14
[QUOTE=Caligula]I downloaded Gnome again, but some of the things are not working...
And I'm still stuck with all the KDE stuff...

What do i do now?
I think I'll just get the ubuntu CD and install it all again...[/QUOTE]

also you can also remove a large part of KDE base by removing the libqt packages.

---

### Post by JimmyJazz on 2006-04-14
**Also I just updated all the scripts so that they will now ask one by one before removing each and every package.  Much much safer.**

---

### Post by Caligula on 2006-04-14
oh, I've reinstalled Gnome, after it was totally lost(long story...).
I removed the KDE stuff manually, slow but safe...

---

### Post by dk_pa on 2006-05-28
Thank you!  After upgrading to Dapper one of the weird problems I had was constanting being thrown into Xubuntu.  I had it loaded before but just selected when I wanted to work in it --- well nothing was working to boot Gnome by default.  I decided to trash xubuntu ---- well it was detected as installed so "reinstalled" it and trashed it again -- didn't work.  

Your script seems to have done the trick!  I still see Xubuntu when i start my system  (which is fine -- it's prettier :P ). 

Thanks again.

---

### Post by JimmyJazz on 2006-08-29
I just updated this script to version 2.0.5

It is much safer to use.  In fact I would say that they are almost completly safe for most all users to use.

you can download the latest version at 
[http://jimmyjazz.homeip.net:808/debuntu.tar.gz](http://jimmyjazz.homeip.net:808/debuntu.tar.gz)

enjoy

---

### Post by aysiu on 2006-08-29
I don't know if you're aware of this, but I also have a tutorial on how to remove these by pasting a command into the terminal... probably very similar to your script, but I don't know:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by JimmyJazz on 2006-08-29
> **aysiu said:**
> I don't know if you're aware of this, but I also have a tutorial on how to remove these by pasting a command into the terminal... probably very similar to your script, but I don't know:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Mine is similar but more dynamic and faster.

Dynamic because it checks the meta packages for each version on load time.
Faster because it only tries to remove packages that are installed on your system.

Yes not a major deal but I just like doing things better.

---

### Post by aysiu on 2006-08-29
> **JimmyJazz said:**
> Mine is similar but more dynamic and faster.

Dynamic because it checks the meta packages for each version on load time.
Faster because it only tries to remove packages that are installed on your system.

Yes not a major deal but I just like doing things better.
Cool. Just wanted to make sure you knew it existed. Yours does sound cleaner.

---

### Post by Whitehorse1 on 2006-09-24
I've just tried it on Kubuntu and I let the script run through completely.  It did uninstall Gnome, but then reinstalled it.  

My only problem is that when my system starts it still shows the initial Kubuntu screen. Is there any way to fix this?

Thanks!

---

### Post by aysiu on 2006-09-24
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by Owdy on 2006-10-18
Ubuntu remover arent in that package

---

### Post by cvmostert on 2006-12-05
the xubuntu remover seemd to have worked for me... i just had to enter allot to remove all the stufff... just for security i installed ubuntu-desktop agian to see if i have everything... yup! done hopefully works when i reboot... dont have plans doing that soon :-)

---

### Post by Tirobir on 2007-01-20
Xubuntu removal worked great although I would have liked it if it had automated the 101 confirmation dialogs.

Nevertheless great. I wanted to use Xubuntu but it had a bunch of problems, likely stemming from me apt-getting it into Kubuntu, which I apt-got into Ubuntu, both of which I had already played around with quite a bit. I would still like to switch to Xubuntu so I will probably try your Kubuntu script when Feisty is complete and try installing Xubuntu without Kubuntu.

Thanks again! =D>

---

### Post by Kulabula on 2007-03-09
Here lads im confused, If i download those links onto my laptop with Windows XP will that effect it?
Can I download it on the laptop and put them on my memo.stick and transffer them to the other computer with Kubuntu V 6.06 LTS?  
Please reply in easy language im onl 13.
Tnx Kulabula



:guitar: ](*,) ?? Reply fast plz...

---

### Post by maxamillion on 2007-03-09
I hate to be a annoying, but I was wondering why you used apt-get instead of aptitude?

---

### Post by y0ssarian on 2007-03-16
why not just do
```
sudo apt-get remove kubuntu-desktop kubuntu-artwork-usplash
```
or 
```
sudo apt-get remove xubuntu-desktop xubuntu-artwork-usplash
```

and then

```
sudo apt-get autoremove
```

---

### Post by aysiu on 2007-03-16
Have you actually tried that, or did you just think it might work in theory?

Also, the *autoremove* feature for *apt-get* is available only in Edgy Eft.

---

### Post by karellen on 2007-03-16
why not simply "sudo aptitude install kubuntu-desktop" - "sudo aptitude remove kubuntu-desktop" ?...and xubuntu just the same...;)

---

### Post by aysiu on 2007-03-16
Some people didn't have the foresight to install with *aptitude*.

I can't tell you how many times I've seen people write > Oh, just do ```
sudo apt-get install kubuntu-desktop
```

---

### Post by y0ssarian on 2007-03-19
This weekend I thought I'd try KDE and didn't like it. I installed it with 
```
sudo apt-get install kubuntu-desktop
```
and removed it with
```
sudo apt-get remove kubuntu-desktop
sudo apt-get autoremove
```
and it deleted a couple hundred megs of files. I noticed that a couple had to be explicitly removed and did those by hand. I also had to modify my .gtkrc file to remove some of the crap that KDE had installed that was throwing off my font size. For some reason I still can't get my gtk fonts to render like they used to (I did dpkg-reconfigure fontconfig-config to get the OSX look) if you have any suggestions for that.

EDIT: if you cant get autoremove to work, perhaps apt-get -f install might work.

---

### Post by atdi4ever on 2007-03-20
i wish i had this when i first started using ubuntu. but good job anyways.

---

### Post by tjl30 on 2007-04-22
Worked good, but it worried me when it asked to remove the ubuntu-desktop

> The following packages will be REMOVED:
  dbus-1-utils* ubuntu-desktop* update-notifier* xubuntu-desktop*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 827kB disk space will be freed.
Do you want to continue [Y/n]? n


---

### Post by cyrylski on 2007-06-07
perhaps I'm too lame but executing it in bash tells me "no such command" :|

I also tried this [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) but I don't recommend it. It removed my audacious player and luckily it goes from A to Z cuz who knows what else would delete if haven't noticed that :|

---

### Post by JimmyJazz on 2007-06-13
To be honest updates in feisty have made this program obsolete.

---

### Post by GaiusJuliusCaesar on 2007-09-13
> **JimmyJazz said:**
> To be honest updates in feisty have made this program obsolete.
Hey JJ
What do you mean, is there an easy way to remove a *ubuntu desktop you don't want in Feisty?  I'm a N008 and thought I'd try them all out before realising the difference between aptitude and apt-get....

---

### Post by ballas on 2008-05-22
Can't you just remove Xubuntu from the Synaptic Package Manager without risking all kinds of trouble?

---

### Post by geekguoji on 2008-05-22
Sometimes those old chinese dresses are outdated beyond repair  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.  What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.  It is a conventional belief that [silk clothes](http://www.prettyladygirl.com/) should invariably be present in the wardrobe of everyone who claims to be a connoisseur, when it comes to clothes. The fascination of silk fabric dates back to the ancient times. Silk production was already present at the earliest stages of development of human civilization, and silk trade was a very important part of the economy in ancient China. It was the place where the first silkworm breeding and silk manufacturing traditions were established.   Literature, History and Philosophy have covered, and occasionally love to popular movies, but not limited to, circumstances eyeball, and can [cheongsam wholesale](http://www.prettyladygirl.com/) seen from different things. Perhaps, she will learn English,calligraphy, tea ceremony learning, learning flower arranging,yoga. A wide range of hobbies, and accumulation of introversion her soul. Can be with their own inherent temperament is focused woman, a woman is the most flavored woman.   On the other hand, Tang chinese jackets have also been blended with western designs to please the diversified tastes of modern Chinese. Jin Yonglin, assistant to the general manager of Gege, a famous Tang [chinese jacket](http://www.prettyladygirl.com/) manufacturer in Beijing, said, It is wonderful to name Chinese-style costumes Tang chinese jackets, because Tang Dynasty ( 418 A.D.- 907 A.D.) is the most prosperous period in ancient China and China towns throughout the world are also called Tang streets.

---

### Post by aysiu on 2008-05-22
> **ballas said:**
> Can't you just remove Xubuntu from the Synaptic Package Manager without risking all kinds of trouble?
No, not really, unless you have a lot of time on your hands.

Removing *xubuntu-desktop* does not remove all its dependencies, and manually marking each of those for removal isn't an easy task in Synaptic.

If you thnk this sript business is too much trouble, I have a single command you can paste in the terminal to remove Xubuntu: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ballas on 2008-05-22
> **aysiu said:**
> I have a single command you can paste in the terminal to remove Xubuntu

In fact that works great! I'm learning every single day about Ubuntu :) Thanks!

---

### Post by igpf on 2008-06-28
I tried both the remove and purge options with no luck.  That just removed the kde, but all the other applications where still there.  i found this ```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
``` on [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by agibby5 on 2008-07-15
Worked great, thanks!

---

### Post by nitinbobade on 2009-07-11
hello Friend,
I have created shell script file that name's file1.now i want to remove file1 script file,could you tell me,which command should i used????/

My mail ID is [EMAIL="nitinbobade@gmail.com"]nitinbobade@gmail.com[/EMAIL]

Thanks 

Nitin.L.B

---

### Post by waleedakleh on 2009-09-21
> **JimmyJazz said:**
> 
[http://jimmyjazz.homeip.net:808/debuntu.tar.gz]("http://jimmyjazz.homeip.net:808/debuntu.tar.gz") 


this link doesnt work any other i can use

---

