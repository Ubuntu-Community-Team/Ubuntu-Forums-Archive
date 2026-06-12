---
title: "HOWTO: Install LinuxDC++"
date: 2006-06-10
forum: Tutorials
---

### Post by stevensheehy on 2006-06-10
[COLOR="Red"][SIZE="4"]UPDATE 1: LinuxDC++ 1.1.0 has been released. This guide is only if you want to compile the latest LinuxDC++ from Bazaar, which may or may not be as stable as 1.1.0. You can find it in our: [LinuxDC++ Release PPA]("https://launchpad.net/~linuxdcpp-team/+archive/release")[/SIZE][/COLOR]

[COLOR="Red"][SIZE="4"]UPDATE 2: You can install debian binaries of our latest unreleased code from our [Launchpad PPA]("https://launchpad.net/~linuxdcpp-team/+archive/ppa").[/SIZE][/COLOR]

First off, for those that don't know, [LinuxDC++]("https://launchpad.net/linuxdcpp") is a Linux port of the file-sharing program [DC++]("http://dcplusplus.sourceforge.net/"). It uses the DC++ core but with a GTK+ GUI. It has also been called by many other names including: linuxdcpp, ldcpp, dcpp, ldc++, dc++ for linux, wulfor. I'm a developer on LinuxDC++ and thought I'd write up a guide to install LinuxDC++ on Ubuntu.

First, download the required dependencies:

bzr
scons
build-essential
libgtk2.0-dev
libglade2-dev
zlib1g-dev
libbz2-dev
libssl-dev
libboost-dev

To do this in one command:
```
sudo apt-get install bzr scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev libboost-dev
```

There are no official releases of the program since it's still in alpha. This means that there exists no official binaries for any distribution. However, to install LinuxDC++ you can download it through bazaar. Run these commands in your home directory or somewhere else where you have write access:

```

bzr branch lp:linuxdcpp
```

Now to install (you can set PREFIX to whatever, but I'd recommend /usr/local):
```

cd linuxdcpp
scons release=1 PREFIX=/usr/local
sudo scons install
```

To run:
```
linuxdcpp
```
Note: Turn off Assistive Technologies before running LinuxDC++ (System->Preferences->Assistive Technologies). For some reason, it makes linuxdcpp run very slowly and display a bunch of errors.



When we update the source, you can update your linuxdcpp source and re-run the scons & scons install commands from above to install it again. To update the source:
```

cd /path/to/source/dir
bzr update
```

To uninstall LinuxDC++:
```

cd /path/to/source/dir
sudo scons -c install
```
Then you can delete your source directory if you like.

Some links:
[LIST]
[*][LinuxDC++]("https://launchpad.net/linuxdcpp"): official homepage
[*][PPA]("https://launchpad.net/~linuxdcpp-team/+archive/ppa"): Debian packages of our latest unreleased code
[*][LinuxDC++ Wiki]("http://openfacts.berlios.de/index-en.phtml?title=DC%2B%2B+for+Linux"): You can find our FAQ and our manual here.
[*][DC++]("http://dcplusplus.sourceforge.net/"): original windows DC++ program that LinuxDC++ is based on.
[*][#linuxdc++@freenode.net]("irc://irc.freenode.net/linuxdc++"): Visit our IRC channel if you have any questions. I'm usually there under the nick "_steven_"; if I'm not, just ask in the channel and somebody should hopefully respond.[/LIST]

---

### Post by Poka64 on 2006-06-11
Great howto, thx for all the help on irc :)

---

### Post by anodizer on 2006-06-11
Nice howto, thnx. Now let's hope for a final and bug-free release of linuxdc++.

---

### Post by mrazster on 2006-06-12
Works like a charm....no problems here. 
Ran one of your previous releases under breezy...very unstable and buggy.

One thing thou...it uses alot of cpu power from time to time....ie. when I connect to a hub with say 3000+ users....it takes alot of cpu power to calculate number of users and the amount of files shared.

Other than, that everything is peachy..!!!  :p

---

### Post by stevensheehy on 2006-06-12
[QUOTE=mrazster]One thing thou...it uses alot of cpu power from time to time....ie. when I connect to a hub with say 3000+ users....it takes alot of cpu power to calculate number of users and the amount of files shared.[/QUOTE]

Don't sort the user list. GtkTreeView is inefficient when inserting thousands of rows and having it sorted. Keeping it unsorted until it fully loads should speed things up. Same with search.

---

### Post by Rizado on 2006-06-12
Works ok, it's allittle buggy still. /fav doesn't seem to work (Maybe it's supposed to be like this?) and it refuses to show any hublist. Anyone else having this problem? One of the hublists doesn't exist and dc tells me this but when I remove that one nothing happens at all.

---

### Post by stevensheehy on 2006-06-12
[QUOTE=Rizado]Works ok, it's allittle buggy still. /fav doesn't seem to work (Maybe it's supposed to be like this?) and it refuses to show any hublist. Anyone else having this problem? One of the hublists doesn't exist and dc tells me this but when I remove that one nothing happens at all.[/QUOTE]

As I've said previously, it's still in alpha so bugs are to be expected. I've also mentioned that not all features have been implemented (eg /fav). hublist.org might be down again.

---

### Post by mrazster on 2006-06-12
[QUOTE=stevensheehy]Don't sort the user list. GtkTreeView is inefficient when inserting thousands of rows and having it sorted. Keeping it unsorted until it fully loads should speed things up. Same with search.[/QUOTE]

Well...it does that by default. Atleast it does for me....and either I'm dumb or blind :p ....but I can't a setting for it.

---

### Post by stevensheehy on 2006-06-12
[QUOTE=mrazster]Well...it does that by default. Atleast it does for me....and either I'm dumb or blind :p ....but I can't a setting for it.[/QUOTE]

No it does not. Sometimes a hub sends the user list in somewhat sorted order, but the GtkTreeView is not sorted upon startup. You can tell because there's no arrow indicating order on any of the column headers.

---

### Post by Rizado on 2006-06-13
[QUOTE=stevensheehy]As I've said previously, it's still in alpha so bugs are to be expected. I've also mentioned that not all features have been implemented (eg /fav). hublist.org might be down again.[/QUOTE]Well the thing is hublist.org isn't down, the other one is and it tell me this but then nothing happens. I just wanted to know if this only happens to me.

---

### Post by stevensheehy on 2006-06-13
[QUOTE=Rizado]Well the thing is hublist.org isn't down, the other one is and it tell me this but then nothing happens. I just wanted to know if this only happens to me.[/QUOTE]

[http://www.hublist.org/PublicHubList.xml.bz2](http://www.hublist.org/PublicHubList.xml.bz2) works for me. Are you able to connect to hubs and search just fine? If not, then a firewall of some sort might be blocking you and you could try switching to passive.

---

### Post by Rizado on 2006-06-14
[QUOTE=stevensheehy][http://www.hublist.org/PublicHubList.xml.bz2](http://www.hublist.org/PublicHubList.xml.bz2) works for me. Are you able to connect to hubs and search just fine? If not, then a firewall of some sort might be blocking you and you could try switching to passive.[/QUOTE]Everything works except hublists, I can copy the favorites xml from windows and use it. Maybe it's just a new bug that'll be fixed soon.

---

### Post by Angellis_ater on 2006-06-14
Hi! I've been using LDCPP for a few days now and everything has been working excellently, up until today.

Now, when I start LDCPP it acts as if my active mode isn't correctly set or something - I can't search nor download from other users. I've checked my IP settings and they are correct.

All of this happened, as far as I can tell, after installing Automatix and BitTornado - can they have affected something crucial for LDCPP?

---

### Post by Angellis_ater on 2006-06-14
I tried to uninstall it and got the following error:

> IOError: [Errno 13] Permission denied: 'config.log':
  File "SConstruct", line 73:
    conf = Configure(env, custom_tests = {'CheckPKGConfig' : CheckPKGConfig,
  File "/usr/lib/python2.4/site-packages/SCons/SConf.py", line 129:
    self._startup()
  File "/usr/lib/python2.4/site-packages/SCons/SConf.py", line 464:
    self.logstream = open(str(self.logfile), log_mode)


So, how do I fix this problem?

---

### Post by stevensheehy on 2006-06-15
[QUOTE=Angellis_ater]So, how do I fix this problem?[/QUOTE]

Which problem? You mentioned two...

For the first one, try a new profile (rename ~/.dc++). If same deal, then it's a problem with your local network config (firewall, router, etc). At the very least, it should work on passive.

Second one, no idea. Looks like your something is wrong with the scons installed on your system.

---

### Post by skatedawe on 2006-06-15
I got problem with hash! It has to hash everytime i start ldcpp, when its starting it want to hash +150gb everytime im restarting the program.

Is there anything I can do ?

---

### Post by Rizado on 2006-06-15
[QUOTE=skatedawe]I got problem with hash! It has to hash everytime i start ldcpp, when its starting it want to hash +150gb everytime im restarting the program.

Is there anything I can do ?[/QUOTE]I have to hash everything with åäö in the name, could be something like that for you too. Luckely I only have one movie with those letters.

---

### Post by skatedawe on 2006-06-15
Thank you so much [tackar] :)

I'm gonna try it. I think it will solve the problems.

---

### Post by stevensheehy on 2006-06-15
[QUOTE=skatedawe]I got problem with hash! It has to hash everytime i start ldcpp, when its starting it want to hash +150gb everytime im restarting the program.

Is there anything I can do ?[/QUOTE]

Please read our [Bug Tracker]("http://developer.berlios.de/bugs/?group_id=2230") to see if the bug is already known before mentioning it. In this instance, Bug #4138.

---

### Post by xerixs on 2006-06-15
All work. Thx :)

---

### Post by stevensheehy on 2006-06-15
I just upgraded the dc++ core of LinuxDC++ from 0.674 to 0.691. There are a lot of nice features and bug fixes in this. This is from the changelog (pay special note to the warning):

* Upgraded the client core to version 0.691:
[INDENT]<WARNING> 
[INDENT]* All sources to downloads will be lost (not the files) due to Queue.xml core changes.
* Some settings will have to be reconfigured (namely connection mode & speed).[/INDENT]
</WARNING>
* Added features:
[INDENT]* Disconnect slow users.
* IP field can accept a hostname.
* Markers for ZDownloads, TTH Trees, TTH Check, Secure (Not supported) & Rollback.
* Show timestamps options.
* Log Hub, PM and Filelist transfers.
* Option to use Monospaced font for Hub & PM (thanks UrkeMMI).
* Tab bolding options for Hub, PM, Search, Finished Downloads and Finished Uploads.
* Notification when searching too soon.[/INDENT]
* Fixed bugs:
[INDENT]* Bug #6103: crashes when have no permission to create file/directory (untested)
* Bug #6294: Hub topics not working
* Bug #6462: User list loading very slow (on Open DC hubs)
* Switching connection mode requires a restart.[/INDENT][/INDENT]
* Completely rewrote settings dialog to make room for the new options.
* Hid most of the unimplemented settings.
* Fixed bug #7651: GUI Freeze (in downloadqueue)
* Rewrote the character encoding code to use a user-specified fallback locale (default CP1252)
  if current locale fails. Not a 100% fix for unicode issues, but a start.

Enjoy

---

### Post by stevensheehy on 2006-06-15
Note that this updated may fix the rehashing files on startup issue. I would appreciate if people could test and reply back here if fixed or not.

---

### Post by anodizer on 2006-06-15
[QUOTE=stevensheehy]Note that this updated may fix the rehashing files on startup issue. I would appreciate if people could test and reply back here if fixed or not.[/QUOTE]

No it isn't. Still rehashing the same tracks.

---

### Post by Angellis_ater on 2006-06-16
Can't say what it is, but the upgrade fixed any problems I had with downloading! Excellent work and nice update in general! You guys ROCK!

---

### Post by weiersc on 2006-06-18
Hi, 

I think I have a different problem. When I try to contact cvs with *"cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login"* the connection fails, and I am quite sure that it is because the Firewall is blocking access to the port (2401).

Is there any other way for me to download the source? I was able to downlaod the .deb package* linuxdcpp_0.0.1.cvs20060530-1_i386.deb*, but my debian installer  gives an error: Depenency is not satisfiable: libc6.

I wonder if somebody could help me with a workaround? (I use ubuntu dapper, I have all the other programmes installed, except for the files that I need to download from the cvs server)

Thanks

Weiers

---

### Post by stevensheehy on 2006-06-18
[QUOTE=weiersc]I think I have a different problem. When I try to contact cvs with *"cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login"* the connection fails, and I am quite sure that it is because the Firewall is blocking access to the port (2401).[/QUOTE]

You don't need to specifically allow ports to connect with cvs. You're initiating the connection so the port is already open when the server replies. More likely, the server was down at the time and you should try again. Unless you setup some really weird firewall rules...

[QUOTE=weiersc]Is there any other way for me to download the source? I was able to downlaod the .deb package* linuxdcpp_0.0.1.cvs20060530-1_i386.deb*, but my debian installer  gives an error: Depenency is not satisfiable: libc6.[/QUOTE]

We don't provide the source except through CVS. The debian is the only other way (and that isn't an official way). If the debian doesn't install, then probably the CVS won't install either. You need to get libc6, which should've been downloaded if you got the build-essential package.

---

### Post by h2gofast on 2006-06-19
how does this compare to valknut?

---

### Post by NeoChaosX on 2006-06-19
Valknut, being written in Qt, intergrates better with KDE. However, if you're familiar with DC++ in Windows and are a GNOME user, Linux DC++ will make you feel at home. Valknut's is a complete program, though, while DC++ is alpha and doesn't have as many features implemented (properly) yet (for instance, downloading a directory is still buggy in Linux DC++).

---

### Post by Oblong_Cheese on 2006-06-21
Under Dapper amd-k8 kernel (not that that should make a difference?), the download, compile and install works fine, I can run the programme fine, but it simply will not hash any files or generate a file list.

When I open ldcpp, in the statusbar is the message "Hashing failed: could not open file", irrespective of the file I have set it to hash; be it in my local directory or not.

Executing ldcpp under gksudo does not help either.

Does anyone know why this is happening?

***Fixed!***

Turns out there's a bug in the 64-bit compile whereby ~/.dc++/HashData.dat isn't created. A simple # touch ~/.dc++/HashData.dat and ldcpp is on it's way!

---

### Post by snek on 2006-06-22
I got the program working fine, except I can't seem to share most directories.. It works for some, but on others it crashes right away. So far I haven't been able to share a folder on an NTFS drive. But it even has problems with some folders under ext3. It seems like it doesn't like sharing folders with lots of periods and/or strange symbols.. But if I share a dir under that with a simple name it does share it o_0

Ubuntu 6.06LTS - Kernel 6.15-25 K7

AMD Sempron64 3400+
Asus K8V-SE Deluxe
1.5GB DDR400
80GB IDE133 - EXT3
250GB SATA - NTFS
300GB SATA - NTFS
120GB FireWire External - NTFS

---

### Post by stevensheehy on 2006-06-23
[QUOTE=Oblong_Cheese]Turns out there's a bug in the 64-bit compile whereby ~/.dc++/HashData.dat isn't created. A simple # touch ~/.dc++/HashData.dat and ldcpp is on it's way![/QUOTE]

Fixed in CVS.

[QUOTE=snek]I got the program working fine, except I can't seem to share most directories.. It works for some, but on others it crashes right away. So far I haven't been able to share a folder on an NTFS drive. But it even has problems with some folders under ext3. It seems like it doesn't like sharing folders with lots of periods and/or strange symbols.. But if I share a dir under that with a simple name it does share it o_0[/QUOTE]

I committed a possible fix for the crashing when adding shares problem. The not sharing some dirs is due to character encoding issues. There's not an easy fix.

---

### Post by snek on 2006-06-27
Ah thanks a lot. I will give it a try once I am back home.

---

### Post by snek on 2006-06-28
Somehow the update didn't want to work, but after uninstalling (and deleting all files from the .whatever dir in my home) and reinstalling the program it's working fine. It even shared all the files on my NTFS drives without problems...

Thanks stevensheehy, saved my life!! ;)

---

### Post by Nikolas on 2006-07-01
Hello,
I ran into a little problem while compiling LinuxDC++. It seems that I have all the packages that it requires, but when I run scons in linuxdcpp directry, I get *loads* of weird errors saying some crazy stuff like "./string:593:1: error: exponent has no digits". I've pasted some of the errors to [here]("http://rafb.net/paste/results/1gm5mz84.html"). Anyone have any ideas what might be wrong? Any help would be appreciated.

---

### Post by stevensheehy on 2006-07-01
[QUOTE=Nikolas]Hello,
I ran into a little problem while compiling LinuxDC++. It seems that I have all the packages that it requires, but when I run scons in linuxdcpp directry, I get *loads* of weird errors saying some crazy stuff like "./string:593:1: error: exponent has no digits". I've pasted some of the errors to [here]("http://rafb.net/paste/results/1gm5mz84.html"). Anyone have any ideas what might be wrong? Any help would be appreciated.[/QUOTE]

It looks like your STL string header is messed up. Your install messes up as soon as <string> is included, so it's definitely something wrong with your system. You should have the dev files for libstdc++. If you do, try re-installing libstdc++ (mine is libstdc++6 & libstdc++6-4.0-dev).

---

### Post by kikkum on 2006-07-04
I built a Dapper i386 package from the deb-source at [http://packages.debian.org/unstable/net/linuxdcpp](http://packages.debian.org/unstable/net/linuxdcpp), which is a cvs build itself. Installing with this package works like a charm for me, haven't experienced any bugs yet (though this is only my 2nd testing hour).

You can download it from [http://ubuntu.kikkum.net/pakketten/linuxdcpp_0.0.1.cvs20060613-1_i386.deb](http://ubuntu.kikkum.net/pakketten/linuxdcpp_0.0.1.cvs20060613-1_i386.deb) or build it yourself from the source package at the above URL by doing

$ dpkg-source -x linuxdcpp_0.0.1.cvs20060613-1.dsc
$ cd linuxdcpp_blah
$ fakeroot dpkg-buildpackage

and installing like

$ cd ..
$ sudo dpkg -i linuxdcpp_0.0.1.cvs20060613-1_i386.deb

---

### Post by stevensheehy on 2006-07-04
[QUOTE=kikkum]I built a Dapper i386 package from the deb-source at [http://packages.debian.org/unstable/net/linuxdcpp](http://packages.debian.org/unstable/net/linuxdcpp), which is a cvs build itself.[/QUOTE]

Did you happen to try installing the already built Debian ones on that page to see if they worked first? I'm curious to see whether they work on Ubuntu or not...

---

### Post by kikkum on 2006-07-05
[QUOTE=stevensheehy]Did you happen to try installing the already built Debian ones on that page to see if they worked first? I'm curious to see whether they work on Ubuntu or not...[/QUOTE]

Indeed I tried that first, but because it's a build from the unstable branch, it has a bunch of dependencies with versions higher than the versions in Dapper. If you'd really want to, I suppose you can install all those dependencies by downloading them from the Debian repo's, but you'd be screwing up your Dapper in the process (security updates won't be applied automatically anymore, because your version would always stay higher until the next Ubuntu).

Long story short: it doesn't work (at least not out of the box, and isn't that what we all want ;) ).

---

### Post by stevensheehy on 2006-07-13
I just committed a major update in which I added a bunch of features like /commands, etc.:

```

* Removed the last vestiges of Wulfor name in the GUI (thanks Pavlov Konstantin).
* Fixed some memory leaks.
* callback.hh was finally removed.
* Re-added show tray icon setting.
* Fixed a crash when adding the same share twice (thanks Mikael Eman).
* Fixed a crash when downloading a dir from search in debug mode (regression).
* Hub changes:
	* Cleaned up the source.
	* Added keyboard events.
	* Added ability to retrieve chat history by using the up and down arrows.
	* Fixed problem with not having userlist sorted when joining a hub.
	* Turned off "rules-hint" (AKA striped lines) in nick treeview to speed things up.
	* Replaced nick completion code with the much simpler GtkEntryCompletion (5 lines of code vs 100).
	* Implemented these options:
		* Filter kick messages
		* Log status messages
		* Automatically follow redirects
		* Show timestamps in chat by default
		* View status messages in main chat
		* Show joins / parts in chat by default
		* Only show joins / parts for favorite users
		* Send unknown /commands to the hub
		* Open new window when using /join
		* Ignore private messages from offline users
		* Open new private message windows in the background
		* Open file list window in the background
	* Added these commands: /away, /back, /clear, /close, /favorite, /getlist,
	  /grant, /help, /join, /pm, /rebuild, /userlist
```

---

### Post by ekravche on 2006-07-15
Thanx for posting this howto

---

### Post by Dunkel Engel on 2006-07-16
Hello, I have a "little" problem.
I just can't download files not neither the filelist, it just says "connection timeout" 
This it not happens with all users, and I know that the problem it's not about passive mode or something like that, because I can download files from some passives users. 
maybe someone knows what it's happening?

---

### Post by kikkum on 2006-07-16
> **stevensheehy said:**
> I just committed a major update in which I added a bunch of features like /commands, etc.:

```

...
```

Did you notify the Debian package manager (Romain Beauxis <toots@rastageeks.org>)?

---

### Post by stevensheehy on 2006-07-16
> **kikkum said:**
> Did you notify the Debian package manager (Romain Beauxis <toots@rastageeks.org>)?

Why would I do that? We update much more often than I've happened to mention in this thread, as you can see in our [changelog](http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain). Am I to email him each time? Am I also to email other distro package providers like ALT Linux Sisyphus, FreeBSD, NetBSD, etc.? Besides, he's been able to keep up-to-date thus far, except it looks like Romain is having issues with the upgrade to DC++ core 0.691 since his cvs version is 20060613. This is why I recommend compiling from CVS, you don't get the latest updates otherwise.

---

### Post by kikkum on 2006-07-16
You could do it to make me a happier man :p But I'll try cvs'ing it them sometime.

---

### Post by Poka64 on 2006-07-16
> **kikkum said:**
> You could do it to make me a happier man :p But I'll try cvs'ing it them sometime.

It's not that hard, the step-by-step instructions on the first page works perfectly ! :)

---

### Post by evdm on 2006-07-20
I do not seem to be able to install as described in this howto. I run a pretty fresh Dapper (i386) installation and get the following:

[I][FONT="Courier New"]sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev[/FONT]

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.18-0ubuntu2 is to be installed
                 Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
E: Broken packages[/I]

I have also tried the suggested:

[FONT="Courier New"]sudo apt-get install libglitz1-dev[/FONT]

But that did not seem to help.

Any suggestion would be much appreciated, thanks!

Erik

---

### Post by stevensheehy on 2006-07-20
Looks like there's some issues with your repository. Your libgtk2.0-dev is depending on an older libgtk2.0 package. It even says as much at the bottom with "Broken packages". You should make sure you only have the default repositories enabled and reload the list using synaptic. If that doesn't work, you may have to contact Ubuntu devs for help.

---

### Post by evdm on 2006-07-22
> **stevensheehy said:**
> You should make sure you only have the default repositories enabled and reload the list using synaptic. 

Thanks a Mil for that! I replaced the repository (which was, IIRC, a present from easyubuntu) with the one from the ubuntuguide and it worked like a charm. I am very pleased with LinuxDC++!

There seems to be a minor issue that the terminal from which I start the application keeps giving:

[FONT="Courier New"](ldcpp:6691): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()[/FONT]

Not sure if that should bother me?
Further I do not seem to get stunnel encryption working on Dapper, but that might be a bit off-topick here.

Anyway, thanks again!

---

### Post by nylle on 2006-07-22
This is weird, I used to run the version that is installed with automatix, and after reading this thread realised that it was quite old. I installed from cvs today, and while the application looks a lot better I can't connect to my normal hubs anymore.

They complain:
```
You are either using a too old or non accepted client for this hub. We are currently only allowing clients that support extended protocol tth hashing and have dc++  myinfo string present. The client can not have such as bandwidth limitation or fake share possibilities.
We currently require atleast DC++ 0.668, fulDC 6.58 or McDC++ 0.26

```

And the hublog says:

```

The clientversion that you are running is not allowed in this
 hub, please upgrade before coming back!

```

This is quite odd, as I just upgraded from an older version, and then it was no problem to connect.

Has LinuxDC++ changed its info string recently?

EDIT: Crap, it seems that it's the hubs I'm connecting to that hasn't changed the version they allow to the latest dc++. So, disregard the above.

---

### Post by stevensheehy on 2006-07-22
> **evdm said:**
> [FONT="Courier New"](ldcpp:6691): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()[/FONT]

Ignore these.

---

### Post by nylle on 2006-07-22
Heh, I changed the version string to 0.674 and recompiled. Now everything seems to work fine.

Thanks for bringing this program to Linux!

---

### Post by kaamos on 2006-07-22
> **stevensheehy said:**
> 
> Turns out there's a bug in the 64-bit compile whereby ~/.dc++/HashData.dat isn't created. A simple # touch ~/.dc++/HashData.dat and ldcpp is on it's way!
Fixed in CVS.

Present in todays cvs on a 32bit platform.

---

### Post by stevensheehy on 2006-07-23
> **kaamos said:**
> Present in todays cvs on a 32bit platform.

I'm on 64bit and don't experience this problem. I also asked another guy in the channel to reproduce this problem on 32bit and he could not. Deleting ~/.dc++/ and starting ldcpp creates a new profile. HashIndex.xml isn't created until you add a share.

---

### Post by stevensheehy on 2006-07-27
If you get this error when trying to download the source tree using cvs:

```
can't create temporary directory /tmp/cvs-serv9546
No space left on device
```

That means the actual berlios CVS server is out of space on their hard drive (your hard drive is fine ;) ). Until berlios fixes it, you can download the latest source here:

[http://tinyurl.com/m88fo](http://tinyurl.com/m88fo)

---

### Post by lovewontbebetter on 2006-07-29
XML Parsing Error:not well-formed
Location:chrome://mozapps/content/downloads/unknownContentType.xul
Number 1,Column 1:
Downloads/unknownContentType.xulUT


this was the message which i got when i tried to directly download
linuxdcpp_0.0.1.cvs20060530-1_i386.deb from "http://ftp.gva.es/mirror/debian/pool/main/l/linuxdcpp/?C=N;O=D"

If i take up the regular routine for installing Dc++ like what is mentioned in the manual for breezy n the begining of thread i get ::

tatsat@ubuntu:~/ldcpp$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcppCVS password:
Unknown host cvs.linuxdcpp.berlios.de.

$$$$$What should i do about it?? Please help me out am stuck,If anyone is having the deb please mail me at [email]lovewontbebetter@yahoo.co.in[/email]..I will be obeliged to him for kindness..
Please helpme out

---

### Post by stevensheehy on 2006-07-29
> **lovewontbebetter said:**
> this was the message which i got when i tried to directly download
linuxdcpp_0.0.1.cvs20060530-1_i386.deb from "http://ftp.gva.es/mirror/debian/pool/main/l/linuxdcpp/?C=N;O=D"

As I said, there are no official binaries so we do not provide support for any that you may find. The one you downloaded is a Debian binary and someone else in the thread has already confirmed it doesn't work on Ubuntu. I should probably remove it from the front page.

> **lovewontbebetter said:**
> If i take up the regular routine for installing Dc++ like what is mentioned in the manual for breezy n the begining of thread i get ::
The CVS server has been having issues lately. It seems to be okay at the moment so try it again. You only have to press enter when it prompts for the password.

---

### Post by lovewontbebetter on 2006-07-30
its not working even now

---

### Post by stevensheehy on 2006-08-01
> **lovewontbebetter said:**
> its not working even now

It seems to be back down again. Download the archive I posted 3 posts up.

---

### Post by lleberg on 2006-08-16
Seems i'm stuck in some passive-mode thing, can't search and can't download filelists..
Upgraded from linuxdc++, some older version.. and it took the settings and everything from that, really wounderful!

But how to fix the downloading issue? the activemode ports are open..

---

### Post by stokedfish on 2006-08-17
thank you so much for this how-to! 

i hope everything works fine here, giving it a go now! :)

---

### Post by humansuit on 2006-08-21
Hi

I upgraded with cvs today 21.8 (cvs update -d) and now the program crashes every time i try to add custom Download to -option in options->download. The programs just shuts down when I click the Add-button. I went ahead to file a bug but there was something wrong with the registration so i figured someone might find this here.

EDIT: The crashing happens also when i try to add a shared folder so maybe something wrong with that add-window

I ran the ldcpp in gdb and this followed:

```
.......
[New Thread -1324110928 (LWP 10263)]
[Thread -1324110928 (LWP 10263) exited]
[New Thread -1324110928 (LWP 10264)]
[Thread -1324110928 (LWP 10264) exited]
[New Thread -1324110928 (LWP 10271)]
[Thread -1324110928 (LWP 10271) exited]
[New Thread -1324110928 (LWP 10272)]
[Thread -1315447888 (LWP 10262) exited]
terminate called after throwing an instance of 'SocketException'

Program received signal SIGABRT, Aborted.
[Switching to Thread -1289864272 (LWP 10259)]
0xffffe410 in __kernel_vsyscall ()
```

and backtrace produced the following:
```
(gdb) backtrace
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75f49a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb75f62b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb77d3c1e in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#4  0xb77d1915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#5  0xb77d194a in std::terminate () from /usr/lib/libstdc++.so.6
#6  0xb77d195f in std::terminate () from /usr/lib/libstdc++.so.6
#7  0xb77d1418 in __cxa_call_unexpected () from /usr/lib/libstdc++.so.6
#8  0x0808ec8a in ConnectionManager::Server::run ()
#9  0x081646c0 in Thread::starter ()
#10 0xb7f61341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb76954ee in clone () from /lib/tls/i686/cmov/libc.so.6
```

I'm running ubuntu dapper drake with gnome 2.14.3

Hope this helps, 
pete

---

### Post by stevensheehy on 2006-08-21
> **humansuit said:**
> I upgraded with cvs today 21.8 (cvs update -d) and now the program crashes every time i try to add custom Download to -option in options->download. The programs just shuts down when I click the Add-button. I went ahead to file a bug but there was something wrong with the registration so i figured someone might find this here.

EDIT: The crashing happens also when i try to add a shared folder so maybe something wrong with that add-window

I could not reproduce your crash. Most likely you updated and somehow your glade file is out of sync with CVS head (probably due to differing PREFIX's). Open settingsdialog.glade and search for "dirChooserDialog", which is the dialog that pops up when you press the add button. If it doesn't exist, then it's the above problem I mentioned. If it does exist, re-compile with scons debug=1, then run in gdb and try to get it to crash when adding a download to option.

---

### Post by humansuit on 2006-08-22
> **stevensheehy said:**
> I could not reproduce your crash. Most likely you updated and somehow your glade file is out of sync with CVS head (probably due to differing PREFIX's). Open settingsdialog.glade and search for "dirChooserDialog", which is the dialog that pops up when you press the add button. If it doesn't exist, then it's the above problem I mentioned. If it does exist, re-compile with scons debug=1, then run in gdb and try to get it to crash when adding a download to option.

Thanks for your reply. 
This was the only mention of dirChooserDialog in settingsdialog.glade:

```
<widget class="GtkFileChooserDialog" id="dirChooserDialog">
```
followed by bunch of <property name>s

I re-compiled dc++ with debug=1 but i don't thinks it's giving me any more info than i already pasted. Now it hangs instead of crashing when i run it in gdb and crashes with "terminate called after throwing an instance of 'SocketException' Aborted" when i run it normally. 

I installed Glade Interface Designer a while ago (between initial install of ldcpp and yesterdays upgrade), could some of it's glade-libraries or something affect this? Just guessing, i really don't know much of these things :)

Is there any way to add shares and download to -options from the command line? everything else works just fine..

thanks, 
pete

---

### Post by stevensheehy on 2006-08-22
You can always edit ~/.dc++/Favorites.xml if you want to add favorite dirs and edit DCPlusPlus.xml if you want to add shared dirs. Though unless you have an existing entry, the exact format to add it as is not exactly clear.

Just because the settingsdialog.glade that you opened has dirChooserDialog doesn't mean that there might not be another settingsdialog.glade on your system that ldcpp is using. It still sounds to me like you didn't upgrade it properly (e.g. you didn't supply PREFIX to both scons and scons install after cvs update). What I would recommend though is to completely start over from scratch. Remove the install and compile linuxdcpp directories and follow this howto again from scratch. You may also want to try with a new profile to see if that helps.

---

### Post by humansuit on 2006-09-01
> **stevensheehy said:**
> You can always edit ~/.dc++/Favorites.xml if you want to add favorite dirs and edit DCPlusPlus.xml if you want to add shared dirs. Though unless you have an existing entry, the exact format to add it as is not exactly clear.

Just because the settingsdialog.glade that you opened has dirChooserDialog doesn't mean that there might not be another settingsdialog.glade on your system that ldcpp is using. It still sounds to me like you didn't upgrade it properly (e.g. you didn't supply PREFIX to both scons and scons install after cvs update). What I would recommend though is to completely start over from scratch. Remove the install and compile linuxdcpp directories and follow this howto again from scratch. You may also want to try with a new profile to see if that helps.

Hi

I just uninstalled, slocated and removed everything related to dc++, including ~/.dc++/, installed again following the howto in this thread, and it still crashes everytime dirChooserDialog is needed. Any ideas? :) Now I can't add shared folders anymore so i can't use it anymore :(

Pete

---

### Post by stevensheehy on 2006-09-01
> **humansuit said:**
> Hi

I just uninstalled, slocated and removed everything related to dc++, including ~/.dc++/, installed again following the howto in this thread, and it still crashes everytime dirChooserDialog is needed. Any ideas? :) Now I can't add shared folders anymore so i can't use it anymore :(

Pete

Not unless you compile in debug mode and paste me an updated backtrace.

---

### Post by humansuit on 2006-09-01
> **stevensheehy said:**
> Not unless you compile in debug mode and paste me an updated backtrace.

Ok, 
```
(gdb) run
Starting program: /usr/local/bin/ldcpp
[Thread debugging using libthread_db enabled]
[New Thread -1219615040 (LWP 10314)]
Thrown: FileException: Could not open /home/koti/.dc++/GeoIpCountryWhois.csv
Thrown: FileException: Could not open /home/koti/.dc++/Favorites.xml
FavoriteManager::load: FileException: Could not open /home/koti/.dc++/Favorites.xml
Loading: Hash database
[New Thread -1220850768 (LWP 10317)]
Thrown: FileException: Could not open /home/koti/.dc++/HashIndex.xml
Loading: Shared Files
Thrown: FileException: Could not open /home/koti/.dc++/files.xml.bz2
FileException: Could not open /home/koti/.dc++/files.xml.bz2
[New Thread -1229243472 (LWP 10318)]
[Thread -1229243472 (LWP 10318) exited]
Loading: Download Queue
[New Thread -1229243472 (LWP 10319)]
[New Thread -1238053968 (LWP 10320)]
[New Thread -1246446672 (LWP 10321)]
[New Thread -1270867024 (LWP 10322)]
[New Thread -1271583824 (LWP 10323)]
[New Thread -1279976528 (LWP 10324)]
[New Thread -1288369232 (LWP 10325)]
[New Thread -1296823376 (LWP 10326)]
Thrown: SocketException: Keskeytetty järjestelmäkutsu
terminate called after throwing an instance of 'SocketException'
Thrown: SocketException: Keskeytetty järjestelmäkutsu
terminate called recursively

Program received signal SIGABRT, Aborted.
[Switching to Thread -1279976528 (LWP 10324)]
0xffffe410 in __kernel_vsyscall ()
```

(Keskeytetty järjestelmäkutsu means Interrupted System Call)

```
(gdb) backtrace
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75df9a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb75e12b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb77bec1e in __gnu_cxx::__verbose_terminate_handler () from /usr/lib/libstdc++.so.6
#4  0xb77bc915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#5  0xb77bc94a in std::terminate () from /usr/lib/libstdc++.so.6
#6  0xb77bc95f in std::terminate () from /usr/lib/libstdc++.so.6
#7  0xb77bc418 in __cxa_call_unexpected () from /usr/lib/libstdc++.so.6
#8  0x0808fdf2 in ConnectionManager::Server::run (this=0x8585568) at client/ConnectionManager.cpp:260
#9  0x08168750 in Thread::starter (p=0x8585568) at Thread.h:130
#10 0xb7f4c341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb76804ee in clone () from /lib/tls/i686/cmov/libc.so.6

```

Did i compile it corretly in debug mode; i mean is this the info you need?

Thanks,
pete

---

### Post by stevensheehy on 2006-09-01
The cvs update from today changed the binary name and prefix path. Though you should always read the changelog when updating, I'll post part of it here since this is important:

```
2006-09-01 - Steven Sheehy
* Changed binary name and data path from ldcpp to linuxdcpp to satisfy package maintainers.
  !!IMPORTANT!! - run "scons -c install" to remove all the old files before compiling.
```

Thus, run "scons -c install" to delete the executable and any installed files. If you never ran scons install, you just need to run "scons -c".

This also means you should update your menu entries and any scripts to point to the new executable name.

---

### Post by stevensheehy on 2006-09-01
> **humansuit said:**
> Did i compile it corretly in debug mode; i mean is this the info you need?

Compiling in debug mode adds line numbers so I can see where it crashed. The backtrace shows it's crashing because of some socket issues but that should be completely unrelated to the issue with adding a shared folder. Ok, let's try a few things. First don't open up any tabs when you startup (so remove autoconnect stuff). Second, instead of running in gdb, run "ulimit -c unlimited" to enable coredumps. Then run ldcpp as normal. It will produce a coredump file when it crashes. Run "gdb --core=your.core.file ./ldcpp" then run "bt" and paste the backtrace here. Sometimes ldcpp has weird crashes when ran in gdb and connecting over sockets.

---

### Post by humansuit on 2006-09-01
Well, i removed all once again and reinstalled, but running linuxdcpp crashes exactly the same. 
```
terminate called after throwing an instance of 'SocketException'
Aborted.
```

I'm beginning to think there's something wrong with my systemwide GTK/glade/whatever-files.

---

### Post by humansuit on 2006-09-01
> **stevensheehy said:**
> Compiling in debug mode adds line numbers so I can see where it crashed. The backtrace shows it's crashing because of some socket issues but that should be completely unrelated to the issue with adding a shared folder. Ok, let's try a few things. First don't open up any tabs when you startup (so remove autoconnect stuff). Second, instead of running in gdb, run "ulimit -c unlimited" to enable coredumps. Then run ldcpp as normal. It will produce a coredump file when it crashes. Run "gdb --core=your.core.file ./ldcpp" then run "bt" and paste the backtrace here. Sometimes ldcpp has weird crashes when ran in gdb and connecting over sockets.

Sorry, I completely missed your second post. I don't have any tabs opening at startup so it's not it. Here's the backtrace from coredump.

```
(gdb) bt
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb763a9a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb763c2b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7819c1e in __gnu_cxx::__verbose_terminate_handler () from /usr/lib/libstdc++.so.6
#4  0xb7817915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#5  0xb781794a in std::terminate () from /usr/lib/libstdc++.so.6
#6  0xb781795f in std::terminate () from /usr/lib/libstdc++.so.6
#7  0xb7817418 in __cxa_call_unexpected () from /usr/lib/libstdc++.so.6
#8  0x0808fd3a in ConnectionManager::Server::run (this=0x85518f8) at client/ConnectionManager.cpp:260
#9  0x081685d8 in Thread::starter (p=0x85518f8) at Thread.h:130
#10 0xb7fa7341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb76db4ee in clone () from /lib/tls/i686/cmov/libc.so.6

```

---

### Post by stevensheehy on 2006-09-02
Open up client/ConnectionManager.cpp and scroll to line 260. Replace the while loop (e.g. lines 261-265) with this:
```
	try {
		while(!die) {
			if(sock.wait(POLL_TIMEOUT, Socket::WAIT_READ) == Socket::WAIT_READ) {
				ConnectionManager::getInstance()->accept(sock, secure);
			}
		}
	} catch(const SocketException&) { }
```

sock.wait() throws an exception but ConnectionManager::Server::run() is not supposed to throw any exceptions. Why this is at all related to adding a share, I have no idea.

---

### Post by humansuit on 2006-09-02
> **stevensheehy said:**
> Open up client/ConnectionManager.cpp and scroll to line 260. Replace the while loop (e.g. lines 261-265) with this:
```
	try {
		while(!die) {
			if(sock.wait(POLL_TIMEOUT, Socket::WAIT_READ) == Socket::WAIT_READ) {
				ConnectionManager::getInstance()->accept(sock, secure);
			}
		}
	} catch(const SocketException&) { }
```

sock.wait() throws an exception but ConnectionManager::Server::run() is not supposed to throw any exceptions. Why this is at all related to adding a share, I have no idea.

Heh, don't know either what was going on, but anyhow, that did the trick and no more crashes. Thank you very much for your help and keep up the good work!

Pete

---

### Post by naktekh on 2006-09-06
Looks great! I had no problems pulling the latest sources from CVS and compiling them. Fantastic job and this was a real help to me.

---

### Post by minj on 2006-09-10
I used ur advice from Ubuntu:Compiling Linux DCpp about running linuxdcpp in a different locale but I get this error:
```

(linuxdcpp:25489): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```

Is there any package I need to install? btw my locale is lt_LT

---

### Post by pebe on 2006-09-19
Thanks for improving the hash speed, hashes ~100% faster at best :) 

> **Oblong_Cheese said:**
> Under Dapper amd-k8 kernel (not that that should make a difference?), the download, compile and install works fine, I can run the programme fine, but it simply will not hash any files or generate a file list.

When I open ldcpp, in the statusbar is the message "Hashing failed: could not open file", irrespective of the file I have set it to hash; be it in my local directory or not.

Executing ldcpp under gksudo does not help either.

Does anyone know why this is happening

***Fixed!***

Turns out there's a bug in the 64-bit compile whereby ~/.dc++/HashData.dat isn't created. A simple # touch ~/.dc++/HashData.dat and ldcpp is on it's way!

Same problem with my 32-bit compile (tested with both dapper and edgy), "touch .dc++/hashData.dat" fixes it for me as well.

---

### Post by rebegin on 2006-09-21
hey,
i've followed your instrucions and everything is fine exept one important thing: i cannot search...though i can download from a user's file list, and the search is only showing that hint i've already have in my downloading queue.
i've got a router, but i've got port forwarding set up correctly too(i think), normaly it doesn't tell me any error, just doesn't search... 
but if i change the port numbers to others one(which aren't open) then i get tcp and upd error message in the terminal where i started the program.

anyway, is it posibble, to download with multiple line?

thanks in advance.

p.s.: sorry for my bad english

---

### Post by stevensheehy on 2006-09-21
> **rebegin said:**
> hey,
i've followed your instrucions and everything is fine exept one important thing: i cannot search...though i can download from a user's file list, and the search is only showing that hint i've already have in my downloading queue.
i've got a router, but i've got port forwarding set up correctly too(i think), normaly it doesn't tell me any error, just doesn't search... 
but if i change the port numbers to others one(which aren't open) then i get tcp and upd error message in the terminal where i started the program.

Searching requires a UDP port to be open. Make sure you have this set up correctly in your router and your firewall (if any). Read the [DC++ FAQ]("http://dcpp.net/faq/") to see how to poke through routers. You can always set it to passive if you can't get it to work. By the way, I have never seen a case where not being able to search was caused  by something other than user error. :)


> **rebegin said:**
> anyway, is it posibble, to download with multiple line?

Not sure what you're asking here.

---

### Post by janne5011 on 2006-09-28
First off all thanks for all work with Linudc++ and this How to:D.

Application works  but I want it to start without have terminal-window  open,
how is that done?

Edit:Im op in a hub, app crasched when I kicked a user "segmentation error"...

---

### Post by stevensheehy on 2006-09-28
> **janne5011 said:**
> Application works  but I want it to start without have terminal-window  open, how is that done?

Open it in nautilus and double click the executable or make a link to put on your desktop or make a menu etry or add to panel or... :)

> **janne5011 said:**
> Edit:Im op in a hub, app crasched when I kicked a user "segmentation error"...

Read the manual in the wiki on how to get backtraces and paste it here or open a bug on our site.

---

### Post by janne5011 on 2006-09-28
thanks crash occured only once, so maybe it was somethin else, I put errors here if I it occurs again - thanks for reply=)

---

### Post by Zaggy on 2006-10-08
Great work! LinuxDC++ looks slick and seems to work well!

---

### Post by Jellyffs on 2006-10-11
Looks fine for me. Currently hashing...

Thanks so much for making a descent dc++ client on linux !

---

### Post by Jellyffs on 2006-10-15
Hi,

Actually, I'm meeting a rather strange problem.

DC++ seems to have difficulties hashing some mp3 files.

For example, in a folder of 10Go of mp3, each albums contains .sfv .nfo .m3u and .mp3 of course.

Well the first three kind of files mentionned are all hashed perfectly. But 50-70% of the .mp3 files doesn't appear at the end in my share.

When DC++ start hashing these 10Go, it does show "10Go left" --> then "9Go left" etc..etc... But when it finished, I check my share and/or go through my filelist and realize that a huge amount of .mp3 files are missing.

Also I tried to compare the one it succeeded to hash and the others, but I don't see any difference between them... Same kind of TAG, same characters in the name ("**_ - )(**")...

Anyone meeting the same issue? (I didn't see any posted bug about it).

Anyone has an idea, or a test I could do to move on with this problem?

Thanks in advance.

Alex.

---

### Post by stevensheehy on 2006-10-16
DC++ does not add files to the list immediately after they're hashed. You have to manually refresh the list or wait for someone to download your list. There have also been cases in the past where if the files contain non-ASCII characters they might not show up in the share.

---

### Post by wolf202 on 2006-10-16
:) Great Guide, Submitted to [Wikitut.org]("http://www.wikitut.org")

[http://www.wikitut.org/index.php?title=How_to_Install_LinuxDC](http://www.wikitut.org/index.php?title=How_to_Install_LinuxDC)

-wolf

---

### Post by Jellyffs on 2006-10-16
> **stevensheehy said:**
> DC++ does not add files to the list immediately after they're hashed. You have to manually refresh the list or wait for someone to download your list. There have also been cases in the past where if the files contain non-ASCII characters they might not show up in the share.
Thanks for your reply.

I'm using it since a week or so. I did refresh it a few times. And actually, DC++ hash my files at each start up and also every 1 hour or so, concerning this particular folder. It seems DC++ notices that something is wrong with the current filelist available to users and the "real" amount of files that aren't there. So it restart hashing this folder (and only that one) every hour or so.

So I guess the theory of non-ASCII characters might be closer to the problem. So I compared two examples again, but don't see any difference... I'm a beginner though..

**Example of files (contained in one subfolder) that will appear correctly in share/filelist:**

00-asylum-dj_vibes-asy003-vinyl-1993-xtc.jpg
00-asylum-dj_vibes-asy003-vinyl-1993-xtc.m3u
00-asylum-dj_vibes-asy003-vinyl-1993-xtc.nfo
00-asylum-dj_vibes-asy003-vinyl-1993-xtc.sfv
a-dj_vibes-hey_dj-xtc.mp3
b-dj_vibes-get_high_(new_jack_london)-xtc.mp3

**Example of a subfolder that appears (subfolders always appear, it's only the .mp3 files inside it that are missing) but with the missing .mp3 files:**

aa-calyx-schitzoid-sour.mp3
a-calyx-morphology-sour.mp3

**In this same subfolder there's these following files, and they do appear:**

00-31_Records-Calyx-31R007-1999-sour.nfo
00-31_Records-Calyx-31R007-1999-sour.m3u
00-31_Records-Calyx-31R007-1999-sour.sfv


I really don't get it... O_o

Thanks again.

Alex.

---

### Post by stoft on 2006-10-17
> **Jellyffs said:**
> 
**Example of a subfolder that appears (subfolders always appear, it's only the .mp3 files inside it that are missing) but with the missing .mp3 files:**

aa-calyx-schitzoid-sour.mp3
a-calyx-morphology-sour.mp3


Have you checked to make sure they don't already exist in some other folder, iirc DC++ has an option to hide files that already exist in share (and a rough guess is that DC++ goes by TTH in these cases).

---

### Post by AdamWarlock on 2006-10-17
Isn't LinuxDC++ now available for Dapper using Automatix2?

---

### Post by Jellyffs on 2006-10-17
> **stoft said:**
> Have you checked to make sure they don't already exist in some other folder, iirc DC++ has an option to hide files that already exist in share (and a rough guess is that DC++ goes by TTH in these cases).
Could have been yes. But it's a folder of 30Go. And only 11Go appears.. so..

Thanks.

---

### Post by sefmars on 2006-10-20
cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login

does not work it gives me connection timeout


mars@XANPVKGDT2:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcpp
CVS password:
cvs [login aborted]: connect to cvs.linuxdcpp.berlios.de(195.37.77.137):2401 failed: Connection timed out


any ideear

---

### Post by LetsLinux on 2006-11-12
I have problems with the seach functions. I don't get any results. 

Do any of you know why this happends?

---

### Post by Jellyffs on 2006-11-12
you have a problem with your port forwarding apparently.

Have a look at any tutorial for any direct connect client out there. You'll find the problem.

---

### Post by bartbouter on 2006-11-14
Thnx for this howto. :-D 
I was looking for this to run on AMD64.

---

### Post by fw0127 on 2006-11-15
hi, I meet this problem when compile, how can it happen, I'am new to ubuntu:confused: 

linuxdcpp$ scons release=1 PREFIX=/usr/local
scons: Reading SConscript files ...
Checking for g++-4.0 >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
KeyError: 'debug':
  File "SConstruct", line 166:
    if env['debug']:
  File "/usr/lib/python2.4/site-packages/SCons/Environment.py", line 290:
    return self._dict[key]

---

### Post by stevensheehy on 2006-11-15
> **fw0127 said:**
> hi, I meet this problem when compile, how can it happen, I'am new to ubuntu:confused: 

linuxdcpp$ scons release=1 PREFIX=/usr/local
scons: Reading SConscript files ...
Checking for g++-4.0 >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
KeyError: 'debug':
  File "SConstruct", line 166:
    if env['debug']:
  File "/usr/lib/python2.4/site-packages/SCons/Environment.py", line 290:
    return self._dict[key]

Not sure why that happened to you, but I've modified the SConstruct code to be a bit more robust in its error checking. This should hopefully fix your problem once it's committed to cvs. Until then, you can always delete the offending lines from SConstruct. ;)

---

### Post by stokedfish on 2006-11-15
Great how-to, great client, great people on the IRC...thx for everything!  :)

---

### Post by Christmas on 2006-11-21
This works great, thank you, very well explained.

---

### Post by nbayiha on 2006-11-21
great how to really helpful
thanks dude

---

### Post by ciscosurfer on 2006-11-21
You could also use Automatix2 and have it installed in 20 seconds. :D

---

### Post by stokedfish on 2006-11-22
> **ciscosurfer said:**
> You could also use Automatix2 and have it installed in 20 seconds. :D

You could, but the automatix2 version is totally outdated!

I didn't manage to set up my ports properly with it, because some options in that dialog were missing. Now that I compiled the newest version from the source, it works like a charm.

Unless the automatix version doesn't get regularly updated in the future, I cannot recommend it!  ;)

---

### Post by ciscosurfer on 2006-11-22
The vesion that Autamatix2 puts out seems to work fine for me.

---

### Post by rokixz on 2006-11-23
error accessing 'file:///home/ubuntu/dc%2B%2B/Downloads': File not found

What does it mean ?

---

### Post by stevensheehy on 2006-11-30
> **rokixz said:**
> error accessing 'file:///home/ubuntu/dc%2B%2B/Downloads': File not found

What does it mean ?

It's debug output. It means you can ignore it or create that directory so it doesn't complain.

---

### Post by stevensheehy on 2006-12-04
```
2006-12-04 - Steven Sheehy
* Upgraded the DC++ core to 0.698:
	* The 0.691 core contains a security flaw so I recommend you upgrade ASAP.
	* Support for non-TTH files was removed (by DC++, so don't complain to us).
	* Added SSL support (thanks Mattias Webjörn Eriksson for some help with this).
		* OpenSSL is now a required dependency to build.
		* Added a "Security Certificates" page in the preferences dialog.
		* Added a TLS port entry in the "Connection" page.
	* Added "Ignore private messages from bots" option.
	* Added "Ignore private messages from the hub" option.
	* Added "Don't download files already in the queue" option.
	* Removed "Ignore private messages from offline users" option.
	* Removed "Only results with TTH root" option.
	* Lots of other bug fixes to get the core to compile on *nix.
```

LinuxDC++ now requires OpenSSL in order to compile:
```
sudo apt-get install libssl-dev
```
You may have to run scons --clean and/or delete the "build/" directory in order to get this update to compile.

---

### Post by Georadu on 2006-12-04
Can someone provide me the sources for version 0.689. I have installed the latest linuxdcpp and only after I have checked my network to see what clients they use, and most of them don't have TTH. Now I can't download form them so untill they upgrade I have to use old dc++ too.
If you have the sources for that version please send me a private message and I'll give you my e-mail address.
Thank you

---

### Post by NeoChaosX on 2006-12-08
So Steven, is there a page on the LDCPP site that gives an indication of how much needs to be done until an official release? I'm enjoying this program immensely (for the most part, it's superior to Valknut), but I'd love to have a release so I don't have keep hitting up CVS every week or so.

---

### Post by stevensheehy on 2006-12-09
> **NeoChaosX said:**
> So Steven, is there a page on the LDCPP site that gives an indication of how much needs to be done until an official release? I'm enjoying this program immensely (for the most part, it's superior to Valknut), but I'd love to have a release so I don't have keep hitting up CVS every week or so.

* Fix download queue
* Add translations
* Fix character encodings
* Other small fixes

---

### Post by jocko on 2006-12-09
I have a problem that started a few days ago after updating to the latest cvs build. When I try to download files, they start to download, but I get disconnected after a few seconds (disconnected from the user, not from the hub).

Does anyone recognize this problem?
Any known fixes?
Is there any way to downgrade to an earlier version to see if that would help?

[COLOR=Red]Edit:[/COLOR] I found the solution myself... Managed to downgrade by "cvs update -D 20061101". Then I got error messages instead of "disconnected", turned out my disk was full:). Deleted some files and got it working. I'm stupid.

---

### Post by dutchmega on 2006-12-09
I'm waiting for multisource-downloading-support. Without it, downloading just goes too slow. There are enough ports in Windows that support this...

---

### Post by wilberfan on 2006-12-09
Thanks for this invaluable guide! (I'm running the latest build now...)  However, I've got near 100% CPU while running (I saw the comment about NOT sorting the user list--but I have no idea how to turn that off...)

Plus, my nick is blue--which confuses me a little... I've got my ports forwarded, etc...

---

### Post by stevensheehy on 2006-12-10
> **wilberfan said:**
> Thanks for this invaluable guide! (I'm running the latest build now...)  However, I've got near 100% CPU while running (I saw the comment about NOT sorting the user list--but I have no idea how to turn that off...)

Plus, my nick is blue--which confuses me a little... I've got my ports forwarded, etc...

100% cpu usage occurs when loading very large hubs. We're trying to come up with a solution (patches welcome).

Blue icon means you're a DC++ user, green non-DC++ user. Firewall in front of either are passive users.

---

### Post by stevensheehy on 2006-12-10
> **dutchmega said:**
> I'm waiting for multisource-downloading-support. Without it, downloading just goes too slow. There are enough ports in Windows that support this...

[http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_FAQ](http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_FAQ)

---

### Post by dutchmega on 2006-12-13
> **stevensheehy said:**
> [http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_FAQ](http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_FAQ)
Yes, I saw that but considering it's all open-source, I hoped there would be a port. :(

---

### Post by Tine on 2006-12-19
I know that nmdc-style file listing support is removed from dc++ but can someone make a patch or something so i can compile dc++ with that old filelist support included. 
I would appreciate that, because in our lan-hub(the one and only hub i can use) there are several users with these 0.401 version and there is now way on earth i can convince them all to upgrade. 

-Tine

---

### Post by stokedfish on 2007-01-03
Is the linuxdc++ page down? Why? What happened? :(

---

### Post by stoft on 2007-01-04
> **stokedfish said:**
> Is the linuxdc++ page down? Why? What happened? :(

Quick guess, Berlios.de is down, not just linuxdc++.

---

### Post by stevensheehy on 2007-01-04
> **stoft said:**
> Quick guess, Berlios.de is down, not just linuxdc++.

Exactly. We may have to switch soon if this keeps up.

You can access the cvs and the [mailing list]("https://lists.berlios.de/pipermail/linuxdcpp-developers/") still.

---

### Post by stokedfish on 2007-01-11
Soo...what's up with berlios?   :-?

---

### Post by stokedfish on 2007-01-13
:(

---

### Post by stokedfish on 2007-01-14
It's back!  :)

---

### Post by gav616 on 2007-01-16
is there any recomended settings? 
is dropping ok to use.?..

---

### Post by stokedfish on 2007-01-17
steven, 3 questions:

1. why don't you work together with the guys who try to port apexdc to linux?

joined forces could speed up things, no? uhm...

2. why do right-click commands not work?

I enabled the "accept commands" option and I also get a message...

freshstuff - [http://lawmaker.no-ip.org/forum/forum.php?id=11](http://lawmaker.no-ip.org/forum/forum.php?id=11) - sends me like 175 right-click commands when I connect to our hub, but then, when I right-click on the user "fresh" (the bot) no menu appears...on windows dc++ this works just fine!

3. will the remaining right-click menus ever be implemented?

(dc++ on windows has way more options when you right-click on something)

---

### Post by stevensheehy on 2007-01-18
> **stokedfish said:**
> steven, 3 questions:

1. why don't you work together with the guys who try to port apexdc to linux?

joined forces could speed up things, no? uhm...

We use the default DC++ core, not the StrongDC++ core. This factor will not change. Instead, the StrongDC++ guys should try to get their changes into the DC++ core.

> **stokedfish said:**
> 2. why do right-click commands not work?

I enabled the "accept commands" option and I also get a message...

freshstuff - [http://lawmaker.no-ip.org/forum/forum.php?id=11](http://lawmaker.no-ip.org/forum/forum.php?id=11) - sends me like 175 right-click commands when I connect to our hub, but then, when I right-click on the user "fresh" (the bot) no menu appears...on windows dc++ this works just fine!

a) it's not implemented. b) I don't care about such a feature so someone else will have to send a patch.

> **stokedfish said:**
> 3. will the remaining right-click menus ever be implemented?

(dc++ on windows has way more options when you right-click on something)

Only if they make sense. There is such a thing as [feature creep]("http://en.wikipedia.org/wiki/Feature_creep").

---

### Post by stokedfish on 2007-01-19
tons of hubs use bots with right-click commands out there and you don't want to support them?

wtf dude...

so linuxdc++ will just be another poor and incomplete dc client for linux.

I thought we had enough of them already, no need for one more - guess I'll pass then...

---

### Post by sultanoswing on 2007-01-19
A word of support, Stephen. Your port of DC++ is the best I've found fpr *nix (stokedfish, if you know of something better, I'm all ears).

Yes, it remains a work in progress, in particular I can't connect to older-cored clients in the 0.698 cored versions (a DC++ core bug/feature, I suspect), however, keep up the good work, fellas!

---

### Post by stevensheehy on 2007-01-19
> **stokedfish said:**
> tons of hubs use bots with right-click commands out there and you don't want to support them?

wtf dude...

so linuxdc++ will just be another poor and incomplete dc client for linux.

I thought we had enough of them already, no need for one more - guess I'll pass then...

What part of "someone else will have to send a patch" do you not understand? I am not here to service your every need, I do this on my free time. I don't really know why I bothered answering such a rude person.

---

### Post by stokedfish on 2007-01-20
Yeah, sorry. Yesterday definitely wasn't my day...didn't mean! :\

---

### Post by D!mon on 2007-01-22
sorry if this question is duplicated - have no time to read all pages;
Can I create .deb package somehow? Something like checkinstall with make?
Thx

---

### Post by stokedfish on 2007-01-22
> **sultanoswing said:**
> Yes, it remains a work in progress, in particular I can't connect to older-cored clients in the 0.698 cored versions (a DC++ core bug/feature, I suspect), however, keep up the good work, fellas!
I just browsed a DC++ 0.691 user without a problem.

---

### Post by ovidescu on 2007-01-23
I just installed LinuxDC++ and I must say I am impressed. It looks as if I'm actually running DC++ win32 version. Great job stevensheehy and keep up the good work. =D>

---

### Post by stevensheehy on 2007-01-27
> **ovidescu said:**
> I just installed LinuxDC++ and I must say I am impressed. It looks as if I'm actually running DC++ win32 version. Great job stevensheehy and keep up the good work. =D>

If you're impressed now, just wait until the next update. It'll be the best update ever, in my opinion. :)

---

### Post by Poka64 on 2007-01-27
Oh, great steven, the much anticipated Unicode update :)

---

### Post by stokedfish on 2007-01-30
Hmm, what's Unicode good for? So far, whenever I tried sth connected to Unicode it didn't work...for instance, setting both nicotine and gaim to utf-8 gave me wrong ö, ä, ü and other umlauts. So what advantage will the "much anticipated" (?) Unicode update bring with it? Uhm... *wonders*

---

### Post by stevensheehy on 2007-01-30
> **stokedfish said:**
> Hmm, what's Unicode good for? So far, whenever I tried sth connected to Unicode it didn't work...for instance, setting both nicotine and gaim to utf-8 gave me wrong ö, ä, ü and other umlauts. So what advantage will the "much anticipated" (?) Unicode update bring with it? Uhm... *wonders*

I would answer your question, but you've already proven previously you don't deserve to be answered.

---

### Post by Enigmatic on 2007-02-03
Is anyone else having trouble with hublists? It will download and say the download is finished, but nothing ever appears in the window.

---

### Post by ovidescu on 2007-02-03
> **Enigmatic said:**
> Is anyone else having trouble with hublists? It will download and say the download is finished, but nothing ever appears in the window.

My installation works just fine, hublists and all...

---

### Post by Enigmatic on 2007-02-03
Strange. I didn't install from this thread but the older thread, but I should still end up with the same thing as the packages have been updated since then.

---

### Post by Jellyffs on 2007-02-04
Many hublist are down. Try that one:

[http://dchublist.com/hublist.xml.bz2](http://dchublist.com/hublist.xml.bz2)

Alex.

---

### Post by Enigmatic on 2007-02-04
Nice, that one worked.

---

### Post by janfsd on 2007-02-05
Hi, thanks for the work you are making...
I've got a question, how does "/away" work? Is it not supposed to auto answer anybody that writes me a pm? Nothing like this happens, so I am wondering if it is like this that it should work.

---

### Post by NeoChaosX on 2007-02-05
Yesterday's update = good job Steven. 

> **stevensheehy said:**
> * Fix download queue
* Add translations
* Fix character encodings
* Other small fixes

So, that's item #3 down. Dunno about #1 (although the latest changelog mentions at least one fix for the queue), so I'm guessing most of the work left is translation?

---

### Post by stevensheehy on 2007-02-05
> **NeoChaosX said:**
> Yesterday's update = good job Steven. 

So, that's item #3 down. Dunno about #1 (although the latest changelog mentions at least one fix for the queue), so I'm guessing most of the work left is translation?

Everything is done except translations and any new bugs that might pop up between now and a release.

---

### Post by stevensheehy on 2007-02-05
> **janfsd said:**
> Hi, thanks for the work you are making...
I've got a question, how does "/away" work? Is it not supposed to auto answer anybody that writes me a pm? Nothing like this happens, so I am wondering if it is like this that it should work.

It doesn't auto-respond. It should in pm, but it hasn't been implemented yet.

---

### Post by janfsd on 2007-02-06
Thanks for answering Steven, that answered my doubts. By the way, great release!

---

### Post by gholen on 2007-02-06
The HOWTO is really good, but I'm having one bg problem. The pakage "scons" does not exist anymore. What should I do?

---

### Post by NeoChaosX on 2007-02-07
> **gholen said:**
> The HOWTO is really good, but I'm having one bg problem. The pakage "scons" does not exist anymore. What should I do?

It's in main for all Ubuntu distros. Are you sure you have it installed?

---

### Post by platinummonkey on 2007-02-10
um, im not sure if anyone else has had this problem but whenever i try to launch ldcpp it always just runs taking up all my swap and ram until they almost reach 100% but i always kill the process before that happens... x.x  I just recently upgraded to edgy with a fresh install, and i also have beryl running. I used to have ldcpp on dapper that worked great :P, but i cant seem to get it to work anymore on edgy. Ive followed the instructions exactly, and ive definetly made sure i have the necessary packages, but it nevers works x.x

any help would be much appreciated,
platinummonkey

---

### Post by maloki on 2007-02-13
Switched from widows to Linux some time ago, and i got to say this is definitely a worthy replacement for DC++.

I salute you for your work.

---

### Post by Jellyffs on 2007-02-13
@platinummonkey

Submit this issue on IRC:  #linuxdcpp on freenode channel. It will be easier to sort out the pb for the developers.

Alex.

---

### Post by stevensheehy on 2007-02-13
> **Jellyffs said:**
> @platinummonkey

Submit this issue on IRC:  #linuxdcpp on freenode channel. It will be easier to sort out the pb for the developers.

Alex.

Actually it's #linuxdc++. But anyways, I'm a developer and have no idea why he has those issues. Might try seeing if it does it when using metacity instead of beryl. I also saw this problem before when Assistive Technology Support was enabled on Edgy, but I don't see where Dapper has ATS so... Might also want to try starting ldcpp with a new profile (~/.dc++).

---

### Post by Hero_boy on 2007-02-24
Thank you stevensheehy!

I was previously struggling along with Valknut. It would install correctly, hash files OK & connect to servers fine - but after a short while of my downloads running _they would all just stop._

Furthermore users trying to connect to me would receive the error* "DC Client does not fully support TTH"* - I don't even know what that is!

Anyway I found your thread and followed it step by step. The program deployed correctly & works great, it's also more ascetically pleasing to the eye.

Cheers :)

---

### Post by 4tro on 2007-02-24
i'm having a weird issue starting LinuxDCPP.
every time i start ldcpp a terminal starts and when i close it my linuxdcpp will close as well, though i expected ldcpp to stop when i close that terminal, it shouldn't show up in the first place in my opinion, just updated the source a few minutes ago.

---

### Post by stokedfish on 2007-03-14
Any help with translations needed? German? Uhm...

---

### Post by gav616 on 2007-03-16
whats happening about adc?

[http://en.wikipedia.org/wiki/Direct_Connect_(file_sharing)#Protocol](http://en.wikipedia.org/wiki/Direct_Connect_(file_sharing)#Protocol)

---

### Post by stevensheehy on 2007-03-16
> **stokedfish said:**
> Any help with translations needed? German? Uhm...

Yes, we will definitely need help. Unfortunately, I'm still trying to add translation support to the code. The dcpp core is a major source of headache since it will not work with gettext without major modifications. I will post to ldcpp's mailing list asking for translations when it is ready.

[QUOTE=gav616]whats happening about adc?

[http://en.wikipedia.org/wiki/Direct_...ring)#Protocol](http://en.wikipedia.org/wiki/Direct_...ring)#Protocol)[/QUOTE]

ADC is implemented and fully working in DC++ (and thus LinuxDC++). There's only a handful of actual hubs that run ADC, though (check out the ADC specific public hub list).

---

### Post by obbe on 2007-03-17
hi guys, I use the last version of linuxdc++ but i've a problem.. many users can't download a few of my files, the upload-bar stand to Connecting and upload doesn't start, i've open all dc++ ports on firewall and try to use the passive mode but nothing happen;  i've noticed that the same users can download only a few of my files but not others.. anyone have this problem?

---

### Post by naseem on 2007-03-22
hy I'm on feisty cannot find this AST (my menu is in italian, but nothing even similar to that) where should I loock for it, and what happens when I swich it of (just in case I'll find it)

ok found it where it was supposed to be

---

### Post by stoft on 2007-04-11
I was playing around with python the other night and I ended up writing a share checker/searcher script (for checking/searching your own share), anyone have an idea where I could possibly publish it? (some forum, wiki or something for example) In case someone else might like to use it as well?

Steve and the others, thanks for the great work, keep it up!

---

### Post by stevensheehy on 2007-04-12
> **stoft said:**
> I was playing around with python the other night and I ended up writing a share checker/searcher script (for checking/searching your own share), anyone have an idea where I could possibly publish it? (some forum, wiki or something for example) In case someone else might like to use it as well?

Steve and the others, thanks for the great work, keep it up!

You can send it to our mailing list, if you'd like (the list allows sending without having to register first). You can also post it here in this thread (in a code iframe).

---

### Post by stoft on 2007-04-13
> **stevensheehy said:**
> You can send it to our mailing list, if you'd like (the list allows sending without having to register first). You can also post it here in this thread (in a code iframe).

By the list you mean the developer's list accessible through berlios?

Constructive criticism greatly appreciated. This code is probably not very pythonesque (nor efficient) but it was fun fiddling with. The script either traverses the sharelist xml or the filesystem (for historical reasons mostly, using 'find'). Save to e.g. sharecheck.py and run: ./sharecheck.py --help

```

#!/usr/bin/python

# Copyright (C) 2007 Rasmus Larsson 
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# Read the full license agreement here: http://www.gnu.org/licenses/gpl.txt

import os, sys, getopt, bz2, fnmatch
from xml.dom import minidom

DEFSEARCHSTRS = ['Descript.ion','thumbs.db','*.html','*.htm','*.msg','*.permissions','*.pls','*.status','*.url','*.filled','*.debug','*.ccd','*.ioFTPD*','*.banana','*.bad','*.checked','*.raidenftpd.acl','*.SimSfvChk.log','*.message','*.upChk.log','*.crc','imdb.nfo','*.bc!','*(1).nfo','*(2).nfo','*(3).nfo','*.log','*.pls','*.dctmp','*(1).sfv','*.ini','*.bak','*(2).sfv','*.dt!','*.bat','*.ink','*missing','*.antifrag']

#DEFSEARCHSTRS= ['*.srt','*.sub','*.idx'] #removed
DEFSOURCE="bz2"
DCCONFFILE='~/.dc++/DCPlusPlus.xml'
DCSHAREFILE='~/.dc++/files.xml.bz2'

class DCFileHandler:
	""" Opens the DC++ config file and share list file. """
	def __init__(self, configfile='~/.dc++/DCPlusPlus.xml', sharelistfile='~/.dc++/files.xml.bz2'):
		"""
		configfile -- location and name of configfile relative to the userdirectory, default is ~/.dc++/DCPlusPlus.xml
		sharelistfile -- location and name of the sharelistfile relative to the userdirectory, default is ~/.dc++/files.xml.bz2
		"""
		self.xmldirlist = self.extractShareDirectories(configfile)
		self.xmlsharelist = self.extractSharelist(sharelistfile)

	def expandUserDir(self, string):
		if(string[0]=='~'): return os.path.expanduser(string)
		else: return string

	def extractShareDirectories(self, configfile):
		"""Extract the share directories from DCPlusPlus.xml"""
		try:
			fsock_conf = file(self.expandUserDir(configfile))
			xmldoc = minidom.parse(fsock_conf)
			fsock_conf.close()
			return xmldoc
		except IOError:
			print IOError
			sys.exit(2)

	def extractSharelist(self, sharelistfile):
		try:
			fsock_share = bz2.BZ2File(self.expandUserDir(sharelistfile))
			xmlsharelist = minidom.parse(fsock_share)
			fsock_share.close()
			return xmlsharelist
		except IOError:
			print IOError
			sys.exit(2)

class DCAnalyzer:
	def __init__(self, dcfh):
		self.dcfilehandler = dcfh
		self.createDirMap()

	def lookupShareDirPath(self, dirname):
		"""Lookup the complete path (dir included) of a directory."""
		return self.dirmap[dirname]

	def createDirMap(self):
		sharedirlist = self.dcfilehandler.xmldirlist.getElementsByTagName('Share') #parametrize?
		firstref = sharedirlist[0]
		dirlist = firstref.getElementsByTagName('Directory') #parametrize?
		self.dirmap = {} 
		for dir in dirlist:
			self.dirmap[ dir.attributes['Virtual'].value ] = dir.firstChild.data 

	def search(self, searchstrings, source="bz2"):
		"""
		searchstrings -- list of search strings to look for
		source -- where to look for the files, in the share list ("bz2", default) or in the file system ("fs")
		"""
		if(source == "bz2"):
			return self.searchbz2(searchstrings)
		elif(source == "fs"):
			return self.searchfs(searchstrings)
		else:
			raise Error, source + " is an unknown source"

	def searchfs(self, searchstrings):
		""" Search the share directories (using unix 'find') for files matchin search strings.
		searchstrings -- list of search strings
		"""
		print "Searching filesystem...\n\n"
		print 'Search strings are: ' 
		print searchstrings

		print 'Share directories are:'
		for key in self.dirmap:
			#print var.firstChild.data
			print self.dirmap[key]
		print "\n"
		
		files=[]
		for key in self.dirmap:
			for str in searchstrings: 
				cmd = 'find ' + self.dirmap[key] + ' -name \'' + str  + '\' -print' 
				o = os.popen(cmd)
				foo = o.read()
				if ( len(foo) > 0 ):
					files.append(foo)
		return files

	def searchbz2(self, searchstrings):
		print "Searching sharelist...\n\n"
		files=[]
		foundElements=[]
		filelist = self.dcfilehandler.xmlsharelist.getElementsByTagName('File') #parametrize?
		for elementFile in filelist:
			for pattern in searchstrings:
				filename = elementFile.attributes['Name'].value
				if (fnmatch.fnmatch(filename,pattern)):
					foundElements.append(elementFile)
		
		for element in foundElements:
			pnames=[]
			parents = self.recurseParents(element.parentNode, 'Directory') #parametrize?
			for pelement in parents:
				pnames.append(pelement.attributes['Name'].value)		
							
			path = self.lookupShareDirPath(pnames.pop(0))
			for pname in pnames:
				path += pname + "/"
			path += element.attributes['Name'].value
			files.append( path )
		
		return files	

	def recurseParents(self, parent, name):
		"""Recurses the parent and all its parents having 'name' and returns a list of them."""
		list=[]
		if (parent.parentNode is not None
			and parent.parentNode.nodeName == name):
			list.extend(self.recurseParents(parent.parentNode, name))
		list.append(parent)
		return list

def getArgs():
	"""Gets the input arguments if there are any."""
	myArgs={}
	searchstrings = [] 
	configfile=None
	sharelistfile=None
	source=None
	try:
		opts, args = getopt.getopt(sys.argv[1:], "he:f:s:", ["help","pattern=","configfile=","sharelistfile="])
	except getopt.GetoptError:
		usage()
		exit(2)
	for opt, arg in opts:
		if opt in ("-h", "--help"):
			usage()
			sys.exit(2)
		elif opt in ("-e", "--pattern"):
			searchstrings.append(arg)
		elif opt in ("-c", "--configfile"):
			configfile=arg
		elif opt in ("-f","--sharelistfile"):
			sharelistfile=arg
		elif opt in ("-s","--source"):
			source=arg
			
	if(len(searchstrings) == 0):
		searchstrings = None
	myArgs["sharelistfile"]=sharelistfile
	myArgs["configfile"]=configfile
	myArgs["searchstrings"]=searchstrings
	myArgs["source"]=source
	return myArgs

def usage():
	"""Prints the correct usage of the program"""
	print "This program searches your linuxdc++ share for files with specified search pattern.\
		\nIt may work on windows as well, but I haven't tried."
	print "Usage:\tsharecheck.py [-h|-e PATTERN*|-c FILEPATH|-f FILEPATH|-s SOURCE] -e\n\t-h, --help shows this help \
		\n\t-e, --pattern=[PATTERN] use PATTERN as search expression \
		\n\t-c, --configfile=[FILEPATH] use FILEPATH file as DC++ config file, default is ~/.dc++/DCPlusPlus.xml \
		\n\t-f, --sharelist=[FILEPATH] use FILEPATH file as DC++ sharelist file, default is ~/.dc++/files.xml.bz2 \
		\n\t-s, --source=[SOURCE] look in SOURCE ('bz2'|'fs') (sharelist or filesystem) for files, default is bz2\
		\n\nNotes: \
		\n\t- Search is performed using fnmatch syntax. 'man fnmatch' for details.\
		\n\t- more than one search pattern is permitted.\
		\n\nExample: \
		\n\t./sharecheck.py -e imdb.* -e Thumbs* -s fs\n\n "

def run():
	myArgs = getArgs()
	searchstrings = DEFSEARCHSTRS
	configfile = DCCONFFILE
	sharelistfile = DCSHAREFILE
	source = DEFSOURCE
	if(myArgs["searchstrings"] is not None):
		searchstrings = myArgs["searchstrings"]
	if(myArgs["configfile"] is not None):
		configfile = myArgs["configfile"]
	if(myArgs["sharelistfile"] is not None):
		sharelistfile = myArgs["sharelistfile"]
	if(myArgs["source"] is not None):
		source = myArgs["source"]
	dcfh = DCFileHandler(configfile, sharelistfile)
	dca = DCAnalyzer(dcfh)
	list = dca.search(searchstrings, source)
	for l in list:
		print l

run()



```

---

### Post by mrmodin on 2007-04-15
Really good job there, thanks alot =)

---

### Post by stokedfish on 2007-04-25
Will there ever be a core/gui seperation in linuxdcpp?

It's the thing I miss the most...

Museek has it - [http://museek-plus.org/](http://museek-plus.org/) - but that's a slsk client...

I can ssh into my server, start museekd (the core) in a screen session (without x) and detach it, end my ssh session and the core will keep on running. It's genius! When I want to search files or chat I just connect to the core on my notebook with the QT, GTK or ncurses GUI.

That's why my slsk is on almost 24/7 but I rarely ever use LinuxDC++ anymore.

Soo...any chance that there will be a core/gui seperation any time soon?

---

### Post by Znupi on 2007-04-25
On the first command (sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev) it says it has to download 92.7MB to my harddisk. Is that normal? I'm a valknut user and it only uses like 12MBs, but I don't quite like it and LinuxDC++ sounds much better... but 92.7MB seems a bit high...

---

### Post by stoft on 2007-04-25
> **Znupi said:**
> On the first command (sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev) it says it has to download 92.7MB to my harddisk. Is that normal? I'm a valknut user and it only uses like 12MBs, but I don't quite like it and LinuxDC++ sounds much better... but 92.7MB seems a bit high...

Those are not linuxdc++, but other libraries linuxdc++ uses (build environment, header files and so forth) and probably contain a whole lot more than just what is used by linuxdc++. I'm not sure how big they are together but it doesn't sound way off with ~90MB. The source files for linuxdc++ itself are around 11MB in total.

---

### Post by Bapman on 2007-04-28
Hi,

 I am a user of linuxdcpp and it works great for me ! But I have some little problems :
- the icon in the task bar is not transparent (there is a white frame on it whereas the .png is really transparent)
- the number of search results seems to be limited (around 60-70) but it seems to be wanted by the protocol : I am the admin of the hub (ptokax) but I don't see any option to change it.
- the search engine does not work very well with accents (I am french) : when you search for "vidéo", it should be able to return files with a name containing "video" !

Again, thanks for all the work done here !

---

### Post by stevensheehy on 2007-04-28
> **stokedfish]Will there ever be a core/gui seperation in linuxdcpp?[/QUOTE]

[http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Todo](http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Todo)
See 6th bullet down. Gonna be awhile, though.

[QUOTE=Znupi said:**
> On the first command (sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev) it says it has to download 92.7MB to my harddisk. Is that normal? I'm a valknut user and it only uses like 12MBs, but I don't quite like it and LinuxDC++ sounds much better... but 92.7MB seems a bit high...

It's only because you're compiling from source and don't already have the compiler tools and other libraries. You need most of these anyway if you're every going to compile anything else on Ubuntu.

[QUOTE=stokedfish]The source files for linuxdc++ itself are around 11MB in total.[/QUOTE]

The source is 2.3 MB. ~340KB if compressed.

---

### Post by stevensheehy on 2007-04-28
> **Bapman said:**
> - the icon in the task bar is not transparent (there is a white frame on it whereas the .png is really transparent)

The task bar icon shows up fine for me. If it doesn't show transparent for you, it is an issue with either your system. If, however, you mean the system/task tray instead of the task bar, then that is a known problem.

> **Bapman said:**
> - the number of search results seems to be limited (around 60-70) but it seems to be wanted by the protocol : I am the admin of the hub (ptokax) but I don't see any option to change it.

There is no such limit in linuxdcpp, the problem lies elsewhere.

> **Bapman said:**
> - the search engine does not work very well with accents (I am french) : when you search for "vidéo", it should be able to return files with a name containing "video" !

Make sure you have the encoding set properly. The NMDC protocol does not specify a text encoding, so you have to manually set it yourself. Go into Preferences and change your "Default Hub Encoding". You can also change it per-hub on the favorite hubs tab.

---

### Post by stevensheehy on 2007-04-28
By the way, I need someone to test if this guide works on Feisty. I'm probably not going to be upgrading for awhile (if at all), so I need someone else to test. Thanks.

---

### Post by janfsd on 2007-04-28
> **stevensheehy said:**
> By the way, I need someone to test if this guide works on Feisty. I'm probably not going to be upgrading for awhile (if at all), so I need someone else to test. Thanks.

It worked for me in Feisty.

---

### Post by Bapman on 2007-04-28
Thanks a lot Stevensheehy for your answers ! And yes, I meant the system/task tray in fact for the icon problem (it's where gaim or the sound volume is docked for example).
And like janfsd, it works great for me under feisty ! No need to update the how-to :D

---

### Post by darkdays on 2007-05-01
Thank you! Followed the guide and it was all smooth sailing. No issues at all with the app so far.

---

### Post by Znupi on 2007-05-02
Same here, everything's smooth, was worried about download time but it seems Linux connects to some server from my country (Romania) from which it downloaded the files needed pretty quick (under 1 min?) (i'm talking about the first set of packages, needed to build LinuxDC++)... Linux just keeps amazing me...

---

### Post by sssbbb on 2007-05-07
thanks a lot for the howto!  up and running with no problems.

---

### Post by ovidescu on 2007-05-11
> **stevensheehy said:**
> By the way, I need someone to test if this guide works on Feisty. I'm probably not going to be upgrading for awhile (if at all), so I need someone else to test. Thanks.

Hi

I had linuxDC++ v0.698 installed back when I was on edgy. I recently updated to feisty and I can still use linuxdcpp same way as in edgy. So once again, good work Steven.

BTW, is there a more recent version and if so, how can I update ?

---

### Post by stevensheehy on 2007-05-12
> **ovidescu said:**
> Hi

I had linuxDC++ v0.698 installed back when I was on edgy. I recently updated to feisty and I can still use linuxdcpp same way as in edgy. So once again, good work Steven.

BTW, is there a more recent version and if so, how can I update ?

0.698 is the version of the dc++ core, not linuxdc++. We have yet to make a release, so we're going by cvs date at the moment. Check your Changelog.txt to see if it is older than the newest date in the changelog linked at [http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index). If it is, follow the update instructions on the first page of this howto. cheers

---

### Post by dngpng on 2007-05-14
I installed it on a friends laptop and I found out the installation script didn't create /usr/local/share/linuxdcpp, which caused a segment fault when launching the app from a location other than the source dir. (From the error message, I noticed it tried to use files in the dir. mentioned above)

Then I update my installation and did a scons -c install, and all the stuff under /usr/local/share/linuxdcpp/pixmaps and /usr/local/share/linuxdcpp/glade/ were automatically deleted. Then I ran into the same problem.  I had to link those file from the source dir. to make it work again.

Don't know if it's a bug or what.

---

### Post by jlbiasini on 2007-05-15
It works fine but only if I launch it as root (or sudo) ... Is it dangerous to do so ?

---

### Post by stevensheehy on 2007-05-15
> **jlbiasini said:**
> It works fine but only if I launch it as root (or sudo) ... Is it dangerous to do so ?

Do not launch linuxdcpp as root, it is not tested for such escalated privileges. You must not have followed the instructions on the howto exactly. I would guess that you ran both scons and scons install with sudo. You should only run scons install as root.

---

### Post by stevensheehy on 2007-05-15
> **dngpng said:**
> I installed it on a friends laptop and I found out the installation script didn't create /usr/local/share/linuxdcpp, which caused a segment fault when launching the app from a location other than the source dir. (From the error message, I noticed it tried to use files in the dir. mentioned above)

Then I update my installation and did a scons -c install, and all the stuff under /usr/local/share/linuxdcpp/pixmaps and /usr/local/share/linuxdcpp/glade/ were automatically deleted. Then I ran into the same problem.  I had to link those file from the source dir. to make it work again.

Don't know if it's a bug or what.

Sounds like you also didn't follow the howto exactly. You run scons to compile and link it, then sudo scons install to copy the executable, pixmaps and glade files to /usr/local/. You have to have root access in order to create /usr/local/share/linuxdcpp and add files to it, hence the sudo.

---

### Post by jlbiasini on 2007-05-16
That's wright ! I had made both "scons" and "scons install" as root 

but I just made a new install of linuxdcpp with only "scons install" as root and that's the same : it works only if launch as root (even "sudo linuxdcpp" don't works

It hang just after connection scaning of the network. Here are the output from console :

```

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

** ERROR **: file gailtreeview.c: line 3723 (traverse_cells): assertion failed: (row_path != NULL)
```

---

### Post by dngpng on 2007-05-16
> **stevensheehy said:**
> Sounds like you also didn't follow the howto exactly. You run scons to compile and link it, then sudo scons install to copy the executable, pixmaps and glade files to /usr/local/. You have to have root access in order to create /usr/local/share/linuxdcpp and add files to it, hence the sudo.

Thanks for the reply and very sorry for omitting the tiny but important "sudo" ;)

---

### Post by stevensheehy on 2007-05-17
> **jlbiasini said:**
> That's wright ! I had made both "scons" and "scons install" as root 

but I just made a new install of linuxdcpp with only "scons install" as root and that's the same : it works only if launch as root (even "sudo linuxdcpp" don't works

It hang just after connection scaning of the network. Here are the output from console :

```

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:15558): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

** ERROR **: file gailtreeview.c: line 3723 (traverse_cells): assertion failed: (row_path != NULL)
```

Try installing again one more time, but delete all your previous installed files ("scons -c" and "sudo scons -c install", but doublecheck the files just to confirm they are gone from your prefix).

What worries me is that last error about the gailtreeview. I've seen other people complain about it before and I am not entirely sure what causes it. See [http://developer.berlios.de/bugs/?func=detailbug&bug_id=11002&group_id=2230](http://developer.berlios.de/bugs/?func=detailbug&bug_id=11002&group_id=2230) for the latest complaint about it and my response.

---

### Post by stevensheehy on 2007-05-17
> **dngpng said:**
> Thanks for the reply and very sorry for omitting the tiny but important "sudo" ;)

No worries. We all make mistakes.

---

### Post by jlbiasini on 2007-05-17
Thanls for your help ! :)

unfortunatly it still don't works. I've just réinstall everything and also deleted all linuxdcpp folder but it don't works. When connecting as root the scan for other user and their sharing files is nearly immediate, when running the program as user it takes 10 seconds more to catch the informations and finally hang at the end of it:

```
(linuxdcpp:8914): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:8914): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:8914): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:8914): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

** ERROR **: file gailtreeview.c: line 3723 (traverse_cells): assertion failed: (row_path != NULL)
aborting...
Abandon (core dumped)
```

---

### Post by jlbiasini on 2007-05-17
Ok shame on me ... I just forget to put AST off
actually I've done it but it need a reboot to occurs 

thank you so much :)

---

### Post by prosamantha on 2007-05-22
and if that one wont work then try the [www.hublist.co.uk](www.hublist.co.uk) one 
public hublist address
For DC++ clients newer than 0.4033 use
[http://www.hublist.co.uk/hublist.xml.bz2](http://www.hublist.co.uk/hublist.xml.bz2)

For older DC client
[http://www.hublist.co.uk/hublist.config.bz2](http://www.hublist.co.uk/hublist.config.bz2)

---

### Post by fridaythe14th on 2007-05-24
Thanks for a great port Steven. It has improved greatly since you got involved.

When in port forward mode I can't search. Starting linuxdcpp from the terminal I get these lines:
> Thrown: SocketException: Permission denied
Bind failed, retrying with INADDR_ANY: SocketException: Permission denied
Thrown: SocketException: Permission denied
StartSocket (tcp): Caught "SocketException: Permission denied"
Thrown: SocketException: Permission denied
Bind failed, retrying with INADDR_ANY: SocketException: Permission denied
Thrown: SocketException: Permission denied
StartSocket (udp): Caught "SocketException: Permission denied"

If I start linuxdcpp as root it works. I followed the instructions (apart from adding the debug flag) and only used sudo for the last step.

---

### Post by Jellyffs on 2007-05-25
GetDeb has released a .deb:

[http://www.getdeb.net/app.php?name=Linux+DC%2B%2B](http://www.getdeb.net/app.php?name=Linux+DC%2B%2B)

---

### Post by stevensheehy on 2007-05-25
> **fridaythe14th said:**
> Thanks for a great port Steven. It has improved greatly since you got involved.

When in port forward mode I can't search. Starting linuxdcpp from the terminal I get these lines:

If I start linuxdcpp as root it works. I followed the instructions (apart from adding the debug flag) and only used sudo for the last step.

You're probably using a reserved port. Linux treats ports 0-1023 as reserved and require root access in order to modify. Set the ports you're using to > 1023 in the preferences.

---

### Post by fridaythe14th on 2007-05-25
> **stevensheehy said:**
> You're probably using a reserved port. Linux treats ports 0-1023 as reserved and require root access in order to modify. Set the ports you're using to > 1023 in the preferences.
You're right. Thanks for the fast reply :)

---

### Post by pinknyunyu on 2007-06-01
I tried the other threads with instructions on how to install linuxdc++, even tried dc++ on wine, but only this thread resulted in a linuxdcpp that actually works...sort of.  my files were hashed correctly, I can connect to hubs, but I can't search.  

In preferences, when I go to the Connection tab, both of the ports listed, TCP and UDP are greater than 1023.

And I get this in terminal.  

```

(linuxdcpp:27138): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:27138): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:27138): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 17: Invalid UTF-8 encoded text

(linuxdcpp:27138): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:27138): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()


```

I know the other previous posts were about this, but the ports are greater than 1023...

I'm completely new to linux, so be gentle :)

---

### Post by schade on 2007-06-02
If you are getting this error:  "Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)
Segmentation fault (core dumped)' failed", just before you start download,  make sure that you are NOT trying to save downloaded data to NTFS partition. And also that you are NOT sharing any data stored on NTFS partitions.

---

### Post by pinknyunyu on 2007-06-02
Thanks for the tip, but I don't even get up to that point, because I can't search and therefore I can't download anything.  Plus, I checked and it's not set to save to that part...

---

### Post by stevensheehy on 2007-06-03
> **pinknyunyu said:**
> Thanks for the tip, but I don't even get up to that point, because I can't search and therefore I can't download anything.  Plus, I checked and it's not set to save to that part...

That utf8 validate error usually just means that it couldn't convert some text. You can try adjusting the charset of the hub to reduce those, but it's normal to see some of those errors even with the correct hub charset.

As far as not being able to search, try setting to passive or configuring it properly for active by reading some guides.

---

### Post by pinknyunyu on 2007-06-04
Thanks!  I changed my connection type to passive and now it&#347; working fine.  :)

---

### Post by olmari on 2007-06-06
Current version doesn't seem to work too well... I need just to connect to some hub and LinuxDC++ starts to eat up memory and CPU... I closed it at 500megabytes, which took only like minute to get there, wnd I didn't even relaly done anythign yet.

---

### Post by stokedfish on 2007-06-06
ubuntu feisty, svn compiled 4 hours ago.

I get almost no hits in search. ports are forwarded and dyndns is enabled and works well. I get 16 hits for a band...but should get at least 150 hits according to others. another guy on the hub uses linuxdc++ as well and says his version is about 2 months old and it works well for him.

-rwxr-xr-x 1 root root 3.7M 2007-03-24 11:59 /usr/local/bin/linuxdcpp

that's when he checked out...

hub is running verlihub 0.9.8.d custom modded.

also, when I do a search for whatever band I get xx hits. then I cancel the search and search for the same band again...and get 0 hits. then I press reconnect and it reconnects me to the hub...and says connected...and shows me as the only user in the userlist. no iptables, no firewall, forwarded ports.

I'm browsable and I can upload. weird...

what could this be?

---

### Post by olmari on 2007-06-06
PLease check your CPU and memoryusage too, I am having also those side-effects on my problem...

---

### Post by stokedfish on 2007-06-06
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8740 fish      17   1  143m  29m  16m S  2.3  6.1   3:46.02 linuxdcpp
```

Naw, no problem on that...but search is ****** up.

---

### Post by stevensheehy on 2007-06-06
> **olmari said:**
> Current version doesn't seem to work too well... I need just to connect to some hub and LinuxDC++ starts to eat up memory and CPU... I closed it at 500megabytes, which took only like minute to get there, wnd I didn't even relaly done anythign yet.

Are you sure you're not trying to hash a large amount of data at the same time? Hashing is a cpu and memory intensive process. Try starting with a new profile to see if it fixes the problem.

---

### Post by olmari on 2007-06-06
> **stevensheehy said:**
> Are you sure you're not trying to hash a large amount of data at the same time? Hashing is a cpu and memory intensive process. Try starting with a new profile to see if it fixes the problem.

I am sure, have cleared my settings and rehashed again before doing anythign else... Problem persists. HAshing eats CPU ofcourse, but no memoryeat there and works snappy etc... but as soon as I even hit the "public hubs" button the memeating starts...

---

### Post by stevensheehy on 2007-06-07
> **olmari said:**
> I am sure, have cleared my settings and rehashed again before doing anythign else... Problem persists. HAshing eats CPU ofcourse, but no memoryeat there and works snappy etc... but as soon as I even hit the "public hubs" button the memeating starts...

When you say current version, you mean changelog date of 2007-05-06, right? If not, try updating to the latest. If you do have the latest, try downgrading to the 2007-03-27 version to see if it has this problem (cvs update -D 2007-03-27).

---

### Post by hul on 2007-06-27
I'm trying to install DC++, and I'm getting this message after running
```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
```

```
cvs [checkout aborted]: cannot make directory linuxdcpp: Permission denied
```

What does this mean?  I'm new to Ubuntu--is there some permissions I'm supposed to set somewhere that will allow me to run this command?

Thanks!

---

### Post by stevensheehy on 2007-06-27
> **hul said:**
> I'm trying to install DC++, and I'm getting this message after running
```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
```

```
cvs [checkout aborted]: cannot make directory linuxdcpp: Permission denied
```

What does this mean?  I'm new to Ubuntu--is there some permissions I'm supposed to set somewhere that will allow me to run this command?

Thanks!

Run the cvs command in your home directory, where you have write permission. In a terminal type this command before running the cvs command to navigate to your home:
```
cd ~
```

---

### Post by sauvik on 2007-07-04
I tried installing dc++ using this method. Everything worked fine, but when I run the linuxdcpp command, I get the following error :

[COLOR="Blue"]root@necro:/home/sauvik/linuxdcpp# linuxdcpp
/root/.dc++/Certificates/client.key: No such file or directory
7569:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/root/.dc++/Certificates/client.key','w')
7569:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
Error opening Private Key /root/.dc++/Certificates/client.key
7571:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/root/.dc++/Certificates/client.key','r')
7571:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load Private Key
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(linuxdcpp:7567): Gtk-WARNING **: cannot open display:
[/COLOR]

Please help me out.
I am running Kubuntu 7.04. I know I should be posting in the Kubuntu forums, but I installed the program from here.
I am new to linux, with only very basic knowhow.

---

### Post by stoft on 2007-07-05
> **sauvik said:**
> I tried installing dc++ using this method. Everything worked fine, but when I run the linuxdcpp command, I get the following error :

[COLOR="Blue"]root@necro:/home/sauvik/linuxdcpp# linuxdcpp
/root/.dc++/Certificates/client.key: No such file or directory
7569:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/root/.dc++/Certificates/client.key','w')
7569:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
Error opening Private Key /root/.dc++/Certificates/client.key
7571:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/root/.dc++/Certificates/client.key','r')
7571:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load Private Key
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(linuxdcpp:7567): Gtk-WARNING **: cannot open display:
[/COLOR]

Please help me out.
I am running Kubuntu 7.04. I know I should be posting in the Kubuntu forums, but I installed the program from here.
I am new to linux, with only very basic knowhow.

Quick guess, it looks like you are try to run linuxdcpp as root, but logged into KDE as your normal user which means root doesn't have a display so linuxdcpp can't display. Easiest solution would probably be running linuxdcpp as your normal user.

---

### Post by stokedfish on 2007-08-01
Uhmm...so how far away is the final?  *wonders*

---

### Post by olmari on 2007-08-08
Okay update: After total hard disk formatting and leaving nothing behind, now the LinuxDC++ compiles and installs just fine and works on Feisty amd64 :)

---

### Post by piivanov82 on 2007-08-19
really useful HOW TO, thanks a lot

---

### Post by ramanan86 on 2007-08-19
works great..thank you so much for the how to...

---

### Post by Ek0nomik on 2007-08-21
Thanks for the tutorial.  :)

---

### Post by ManqueM on 2007-09-01
Hi, 
I'm quite a newbie when it comes to ubuntu , but I've downloaded the .dev installation file of linuxdcpp 0.0.1 for ubuntu and installed it correctly and it works very good. All downloading, uploading and hashing works fine, but I have one problem. I can't see the hub topics anywhere. Is that not implemented in the build yet, or is there some command I should write?

Also, I don't know if it is related, but some of the PMs from bots open up in empty chat windows where I can't see what they wrote to me...

I'm thankful for any help

Peace
/ManqueM

---

### Post by stevensheehy on 2007-09-04
> **ManqueM said:**
> Hi, 
I'm quite a newbie when it comes to ubuntu , but I've downloaded the .dev installation file of linuxdcpp 0.0.1 for ubuntu and installed it correctly and it works very good. All downloading, uploading and hashing works fine, but I have one problem. I can't see the hub topics anywhere. Is that not implemented in the build yet, or is there some command I should write?

Also, I don't know if it is related, but some of the PMs from bots open up in empty chat windows where I can't see what they wrote to me...

I'm thankful for any help

Peace
/ManqueM

You need to change the character encoding to match the hubs you are visiting. Try changing the default hub encoding in the preferences to CP1252, it's the most common encoding.

---

### Post by Depressed Man on 2007-09-04
Hi, I have Linux DC++ installed and it connects to the hub. However, I cannot search for files unless I'm on passive. I am behind a router (which causes me similar problems on Windows with ApexDCD++) but I forwarded the ports as well as DMZed my computer (no firewall on router for this one). 

But it still can't search on the regular settings. So I'm assuming IPtables is blocking it somehow (it works in Windows). So any idea?

---

### Post by 4tro on 2007-09-05
> **Depressed Man said:**
> Hi, I have Linux DC++ installed and it connects to the hub. However, I cannot search for files unless I'm on passive. I am behind a router (which causes me similar problems on Windows with ApexDCD++) but I forwarded the ports as well as DMZed my computer (no firewall on router for this one). 

But it still can't search on the regular settings. So I'm assuming IPtables is blocking it somehow (it works in Windows). So any idea?


Making a DMZ for your own computer is not needed, working with DMZ's is tricky business, check if your internal IP is the same as in windows
.

---

### Post by Depressed Man on 2007-09-05
The internal IP is the same (I have it set to place the same IP for the MAC address). And I didn't DMZ the computer, I DMZed the firewall on the router for the IP for my desktop. So the router doesn't attempt to block any connections to my desktop (my desktop is also running a firewall).

---

### Post by stoft on 2007-09-05
> **Depressed Man said:**
> Hi, I have Linux DC++ installed and it connects to the hub. However, I cannot search for files unless I'm on passive. I am behind a router (which causes me similar problems on Windows with ApexDCD++) but I forwarded the ports as well as DMZed my computer (no firewall on router for this one). 

But it still can't search on the regular settings. So I'm assuming IPtables is blocking it somehow (it works in Windows). So any idea?

If I'm not mistaken search in active mode uses udp (iirc the port either right above/below tcp), have you taken that into account when setting your firewall rules etc.?

---

### Post by stevensheehy on 2007-09-05
> **stoft said:**
> If I'm not mistaken search in active mode uses udp (iirc the port either right above/below tcp), have you taken that into account when setting your firewall rules etc.?

Well, you're half right. DC++ search does use UDP, but its port isn't right above/below TCP. They don't have to use different ports, they can use the same port if you so choose.

---

### Post by emeyer on 2007-09-06
Regarding the ability for LinuxDC++ to accept and display hub-specific right-click commands, as DC++ for Windows does:
> **stevensheehy said:**
> I don't care about such a feature so someone else will have to send a patch.

Has anyone created such a patch?

---

### Post by ManqueM on 2007-09-07
I cant see the topics due to the character encodings. I've tried changing to UTF-8, CP1252  and ISO-8859-2, but I can't see the characters å, ä or ö... And if any message includes any of those characters, I recieve nothing at all.

For example, if someone writes: "Små hästar" to me, I would expect to recieve a message saying: "Sm? h?star", but I dont recieve any message at all. I recieve all messages that are not containing any of these characters perfectly.

And further if I write "Små hästar" in the chat window, I see the message displayed correctly on my screen, but everyone else sees the öäå replaced by two weird symbols each whom I can not even type =)

It is really annoying since I recieve important information through the hub topics. It would have been fine if I recieved the messages as "Sm? h?star" because I would have been able to figure the message out anyway, but the WHOLE message gets discarded...

Has anyone had the same problems? How do I deal with it? Are certain characters not compatible with the application?
Thanks
/ManqueM

---

### Post by gav616 on 2007-09-10
> **ManqueM said:**
> I cant see the topics due to the character encodings. I've tried changing to UTF-8, CP1252  and ISO-8859-2, but I can't see the characters å, ä or ö... And if any message includes any of those characters, I recieve nothing at all.

For example, if someone writes: "Små hästar" to me, I would expect to recieve a message saying: "Sm? h?star", but I dont recieve any message at all. I recieve all messages that are not containing any of these characters perfectly.

And further if I write "Små hästar" in the chat window, I see the message displayed correctly on my screen, but everyone else sees the öäå replaced by two weird symbols each whom I can not even type =)

It is really annoying since I recieve important information through the hub topics. It would have been fine if I recieved the messages as "Sm? h?star" because I would have been able to figure the message out anyway, but the WHOLE message gets discarded...

Has anyone had the same problems? How do I deal with it? Are certain characters not compatible with the application?
Thanks
/ManqueM

same problem..

older releases (month or two ago) its ok.

---

### Post by olmari on 2007-09-11
Yeps... Seeing same here... also same with some times with file searches including those letters...

---

### Post by superdif on 2007-09-12
Hi,
I just downloaded it and compiled without errors, but if I try to run it (both as normal user and root) I get the following error message:

```
GThread-ERROR **: file gthread-posix.c: line 140 (): error 'Function not implemented' during 'pthread_getschedparam (pthread_self(), &policy, &sched)'
aborting...
Aborted (core dumped)
```

Strangely I get the same problem by running aMule (I compiled that too without error so I guess it is a system-wide problem).

I have Kubuntu 7.04 (I upgraded the kernel to 2.6.22) on an Intel Core 2 Duo.

Any suggestion on how can I solve the problem (I tried to google around first, but without result).

---

### Post by 4tro on 2007-09-13
linuxDC++ made it into the gutsy repositories ^_^

on your problem, you could try to install/reinstall libglib-dev.
i don't know if that's the problem though.

oh and by the way, why upgrade your kernel to 2.6.22 and still stick with 7.04....
Upgrade all to gutsy then ;-)

Be sure to backup all important stuff though, as always =)

---

### Post by stevensheehy on 2007-09-15
> **emeyer said:**
> Regarding the ability for LinuxDC++ to accept and display hub-specific right-click commands, as DC++ for Windows does:


Has anyone created such a patch?

[Yes]("http://developer.berlios.de/patch/?func=detailpatch&patch_id=1891&group_id=2230"), look for it sometime soon.

---

### Post by superdif on 2007-09-15
> **4tro said:**
> linuxDC++ made it into the gutsy repositories ^_^

on your problem, you could try to install/reinstall libglib-dev.
i don't know if that's the problem though.

I tried to re-install libglib-dev, but without success.

(Un)fortunately I had other issues that forced me to reinstall Kubuntu and now I took the opportunity to install it directly from Adept (and it is working). 

Thank anyway for the answer.

> **4tro said:**
>  oh and by the way, why upgrade your kernel to 2.6.22 and still stick with 7.04.... Upgrade all to gutsy then ;-)
Be sure to backup all important stuff though, as always =)

As far as I understood 7.04 is the the latest stable release and Gutsy is the testing ground for the next release. Am I right?

I got the  the 2.6.22 kernel just to upgrade it specifically, but for the rest of the system I would like to stick with the stable releases (unless I have specific reasons to upgrade specific packets). :)

---

### Post by 4tro on 2007-09-15
> **superdif said:**
> I tried to re-install libglib-dev, but without success.

(Un)fortunately I had other issues that forced me to reinstall Kubuntu and now I took the opportunity to install it directly from Adept (and it is working). 

Thank anyway for the answer.



As far as I understood 7.04 is the the latest stable release and Gutsy is the testing ground for the next release. Am I right?

I got the  the 2.6.22 kernel just to upgrade it specifically, but for the rest of the system I would like to stick with the stable releases (unless I have specific reasons to upgrade specific packets). :)

good reasoning ^_^
in another month gutsy is going to be unleashed to the unsuspecting world =)

---

### Post by superdif on 2007-09-15
> **4tro said:**
> in another month gutsy is going to be unleashed to the unsuspecting world =)

Oh my good!!!! Oh my good!!!! I must warn the wor ............... who are those penguins in black that are approaching my house?!?!? :-#

---

### Post by 4tro on 2007-09-16
> **superdif said:**
> Oh my good!!!! Oh my good!!!! I must warn the wor ............... who are those penguins in black that are approaching my house?!?!? :-#

they are the "non-free software elimination squad" coming to clean the neighbourhood :twisted:
on a slightly more serious note: you know linuxDC++ doesn't compile on Red Hat Linux 3.2.2-5? bwahahaha
(I must say I'm slightly unable to grasp the red hat versioning system)

---

### Post by texicle on 2007-09-20
Ok, I'm having a heck of a time getting linuxdcpp out of passive mode.  I've followed the instructions to a T, and all my ports are forwarded properly (or so I think) but nothing seems to take.  To attempt to solve it, I flushed my iptables, ran firestarter to make sure no ports were being blocked, set up port forwarding (9176 -> 9176 for both UDP and TCP), and set my Ubuntu box on the DMZ for my router so it's not behind the firewall.  I can't think of anything else.  My WAN IP is dynamic, but my internal IPs are static. 

I used Valknut on Slackware for the past few years with no router and I had no problem going active.  I'd like the same for linuxdc++ as it seems to be as good or better than Valknut, but there is something that is preventing it.  I think it must be in my router config, but I can't figure it out since the ports are forwarded properly and it's on the DMZ.  The only thing I can think of is that it has to do with the dynamic vs. static IP addresses.  I could be way off base here, but that's what it seems to be to me.   Any suggestions?  

Thanks!

---

### Post by stokedfish on 2007-09-21
Use DynDNS! That should help...

---

### Post by stevensheehy on 2007-09-23
LinuxDC++ 1.0 has been released.

Read the [release notes]("ftp://ftp.berlios.de/pub/linuxdcpp/linuxdcpp-1.0.0-release_notes.txt").

---

### Post by muzzamo on 2007-09-24
version 1.0.0 has just been released...

---

### Post by 4tro on 2007-09-25
does the cvs contain the current 1.0 version?
i see no updates since i last checked a week ago....

---

### Post by stevensheehy on 2007-09-25
[QUOTE=4tro]does the cvs contain the current 1.0 version?
i see no updates since i last checked a week ago....[/QUOTE]

August 04 cvs == linuxdc++ 1.0.0

---

### Post by Amazona aestiva on 2007-09-25
[Linux DC++ 1.0.0 in Debian package!]("http://www.getdeb.net/app.php?name=Linux+DC%2B%2B")

---

### Post by stevensheehy on 2007-09-25
By the way, LinuxDC++ has made its way into [Gutsy]("http://packages.ubuntu.com/gutsy/net/linuxdcpp"), although it's an older version.

I'm not sure who wrote that cheesy description though....

---

### Post by stokedfish on 2007-09-28
Thank you for all your hard work. 1.0 is a great release. Thumbs up!

---

### Post by hundrambit on 2007-10-07
Good day.

I have just visited LinuxDC++ website and downloaded "new" source, version 1.0.0. After compiling it I was trying to find the changes, like it says in release notes; user commands and magnet links. I don't see any changes. Then I open source code and compare it to a version I took from CVS about a month ago, I don't see any changes in source code either.

1.0.0 package was downloaded from here; [ftp://ftp.berlios.de/pub/linuxdcpp/linuxdcpp-1.0.0.tar.bz2](ftp://ftp.berlios.de/pub/linuxdcpp/linuxdcpp-1.0.0.tar.bz2)

Is this a joke or bad luck, or what ever it is?

Thank you.

---

### Post by olmari on 2007-10-07
1.0.0 is exact same version than latest in CVS, and also if you read the release notes you'll see this:

You can look forward to many more things [B]to
come in the near future[/B] including i18n support, user commands and magnet
support.

---

### Post by hundrambit on 2007-10-07
Just realized that I'm totally blind. Thank you, and sorry for misunderstanding. :)

---

### Post by olmari on 2007-10-07
Mm well, crap happends for all of us sometimes :)

---

### Post by pranshu on 2007-10-11
hey i installed linuxdcpp but it still is not connecting...
i guess it is connecting but probably there is some incompatibility with linux in the hub... it is showing following message...


*** Connecting
*** Connected
*** Connect failed: Connection closed

---

### Post by pranshu on 2007-10-11
also when i try to connect with password then i'm getting connected to hubs but the problem is with file list.... i' receiving this message...


(linuxdcpp:8761): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()



and after some time i get this message...


(linuxdcpp:8761): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

please help i'm desparately trying to keep myself on UBUNTU but every time i need to use dc++ i have to restart to windows... this is the only application that is keeping me on windows...

---

### Post by pranshu on 2007-10-11
hey i just worked out and somehow managed to connect... but now the problem has changed... now i can easily get file lists and match queues and all but the problem is that the program crashes with the following message on the terminal....

(linuxdcpp:8409): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
Segmentation fault (core dumped)


now this is a real problem....

actually what i think the problem might be is that on the nick list lot of nicks are not ascii characters... and i'm assuming probably that's the reason this message is shown...

(linuxdcpp:8409): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()


i'm a hardcore fan of dc++ and with dc++ being available on linux i'm really thrilled... please please help me solve this problem....

---

### Post by stevensheehy on 2007-10-12
> **pranshu said:**
> hey i just worked out and somehow managed to connect... but now the problem has changed... now i can easily get file lists and match queues and all but the problem is that the program crashes with the following message on the terminal....

(linuxdcpp:8409): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
Segmentation fault (core dumped)


now this is a real problem....

actually what i think the problem might be is that on the nick list lot of nicks are not ascii characters... and i'm assuming probably that's the reason this message is shown...

(linuxdcpp:8409): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()


i'm a hardcore fan of dc++ and with dc++ being available on linux i'm really thrilled... please please help me solve this problem....

Those errors on the commandline are not necessarily what caused it to crash. They occur all the time and are generally just warnings. You need to look at the backtrace from the coredump to see why it really crashed. Read our manual in the wiki (mentioned in the first post) to see how to do this.

---

### Post by jak on 2007-10-17
Its in Gutsy and it works fine. 
sudo apt-get install linuxdcpp

Or should I have read the whole thread?

---

### Post by jocko on 2007-10-20
stevensheehy:
I think there is something missing on the cvs server.
If I get a fresh copy from cvs and try to build and install according to your instructions, it immediately errors out:
>  scons: *** Error writing options to file: build/sconf/scache.conf
[Errno 2] No such file or directory: 'build/sconf/scache.conf'The reason for this is that there is no linuxdcpp/build/ directory (it's not on the cvs server either).
If I copy my build/ directory from a backup it all works fine.

[COLOR=DimGray] I posted a **temporary** fix [here]("http://ubuntuforums.org/showthread.php?p=3577765#post3577765"), in case anyone would run in to this problem before it is solved in a proper way.[/COLOR]

[SIZE=3][COLOR=Red]Edit[/COLOR][/SIZE][SIZE=3]: An even better fix is of course to install the deb from [getdeb.net]("http://www.getdeb.net/app.php?name=Linux+DC%2B%2B"). It's the same as the current cvs build.[/SIZE]

---

### Post by stevensheehy on 2007-10-28
> **jocko said:**
> stevensheehy:
I think there is something missing on the cvs server.
If I get a fresh copy from cvs and try to build and install according to your instructions, it immediately errors out:
The reason for this is that there is no linuxdcpp/build/ directory (it's not on the cvs server either).
If I copy my build/ directory from a backup it all works fine.

[COLOR=DimGray] I posted a **temporary** fix [here]("http://ubuntuforums.org/showthread.php?p=3577765#post3577765"), in case anyone would run in to this problem before it is solved in a proper way.[/COLOR]

[SIZE=3][COLOR=Red]Edit[/COLOR][/SIZE][SIZE=3]: An even better fix is of course to install the deb from [getdeb.net]("http://www.getdeb.net/app.php?name=Linux+DC%2B%2B"). It's the same as the current cvs build.[/SIZE]

Well, it's not the same as CVS. GetDeb has binaries for the 1.0.0 release. Since that time there have been two CVS updates. Regardless, I recommend installing the 1.0.0 deb unless you need the bleeding edge features of CVS (and the defects that go along with them).

Your build dir issue has been fixed in the latest CVS.

---

### Post by stevensheehy on 2007-10-28
By the way, I just added the highly requested feature of user commands to today's CVS update.

---

### Post by mrukus on 2007-10-29
is there a way to launch this app without having to go through the terminal???

---

### Post by 4tro on 2007-10-29
nicely done =)
I really missed the user commands as an op
but are there any plans on implementing the context with the usercommands?

$UserCommand <type> <context> <details>|

<context> is sent as an integer, but is derived by logical or'ing the following values together. This number controls which contexts the menus will be shown in:
0x01 = Hub context (available in DC++ when clicking on the hub's tab)
Example: view hub rules, change password
This command should contain no 'somenick' arguments (i.e. not %[nick] but it may contain %[mynick] or %[line:blah]).
0x02 = User context (generally available in DC++ when clicking on a user's nick)
Example: show users's statistics, ban user
This command may take nick-specific arguments.
0x04 = Search context
Example: report "bad" file in search results
This command may take nick and file-specific arguments.
0x08 = Filelist command
Example: report a bad file found then browsing a user's list
This command may take nick and file-specific arguments.
Note: this context is new in DC++ 0.669


> **mrukus said:**
> is there a way to launch this app without having to go through the terminal???
just create a launcher for it using your main menu editor

---

### Post by stevensheehy on 2007-10-29
> **4tro said:**
> nicely done =)
I really missed the user commands as an op
but are there any plans on implementing the context with the usercommands?

$UserCommand <type> <context> <details>|

<context> is sent as an integer, but is derived by logical or'ing the following values together. This number controls which contexts the menus will be shown in:
0x01 = Hub context (available in DC++ when clicking on the hub's tab)
Example: view hub rules, change password
This command should contain no 'somenick' arguments (i.e. not %[nick] but it may contain %[mynick] or %[line:blah]).
0x02 = User context (generally available in DC++ when clicking on a user's nick)
Example: show users's statistics, ban user
This command may take nick-specific arguments.
0x04 = Search context
Example: report "bad" file in search results
This command may take nick and file-specific arguments.
0x08 = Filelist command
Example: report a bad file found then browsing a user's list
This command may take nick and file-specific arguments.
Note: this context is new in DC++ 0.669



just create a launcher for it using your main menu editor

There's already a context checkbox option in the user command dialog. I'm not sure why you're saying it has to be in the command itself, it's not a command it's just a gui option. We already have a popup menu in the chat userlist. Someone is currently working to add the popup context menu for search, filelist, etc.

---

### Post by 4tro on 2007-10-30
i was talking about the context of the user commands provided by the hub...
the so called right-clickers

---

### Post by stevensheehy on 2007-10-30
> **4tro said:**
> i was talking about the context of the user commands provided by the hub...
the so called right-clickers

Oh, I wasn't aware of them previously. According to the code, it is already implemented in the dc++ core. So it should work already.

---

### Post by 4tro on 2007-10-31
> **stevensheehy said:**
> Oh, I wasn't aware of them previously. According to the code, it is already implemented in the dc++ core. So it should work already.

they work.
but the context isn't used and i believe the submenu's aren't used either

---

### Post by //RF on 2007-10-31
Yeah, some of my hubs use multiple different submenus for usercommands and the list looks like [this]("http://img140.imageshack.us/my.php?image=200710312240291280x1024at6.jpg")

---

### Post by stevensheehy on 2007-10-31
> **4tro said:**
> they work.
but the context isn't used and i believe the submenu's aren't used either

Yeah, submenus haven't been implemented yet. What do you mean by the context isn't used? The core populates it with the value sent from the hub. As I said, only user list context menu has been implemented at the moment so you'll only be able to see those types from the hub.

---

### Post by 4tro on 2007-11-01
> **stevensheehy said:**
> Yeah, submenus haven't been implemented yet. What do you mean by the context isn't used? The core populates it with the value sent from the hub. As I said, only user list context menu has been implemented at the moment so you'll only be able to see those types from the hub.

ah i see =)
i missed that you said only user list context was implemented :(

---

### Post by stokedfish on 2007-11-11
Hello, I wanted to ask if there is a chance to see a core/gui split soon? Any plans for a console linuxdcplusplus? That would be really awesome. I could have it on 24/7 on my screenless dapper home-server...

---

### Post by snek on 2007-11-12
Here here, I second this motion! :P

Seriously though, I am a bit surprised that there is Linux software which ISN'T split into a core & gui.. The only thing I ever restart on my server is the Gnome, and it's a shame it disconnects DC++ then..

---

### Post by stevensheehy on 2007-11-12
> **stokedfish said:**
> Hello, I wanted to ask if there is a chance to see a core/gui split soon? Any plans for a console linuxdcplusplus? That would be really awesome. I could have it on 24/7 on my screenless dapper home-server...

Yes, I would eventually like to turn linuxdcpp into a daemon/frontend setup, but it's going to take some time. Right now I still have to add magnet support, finish user commands and finally add l18n, on top of many other small changes here and there.

There's already a console-based dc++ app called nanodc (not up to date, though). If we did develop a daemon mode, then nanodc's author said he might port his text-based gui to it. Plus I know guys who can write a cocoa and a qt interface.

---

### Post by stokedfish on 2007-11-12
Wow, that would be awesome. I have always been wondering if the museek-code could be used as a base for the core/gui split...

[http://www.museek-plus.org/](http://www.museek-plus.org/)

I know it's for slsk and not dc, but who knows...just a thought.

---

### Post by gav616 on 2007-11-17
i love the development of this app, just wondering though, i can never find anything that i want (rare stuff) any tips? apart from the really obvious (im a above average linux user)

main question is are the default advanced options ok? whats the point in all the auto drop stuff should i touch it? (hate too many options)

---

### Post by hundrambit on 2007-11-21
I like new magnet links support. Good job. :)

---

### Post by gav616 on 2007-11-22
> **hundrambit said:**
> I like new magnet links support. Good job. :)

how do u use magnet links?

---

### Post by hundrambit on 2007-12-04
Beg someone to create one, and send it in chat, someone who has StrongDC++ or any other client that fully supports magnet links. Then click on it and you'll see the search window autosearching for right TTH.

I wish **http://**, **ftp://**, **dchub://** and **www.** links worked same way, opened the link in default system browser. :(

---

### Post by stevensheehy on 2007-12-04
> **hundrambit said:**
> I wish **http://**, **ftp://**, **dchub://** and **www.** links worked same way, opened the link in default system browser. :(

Should be implemented in the near future.

---

### Post by hundrambit on 2007-12-07
Allright Steven, I look forward to it very much. :)

---

### Post by djbon2112 on 2007-12-13
Hey everone, just installed this, but when I go to share a folder, the program crashes. Anyone have any ideas? Using the latest one from your first post.

---

### Post by stevensheehy on 2007-12-13
> **djbon2112 said:**
> Hey everone, just installed this, but when I go to share a folder, the program crashes. Anyone have any ideas? Using the latest one from your first post.

Are you sharing anything weird or unique (Networked share, huge files, etc.)? I've  seen a crash that occurs when it tries to hash a file and encounters a disk read error on the hard drive. Could never figure it out... You can compile in debug mode and get a backtrace of the crash using the steps in the manual (link on 1st page) and paste the backtrace here in a code block.

---

### Post by djbon2112 on 2007-12-14
Got it to work... It would fail if I clicked the folder I wanted to add (but not actually OPEN it) and pressed add. But opening the folder first then clicking add worked.

Weird... I'd submit a bug report or something but I don't even know what to do there! And I just used apt-get to install it so I have no idea how to recompile or anything!

---

### Post by hibernate on 2007-12-14
Hello. I hope that I'm not duplicating someone's issue already fixed... If so, please give me a link, because I've searched really hard to find out what's happening,,,

Anyway, this is my issue.

I've installed linuxdcpp for deb and had this kind of issue: i can see all users, can chat with them, search for some files in search tab, but i can't download anything and filelists also.

The strange thing is that i've reinstalled windows 3 days ago (still have to use that innocent OS sometimes) and installed Flynik DC++ which worked well before I installed ubuntu and reinstalled win. So, i can't understand a thing now. It was working - but now it is not. As i see, it is not a client trouble.

Ah, almost forgot. I've just installed latest cvs version of linuxdcpp and still nothing.

I'm not very experienced user in DC - i use it not for very long time, so please help me understand what's wrong. BTW, I'm not sure which settings are right, so here are mine:

I specified nick,
incoming connection settings:
*Active - chosen
external/wan ip: my network ip
ports - nothing changed - they all are 0
checked "Don't allow hub/UPnP to override"
outgoing connection settings:
*Direct connection - chosen
my share is all right - 38 GB already hashed

Also i tried to specify logs - checked chat (just for test), system messages, status, etc.
But they don't appear in my home directory. I have not .dc++ folder and it's not being created.

Please help me.

---

### Post by Razzloss on 2007-12-14
> **hibernate said:**
> I've installed linuxdcpp for deb and had this kind of issue: i can see all users, can chat with them, search for some files in search tab, but i can't download anything and filelists also.

The strange thing is that i've reinstalled windows 3 days ago (still have to use that innocent OS sometimes) and installed Flynik DC++ which worked well before I installed ubuntu and reinstalled win. So, i can't understand a thing now. It was working - but now it is not. As i see, it is not a client trouble.


Have you tried passive mode? It should work. It is possible that the windows client used upnp to forward the ports from your router to your computer. Linuxdcpp doesn't support this and if you are behind a NAT device you have to configure the forwarding manually.

> **hibernate said:**
> 

Ah, almost forgot. I've just installed latest cvs version of linuxdcpp and still nothing.

I'm not very experienced user in DC - i use it not for very long time, so please help me understand what's wrong. BTW, I'm not sure which settings are right, so here are mine:

I specified nick,
incoming connection settings:
*Active - chosen
external/wan ip: my network ip
ports - nothing changed - they all are 0
checked "Don't allow hub/UPnP to override"
outgoing connection settings:
*Direct connection - chosen
my share is all right - 38 GB already hashed

But they don't appear in my home directory. I have not .dc++ folder and it's not being created.

Well, most filemanagers don't show the hidden directories by default (the ones beginning with .) If it really isn't there something very weird has happened (Only things I could think of are HOME -environment var not set (and then it defaulted to /tmp/.dc++/ as far as I can remember) or no write permissions to the home dir.).

And about your settings. They are fine for the direct connection (incase there isn't a firewall blocking the connections), but if you are behind a NAT device you need to provide the ports and set up proper forwarding for the active mode to function.

--RZ

---

### Post by hibernate on 2007-12-14
Razzloss, you're right. I found logs, thank you. Didn't know about hidden .* dirs. I tried to specify ports (411 for all protocols) and accessed a hub via 411 port, tried also passive connection - but still nothing. I was fully restarting dc each time i made changes to connections, so i think, i was doing right as you said. But still i am where i am. No downloading... Logs don't tell me a thing about that...

---

### Post by hibernate on 2007-12-15
Tried passive connection today. It works for search and for retrieving file lists from some users (really few of them), but when i try to download something, it says disconnected - user is online all time... 
When i press force attempt, it requests many users for file lists (they must have that file as i understand) and they all have connection timeout...
Does anyone know what's that? And what should i do?

---

### Post by Windwielder on 2007-12-15
EDIT: Never mind, I found a fix for my problem.

---

### Post by stevensheehy on 2007-12-16
> **hibernate said:**
> Tried passive connection today. It works for search and for retrieving file lists from some users (really few of them), but when i try to download something, it says disconnected - user is online all time... 
When i press force attempt, it requests many users for file lists (they must have that file as i understand) and they all have connection timeout...
Does anyone know what's that? And what should i do?

Passive users can only download from active users, not from other passive users. You're probably trying to download from passive users. Also, if you're going to specify a port make sure it's > 1023. In linux, ports <= 1023 require root in order to use and running linuxdcpp as root is not recommended.

---

### Post by hibernate on 2007-12-16
2 stevensheehy:
Thank you for the info about ports. But that's not it. 
I've all ports grater than even 2000.
Linuxdcpp is too smart to let me download anything from passive users. They occur with brick wall in icon and my client doesn't even try to connect to them. The problem is that i had no troubles before. 
Just had windows installed with flylink which i didn't configure at all (my brother could do that, but now i can't know for sure). And i could download anything from anybody without a sound. 
But when i got pissed off with win, i've just formatted all, installed ubuntu and win (for some exidental case). So now i can't get right settings. 
Have no info about dc++ configuration thanks to my LAN ISP with those genius guys in the service. 
I found out the right router IP and tested the ports (got from one user) using some site which checks the correctness of ports by requesting server via them. It told me that TCP port is not right, and UDP is. It doesn't check TLS. I don't really know how is UDP transfered, but when i scan ports on any machine with UDP, i resps all reqs even if for TCP the port is closed. Could you please give me an advice because i can't download now a thing but filelists from some (really few) users. 
NOTE: i have really few passive users and i don't connect to them. Can download only filelists from some of active users (they must be the chosen ones ;) ).

---

### Post by djbon2112 on 2007-12-18
I'm once again having problem with this.

The program will start, run for a bit of time, then simply close. I don't know if it's crashing, or closing of its own accord, or what, but it's frustrating to say the least!

I don't know where to access any information that may be helpful, so if you can tell me how I can post stuff.

---

### Post by gfg on 2007-12-18
> **djbon2112 said:**
> I'm once again having problem with this.

The program will start, run for a bit of time, then simply close. I don't know if it's crashing, or closing of its own accord, or what, but it's frustrating to say the least!

I don't know where to access any information that may be helpful, so if you can tell me how I can post stuff.

I'm having the same problem. Some help would be useful.

Edit: It seems that I have somewhat found a solution. I followed the hashing progress and I noticed that  the program crashed on certain files, which I think might've been corrupted. The solution then was simply to delete those files. Although it might be a bit tiresome, it worked, and LD++  is for sure a lot better than running DC++ in wine which uses about 1gig of ram on my system.

---

### Post by stevensheehy on 2007-12-18
I've heard of this situation before, but I'm not sure what causes it. In order to fix it I would need somebody to compile the latest cvs in debug mode then run in gdb and send me the output of "backtrace full" after it crashes.

---

### Post by hibernate on 2007-12-19
I found out what's going on. Thanks all for your replies. I just had wrong routing table.
The gateway for one of my routes was 0.0.0.0 when it had to be 10.9.23.254!

To all having connecting troubles:
Pay attention to network and routing!

---

### Post by wirespot on 2008-01-03
Any advice on making hubs with many users (5000+) actually usable? I saw on the LDCPP tracker that there's a bug for crashing when connecting to such hubs. Mine doesn't crash, but it freezes and uses a lot of CPU. This happens to a smaller extent on hubs with fewer users (periodical small freezes), but it recovers.

I suppose it's doing "something" and that if I'd leave it it would eventually come out of the freeze, but it's just not usable like that. StrongDC in Wine works without a problem with 10,000+ users (except it also crashes for other reasons, so I can't use that either).

---

### Post by sageb1 on 2008-01-09
dcpp.net is down. when i enter the following command:

$ host dcpp.net

I get:
dcpp.net has address 0.0.0.0

todd needs to get a new server!

---

### Post by olmari on 2008-01-09
[http://dcplusplus.sourceforge.net/](http://dcplusplus.sourceforge.net/)

---

### Post by sammydee on 2008-01-24
Hi all.

I'm having major problems with all versions of linuxdcpp on two separate systems both running ubuntu gutsy. The problem is basically that although I can connect to a hub and see peers (most of the time) and even download theire file listings, whenever I try to download a file from them it is just listed as "disconnected" even when I force a reconnect.

I am behind a router firewall but I have forwarded ports and tried connection mode on passive, firewalled and active but get nothing. I know the port is open because it can be pinged and scanned. Any ideas?

Sam

---

### Post by sammydee on 2008-01-24
Fixed it!

I had to remove the ~/.dc++ directory, start up linuxdcpp, change character encoding to the european one, and then reconnect to all my hubs. Works like a charm now!

Sam

---

### Post by Mudit_BITS on 2008-01-26
hi to all 
When ever i type 
sudo apt-get install linuxdcpp my system starts downloading ldcpp 0.0.1

but i want to install the latest version can any 1 help me with the repositeries.
Thanks

---

### Post by snek on 2008-01-28
> **Mudit_BITS said:**
> hi to all 
When ever i type 
sudo apt-get install linuxdcpp my system starts downloading ldcpp 0.0.1

but i want to install the latest version can any 1 help me with the repositeries.
Thanks

You need to follow the guide in the first post.
That will get you the latest CVS version.

---

### Post by darthshak on 2008-01-29
Ok...so I am being accosted by this strange problem in LinuxDC++

I have been running it for the last 20 days without a hitch. Suddenly, today evening, whenever I hit the Download button for anything, I found that it just displayed "Disconnected". I checked to see if my disk was full, but I had at least 11 GB free on that partition.
Also, the users had free slots as the search results for the file i was downloaded had the "Users with free slots checked". 

Also, when I went to my Vista install (GOD, Vista is slow), and tried to download the same files from the same DC++ user, it worked just fine. Can anyone please help?

Thanks

---

### Post by snek on 2008-01-30
Yeah I have had this same problem a few times as well. At first I thought it was just because the ppl are pretty far away from me, but from what I can tell this is actually not the problem. So I am also a bit stumped on this on, thank god there's always multiple ppl to get it from ;)

---

### Post by bartkl on 2008-01-31
I'm experiencing the same problem for ages. 
I did notice however that it mostly occurs when the users I connect to have a client containing special characters like Ü, of which it's tag is displayed by LinuxDC++ as "?" (without the quotes).

Could this have anything to do with the problem?

[edit] Not to forget, when I run it from a terminal I get this:

> 
...

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(linuxdcpp:6354): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
Shutting down...

...


That seems to have to do with character encoding? I may be totally wrong about stuff being related to each other here though.

Thanks in advance.

[edit]**I changed the Encoding for the hub and now I do see all special characters but connection issues are still the same**

---

### Post by sitech on 2008-02-25
Okay so I'm having the same problem as quite a few people have and it occurs in version 1.01 and whatever version exists in the Ubuntu repositories.

Note: I'm behind a NAT with port forwarding.

Previously on Windows I've been using BCDC++ without any problems for years. Then I switched to Linux and had BCDC++ working without any network problems in Wine (there were some other bugs though). Search worked, downloads worked, uploads worked.

Decided that I'd switch to LinuxDC++ and using exactly the same network settings as BCDC++ was using and so the result? Uploads work, search works but any type of downloading DOESN'T WORK (file lists or files). It just says 'connecting' for two seconds and then an instant 'disconnected'.

This doesn't seem to be a forwarding issue because excluding the fact that no settings have changed, generally search and uploading doesn't work either.

If anyone knows a fix for this it would be much appreciated, I've been trying various versions for the last couple of months with no avail.

---

### Post by Razzloss on 2008-02-25
> **sitech said:**
> Okay so I'm having the same problem as quite a few people have and it occurs in version 1.01 and whatever version exists in the Ubuntu repositories.

Note: I'm behind a NAT with port forwarding.

Previously on Windows I've been using BCDC++ without any problems for years. Then I switched to Linux and had BCDC++ working without any network problems in Wine (there were some other bugs though). Search worked, downloads worked, uploads worked.

Decided that I'd switch to LinuxDC++ and using exactly the same network settings as BCDC++ was using and so the result? Uploads work, search works but any type of downloading DOESN'T WORK (file lists or files). It just says 'connecting' for two seconds and then an instant 'disconnected'.

This doesn't seem to be a forwarding issue because excluding the fact that no settings have changed, generally search and uploading doesn't work either.

If anyone knows a fix for this it would be much appreciated, I've been trying various versions for the last couple of months with no avail.

I'd recommend that you make sure that you are using correct character encoding settings for your hubs. This needs to be set from the preferences and for each favorite hub seperately. 

Also make sure you can write to your incomplete downloads directory and to your $HOME/.dc++ -directory and all its subdirs.

And third. Make sure your TCP and TLS ports are set to different values. 

Fourth, LinuxDC++ doesn't support UPnP (which might or might not work under wine) so you need to configure your router manually. 

Those were the first things I'd check. Might wanna try to start it from the terminal and see if it prints any errors there (even better with debug-build).

--RZ

---

### Post by sitech on 2008-02-27
OK, worked it out. No one on the server is using a client that is compatible with the new DC++ core.

Is there a way to change the core or do I have to go searching for an older version of LinuxDC++?

---

### Post by janfsd on 2008-02-27
> **sitech said:**
> OK, worked it out. No one on the server is using a client that is compatible with the new DC++ core.

Is there a way to change the core or do I have to go searching for an older version of LinuxDC++?
Well, the version on the offcial ubuntu repos uses an older core (0.691), maybe that one could work.

---

### Post by sitech on 2008-02-27
I actually ended up using the CVS and taking it back to 22/11/2006. Works perfect now :D.

Its a shame so many of of the users are using such an old version of DC++ (about 90%).

---

### Post by k0rv3n on 2008-02-29
I dont know if this is relevant in this topic.
But is there a way to set autorefresh time to higher than 100minutes?
I'm using version 0.698 and in this version 100minutes is the maximum value :/

---

### Post by Frozzare on 2008-03-01
Thanks ;D

---

### Post by bronx on 2008-03-04
Thanks for this new .deb package. its actually solved my problem. quick & easy.:guitar:

---

### Post by stevensheehy on 2008-03-07
> **k0rv3n said:**
> I dont know if this is relevant in this topic.
But is there a way to set autorefresh time to higher than 100minutes?
I'm using version 0.698 and in this version 100minutes is the maximum value :/

Open settingsdialog.glade and search for "autoRefreshSpinButton". Change the 100 to your desired amount.

---

### Post by dj3mb3 on 2008-03-24
Hi, this HOW TO is fantastic,
Now LinuxDC++ work fine for me... the only thing I have notice is that on my laptop the program is very slow in general ... switching Tab,open  dialogs ... (the connection speed is all right).

I have an intel T7500 processor, wiht 2 GB of ram, 160 GB Hard disk (7200 rpm)  and a Quadro Fx 360M

And this is the first app very very slow (2 - 3 seconds waiting every click)

Someone else notice this? or is my pc that don't like dc

I think this is almost strange

---

### Post by stevensheehy on 2008-03-24
> **dj3mb3 said:**
> Hi, this HOW TO is fantastic,
Now LinuxDC++ work fine for me... the only thing I have notice is that on my laptop the program is very slow in general ... switching Tab,open  dialogs ... (the connection speed is all right).

I have an intel T7500 processor, wiht 2 GB of ram, 160 GB Hard disk (7200 rpm)  and a Quadro Fx 360M

And this is the first app very very slow (2 - 3 seconds waiting every click)

Someone else notice this? or is my pc that don't like dc

I think this is almost strange

While I wouldn't say that LinuxDC++ is extremely fast, it is definitely not as slow as you're experiencing. Something in your OS is causing it to be slow. Try disabling Assistive Technology to see if that helps (System->Preferences->Universal Access->Assistive Technology Preferences). Also, make sure you're not hashing files as it is generally pretty slow until it finishes hashing.

---

### Post by caglartac on 2008-04-18
hi when i try to lauch dcpp from the terminal i get this message

enve1@enve-ubuntu:~/linuxdcpp$ linuxdcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault (core dumped)
enve1@enve-ubuntu:~/linuxdcpp$

i cant find out what the problem is
dc window appears and crashes, just disappering from the screen

and in the terminal i get the message above
i need help please

---

### Post by stevensheehy on 2008-04-19
What version are you using?

Read the debugging section of the [manual]("http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Manual") to get a backtrace and post it here.

---

### Post by caglartac on 2008-04-21
not sure if i did it right but i got this message;

Starting program: /home/enve/linuxdcpp/linuxdcpp 
[Thread debugging using libthread_db enabled]
[New Thread -1223112496 (LWP 29952)]
Loading: Hash database
[New Thread -1224578160 (LWP 29953)]
Loading: Shared Files
[New Thread -1232970864 (LWP 29954)]
[Thread -1232970864 (LWP 29954) exited]
Loading: Download Queue
[New Thread -1232970864 (LWP 29955)]
[New Thread -1241642096 (LWP 29956)]
[New Thread -1250034800 (LWP 29957)]
/usr/local/share/linuxdcpp is inaccessible, falling back to current directory instead.
[New Thread -1272329328 (LWP 29958)]
[New Thread -1280722032 (LWP 29959)]
[Thread -1272329328 (LWP 29958) exited]
[Thread -1280722032 (LWP 29959) exited]
[New Thread -1280722032 (LWP 29960)]

and this should be added that when i run with gdb, it seems to work, i'll check if it does

---

### Post by charliebrownau on 2008-04-27
Hello , 

Does anyone know how to install LinuxDC++
that is based off Windows DC++ 0.261 or 0.674.

I am recently learning to use Ubuntu 8.04
and it comes bundled with an incompatble 
edition .

I don't use DC++ over the internet only
for LAN offline use .

Most of the Windows users , are using DC++
0.261 (non hashing) or DC++ or BCDC++ 0.674

I have tired to convert an RPM to DEB and install
dcpp 0.674 and the program HALF works 
It loads , it connects, it can do a file list
it can grab files . Only if I dont share files
in DC++ under Linux , once I setup some folders
to share it constantly crash's
with segment error's (see error below)

charlie@charlie-desktop:~$ dcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault

Idealy if I could install Linux DC++ 0.261
that would be perfered as its not hashing
(or if anyone else knows of a stable
 one that doesnt hash)

Here is a pic of the one I have running:
[[IMG]http://img292.imageshack.us/img292/9862/dcpplinux27april2008jh8.th.png[/IMG]](http://img292.imageshack.us/my.php?image=dcpplinux27april2008jh8.png)

Thanks for any help in advance

---

### Post by 4tro on 2008-04-28
> **charliebrownau said:**
> Hello , 

Does anyone know how to install LinuxDC++
that is based off Windows DC++ 0.261 or 0.674.

I am recently learning to use Ubuntu 8.04
and it comes bundled with an incompatble 
edition .

I don't use DC++ over the internet only
for LAN offline use .

Most of the Windows users , are using DC++
0.261 (non hashing) or DC++ or BCDC++ 0.674

I have tired to convert an RPM to DEB and install
dcpp 0.674 and the program HALF works 
It loads , it connects, it can do a file list
it can grab files . Only if I dont share files
in DC++ under Linux , once I setup some folders
to share it constantly crash's
with segment error's (see error below)

charlie@charlie-desktop:~$ dcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault

Idealy if I could install Linux DC++ 0.261
that would be perfered as its not hashing
(or if anyone else knows of a stable
 one that doesnt hash)

Here is a pic of the one I have running:
[[IMG]http://img292.imageshack.us/img292/9862/dcpplinux27april2008jh8.th.png[/IMG]]("http://img292.imageshack.us/my.php?image=dcpplinux27april2008jh8.png")

Thanks for any help in advance

you're not the first one to ask about a non-hashing client,
but most of the hubs will kick you for it, so nobody is interested in maintaining such a client.

and hashing is only a problem for a very short time, after that it will stop hashing.
try to let it hash over night without being connected to a hub, and limit the hashing speed if that's possible...

or try to use wine to run an older DC++ version, but i cannot guarantee it will work

---

### Post by charliebrownau on 2008-04-28
To the person above that did NOT READ MY POST
here is the key points

I asked for :

> **charliebrownau said:**
> Hello , 

Does anyone know how to install LinuxDC++
that is **based off Windows DC++ 0.261 or 0.674.**

_**I don't use DC++ over the internet **_only
for *LAN offline use* .

**Most** of the Windows users , are using [I]DC++
0.261 (non hashing) or DC++ or BCDC++ 0.674[/I]



Also half the time I AM hosting a DC++ HUB on an LAN
network at home or lan partys so I do not
have the issues of internet hubs as I **NEVER**
use DC++ over the internet

---

### Post by 4tro on 2008-04-28
> **charliebrownau said:**
> To the person above that did NOT READ MY POST
here is the key points

I asked for :



Also half the time I AM hosting a DC++ HUB on an LAN
network at home or lan partys so I do not
have the issues of internet hubs as I **NEVER**
use DC++ over the internet

i did read your post, my keypoints are:
- i don't believe there is a version of linuxDC++based on 0.261
- i heard dozens upon dozens people complain about hashing when i told them to update their client, hashing is NOT bad, even on a LAN based hub.
- your best bet would be to find an old version of valknut or you're stuck using dc++ 0.621 through wine, although i doubt that will work.
- most newer clients are incompatible with clients that old, that's not on purpose but sometimes cannot be avoided. all the people in that lan-hub should use old clients then. (maybe that's the case, i wouldn't know.)

p.s.
I'm not offending you here, i give you my viewpoint as a longtime hubrunner, huboperator and DC++ user. (occasional client-hacker as well)

---

### Post by stokedfish on 2008-05-09
Hm, is linuxdc++ still alive? Just wondering...

---

### Post by stevensheehy on 2008-05-09
> **stokedfish said:**
> Hm, is linuxdc++ still alive? Just wondering...

Why would you ask that?

---

### Post by stokedfish on 2008-05-10
The last official release was in 2007 and it's May 2008 now.

I was just wondering.

---

### Post by jocko on 2008-05-10
> **stokedfish said:**
> The last official release was in 2007 and it's May 2008 now.

I was just wondering.

If you [look here]("http://cvs.berlios.de/cgi-bin/viewcvs.cgi/linuxdcpp/linuxdcpp/") you can see that the last update in cvs was only five days ago (by Stevensheehy), so it's still being worked on.
If you only count the "official" releases (1.0.0 and 1.0.1) there's only been two releases,  both released in 2007, but linuxdcpp has been available from cvs longer than that (I've used it since I found this thread in june 2006, with only occasional breakages and minor isses).
I'm sure the next official release will come "when it's ready", i.e when the developer thinks it's necessary.

---

### Post by stevensheehy on 2008-07-04
LinuxDC++ [1.0.2]("http://prdownload.berlios.de/linuxdcpp/linuxdcpp-1.0.2.tar.bz2") has been released.

---

### Post by stokedfish on 2008-07-05
Great release, very stable. Thank you!  :)

---

### Post by ThomasNovin on 2008-07-07
If you try to download from GetDeb you cannot find a supported Hardy release.

"Selected Ubuntu version no longer supported by Getdeb, this package will not be updated!"

Wonder why...

---

### Post by stevensheehy on 2008-07-08
> **ThomasNovin said:**
> If you try to download from GetDeb you cannot find a supported Hardy release.

"Selected Ubuntu version no longer supported by Getdeb, this package will not be updated!"

Wonder why...

I guess because GetDeb is for applications not available in the Ubuntu repositories. Since Linuxdcpp is now available in Ubuntu they must be discontinuing their support. I'll remove the link from the first page.

---

### Post by snek on 2008-07-08
I can't seem to use the old CVS method to update LinuxDC++

cvs [update aborted]: connect to cvs.linuxdcpp.berlios.de(195.37.77.137):2401 failed: Connection refused

This is using the normal: cvs update -d

Has something changed?

I did get it to work however, I just downloaded the 1.0.2 tar and untarred it in the old dir and then ran the scons install command again and that seems to have upgraded it just fine. At least, it says 1.0.2 now and it seems stable ;)

I would still like the cvs method to work though, since I like compiling stuff myself :P

---

### Post by jocko on 2008-07-08
It works fine from here. Maybe the server was temporarily offline when you tried?

---

### Post by snek on 2008-07-09
Ah I figured it out.. Seems the ip is being blocked by ipblock.
Guess I'll just whitelist it and try again ;)

UPDATE: Yeah whitelisting solved the problem, everything went fine after that

---

### Post by encikraju on 2008-08-05
Do you ever experience with file hashing everytime you load the dcpp?
Hashing slows down my pc perfomance
```
LinuxDC++ version: 1.0.1
Core version: 0.698
```

---

### Post by WillemToerien on 2008-08-05
Before I found this HOWTO I used to use ApexDC++ with wine. This is way much better. (^_^)

---

### Post by richa.cseit@gmail.com on 2008-08-15
hi!
I tried wat is explained.I donwloaded
 cvs
scons
build-essential
libgtk2.0-dev
libglade2-dev
zlib1g-dev
libbz2-dev
libssl-dev
and run the commands
sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev
and
sudo apt-get install libglitz1-dev
successfully.After this whn i entered following code  in terminal

cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
[hit enter when prompted for the password]

cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
It is giving following error
honey@honey-laptop:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcpp
CVS password: 
Unknown host cvs.linuxdcpp.berlios.de.
honey@honey-laptop:~$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
Unknown host cvs.linuxdcpp.berlios.de.
honey@honey-laptop:~

so plssssssssssssss hellp.. <i hit when it asked fr password>

---

### Post by richa.cseit@gmail.com on 2008-08-15
> **richa.cseit@gmail.com said:**
> hi!
I tried wat is explained.I donwloaded
 cvs
scons
build-essential
libgtk2.0-dev
libglade2-dev
zlib1g-dev
libbz2-dev
libssl-dev
and run the commands
sudo apt-get install cvs scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev
and
sudo apt-get install libglitz1-dev
successfully.After this whn i entered following code  in terminal

cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
[hit enter when prompted for the password]

cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
It is giving following error
honey@honey-laptop:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcpp
CVS password: 
Unknown host cvs.linuxdcpp.berlios.de.
honey@honey-laptop:~$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
Unknown host cvs.linuxdcpp.berlios.de.
honey@honey-laptop:~

so plssssssssssssss hellp.. <i hit when it asked fr password>
:confused:

---

### Post by snek on 2008-08-18
Seems the cvs server was down when you tried it..
I just issued this at home:
```
cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
```
And it worked fine. So try again and it should probably work.

On another note..

**BUG REPORT**
Sometimes ldcpp doesn't update the user list properly. A friend who had connection problems got diconnected a lot and reconnected every time.. After a long time ldcpp never showed him as online anymore. I had to restart ldcpp to get it to show him in the userlist.

---

### Post by stevensheehy on 2008-09-06
LinuxDC++ has moved to [Launchpad]("https://launchpad.net/linuxdcpp"). I have updated the install instructions accordingly.

---

### Post by dualpretop on 2008-09-16
Deb.package:

[http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.1-1_i386.deb](http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.1-1_i386.deb)

---

### Post by stevensheehy on 2008-09-16
> **dualpretop said:**
> Deb.package:

[http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.1-1_i386.deb](http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.1-1_i386.deb)

[1.02]("http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.2-1_i386.deb") would be a better choice. ;)

---

### Post by zajc on 2008-09-17
**SOLVED :)**

> **stevensheehy said:**
> [1.02]("http://ge.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.2-1_i386.deb") would be a better choice. ;)

When trying to install on Ubuntu 8.04, 64-bit I'm getting **[COLOR="Red"]Error: Dependency is not satisfiable: libgtk2.0-0[/COLOR]**.

libgtk2.0-0 and libgtk2.0-dev are installed.

What should I do :confused:

EDIT: I found .deb package in this repository [http://packages.debian.org/lenny/amd64/linuxdcpp/download](http://packages.debian.org/lenny/amd64/linuxdcpp/download) and it works fine :)

---

### Post by Sahtor on 2008-10-07
Same for i386
[http://packages.debian.org/lenny/i386/linuxdcpp/download](http://packages.debian.org/lenny/i386/linuxdcpp/download)

---

### Post by nandoflorestan on 2009-04-26
linuxdcpp, as provided with Ubuntu 9.04 Jaunty Jackalope, does not even start.

My solution has been to download the newest version (1.0.3) and compile it:

```
# Download linuxdcpp 1.0.3 from
# http://launchpad.net/linuxdcpp/1.0/1.0.3/+download/linuxdcpp-1.0.3.tar.bz2
# Uncompress it.
# Go into the uncompressed directory.

# Install dependencies
sudo apt-get install libgtk2.0-dev libglade2-dev libssl-dev scons

# Create a build directory
mkdir ../linuxdcpp-build

# Compile
scons PREFIX=../linuxdcpp-build
# Bla bla bla... Just check that there are no errors in the compilation output.

# Go to build directory and run the application
cd ../linuxdcpp-build
bin/linuxdcpp

# If you confirm that it works, you can compile and install it globally:
# Build again, but this time PREFIX=/usr
scons
# As root, copy files to system directories
sudo scons install
```

---

### Post by zalenix on 2009-05-21
when i give the following command:

bzr branch lp:linuxdcpp
I get the following statement:

bzr: ERROR: [Errno -2] Name or service not known

I again give the same command, this time I get:

bzr: ERROR: [Errno 111] Connection refused

Plz Help.!

---

### Post by Znupi on 2009-05-21
> **zalenix said:**
> when i give the following command:

bzr branch lp:linuxdcpp
I get the following statement:

bzr: ERROR: [Errno -2] Name or service not known

I again give the same command, this time I get:

bzr: ERROR: [Errno 111] Connection refused

Plz Help.!
You don't have to compile LinuxDC++ anymore, it's included in the respositories. Just do:
```
sudo apt-get install linuxdcpp
```
And you are done! :)

---

### Post by piyush.neo on 2009-08-29
i am using ubuntu 9.04...
while executing this command:
bzr branch lp:linuxdcppthe error is
[B]bzr: ERROR: [Errno -2] Name or service not known

plz help..
[/B]

---

### Post by piyush.neo on 2009-08-29
sorry i didnt read preious post...got the solution...

---

### Post by piyush.neo on 2009-08-29
how to share files....
i am using **preference>sharing>add**
but its not accepting any of my files...
plz help..

---

### Post by rexxxlo on 2009-10-28
i have this program running on my asuseee with easypeasy 1.5 as the os 

i am using an brand new "HP simplesave" 320gb 2.5" usb for my dl folder and share also.

i have everything configured fine it connects to my hub and files transfer just fine too but every now and then it closes and the hdd unmounts at the same time, i noticed this when i added a large file to be hashed for sharing 

when dc++ closes the drive unmounts and sometimes is very difficult to remount taking 3-4 tries 

when the hdd is in use a light blinks but after the program closes the light stays on solid  

when i run dc++ the hdd clicks like its a bad drive but it works fine if i dont run dc++ and just use it for storage

if i try to connect the drive and start dc++ sometimes the program will not start until i unplug it opening as soon as i unplug the drive

---

### Post by yeeshkull on 2009-11-11
> **piyush.neo said:**
> how to share files....
i am using **preference>sharing>add**
but its not accepting any of my files...
plz help..

I'm having the same problem too and I've abandoned my attempts at getting Linux dc++ to work.  I'm wondering if it's a partition format issue as my external hdd is in NTFS.  I've had success getting Windows based dc clients to work with Crossover Pro.

---

### Post by rexxxlo on 2009-11-12
strange i have had ntfs drives share fine...

how large s the file you are trying to share?

try making a folder that has a small share like 5-10 gb

i figures out my previous question my usb hdd uses to much power for one port.

if i share a small size it does fine but when i try to hash over 30gb it crashes

---

### Post by shankhs on 2009-11-17
I am experiencing very slow downloads from linuxdcpp like 5 kiB/s whereas the win counterpart is downloading at 9 MB/s!!!
How to detect and correct the problem?

Thank You eagerly waiting for some advice.

---

### Post by MarkC502 on 2010-01-16
I am using StrongDC++ 2.30 Based on DC++ 0.75 under wine 1.1.36 with almost no bad effects. Minor problem with some text lists not displaying text sometimes but minimize to tray and then it comes back OK. Also it has crashed twice but I was also running emule in wine and doing network disk transfers so I can't complain. Since StrongDC++ is a multi-segment download client it can download from multiple people at once and I downloaded 6 700MB video files overnight with speed caps set at 400KB Down / 60KB Up ( you have to at least do 1 for 7 with your UL vs DL speed caps ). So I would vote for StrongDC++ via Wine as the best DC++ solution since it works 95% and has many more features and speed than other DC clients.

I just wish I would have tried to run it in Wine a year ago :-(

Note: I did add the repositories from WineHQ to allow install of Wine 1.1.36 as I am using 9.04 Ubuntu x86 Desktop on the box in question and it only has Wine 1.0.1-0ubuntu6 in the repositories so I have no idea if StrongDC++ works with the 1.0.1 Wine in the Repositories as I did not test that and went strait to the newest stable wine release.

---

### Post by stevensheehy on 2010-04-03
LinuxDC++ also has segmented downloads in its latest version. It's not officially released yet, but you can find pre-release debian packages for it on our PPA on Launchpad: 

[https://launchpad.net/~linuxdcpp-team/+archive/ppa](https://launchpad.net/~linuxdcpp-team/+archive/ppa)

---

### Post by stevensheehy on 2011-04-17
LinuxDC++ 1.1.0 released:

> LinuxDC++ 1.1.0 is a major milestone encapsulating over two years worth of effort. Major changes include internationalization support, DC++ core 0.75, a favorite users tab, desktop notifications and a command line interface. Numerous other changes including bug fixes and feature enhancements can be found in the changelog.

Binaries can be found in our release PPA: [https://launchpad.net/~linuxdcpp-team/+archive/release](https://launchpad.net/~linuxdcpp-team/+archive/release)

[Read more]("https://launchpad.net/linuxdcpp/1.1/1.1.0")

---

### Post by siddhi_1803 on 2011-04-29
Hi

I have some problem with linux dcpp on ubuntu.
I have to run opendchub as server and want two clients to connect to it.
I have one vitual machine running on same ubuntu.
I connect to same server from my machine as well as VM client using linuxdcpp.
But I do not see the files shared by VM client on my machine client and vice versa. 

Where do I see other users and files. I tried searching , no use.
Am i doing something wrong?

Please help.

---

### Post by Nitronium on 2011-08-01
Works a dream, even 5 years on!

---

### Post by igitur on 2012-04-09
> **stevensheehy said:**
> 
To do this in one command:
```
sudo apt-get install bzr scons build-essential libgtk2.0-dev libglade2-dev zlib1g-dev libbz2-dev libssl-dev libboost-dev
```


libnotify-dev is now also required.

---

