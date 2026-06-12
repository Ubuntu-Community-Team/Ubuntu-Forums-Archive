---
title: "Gnucash 2.0"
date: 2006-07-24
forum: Ubuntu Backports
---

### Post by byteshack on 2006-07-24
There are some "personal" packages for gnucash 2.0 out there, but there doesn't seem to be a more standard one.  Would it be possible to create one?

---

### Post by mlind on 2006-07-24
> **byteshack said:**
> There are some "personal" packages for gnucash 2.0 out there, but there doesn't seem to be a more standard one.  Would it be possible to create one?

You can build it from edgy's source repository. Insert new repository to /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

```

Then execute
```

sudo aptitude update
sudo apt-get build-dep gnucash
sudo apt-get source -b gnucash

```

Or use [pbuilder]("http://www.ubuntuforums.org/showthread.php?t=206382")/sbuild to build the package.

---

### Post by Garyu on 2006-07-25
hmm, that looked easy enough, but it didn't work for me:

```
dpkg-source: extracting gnucash in gnucash-2.0.0
dpkg-source: unpacking gnucash_2.0.0.orig.tar.gz
dpkg-source: applying ./gnucash_2.0.0-1ubuntu1.diff.gz
dpkg-buildpackage: source package is gnucash
dpkg-buildpackage: source version is 2.0.0-1ubuntu1
dpkg-buildpackage: source changed by Sebastian Dröge <slomo@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev libofx-dev (>= 1:0.8.0-8) guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libgtkhtml3.8-dev g-wrap
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Byggkommandot "cd gnucash-2.0.0 && dpkg-buildpackage -b -uc" misslyckades.
E: Barnprocessen misslyckades

```
Pardon my swedish. It says "build command "cd gnucash...&& dpkg-bu..." failed".
E: Child process failed.

---

### Post by JoWilly on 2006-07-25
> **Garyu said:**
> hmm, that looked easy enough, but it didn't work for me:

```
dpkg-source: extracting gnucash in gnucash-2.0.0
dpkg-source: unpacking gnucash_2.0.0.orig.tar.gz
dpkg-source: applying ./gnucash_2.0.0-1ubuntu1.diff.gz
dpkg-buildpackage: source package is gnucash
dpkg-buildpackage: source version is 2.0.0-1ubuntu1
dpkg-buildpackage: source changed by Sebastian Dröge <slomo@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev libofx-dev (>= 1:0.8.0-8) guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libgtkhtml3.8-dev g-wrap
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Byggkommandot "cd gnucash-2.0.0 && dpkg-buildpackage -b -uc" misslyckades.
E: Barnprocessen misslyckades

```
Pardon my swedish. It says "build command "cd gnucash...&& dpkg-bu..." failed".
E: Child process failed.



Just read what it says, you need to install these unmet dependencies :

Unmet build dependencies: libltdl3-dev libofx-dev (>= 1:0.8.0-8) guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libgtkhtml3.8-dev g-wrap

---

### Post by mlind on 2006-07-25
Yeah, install the missing packages
```

sudo aptitude install libltdl3-dev libofx-dev guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev libbonobo2-dev libgnomevfs2-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libgtkhtml3.8-dev g-wrap

```

I'm not sure how build-dep works, I never use it myself. Could be that it's checking build dependencies of old the gnucash package, not the new one.

---

### Post by Garyu on 2006-07-26
weird... when I ran 

sudo apt-get install libltdl3-dev libofx-dev guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev libbonobo2-dev libgnomevfs2-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libgtkhtml3.8-dev g-wrap

I got the error that packages could not be found. But with the aptitude command everything worked fine. What's up with that? I didn't even to a "sudo apt-get update" so that could not be the difference...

Anyways, I get complaints about "liblighthouseblue.so" when I start gnucash, but at least now it works. :D 

Thanks for the help.

---

### Post by mlind on 2006-07-26
> **Garyu said:**
> weird... when I ran 

sudo apt-get install libltdl3-dev libofx-dev guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev libbonobo2-dev libgnomevfs2-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libgtkhtml3.8-dev g-wrap

I got the error that packages could not be found. But with the aptitude command everything worked fine. What's up with that? I didn't even to a "sudo apt-get update" so that could not be the difference...

Anyways, I get complaints about "liblighthouseblue.so" when I start gnucash, but at least now it works. :D 

Thanks for the help.

Maybe apt-get was having a bad day, dunno. aptitude and apt-get are using same package lists, so same packages should be found by both apps.
gtk2-engines-lighthouseblue.so file is on gtk2-engines-lighthouseblue and gtk-engines-lighthouseblue packages. What theme are you using ?

---

### Post by mmcmonster on 2006-07-26
Actually, this seems to be a great one to get into backports.  It doesn't depend on a major library, and all the deps are in dapper already.

---

### Post by bhspencer on 2006-07-28
I have been trying to get gnucash 2.0 running on my ubuntu dapper install for a couple of weeks now. I followed your instruction and all seemed to be well, the dependencies downloaded and compliation went with out hitch however when I type gnucash at the shell i get

bash: gnucash: command not found

is their something else I must do to get things running?

---

### Post by mlind on 2006-07-28
> **bhspencer said:**
> I have been trying to get gnucash 2.0 running on my ubuntu dapper install for a couple of weeks now. I followed your instruction and all seemed to be well, the dependencies downloaded and compliation went with out hitch however when I type gnucash at the shell i get

bash: gnucash: command not found

is their something else I must do to get things running?

Those instructions will build the .deb package, but you still need to install it.

```

sudo dpkg -i *package*

```

---

### Post by snerge on 2006-08-01
thanks, very usefull

---

### Post by /dev/clast on 2006-08-06
even though people seem to get it to work here, i would welcome a backport.
the newest version (2.0.1) would be great to have for dapper :)

my dad really wants to try it and he needs an easy way to get it.

clast

---

### Post by kleeman on 2006-08-09
I built some debs for 2.0.1 from Debian unstable so they have dependency checking. They do not have online banking unfortunately.

[http://www.yourfilelink.com/get.php?fid=151771](http://www.yourfilelink.com/get.php?fid=151771)
[http://www.yourfilelink.com/get.php?fid=151772](http://www.yourfilelink.com/get.php?fid=151772)

remove the old gnucash debs (not the docs if you have 1.9) and install using


sudo dpkg -i gnucash-common_2.0.1-1_all.deb gnucash_2.0.1-1_i386.deb

---

### Post by StratosL on 2006-08-13
I installed your debs, good work btw. gnucash 2.0.x should be in dapper backports

I had to give the following command prior to actually installing the gnucash deb (-common deb installed "out of the box"). Maybe it was overkill, but I just followed the dependency failure messages

```
sudo apt-get install libgnutls11 libgsf-gnome-1-113 g-wrap guile-library libgwrap-runtime0-dev libgwrap-runtime0 guile-g-wrap guile-1.6-dev libffi4-dev libncurses5-dev libreadline5-dev
```

seems to be working fine, thanks

---

### Post by registering on 2006-08-15
Hate to beat a dead horse, but are there plans to make 2.0.1 available via the "Add/Remove Software" option under "Applications"? The .deb packages in this thread don't seem to be built with the --enable-ofx option, and compiling generates errors that my glib isn't >=2.4 (which surprises me, but I'm not sure how to check/fix using apt-get; I'd normally do rpm -qa|grep glib). I'd prefer to just point and click to install software than turn my home system into a science experiment (I tried grabbing them from edgy but I get another list of dependancy failures, and trying to fix them leads to yet more). Thanks for any help, this is a great thread. :)

---

### Post by madrebel on 2006-08-19
i get this

> 
grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
make[7]: *** [libgoffice-1.la] Error 1
make[7]: Leaving directory `/home/ron/gnucash-2.0.0/lib/goffice-0.0.4/goffice'
make[6]: *** [all-recursive] Error 1
make[6]: Leaving directory `/home/ron/gnucash-2.0.0/lib/goffice-0.0.4/goffice'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/ron/gnucash-2.0.0/lib/goffice-0.0.4/goffice'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/ron/gnucash-2.0.0/lib/goffice-0.0.4'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ron/gnucash-2.0.0/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ron/gnucash-2.0.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ron/gnucash-2.0.0'
make: *** [build-stamp] Error 2
Build command 'cd gnucash-2.0.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed


when i follow those instructions. any ideas?

---

### Post by mark2741 on 2006-08-21
How do I get online banking working?

---

### Post by mlind on 2006-08-22
> **madrebel said:**
> i get this



when i follow those instructions. any ideas?

This is probably the fifth hit on same issue
[http://www.ubuntuforums.org/showthread.php?t=238449](http://www.ubuntuforums.org/showthread.php?t=238449)

---

### Post by ricochet on 2006-09-07
I am trying to install gnucash and have a lot of missing dependences.  I have tired using apt-get but get the follow message:
```
Reading package lists... Done
Building dependency tree... Done
Package libgnutls11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnutls11 has no installation candidate

```

I think I just need to add a source to make this work, however I don't know what source to add.

Thanks
Richie

---

### Post by kleeman on 2006-09-07
That package is in the universe repository. You need to enable it.

---

### Post by ricochet on 2006-09-08
It is enabled.  I cant seem to make apt-get work for any thing.

Thanks
Richie

---

### Post by kleeman on 2006-09-08
Wierd problem. What does

sudo apt-get update

give?

---

### Post by ricochet on 2006-09-12
When I tried to use apt-get it failed to connect.  I have the same problem with Adept.  However the internet works fine on this computer.  I am thinking I should move this to a new thread since this problem is not really related to gnucash but more of a problem with apt-get. 

Thanks
Richie

---

### Post by ricochet on 2006-09-27
I found the problem was a bad dns source related to my dsl modem.  All is working fine now.

Thanks
Richie

---

### Post by Das Goat on 2006-09-29
Ok, I am so wet behind the ears that I need a towel.

I got gnucash with Automatix last night. I tried it and found the problems you all describe. Turns out it gives me version 1.8.somthing. Ok, I need the new version.

i find the new version, 2.0.1 and am able to d/l the tarball. I want to remove the version Automatix gave me, but I can't figure out how. Add/Remove doesn't list it. I am sure the is some sudo command that will do it, but right now i don't know what it is. Since i am on a project to make this laptop windows free befor I tackel the company as a whole, I don't mind that I frequently wipe the installation and do it all over gain. it is good practice. But a hint would help, sind I went over board last noght and d/l every package that automatix had.

Anyway, I figure that Gnucash will either a) update the version it finds or b) give me another installed version. either is ok by me at this point.

I extract the tarball and read the installation instructions. I have to compile the program. ok, what Is get is:

configure: error: no acceptable C compiler found in $PATH

uh, there is no compiler native in the distro? this seems silly. where do I find one? Surely i though Automatix would install one.

:-?

---

### Post by Sef on 2006-09-29
> uh, there is no compiler native in the distro? this seems silly. where do I find one? 

Applications > Accessories > Terminal (GNOME)

sudo aptitude update

sudo aptitude install build-essential

Then you will be able to compile as build-essential is necessary to compile.

---

### Post by kleeman on 2006-09-29
If you are new to linux I STRONGLY recommend you install the deb packages I listed ealier in this thread. There are also instructions for installation in that post as well. Yell if you have a problem.

---

### Post by bps7j on 2006-10-01
The .deb files posted earlier don't work for amd64.  And I couldn't get the installation from source to work either (no version of glib wrapper could satisfy the dependencies).  Is there something different I'd have to do for amd64?

I already have the official version installed, so maybe I need to remove it and its dependencies first?

I'm pretty new to Ubuntu/Debian, so any help is appreciated.

---

### Post by kleeman on 2006-10-01
For amd64 debs you need to go here:

[http://www.ubuntuforums.org/showthread.php?t=248559](http://www.ubuntuforums.org/showthread.php?t=248559)

---

### Post by mlind on 2006-10-01
> **bps7j said:**
> The .deb files posted earlier don't work for amd64.  And I couldn't get the installation from source to work either (no version of glib wrapper could satisfy the dependencies).  Is there something different I'd have to do for amd64?

I already have the official version installed, so maybe I need to remove it and its dependencies first?

I'm pretty new to Ubuntu/Debian, so any help is appreciated.

i386 binaries won't work for amd64, so you need to compile the source package. You're probably missing some build dependency. You can try using autobuilders like pbuilder or sbuild.

---

### Post by Das Goat on 2006-10-01
Er..... this is the sort of thing that makes it hard for us newbies to get a handle on linux. i suppose it seperates the true believers from the casual converts, but I think as a community, we would get more active users if things were just a bit more clear, or at least packaged better for us neophites.

So, I went to kleeman's repositiorie, d/l the amd64/gnucash_2.0.1-1_amd64.deb

opened it with the package installer and got Error: Dependancies not satisfiable: Gnucash-common.

ok, i at least understand that it is trying to find additional files and doesn't know where to look. i suspect that I should be putting something like deb gnu-cash something something in the sources.list But what? When you guys make these packages, why don't you package everything together? Is it because each flavor of linux needs different dependancies?

Consider this gem from the install instructions i d/l in the gnu-cahs 2.0.1 tarball:

2. Type `make' to compile the package.  (ok, simple enough)
dasgoat@dasgoat-laptop:~/Desktop/gnucash-2.0.1$ make
make: *** No targets specified and no makefile found.  Stop.

?????????? this comes from the distro publisher themselves. Shouldn't they know that this doesn't work?

more research. in the read me files it tells me I need libtool so this thing can compile right. Fine. i finally find the latest libtool tarball, extract it, and find I have to compile it. Ok, i am cool with that too. in it's Install instructions, i get to:
4. Type `make install' to install the programs and any data files and
     documentation.
dasgoat@dasgoat-laptop:~/Desktop/libtool-1.5.22$ sudo make
seemed to work, no errors I can find. but....now what? there are no more instructions for installing the program.

Believe me, I am committed to making Ubuntu work and replacing all the Windows units in my little $2M company. Over three weeks, I have learned how to: Install Unbuntu several times, find libraries, make my wireless card work (one of the hardest i have read), listen to NPR through my browser, and the fundamentals of making Automatix work. Gnucash is just my latest milestone. But it makes me wonder just how successful i am going to be setting up an Appache server, a mail server, integrating scanning and graphics devices, using WINE to convert a propriatry retail application, setting up remote access, converting our documents, and making 15 workstations with at least 7 different hardware configurations all work together. i know i am just venting and i appreciate all the help everyone is giving, but the task is daunting. I just try to keep in mind that we save more that $10k in software and another $8k in hardware, not to mention all of the security enhancements, if i can make this work.

sorry to vent, just frustrated. Unbuntu seems to have so much promise, I just want to make it work.
](*,) 

Anyway, please, what am i doing wrong?

---

### Post by kleeman on 2006-10-01
You need to download BOTH gnucash debs from my site. There is a gnucash-common deb there as well. 

Save them to disk and then go to a console and issue the following command:

sudo dpkg -i gnucash-common_2.0.1-1_all.deb gnucash_2.0.1-1_amd64.deb

---

### Post by Das Goat on 2006-10-02
Ah, ok. Well after I figured out I didn't have g-wrap and that other g-wrap-something, then the command you gave me worked like a charm. If I had those two dependancies previously installed, would the package manager have installed them correctly? Or is this something I needed to do via the console? How would I have known what to do?

:-k

---

### Post by Das Goat on 2006-10-02
Well Gnucash definatly works, but when I imported my QIF file, Gnucash imported the data all over the place. No account is right, money is everywhere, and i have no idea why it did this. Plus, maybe this is the intention og Gnu-cash, but it made nearly every transaction an account.

Maybe this works if you are starting fresh, but I have three years of data to import and can't loose it.

Has anyone maybe gotten thier quicken 2006 files to work, or has used WINE to make Quicken work under Ubuntu?

---

### Post by rbmorse on 2006-10-03
I use Q2006 Premier on Kubuntu Dapper with CrossoverOffice. Works fine. Crossover Office is payware, but you can get an evaluation copy for no charge from their site:

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Das Goat on 2006-10-04
So you like crossove office? what other apps does it work with?

---

### Post by Das Goat on 2006-10-11
Well, some poking and i have figured out this much:

Gnucash imports *.qif files. Ok, that is fine, but you have to import EVERY account you have as a seperate .gif file. I have at least twenty accounts, and this become laborious. i was going to see what happens when I import the "next" .qif file with my bank loaded, but then I realized I wiped my laptop due to the "crash" I will describe below. So i currently can't test this effect with Gnucash, and i am loath to install it again since it acted so poorly. 

The bottom line: Wait until Gnucash can "restore" a back up of your Quicken data. That way it gets all of the accounts and interdepenancies at one time. If you have no data to import, Gnucash maybe the program for you. I am not sure. If you are used to Quicken, the interface is a little confussing and could be a bit daunting, even if you have no data. The way it handles accounts is not like quicken and categories. So, be mindful. In my humble opinion, it is not quite ready for prime time.

Now, about the "crash".

Thanks to rbmorse for pointing me to Crossover Office. I didn't know this application existed. It truely has great promise.

So, I install the Beta 6 version. Then I install Quicken. So far so good. Everything seems to be running correctly. Then i restore my back up. CRASH.
The data is loaded. I can see all of the accounts. The ammounts on the left side of the screen seem accurate. But it is frozen on the opening bank account. I don't know why. And the window for the account is postage stamp sized and will not open.

So, I posit (I do this a lot since i am little better than a noob) that maybe all of the crazy updates and things I have loaded are preventing the application form acting right. So I reformat and re-install Ubuntu. And then re-install Crossover Office and Quicken. It seemes to work just fine. Once I resstore my backup file, the application freezes in the same way it froze before. The data seems to be all there, but you can't do anything, and you end up killing the application.

This is so close to working that the only thing i can think of for what is wrong is that I run 64-bit Ubuntu and Crossover Office is 32-bit. I may be wrong, i have been before, but i am guessing this is the case since rbmorse has been running this effectively and Quicken is a known and supported appication for Crossover Office. 

If anyone can shed some insight on this problem, i would appreciate it, since this is a mission critical application for me to give up Windoze.

Das Goat

](*,)

---

### Post by delfell on 2006-10-14
Where is your site???

---

### Post by Das Goat on 2006-10-14
[www.myspace.com/dergoat](www.myspace.com/dergoat)

I will admit that there is not a lot there right now, but as I figure things out I will post them.

---

### Post by Das Goat on 2006-10-14
What version of Crossover are you using? I downloaded Ver 6 beta to try it out. I run a 64bit PC. Crossover loaded just fine, and installed Quicken 2006 just fine. I could even update Quicken to the current release. But when i restored my back up file, it crashes the application. I did things like re-install Ubuntu, re-install everything, and the problem persists. I also loaded up an old PC with Ubuntu 32bit, and did all of the steps. It crashes when I restore the backup file just like my laptop does.

Any thoughts?

---

### Post by juseal on 2007-01-03
Wow, thanks for the awesome install of gnucash 2!!!

---

### Post by datakid on 2007-04-02
Any news on whether the recent upgrades to Gnucash will be in feisty? atm I'm running 2.0.1 in edgy, but have feisty at home and know that 2.0.5 of GnuCash is available...and I can't seem to find which version is in feisty anywhere...

---

### Post by kleeman on 2007-04-03
2.0.2
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by 55Rebel on 2007-07-13
Not sure if this has been addressed here or not, sorry if it has, but:
I just installed gnucash_2.0.2 using the Synaptic Package Manager. Every thing seemed to go smoothly with the install, dependencies and all,  but can find it nowhere in the application menu after install. :confused: Any clues to where i might find it.
I'm running ubuntu feisty

Thanks

---

### Post by 55Rebel on 2007-07-13
Never mind, it just showed up in Applications > Office :P
Wasn't there earlier :-\"

---

### Post by cyb3rj on 2007-08-08
Per chance, has anyone built GnuCash 2.2.0 OFX/HCBI enabled packages for Feisty 32bit?

---

### Post by coolcar on 2007-10-11
> **mlind said:**
> You can build it from edgy's source repository. Insert new repository to /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

```

Then execute
```

sudo aptitude update
sudo apt-get build-dep gnucash
sudo apt-get source -b gnucash

```

Or use [pbuilder]("http://www.ubuntuforums.org/showthread.php?t=206382")/sbuild to build the package.

Hi Mlind,

Its been a while since this thread was touched. But I am still on dapper and would like to update the gnucash to the latest version on Dapper. Do you think I can add the latest repository and build :confused: The Dapper backports still is on gnucash 1.8 :mad:

Thanks!

---

### Post by mlind on 2007-10-15
> **coolcar said:**
> Hi Mlind,

Its been a while since this thread was touched. But I am still on dapper and would like to update the gnucash to the latest version on Dapper. Do you think I can add the latest repository and build :confused: The Dapper backports still is on gnucash 1.8 :mad:

Thanks!

hmm, I'll check if it's possbile to backport gnucash from Gutsy to Dapper.

---

### Post by coolcar on 2007-10-16
> **mlind said:**
> hmm, I'll check if it's possbile to backport gnucash from Gutsy to Dapper.

Backport of GNUCash from Gutsy to Dapper will be great :) :KS I am sure this will be useful for the not_so_technical user group that need this program on dapper ! I started to look for update from 1.8 because the reports started to crash it regularly.

I am currently struggling to build 2.0 or later. I have tried but guess my lack of compiling skills is limiting it. I tried with the Feisty repository but get stuck with g-wrap dependancies. :confused:

This is what I did. Inserted feisty repository to /etc/apt/sources.list

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

```

sudo aptitude update
sudo apt-get build-dep gnucash

```

E: Build-Depends dependency for gnucash cannot be satisfied because no available versions of package g-wrap can satisfy version requirements

```

sudo apt-get source -b gnucash

```

sh: dpkg-source: command not found
Unpack command 'dpkg-source -x gnucash_2.0.1-3ubuntu3.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

```

sudo aptitude install libltdl3-dev libofx-dev guile-1.6-dev libdb3-dev liborbit-dev libungif4-dev libxml2-dev libbonobo2-dev libgnomevfs2-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libgtkhtml3.8-dev g-wrap

sudo dpkg -i package

```


Guess I was looking at too many places and doing many things besides this thread. Also was unable to figure out the above errors

e,g. [http://ubuntuforums.org/showthread.php?t=268687]("http://ubuntuforums.org/showthread.php?t=268687")
[http://wiki.gnucash.org/wiki/Building#Ubuntu]("http://wiki.gnucash.org/wiki/Building#Ubuntu")

Thanks and will keep looking. 

Meanwhile - this is the part I hate - I have downloaded GNUCAsh latest stable version for Windows XP and am updating there :(

---

### Post by mlind on 2007-10-16
> **coolcar said:**
> Backport of GNUCash from Gutsy to Dapper will be great :) :KS

hiya,

to backport the package, you need to adjust debian/control slightly as dependecies have changed/updated between distributions. Here's my changelog entry
> 
gnucash (2.2.1-1ubuntu4~dapper1) dapper; urgency=low

  * debian/control:
    - b-depends on libgoffice-1-dev instead of libgoffice-0-dev.
    - use ${Source-Version} instead of ${source:Version} as dapper's
      dpkg-dev doesn't know this syntax. remove dpkg-dev b-depends.

 -- mlind <foo@bar>  Tue, 16 Oct 2007 17:55:07 +0300


You can download the binaries for dapper i386 (including source package) from
[http://rapidshare.com/files/63000101/gnucash_2.2.1-1ubuntu4_dapper1.tar.gz](http://rapidshare.com/files/63000101/gnucash_2.2.1-1ubuntu4_dapper1.tar.gz)

---

### Post by coolcar on 2007-10-16
> **mlind said:**
> hiya,

to backport the package, you need to adjust debian/control slightly as dependecies have changed/updated between distributions. Here's my changelog entry


You can download the binaries for dapper i386 (including source package) from
[http://rapidshare.com/files/63000101/gnucash_2.2.1-1ubuntu4_dapper1.tar.gz](http://rapidshare.com/files/63000101/gnucash_2.2.1-1ubuntu4_dapper1.tar.gz)

Hey Thanks a ton for super fast response !  

But ... as I am fairly new to linux I think you will have to go through the pain of spelling out the steps. What do you mean by debian/control changes and changelog entry ? Do I still follow the same steps and add the Gutsy repository ? 

Meanwhile I have downloaded the 2.2.1 binaries from the link you suggested and managed to install it using the debs.

You are a STAR thanks for your help Mlind !  I can now continue using GNUCash on Ubuntu as a part of my role of the Treasurer of a Community Organization, Maybe you can explain the steps and how you compiled ?

Thanks again

---

### Post by coolcar on 2007-10-17
> **coolcar said:**
>  do I download the 2.2.1 binaries from the link you suggested and try to install it using synaptic?
Thanks again
I downloaded the binaries from the link and extracted all the files :)  I tried to install the gnucash_2.2.1-1ubuntu4~dapper1_i386.deb but end up getting the dependency error - "Dependancy is not satisfiable: gnucash-common".  Then I realised that there was gnucash-common_2.2.1-1ubuntu4~dapper1_all.deb in the files. So installed that first.

Great stuff ! GNUCash 2.2.1 on Dapper works now !! 

Mlind you are a STAR !  I can now continue the role of the Treasurer of a Community Organisation on Ubuntu Thanks !

---

### Post by mlind on 2007-10-17
> **coolcar said:**
> I downloaded the binaries from the link and extracted all the files :)  I tried to install the gnucash_2.2.1-1ubuntu4~dapper1_i386.deb but end up getting the dependency error - "Dependancy is not satisfiable: gnucash-common".  Then I realised that there was gnucash-common_2.2.1-1ubuntu4~dapper1_all.deb in the files. So installed that first.

Great stuff ! GNUCash 2.2.1 on Dapper works now !! 

Mlind you are a STAR !  I can now continue the role of the Treasurer of a Community Organisation on Ubuntu Thanks !

sorry, I forgot to include instructions to install the binaries, but you seem to have found out the solution yourself :) My earlier post about changelog entry was just a hint of what packaging changes were needed to make the package compile and install in Dapper.

I included the source package as well, so you or someone else can compile it if required (for different architecture perhaps). I'm glad that the package worked out fine for you!

---

### Post by coolcar on 2007-10-17
> **mlind said:**
> I included the source package as well, so you or someone else can compile it if required (for different architecture perhaps). I'm glad that the package worked out fine for you!

Did you get the source code from GNUCash website and then use [COLOR="Blue"]your Pbuilder [/COLOR]to build the package? Or did you get the source from Gutsy repository? Thanks again !:)

---

### Post by mlind on 2007-10-18
> **coolcar said:**
> Did you get the source code from GNUCash website and then use [COLOR="Blue"]your Pbuilder [/COLOR]to build the package? Or did you get the source from Gutsy repository? Thanks again !:)

I fetched the source from Gutsy's repositories using apt-get, then built it with pbuilder (you need to have deb-src repositories enabled in your /etc/apt/sources.list).

Then do something like this
```

mkdir /tmp/test
cd /tmp/test
sudo aptitude update
sudo aptitude install dpkg-dev devscripts
apt-get source gnucash
cd gnucash-2.1.1

#modify debian/control
nano debian/control
#create new changelog entry and document your changes
dch -i

#re-generate .diff.gz and build the package
cd /tmp/test
dpkg-source -b gnucash-2.1.1
sudo pbuilder **build** gnucash_2.2.1-1ubuntu4~dapper1.dsc

```

---

### Post by coolcar on 2007-10-19
> **mlind said:**
> I fetched the source from Gutsy's repositories using apt-get, then built it with pbuilder (you need to have deb-src repositories enabled in your /etc/apt/sources.list).

Thanks I will try to note this method in my growing linux tips arsenal / text file.

By the way the GNUCash 2.2.1 works on Dapper like a charm. It also got listed in the Applications / Office Menu :) For the 1.8 I had to create a Launcher myself.

In fact at start up it is also throwing up some warnings which I suspect was the main cause why the Dapper standard 1.8 was crashing when I ran Reports. But that version did not give me any warnings. 

"A custom report with this name already exists. Either rename the report to store it with a different name, or edit your saved-reports file and delete the section with the following name: Account Summary, Register"

Thanks!

---

