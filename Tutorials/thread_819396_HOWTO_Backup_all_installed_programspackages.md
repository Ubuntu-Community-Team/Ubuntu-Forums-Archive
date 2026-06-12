---
title: "HOWTO: Backup all installed programs/packages"
date: 2008-06-05
forum: Tutorials
---

### Post by abhiroopb on 2008-06-05
[COLOR="Red"][SIZE="4"]PROBLEM:[/SIZE][/COLOR] Lets say you have set up your *buntu box. Now you want to backup all the installed deb files so that you can restore them quickly and efficiently.

[COLOR="Red"][SIZE="4"]UPDATE: Why would you want this?[/SIZE][/COLOR]
When I was using windows I had a directory of EVERY Single program that I had downloaded. For one thing it would be easier to install everything as I would not have to go online and hunt for them. Further it would be useful where a computer does not have internet connection. In ubuntu "hunting" for programs is a rare occurrence thanks to the fantastic package managing system. However, I personally have about 20-30 programs that I have either compiled from source (using checkinstall, so that that a deb package is created and they are added to APT), or downloaded debs from obscure locations. Now each of these debs I will save in a directory so that in the future I do not have to go hunting for them. However, this command I have outlined backs up ALL packages, including the ones in the package manager. So, why would you want that? 

Firstly, this is VERY useful if lets say you have setup a very basic installation with all updates, and all non-free video/audio/etc codecs. Further you have installed some basic useful software. Now lets say you want to install the SAME setup on your grandmothers computer, except she does not have internet connection, or at the time you go to set it up she does not have a net connection. Using this script you can have all your debs in one simple location, so you will not have to redownload everything.

Secondly, lets assume you work for a school, or a company, and you need to install the SAME ubuntu installation on 30 computers. Wouldn't it be easier to simply put all these debs in a central server and issue the dpkg -i *.deb command. This way you don't have to individually select the packages AND the packages don't have to download.

Thirdly, (and this is purely personal) I like to be able to have all my installed packages at hand. This command doesn't take much effort, and for me it only requires 1.4 gb of space, so for a bit of piece of mind I can easily have all my packages on hand.

There is no real reason to do this if you are already doing a full system backup (e.g. an image of your Ubuntu partition using partimage). This is just something I discovered and feel could be beneficial to other users.

These commands will do that for you.

Open a terminal and paste the following into it:

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```

(the last command will take some time)

Now if you scroll to your home folder, you should find a folder called "dpkg-repack" which should have all the deb files of all your installed packages.

[B]
RE-INSTALL[/B]
If you want to re-install the packages, navigate to the folder with the packages and input the following command in the terminal:
```
sudo dpkg -i *.deb
```

Thanks to [https://answers.launchpad.net/aptoncd/+question/15592/+index](https://answers.launchpad.net/aptoncd/+question/15592/+index) (Rafael)

NB: I know AptonCD does this but what prompted me to use this method was that I had done the sudo apt-get clean command which had erased all the files in the /var/cache/apt directory, rendering AptonCD useless (as all it does is take the files from there and put it in the list). So I find this method is more efficient, and easier for me to control!

---

### Post by Het Irv on 2008-06-05
This is pretty cool, This will save some time when restoring my computer if I have screwed up the file system. 

If you don't mind I am going to link this in the forums of the Backup Program that I use, QuickStart.  [http://quickstart.phpbb.net/index.php](http://quickstart.phpbb.net/index.php)

Question: Do you have to save this in your home folder or can you change the path to an external drive?

---

### Post by abhiroopb on 2008-06-05
you should be able to do it anywhere you like. Haven't tested that though.

Just change: mkdir ~/dpkg-repack; cd ~/dpkg-repack

to wherever your external directory is (e.g. mkdir /media/external/dpkg-repack; cd /media/external/dpkg-repack)

I don't really want to create a username but would it be ok if I were to suggest requests for QuickStart? It seems like a great program!

---

### Post by Samhain13 on 2008-06-05
How do I restore these back-ups (from say, /media/Storage/dpkg-repack) after I've reinstalled?

---

### Post by abhiroopb on 2008-06-05
Thanks I added it.

---

### Post by mdpalow on 2008-06-05
> **abhiroopb]

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack said:**
> 

[QUOTE=Het Irv;5121129]This is pretty cool. 

If you don't mind I am going to link this in the forums of the Backup Program that I use, QuickStart.  [http://quickstart.phpbb.net/index.php](http://quickstart.phpbb.net/index.php)



Hey Irv,

This is 'pretty cool' as you say. 

Thanks for posting the link to here in the QuickStart forum. I'm always interested in back-up methods.

Do I understand this correctly in that this will create the .deb files again from the apps that are installed? Even if they were deleted using apt-get clean?

If this is something you want Irv, I don't see why we can't do it. If 'abhiroopb' would like to come over to our forum, we could talk with him some more and get his input for the addition.

Drop me a note in the QS forum Irv and let me know. 

Thanks... mdpalow

---

### Post by abhiroopb on 2008-06-05
Yes this basically scans ALL installed deb packages (including those NOT installed through synaptic/apt) and downloads them to a local folder. Also I really liked the QuickStart script, although there are numerous additions/changes I would like to suggest. This is a bad time for me to work on anything though, if you would be willing to wait a couple of weeks I'd be glad to add my input.

---

### Post by Promaster91 on 2008-06-05
This will only backup programs not personal data, right?

---

### Post by abhiroopb on 2008-06-05
> **Promaster91 said:**
> This will only backup programs not personal data, right?

A debian file is much like an exe file in windows or a dmg file in OSX. So it is basically an installer. What this does is looks through ALL the installed programs in you're computer and downloads them to a local directory.

So to answer your question it does not touch any data of any kind. It simply downloads your installed programs.

---

### Post by Bruce M. on 2008-06-05
What is all this?:
```
dpkg-deb: ignoring 1 warnings about the control file(s)

warning, './dpkg-repack-20691/DEBIAN/control' contains user-defined field 'Original-Maintainer'
```


It's doing it's thing now.

Have a good day.
Bruce

**EDIT:** Once it's done can I just copy the directory to a DVD?

---

### Post by abhiroopb on 2008-06-05
It'll give you a massive directory of .deb files. Its completely upto you what you want to do with them. I have them backed up in an external hard drive. You could burn them to DVD if you want.

---

### Post by Bruce M. on 2008-06-05
> **abhiroopb said:**
> It'll give you a massive directory of .deb files. Its completely upto you what you want to do with them. I have them backed up in an external hard drive. You could burn them to DVD if you want.

Well, my /var/cache/apt tells me 359+MB so if it's the same it could go to my second HD or even a CD.

Could I use this to "install" on another machine (ie: not mine)?

---

### Post by abhiroopb on 2008-06-05
the /var/cache/apt directory is debs from a while back (which haven't been erased and are still lying around even after uninstall) and some new installed packages won't be listed there.

Installing on a clean machine is ok. But I have NO idea what will happen if you try it on a machine that already has some programs installed. Apt is quite smart so it should be ok, be careful though.

---

### Post by Het Irv on 2008-06-05
To reinstall everything couldn't you 'cd' to the directory that ther are in and use ```
sudo dpkg -i *.deb
```

If remembered the command correctly, that will install all deb's in the current folder, it will also handle any depencencies (install packages that need to be installed first, first).

---

### Post by abhiroopb on 2008-06-05
I have added that already (but I forgot to add the sudo)

---

### Post by Het Irv on 2008-06-05
> **abhiroopb said:**
> 
I don't really want to create a username but would it be ok if I were to suggest requests for QuickStart? It seems like a great program!

I guess so, but It would be easier for you to join.  If you are busy thats fine, We used to have a thread here in the Ubuntu Forums, but there was a little dust up, and the program was getting to big for one thread anyway.  It's not the most active of forums but mdplaow is usually on two or three times a day.

---

### Post by starcannon on 2008-06-05
Have you tried apt on cd?

```
sudo apt-get install aptoncd
```

---

### Post by abhiroopb on 2008-06-05
I have already mentioned EXACTLY why aptoncd is not appropriate. Thanks for mentioning anyway.

---

### Post by Sef on 2008-06-05
Moved to Tips and Tricks.

---

### Post by PinkFloyd102489 on 2008-06-05
Wouldnt it just be easier to do this?

```

To make the list:
sudo dpkg --get-selections > installed-software

To restore packages:
sudo dpkg --set-selections < installed-software

```

This gives you the list of packages without all of the deb files. Mind that you'll need an internet connection, but most computers do.



EDIT: installed-software is a file btw. It just acts as a list that you pipe back into the dpkg command so it will know what packages to download.

---

### Post by abhiroopb on 2008-06-05
yes i usually use that if as it takes a lot less space. The point of this is say for example you have to install the packages on multiple computers, using this command since they're downloaded you only have to run them.

---

### Post by PinkFloyd102489 on 2008-06-05
> **abhiroopb said:**
> yes i usually use that if as it takes a lot less space. The point of this is say for example you have to install the packages on multiple computers, using this command since they're downloaded you only have to run them.

Understandable. I just like my way better because I have a fast connection. :-)

---

### Post by abhiroopb on 2008-06-05
Thats the beauty of linux, a million ways to do the same thing :)!

---

### Post by Bruce M. on 2008-06-05
> **PinkFloyd102489 said:**
> Wouldnt it just be easier to do this?

```

To make the list:
sudo dpkg --get-selections > installed-software

To restore packages:
sudo dpkg --set-selections < installed-software

```

Thanks for this.  :)
I've made the list, nice.

> **abhiroopb said:**
> yes i usually use that if as it takes a lot less space. The point of this is say for example you have to install the packages on multiple computers, using this command since they're downloaded you only have to run them.

This is, of course, the plus side of things as I have a slow internet connection (128kbs), so it did take a while to get them (633.2 MB)

> **PinkFloyd102489 said:**
> Understandable. I just like my way better because I have a fast connection. :-)

> **abhiroopb said:**
> Thats the beauty of linux, a million ways to do the same thing :)!

And combined, I now have a list I can use to look up a file, and the files on a CD.

**[CENTER]Call that: 1,000,001 ways to do the same thing.[/CENTER]**

**Thanks to both of you.**
Have a nice day.
Bruce

---

### Post by Gourgi on 2008-06-05
> **PinkFloyd102489 said:**
> Wouldnt it just be easier to do this?

```

To make the list:
sudo dpkg --get-selections > installed-software

To restore packages:
sudo dpkg --set-selections < installed-software

```

This gives you the list of packages without all of the deb files. Mind that you'll need an internet connection, but most computers do.



EDIT: installed-software is a file btw. It just acts as a list that you pipe back into the dpkg command so it will know what packages to download.
i liked your method and i gave it a try, but ..

i exported the list of files, i edited it and added 1 application that i don't have installed ```

2vcard						install

```

and after that ```
sudo dpkg --set-selections < installed-software
``` it is supposed to have 2vcard installed :confused:
it does that automatically?? i tried sudo apt-get update && sudo apt-get upgrade but nothing happened 
2vcard yet not installed

---

### Post by abhiroopb on 2008-06-06
You can't edit the file and add something like that.  Just recreate the file, it takes a couple of seconds.

---

### Post by abhiroopb on 2008-06-11
IMPORTANT: I just discovered that using this command:

Code:

dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:

dpkg --set-selections < installed-software

followed by

Code:

dselect

DOES NOT install packages not in repos. So if you have used this to backup packages it will be no good installing say a .deb package you downloaded from getdeb. Keep this in mind. Mine however, should work fine.

---

### Post by unutbu on 2008-06-11
Thank you abhiroopb for the very informative tutorial!

I have one reservation about the method however, that I hope someone here will put to rest:

If you run

```
sudo dpkg -i *.deb
```

will it really install the debs in the correct order? I thought you would need a tool like apt-get to straighten out the dependency problems. 



[B]
EDIT: Please ignore the rest of this message. I've tried it -- and it does not work. Setting up apt-get and sources.list properly is more complicated than what I showed below.
[/B]



If that is true perhaps what we could do is

edit /etc/apt/sources.list by adding something like
```

deb file://home/user/dpkg-repack gutsy universe multiverse restricted main security gutsy-backports

``` 
(changing gutsy to hardy if that's the way you roll) then generate the list of packages with

```
% dpkg --get-selections | grep install | cut -f1 > installed-pkgs
```

(if you didn't have the list already) and install them with
```
% sudo apt-get install `cat installed-pkgs`
```

---

### Post by abhiroopb on 2008-06-11
I haven't tested it exactly, but from what I've heard dpkg is able to do it automatically installing first the packages that need to be installed. What exactly is the difference? I'm sorry I'm a bit confused with what your solution does?

---

### Post by unutbu on 2008-06-11
Here is a little experiment I ran to test if dpkg is smart enough to resolve dependencies on its own. 

I've downloaded 
warsow_0.42-1~getdeb1_i386.deb
warsow-data_0.42-1~getdeb1_all.deb

from [http://www.getdeb.net/app.php?name=Warsow](http://www.getdeb.net/app.php?name=Warsow).
(This is a noble sacrifice in the name of science, mind you. I have no interest in warsow whatsoever except insofar as it shall help us explore the capabilities of dpkg. :rolleyes:)

```
% dpkg --info warsow_0.42-1~getdeb1_i386.deb 
<snip>
 Depends: libc6 (>= 2.6-1), libcurl3-gnutls (>= 7.16.2-1), libjpeg62, libkrb53 (>= 1.6.dfsg.1), libsdl1.2debian (>= 1.2.10-1), 
libvorbisfile3 (>= 1.2.0), libx11-6, libxext6, libxinerama1, libxxf86dga1, libxxf86vm1, zlib1g (>= 1:1.2.3.3.dfsg-1), mesa-utils, xbase-clients, 
**warsow-data** (= 0.42-1~getdeb1)
<snip>
```


Notice warsow-data is one of the packages upon which warsow depends.

So what if I say 

sudo dpkg -i warsow_0.42-1~getdeb1_i386.deb?

Will it install warsow-data first, or will it fail, complaining that warsow-data is not installed?

```
% sudo dpkg -i warsow_0.42-1~getdeb1_i386.deb
Selecting previously deselected package warsow.
(Reading database ... 169934 files and directories currently installed.)
Unpacking warsow (from warsow_0.42-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of warsow:
 warsow depends on warsow-data (= 0.42-1~getdeb1); however:
  **Package warsow-data is not installed**.
dpkg: error processing warsow (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 warsow 
```

This shows that dpkg is not smart enough to resolve dependencies.

I then tried to set up sources.list so that apt-get could work with a local directory filled with debs.
The reason why I tried to use apt-get to install the packages instead of dpkg is because I know apt-get is smart enough to resolve dependencies for me. 

I've never done that before and I've just found out its a bit more complicated than I made it out to be in my previous post. 

You need the right directory structure and a Package.gz file, a proper sources.list. I don't know how to do it... yet. Maybe a friendly neighborhood apt-wizard will be kind enough to show us the way...

---

### Post by unutbu on 2008-06-11
APT-wizard Capink has provided us with the solution: [http://ubuntuforums.org/showpost.php?p=3501424&postcount=3](http://ubuntuforums.org/showpost.php?p=3501424&postcount=3)!

In the commands below, change engine to your username, and
change /home/engine/dpkg-repack to the directory where you keep your debs.

```
export private=/home/engine/dpkg-repack
echo $private /home/engine/dpkg-repack
apt-ftparchive packages ${private} > ${private}/Packages
sed  --in-place 's_Filename: '${private}'/_Filename: _' ${private}/Packages
gzip -9c "${private}/Packages" > ${private}/Packages.gz
gksu gedit /etc/apt/sources.list
```

Add to the bottom:
```

deb file:///home/engine/dpkg-repack ./
```
```

sudo apt-get update
```

You will now be able to use your dpkg-repack directory just like any other official or unofficial repository. You'll be able to use Synaptic or apt-get, for example.

Instead of 

```
sudo dpkg -i *.deb
```

you can now

```
sudo apt-get install `cat installed-pkgs`
```
to install all .debs from your local repository and apt-get will install them all in an order which handles dependencies correctly and automatically.

---

### Post by abhiroopb on 2008-06-12
Ok I think the mistake you made was this: 
```

sudo dpkg -i warsow_0.42-1~getdeb1_i386.deb

```

No expert but this is basically telling dpkg to install warsow first. What I suggested was you do:
```

sudo dpkg -i *.deb

```

For whatever reason I think this scans the directory. Alphabetically warsow-data is lined up first so a better test may be needed. Now this isn't the best test, perhaps if you point me towards a prgoram that has a lot of smaller dependencies we can run a more thorough test.

Here is the output:
```

abhiroop@Vanimo:~/MyDownloads/New Folder$ sudo dpkg -i *.deb
Selecting previously deselected package warsow.
(Reading database ... 134783 files and directories currently installed.)
Unpacking warsow (from warsow_0.31.dfsg-6_i386.deb) ...
Selecting previously deselected package warsow-data.
Unpacking warsow-data (from warsow-data_0.31-1_all.deb) ...
Setting up warsow-data (0.31-1) ...
Setting up warsow (0.31.dfsg-6) ...

```

The key here is that you DON'T point it towards a certain file, but just tell it to do a general one.

Thanks for your tip though seems useful!

---

### Post by unutbu on 2008-06-12
I believe you are right! I just tried the following test:

graphviz depends on libgraphviz3.
So libgraphviz3 has to be installed first, but graphviz comes first alphabetically (unlike warsow and warsow-data, where I'm a bit unsure about the order in which "*.deb" is expanded).
```

sudo apt-get --download-only install graphviz libgraphviz3
```

This downloads graphviz_2.12-4ubuntu3_i386.deb and
libgraphviz3_2.12-4ubuntu3_i386.deb into /var/cache/apt/archives without installing them.

I then copied the debs into a test directory:
```
cp /var/cache/apt/archives/libgraphviz3_2.12-4ubuntu3_i386.deb /var/cache/apt/archives/graphviz_2.12-4ubuntu3_i386.deb .

sudo dpkg -i *.deb

Selecting previously deselected package graphviz.
(Reading database ... 170366 files and directories currently installed.)
Unpacking graphviz (from graphviz_2.12-4ubuntu3_i386.deb) ...
Selecting previously deselected package libgraphviz3.
Unpacking libgraphviz3 (from libgraphviz3_2.12-4ubuntu3_i386.deb) ...
Setting up libgraphviz3 (2.12-4ubuntu3) ...

Setting up graphviz (2.12-4ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

dpkg does seem to be able to sort out the dependency problem as long as all the required deb packages are listed at once (in the same command)! 

Thanks for helping me learn this, abhiroopb.

---

### Post by abhiroopb on 2008-06-12
No problem. So it seems that all it takes is putting ALL debs in one directory and running dpkg -i *.deb. But you have to make sure that all dependencies are in the directory.

---

### Post by blaz_boy on 2008-08-16
ok, thats good but how can i repackage a single program with it's dependences ? it's really urgent for me as i sometime want to transfere a program form my labtop to my friend labtop and i have no way ? could any one tell me ?

---

### Post by unutbu on 2008-08-16
On the friend's computer run
```

sudo apt-get install --simulate LIST-OF-PACKAGES

```
You don't have to have an internet connection to run this.

Here is an example of the output using the package 'kate':
```

% sudo apt-get install --simulate kate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdelibs-data kdelibs4c2a libarts1c2a libavahi-qt3-1 liblua50 liblualib50
Suggested packages:
  kate-plugins khelpcenter konsole fam
Recommended packages:
  kregexpeditor perl-suid libarts1-akode
The following NEW packages will be installed:
  kate kdelibs-data kdelibs4c2a libarts1c2a libavahi-qt3-1 liblua50
  liblualib50
0 upgraded, 7 newly installed, 0 to remove and 87 not upgraded.
```

Note this line:
```

The following NEW packages will be installed:
  kate kdelibs-data kdelibs4c2a libarts1c2a libavahi-qt3-1 liblua50
  liblualib50

```

This shows all the packages your friend would need to install kate.

Now go to your machine and type abhiroopb's commands (slightly modified):
```

sudo apt-get install dpkg-repack fakeroot
mkdir ~/dpkg-repack; cd ~/dpkg-repack
fakeroot -u dpkg-repack kate kdelibs-data kdelibs4c2a libarts1c2a libavahi-qt3-1 liblua50 liblualib50       # Just list all the packages you need
```

---

### Post by adept_king on 2008-10-28
is this just for .debs or is it for other installed things too?
does it also include things like drivers i installed like flash or restricted old drivers, etc?  if not, is there a method to encompass both?

is there a way to make a list of the programs i installed?  i dont know exactly where to look if i want a list of stuff like

envy
mysql
php
shorewall
wordpress
etc...

just want the programs i installed.  a list of everything i added.

---

### Post by Nausser on 2009-05-02
I've used this tool several times in the past and has always worked flawlessly until Jaunty came along.

Anyone know why this may be? 

Here is what the terminal spat back at me:

```
fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut
> -f1`
cut: you must specify a list of bytes, characters, or fields
Try `cut --help' for more information.
bash: -f1: command not found
Usage: dpkg-repack [options] packagename [packagename ..]
	--root=dir	Take package from filesystem rooted on <dir>.
	--arch=arch	Force the parch to be built for architecture <arch>.
	--generate	Generate build directory but do not build deb.
	packagename	The name of the package to attempt to repack.
renken@renken-desktop:~/dpkg-repack$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install
> 
```

I hope someone else has been brave enough to try Jaunty and came up with the same issue.

---

### Post by abhiroopb on 2009-05-13
are you putting cut -f1 on the same line?

it should be:

```

fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

```

from what you posted it seems to be doing:
```

fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut
> -f1`

```

---

### Post by bbowdry on 2009-05-13
Can you add remarks to this file such as date and information on how back and/or restore?

---

### Post by abhiroopb on 2009-05-13
> **bbowdry said:**
> Can you add remarks to this file such as date and information on how back and/or restore?

Not sure how this would be possible. But I suppose you could create another list with all the packages (in one txt file) that has the information you require. When I remember how to do this I will let you know!

---

### Post by hero1900 on 2009-05-21
thanks it was very helpful i was looking for it

---

### Post by Cuba71 on 2009-07-29
I finished repackaging my Jaunty, a total of 1,425 pkgs in 942 MB of storage.
It took about 3 hours and I did get a couple of error messages indicating broken packages.  I have to assume that my system was not utilizing these broken packages.

---

### Post by unutbu on 2009-07-29
Cuba71, if you have ever uninstalled a package then when you run
```

fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```

you will get an error because 
```

dpkg --get-selections | grep install | cut -f1
```

will list "deinstalled" packages as well as "installed" packages.

A way to avoid this problem is to run
```

fakeroot -u dpkg-repack $(aptitude -F '%p' search '~i')
```

instead, because unlike the dpkg command
```

aptitude -F '%p' search '~i'
```

will list installed packages only.

---

### Post by Cuba71 on 2009-07-29
unutbu:
I see where I made the mistake.  I think I could've used:

```

fakeroot &#8211;u dpkg-repack `dpkg &#8211;get-selections | grep -v deinstall | cut -f1`

```

to eliminate the "deinstall" packages

---

### Post by atoztoa on 2009-12-08
> **PinkFloyd102489 said:**
> Wouldnt it just be easier to do this?

```

To make the list:
sudo dpkg --get-selections > installed-software

To restore packages:
sudo dpkg --set-selections < installed-software

```

This gives you the list of packages without all of the deb files. Mind that you'll need an internet connection, but most computers do.



EDIT: installed-software is a file btw. It just acts as a list that you pipe back into the dpkg command so it will know what packages to download.

How will you install the packages after set-selections?

If you use dselect, it will remove any installed packages which are not in the list...

---

### Post by atoztoa on 2009-12-08
> **abhiroopb said:**
> No problem. So it seems that all it takes is putting ALL debs in one directory and running dpkg -i *.deb. But you have to make sure that all dependencies are in the directory.

I had once tried that command for the .deb files generated by APTonCD. It worked for some time and showed lots of errors and finally told... "Too many errors" and aborted.

The next time I restarted, X-windows wont load... I had to reinstall Ubuntu :(

Be careful...

---

### Post by herophuong on 2010-07-23
I think we should use
> dpkg -E -i *.deb
to ignore all the packages have the same version with the installed packages.

---

### Post by farmerjohn73 on 2010-08-20
```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```

(the last command will take some time)


When I tried the third command, it says 

Unknown option: --get selections

and displays some options with --

what should i do to resolve this?

---

### Post by ironic.demise on 2010-08-20
> **abhiroopb said:**
> [COLOR="Red"][SIZE="4"]PROBLEM:[/SIZE][/COLOR] Lets say you have set up your *buntu box. Now you want to backup all the installed deb files so that you can restore them quickly and efficiently.


Interesting, might come in handy someday, +1

---

### Post by vahidasadi on 2010-08-24
hi guys
[could anybody help me please ]("http://ubuntuforums.org/showthread.php?p=9760426#post9760426") it is related to this thread
thank you;)

---

### Post by lbrty on 2010-09-01
> **abhiroopb said:**
> 
```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```


Great tips! This is exactly what I was looking for! When I entered the first command:
```
sudo apt-get install dpkg-repack fakeroot
```I received this:
```
sudo apt-get install dpkg-repack fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dpkg-repack
```What do I need to do?

I then continued and received this:
```

sudo apt-get install dpkg-repack fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dpkg-repack
mkdir ~/dpkg-repack; cd ~/dpkg-repack
~/dpkg-repack$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
/usr/bin/fakeroot: line 176: dpkg-repack: command not found
~/dpkg-repack$ 
```Thanks in advance!

---

### Post by lbrty on 2010-09-04
I was able to get it to work. Thanks for this post abhiroopb!

---

### Post by Toxicbits on 2010-09-05
Hi, 
I'm looking for an option to get a list of all the packages I installed additionally to the ones which were selected from the beginning. I found computer janitor which gives me a list of all .deb files I installed manually, but I also want a list for the apps I got from the software center. Is there any way to exclude the pre-installed packages from the list?

Thanks in advance Toxicbits

---

### Post by dcstar on 2010-09-12
> **Toxicbits said:**
> Hi, 
I'm looking for an option to get a list of all the packages I installed additionally to the ones which were selected from the beginning. I found computer janitor which gives me a list of all .deb files I installed manually, but I also want a list for the apps I got from the software center. Is there any way to exclude the pre-installed packages from the list?

Thanks in advance Toxicbits

There is a utility call apt-log (web search for it) which will list all the package changes made since system installation.

---

### Post by Black_Tanto on 2010-09-21
I am not sure I understand how this works.


Anyway, I am not trying to back up my installed files so much as I am trying to copy all of the installed files found on one distro and transplant them to another....the files that came on the ISO rather than the ones I added personally, then dropping them onto my own custom remix as deb files.



Is there a technique for this?

---

### Post by lbrty on 2010-09-21
> **Black_Tanto said:**
> I am not sure I understand how this works.

Anyway, I am not trying to back up my installed files so much as I am trying to copy all of the installed files found on one distro and transplant them to another....the files that came on the ISO rather than the ones I added personally, then dropping them onto my own custom remix as deb files.

Is there a technique for this?

The OP stated exactly how to do what you are trying to achieve. The only difference is wording really. Follow the directions in the OP and you will have all the .deb files in one folder. Copy that folder onto a USB drive (or another storage medium) and then plug the storage medium into the other computer you wish to install the programs you had on the original computer.

Use the terminal on the computer that does not have the .deb files installed on, navigate to the directory in which you copied the .deb files to and execute the command below. This command will install all the .deb packages on the new computer.

```
sudo dpkg -i *.deb
```

---

### Post by Black_Tanto on 2010-09-22
That is what I wanted to hear.

---

### Post by Black_Tanto on 2010-09-22
> **linuxliberty said:**
> The OP stated exactly how to do what you are trying to achieve. The only difference is wording really. Follow the directions in the OP and you will have all the .deb files in one folder. Copy that folder onto a USB drive (or another storage medium) and then plug the storage medium into the other computer you wish to install the programs you had on the original computer.

Use the terminal on the computer that does not have the .deb files installed on, navigate to the directory in which you copied the .deb files to and execute the command below. This command will install all the .deb packages on the new computer.

```
sudo dpkg -i *.deb
```


The reason I doubted this is because he said it did what AptonCD did, which does NOT meet my needs. It only downloads the apps I downloaded myself, not the ones the installation disk installed for me. Thats the difference and the reason I am looking for an alternative.

---

### Post by Black_Tanto on 2010-09-22
So, if I want to make a GUI program to do this for myself in the future, is there a tool where I can just enter the commands and tell it to execute them for me when I press a button?


This is really useful.

---

### Post by lbrty on 2010-09-22
> **Black_Tanto said:**
> So, if I want to make a GUI program to do this for myself in the future, is there a tool where I can just enter the commands and tell it to execute them for me when I press a button?

Since there are only three lines of commands that one enters to recreate the .deb packages and a one line command to re-install the packages, I did not search for a GUI program to automate this simple process. But there probably is someone in the Linux community that has done this already.

Creating the .deb packages
```
sudo apt-get install dpkg-repack fakeroot
mkdir ~/dpkg-repack; cd ~/dpkg-repack
fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```Re-Install
```
sudo dpkg -i *.deb
```

---

### Post by Black_Tanto on 2010-09-22
The app I want to learn how to make would do several things, this being just one of them. I have never been good at remembering strings of code without it being written down somewhere. Im trying to speed up the human portions of certain tasks rather than the computer, since I am usually the bottle neck rather than my computer.

---

### Post by azertyh on 2010-12-31
hello,

good howto. an alternative to aptoncd.

i got an error on installing dpkg-repack. the package libstdc can't be installed, it hangs at the last step of the installation. i solved by upgrading the package.

thanks for sharing.

i made the backup. if i want to remake it, say one month later, how to select only the packages that i install after the previous backup?

---

### Post by fryle on 2011-01-11
I backed up all my softwares using this procedure told by abhiroop. It constitutes something like 6 gbs of them. Now after reinstallation of ubuntu on a new comp when i tried sudo dpkg -i *.deb It says  that possible length exceeded or something like that. What should I do???
I think the no. of softwares is huge (Its around 4000). 
So I tried 
sudo dpkg -i [abcdef]*.deb 
It tries to install all softwares starting with a,b,c,d,e,f but The problem of dependecy resolving occurs. I mean yeah there may be some softwares with dependencies starting with letters g, h or whatever. 

If I go like this for abcdefg and then next time hijklmn and so on, This process will always miss a lot of softwares. 
So it would be really difficult to figure out what has been installed and what not.. 

(I am using UBUNTU 10.10 amd 64)
Please help!!! Please...

---

### Post by EnigmaticCoder on 2011-02-03
I think this will work for you, fryle. You can solve the issue of aptoncd not finding all your packages, and then use it to restore your installed packages instead of dpkg. 

The OP said
> 
NB: I know AptonCD does this but what prompted me to use this method was that I had done the sudo apt-get clean command which had erased all the files in the /var/cache/apt directory, rendering AptonCD useless (as all it does is take the files from there and put it in the list). So I find this method is more efficient, and easier for me to control!


But, if you use aptoncd in combination with the method described in the OP, you can get the benefits of aptoncd and still backup all your packages.

Use the commands that were given in the OP to backup your packages:

```

$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep -v deinstall | cut -f1`

```
#Note that I use grep -v deinstall instead of grep install

Now that you have a directory with all your packages, use aptoncd:

```

$ sudo apt-get install aptoncd
$ aptoncd --cache-dir ~/dpkg-repack/

```

Then use the aptoncd GUI to backup your packages to ISOs. Make sure metapackage is selected when you create the ISOs so that you can install everything at once (you'll see this option when you click the "Burn" button).

After the ISOs have been created, mount one with the archive manager:
Open Nautilus | Navigate to ISO | Right Click | Open with Archive Mounter

Run the aptoncd-metapackage:
Places | aptoncd | packages | aptoncd-metapackage

That should work, but I want to put a disclaimer that I haven't personally restored packages this way.

---

### Post by maungperfect on 2011-02-04
> **abhiroopb said:**
> 
Open a terminal and paste the following into it:

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```(the last command will take some time)

Now if you scroll to your home folder, you should find a folder called "dpkg-repack" which should have all the deb files of all your installed packages.

[B]
RE-INSTALL[/B]
If you want to re-install the packages, navigate to the folder with the packages and input the following command in the terminal:
```
sudo dpkg -i *.deb
```Thanks to [https://answers.launchpad.net/aptoncd/+question/15592/+index](https://answers.launchpad.net/aptoncd/+question/15592/+index) (Rafael)
Good Day Everybody.
After finish backup my programs, I was open my backup folder.
There is a lot of .deb file.
For example I want to restore cairo-dock, I have found many .deb file name with cairo dock.

cairo-dock_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_all.deb
cairo-dock-core_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_i386.deb
cairo-dock-data_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_all.deb
cairo-dock-plug-ins_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_i386.deb
cairo-dock-plug-ins-data_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_all.deb
cairo-dock-plug-ins-integration_2.2.1~0alpha0-20101002-0ubuntu1~ppa0~lucid_i386.deb

Which deb file  I have to add for restoring cairo-dcok?
```
sudo dpkg -i [COLOR=DarkRed]*.deb[/COLOR]
```======================

And the next one is I'm really love to use CLI.
So I want to understand following command
```
 sudo apt-get install dpkg-repack fakeroot
```

I already know, sudo apt-get install and dpkg-repack is package name.
But I don't know what is fakeroot

I have search in
```
man dpkg-repack
```But I can not find about that.

Please somebody explain for me.
Thanks A Lot

---

### Post by farmerjohn73 on 2011-02-17
I think [this method]("http://ubuntuforums.org/showthread.php?t=688872") is also working well, even though it is taking a little time.  'coz a dumb noob like me could do it !  :D

---

### Post by rvchari on 2011-02-17
thats great abhiroop...
i am sure it will be a very useful tool to have a bckup like this and issue a single command for re-install !!!

---

### Post by lingyizhenyi on 2011-02-23
is it possible to backup only certain programs instead of all of them?

---

### Post by texinfo on 2011-03-06
Yeah this is an oldschool answer! ;)

But I have a newschool question! :confused:

I just backed-up my debs using dpkg-repack... something seems to be fishy here... I checked the result of... ```
dpkg --get-selections | grep install | cut -f1
``` ... there where 2574 line of package names... but when I check the result of...```
ls
``` ... there where 2564 line .deb files...!!! 

Please have a look at this... and tell me a little about it...

---

### Post by L Campbell on 2011-07-27
> **abhiroopb said:**
> [COLOR="Red"][SIZE="4"]PROBLEM:[/SIZE][/COLOR] Lets say you have set up your *buntu box. Now you want to backup all the installed deb files so that you can restore them quickly and efficiently.

[COLOR="Red"][SIZE="4"]UPDATE: Why would you want this?[/SIZE][/COLOR]
When I was using windows I had a directory of EVERY Single program that I had downloaded. For one thing it would be easier to install everything as I would not have to go online and hunt for them. Further it would be useful where a computer does not have internet connection. In ubuntu "hunting" for programs is a rare occurrence thanks to the fantastic package managing system. However, I personally have about 20-30 programs that I have either compiled from source (using checkinstall, so that that a deb package is created and they are added to APT), or downloaded debs from obscure locations. Now each of these debs I will save in a directory so that in the future I do not have to go hunting for them. However, this command I have outlined backs up ALL packages, including the ones in the package manager. So, why would you want that? 

Firstly, this is VERY useful if lets say you have setup a very basic installation with all updates, and all non-free video/audio/etc codecs. Further you have installed some basic useful software. Now lets say you want to install the SAME setup on your grandmothers computer, except she does not have internet connection, or at the time you go to set it up she does not have a net connection. Using this script you can have all your debs in one simple location, so you will not have to redownload everything.

Secondly, lets assume you work for a school, or a company, and you need to install the SAME ubuntu installation on 30 computers. Wouldn't it be easier to simply put all these debs in a central server and issue the dpkg -i *.deb command. This way you don't have to individually select the packages AND the packages don't have to download.

Thirdly, (and this is purely personal) I like to be able to have all my installed packages at hand. This command doesn't take much effort, and for me it only requires 1.4 gb of space, so for a bit of piece of mind I can easily have all my packages on hand.

There is no real reason to do this if you are already doing a full system backup (e.g. an image of your Ubuntu partition using partimage). This is just something I discovered and feel could be beneficial to other users.

These commands will do that for you.

Open a terminal and paste the following into it:

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```

(the last command will take some time)

Now if you scroll to your home folder, you should find a folder called "dpkg-repack" which should have all the deb files of all your installed packages.

[B]
RE-INSTALL[/B]
If you want to re-install the packages, navigate to the folder with the packages and input the following command in the terminal:
```
sudo dpkg -i *.deb
```

Thanks to [https://answers.launchpad.net/aptoncd/+question/15592/+index](https://answers.launchpad.net/aptoncd/+question/15592/+index) (Rafael)

NB: I know AptonCD does this but what prompted me to use this method was that I had done the sudo apt-get clean command which had erased all the files in the /var/cache/apt directory, rendering AptonCD useless (as all it does is take the files from there and put it in the list). So I find this method is more efficient, and easier for me to control!

Hi, this looks very interesting, so I followed the instructions and now have a folder called "dpkg-repack" in my home folder.

However, when I try to re-install, I keep getting this result:-

qwer@qwer-desktop:~$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
qwer@qwer-desktop:~$ 

I would really appreciate a suggestion here, as I am confused.

TIA

---

### Post by grubu on 2011-07-28
Hello Lewis,

this is just a small mistake, you should enter into the path you created for the packages by: 
```

cd ~/dpkg-repack

```just open your terminal and type that in, you should then get onto a prompt called:
[highlight]
qwer@qwer-desktop:~/dpkg-repack$
[/highlight]

try an "ls" to verify if the .deb-packages are in there and if so just do the:

```

sudo dpkg -i *.deb

```again and you should be fine.

Thanks to [abhiroopb]("http://ubuntuforums.org/member.php?u=92445") for this nice guide.

---

### Post by Suhel28 on 2011-09-24
;)I just want to ask one question,
 
does this tutorial require use of internet anywhere?! If I'm understanding it right it will recompile all the pkgs into resp deb files right?!

---

### Post by cmcanulty on 2012-01-14
PinkFloyd where will the file be after I run the get selections?

---

### Post by kamaradski on 2012-02-16
I'm wondering if all my personal settings are being saved too?

- settings of widgets on screen etc
- Settings of programs like Skype
- Any manual created\edited setting-files like Unison profiles, etc..


KR
kamaradski

---

### Post by zaverisaahil on 2012-02-19
Really helpful post , can i post on my blog for other readers to get this valueable info....:D

---

### Post by marbertone on 2012-02-21
Hi everybody!
An information please: is it possible to put an option in dpck-repack in order not to overwrite already extracted .debs? Or, alternatively, to resume the process (it lasts 12h on a VAIO Dual 2.2Ghz 2GB RAM laptop, it will be useful in my modest opinion). 
Best regards!
M.

---

### Post by tumutanzi.com on 2012-05-19
To late for me. I have already re-installed Ubuntu 12.04 after the failure upgrade from 10.04.

---

### Post by goaliedude3919 on 2012-05-23
This sounds like a great and easy alternative to creating a custom Live CD/USB. This is something that will definitely be useful for reinstallation or installation on another machine.

---

### Post by Simeo on 2013-02-19
Hello, this is exactly what I was looking for. Could somebody please verify this still works with Ubuntu 12.10 (because it's an old thread). 

Thank you.

---

### Post by kamaradski on 2013-02-19
Yes it does work in 12.10.

I will take the liberty to promote my own post here and link you to a set-by step on how i personally implemented this:

[http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux](http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux)

---

### Post by Simeo on 2013-02-19
> **kamaradski said:**
> Yes it does work in 12.10.

I will take the liberty to promote my own post here and link you to a set-by step on how i personally implemented this:

[http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux](http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux)

Sweet. Thank you for the confirmation.

---

### Post by shouso_boy on 2013-09-05
> **kamaradski said:**
> Yes it does work in 12.10.

I will take the liberty to promote my own post here and link you to a set-by step on how i personally implemented this:

[http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux](http://kamaradski.com/818/how-to-backup-your-installed-software-on-ubuntu-based-linux)

yes,it is work on Debian Wheezy too, but with -w option on grep, because without -w option, grep also get packages with deinstall status, dan dpkg-repack doesn't work with deinstall status packages

this is my blog posting

[http://attaqi.com/2013/09/wheezy-backup-paket-yang-terinstall.html]("http://kougarku.blogspot.com/2013/09/wheezy-backup-paket-yang-terinstall.html")

---

### Post by david98 on 2013-10-18
Thank you this is going to save me a lot of time as i need to set up 3 identical laptops ):P

---

