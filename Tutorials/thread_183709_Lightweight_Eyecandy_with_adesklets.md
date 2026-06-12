---
title: "Lightweight Eyecandy with adesklets"
date: 2006-05-28
forum: Tutorials
---

### Post by racoq on 2006-05-28
Hello everyone, since i don't like gdesklets heavy requirements (because is too heavy for the hardware), i've decided to find a more lightweight alternative for gnome. So I present in this small guide how to install, and run adesklet on Gnome, KDE, and XFCE. This guide was tested in Dapper, Edgy and Feisty and Gutsy.

**_Requirements:_**
- Internet connection
- Universe repository enabled

First of all you will need to get the adesklets package by typing the folowing command in the console:

> 
sudo apt-get install adesklets


This will install the adesklet package and all related packages.

**Important Note:**
I advise the upgrade to 0.6.1 or upper, since some important, 
bugs like memory leaks were adressed, for that see the folowing link:

> 
[http://sourceforge.net/project/showfiles.php?group_id=126227](http://sourceforge.net/project/showfiles.php?group_id=126227)



After that, you need to download a valid desklet to use in adesklets

This can be done by two ways:

_1 -_ 
Go to [http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html), and download a valid desklet, if you want to see weather information try downloading the weatherforecast package

You will need to extract the package, and copy it to your home directory for instance:

> 
tar-xvf weatherforecast-0.2.0.tar.bz2
mv  weatherforecast-0.2.0 /home/"you home name account"


_2 -_

run the folowing command and adesklets will automatically give you the option of downloading and installing the adesklets using an graphical user interface:

> 
adesklets -i



Either way. assuming that you've chosen to go by the first step, go to your home directory and do:

> 
cd weatherforecast-0.2.0
./weatherforecast.py


that batch will ask you if you want to register this desklet, say 'r' (you want to register)

This will create the file .adesklets in your home directory and it will fill it with instructions, for running weatherforecast each time adesklets is executed

after that you need to know your city code, so go to weather.com and type your city name:

Click on your city in the search results, and he will display the weather information, copy the link and copy the reference between "/local/" and "?from=", see the following example:

[http://www.weather.com/outlook/travel/businesstraveler/local/POXX0035?from=search_city](http://www.weather.com/outlook/travel/businesstraveler/local/POXX0035?from=search_city)

for my city the weather.com code is POXX0035

after that do inside weatherforecast directory:

> 
sudo nano config.txt


and replace the location default code with your code for instance i've did for my city:

> 
'location': 'POXX0035'


After that to run your adesklet do:

for gnome:
> 
adesklets --nautilus


for kde:
> 
adesklets --kde


for XFCE:
> 
adesklets --xfce4


for Enlightenment:
> 
adesklets --e16


If you want that adesklets load at boot time, in gnome you can go to System => Sessions, KDE and XFCE have equivalent ways of doing that, and add one of the previous lines to startup.

If you want to download and install another desklet you can do something similar what i've did to install the weatherforecast desklet, all desklet include an config.txt, and an python batch file for registering the desklet.

The following scenarios were tested in a AMD k6-II 450 Mhz, with 256 MB RAM:
- Ubuntu (Gnome), and it worked fast.
- Kubuntu (KDE), and it worked fast.
- Xubuntu (XFCE), and it was even faster.


So you can take your own conclusions :D

[B]
Note for BERYL and Compiz users
[/B]

Some users of beryl  have been experiencing  transparency problems with desklets. Since there isn't yet a solution, i found a workaround. This workaround was bnased on the feisty instructions available at the beryl project homepage. If u have any file already loading bery-manager please remove it, or don't load it.

Create the following file in your home directory 


> 
nano startcomposite.sh


after that fill it with the following info:

> 
#!/bin/sh
adesklets --"your DE abbreviation"
sleep 4
beryl-manager
#if you have compiz to the following
#compiz --replace& 


and save the file.

The trick here is to run adesklets before beryl / compiz, and make a sleep of 4, in order to adesklets to load before beryl-manager. Pay attention if you have more applications in the startup, you should include then in that file, for instance in my system, i also load amsn at startup so my startberyl.sh file is:

> 
#!/bin/sh
adesklets --xfce4
sleep 4
beryl-manager
amsn


Finally i had this script in my autostarted applications (In my XFCE system,  Applications  > Settings >  Autostarted Applications)


This workaround worked on my Xubuntu Feisty system.  In other systems the you may have to adjust the time of the sleep if it isn't enough to do the trick.

--

Adesklets its the only desklets program, prepared to be installed in either Gnome, KDE and XFCE, without installing "half system" (like it would be required if you wanted to install gdesklets in another DE than Gnome).

I've uploaded the following screenshot, taken from Xubuntu Feisty, for people who want to see adesklets in action, before installing it.

Hope this guide is useful to you!
--

**_UPDATE**_

A recent change on weather.com have broken weatherforecast desklet behaviour, if you were afected by this, please visit the following post, for the resolution.

[http://ubuntuforums.org/showthread.php?p=5152994#post5152994](http://ubuntuforums.org/showthread.php?p=5152994#post5152994)

---

### Post by yabbadabbadont on 2006-06-03
Good guide.  A quick tip for anyone in the USA, you can just use your 5 digit zipcode instead of looking up the city code as suggested.

---

### Post by Kryptizzle on 2006-06-04
Thanks! Nice guide. This is the first time I've tried really tried to make my desktop look good and it's looking pretty good :P. The next few days look cold according to this desklet :S.

---

### Post by racoq on 2006-06-04
Thanks, this was my first guide, i'm glad someone enjoyed it.

---

### Post by yabbadabbadont on 2006-06-04
Perhaps you can point me in the right direction.  I started a thread in the desktop support forum asking if any one knows how to have gnome run a user script on logoff.  So far there are no takers.  Do you know how to call adesklets -k on logoff so that all running desklets will be shutdown?

---

### Post by racoq on 2006-06-04
See the following thread, i think it will adress your issue:

[http://www.ubuntuforums.org/showthread.php?t=185261](http://www.ubuntuforums.org/showthread.php?t=185261)

---

### Post by giuliastro on 2006-06-04
I tried this with Dapper but nothing happens launching "adesklets --nautilus". Does adesklets work under Dapper or is it just me?

---

### Post by racoq on 2006-06-04
i'm running it well on Dapper, why don't you try, within your desklet directory, for instance:

./weatherforecast.py --nautilus (for weatherforecast, its the same parameter for other desklet)


and try chosing 't' to test.

If it appears then you're setup is OK, and it's working.

If not, please post here the errors.

---

### Post by Poul on 2006-07-26
> **giuliastro said:**
> I tried this with Dapper but nothing happens launching "adesklets --nautilus". Does adesklets work under Dapper or is it just me?
Hey 
Exact same problem. I've tried running the desklet from the console. Here's the output:
```
pawel@pawel-p1500:~/.desklets/weatherforecast-0.2.0$ ./weatherforecast.py
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./weatherforecast.py", line 332, in ?
    Events(dirname(__file__)).pause()
  File "./weatherforecast.py", line 97, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.4/site-packages/adesklets/events_handler.py", line 157, in __init__
    self.ready()
  File "./weatherforecast.py", line 105, in ready
    join(self.basedir,'config.txt'))
  File "./weatherforecast.py", line 79, in __init__
    adesklets.ConfigFile.__init__(self,id,filename)
  File "/usr/lib/python2.4/site-packages/adesklets/configfile.py", line 162, in __init__
    self._load_and_save()
  File "/usr/lib/python2.4/site-packages/adesklets/configfile.py", line 205, in _load_and_save
    all= ConfigImport.load(buf[:])
  File "/usr/lib/python2.4/site-packages/adesklets/configfile.py", line 41, in __call__
    return dict(self._group(
  File "/usr/lib/python2.4/compiler/transformer.py", line 52, in parse
    return Transformer().parsesuite(buf)
  File "/usr/lib/python2.4/compiler/transformer.py", line 129, in parsesuite
    return self.transform(parser.suite(text))
  File "<string>", line 1
    'location': 'UKXX0085'
              ^
SyntaxError: invalid syntax
pawel@pawel-p1500:~/.desklets/weatherforecast-0.2.0$
```
please help.

---

### Post by racoq on 2006-07-26
i guess that it's a bug from the weatherforecast-0.2.0 desklet, i've had the same problem. you can try using, weather 0.0.4 instead at, [http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html). This happens because the weather info that weather.com provides in some city's, some times go down, causing this error from the desklet, however weather 0.0.4, doesn't have this problem.

The use of this desklet was just an example on how to set up adesklets. So don't worry, if you can run another desklet on adesklet that means that your configuration is just fine :) !

---

### Post by zarathustra on 2006-07-26
What version of Adesklets is in the repositories? It looks like the version is older than the current one available for download off Sourceforge.

---

### Post by raul_ on 2006-09-15
I hope this is not a very noobish question but.... when i type adesklets -i in the terminal...nothing happens..i mean, it happens, but i don't know what to type on the prompt =\ 

root@raul:/home/raul # adesklets -i
adesklets 0.4.8 (unknown time), on an unknown OS
[i386-linux-gcc 4.0.gcc-opt (GCC) 4.0.0 20050413 (prerelease) (Debian 4.0-0pre11)]
Press TAB for hints.
0 >>>

---

### Post by yabbadabbadont on 2006-09-15
> **raul_ said:**
> I hope this is not a very noobish question but.... when i type adesklets -i in the terminal...nothing happens..i mean, it happens, but i don't know what to type on the prompt =\ 

root@raul:/home/raul # adesklets -i
adesklets 0.4.8 (unknown time), on an unknown OS
[i386-linux-gcc 4.0.gcc-opt (GCC) 4.0.0 20050413 (prerelease) (Debian 4.0-0pre11)]
Press TAB for hints.
0 >>>
I don't believe that the 0.4.8 version supports the installer (-i) option.  You need a newer version for that.  I'll have to go read the changelog at sourceforge to be sure though.  I'll edit my post with the needed version when I find it.

EDIT: Looks like the curses based installer wasn't added until 0.5.0.

---

### Post by raul_ on 2006-09-15
this error ocurred while compiling adesklets

checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path


but i already have the latest version of python (i think) and i don't think that's the problem...

---

### Post by raul_ on 2006-09-15
Ok got it. Fond this on another forum:

nozey
August 25th, 2005, 09:03 PM
Ok ... got it working already.

I did this:

$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev

And got it working. =)

So ... here goes the steps i made to compile adesklets:

$ wget [http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb](http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb)
$ sudo dpkg -i python-dev_2.4.1-0ubuntu2_all.deb
$ sudo apt-get install python2.4-dev
$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev
$ cd adesklets/dir
$ ./configure
$ make
$ sudo make install

Hope it helps someone. \o/


----------------------------

U can just run synaptic and install those libs, and it should be enough =)

---

### Post by rackne on 2006-09-16
i've just installed adesklets. however when type ```
adesklets --nautilus
``` nothing happes. can anyone tell me what's wrong and how to fix it?

---

### Post by raul_ on 2006-09-16
I'm sorry i must be very stupid...i installed 2 desklets, registered them, and then i try to run adesklets by typing adesklets in the terminal and nothing happens..i know it's running because i can see the process id when i do "ps aux" but the desklets don't load...i think it's the same problem that rackne has. Everyone else seems to get it to work except me =\

---

### Post by rackne on 2006-09-17
it seems like we got the same problem. i really dont know what's wrong. i've asked google, i been to 3 diffrent ubuntu forums and couldnt find the nature of the problem with adesklets. although i suspect that gdesklet might have something to do with that stragne issue coz b4 i had adesklets i'd installed gdesklets first. oh well, i'll try on more time maybe i'll find something on the net if i fail i guess im gonna wait for edgy to come out. hope that the stragne bug (if it is a bug) will be fixed.

---

### Post by raul_ on 2006-09-18
Yeap..and awkwardly, when u install a desklet, it should create a folder named .adesklets in your home dir (i read that) but i checked and there's no such folder in my home dir

---

### Post by yabbadabbadont on 2006-09-26
> **raul_ said:**
> Yeap..and awkwardly, when u install a desklet, it should create a folder named .adesklets in your home dir (i read that) but i checked and there's no such folder in my home dir

Actually, it should create a *file* called .adesklets in your home directory that contains all the registered desklets.  If you use the adesklets installer to install a desklet, it will usually create a directory called .desklets in your home directory and then it will put the desklet into a subdirectory of that based on the name of the desklet.  For example, this is what I have on my system from using the adesklets installer:
```
/home/bubba $ cat .adesklets 
# This is adesklets configuration file.
#
# It gets automatically updated every time a desklet main window
# parameter is changed, so avoid manual modification whenever
# a desklet is running. In fact, manual changes to this file
# should rarely be needed. See `info adesklets'.

[/home/bubba/.desklets/weatherforecast-0.2.0/weatherforecast.py]
id=0 screen=0 x=0 y=638

[/home/bubba/.desklets/doityourself-0.4.1/doityourself.py]
id=0 screen=0 x=0 y=0

/home/bubba $ ls -l .desklets/
total 8
drwxr-xr-x 7 bubba users 4096 Sep 21 18:24 doityourself-0.4.1
drwxr-xr-x 3 bubba users 4096 Sep 25 14:46 weatherforecast-0.2.0

```

---

### Post by ketnoe on 2006-09-26
ok.

My screen flickers when I do a test.
I'm lost as to what to do next.  I don't seem to be able to figure out anything when I do
info adesklets --help
or
info adesklets

help? thanks.

---

### Post by deblike on 2006-09-29
You don't see anything when execute
$ adesklets 
or 
$ adesklets --nautilus

because adesklets by itself is just a framework where desklets will run, it has no graphical interface whatsoever.
To get any desklet working (and showing) you should register it with adesklets framework.
Let's say:
You have already downloaded and decompresed some desklet in your /home, so next you should type something like this:
$ /home/user/desklet-0.1/desklet.py

then choose to register it, to have it working next time you run adesklets framework with:
$ adesklets
or
$ adesklets --nautilus

I'm using "adesklets --nautilus" here because it's what I use, if you use kde, replace --nautilus with --kde.

---

### Post by raul_ on 2006-09-30
I did everythink the "book" says, and nothing happens..

---

### Post by Gio2k on 2006-10-04
The newest version on adesklets homepage is 0.6.1, the newest ubuntu repository version is 0.5.2 or so. Any way of updating adesklets?

---

### Post by Heril on 2006-10-07
Good guide, and following the first method had no problems. However, instructions involving the graphical installer and configuring the desklets is lacking.

---

### Post by hopstah on 2006-10-08
VERY IMPORTANT TIP FOR KDE USERS!!!!!

i found this in this thread:  [http://ubuntuforums.org/showthread.php?t=94782](http://ubuntuforums.org/showthread.php?t=94782)
> **oskude said:**
> well, i have no idea (eg, never used them) but looking at the faq of adesklets```
As on adesklets 0.4.12, supported window managers in that category are:

    * KDE: for versions >= 3.4.1 (earlier versions untested). You need to turn on “Control Center -> Desktop -> Show icons on desktop -> Allow programs in desktop window”, or to turn off the “Show icons on desktop” altogether1.
    * Nautilus
    * ROX-Filer: only preliminary support for now
    * Xfce4
    * xffm-desktop: only preliminary support for now

```
and not seeing gnome there, i could think its g(nome)desklets...

---

### Post by sktfeelsdapper on 2006-10-08
Still doesn't work for me, either way updates or not.
The screen flickers and then nothing happens.
So...
uninstall!

---

### Post by phstpok on 2006-10-09
I get a config error, which I think points to a problem with my python install, after following all instructions, adesklets gets  "Configuration file parsing error `syntax error', stopped at line 8."

Tried removing adesklets & python then re-installing. Everything leads to the same error.

---

### Post by raul_ on 2006-10-09
Lol..i actually got it to work. Most of the desklets give error but i did what deblike said. I registered the desklets (i was only testing it and it gave me the flickering problem) and then "adesklets --nautilus" and the thing just popped up =)

---

### Post by kno712 on 2006-12-11
> **raul_ said:**
> Ok got it. Fond this on another forum:

nozey
August 25th, 2005, 09:03 PM
Ok ... got it working already.

I did this:

$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev

And got it working. =)

So ... here goes the steps i made to compile adesklets:

$ wget [http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb](http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb)
$ sudo dpkg -i python-dev_2.4.1-0ubuntu2_all.deb
$ sudo apt-get install python2.4-dev
$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev
$ cd adesklets/dir
$ ./configure
$ make
$ sudo make install

Hope it helps someone. \o/


----------------------------

U can just run synaptic and install those libs, and it should be enough =)

Hello,

Thanks for this instructions;

I tried several times with sudo checkinstall and it didn't work; I got this messages:

```
creating /usr/lib/python2.4/site-packages/adesklets
copying build/lib.linux-i686-2.4/adesklets/__init__.py -> /usr/lib/python2.4/site-packages/adesklets
error: /usr/lib/python2.4/site-packages/adesklets/__init__.py: No such file or directory
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/sukno/downloads/adesklets-0.6.1/scripting/python'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/sukno/downloads/adesklets-0.6.1/scripting/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sukno/downloads/adesklets-0.6.1/scripting'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.
```

Then I decided to do a sudo make install and now it is installed.


Why sudo checkinstall doesn't work? If someone has the answer then I will post the deb file here for everybody.

---

### Post by kno712 on 2006-12-11
I find a way to do it; after a make install I repeated the checkinstall.

Not the most elegant solution, but a way to solve it.

Here is the file; I'm a newbie, so, if you have problems...I'll try to help you.

---

### Post by bodhi.zazen on 2006-12-16
Nice How-to

This thread has been added to the UDSF wiki.

[Adesklets](http://doc.gwos.org/index.php/Adesklets)

[color=blue]Thanks Ramses de Norre[/color]

---

### Post by fifafrazer on 2006-12-20
The yab desklet is working but i get the following error from the systemmonitor desklet:

```
peter@xubuntu:~/adesklets/SystemMonitor-0.1.3$ ./SystemMonitor.py 
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./SystemMonitor.py", line 43, in ?
    import statgrab
ImportError: No module named statgrab
peter@xubuntu:~/adesklets/SystemMonitor-0.1.3$ 

```
I'm using the adesklet version from the edgy repo

---

### Post by foureight84 on 2006-12-20
yea it doesn't really work if you're running beryl. nothing shows up

---

### Post by raul_ on 2006-12-20
> **fifafrazer said:**
> The yab desklet is working but i get the following error from the systemmonitor desklet:

```
peter@xubuntu:~/adesklets/SystemMonitor-0.1.3$ ./SystemMonitor.py 
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./SystemMonitor.py", line 43, in ?
    import statgrab
ImportError: No module named statgrab
peter@xubuntu:~/adesklets/SystemMonitor-0.1.3$ 

```
I'm using the adesklet version from the edgy repo

Check if you have all the dependencies installed. Seems that you're missing a script. Check them in the Readme file or in the site

> **foureight84 said:**
> yea it doesn't really work if you're running beryl. nothing shows up

I have Beryl installed and use adesklets until i discovered conky :)

---

### Post by foureight84 on 2006-12-23
> **raul_ said:**
> Check if you have all the dependencies installed. Seems that you're missing a script. Check them in the Readme file or in the site



I have Beryl installed and use adesklets until i discovered conky :)

i used to use conky. but i don't know how to make a good looking weather display

---

### Post by raul_ on 2006-12-23
I have one working. Here:
[http://ubuntuforums.org/showthread.php?t=205865&page=32]("http://ubuntuforums.org/showthread.php?t=205865&page=32")

See the first post on the page

---

### Post by yabbadabbadont on 2006-12-23
> **raul_ said:**
> I have one working. Here:
[http://ubuntuforums.org/showthread.php?t=205865&page=32]("http://ubuntuforums.org/showthread.php?t=205865&page=32")

See the first post on the page

By the way, the link you posted goes to different posts depending on the user's preferred number of posts per page setting...  Perhaps you could provide a link to the specific post, please?

---

### Post by raul_ on 2006-12-23
> **tturrisi said:**
> 
pymetar still works w/ conky, thus no need for weather.com, get the weather data directly.
apt-get install python-pymetar
add to conkyrc
${execi 60 /usr/bin/pymetar KIAD}  #where KIAD = the station you want to grab weather data
get your station here:
[http://www.nws.noaa.gov/tg/siteloc.shtml](http://www.nws.noaa.gov/tg/siteloc.shtml)

tweak the pymetar output by editing the file called pymetar in /usr/bin as root

Here it is

---

### Post by oyvindaa on 2007-01-01
When performing the following operation:

```
./SystemMonitor.py --nautilus
```

and testing it, I got this error message:

```
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./SystemMonitor.py", line 1107, in ?
    EventHandler(dirname(__file__)).pause()
  File "./SystemMonitor.py", line 974, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.4/site-packages/adesklets/events_handler.py", line 157, in __init__
    self.ready()
  File "./SystemMonitor.py", line 1004, in ready
    self.meters[-1].create((8,tmp_height), self.basedir, meter[1])
  File "./SystemMonitor.py", line 918, in create
    info = self.parseFile(self.info_file)
  File "./SystemMonitor.py", line 899, in parseFile
    acpi_file = open(file, "r")
IOError: [Errno 2] No such file or directory: '/proc/acpi/battery/BAT0/info'
```

How do I deal with this? :)

The calendar adesklet, however, works just fine.

---

### Post by raul_ on 2007-01-01
See if you installed all the desklet's dependencies. Take a look at the README file that should be in the desklet's folder

---

### Post by oyvindaa on 2007-01-01
Well I've already done that. The README says I'll need the following dependencies:

libstatgrab >= 0.11.1
pystatgrab  >= 0.3

So I installed libstatgrab6, libstatgrab-dev and python-statgrab.

---

### Post by raul_ on 2007-01-01
Hum...i remember i got that desklet working (back in the days)...maybe you should take a look at the adesklets forums...probably someone with your problem already posted it..here's the link:

[http://adesklets.sourceforge.net/forum/]("http://adesklets.sourceforge.net/forum/")

---

### Post by oyvindaa on 2007-01-01
Thanks :)

---

### Post by oyvindaa on 2007-01-01
Sort of solved the problem. Removed the temperature and battery parts from the config.txt.

Not optimal, but it's working.

Something I need to be working properly though, is the use of eth1 (wireless) instead of eth0.

Has anyone succeeded in getting that up and running? 

They've disabled the possibility of registering at the adesklets forum due to spammers, so I can't ask on there..

---

### Post by raul_ on 2007-01-01
In the config.txt file, just look for the "Networking" section and change the interface name from eth0 to eth1

---

### Post by oyvindaa on 2007-01-02
That's what I thought would work as well, but it doesn't.

---

### Post by raul_ on 2007-01-02
Weird :-k works for me...are you sure you aren't changing the example section? (the one with the #'s in the beginning of every line)

---

### Post by oyvindaa on 2007-01-02
Now, I got this working. Turned out it had been working all along actually, just that I sort of misunderstood its function :) 

Thank you for your help though.

---

### Post by lime4x4 on 2007-01-02
trying to build the latest version cause the deb won't install here is the error i'm getting

configure: error: Could not find the readline library
john@john-edgy:~/Desktop/adesklets-0.6.1$ 

i installed every package i could find that contained readline

---

### Post by bg1256 on 2007-01-09
For the life of me, I can't figure out how to determine my city code...

Maybe weather.com has changed or something.

And I've spent the last half an hour on google trying to find it.

---

### Post by yabbadabbadont on 2007-01-09
> **bg1256 said:**
> For the life of me, I can't figure out how to determine my city code...

Maybe weather.com has changed or something.

And I've spent the last half an hour on google trying to find it.

If you live in the US, just use your five digit zipcode.  If not, post your location and perhaps someone will already know the answer (or knows how to find it easily :)).

---

### Post by bg1256 on 2007-01-09
I do live in the US, so I'll try the zip code.

---

### Post by dothedorky on 2007-01-10
<NEWBISH QUESTION>

i really dig the adesklets, and wanted to get the yab-0.0.2 and got this error.

[B]dorkalicious@ubuntu:~$ tar-xvf weatherforecast-0.2.0.tar.bz2
bash: tar-xvf: command not found
[/B]

---

### Post by raul_ on 2007-01-10
it's tar<space>-xvf

---

### Post by dothedorky on 2007-01-11
I've tried it with the corrections, and i get this:

```
 dorkalicious@ubuntu:~$ tar -xvf yab-0.0.2.tar.bz2
tar: yab-0.0.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
 
```

Sort of confused, i downloaded the adesklet as directed to in step one. Still not working for me. Any more ideas?

---

### Post by Sklasko on 2007-01-11
Make sure your cd'd to the directory that you downloaded the tar to.

For example, if you have your browser set to download to the desktop, then open a terminal and...

```
cd Desktop
```

and then proceed with the previously mentioned commands.

---

### Post by dothedorky on 2007-01-11
finally!

```
dorkalicious@ubuntu:~$ cd Desktop
dorkalicious@ubuntu:~/Desktop$ tar -xvf yab-0.0.2.tar.bz2
yab-0.0.2/
yab-0.0.2/icons/
yab-0.0.2/icons/terminal.png
yab-0.0.2/icons/emacs.png
yab-0.0.2/icons/xmms.png
yab-0.0.2/icons/firefox.png
yab-0.0.2/icons/gimp.png
yab-0.0.2/GNUmakefile
yab-0.0.2/README
yab-0.0.2/yab.py
yab-0.0.2/COPYING
yab-0.0.2/config.txt.minimal
dorkalicious@ubuntu:~/Desktop$ mv yab-0.0.2 /home/dorkalicious 
dorkalicious@ubuntu:~/Desktop$ adesklets -i
 
```

so after using the last command, i installed weather forecast and system monitor in addition to yab. It says all three were installed, but i cant seem to open the program. ](*,)

---

### Post by raul_ on 2007-01-11
You didn't install, you just moved the folder..you have to run the desklet. Something like:
```

./nameofthedesklet.py

```

Of course, that has to be done in the desklet's folder

---

### Post by bg1256 on 2007-01-11
I tried compiling from source from the tarball on sourfourge, but for the life of me, I can't figure out how to do it.

I normally just follow instructions given on monkeyblog, but they don't work for this one.

Any idea how I could install that way successfully?

---

### Post by dothedorky on 2007-01-11
I started out my journey with yab, and thanks to everyone's help, i finally got it to show on my desktop. 

FIrst off, I just wanted to note, that although i selected (r) to register the desklet, it did not create the file .adesklets in my home directory (was this only for weatherforecast, or for all adesklets?)

A few things that happened later:

---The default was blue (my desktop is a forest scene with browns and greens) so of course it didnt go well. I tried to move the desklet into my top toolbar, but it refused to do so.

---I right clicked the desklet and clicked on 'configure' and nothing happened. 

---I closed the desklet (manually), and then tried to run the desklet again- since it's the only one i've 'officially' installed into my /home directory, i just typed

```
adesklets
```
into the terminal.

I see a flickering type-thing going on in my upper left hand corner of the desktop (where it normally should appear), but nothing actually appears.

---I checked the adesklets FAQ page and it suggested terminating all desklets that are operating (maybe it was running in the background somewhere, or i didnt close it properly) by using

```
killall -9 adesklets
```

then trying restarting the adesklet again. Again with the flickering.

So now i have a desklet that i cant see but i know is there. All this work (for me anyhow lol) and i didnt even get to experience it long enough for it to be actually functional!](*,)

---

### Post by racoq on 2007-01-12
> **bg1256 said:**
> I tried compiling from source from the tarball on sourfourge, but for the life of me, I can't figure out how to do it.

I normally just follow instructions given on monkeyblog, but they don't work for this one.

Any idea how I could install that way successfully?

Generally for tar.gz or tar.bz2 archives, you can do, for instances for the latest version of adesklets.

> 
 tar -zxvf adesklets-0.6.1.tar.bz2  


a adesklets-0.6.1 directory will be created

After that you will need to make sure that your system has the adesklets pre-requisites for compiling doing inside the adesklets-0.6.1 directory

> 
./configure 


(if you have dependency problems, specific errors will appear, post them here if you didn't managed to solve them)

after all the requirements check are successfully done, than you must execute the following command to compile:

> 
make


after that you just want to install the compiled adesklets to the system, doing

> 
sudo make install



I haven't found any particular issue compiling adesklets.

---

### Post by bg1256 on 2007-01-12
Yes, those are all the steps I've taken.

However, I may be missing some of the libraries required... I forgot to check that.

Thanks!

---

### Post by bg1256 on 2007-01-13
After running ./configure, I get this errror:
edit: let me just post the entire output, there are some warnings as well.

```
benjamin@BG-notebook:~/adesklets/adesklets-0.6.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
configure: WARNING:
-----------------------------------------------------
`flex' was not found on your system. If you encounter
problems recompiling a `l' file, please try `flex'
first. You can get it from any GNU archive site.
You will not need `flex' as long as you do not
modify `l' files.
----------------------------------------------------
checking for bison... no
checking for byacc... no
configure: WARNING:
-----------------------------------------------------
Nor `byacc' or `yacc' parsers had been used
for developing adesklets. If you encounter problems
recompiling a `y' file, please try `bison' instead.
You can get it from any GNU archive site. You will
not need `bison' as long as you do not modify
`y' files.
-----------------------------------------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path
benjamin@BG-notebook:~/adesklets/adesklets-0.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by bg1256 on 2007-01-13
Has anyone run this under Beryl?

I'm trying to run it on two machines.

On Edgy with Beryl, I get it installed just fine, but most of the desklets just plain look funny.

On Dapper, I still can't get it installed properly: see above post.

---

### Post by dothedorky on 2007-01-16
*bump*

still no suggestions for the flickering?

---

### Post by yabbadabbadont on 2007-01-16
> **dothedorky said:**
> *bump*

still no suggestions for the flickering?

Try launching all registered deskletts with "adesklets --nautilus".  Assuming, of course, that you are using Gnome.

---

### Post by tlacuache on 2007-01-16
> **bg1256 said:**
> Has anyone run this under Beryl?

I'm trying to run it on two machines.

On Edgy with Beryl, I get it installed just fine, but most of the desklets just plain look funny.



I installed Beryl last night (running with the nvidia layer underneath it) and my desklets look the same as they did before.

---

### Post by Omnios on 2007-01-16
I just installed the latest version with .configure / make and / fakeroot checkintall and only had to install a lib dev package. Cudos and home this world well.

---

### Post by dothedorky on 2007-01-16
> **yabbadabbadont said:**
> Try launching all registered deskletts with "adesklets --nautilus".  Assuming, of course, that you are using Gnome.

I am using gnome, however i only registered/installed the yab desklet.

---

### Post by yabbadabbadont on 2007-01-16
> **dothedorky said:**
> I am using gnome, however i only registered/installed the yab desklet.

Doesn't matter how many you have registered.  When you are using gnome, you need to add the "--nautilus" option when calling adesklets since nautilus is hiding the real root window and it has to be worked around.

---

### Post by racoq on 2007-01-16
> **bg1256 said:**
> After running ./configure, I get this errror:
edit: let me just post the entire output, there are some warnings as well.

```
benjamin@BG-notebook:~/adesklets/adesklets-0.6.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
configure: WARNING:
-----------------------------------------------------
`flex' was not found on your system. If you encounter
problems recompiling a `l' file, please try `flex'
first. You can get it from any GNU archive site.
You will not need `flex' as long as you do not
modify `l' files.
----------------------------------------------------
checking for bison... no
checking for byacc... no
configure: WARNING:
-----------------------------------------------------
Nor `byacc' or `yacc' parsers had been used
for developing adesklets. If you encounter problems
recompiling a `y' file, please try `bison' instead.
You can get it from any GNU archive site. You will
not need `bison' as long as you do not modify
`y' files.
-----------------------------------------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path
benjamin@BG-notebook:~/adesklets/adesklets-0.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
```



Sorry just replying now. You need the latest Python-dev package,  an user had the same issue as you in  the folowing thread:

> 
[http://www.ubuntuforums.org/showthread.php?t=206033](http://www.ubuntuforums.org/showthread.php?t=206033)


Try searching python in synaptic and check the pythonxx-dev (xx is the current version of python development package) for install

---

### Post by simanek79 on 2007-01-22
I tried

sudo apt-get install adesklets

adesklets_installer or adesklets -i

and I got

Traceback (most recent call last):
  File "/usr/bin/adesklets_installer", line 631, in ?
    if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'


do you know what to do with that?

THX

---

### Post by hey560 on 2007-01-27
******@a64:~$ adesklets -i
Traceback (most recent call last):
  File "/usr/bin/adesklets_installer", line 631, in ?
    if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'

I get the same issue, has a bug report been filed for this?

---

### Post by SethP on 2007-02-01
[QUOTE="adesklets error"]
Traceback (most recent call last):
  File "/usr/bin/adesklets_installer", line 631, in ?
    if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'
[/QUOTE]

To fix the above error, just install the python-tk package. The easiest way to do this is to run the following commands from a terminal:

> 
sudo apt-get update
sudo apt-get install python-tk


---

### Post by Kevf on 2007-02-14
I can't configure weather 0.4
How come? :confused:

---

### Post by racoq on 2007-02-14
> **Kevf said:**
> I can't configure weather 0.4
How come? :confused:

Got to the directory were you have installed the weather desklet and then for configuring the desklet do:

> 
nano config.txt


---

### Post by zzzname on 2007-02-17
Does anybody have a desknote desklet? The website which usually hosts it seems to be down so if anybody can share it with me that would be splendid.

---

### Post by LucasLinard on 2007-03-04
Hi,
I installed adesklests via pat-get, I tried building it from source, but every time I try to install some desklet i get this error:
./photo.py
> 
.....

b7b2b0Traceback (most recent call last):
  File "./photo.py", line 6, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb796bdcc>> ignored

Also, if I try to install a desklet with adesklets_installer i get this output after selecting the desklet to download:
> Verifying download integrity... OK
Opening the downloaded archive... 
!!! An error occured during the operation !!!
Traceback (most recent call last):
  File "/usr/local/bin/adesklets_installer", line 223, in run
    getattr(self, '_'+op)(**kw)
  File "/usr/local/bin/adesklets_installer", line 244, in _install
    self.desklets.install(desklet)  #    refresh of desklets states
  File "/usr/local/bin/adesklets_installer", line 150, in install
    tar = tarfile.open(mode='r|bz2', fileobj=f)
  File "tarfile.py", line 1168, in open
    _Stream(name, filemode, comptype, fileobj, bufsize))
  File "tarfile.py", line 1047, in __init__
    self.name = os.path.abspath(name)
  File "posixpath.py", line 402, in abspath
    if not isabs(path):
  File "posixpath.py", line 49, in isabs
    return s.startswith('/')
AttributeError: 'NoneType' object has no attribute 'startswith'

can anyone help?

---

### Post by olskar on 2007-03-05
> askar@barbara:~/SystemMonitor-0.1.3$ adesklets -i
Traceback (most recent call last):
  File "/usr/bin/adesklets_installer", line 631, in ?
    if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'


help?

---

### Post by racoq on 2007-03-05
> **olskar said:**
> 
Quote:
askar@barbara:~/SystemMonitor-0.1.3$ adesklets -i
Traceback (most recent call last):
File "/usr/bin/adesklets_installer", line 631, in ?
if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'

help?



Looks like u have tried to install a desklet with the built in user interface. In some ocasions that can fail (if u dont have some of the prerequisites installed). Try the manual method i referrer in my howtoguide (manually download the desklets u want to use). If still u get an error post here the error.

---

### Post by unregistr3d on 2007-03-17
Hi,
i have Feisty and tried to compile and install adesklets, but when i trie to install some desklet: 

```
unregistr3d@ubuntu-laptop1:~/.desklets/anetmon-0.1.0$ ./anetmon.py
Traceback (most recent call last):
  File "./anetmon.py", line 38, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

```
please help

---

### Post by racoq on 2007-03-18
> **unregistr3d said:**
> Hi,
i have Feisty and tried to compile and install adesklets, but when i trie to install some desklet: 

```
unregistr3d@ubuntu-laptop1:~/.desklets/anetmon-0.1.0$ ./anetmon.py
Traceback (most recent call last):
  File "./anetmon.py", line 38, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

```
please help
That looks like there are missing some pre requisites, did u read the README file on that desklet to see which packages you must have installed for it to work with adesklets?

If everything seems ok, see if you skiped any of the packages needed for adesklet to run. If u cant manage  to get it working use the latest version from the repository, it worked fine on my xubuntu feisty.

---

### Post by olavjunior on 2007-03-20
I'm using gnome and compiz. 

I have trouble running adesklets automatic at startup. The weather desklet starts, but it's not transperrant. When I right-click and chose restart, it just dissaperes. But if I call it with alt+f2 and adesklets --nautilus, it comes with a messy background, and I then have to click restart to get it showing up properly (usually anyway..)

Any ideas?

---

### Post by yabbadabbadont on 2007-03-20
> **olavjunior said:**
> Any ideas?

Don't run compiz or beryl...  ;)

Or switch to screenlets (or whatever they are called).  There is a big thread about them and they apparently **require** real transparency in order to work correctly.

---

### Post by racoq on 2007-03-20
> **yabbadabbadont said:**
> Don't run compiz or beryl...  ;)

Or switch to screenlets (or whatever they are called).  There is a big thread about them and they apparently **require** real transparency in order to work correctly.

I don't know about Compiz, but the screenshot i've uploaded to this guide, was taken from my computer, which is running beryl.

I've had problems with transparency when i've add my previous graphic card, an S3 Savage card, which have limited capabilities (running XFCE default composite manager), since i've acquired a Geforce 4 Ti4200 with 64 MB, and installed beryl, adesklets run just fine. 

I guess the problem must be the graphic card you are using. 
Which one are you using? What drivers are you running for it?

And screenlets IMO have too few "screenlets" (don't have weather forecast, and other important desklets as adesklet have)

---

### Post by olavjunior on 2007-03-20
> **racoq said:**
> 

I guess the problem must be the graphic card you are using. 
Which one are you using? What drivers are you running for it?



I guess it's my graphics card then. I have a geforce go7200, and I don't have any proper drivers for them. I use the nvidia drivers, but my card isn't really supported. That's why I had to leave beryl. But compiz is working flawlessly though! :)

I guess it just won't be any adesklets for me this time then :(

---

### Post by racoq on 2007-03-20
> **olavjunior said:**
> I guess it's my graphics card then. I have a geforce go7200, and I don't have any proper drivers for them. I use the nvidia drivers, but my card isn't really supported. That's why I had to leave beryl. But compiz is working flawlessly though! :)

I guess it just won't be any adesklets for me this time then :(

What nvidia drivers are u using, the open source ones, or the proprietary from nvidia? If its a matter of drivers, u can test each other, to see if u can work, with one of them both on beryl / compiz, and adesklets

---

### Post by olavjunior on 2007-03-28
> **racoq said:**
> What nvidia drivers are u using, the open source ones, or the proprietary from nvidia? If its a matter of drivers, u can test each other, to see if u can work, with one of them both on beryl / compiz, and adesklets

I guess I'm using the proprietary from nvidia. I'm satisfied with getting compiz to run. I remember it was hard to get it to work, so I don't think I'll start messing with the graphics-settings again. Not until I install feisty fawn anyway... :)

---

### Post by sagara on 2007-03-29
racoq thanks for the guide, after a little messing around I got it to work : )

I need to ask did you ever install the **SystemMonitor** desklet?
Did you have any problems with its transparency?

Some desklets on the first time they load have their background messed up.  I have to reload them and/or move them around to get this fixed.  Did you happen to also experience this?

---

### Post by racoq on 2007-03-29
> **sagara said:**
> racoq thanks for the guide, after a little messing around I got it to work : )

I need to ask did you ever install the **SystemMonitor** desklet?
Did you have any problems with its transparency?

Some desklets on the first time they load come have their background messed up.  I have to reload them and/or move them around to get this fixed.  Did you happen to also experience this?


Apparently users of beryl, or compiz are experiencing these kind of problems. I don't have yet a solution for that,. Are you using one of this composites for rendering?  As it is showed on  the screenshot attached to my guide, i have systemmonitor configured, with a certain level of transparency. And i don' have that kind of problems. I will post here a solution for these transparency problems once i find one.

---

### Post by racoq on 2007-03-29
I have messed with some of the beryl options, and i have experienced the same problems that many beryl  users have been experiencing. So that motivated me to find a workaround. I have already edited my guide, so please follow the instructions and report to me if that worked. That workaround was tested on my Geforce TI 4200, using aiglx and nvidia proprietary drivers.

---

### Post by sagara on 2007-03-29
racoq you were right! once beryl loads, the transparencies for the different adesklets get messed up.  

I started a session, manually loaded adesklets followed by beryl and it worked flawlessly.  However you can't mess around and start moving the desklets cause the transperencies get messed up.

One thing though, I copied your script and placed it for autostartup on each session.  For some reason adesklets loads or tries to load but no desklets  remain.  Beryl does load afterwards with no problems.  Any ideas why?

Once again **you rock! thanks a lot for the quick hack!!**

---

### Post by Mateo on 2007-03-30
anyone know how often the weather desklet refreshes?

---

### Post by racoq on 2007-03-30
> **sagara said:**
>  However you can't mess around and start moving the desklets cause the transperencies get messed up.

That's why i called it a woraround it adresses the problem at startup., but not when u move the desklets. However i think that is not the problem, because i only moved the desklets for my desired position only once. For me and the majority of people work, because we don't move the desklets very often.

> 
One thing though, I copied your script and placed it for autostartup on each session.  For some reason adesklets loads or tries to load but no desklets  remain.  Beryl does load afterwards with no problems.  Any ideas why?

don't really now... Maybe its a misconfigured desklet?

try typing, adesklets --"your DE" at console and post here if it shows a error

---

### Post by yabbadabbadont on 2007-03-30
> **Mateo said:**
> anyone know how often the weather desklet refreshes?

As often as you configure it to...  but not more frequently than every 5 minutes.  I think it defaults to either 15 or 30 minutes.  Check your config file in the directory with the desklet.  It is specified in seconds by the way.

---

### Post by Mateo on 2007-03-31
Has anyone else had the problem of when you start your computer, adesklets loads up and then the  wallpaper loads on top of it?  so then you have to restart it.  how do you make it to load after the wallpaper, so that it is on top?

---

### Post by sagara on 2007-03-31
I had this issue too.  The solution was racoq's script only with a little modification.

See the first page of this thread for the instructions.  What I added to his script was a small sleep time when the script starts and adesklets gets loaded.  This way, the background would load first and adesklets would follow up.

My script:
```

#!/bin/sh
**sleep 3**                            # this sleep ensures the desktop loads first
adesklets --nautilus
sleep 3
beryl-manager
```

Remember to place the file in your startup session: System>Preferences>Sessions>Startup Programs

---

### Post by Mateo on 2007-03-31
is that 3 seconds?

---

### Post by yabbadabbadont on 2007-03-31
> **Mateo said:**
> is that 3 seconds?

Yes.

---

### Post by Posh on 2007-04-20
> **unregistr3d said:**
> Hi,
i have Feisty and tried to compile and install adesklets, but when i trie to install some desklet: 

```
unregistr3d@ubuntu-laptop1:~/.desklets/anetmon-0.1.0$ ./anetmon.py
Traceback (most recent call last):
  File "./anetmon.py", line 38, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

```
please help

I am having this same problem.  I just upgraded to Feisty from Edgy and my adesklets weren't coming up.  So I deleted my .adesklets file and tried to register my weatherforecast and get the same error as above.

If I change my default python to 2.4 it works fine but with 2.5 i get that error.  I have tried to remove and reinstall adesklets but it still persists.  I would just use 2.4 but beryl-settings wont work with 2.4.

Thanks for your help.

Edit: Forgot to mention i am running amd64 ubuntu.

---

### Post by racoq on 2007-04-23
> **Posh said:**
> I am having this same problem.  I just upgraded to Feisty from Edgy and my adesklets weren't coming up.  So I deleted my .adesklets file and tried to register my weatherforecast and get the same error as above.

If I change my default python to 2.4 it works fine but with 2.5 i get that error.  I have tried to remove and reinstall adesklets but it still persists.  I would just use 2.4 but beryl-settings wont work with 2.4.

Thanks for your help.

Edit: Forgot to mention i am running amd64 ubuntu.



Hello Posh

Well the anetmon desklet is kind of "messy" to make it to work, you have to install some pre-requisites, see the README from the desklet, if you want a quick workaround,  oyvindaa placed a suggestion, that worked well for me and other users. You can try that if that suites you well.

See the following link:

[http://ubuntuforums.org/showthread.php?t=183709&page=5]("http://ubuntuforums.org/showthread.php?t=183709&page=5")

---

### Post by Posh on 2007-04-23
Thanks for replying.. i have the prereqs installed.  Although I guess I should have stated I am actually trying to get weatherforecast to work... not anetmon.  But i get the same error just substitute weatherforecast for anetmon.  It's strange that it works in python2.4 and not python2.5.  I wonder if its something with the amd64 deb package that is broken.  If anyone has any suggestions I would greatly appreciate it.

---

### Post by racoq on 2007-04-23
> **Posh said:**
> Thanks for replying.. i have the prereqs installed.  Although I guess I should have stated I am actually trying to get weatherforecast to work... not anetmon.  But i get the same error just substitute weatherforecast for anetmon.  It's strange that it works in python2.4 and not python2.5.  I wonder if its something with the amd64 deb package that is broken.  If anyone has any suggestions I would greatly appreciate it.

Post here your error log, from weatherforecast

---

### Post by Posh on 2007-04-23
```
posh@posh:~/weatherforecast-0.2.0$ ./weatherforecast.py
Traceback (most recent call last):
  File "./weatherforecast.py", line 41, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

```

if there is something else you would like me to post just let me know (and where to locate it).

Thanks for the help.

---

### Post by coldstatue on 2007-05-01
same problem here - 
File "/usr/local/bin/adesklets_installer", line 223, in run 

I got adesklets running in my session (finally) but when I download a desklet manually and launch. It runs terminal, asks to be registered, runs some code, and the terminal disappears - with no desklet runnign. When I run the graphical installer, I get the above error.

---

### Post by coldstatue on 2007-05-01
I also get this when running weatherforecast.py
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7c6d72c>> ignored

---

### Post by coldstatue on 2007-05-01
when I use the graphical installer for weather forecast, I get this too

  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7c6d72c>> ignored

---

### Post by yabbadabbadont on 2007-05-01
Apparently, adesklets is not compatible with version 2.5 of python.  Go the adesklets forums and post the errors.  Perhaps the desklet authors will update them.

---

### Post by racoq on 2007-05-03
> **yabbadabbadont said:**
> Apparently, adesklets is not compatible with version 2.5 of python.  Go the adesklets forums and post the errors.  Perhaps the desklet authors will update them.

Strange... i'm not getting this error, as i've updated from Xubuntu Edgy to Feisty (so i'm know using python 2.5)... I'll try to look into this to see if there is a possible solution / workaround.

---

### Post by Posh on 2007-05-04
There was a problem with adesklets and Feisty amd64 only I believe.  It was actually a code bug in adesklets that is now fixed.   I worked with the developer for several days figuring this out.  It would be nice if the adesklets package got updated but my guess that will take a while.

---

### Post by racoq on 2007-05-05
> **Posh said:**
> There was a problem with adesklets and Feisty amd64 only I believe.  It was actually a code bug in adesklets that is now fixed.   I worked with the developer for several days figuring this out.  It would be nice if the adesklets package got updated but my guess that will take a while.

Posh, thanks for reporting the bug here in this thread, letting the users of adesklets know whats happening. please take a few minutes of your time, to submit a description of the bug, to launchpad in order for the MOTU responsible for the maintenance of the package to upgrade the package in the repositories.

---

### Post by Posh on 2007-05-06
> **racoq said:**
> Posh, thanks for reporting the bug here in this thread, letting the users of adesklets know whats happening. please take a few minutes of your time, to submit a description of the bug, to launchpad in order for the MOTU responsible for the maintenance of the package to upgrade the package in the repositories.

Already done. [https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942](https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942)

---

### Post by racoq on 2007-05-06
> **Posh said:**
> Already done. [https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942](https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942)

Subscribed the MOTU team on the bug report, hopping, for the fixed upgrade of the package, is uploaded as soon as possible ;). 

Thanks again :)

---

### Post by Forlong on 2007-06-07
Does anybody know how to get the liquid icons working with weatherforecast?
When I change ```
'theme': 'wetaher.com'
``` to ```
'theme': 'liquid'
``` it just crashes ('um' works, though) :-|

Also... is there a way to move it a little over the right side of the screen? There's too much space if you put it on the far right.

---

### Post by alek66 on 2007-06-08
I get a 
```
configure: error: Could not find the readline library
```
how can I fix this?

---

### Post by racoq on 2007-06-08
> **Forlong said:**
> Does anybody know how to get the liquid icons working with weatherforecast?
When I change ```
'theme': 'wetaher.com'
``` to ```
'theme': 'liquid'
``` it just crashes ('um' works, though) :-|


this is my config.txt of weatherforecast

id0 = {'bg': False,
 'cc_color': 'AAAAAAFF',
 'delay': 1800,
 'forecast_color': 'AAAAAAFF',
 'location': 'POXX0035',
 'location_color': 'AAAAAAFF',
 'location_font_size': 10,
 'metric': True,
 'show_big_icon': True,
 'show_current_conditions': True,
 'show_forecast': True,
 'small_font_size': 10,
 'theme': 'liquid',
 'time_format': 12}

it is working good with liquid maybe the liquid icons (icons/liquid directory) got corrupted, try to install the desklet again.

> **Forlong said:**
> 
Also... is there a way to move it a little over the right side of the screen? There's too much space if you put it on the far right.

Right click over your desklet when its drawn on screen and choose > move.
adesklets will remember the position you've left the desklet ;)

Enjoy

---

### Post by yabbadabbadont on 2007-06-08
You may have to Control-Right-click depending upon which options were used when adesklets was built.

---

### Post by NTolerance on 2007-06-11
Does this not work when Desktop Effects are enabled?  I can run the weather widget but its display is corrupted and the only thing I can do is kill it.

Edit:  I now see the note for Beryl users.  Anyone know of a work-around for Compiz users?

---

### Post by Tamacracker on 2007-06-19
When I test the System Monitor I get this error:

```
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./SystemMonitor.py", line 1107, in <module>
    EventHandler(dirname(__file__)).pause()
  File "./SystemMonitor.py", line 974, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.5/site-packages/adesklets/events_handler.py", line 157, in __init__
    self.ready()
  File "./SystemMonitor.py", line 989, in ready
    join(self.basedir,'config.txt'))
  File "./SystemMonitor.py", line 265, in __init__
    adesklets.ConfigFile.__init__(self, identifier, filename)
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 162, in __init__
    self._load_and_save()
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 205, in _load_and_save
    all= ConfigImport.load(buf[:])
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 42, in __call__
    self.start_walk(compiler.parse(buf).getChildNodes()[0])))
  File "compiler/transformer.py", line 52, in parse
  File "compiler/transformer.py", line 129, in parsesuite
  File "<string>", line 52
    {"meters" : [
    ^
IndentationError: unexpected indent
illriginal@illriginal:~/SystemMonitor-0.1.3$ 

```

---

### Post by Tamacracker on 2007-06-19
Bump!!! 

I don't understand a darn thing what these error messages are giving me. It's all jibberish.

---

### Post by Irti on 2007-06-19
am getting this error wen i try to run the desklet......can anyone please help me??????



irti@irti-Linux:~/EYE CANDY/adesklet/adeskclock-0.1.0$ ./adeskclock.py --nautilusTraceback (most recent call last):
  File "./adeskclock.py", line 57, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

---

### Post by racoq on 2007-06-19
> **Tamacracker said:**
> When I test the System Monitor I get this error:

```
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./SystemMonitor.py", line 1107, in <module>
    EventHandler(dirname(__file__)).pause()
  File "./SystemMonitor.py", line 974, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.5/site-packages/adesklets/events_handler.py", line 157, in __init__
    self.ready()
  File "./SystemMonitor.py", line 989, in ready
    join(self.basedir,'config.txt'))
  File "./SystemMonitor.py", line 265, in __init__
    adesklets.ConfigFile.__init__(self, identifier, filename)
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 162, in __init__
    self._load_and_save()
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 205, in _load_and_save
    all= ConfigImport.load(buf[:])
  File "/usr/lib/python2.5/site-packages/adesklets/configfile.py", line 42, in __call__
    self.start_walk(compiler.parse(buf).getChildNodes()[0])))
  File "compiler/transformer.py", line 52, in parse
  File "compiler/transformer.py", line 129, in parsesuite
  File "<string>", line 52
    {"meters" : [
    ^
IndentationError: unexpected indent
illriginal@illriginal:~/SystemMonitor-0.1.3$ 

```


I attach my working copy of config.txt to the SystemMonitor Desklet, unfortunately i didn't managed to get the meter measure working, butt all other stats are working great

---

### Post by Tamacracker on 2007-06-19
Well I finally got it to work, but I honestly don't know how. Thanks for your config file, hopefully someone will be lucky enough to get it to work without any trouble :D

---

### Post by Apewall on 2007-08-03
> **Irti said:**
> am getting this error wen i try to run the desklet......can anyone please help me??????



irti@irti-Linux:~/EYE CANDY/adesklet/adeskclock-0.1.0$ ./adeskclock.py --nautilusTraceback (most recent call last):
  File "./adeskclock.py", line 57, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

I am getting the same error when trying to install from a desklet script.

The auto installer (adesklets -i) returns with ```
&#9474;Retrieving data online... OK                                                  &#9474;
&#9474;Checking locally installed desklets... OK                                     &#9474;
&#9474;Downloading Calendar desklet...                                               &#9474;
&#9474;!!! An error occured during the operation !!!                                 &#9474;
&#9474;Traceback (most recent call last):                                            &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 223, in run                       &#9474;
&#9474;    getattr(self, '_'+op)(**kw)                                               &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 244, in _install
```

---

### Post by mkquist on 2007-08-04
Hey just a quick thank you racoq for this tut.  Didn't even know about adesklets.  Running Xubuntu on an older 500mz P2 and its totally useable.  Desklets adds a nice touch to my desktop. :)

---

### Post by racoq on 2007-08-06
> **Apewall said:**
> I am getting the same error when trying to install from a desklet script.

The auto installer (adesklets -i) returns with ```
&#9474;Retrieving data online... OK                                                  &#9474;
&#9474;Checking locally installed desklets... OK                                     &#9474;
&#9474;Downloading Calendar desklet...                                               &#9474;
&#9474;!!! An error occured during the operation !!!                                 &#9474;
&#9474;Traceback (most recent call last):                                            &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 223, in run                       &#9474;
&#9474;    getattr(self, '_'+op)(**kw)                                               &#9474;
&#9474;  File "/usr/bin/adesklets_installer", line 244, in _install
```

thats an odd error. have your checked the README file of the desklet, and you can say that you have installed all the requirements/dependencies listed there?


> **mkquist said:**
> Hey just a quick thank you racoq for this tut.  Didn't even know about adesklets.  Running Xubuntu on an older 500mz P2 and its totally useable.  Desklets adds a nice touch to my desktop. :)

It was my pleasure ;)

---

### Post by Jhet on 2007-08-08
I'm not sure if this is the right place for this, but maybe you can help me understand this error.  I've been trying to get the newsfeed desklet to run but i get this when testing
```
<dir where it is>  ./newsfeed.py --nautilus
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./newsfeed.py", line 419, in <module>
    Events(dirname(__file__)).pause()
  File "./newsfeed.py", line 109, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.5/site-packages/adesklets/events_handler.py", line 158, in __init__
    self._alarm()
  File "/usr/lib/python2.5/site-packages/adesklets/events_handler.py", line 296, in _alarm
    timeout=self.alarm()
  File "./newsfeed.py", line 157, in alarm
    self._display()
  File "./newsfeed.py", line 180, in _display
    self.draw_info()
  File "./newsfeed.py", line 234, in draw_info
    if (self.draw_news_header(item)==0):
  File "./newsfeed.py", line 266, in draw_news_header
    feed_title=str(self.feed['items'][item]['title'])
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2019' in position 5: ordinal not in range(128)

```
when just running the desklet it pops up briefly then terminates.  I had a quick look on the adesklet forum and the problem was mentioned for the desklet, but the only possible thing was down to the url for the feed.  Here is the config file for it:
```
# -*- coding: ASCII -*-
#
#This is newsfeed.py desklet configuration file; for each desklet,
#you only have to write down the minimal delay between updates
#(in seconds: less than 300 will be ignored), the URL of the feed
#and the size of the desklet
#Details:
#       sizeX,sizeY: width and height
#       head_font, head_font_height: font for news title
#       item_font, item_font_height: font for news details
#       url: rss/atom newsfeed url
#       line_spacing: pixels between two lines
#       borderX, borderY: area reserved to borders
#       interactive: if True, enables highlighting of news details and calling 
#               selected browser
#       browser: browser to call for viewing selected news
#
id0 = {'borderX': 7,
 'borderY': 7,
 'browser': 'firefox',
 'delay': 600,
 'head_font': 'VeraBd',
 'head_font_color': 'ffff00',
 'head_font_height': 8,
 'interactive': False,
 'item_font': 'Vera',
 'item_font_color': '02c601',
 'item_font_height': 8,
 'line_spacing': 5,
 'managed': False,
 'selected_font_color': 'ffffff',
 'sizeX': 400,
 'sizeY': 600,
 'title_font': 'VeraBd',
 'title_font_color': 'ffe600',
 'title_font_height': 12,
 'url': 'http://feeds.feedburner.com/gizmodo/Uk.rss'}

```
 Any ideas?

---

### Post by Yes on 2007-08-29
I have a quick question:  I downloaded the SystemMoniter desklet, and I was wondering if I could just comment out all the things like Network Moniter that I don't want in the confg.txt file.  Or would that screw everything up?

Thanks, and great guide!

---

### Post by katxor on 2007-11-02
just an odd question, i just saw this thread and finally got it working,,, the yab bar looks really good.

just one question though, when i installed the yab bar, my weatherforecast disappeared. can i only run 1 applet at the time? if not then what do i configure so all the applets start?

looking forward to an answer... thanks :)

---

### Post by katxor on 2007-11-02
im an idiot... got it to work... :)

---

### Post by Posh on 2007-11-26
> **Irti said:**
> am getting this error wen i try to run the desklet......can anyone please help me??????



irti@irti-Linux:~/EYE CANDY/adesklet/adeskclock-0.1.0$ ./adeskclock.py --nautilusTraceback (most recent call last):
  File "./adeskclock.py", line 57, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

Ahhhhhh... I just upgraded to Gutsy and we are now back to a broken package for the amd64 build.  This was the same in Feisty and I worked with the developer to get this fixed and it has been fixed for months now.  We just need a new package made with the new source.  This seriously needs fixed as it is completely broken as is.  

Here's the bug I posted months ago. [https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942](https://bugs.launchpad.net/ubuntu/+source/adesklets/+bug/109942)

Anybody know how to get this elevated a bit.

---

### Post by Posh on 2007-11-27
Well here is a temporary fix that works for me until they fix the package.

[SIZE="4"]THIS IS FOR AMD64 Feisty or Gutsy ONLY[/SIZE]

Replace posix_signal.so from /usr/lib/python2.5/site-packages with the one attached in this post.  You may want to backup posix_signal.so first if you like.

---

### Post by empthollow on 2008-01-04
i am a fan of adesklets and i have successfully got everything up and running on my desktop.  My situation is i'm building a live cd which i probably will turn into a linux distro based on ubuntu.  i am using the fluxbox desktop and want to include adesklets as part of the stock desktop but all of the config files are in my home directory.  This poses a problem as the user directory is created at boot time.  Is there any way to configure adesklets globaly in /usr/share or something like that?

---

### Post by bavardage on 2008-01-05
Time for some selfish advertising.
I have created two desktops, one of which is currently on the adesklets site (although I have submitted an update which is yet to appear)

I give you:
**aanalogue**
Click to download: [aanalogue-0.0.1]("http://ben.jeffers727.com/adesklets/aanalogue-0.1.0.tbz2")
[[IMG]http://ben.jeffers727.com/adesklets/aanalogue_thumb.jpg[/IMG]]("http://ben.jeffers727.com/adesklets/aanalogue_screen.jpg")
and
**anote**
Click to download: [anote-0.0.0]("http://ben.jeffers727.com/adesklets/anote-0.0.0.tbz2")
[[IMG]http://ben.jeffers727.com/adesklets/anote_thumb.jpg[/IMG]]("http://ben.jeffers727.com/adesklets/anote_screen.jpg")

(Click on images for larger and click on names to download the desklet)

I have also made a desk-calculator, but I haven't packaged it up yet, so watch this space?

Hope they may be of use to somebody.

---

### Post by racoq on 2008-01-15
Thanks for contributing to adesklets by making those desklets, 

it would be good that your example, is taken by many skilled coders on these forums and further support and help improve adesklets, who IMHO doesn't stay behind other alternatives like gdesklets or superkaramba.

I'm looking forward to see your other work in the future on adesklets and specially some updates on this thread,

Best Regards

---

### Post by Shaggydabbydo on 2008-01-17
I have a problem trying to get desklets working on startup.

(I'm a newby to Linux, so bare with me - I'm on Gutsy/Gnome).

I can get the desklet weatherforecast-0.2.0 up when I open a Terminal and type "*adesklets --nautilus*", but only after I have typed "*su*" & "*<su's password>*"

I had a look again at your documentation and I think I have found the problem.  I could not get the command "*adesklets -i*" to work so went straight to the manual option, "*cd weatherforecast-0.2.0*"/"*./weatherforecast.py*".  

I guess this means that this file mentioned here did not get created: "*This will create the file .adesklets in your home directory and it will fill it with instructions, for running weatherforecast each time adesklets is executed*"

I've gone to System => Sessions and added "adesklets --nautilus" as a new line in Startup Programs.

Any ideas what to do to get it working on startup

Regs, Shaggy

---

### Post by empthollow on 2008-01-17
go to  the directory 
```
cd weatherforecast-0.2.0
```
then type
```
./weatherforecast.py
```
it should ask weather you would like to register or test, type
```
r
```
and it will add itself to your .adesklets file

if it is not asking you to register or test you may want to re-download and extract it.  you shouldn't need root prvliges for adesklets.

---

### Post by Mark76 on 2008-01-22
I've tried to get system monitor working under Xubuntu 7.10 on AMD64 and I've had no luck whatsoever.

Everytime I run the py script in the terminal some text rushes past and then it just seems to crash

---

### Post by macozz on 2008-01-23
I have adesklets installed and working, but there is an strange behavior with them. The desklets starts just after X load, but when the Gnome desktop starts they disappear. I have to run them again manually. I have them in my sessions, so it is supposed to run OK, but not. I tried to  change the sequence of loading, to start after Nautilus, but does not work.
Any clue about why this is happens and how can I correct it?
Thanks!

---

### Post by empthollow on 2008-01-24
if you use gnome you have to start it like this
```
adesklets --nautilus
```
this will tell adesklets how to display over the desktop.

---

### Post by macozz on 2008-01-25
This is the way I have it in my Sessions section, but I get the problem described any way. They are loaded during the initial graphical desktop load and when Nautilus loads the desklets disappear.

---

### Post by macozz on 2008-02-18
No other user is experiencing the same problem? I still have it. adesklets are killed when the desktop wallpaper and icons load. It appears during load but crash after that. There is no way to start the adesklets AFTER the desktop? It seems to me that what kill the application is Nautilus starting.
Thanks

---

### Post by stedevil on 2008-03-03
> **macozz said:**
> There is no way to start the adesklets AFTER the desktop? It seems to me that what kill the application is Nautilus starting.
Thanks



1) Start adesklets --nautilus
2) System > Preferences > Sessions > Current Session
3) Select the entry for adesklets --nautilus and increase the order number (to eg 99)
4) Session Options > [Remember currently running applications]
5) Close

With some luck things should work fine next time you restart (though sometimes 1 or more desklets can still randomly be missing, I guess it's lightweightness makes it starts too quick).


I have a problem of my own though, on my laptop I have powertop installed to try to increase battery time and it turns out that the #1 offender by far (~80%...) for waking my CPU out of sleep is adesklets (~300/s). Since I only run 4 weather reports (updated about every 30min) and 3 calendars (month + +/-1) I can't imagine any reason adesklets would have to process information 300 times per second waking up the CPU in the process...  

Anybody knows how to fix this in the code for adesklets? It would really suck to have to remove it just to keep the battery lasting a bit longer.

---

### Post by stedevil on 2008-03-05
> **stedevil said:**
> 1) Start adesklets --nautilus
2) System > Preferences > Sessions > Current Session
3) Select the entry for adesklets --nautilus and increase the order number (to eg 99)
4) Session Options > [Remember currently running applications]
5) Close


Another, probably better way to do this is to eg start it as
adesklets --nautilus -d 5
in the session manager (d 5 makes it wait 5s before actually starting the desklets, which should be enough to not have nautilus overwrite them).

> waking my CPU out of sleep is adesklets 

Answering my own question, if you download and compile from source it is possible to send instructions to the ./configure script with a new value for   
--enable-x-polling-frequency=FREQ

                          FREQ (in hertz) for polling the X server
                          for events. Lower values leads to less responsive,
                          but less CPU hungry desklets default=50

---

### Post by macozz on 2008-03-06
Thanks you very much!
The suggestion of increase the order number worked for me. I did not try yet the other way, since the frst one is working. Does it have any advantage?
Thanks again!

---

### Post by stedevil on 2008-03-06
> **macozz said:**
> Thanks you very much!
The suggestion of increase the order number worked for me. I did not try yet the other way, since the frst one is working. Does it have any advantage?


I assume on slow systems it's might not be enough to edit the order of when a software is started because even if adesklet is started later, it's so small and quick that it might still finish before Nautilus does (thus causing Nautilus to still overdraw the desklets).

Putting in a relatively big delay should completely remove that risk. But if it works without it you wont see any difference. :)

---

### Post by racoq on 2008-06-09
A recent update on the Weather.com that WeatherForecast Desklet relies on, have broken WeatherForecast behaviour.

The error displayed on the console is something like this:

```

File "./weatherforecast.py", line 143, in alarm
    self._display()
  File "./weatherforecast.py", line 206, in _display
    location=str(self.w.loc.dnam).split(',')[0]
  File "/someplace/weather/xmltramp.py", line 113, in __getattr__
    raise AttributeError, 'No child element named \''+n+"'"
AttributeError: No child element named 'loc'

```


I have detected the source of the problem, at the line 184 of the WeatherForecast.py python script, i have replaced:

```

             self.w = xmltramp.load('http://xoap.weather.com/weather/local/%s?prod=xoap&par=1003832479&key=bb12936706a2d601&cc=*&dayf=3&unit=%s' % (str(self.config['location']), self.unit_sys))

```

with:

```

             self.w = xmltramp.load('http://xoap.weather.com/weather/local/%s?cc=*&dayf=3&unit=%s' % (str(self.config['location']), self.unit_sys))

```

Weather.com made some kind of update to the way one must get the xml definition of the data for forecast and eliminated some parameters. The previous behaviour was now incompatible and it was messing up weatherforecast.py behaviour, and the author of this desklet didn't updated the desklet.

For your convinience i attach the correct weatherforecast.py at this reply. Please put this file in your weatherforecast folder in the desklet folder. I have mine for instance at /home/myusername/.desklets/weatherforecast-0.2.0 . Hope this helps

---

### Post by OldGaf on 2008-06-23
I get the same errors when trying to install desklets:

SystemMonitor: (after installing libstatgrab 0.15-1 & pystatgrab  0.4-1)

> Traceback (most recent call last):
  File "./SystemMonitor.py", line 42, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

and aanalogue:

> Traceback (most recent call last):
  File "./aanalogue-0.1.0.py", line 36, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 30, in <mo                                                                      dule>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.5/site-packages/adesklets/initializer.py", line 13, in                                                                       <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.5/site-packages/adesklets/children_handler.py", line 5,                                                                       in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 12,                                                                       in <module>
    class Signal_handler:
  File "/usr/lib/python2.5/site-packages/adesklets/signal_handler.py", line 20,                                                                       in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'

Running Kubuntu 8.04 64bit

---

### Post by Hooya on 2008-06-24
> **OldGaf said:**
> I get the same errors when trying to install desklets:

SystemMonitor: (after installing libstatgrab 0.15-1 & pystatgrab  0.4-1)



and aanalogue:



Running Kubuntu 8.04 64bit

Ditto for everything above, but running Fluxbox at the moment (over Ubuntu 8.06 64bit)  No desklets install, all give the same python error.

---

### Post by OldGaf on 2008-07-03
> **Hooya said:**
> Ditto for everything above, but running Fluxbox at the moment (over Ubuntu 8.06 64bit)  No desklets install, all give the same python error.


Gave up for now... got conky woring for now.

---

### Post by davidryder on 2008-09-23
I HATE to hijack the thread but I've been screwing around with this (adesklets) for hours and can't it to work very well. I finally found another program called screenlets available in the Synaptic Package manager and I must say - it is THE bomb. 

```
sudo apt-get install screenlets
screenlets-manager
```

Image: [http://www.phpstory.net/graphics/ss_Sep_23_2008_1312.png](http://www.phpstory.net/graphics/ss_Sep_23_2008_1312.png)

:D

---

### Post by gp_jaunty on 2009-06-14
> **Posh said:**
> Well here is a temporary fix that works for me until they fix the package.

[SIZE=4]THIS IS FOR AMD64 Feisty or Gutsy ONLY[/SIZE]

Replace posix_signal.so from /usr/lib/python2.5/site-packages with the one attached in this post.  You may want to backup posix_signal.so first if you like.

Thanks!! this patch worked for me for jaunty...python2.6
how did u generate this patch??:o

..i tried to install adesklets by compiling from source ..but i got
[glibc detected *** adesklets: double free or corruption ] error

then i installed thru apt-get and replaced the posix_signal.so but this time i got 
[import posix_signal.so: unable to find Py_InitModule4] error

However ur file removed all the probs..:):)

---

### Post by Doctor Drive on 2009-11-09
when I try to launch any desklet I get same error

[email]doctor@Doctor:~/.deskle[/email]ts/yab$ python yab.py
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "yab.py", line 48, in <module>
    import adesklets
  File "/usr/local/lib/python2.6/dist-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x8ea69ec>> ignored

---

### Post by Doctor Drive on 2009-11-20
ok. I've fixed ^that^ by installing adesklets from synaptic.
Now there's no such errors.

But now another error appeared.
adesklets.error_handler.ADESKLETSError: adesklets command error - font 'Vera/8' could not be loaded

Something with Vera font. I've install msttcorefonts and. some european font package.
But the error still appeares.

---

### Post by Mark76 on 2009-11-20
Do they work on 64 bit systems yet?

---

### Post by Doctor Drive on 2009-11-20
ok now i'm done. 'Just needed to copy some fonts to /usr/share/fonts/TTF

---

### Post by epyonx1 on 2012-04-25
I believe I have found the problem:

Weather.com has changed its XML data from being freely available to being only available on a paid subscription basis.

Check it out:
[http://beta.weather.com/services/xmloap.html](http://beta.weather.com/services/xmloap.html)

---

