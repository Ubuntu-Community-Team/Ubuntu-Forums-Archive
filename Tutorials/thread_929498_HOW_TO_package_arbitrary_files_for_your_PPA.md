---
title: "HOW TO package arbitrary files for your PPA"
date: 2008-09-25
forum: Tutorials
---

### Post by Pro-reason on 2008-09-25
This tutorial necessarily assumes that you have a PPA (Personal Package Archive) on Launchpad.  This involves:
[LIST]
[*]creating a [Launchpad account](https://launchpad.net/ubuntu/+ppas/+login)
[*]setting up a [GPG key](https://help.launchpad.net/YourAccount/ImportingYourPGPKey)
[*]signing the [code of conduct](https://help.launchpad.net/BecomingAnUbuntero)
[/LIST]
The official documentation is at [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) and [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete).

The first thing that newbie packagers will notice is that a lot of the documentation assumes that you already have a basic understanding of compiling code, writing makefiles, and the packaging process.  It also assumes that you want to package quite complex stuff.  All this may be true, but what if you're just trying to package a picture or a bash script?

This tutoral walks you through every step of doing that basic packaging work.

---------------------

Let's say that you have written a script with the following content:

```

#!/bin/bash
*echo "Hello, world!"*

```

You could just save it as /usr/local/bin/helloworld.sh.  However, you want to share your fabulous code with the world.  This is how you do it.

First, make a directory for your code.  It needs to end in the version number of the software.  We will be creating files both inside this directory and also one step above it.

```

mkdir -p ~/PPA/helloworld/helloworld-1.0/
cd ~/PPA/helloworld/helloworld-1.0/

```

Put your script in that directory.

Put any documentation you have written in there too.

If you just wanted to distribute source code, you could at this stage just archive this directory as *helloworld-1.0.tgz* and send it to people, but we want to go further than that.

The key to Debian/Ubuntu packaging is the &#8220;*debian*&#8221; directory.  So let's create it.

```

mkdir debian
cd debian

```

There are a few files that we need to put into this directory.  Let's create them all:

```

touch *changelog compat control copyright install rules*
gedit * &

```

All the files will now be open in gedit, in various tabs.

Go to the *changelog* tab, and put something like this:

```

*helloworld* (*1.0*-0ubuntu1~ppa1) hardy; urgency=low

  * Initial release

 -- *Joe Bloggs <j.bloggs@example.com>  Sun, 01 Jan 2000 01:01:01 +0000*

```
The version number should be constructed like this: 
[LIST]
[*]First, you have the version of the actual software.  If it's your own, then you get to decide what version it is at.  Let's say it is &#8220;1.0&#8221;.
[*]Then, we put a hyphen and the Debian version number.  Since this is your own stuff, you know that it is not in Debian, so we put a zero.
[*]The, we write &#8220;ubuntu1&#8221;, because this is the first version of it available for Ubuntu.
[*]Then, we put &#8220;~ppa1&#8221;, to say that this is the first PPA version.
[/LIST]
Put the same e-mail address that you gave when you created your Launchpad account.  It must have a GPG fingerprint associated with it.

To get the correct date, type &#8220;date -R&#8221; on the command line.  Copy and paste it into the file.  In must be in that format exactly.

Go to the *compat* tab, and put this:

```

5

```

Go to the *control* tab, and put this:

```

Source: *helloworld*
Section: utils
Priority: extra
Maintainer: *Joe Bloggs <j.bloggs@example.com>*
Build-Depends: debhelper (>= 5), cdbs (>= 0.2)
Standards-Version: 3.8.0

Package: *helloworld*
Architecture: all
Depends: ${shlibs:Depends}, ${misc:Depends}, *bash (>= 2)*
Description: *Prints a pointless message*
[I] This is a long description of the package and most of
 the stuff it does.  I don't want each line to be more
 than about 50 or 60 characters.  Each line starts with
 a space.
 .
 If I need to make a new paragraph, I have to put a dot
 as you can see above.[/I]

```
Depending on what you are packaging, you may need to change the section to something other than &#8221;utils&#8221;.

I have added &#8220;bash&#8221; to the dependencies, because this is a bash script.  Specify a recent version of bash if your script uses some new feature of bash.  Also specify any other programs which are called by your script.  For example, if your script compresses something with bzip2, then you would add &#8220;bzip2&#8221; as a dependency.

Go to the *copyright* tab, and put something like this:

```

This package was debianised by *Joe Bloggs <j.bloggs@example.com>* on
*Sun, 01 Jan 2000 01:01:01 +0000*

It can be downloaded from *https://launchpad.net/~joebloggs/+archive*

Upstream Author: 

    *Joe Bloggs <j.bloggs@example.com>*

Copyright:
[I]
    This software (including its Debian packaging)
    is under the copyright of the above author.[/I]

Licence:
[I]
    This software (including its Debian packaging)
    is available to you under the terms
    of the GPL-3, see "/usr/share/common-licenses/GPL-3".
    You can also use it under the terms of any other GPL version.[/I]

```
Put the name and e-mail exactly as in the *changelog* file.  Also enter the date in the same way.  Include the actual copyright and licence of the software.  It must be under a Free licence.

If you are not packaging your own work, then you have to be slightly more careful, making sure that everything in the package is properly licensed.

For the &#8220;downloaded from&#8221; address, you normally put the address that you found the source code at.  If it is your own, then you give your website (where people can download the source code).  If you have created the code just to upload it to Launchpad, then your full Launchpad URL is probably the most sensible website to give.

Go to the *install* tab, and put something like this:

```

helloworld.sh			/usr/bin/

```
As you can see, this is a file that consists of lines which consist of: a file in your package directory, some spaces or tabs, and then the location that they will be installed to.  There can be as many lines as you need.

The proper place for most executable files is */usr/bin/*.  Do your research to find out where other files ought to go.  A GRUB background picture would go in */boot/grub/splashimages/*, for example.  Make sure that the files installed by your package do not clash with those installed by those in any other commonly used package.

Go to the *rules* tab, and put something like this:

```

#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk

binary-install/*helloworld*::
	dh_icons

binary-fixup/*helloworld*::
	dh_gconf --priority=16

```
With most packages, this is a bit complicated.  However, since we have nothing to compile, we can use a nice simple *rules* file like this.

Save all, and close.  

Return to your terminal, and exit the debian directory:

```

cd ..

```
Into this directory you can now put a file called &#8220;README&#8221; with any basic notes about the package; a file called &#8220;THANKS&#8221; with any people who really helped with the software; a file called &#8220;COPYING&#8221; with the full text of the licence under which the software is released; and a file called &#8220;AUTHORS&#8221; with the names and e-mail addresses of the people who wrote the software (you, in this case).  These are files that are expected to be in any tarball of source code anyway.  They aren't specifically to do with Debian packaging.  That's why they aren't in the *debian* directory.

Now make sure that you have the software needed to work with Launchpad:

```

sudo apt-get install devscripts dput

```

Now let's prepare this stuff for Launchpad:

```

debuild -S

```

That will take a while to complete, and spit out a load of info.  If there is an error, then you messed something up.  Go to the top of this guide and check that you did each step properly.

At the end, debuild will ask your for your GPG password so that it can sign the package with your name.  This is for security.  Launchpad won't accept unsigned stuff.

If all goes well, debuild will have created several files in the parent of the current directory.  In our case, this is *~/PPA/helloworld*.

You can now do &#8220;*ls ..*&#8221; or &#8220;*cd .. && ls*&#8221; to check that the files are indeed there.

Let's make sure that your computer knows where to upload the stuff.  Do this:

```

gedit ~/.dput.cf

```

In the window that comes up, paste the following:

```

[my-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~*joebloggs*/ubuntu/
login = anonymous
allow_unsigned_uploads = 0

[DEFAULT]
default_host_main = my-ppa

```
Change &#8220;*joebloggs*&#8221; to your actual Launchpad ID.  Save and close.

Now upload your work to Launchpad:

```

dput my-ppa *~/PPA/helloworld_1.0-0ubuntu1~ppa1_source.changes*

```

As you can see, you have to point the dput command at the *.changes* file that you have just created.  It won't upload just that file though; it will also upload the source-code tarball.

A few minutes later, you'll get an e-mail from Launchpad saying that the package has been accepted and added to the queue.  It could take anything from a couple of minutes to a couple of hours for your source code to be turned into an actual .deb package and be available in your PPA.

Relax and have a cup of tea, and think about which friends you'll brag to about your new techno-skills.

---------------------

There is more to learn than this, but my assumption is that you need the psychological boost of successfully packaging something, and that after all this you will look into learning how to tweak this for more complex tasks.

---

### Post by swegner on 2008-09-26
Is it really necessary to create a whole .deb package to distribute some arbitrary files or a shell script?  Seems like a lot of work where a simple FTP would do the trick.

Or, if you're intent on using Launchpad, why not start a new project (named, perhaps, "[username]s-files"), and use the bzr version control to upload and distribute your files.

It just seems like a lot of extra work to create all of the extra debian/ files.  Also, having a more general interface (FTP or bzr) allows users more flexibility in downloading and installing your files.

---

### Post by Pro-reason on 2008-09-26
> **swegner said:**
> Is it really necessary to create a whole .deb package to distribute some arbitrary files or a shell script?

Yes.  Look in Synaptic.  There are hundreds of packages that involve no compiling.  They contain images, dictionaries, scripts, documentation, or are even empty metapackages.  If you disagree with my tutorial, you're disagreeing with Ubuntu!

Using bzr instead of a repository excludes the vast majority of Ubuntu users.  Ubuntu software is centred around APT repos.  Your approach is more appropriate for Slackware.

---

### Post by swegner on 2008-09-27
Your approach seems most appropriate for files and packages you assume will be universally applicable and well-distributed.  If you are just sharing "arbitrary files", then sometimes it doesn't make sense to create a whole package for it.  For example, does it make sense to download via apt "someguy-resume", or just grab the resume from a website or FTP?

It's true that there are many packages which already exist that don't need to be compiled.  However, these generally relate to some sort of existing functional package (themes for GDM, documentation for GIMP, screensaver packs for xscreensaver, etc.).  These packages are generally installed at some system location that makes sense for the application.  But individual users' files should really live in the home directory, and shouldn't need administrator privelages to add/delete/modify.

The other main downside is the cost of set up.  It does take quite some time to register for Launchpad and a PPA, set up a development environment, and create the packaging files to get them ready to upload.  Then you require users to actually add your PPA to their sources list (which implies that they really need to trust you), and then finally download the package.

In general, I think in determining whether files are appropriate for a PPA, you need to consider the scope and audience of the files.  I agree that there are instances where this could be beneficial, but not as a general case.  If the files are mostly for personal use, then why go through the trouble?

---

### Post by Pro-reason on 2008-09-27
> **swegner said:**
> If the files are mostly for personal use...
What on earth are you talking about?  Please go away.

---

### Post by SeanHodges on 2008-09-29
Good HOW-TO, thanks for that.

I'd just point out that the "dh_make" script provided by the dh-make package will nearly half the steps you've given for creating the package.

A quick and dirty run-down on how to use it:

```

$> sudo apt-get install dh-make
$> mv test test-1.0.0 && cd test-1.0.0
$> dh_make --single --native --email seanhodges@bluebottle.com

Maintainer name : Sean Hodges
Email-Address   : seanhodges@bluebottle.com 
Date            : Mon, 29 Sep 2008 18:18:21 +0100
Package Name    : test
Version         : 1.0.0
License         : gpl
Type of Package : Single
Hit <enter> to confirm: 
Currently there is no top level Makefile. This may require additional tuning.
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the test Makefiles install into $DESTDIR and not in / .

$> rm debian/*.ex debian/*.EX
$> ls
debian  test.sh
$> ls debian/
changelog  compat  control  copyright  dirs  docs  README  README.Debian  rules

```

This would avoid people needing to create all the necessary files, and set up things like the package compat value.

Of course, you may already be aware of this and gave the long-winded approach to describe the package files in more detail. Either way, I love these "get started quickly" HOWTO's, and this one is pretty easy to follow.

---

### Post by Pro-reason on 2008-09-29
> **SeanHodges said:**
> Good HOW-TO, thanks for that.

I'd just point out that the "dh_make" script provided by the dh-make package will nearly half the steps you've given for creating the package.


Yes, I started by using those scripts that create the necessary structure.  However, you then have to go back over it, deleting unnecessary files and editing the others. It doesn't actually set things up the way you need.

I would have appreciated a guide that explained things from the bottom up, rather than cutting from the top.  A guide that explained each file necessary to package arbitrary files, and nothing else.  So, I wrote that guide.

---

### Post by SeanHodges on 2008-09-30
> **Pro-reason said:**
> Yes, I started by using those scripts that create the necessary structure.  However, you then have to go back over it, deleting unnecessary files and editing the others. It doesn't actually set things up the way you need.

Personally I find it quicker and less error-prone to edit some skeleton files than create them from scratch each time, but the scripts are probably a matter of taste, especially when getting used to the packaging process.

If your intention was to explain the files from the bottom up, then I agree avoiding scripts like dh_make was the better strategy.

---

### Post by RATM_Owns on 2008-10-05
> Now signing changes and any dsc files...
 signfile yt2mp3_1.0-0ubuntu1~ppa1.dsc Andrew Kiss <xanga9885@hotmail.com>
gpg: skipped "Andrew Kiss <xanga9885@hotmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1250:
running debsign failed
andy@comp ~/Projects/yt2mp3/yt2mp3-1.0 $ 

...what?

---

### Post by Pro-reason on 2008-10-05
> **RATM_Owns said:**
> ...what?

Have you [registered a public encryption key]("https://help.launchpad.net/YourAccount/ImportingYourPGPKey") for the address &#8220;xanga9885@hotmail.com&#8221;?  This is required for security reasons.

---

### Post by loell on 2008-10-05
yeah, one of the hurdles in setting up a PPA is setting up your pgp key, once you're past it, then you'll be fine. :)

but the preferred builder for PPA's are those who have some participation in launchpad itself, that way PPA users can do a background check on your previous activities and contributions.

---

### Post by RATM_Owns on 2008-10-05
Yep. I've sent my new one in about 3 or so days ago?
It's all verified and everything.

---

### Post by Pro-reason on 2008-10-05
> **RATM_Owns said:**
> Yep. I've sent my new one in about 3 or so days ago?
It's all verified and everything.

And debsign is still failing?  Forgetting Launchpad for a moment, can you encrypt files on your computer?

---

### Post by RATM_Owns on 2008-10-05
Yep. I can.

---

### Post by loell on 2008-10-05
I seem to recall this kind of problem, atleast in my case and few others that debsign will fail, even if you import back your uploaded pgp key to your pc, normally it shouldn't, i bet you can even encrypt a file using the particular pgp key but debsign still fails.

so, what I did , I created another personal pgp key with the **ultimate trust**.

you can do that in **seahorse** easily, then sync it or publish that key to the pgp servers, then add your newly created key in your launchpad account, even if you have previous key(s) in your launchpad that should be fine as you can add multiple pgp keys in your account.

because  it's a personal key with the ultimate trust, debsign should succeed.

---

### Post by RATM_Owns on 2008-10-05
Mine already had ultimate trust.

---

### Post by loell on 2008-10-05
> **RATM_Owns said:**
> Mine already had ultimate trust.

hmm, after re-reading your previous post and looking at your archive,

do you mean to say that debsign fails now, after you've  uploaded some packages in your PPA?

---

### Post by RATM_Owns on 2008-10-05
No, I mean debsign has always failed, as those are copied. :P

---

### Post by loell on 2008-10-05
> **RATM_Owns said:**
> No, I mean debsign has always failed, as those are copied. :P

I see, :biggrin:


so in seahorse, are you seeing that key in the "My personal Keys" tab?

---

### Post by RATM_Owns on 2008-10-05
Yep.

---

### Post by loell on 2008-10-05
could this most probably be a typo?

you typed in

```
Andrew Kiss <xanga9885@hotmail.com>

```

but your complete PGP key adress is

```
Andrew Kiss [COLOR="Red"](I Own)[/COLOR] <xanga9885@hotmail.com>

```

---

### Post by RATM_Owns on 2008-10-06
That worked.

Now I feel retarded. :P

---

### Post by loell on 2008-10-06
> **RATM_Owns said:**
> That worked.

Now I feel retarded. :P

heheh.. :D 

probably more than half of ppa builders made that mistake.

I did too.. :tongue:

---

### Post by RATM_Owns on 2008-10-06
Well I made a easy script just to automate most of it.

```
#!/bin/bash
echo "Name of project? (i.e. helloworld)"
read pname
echo "Version of $pname? (i.e. 1.0)"
read pversion
clear
zenity --info --text="Please move the script into ~/Projects/$pname/"
mkdir -p ~/Projects/$pname/$pname-$pversion/debian/
cd ~/Projects/$pname/$pname-$pversion/debian/
touch changelog compat control copyright install rules
clear
zenity --info --text="Please edit the files according to http://ubuntuforums.org/showthread.php?t=929498"
gedit * &
cd ..
debuild -S
clear
echo "You can now upload the files to LaunchPad via dput."
```

---

### Post by loell on 2008-10-06
extend your automation to dput by capturing debuild -S  output and getting the changes file. :)

---

### Post by RATM_Owns on 2008-10-06
...um...

Can you put that into idiot terms for me?

You have 1000 posts, I have 100.
You're more [experienced]("http://www.youtube.com/watch?v=SaZJFWOEzrc") than I am.

---

### Post by Pro-reason on 2008-10-06
> **RATM_Owns said:**
> ...um...

Can you put that into idiot terms for me?

You have 1000 posts, I have 100.
You're more [experienced]("http://www.youtube.com/watch?v=SaZJFWOEzrc") than I am.

If you just add this:

```
dput my-ppa ../*.changes

```
...it will work if there are no other *changes* files cluttering the parent directory.  (I always keep that directory clean.)

You'd need something a bit more complicated if you need to distinguish.

---

### Post by InfinityCircuit on 2008-10-07
debhelper 7 and devcscripts will make this much much much simpler, if someone didn't point it out already:

compat = 7

debian/rules:

```
#!/usr/bin/make -f

%:
        $@
```

dch -i to make changelog entry

Just add copyright and control and install and you're done.  No need to rely on cdbs.

---

### Post by RATM_Owns on 2008-10-07
> **Pro-reason said:**
> If you just add this:

```
dput my-ppa ../*.changes

```...it will work if there are no other *changes* files cluttering the parent directory.  (I always keep that directory clean.)

You'd need something a bit more complicated if you need to distinguish.

The script sets a variable for the project name, pname so I can do
```
dput my-ppa ~/Projects/$pname/$pname*.changes
```New script:
```
#!/bin/bash
echo "Name of project? (i.e. helloworld)"
read pname
echo "Version of $pname? (i.e. 1.0)"
read pversion
clear
zenity --info --text="Please move the script into 
~/Projects/$pname/ and press the OK button."
mkdir -p ~/Projects/$pname/$pname-$pversion/debian/
cd ~/Projects/$pname/$pname-$pversion/debian/
touch changelog control compat copyright install rules
zenity --info --text="Please edit the files according to 
http://ubuntuforums.org/showthread.php?t=929498"
gedit *
cd ..
debuild -S
clear
dput my-ppa ~/Projects/$pname/$pname*.changes
```

---

### Post by _sluimers_ on 2010-02-01
I know this is old, but I would like to know what if all you want to upload is a python file for example? helloworld.py?

I get an error when I try debuild -k<key> -S -sa:
```

make: *** No rule to make target `clean'.  Stop.
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed
scons: *** [test] Error 29


```

My rules file:
```

#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

%:
        $@

```

---

### Post by SeanHodges on 2010-02-02
> **_sluimers_ said:**
> I get an error when I try debuild -k<key> -S -sa:
```

make: *** No rule to make target `clean'.  Stop.
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed
scons: *** [test] Error 29


```

As the error suggests, you don't have a "clean" target in your Makefile. dpkg-buildpackage needs this so that your package can delete the helloworld.py if the user decides to remove the package later on.

If you read the first post carefully, you'll notice this line near the top of the example rules file:

> include /usr/share/cdbs/1/rules/debhelper.mk

This line includes a lot of debhelper targets, including the missing "clean" one. Hopefully adding this line will resolve the issue you're seeing.

---

### Post by _sluimers_ on 2010-02-03
Ah, I see a makefile and a "clean:" line in it are absolutely necessary. I have it working now however, when I try to upload a small multi-platform RPG maker (which I didn't help develop, but have been part of the community for a long long time) on my ppa I encountered some problems:

* Permission. I can't run the program without using sudo.. well the program DOES run, but gives off errors whenever I want to add delete a sprite/map/game file.  

* The excutable doesn't work as I do not know how to use the makefile in order to run and install python files. Below is what's in the iked.py right now (it should simply another iked.py file)
```
print "python /usr/share/ika/iked/iked.py"
```

* the menu icon shows up in 'Others' and not in 'Games'

* ln -s $(SHAREDIR)/iked.png $(PIXMAPSDIR)/iked.png makes the link go to debian/ika/usr/share/ika/ika.png and not /usr/share/ika/ika.png

ika.menu
```

?package(iked):needs="ika" section="Games/Board"\
  icon="iked.png"\
  title="Iked" command="python /usr/share/iked/iked.py"

```

makefile
```

MDIR = iked/app
LDIR = linux

PREFIX=debian/iked/usr
BINDIR=$(PREFIX)/games
SHAREDIR=$(PREFIX)/share/ika
MENUDIR=$(PREFIX)/share/menu
APPDIR=$(PREFIX)/share/applications
PIXMAPSDIR=$(PREFIX)/share/pixmaps
IKEDDIR=$(SHAREDIR)/iked

.PHONY : clean install iked

iked: iked.py	
	python iked.py > $(LDIR)/iked

install: $(LDIR)/iked	
	mkdir -p $(BINDIR)  
	mkdir -p $(SHAREDIR)
	mkdir -p $(IKEDDIR)
	mkdir -p $(PIXMAPSDIR)
	mkdir -p $(MENUDIR)
	mkdir -p $(APPDIR)
	install $(LDIR)/iked $(BINDIR)/iked
	cp -rf $(MDIR)/* $(IKEDDIR)
	cp $(LDIR)/iked.png $(SHAREDIR)/iked.png
	cp $(LDIR)/iked.menu $(MENUDIR)/iked
	cp $(LDIR)/iked.desktop $(APPDIR)/iked.desktop
	ln -s $(SHAREDIR)/iked.png $(PIXMAPSDIR)/iked.png

clean:
	rm -f $(LDIR)/iked
	

```

---

### Post by SeanHodges on 2010-02-04
> **_sluimers_ said:**
> * Permission. I can't run the program without using sudo.. well the program DOES run, but gives off errors whenever I want to add delete a sprite/map/game file.

If the program runs (without using sudo), then it sounds like the package is installing the software correctly, but not configuring it properly afterwards. 

What you need to do is ensure these sprite, map and game files are not stored in /usr/share/ika/ - as a normal user does not have permission to add/remove files from that directory. 

You need to specify a folder in the user's home directory for storing game data, something like "/home/user/.local/share/ika/". You may need to speak to the developers on how to do this, usually it's a matter of setting a variable in a config file.

> * The excutable doesn't work as I do not know how to use the makefile in order to run and install python files. Below is what's in the iked.py right now (it should simply another iked.py file)
```
print "python /usr/share/ika/iked/iked.py"
```

Well I'm not entirely sure what you want, but if you are simply making a wrapper in /usr/bin/ that calls the "iked.py" program, you could just make a shell script, call it something like "iked" (without the .py):

```

#!/bin/sh
exec python /usr/share/ika/iked/iked.py "$@"
```

Alternatively, you could just make a symlink to iked.py in /usr/bin, like you did for your icon...

> * the menu icon shows up in 'Others' and not in 'Games'

Sorry, I'm not sure about this one as I haven't used the .menu approach that you have. I usually hand-craft my .desktop file and drop it in place directly from the Makefile. If you could post the .desktop file that is created I might be able to see what's wrong.

> * ln -s $(SHAREDIR)/iked.png $(PIXMAPSDIR)/iked.png makes the link go to debian/ika/usr/share/ika/ika.png and not /usr/share/ika/ika.png

Your symlink is created before all the files are moved into place by dpkg, which means after installation it is pointing to the wrong directory.

There are a number of ways around this, but the simplest is to use a relative path for the symlink target:

```
ln -s ../ika/iked.png $(PIXMAPSDIR)/iked.png
```

---

### Post by _sluimers_ on 2010-02-04
Thank you so much! Everything works almost perfectly now, including the desktop icon I (g)edited ;). I mistakenly thought the /usr/share/menu folder was for this kind of stuff.

One last problem has to do with permissions. When I try to close the app I get this error message:

```

Traceback (most recent call last):
  File "/usr/share/ika/iked/_iked/ui.py", line 405, in OnClose
    self.app.config.save()
  File "/usr/share/ika/iked/_iked/config.py", line 64, in save
    f = open(self.path, 'w')
IOError: [Errno 13] Permission denied: '/usr/share/ika/iked/config.ini'

```

Do I need to chmod these files in my makefile or ask the developer to change his code?

---

### Post by SeanHodges on 2010-02-04
> **_sluimers_ said:**
> Thank you so much! Everything works almost perfectly now, including the desktop icon I (g)edited ;). I mistakenly thought the /usr/share/menu folder was for this kind of stuff.

Excellent.

> One last problem has to do with permissions. When I try to close the app I get this error message:

```

Traceback (most recent call last):
  File "/usr/share/ika/iked/_iked/ui.py", line 405, in OnClose
    self.app.config.save()
  File "/usr/share/ika/iked/_iked/config.py", line 64, in save
    f = open(self.path, 'w')
IOError: [Errno 13] Permission denied: '/usr/share/ika/iked/config.ini'

```

Do I need to chmod these files in my makefile or ask the developer to change his code?

You definitely don't want to chmod the file, it is being installed as a system file so is deliberately read-only. Otherwise, if one user saves to the file it will overwrite any config settings made by another user on the machine.

What you need is for the config.ini to be read from the user's home directory instead of the system one. If no config file is available (e.g. the engine is run for the first time by a user), then the system config.ini should be copied into that user's home directory.

This may require a code change, if you ask the developer then he might have some thoughts on this. It sounds like the rest of the package is in pretty good shape though.

---

### Post by _sluimers_ on 2010-02-04
Okay, everything works now :).

---

### Post by JamesTheAwesomeDude on 2012-11-11
Hey, I need help. I got an error, but I can't find my problem.
```
james@james-OptiPlex-GX620:~/PPA/helloworld/helloworld-1.0$ debuild -S
parsechangelog/debian: warning:     debian/changelog(l5): found eof where expected more change data or trailer
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
parsechangelog/debian: warning:     debian/changelog(l5): found eof where expected more change data or trailer
dpkg-buildpackage: error: unable to determine source changed by
dpkg-buildpackage: source package helloworld
dpkg-buildpackage: source version 1.0-0ubuntu1~ppa1
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed
james@james-OptiPlex-GX620:~/PPA/helloworld/helloworld-1.0$
```I probably made some ridiculously stupid/obvious mistake, but I can't figure out what. Could you please give this a look?

NOTE: tried [FONT=Courier New]sudo debuild -S[/FONT], but got the same results.

---

### Post by JamesTheAwesomeDude on 2012-11-11
Okay, I tried starting over with a clean slate; just restarting the whole process. It says that the file /usr/share/cdbs/1/rules/debhelper.mk does not exist. What do I need to do? I checked /usr/share/, but there is no file or folder labeled cdbs or anything similar. What do I need to do?

---

