---
title: "HOWTO: Install Linux DC++ (the easy way)"
date: 2005-06-16
forum: Tutorials
---

### Post by mird on 2005-06-16
[size=+1]**[color=red]*** UPDATED ***[/color]**[/size]

*09/Aug/2005* - More CVS commits, as per usual see the project changelog for details.  New package details in the instructions below.

*24/Jul/2005* - Another recent commit (see the [project changelog](http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain) for details) and a new package which should also (hopefully) fix the dependancy issues for anyone not using Backports.  I've updated the instructions below to reflect the new package.

*01/Jul/2005* - There were a few commits to the dcpp repository in the last week (see the [project changelog](http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain) for details) so I've built and packaged it up for all.  Also added menu file for those that wanted it (plz test k thx!).  To install (or upgrade to) the latest package follow the steps below.

---

I've built and packaged the latest version (plus some patches - currently only the user-commands patch by s4kk3 as mentioned [here](http://www.ubuntuforums.org/showthread.php?p=141959#141959)) of Linux DC++ for anyone who is interested.  Development on this particular project is a bit unorganised and rather intermittent but I'll do my best to maintain the latest version.  **Note that this is considered _unstable_ software.  There are bugs'o'plenty and although it works quite satisfactorily for me, it may not for you.  Please submit useful bug reports to the [project's bugtracker](http://developer.berlios.de/bugs/?group_id=2230).**

There may be some additional dependancies which I didn't note as this is the first time I've tried to decipher dependancies from a built binary.  Never-the-less do let me know if you have any problems.

**INSTALL / UPGRADE**

1. Install dependancies.

```
sudo apt-get install libatk1.0-0 libbz2-1.0 libc6 libgcc1 libglade2-0 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libstdc++6 libxml2 zlib1g
```
2. Fetch the package.

```
wget http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb
```
3. Install the package.

```
sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
```

And that's it!  There should now be a *Linux DC++* icon under Applications -> Internet.

---

### Post by kuleali on 2005-06-16
nice,

---

### Post by pdk001 on 2005-06-16
thank you, i will try it right away

---

### Post by moment on 2005-06-16
Works like a charm :D

---

### Post by johannes on 2005-06-17
Thanks very much! It works great.  :)

---

### Post by RadixLecti on 2005-06-22
Does this version work with å, ä , ö?
I've tried a version that didn't show ANY lines in mainchat containing those letters. Annoying like hell, it was.

---

### Post by Krank on 2005-06-29
Seems to work abselutely wonderful, so far...

My one problem is that it doesn't seem to show up in the Debian menu automatically, no matter what I do. Being a Blackbox user (I find it to be more efficient), I don't have the Gnome menu, only the Debian (the "menu" package) menu...

So, any ideas?

---

### Post by mird on 2005-06-30
New package released - check the first post for details.

**Krank**, just for you I've added what I think is required to get it to show up in the Debian menu :)... install the latest package and let me know if it works or not.

---

### Post by Majlo on 2005-07-02
Many thanks , package work great 
:-)

---

### Post by dlpfmVfH on 2005-07-02
It worked great...thanks...linuxdcpp rulez, I think it should be added to the repo's

---

### Post by dabear on 2005-07-02
there isn't some kind of strongdc++ version for linux? I need segmented downloading..

---

### Post by i3dmaster on 2005-07-02
Great! thanks for sharing!

---

### Post by dlpfmVfH on 2005-07-08
dabear:segmented downoads

valknut can do that for you...
there are debian packages..floating around on google...cause hoary isn't up to date...
or you can compile it...

---

### Post by anders on 2005-07-19
I seem to be having dependency problems with the dcpp package , here's the output:

```
$ sudo dpkg -i dcpp_0.0.20050701cvs-1~mird_i386.deb
Selecting previously deselected package dcpp.
(Reading database ... 89003 files and directories currently installed.)
Unpacking dcpp (from dcpp_0.0.20050701cvs-1~mird_i386.deb) ...
dpkg: dependency problems prevent configuration of dcpp:
 dcpp depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 dcpp depends on libstdc++6 (>= 4.0.0-7); however:
  Version of libstdc++6 on system is 4.0-0pre6ubuntu7.
dpkg: error processing dcpp (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dcpp

```

Everything seems to work fine if I force it to be installed, but that of course results in a broken package.

---

### Post by npu on 2005-07-19
nice one, mird!

could you add to/update your first post which patches are included in the latest package?

---

### Post by mird on 2005-07-21
[QUOTE=anders]I seem to be having dependency problems with the dcpp package , here's the output
...
Everything seems to work fine if I force it to be installed, but that of course results in a broken package.[/QUOTE]
Sorry about that, I'm using Ubuntu Backports so some of the libraries I have installed are newer than vanilla Hoary.  Since (as you've noticed) it should run fine on Hoary (without UBP updates) I'll fix those dependancies when I next build a new package (which will probably be in the next few days since there have been some neat patches released).

---

### Post by anders on 2005-07-22
Great! I'm looking forward to it!

---

### Post by mird on 2005-07-23
New package!  See the first post in this thread for more details.

---

### Post by Soulfly on 2005-07-24
[QUOTE=RadixLecti]Does this version work with å, ä , ö?
I've tried a version that didn't show ANY lines in mainchat containing those letters. Annoying like hell, it was.[/QUOTE]

You probably want to disable the UTF-8 locale for the program:

```

$ locale
LANG=sv_SE.UTF-8
LC_CTYPE="sv_SE.UTF-8"
LC_NUMERIC="sv_SE.UTF-8"
LC_TIME="sv_SE.UTF-8"
LC_COLLATE="sv_SE.UTF-8"
LC_MONETARY="sv_SE.UTF-8"
LC_MESSAGES="sv_SE.UTF-8"
LC_PAPER="sv_SE.UTF-8"
LC_NAME="sv_SE.UTF-8"
LC_ADDRESS="sv_SE.UTF-8"
LC_TELEPHONE="sv_SE.UTF-8"
LC_MEASUREMENT="sv_SE.UTF-8"
LC_IDENTIFICATION="sv_SE.UTF-8"
LC_ALL=

```

$ export LC_ALL="sv_SE"
$ <progam>

or (good for launchers/menuitems/...)

$ env LC_ALL="sv_SE" <program>

might do it. Beware that KDE session will not remember environment variables.

---

### Post by cleft on 2005-08-01
I thank the last poster that gave the copy and paste instructions. They were extremely helpful.

---

### Post by Hamman on 2005-08-01
[QUOTE=cleft]I thank the last poster that gave the copy and paste instructions. They were extremely helpful.[/QUOTE]
 Thanks! Worked nicely! Now they only have to replace those horrid WinXP icons with the standard GTK2 ones :P

---

### Post by Idiorrhythmic on 2005-08-04
I have the problem of dcpp not remembering my settings from the last session whenever I startup. Anyone have this problem or know of a solution?

I had it working properly before I reinstalled Ubuntu...

Thanks.

---

### Post by yyagol on 2005-08-05
DC++ crash all the time after 2 minits
i looked everyware still no aswer to this:
```
:~$ dcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault
```

---

### Post by ekravche on 2005-08-06
I have the same problem. I've recently moved away from XP to Ubuntu, and installed DC++ for linux. Linux DC++ hangs way to often! Not usable at all  ](*,)

---

### Post by SKLP on 2005-08-07
[QUOTE=mird] Install dependancies.[/QUOTE]Why would one have to manually install dependencies. Just add the dependencies to the package and edit the tutorial to say sudo apt-get -f install after the install of the package...

---

### Post by ekravche on 2005-08-08
Does anyone know how to update DC++? I was told that I need to checkout the latest source code from cvs and compile it. I also hear that the source code is updated, but not frequently. It seems like interest has been lost in this project, is this true?

---

### Post by bearbigears on 2005-08-08
i have foloowed this thread, i have a question and i know it's a newbie kind of question, but, what is linux dc++ and what does it do? i googled it and i got some not informative stuff. oh should i even be asking this questioj

 :-k  :-k

---

### Post by mird on 2005-08-09
More recent activity in the CVS means a new package.  See the first post in this thread as usual.

And now for some replies:

[QUOTE=Idiorrhythmic]I have the problem of dcpp not remembering my settings from the last session whenever I startup. Anyone have this problem or know of a solution?[/QUOTE]I can't help you sorry, other than to say that dcpp stores such information in [font=fixed]~/.dc++[/font], so check the permissions and/or try removing it.


[QUOTE=yyagol]DC++ crash all the time after 2 minits
i looked everyware still no aswer to this:[/QUOTE][QUOTE=ekravche]I have the same problem. I've recently moved away from XP to Ubuntu, and installed DC++ for linux. Linux DC++ hangs way to often! Not usable at all[/QUOTE]There could be one of a million things causing this problem.  It may be in relation to the differing libraries as mentioned earlier in this thread in which case you're welcome to try compiling from source to see if the problem goes away.  Otherwise I'm sorry I can't be more helpful.  It seems relatively stable to me and the people I know who also use it, although of course in it's current state of development it can't be considered anything other than unstable.  YMMV.


[QUOTE=SKLP]Why would one have to manually install dependencies. Just add the dependencies to the package and edit the tutorial to say sudo apt-get -f install after the install of the package...[/QUOTE]Thanks for the tip and yes you're correct, apt-get *should* be able to sort out dependancies for broken packages, and most of the time it does.  However in my experience it's not entirely reliable to do *what you'd expect* when dealing with such broken packages, and I think it makes more sense to simply install the dependancies explicitly.


[QUOTE=ekravche]Does anyone know how to update DC++? I was told that I need to checkout the latest source code from cvs and compile it. I also hear that the source code is updated, but not frequently. It seems like interest has been lost in this project, is this true?[/QUOTE]I try to keep the packages in this thread reasonably up to date.  Project development is still active albeit very slow, with little work being done by the project maintainers at the moment and most of the development coming in the form of user submitted patches.  For more information see the [project website](http://linuxdcpp.berlios.de), in particular the [mailing list](http://developer.berlios.de/mail/?group_id=2230) and [bugtracker](http://developer.berlios.de/bugs/?group_id=2230).


[QUOTE=bearbigears]i have foloowed this thread, i have a question and i know it's a newbie kind of question, but, what is linux dc++ and what does it do? i googled it and i got some not informative stuff. oh should i even be asking this questioj[/QUOTE]LinuxDC++ is an attempt to [port](http://en.wikipedia.org/wiki/Porting)  the popular Windows [Direct Connect](http://en.wikipedia.org/wiki/Direct_connect_file-sharing_application) [file-sharing](http://en.wikipedia.org/wiki/File_sharing) client [DC++](http://dcplusplus.sourceforge.net/) to the Linux platform.  Essentially it's a client for small to medium sized server-centric file-sharing networks.

---

### Post by bearbigears on 2005-08-09
thanks Mird, i appreciate it.

---

### Post by jax2000 on 2005-08-09
Thanks a lot !

---

### Post by SKLP on 2005-08-09
[QUOTE=mird]Thanks for the tip and yes you're correct, apt-get *should* be able to sort out dependancies for broken packages, and most of the time it does.  However in my experience it's not entirely reliable to do *what you'd expect* when dealing with such broken packages, and I think it makes more sense to simply install the dependancies explicitly.[/QUOTE]I see.

thx for the deb anyway... are you going to submit this to MOTU?

---

### Post by veratyr on 2005-08-10
Excellent! Works great.

---

### Post by Belfagor on 2005-08-11
hi! i ve downloaded and installed the package on my amd 64 hoary system with --force-all argument. when i try to run it on terminal by typing "dcpp" it gives me the error
"belfagor@ubuntu:~/Desktop$ dcpp
dcpp: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory
"

what does this mean? thanks from now on!

---

### Post by mird on 2005-08-11
[QUOTE=Belfagor]hi! i ve downloaded and installed the package on my amd 64 hoary system with --force-all argument. when i try to run it on terminal by typing "dcpp" it gives me the error[/QUOTE]
That's a rather odd error... you're not running Kubuntu by any chance?  [font=fixed]libglade-2.0.so.0[/font] should be installed as part of the [font=fixed]libglade-2.0[/font] package, which should be installed as part of the base Ubuntu system as it's required by Gnome.

---

### Post by Belfagor on 2005-08-12
it is installed and the symlink is placed under /usr/lib but it still coplains about this symlink... where must be the symlink placed?

---

### Post by mird on 2005-08-12
That's what it should be.  I imagine the problem may stem from the way I built the package - breaching a number of Debian packaging policies I'm sure ;).  I've been meaning to do something about this anyway so I can build proper AMD64 and PPC packages for those that want it, and so it's in a better form to submit to MOTU... 

I'll post here when it's done.

---

### Post by Belfagor on 2005-08-13
[QUOTE=mird]That's what it should be.  I imagine the problem may stem from the way I built the package - breaching a number of Debian packaging policies I'm sure ;).  I've been meaning to do something about this anyway so I can build proper AMD64 and PPC packages for those that want it, and so it's in a better form to submit to MOTU... 

I'll post here when it's done.[/QUOTE]
that would be great :) thanks from now on! \\:D/

---

### Post by tpls on 2005-08-14
DC++ is working great in my Ubuntu. Thanks a lot! But I have noticed one little bug (or should I say problem) in filelists. When I arrange files in list by size, it looks like this:

9,99 mb
920,00 kb
914,14 kb
7,98 mb 
698,77 mb
etc......

It would be much better when large files were in the beginning of the list. If it is a bug, hopefully it will be fixed, but if there is an another way to solve this problem, please let me know.

---

### Post by henrrrik on 2005-08-16
Works great! 
I tried compiling the CVS version myself, but I couldn't get it to download anything (searching worked just fine though).

Seems like I can finally ditch Valknut.  :grin:

---

### Post by Carcass on 2005-08-18
Hi, for language support you know anything?
can use the xml file that use in winzoz..... ;-)

---

### Post by denance on 2005-08-27
Nice package - looks pretty slick.
Is there anyway to do bandwidth limiting, so I can limit the download and upload rates used by dc++?

---

### Post by skatedawe on 2005-08-27
A tip for thoose who can't get it with "apt-get" with this package: "libstdc++6"

 Search it with synaptic...

---

### Post by werand on 2005-08-29
Tried doing as shown below, but it still doesn't work. I can't see any lines/perform  searchs that contains å,ä or ö. Any ideas?

/werand

[QUOTE=Soulfly]You probably want to disable the UTF-8 locale for the program:

```

$ locale
LANG=sv_SE.UTF-8
LC_CTYPE="sv_SE.UTF-8"
LC_NUMERIC="sv_SE.UTF-8"
LC_TIME="sv_SE.UTF-8"
LC_COLLATE="sv_SE.UTF-8"
LC_MONETARY="sv_SE.UTF-8"
LC_MESSAGES="sv_SE.UTF-8"
LC_PAPER="sv_SE.UTF-8"
LC_NAME="sv_SE.UTF-8"
LC_ADDRESS="sv_SE.UTF-8"
LC_TELEPHONE="sv_SE.UTF-8"
LC_MEASUREMENT="sv_SE.UTF-8"
LC_IDENTIFICATION="sv_SE.UTF-8"
LC_ALL=

```

$ export LC_ALL="sv_SE"
$ <progam>

or (good for launchers/menuitems/...)

$ env LC_ALL="sv_SE" <program>

might do it. Beware that KDE session will not remember environment variables.[/QUOTE]

---

### Post by finni on 2005-08-30
Got this working on Warty too. Nice work.  =D>

---

### Post by ekravche on 2005-08-31
**DC++ crashes for me** sometimes whenever file hashing is being executed. I'm sharing files in another locale. The files have Russian characters. For example chars like the ones below:

&#1042;&#1077;&#1089;&#1105;&#1083;&#1072;&#1103; &#1087;&#1086;&#1082;&#1086;&#1081;&#1085;&#1080;&#1094;&#1082;&#1072;&#1103; (1970).mp3

If devs can fix this bug, it would be really great!

---

### Post by sumadartson on 2005-09-05
Tnx mate, great package.

Life is sweet on a decent hub :D.

---

### Post by bored2k on 2005-09-13
Worked on breezy. Thanks.

---

### Post by cobrien44 on 2005-09-15
When I try to download the DEB package for dcpp, it doesn't work.  Anyone know of any mirrors to download from?

---

### Post by miga on 2005-09-20
hiya,

installed the client, working so far..

but..

I can't seem to add anything to the share bit..

I add a folder with, let's say mp3 ?

press the open button, add a virtual name to the folder..

seems to be doing some work for a little while, then nothing.. 0bytes .. and I'm sure it isn't 0 bytes.

Am I not doing something I should be doing? Files are not read only, files are not hidden, files are perfectly useable.. *shrug*

help? :)

---

### Post by Elcoco on 2005-09-21
im having trouble searching, i log into the room and everything but when i try to search for something it always comes back empty what's the deal. im set to active and everything. when i try to run it from terminal it hangs on shared files so i dont know what messege the search is sending to the terminal.

---

### Post by Hast la Vista on 2005-09-30
works nice but one problem is that nicknames with
for example ™ in them dont show up as users at all
and that i realy need to use [xxxx™]xxxx as operator in one hub
guess i can have my nickname changed but that dont look to good when all
other operators use it. but anyhow Linux DC++ is far better for me than Valknut.

---

### Post by burk on 2005-10-06
I have now installed DC++. I manage to run it (even in active mode) and i can connect to servers. The only problem is that sometimes it just shuts down without saying anything. I tried to run it from console and when it shuts down i get: "sementation fault". Do you know how to fix this..?

---

### Post by johannes on 2005-10-06
[QUOTE=burk]I have now installed DC++. I manage to run it (even in active mode) and i can connect to servers. The only problem is that sometimes it just shuts down without saying anything. I tried to run it from console and when it shuts down i get: "sementation fault". Do you know how to fix this..?[/QUOTE]

This is a bug that has been fixed in the 2005-09-14 version. Since *mird* hasn't updated this ubuntu-package since 2005-08-09 I would suggest you [install it from source]("http://www.ubuntuforums.org/showthread.php?t=28378&highlight=dc") to get rid of the problem. Uninstall the previous version before of course.

---

### Post by burk on 2005-10-06
This may sound as a stupid question but how do i ununstall the old version?? I know there is a menu item that says add/remove programs but when i click it it stops and hangs before showing the list of installed programs

---

### Post by johannes on 2005-10-06
Open "Synaptic Package Manager" from the menu, or open a terminal and type
```
gksudo synaptic
```
write your password. 

Search for "dcpp" (without the ""). Right click on the package and choose "Mark for removal", then Apply and Apply.

---

### Post by yorick on 2005-10-10
Hi!
I tried installing it from source today. It compiled okay. Only I  cant get it to work...
It only says:

Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault

Do you know of any solution? Thanks.

Edit: 
Nevermind, I got it to work. I backedup the .dc++ folder from my home directory. Then I erased it. Started dcpp, which created a new .dc++ folder. Copied the xml files from teh backup. EXCEPT dcplusplus.xml (the settings file). Now it works.

---

### Post by yabastard on 2005-10-15
thanks.

---

### Post by henkeboy on 2005-11-05
plz help! I can't get Linux DC++ working with åäö. I have tried with the tips on this thread without any results. Is there anybody who can get it working with åäö?? :confused:

---

### Post by RadixLecti on 2005-11-25
Nope, all lines in the chat containing &#229;, &#228;, &#246; and a few other special characters disappear. It's a bug that hasn't been ironed out yet.

---

### Post by nortonedd on 2005-11-27
As if they weren't enough thanks and praises, thank you very much for those instalation stepts. Works fine.

---

### Post by Arvin on 2005-12-05
Like me, have you got a problem to close DC++?
I have to force close it each time with Breezy badger 5.10.

---

### Post by Elcoco on 2005-12-06
ive been getting a segmentation fault when i enter certain hubs while on active mode, it works fine if im on passive, does anyone know why? i tried installing the latest version from cvs but it didnt help.

---

### Post by emmi on 2005-12-11
Hi, I've just recently install Linux DC++ and I'm having couple of problems with it.

Sometimes it works great. (happends rearly)
Sometimes when I've opened it and try to search some files it doesn't find anything and I can't browse any other user files and then it just crashes within 20seconds after it started.
And sometimes it finds alot of files and then it crashes...

Anyone know what the problem is?

---

### Post by martibs on 2006-01-01
Does anyone know a solution for this problem?

After a while DC++ suddenly just crashes, giving this output:

```

$ dcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
terminate called after throwing an instance of 'char const*'
Aborted

```

---

### Post by LaMpiR on 2006-01-02
[http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb](http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb) error 404 NOT FOUND
Please give me another link...

---

### Post by loftx on 2006-01-02
[QUOTE=LaMpiR][http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb](http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb) error 404 NOT FOUND
Please give me another link...[/QUOTE]

I've hosted the file temporarily at 
 [http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20050809cvs-1~mird_i386.deb](http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20050809cvs-1~mird_i386.deb)

---

### Post by loftx on 2006-01-02
I've created a package of the latest CVS release 20060101.cvs (though got my numbering mixed up and put 02's in places) which includes quite a few bugfixes and things.

Get it here:
[http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20060102cvs-1~loftx_i386.deb](http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20060102cvs-1~loftx_i386.deb)

**Warning:** this is the first deb I've ever created, and has been hacked about from mird's so if anything doesn't work uninstall it and reinstall his/hers.

I'm trying to contribute a bit of code to the project, so if anyone has any problems or ubuntu specific bugs I'll try and help first.

---

### Post by toots on 2006-01-06
Hi all!

Sorry for the mess, but I've also made a package for debian which is allready in the archive:
[http://packages.debian.org/linuxdcpp]("http://packages.debian.org/linuxdcpp")

It should then be sync with ubuntu one day or another...
Sorry for the double work I did not know that package..


Romain

---

### Post by tadazmas on 2006-01-11
mayby you know if there is any dc++ for amd64 architecture?

root@alijosius:~# sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
dpkg: error processing dcpp_0.0.20050809cvs-1~mird_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 dcpp_0.0.20050809cvs-1~mird_i386.deb
root@alijosius:~#

---

### Post by loftx on 2006-01-12
I think there is, but there's not a package available and you would need to compile it from source on the CVS. There's a guide for doing this at [http://ubuntuforums.org/showthread.php?t=28378](http://ubuntuforums.org/showthread.php?t=28378)

---

### Post by HarlemHenke on 2006-02-10
I have two mounted NTFS disk's (left from my windows time) on my computer, but every time I start DC++ the program starts to hash files that alredy are hashed and no changes is made on the harddrives... Why does DC++ do this?

---

### Post by loftx on 2006-02-10
Hmm, no Idea - it might  be due to the poor character handling support. If any of the files on the disk contain extended characters they might not get hashed properly. there's certainly no major issues with NTFS drives. Otherwise I don't know - try submitting a bug and hopefully someone will look into it.

---

### Post by optotron on 2006-02-27
'tis a truely great howto. Works great!
Great!

---

### Post by stevensheehy on 2006-03-22
In response to the people mentioning segmentation faults, please run in debug mode to help find out why it is crashing. Most of the time you will find that segmenation faults are caused by assertions that people's nicks must be greater than zero. This happens when the nick contains non-ascii characters that ldcpp can't convert. This is caused by a greater unicode problem that is not easy to fix (believe me, I tried). Anyway, to run in debug mode, see the debug section at our website:

[LinuxDC++ Manual]("http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Manual")

[QUOTE="tadazmas"]mayby you know if there is any dc++ for amd64 architecture?[/QUOTE]
Why not compile from source? I'm running AMD64 and it's working fine.
[QUOTE="HarlemHenke"]every time I start DC++ the program starts to hash files that alredy are hashed[/QUOTE]
This is a bug in the DC++ core that is fixed in more recent versions (>= 0.687). Naga is in the process of porting the most recent core to LinuxDC++.

---

### Post by Angellis_ater on 2006-06-10
How recent is this HOWTO and does it work with Dapper? (6.06)

---

### Post by loftx on 2006-06-11
[QUOTE=Angellis_ater]How recent is this HOWTO and does it work with Dapper? (6.06)[/QUOTE]

Not very - the howto uses very old packages and you won't be getting the latest bugfixes and improvements. The best way to get DC++ is to compile from the CVS. It's a little more complicated, though there's an up to date howto at [http://learn.clemsonlinux.org/wiki/Ubuntu:Compiling_Linux_DCpp](http://learn.clemsonlinux.org/wiki/Ubuntu:Compiling_Linux_DCpp)

---

### Post by stevensheehy on 2006-06-11
[QUOTE=Angellis_ater]How recent is this HOWTO and does it work with Dapper? (6.06)[/QUOTE]

I just wrote a new guide: [HOWTO: Install LinuxDC++]("http://www.ubuntuforums.org/showthread.php?t=193984")

---

### Post by s_spiff on 2006-07-26
neat man...thanks a lot. needed this desp.

---

### Post by seiferkai on 2006-08-14
omg thank you, you are a life-saver thank you so much
this was sooo much easier! i like easy

---

### Post by SlyBlyahoff on 2006-08-25
Hello. I am sorry for the stupid question but... I can't run dcpp :( I did the instructions wrote up, but after that i can't find where it is installed. Locate command didn't help, man also :( 
Please tell me how to do that, or if it there's something wrong.
By the way i am with ubuntu 5.10.
Thanks in advance.

---

### Post by stevensheehy on 2006-08-26
> **SlyBlyahoff said:**
> Hello. I am sorry for the stupid question but... I can't run dcpp :( I did the instructions wrote up, but after that i can't find where it is installed. Locate command didn't help, man also :( 
Please tell me how to do that, or if it there's something wrong.
By the way i am with ubuntu 5.10.
Thanks in advance.

If you followed the instructions in this thread, I cannot offer support to you. Use the new howto I created that I linked to a couple posts up and post again on that thread.

I don't know why you guys keep bringing this old thread back to life, these instructions are not the correct way to install ldcpp! Just let this thread die.

---

### Post by PerXes on 2006-09-01
When I try "sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb" I get the following error:

dpkg: error processing dcpp_0.0.20050809cvs-1~mird_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 dcpp_0.0.20050809cvs-1~mird_i386.deb

Is it not possible to run Linux DC++ on amd64?

---

### Post by stevensheehy on 2006-09-02
> **PerXes said:**
> When I try "sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb" I get the following error:

dpkg: error processing dcpp_0.0.20050809cvs-1~mird_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 dcpp_0.0.20050809cvs-1~mird_i386.deb

Is it not possible to run Linux DC++ on amd64?

Sonuva...

Use the new [howto]("http://www.ubuntuforums.org/showthread.php?t=193984&page=1"). I run LinuxDC++ on AMD64 every day. This package is a year old, LinuxDC++ is completely different nowadays.

---

### Post by artootra on 2006-10-13
Why it don't find anything?

---

### Post by tck on 2007-09-28
Alot of servers need up to date clients.

try sudo apt-get install dcgui

---

### Post by aparigraha on 2007-09-29
LinuxDC++ 1.0.0 has been released
get it [HERE.]("http://www.getdeb.net/app.php?name=Linux+DC%2B%2B")

---

### Post by bratliff on 2007-11-03
Seems to work, but will not download a hub.


Robert Ratliff

---

### Post by archak on 2012-03-09
when I try
wget [http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb](http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb)
I get
ERROR 407: Proxy Authentication Required :(

what to do?

---

