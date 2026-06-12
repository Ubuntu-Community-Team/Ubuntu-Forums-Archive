---
title: "Howto: Build the newest version of Bluefish under Ubuntu"
date: 2010-03-10
forum: Tutorials
---

### Post by andrew.46 on 2010-03-10
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12108384#post12108384](http://ubuntuforums.org/showthread.php?p=12108384#post12108384)


Support threads regarding the wiki and it's content should be created in a suitable forum.

In March Bluefish 2.2.2 was released. This mini-guide demonstrates how to build this version from source under the newest release version of Ubuntu and has been tested most recently under Oneiric Ocelot. First we need to remove the repository version if it has been installed:

```

sudo apt-get remove bluefish

```

Next download some compiling tools and dependencies:

```

sudo apt-get install build-essential checkinstall libart-2.0-dev libaspell-dev \
libbonobo2-dev libbonoboui2-dev libgail-dev libgnome-keyring-dev libgnome2-dev \
libgnomecanvas2-dev libgnomeui-dev libpcre3-dev libpcrecpp0 libpopt-dev \
libgucharmap2-dev libenchant-dev intltool

```

Next download the source code, open the tarball and compile and install it with the following single command:

```

mkdir -pv $HOME/bluefish_build && cd $HOME/bluefish_build && \
wget http://www.bennewitz.com/bluefish/stable/source/bluefish-2.2.2.tar.bz2 && \
tar xjvf bluefish-2.2.2.tar.bz2 && cd bluefish-2.2.2 && \
./configure && make && \
sudo checkinstall --fstrans=no --pakdir "$HOME/bluefish_build" --backup=no \
  --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "2.2.2" && \
make distclean

```

And that is it! This gives you the newest version of this great editor. Please feel free to post any problems in this thread or even better any successes!

**Recent Updates to This Guide:**

[LIST]
[*]Mar 18 2012: Version bump to 2.2.2 and tested under 64bit Oneiric.
[*]Jan 12 2012: Version bump to 2.2.1 and tested under 32bit Oneiric.
[*]May 07 2011: Version bump to 2.0.3 and tested under 32bit Natty.
[*]Sep 24 2010: Version bump to 2.0.2 and tested under 32bit Maverick.
[/LIST]

---

### Post by nilarimogard on 2010-03-12
```
sudo wget [http://debian.wgdd.de/stuff/debian.wgdd.de_ubuntu.list](http://debian.wgdd.de/stuff/debian.wgdd.de_ubuntu.list) -N -P /etc/apt/sources.list.d
sudo apt-get update && sudo apt-get install wgdd-archive-keyring
sudo apt-get install bluefish
```

---

### Post by andrew.46 on 2010-03-12
Hi nilarimogard,

Thanks for pointing this out which of course has the blessing of the Bluefish developers:

Installing Bluefish
[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer)

I would personally read with some care the owner's comments regarding his [Ubuntu packages]("http://debian.wgdd.de/repository"), which I confess I have not tried...

I believe there are also a couple of decent PPAs that offer the new Bluefish. Lots of choices :).

Andrew

---

### Post by Turin Turambar on 2010-03-12
Unfortunately, no, there are no deb's around for karmic koala. Just for jaunty and it's developers release, not final 2.0.
I also checked Lucid's PPA packages and unfortunately Bluefish is still 1.07. It's in the frozen state, so don't expect anything. I hope Bluefish team will update & make new debs.

Sigh... I hate compiling, all those needed packages, it's messy. ;)

---

### Post by thomashw on 2010-03-15
Just installed using your instructions - worked great!

One question - could you explain the last two lines?

```
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "2.0.0"
$ make distclean
```

Just looking to learn a bit about what's going on.

Thanks!

---

### Post by andrew.46 on 2010-03-15
Hi thomas,

> **thomashw said:**
> Just installed using your instructions - worked great!

Excellent news, I hope you enjoy the new version as much as I am :).

> One question - could you explain the last two lines?

```
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "2.0.0"
$ make distclean
```



I use checkinstall here because I am too lazy to learn formal debian package management but checkinstall still produces a decent package that will install and uninstall like any other package that you download from the Ubuntu repository. *--pakdir "$HOME/Desktop"* simply means that the eventual deb package will be deposited on your desktop. The options *--backup=no --deldoc=yes --deldesc=yes --delspec=yes* are designed to minimise the amount of cruft left in the source tree when checkinstall has finished. The option *--pkgversion "2.0.0"* will be the version seen in Synaptic for instance and this will mean that if version 2.0.1 comes to the repository *sudo apt-get upgrade* will automagically install this version. The option *--default* means checkinstall will not ask you questions, it will accept the default response, and these defaults are quite reasonable.

The final command *make distclean * cleans the source tree of all configure logs, compiled executables etc and leaves it as you originally started. This prevents a lot of problems if you recompile from this same directory.

Hope this helps?

Andrew

---

### Post by thomashw on 2010-03-15
Perfect, thanks!

---

### Post by thomashw on 2010-03-16
The .deb package saved to the desktop - this isn't needed, is it?

---

### Post by andrew.46 on 2010-03-16
Hi thomashw,

> **thomashw said:**
> The .deb package saved to the desktop - this isn't needed, is it?

It is not needed for the program to run and can safely be deleted. You *could* save it for reinstallation on your own computer if you liked but it is not suitable for sharing with other users, for this you would have to build a formal debian package.

Andrew

---

### Post by andrew.46 on 2010-03-26
Good news is that I have tested this guide under the beta 1 of Lucid Lynx and it works perfectly without any modification :).

Andrew

---

### Post by MughalShahzad on 2010-05-07
Thank you soooooooooooo much its working :guitar:


Regards
Shahzad



> **andrew.46 said:**
> In February 2010 Bluefish 2.0.0 was released. This mini-guide demonstrates how to build this version from source under Ubuntu and has been tested under Karmic Koala and Lucid Lynx. First we need to remove the repository version if it has been installed:

```

sudo apt-get remove bluefish

```Next download some compiling tools and dependencies:

```

sudo apt-get install build-essential checkinstall libart-2.0-dev libaspell-dev \
libbonobo2-dev libbonoboui2-dev libgail-dev libgnome-keyring-dev libgnome2-dev \
libgnomecanvas2-dev libgnomeui-dev libpcre3-dev libpcrecpp0 libpopt-dev \
libgvfscommon-dev libgucharmap2-dev libenchant-dev

```Next download the source code, open the tarball and compile and install it:

```

$ cd $HOME
$ wget http://www.bennewitz.com/bluefish/stable/source/bluefish-2.0.0.tar.bz2
$ tar xjvf bluefish-2.0.0.tar.bz2
$ cd bluefish-2.0.0
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "2.0.0"
$ make distclean


```And that is it! This gives you the newest version of this great editor. Please feel free to post any problems in this thread or even better any successes!

**Recent Updates to This Guide:**

[LIST]
[*]Successfully tested under Lucid Lynx
[/LIST]


---

### Post by andrew.46 on 2010-05-10
Hi Shahzad,

> **MughalShahzad said:**
> Thank you soooooooooooo much its working :guitar:

Excellent news, I hope you enjoy the new version :).

All the best,

Andrew

---

### Post by ronbrooks on 2010-06-08
When I use make I get an error message that tells me make: *** No targets specified and no makefile found.  Stop. So this is as far as I can go. 

Any help on this one I would like to get this program.

I am using 10.04 ubuntu

---

### Post by uniquedoug on 2010-06-24
I went through all the steps, and everything seemed to go well. My only problem is that I can't find the BlueFish editor to run.... 

I am running Linux Mint...

Thanks

---

### Post by pEkvo on 2010-06-24
> **uniquedoug said:**
> I went through all the steps, and everything seemed to go well. My only problem is that I can't find the BlueFish editor to run.... 

I am running Linux Mint...

Thanks

You can start it by typing 'bluefish' in the terminal.

How can I add it as an icon though, to open it without having to use the terminal? And it also seems like my settings never get saved, I change my basedir to something else but next time I open Bluefish, it has gone back to the default...

I'm on Ubuntu 10.04.

---

### Post by andrew.46 on 2010-06-25
Hi ron,

> **ronbrooks said:**
> When I use make I get an error message that tells me make: *** No targets specified and no makefile found.  Stop. So this is as far as I can go. 

Sorry about the delay, I am not running Ubuntu at the moment and only check on the forums every now and then :(. Can you give the results of ./configure please, but first run 'make distclean' in the source directory.

All the best,

Andrew

---

### Post by valley1967 on 2010-06-29
It worked for me just fine

---

### Post by svensol on 2010-06-29
> **andrew.46 said:**
> Hi ron,



Sorry about the delay, I am not running Ubuntu at the moment and only check on the forums every now and then :(. Can you give the results of ./configure please, but first run 'make distclean' in the source directory.

All the best,

Andrew

Hi All,

I ran into the same problem (Ubuntu 10.04, 64bit).  It turned out (whilst I copy and pasted the script) I missed the error.

At the end of "./configure" it said:
```
checking for intltool-update... no
checking for intltool-merge... no
checking for intltool-extract... no
configure: error: The intltool scripts were not found. Please install intltool.

```then you just:

```
sudo apt-get install intltool
```and try it again, that should finish it.

Hope that helps,

Sven.

---

### Post by Jeece on 2010-07-06
Hello !

I compiled Bluefish 2.0.1 on Lucid Lynx 64Bits. It works !

I had to add intltool package.

Autocompletion is really useful.

Thanks for the help.

---

### Post by andrew.46 on 2010-07-07
Hi Jeece,

> **Jeece said:**
> I compiled Bluefish 2.0.1 on Lucid Lynx 64Bits. It works !

Great news :).

Andrew

---

### Post by leonardjensan on 2010-07-23
> **andrew.46 said:**
> In February 2010 Bluefish 2.0.0 was released. This mini-guide demonstrates how to build this version from source under Ubuntu and has been tested under Karmic Koala and Lucid Lynx. First we need to remove the repository version if it has been installed:

```

sudo apt-get remove bluefish

```

Next download some compiling tools and dependencies:

```

sudo apt-get install build-essential checkinstall libart-2.0-dev libaspell-dev \
libbonobo2-dev libbonoboui2-dev libgail-dev libgnome-keyring-dev libgnome2-dev \
libgnomecanvas2-dev libgnomeui-dev libpcre3-dev libpcrecpp0 libpopt-dev \
libgvfscommon-dev libgucharmap2-dev libenchant-dev

```

Next download the source code, open the tarball and compile and install it:

```

$ cd $HOME
$ wget http://www.bennewitz.com/bluefish/stable/source/bluefish-2.0.0.tar.bz2
$ tar xjvf bluefish-2.0.0.tar.bz2
$ cd bluefish-2.0.0
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "2.0.0"
$ make distclean


```

And that is it! This gives you the newest version of this great editor. Please feel free to post any problems in this thread or even better any successes!

**Recent Updates to This Guide:**

[LIST]
[*]Successfully tested under Lucid Lynx
[/LIST]
Thank you! Works like a charm!

---

### Post by andrew.46 on 2010-07-23
Hi leonard,

> **leonardjensan said:**
> Thank you! Works like a charm!

Good to hear :). I will admit that I am not actually running Ubuntu at the moment so I cannot really update this guide but I believe a point upgrade for Bluefish has been released and this might be worth a look at. Should just be a matter of downloading the new source and compiling as suggested and altering the --pkgversion string for checkinstall...

All the best,

Andrew

---

### Post by EmmyS on 2010-08-03
I got around the issue in my original question below by opening the source directory in the URL directly in my browser and just saving the file to my home directory. 

===================PROBLEM BELOW SOLVED =====================================================
> 
```

$ wget http://www.bennewitz.com/bluefish/stable/source/bluefish-2.0.0.tar.bz2

``` I hope someone's still following this forum. On the quoted line above, I keep getting the following error:

--2010-08-03 09:52:35--  (try:20)  [http://www.bennewitz.com/bluefish/stable/source/bluefish-2.0.0.tar.bz2](http://www.bennewitz.com/bluefish/stable/source/bluefish-2.0.0.tar.bz2)
Connecting to [www.bennewitz.com|85.10.194.36|:80]("http://www.bennewitz.com%7C85.10.194.36%7C:80")... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.


Does this mean the server is having problems? Should I keep trying, or is this source file no longer available?

---

### Post by andrew.46 on 2010-08-03
Hi Emmy,

> **EmmyS said:**
> Does this mean the server is having problems? Should I keep trying, or is this source file no longer available?

I have renovated the guide thanks to a VM I set up and changed the download address to a US one, I would be interested to see if wget is happier with this? Both addresses work for me. A version bump as well that might make it worthwhile recompiling,,,

Andrew

---

### Post by Orfantal on 2010-08-13
The guide worked for me on Ubuntu Lucid 32-bit. What a wonderful auto-complete feature!

I've got one problem though. Syntax highlighting of Comments doesn't work properly in css files. It is very annoying to watch a /* comment */ appear as regular text most of the time. It works sometimes, and it seems to be only within brackets only for some reason.

HTML comments work exactly as they should.

So does anyone else experience this? Know of a sollution?? :D

---

### Post by clevertomato on 2010-08-23
Thanks andrew.46 this is just what I was looking for. It worked for me in Lucid.

---

### Post by andrew.46 on 2010-08-24
Hi shawnboy,

> **shawnboy said:**
> Thanks andrew.46 this is just what I was looking for. It worked for me in Lucid.

Excellent news :).

Andrew

---

### Post by clevertomato on 2010-08-25
I don't suppose Bluefish 2.0.1 will run on Jaunty?

---

### Post by andrew.46 on 2010-08-25
Hi shawnboy,

> **shawnboy said:**
> I don't suppose Bluefish 2.0.1 will run on Jaunty?

It will run but I do not have Jaunty installed at the moment to see if this guide will still build ok. The only problem will be perhaps some of the -dev files and apt-get will tell you if they are not available or have differnt names...

All the best,

Andrew

---

### Post by andrew.46 on 2010-08-31
Hi Orfantal,

> **Orfantal said:**
> I've got one problem though. Syntax highlighting of Comments doesn't work properly in css files. It is very annoying to watch a /* comment */ appear as regular text most of the time. It works sometimes, and it seems to be only within brackets only for some reason.

I can confirm this on my system, it appears to be a bug. Screenshot attached to demonstrate. Might be worth chasing up the Bluefish guys with this one...

Andrew

---

### Post by Orfantal on 2010-08-31
> **andrew.46 said:**
> Hi Orfantal,

I can confirm this on my system, it appears to be a bug. Screenshot attached to demonstrate. Might be worth chasing up the Bluefish guys with this one...
Andrew
Hi Andrew,

I did just that soon after I posted here. I got a fast reply from a dev that said it was fixed, see this link for bug report and reply:
[https://bugzilla.gnome.org/show_bug.cgi?id=626929](https://bugzilla.gnome.org/show_bug.cgi?id=626929)

But... I tried to replace the the files from this guide with the files that he had modified to revision 6051, and then just build according to this guide again (uninstalled in between of course). And that didn't change anything for the syntax highlighting. Course it might work correctly in the current version in Subversion or building in a different way. I don't know. I gave up trying to get it to work. :(

If you manage to get this working, please let me know or reply to this thread. Myself, I'm done digging into this.

---

### Post by andrew.46 on 2010-08-31
Hi Orfantal,

> **Orfantal said:**
> If you manage to get this working, please let me know or reply to this thread. Myself, I'm done digging into this.

No, the changes do not work with bluefish 2.0.1 but surprisingly enough do not work with the svn bluefish either. I have added to your bug report so hopefully the developers will have another look.

Andrew

---

### Post by andrew.46 on 2010-09-02
Hi Orfantal,

The latest svn has really fixed the issue :). I had a look at patching 2.0.1 but with 2.0.2 now with a release candidate out I think that would be a little foolish, 2.0.2 will be released soon enough.

Are you interested in trying the latest svn which has this fix in place? It will be the version just past the release candidate and something like the following (in addition to the tools already installed as per this guide) should work:

```

$ sudo apt-get install subversion automake libtool
$ cd $HOME
$ svn co https://bluefish.svn.sourceforge.net/svnroot/bluefish/trunk/bluefish 
$ cd bluefish
$ ./autogen.sh 
$ ./configure 
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default \
  --pkgversion "2.0.2-rc1-r$(svn info | grep 'Last Changed Rev' | cut -f4 -d " ")"
$ make distclean

```

Or wait for 2.0.2 to be released :).

Andrew

---

### Post by Orfantal on 2010-09-02
> **andrew.46 said:**
> Or wait for 2.0.2 to be released :).
Nah, wanted to try it now ;). It worked. Yay! Nice to have something working to fall back on when I need to edit css again. Thanks for the build instructions. They really need someone to do packaging for them (which they also say on the site).

---

### Post by andrew.46 on 2010-09-02
Hi Orfantal,

> **Orfantal said:**
> Nah, wanted to try it now ;). It worked. Yay! Nice to have something working to fall back on when I need to edit css again. Thanks for the build instructions. 

Great news :). I will update this guide again when 2.0.2 is released but I suspect this will simply involve changing the filenames and download links.

All the best,

Andrew

---

### Post by andrew.46 on 2010-09-24
Those who have been following this guide may be interested to know that I have successfully tested it under Maverick as well as bumping the version up to 2.0.2. Maverick looks like it will ship with 2.0.1 so this guide will equip you with a version that has a number of additional bug fixes :). The ugly checkinstall file translation flaw has reared its head again in Maverick so *--fstrans=no* is back...

All the best,

Andrew

---

### Post by KaiO on 2010-10-27
Thanks.
I managed to build the 2.0.2 fine on my 64-bit 10.10 Kubuntu.

BUT:
I have no PHP highlighting.
All PHP code is just as plain text and there is no distinction between variables, procedures, loop etc.

Is there a way to fix it?
Anyone else experiencing this?

---

### Post by andrew.46 on 2010-10-28
Hi KaiO,

> **KaiO said:**
> 
I have no PHP highlighting.
All PHP code is just as plain text and there is no distinction between variables, procedures, loop etc.

Seems a little odd, I have PHP syntax highlighting out of the box with no extra configuration. I have attached a screenshot to demonstrate. Not sure of the solution to this one :(.

Andrew

---

### Post by inphektion on 2010-11-09
For those on ubuntu lucid, the lucid-bleed ppa is a great repository for the latest bluefish.  I went to follow this to install it but noticed i could already get this version from the ppa.  I prior had this ppa installed for the latest version of gimp and openshot in lucid.  Now it's coming through again to give me latest bluefish.
[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa)

---

### Post by dozycat on 2010-11-17
I just installed it in ubuntu 10.04 in my asus 1000he 2megas ram, it worked great :KS. I checked some perls I did before and they looked great.

---

### Post by andrew.46 on 2010-11-17
Hi doxycat,

> **dozycat said:**
> I just installed it in ubuntu 10.04 in my asus 1000he 2megas ram, it worked great :KS. I checked some perls I did before and they looked great.

Great news :). I was starting to think that this guide would have less and less usage as the number of PPAs with the latest version of Bluefish increase :(.

Andrew

---

### Post by dozycat on 2010-11-17
it works, however everytime It runs I got the following message:

error reading list 1 Error opening file: No such file or directory
config file migration error 1:Error opening file: No such file or directoryerror reading list 1 Error opening file: No such file or directory
htmlbar_build_menu, finished
cleanup_scanner, num_marks=0, fblock_refcount=0,fcontext_refcount=0,fstack_refcount=0

I added jing and intltool

but no change

---

### Post by andrew.46 on 2010-11-18
Hi dozycat,

Try starting from a clean slate with your bluefish configuration. Close bluefish and then run the following:

```
mv -v $HOME/.bluefish $HOME/.bluefish_bak 
```

and then restart bluefish. You will need to then reconfigure all your bluefish options but hopefully the error message will be gone. Your old settings will be preserved in $HOME/.bluefish_bak.

Andrew

---

### Post by dozycat on 2010-11-19
Thanks Andrew.46,

But no luck, it looks like it tries to load a non vital file, too bad there is no debug mode for the bluefish so I can see what file is.
One option is to try the debug symbols of the homepage of bluefish I will try it in the weekend.

Again thanks for your help, and I prefer guides to use other repositories that the official ones.

---

### Post by dozycat on 2010-11-20
I tried:
./configure CFLAGS="-g -O0" && make

I did again the instructions of this guide.

gdb bluefish
 
lawrence@lawrence-laptop:~/bluefish-2.0.2$ gdb bluefish 
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/local/bin/bluefish...(no debugging symbols found)...done.

any idea how to add the debug symbols

---

### Post by andrew.46 on 2010-11-20
Hi dozycat,

> **dozycat said:**
> any idea how to add the debug symbols

Try adding the following to the checkinstall options:

```
--strip=no
```

Andrew

---

### Post by dozycat on 2010-11-21
That option worked, I filled the report and the solution was very easy:

open blue fish and, edition open preferences press ok and finish.

thanks again

---

### Post by clbaines on 2010-12-04
I just used your tutorial to install Bluefish 2.0.2. Great way to go. Awhile back I tried to install this version from a Linux Format disk file. Nothing but trouble trying to install the dependences. Your method:) was perfect.

---

### Post by andrew.46 on 2010-12-04
Hi clbaines,

Glad it worked well for you :). Looks like another point upgrade coming out shortly which will take it to 2.0.3, not sure of the bug-fixes / enhancements available there.

Andrew

---

### Post by Struki on 2011-01-25
I'm impressed with your level of care for this problem, everything worked without problems, and I got a deb package for future installation. Great job. Thanks Andrew!

---

### Post by andrew.46 on 2011-01-27
Hi Struki,

> **Struki said:**
> I'm impressed with your level of care for this problem, everything worked without problems, and I got a deb package for future installation. Great job. Thanks Andrew!

Glad it worked for you :). Just bear in mind that the deb file created by checkinstall is not nearly as portable as a formal debian file.

Andrew

---

### Post by rothbert on 2011-02-03
Thanks for this Andrew.

I've just installed this on Lucid 10.04 on an AMD 64.

All good but I'm having an issue with the custom menu bar. The bar is there but not the actual 'custom menu' element - the drop down menu with 'Edit custom menu'; 'reset'; 'load new'. 

And mousing over any custom commands and entering shortcut keys is not working.

I've had no luck so far looking for solutions.

Any input appreciated.

---

### Post by andrew.46 on 2011-02-14
Sorry Rothbert, I have never really dabbled with the custom menu. Perhaps try the bluefish-users mailing list?

[http://bluefish.openoffice.nl/development.html](http://bluefish.openoffice.nl/development.html)

---

### Post by faceonline on 2011-05-01
Hi,

Just thought I'd mention this technique works great in Natty 11.04 without any modifications!

Thanks very much for your help!

---

### Post by andrew.46 on 2011-05-07
> **faceonline said:**
> Just thought I'd mention this technique works great in Natty 11.04 without any modifications!

That is excellent news, thank you for testing the guide out under the new Ubuntu which I have to admit I have not done yet. I see that 2.0.3 is out now so I will have to get to and make a few small changes to the guide, I believe 2.0.2 is actually available in the Ubuntu repository for Natty...

**Edit: **Done :)

---

### Post by andrew.46 on 2012-01-11
It has been a long time between updates but I have finally updated this guide for Oneiric Ocelot and the newest version of Bluefish: 2.2.1. Please test it out, runs fine on my own system :)

---

### Post by harless on 2012-01-26
Can you tell me how to install 2.2.1 on Linux Mint 11? I used the terminal and install instructions from page one of this thread, it installed but I have to use the terminal to access Bluefish. Not so practical.
When trying to install from deb I get:
Error: Dependency is not satisfiable: bluefish-data (= 2.2.1-1~0dl1~ubu1104+1) 
 
Also how do you get it to auto indent? 
Note: I am not that technically advanced a user of linux so please give dummy instruction. :)

---

### Post by harless on 2012-01-26
> **harless said:**
> Can you tell me how to install 2.2.1 on Linux Mint 11? I used the terminal and install instructions from page one of this thread, it installed but I have to use the terminal to access Bluefish. Not so practical.
When trying to install from deb I get:
Error: Dependency is not satisfiable: bluefish-data (= 2.2.1-1~0dl1~ubu1104+1) 
 
Also how do you get it to auto indent? 
Note: I am not that technically advanced a user of linux so please give dummy instruction. :)

Installed by using this method; don't know, yet, it it will function properly but it is installed. 
sudo wget [http://debian.wgdd.de/stuff/debian.wgdd.de_squeeze.list](http://debian.wgdd.de/stuff/debian.wgdd.de_squeeze.list) -N -P /etc/apt/sources.list.d[FONT=Verdana]
[/FONT]sudo apt-get update
sudo apt-get install wgdd-archive-keyring sudo apt-get install bluefish

---

### Post by andrew.46 on 2012-01-27
> **harless said:**
> Can you tell me how to install 2.2.1 on Linux Mint 11? I used the terminal and install instructions from page one of this thread, it installed but I have to use the terminal to access Bluefish. Not so practical.

Perhaps your menu requires either logout or reboot to refresh properly? Unfortunately I am not familiar with Mint and also once again I am between Ubuntu installations atm :(. Indenting I will have a look at...

---

### Post by andrew.46 on 2012-01-27
> **harless said:**
> Also how do you get it to auto indent? 

If I understand your question there is a simple option in the settings, screenshot attached...

---

### Post by kevdog on 2012-01-28
Confirmed -- compiles and runs fine on 11.10.  Simple build -- I like that!

---

### Post by harless on 2012-02-01
> **andrew.46 said:**
> If I understand your question there is a simple option in the settings, screenshot attached...

That was checked by default; still does not auto indent. Also noticed that auto complete list only works, most of the time, after I have saved file.

I am an OS tryout junkie. I want to next try Minix 3. The BSD flavors have never successfully installed, neither Open BSD nor PC-BSD, but they sound awesome.

---

### Post by tg3793 on 2012-03-13
> **andrew.46 said:**
> In December 2011 Bluefish 2.2.1 was released. This mini-guide demonstrates how to build this version from source under Ubuntu and has been tested most recently under Oneiric Ocelot. First we need to remove the repository version if it has been installed:

```

sudo apt-get remove bluefish

```

Next download some compiling tools and dependencies:

```

sudo apt-get install build-essential checkinstall libart-2.0-dev libaspell-dev \
libbonobo2-dev libbonoboui2-dev libgail-dev libgnome-keyring-dev libgnome2-dev \
libgnomecanvas2-dev libgnomeui-dev libpcre3-dev libpcrecpp0 libpopt-dev \
libgucharmap2-dev libenchant-dev intltool

```

Next download the source code, open the tarball and compile and install it with the following single command:

```

mkdir -pv $HOME/bluefish_build && cd $HOME/bluefish_build && \
wget http://www.bennewitz.com/bluefish/stable/source/bluefish-2.2.1.tar.bz2 && \
tar xjvf bluefish-2.2.1.tar.bz2 && cd bluefish-2.2.1 && \
./configure && make && \
sudo checkinstall --fstrans=no --pakdir "$HOME/bluefish_build" --backup=no \
  --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "2.2.1" && \
make distclean

```

And that is it! This gives you the newest version of this great editor. Please feel free to post any problems in this thread or even better any successes!

**Recent Updates to This Guide:**

[LIST]
[*]Jan 12 2012: Version bump to 2.2.1 and tested under Oneiric.
[*]May 07 2011: Version bump to 2.0.3 and tested under Natty.
[*]Sep 24 2010: Version bump to 2.0.2 and tested under Maverick.
[/LIST]

* Well that was just beautiful. I'm on Lucid and I just copied and pasted all of this without modifying a thing. Now that's beautiful!

---

### Post by moshebagelfresser on 2012-03-13
Many thanks you're great!! Keep up the good work!!!
Moshe

---

### Post by andrew.46 on 2012-03-18
Thank you gentlemen, I was convinced that this guide was no longer being used and it is good to see it is still active :). To celebrate I have bumped the Bluefish version to 2.2.2 and tested this under the 64bit Oneiric Ocelot.

Love to see some of the websites being developed with Bluefish, feel free to post links here. My own personal site is built using Bluefish, it is functional rather than pretty:

Andrew's Corner of the Web
[http://www.andrews-corner.org/index.html](http://www.andrews-corner.org/index.html)

---

### Post by airper on 2012-07-03
Hi Guys,

I've been using Bluefish for a couple of years, excellent editor for PHP and HTML/CSS etc. 

Unfortunately  I've had real problems trying to update to 2.2.3. In fact Ubuntu has  un-installed 2.2.2 and refuses to install 2.2.3 on Ubuntu 12.04.

There seems to be dependency issues, which I am unable to resolve.

I  added the repository from the Bluefish website and the Ubuntu Software Centre locates 2.2.3 okay.  It then un-installs 2.2.2. Okay I understand it needs to build a clean install.

On the install it reports a dependency issue.  All the other dependencies seem okay except this one. 

Depends: libpython2.6 (>= 2.6) but it is not going to be installed. 

This kills the install. 12.04 appears to have   libpython version 2.7 and/or 3.2 installed, but this stops the process for  reason I am unable to determine.

See screenshot for details

I then tried using this thread, which I realise if for Bluefish 2.2.2, but I was getting desperate. Unfortunately it seems to have similar problems with dependencies.

I then tried building from source, following the advice on the Bluefish Wiki, but again it throws up lots of dependency issues.

I  don't want to break my system so I am a little cautious about blindly  installing stuff I don't fully understand. I couldn't find anything more  on the Bluefish Wiki, or in a general search of Debian or Google.

Can  anyone help with advice on installing Bluefish 2.2.3 in  Ubuntu 12.04, or point me  in the direction of a good HowTo. Right now I don't have a Bluefish install at all. [IMG]http://mail.yimg.com/nq/mc/1_0_0/mesg/tsmileys2/02.gif[/IMG] I'm missing it, a lot.

Thanks

---

### Post by andrew.46 on 2012-07-12
Unfortunately this guide will no longer be updated in its current format, and waits for any keen person to convert it to wiki format :(. But it still should work, just make sure you install the depedencies listed under: *Next download some compiling tools and dependencies:*. Sorry I cannot be too much more help, I have in fact [requested this guide be closed or moved]("http://ubuntuforums.org/showthread.php?t=2011777")....

---

### Post by tg3793 on 2012-07-13
> **andrew.46 said:**
> Unfortunately this guide will no longer be updated in its current format, and waits for any keen person to convert it to wiki format :(. But it still should work, just make sure you install the depedencies listed under: *Next download some compiling tools and dependencies:*. Sorry I cannot be too much more help, I have in fact [requested this guide be closed or moved]("http://ubuntuforums.org/showthread.php?t=2011777")....

It's ok Andrew. Time constraints (or otherwise) I understand. I simply hope (if it is moved) that they don't fitz up any of us who are subscribed to it. I've just updated my system from Lucid all the way up to Natty and am happy to report that my Bluefish 2.2.1 installation is still singing happily along.

I have no need to update Bluefish at the moment, but when I do I want to be able to come back here ... I've kept an eye on this thread ever since you first helped me. So thanks for all the help that you have been to myself and others. :guitar:

---

### Post by andrew.46 on 2012-07-13
> **tg3793 said:**
>  So thanks for all the help that you have been to myself and others. :guitar:

Thanks for your kind words :).

---

### Post by airper on 2012-07-13
Thanks Andrew,

This has been a very useful resource over the last few years so I do hope it does get moved to the Wiki and is somehow maintained.

I have got Bluefish 2.2.3 installed okay now, with a little help from the Bluefish mailing list, which is also a very good source of help.

Bluefish has developed very well these last few years, it is by far my most favoured editor for CCS3, HTML and PHP. It has very strong support features and a good mix of keyboard short cuts and mouse control, together with tag completion and other little things that make it a real pleasure to use.

I tried to get on with VIM for a while, but it just does not suit my way of working, I find Bluefish much easier to work with. However I do reconfigure the colour scheme to copy the VIM xario256 theme, which is based on a dark background. The xario256 is highly rated in the VIM world and with a little tinkering can be copied in Bluefish to good effect.

Thanks Andrew your postings and help have  been much appreciated.

Regards

Wayne

---

### Post by andrew.46 on 2012-07-13
> **airper said:**
> Thanks Andrew your postings and help have  been much appreciated.

And thanks again for such kind words :). This guide can be migrated to the Ubuntu wiki by any interested person and perhaps as well can be easily enough maintained by this same interested person. And who knows, perhaps in the future something similar to 'Tutorials and Tips' might spring up again on these Forums and guides like this one may rise Phoenix-like from the ashes :).

---

