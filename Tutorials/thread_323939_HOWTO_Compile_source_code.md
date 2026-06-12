---
title: "HOWTO: Compile source code"
date: 2006-12-23
forum: Tutorials
---

### Post by pay on 2006-12-23
Howto Compile Source Code on Ubuntu

One thing that I have noticed is a lot of new users to Ubuntu have trouble when it comes to compilling source code. Hopefully, after this guide you will see it as the rather simple task that it really is. First thing, make sure that you have the basic compillers, otherwise you won't be able to compile anything. Open up the terminal and type in ```
sudo aptitude install build-essential
```A few other tools that can come in usefull are automake1.9, libtoolize, subversion, cvs and checkinstall.

Now we are on to the fun stuff:) I'll use an example of compilling mplayer (gui) with x264, xvid and ffmpeg support. There are a few ways to download the source and compile it so I will show multiple ways to do each section.

Part 1 &#8211; Compilling XviD
Firstly, download the source code. There are a few ways to do this.

      1)   Using apt
            ```
apt-get source xvid
```

2)Browsing the website and extracting it
```
wget http://downloads.xvid.org/downloads/xvidcore-1.1.2.tar.bz2
tar jxvf xvidcore-1.1.2.tar.bz2
```(note: for a tar.gz archive use tar zxvf <archive>)

3) Using developer cvs/svn repositories
 ```
cvs -d:pserver:anonymous@cvs.xvid.org:/xvid login    #(just type enter)
 cvs -d:pserver:anonymous@cvs.xvid.org:/xvid co xvidcore
```

Now make sure that you have all the dependencies needed to compile the code.```
sudo apt-get build-dep xvid
```will download everything you need (Make sure that you have the deb-src repo enabled). If you get errors while configureing about a missing library or package, install that package;)

Secondly, configure the source code. For cvs it is slightly different (for xvid anyway, normally the readme will give clues). For cvs only run ```
./bootstrap.sh
```before ./configure. Now change the directory to where you have extracted the source code to```
cd ${xvidcore}/build/generic
```Now the hard part. Picking what options you want to compile the source code with. My recommened way is ```
./configure CFLAGS="-march=athlon64 -O2 -pipe -mtune=athlon64&#8221; CHOST="x86_64-pc-linux-gnu"  MAKEOPTS="-j2" &#8211;prefix=/usr
``` This ./configure command will result in optimised code, which should be faster but may make debugging almost impossible. Don't open a new bug report unless if you compile it generically (ie ./configure &#8211;prefix=/usr). Here's a list of CFLAGS recommened for different processors. [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)
For more information on CFLAGS look here [http://gcc.gnu.org/onlinedocs/gcc-3.4.1/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc-3.4.1/gcc/Optimize-Options.html)

Now Compile the source with make```
make
```

Once that finishes without any errors you will have the program compilled in that directory. You can use it to make sure that it works as expected before installing it. There are a few ways to intall the software. A simple```
sudo make install
``` will install it as is. Using checkinstall you can make a debian file with```
sudo checkinstall -D make install
sudo dpkg -i <package>.deb
```Also you can make a more generic debian file with```
sudo dpkg-buildpackage
```However, it will just compile a generic package without optimisations. Also```
sudo apt-get &#8211;build source
``` will make a generic debian package of the source code. Hopefully there is someone that has found this information useful. Recommendations and constructive cristisms are encouraged.

TO BE CONTINUED with x264, ffmpeg with enabling features (xvid and x264 support) and mplayer with a gui and codec support.

---

### Post by Kossilar on 2007-01-26
Well I hate to be the one to say this, and I feel like a total jackass, but this isn't helpful at all. Its much too specific. 

It seems like each individual piece of software needs its own configurations at build time. Frankly I need a manual, or a separate piece of software if I'm ever going to figure out how to do this. It would be nice if Linux devs could come up with a standard so that we could skip this compiling crap and start using the damn software.

---

### Post by pay on 2007-01-26
Have you tried reading the README that comes with the source code?

---

### Post by Ramses de Norre on 2007-01-26
Why a howto? It's as simple as unzip and read the READ_ME and INSTALL files..., all info is in their and if not you should contact the developer.

And a standard is quite impossible because of the big differences between programs, but that's why there are instructions included in every package.

---

### Post by pay on 2007-01-26
The readmes don't have information like where to get the dependencies and they are less specific to Ubuntu. Also, some people look for help here first than elsewhere. And I realise that this is hardly a standard, but I tried to help people that have never compiled anything before to get a general idea of what it is like.

---

### Post by RedSquirrel on 2007-04-07
> **pay said:**
> Howto Compile Source Code on Ubuntu

A few other tools that can come in usefull are automake1.9, [COLOR=Red]libtoolize[/COLOR], subversion, cvs and checkinstall.


I would recommend that you mention the package is named *libtool* so that people can find it in the repositories. ;)

---

### Post by Endolith on 2007-09-08
> **pay said:**
> 2)Browsing the website and extracting it
```
wget http://downloads.xvid.org/downloads/xvidcore-1.1.2.tar.bz2
tar jxvf xvidcore-1.1.2.tar.bz2
```(note: for a tar.gz archive use tar zxvf <archive>)

You claim that this is "to help people that have never compiled anything before", but if so, it doesn't seem like you put a lot of thought into what those people are familiar with.

Why do people persist in using the command line for EVERYTHING?   This is not helpful at all.  A web browser is infinitely more intuitive and familiar than wget.  File-roller is much more intuitive than tar, and handles .tar.bz2, .tar.gz, and whatever else, without requiring special command switches for each type.

Ubuntu is supposed to be a user-friendly OS.  Please describe user-friendly tools that people are familiar with and do everything "the Ubuntu way" as much as possible, instead of "the old way".

> **RedSquirrel said:**
> I would recommend that you mention the package is named *libtool* so that people can find it in the repositories. ;)

Yes.  Another example.   I couldn't find this in Synaptic.  And you should explain what these tools actually *do*, instead of just saying "tools that can come in usefull".  I know checkinstall creates a package in Synaptic, so that it can more easily be upgraded and uninstalled, but why would you mention subversion in a tutorial like this?

---

### Post by Amazona aestiva on 2007-09-08
I just needed this!

Thanks!

---

### Post by Endolith on 2007-09-08
Here are some documents on help.ubuntu.com:
[LIST]
[*][https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[*][https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[/LIST]

---

### Post by netimen on 2007-10-12
I have downloaded the newest version of source code and apt-get build-dep says all dependencies are OK (because it checks for the previous version). But ./configure always finds new missing packages and I have to install those packages and then run ./configure from the beginning and wait before it founds a new error. Can I know all missing packages at one time?

---

### Post by Scimu on 2007-11-01
Thanks.. This has gave me a little insight into how you actually do this.

---

### Post by Blingin2Mingin on 2007-12-30
I needed the very latest source code, so I actually found this most helpful,

---

### Post by picpak on 2007-12-30
> **pay said:**
> Also```
sudo apt-get –build source
``` will make a generic debian package of the source code.

Can you elaborate more on this? Does it create Debian standard debs? Do you do it to the source package or the source folder?

---

### Post by the real omni on 2008-07-28
> **Endolith said:**
> Why do people persist in using the command line for EVERYTHING?   This is not helpful at all.

On the contrary. I'm generally new to the linux scene, having migrated recently from Vista and having been a long time GUI user.

I personally find how-to's with command line a heck of a lot easier, faster, and more efficient to follow/execute than a GUI-based tutorial as you can accomplish with one copy/paste what takes a series of 10-50 mouse movements and button clicks. Also you don't have to wait for any GUI windows to load before you can click one checkmark and dismiss the window. It's just an extra --OPTION=parameter setting, which is all part of the single copy/paste action. 

With a command-line copy/paste it's simply faster and easier to get the job done. 

You might not be ingraining the GUI-method into your memory, but every time you read "wget (address-of-remote-file)" you understand more and more what it does and how to use it. (Likewise with any other command-line code) so instead of building your memory based on the slow and inefficient way of doing things, you're building your memory based on the professional, fast, effective way to do things and when you're proficient enough to do it professionally, you're getting 20 minutes work done in 5 by using the command line and thus your time can be worth a lot more money. Even if you're not doing it professionally, it's just good sense to learn the RIGHT way from the start.

Moreover, GUI's change from version to version. Command-line typically stays the same. If tutorials were mainly based on GUI's they'd have to be updated constantly.

I definitely agree that this tutorial is a bit too specific and also a bit too ambiguous in some areas but even as a linux freshman I have to say I prefer command-line-based how-to's nine times out of ten.

One last note: if you actually bite the bullet and make an effort to type out the commands instead of just copy/pasting then you will learn a LOT faster and you'll learn the back-end commands that all the various GUI's use so it won't matter what program/GUI you're trying to work with, you'll know the methodology of getting the job done. As I say I'm new to linux but just by typing out command line instructions for the past couple weeks I've already gotten to the point where I can perform most actions without having to go back and re-consult the walk-through (and in a lot of cases without having to bring up a walk-through at all in the first place).

---

### Post by Endolith on 2008-07-28
> **the real omni said:**
> You might not be ingraining the GUI-method into your memory, but every time you read "wget (address-of-remote-file)" you understand more and more what it does and how to use it.

A good computer interface wouldn't require you to learn about how the program works in order to use it.  

> so instead of building your memory based on the slow and inefficient way of doing things, you're building your memory based on the professional, fast, effective way to do things

A good computer interface wouldn't require the memorization of cryptic commands to get things done.  The GUI is a better, more efficient interface because it's discoverable.  You don't have to read through a manual to figure out how to do something; in a well-written program, it's obvious what you can do from the options presented to you.

> Moreover, GUI's change from version to version. Command-line typically stays the same.

Not only do command line tools change from version to version, they change from one program to another.  Each has its own idiosyncratic switch syntax that differs from all the rest, requiring you to memorize a separate set of code letters for each program (even for similar options).  It is not an intuitive or usable interface, and we should not be recommending it to new users unless no other option exists.

Teaching new users to copy and paste arbitrary commands from the Internet into a terminal without understanding what they do creates a very dangerous mentality that opens them up to exploitation by malicious users.  See [this notice]("http://ubuntuforums.org/announcement.php?f=328") for an example.

---

### Post by JoshuaRL on 2008-07-29
> **Endolith said:**
> A good computer interface wouldn't require you to learn about how the program works in order to use it.

Well, a good interface might.  But a great one will give you a choice as to whether you want to use a GUI or CLI.  And it makes all the documentation for either readily available either on the system (man pages or help menus) or online.  That way you can choose which you want.

> A good computer interface wouldn't require the memorization of cryptic commands to get things done.  The GUI is a better, more efficient interface because it's discoverable.  You don't have to read through a manual to figure out how to do something; in a well-written program, it's obvious what you can do from the options presented to you.

Well, true.  And one thing you have to remember is that you are posting this in a HOWTO for compiling.  That is a command line set of instructions.  And you really don't need to know how to compile unless you need something really special.  For example, if you need a application that is not in the repos, is not available in a convienient DEB, or you need something fully optimized.  So, most users don't really need to know this.  But if you wanted to make a simple little Python GUI for compiling and keep it up, I'm sure you would have the love of the people.

> Not only do command line tools change from version to version, they change from one program to another.  Each has its own idiosyncratic switch syntax that differs from all the rest, requiring you to memorize a separate set of code letters for each program (even for similar options).  It is not an intuitive or usable interface, and we should not be recommending it to new users unless no other option exists.

Well, not true really for Linux.  CLI commands change very little from version to version.  And many applications are similar for similar tasks.  For instance:  APT, Aptitude, and dpkg all have similar CLI phraseology for handling packages.  Also, when you do something wrong in CLI it often spits out an error along with help as to how to do it right.  I think that qualifies as intuitive.

> Teaching new users to copy and paste arbitrary commands from the Internet into a terminal without understanding what they do creates a very dangerous mentality that opens them up to exploitation by malicious users.  See [this notice]("http://ubuntuforums.org/announcement.php?f=328") for an example.

All good points.  That's why most of the push is to make HOWTOs GUI unless you need the CLI for some reason.  Also, most good HOWTOs explain what the commands mean instead of just "copy this into the terminal."  

And I'm sure you'll agree that no amount of security software will stop this kind of "social engineering."  The only answer is a slightly questioning mindset and plenty of good instruction.  And I believe that Linux, and especially Ubuntu is pretty far along with this.  There's so many places to get good information and help from seasoned users.

---

### Post by LiQuidAiR on 2009-01-14
Thank you Pay for taking the time to write this "How To".  I did find some of the paragraphs confusing but I found something that compliments your article.  Try
[http://tuxarena.blogspot.com/2008/09/compiling-cc-code-in-ubuntu-and.html](http://tuxarena.blogspot.com/2008/09/compiling-cc-code-in-ubuntu-and.html)

as it also provides alittle more information to what the first part of the sudo apt-get install build-essential does and how to compile a easy "Hello world!" application.

Regards.

---

### Post by LiQuidAiR on 2009-01-14
I also ran across this:
[http://coderstalk.blogspot.com/2008/02/simple-linux-socket-programming-in.html](http://coderstalk.blogspot.com/2008/02/simple-linux-socket-programming-in.html)

Here he explains the code from:
[http://linuxgazette.net/issue74/tougher.html](http://linuxgazette.net/issue74/tougher.html)

The first link listed on this post will direct you on how to start off writing your first socket program.  Sockets are used to communicate across a network.  This enables more than one computer to talk to each other.  I would be more than happy to help anyone with questions.  This program was simple enough for me to compile and fix the few bugs I encountered.

I'm very new to this stuff also so please have patience for me as well :)

---

### Post by BIGtrouble77 on 2009-01-16
I just had to reply to this howto as some of the comments here are asinine.  First off, Pay, thanks for the effort.  This is actually pretty useful.  I forgot how to create debs from source so it was nice to see a reference to that here.

For those of you who are whining about how hard linux aps are to install realize that Ubuntu has the Add/Remove Software feature specifically for you!  You don't even need to fire up Synaptic to install apps. It can't get any easier than that.

Also realize that the ability to compile your software out-of-the-box is an AMAZING feature of gnu linux.  It's not straight forward to get a c compiler going in windows, and you are probably going to need to fork over $$ to get one.  The gcc compiler in linux is simply an added bonus.  You absolutely don't need it to run 99% of the apps you'll use.  Most projects have binaries available, and they install just like .exe windows files.

Pay is just trying to help you out if you like running bleeding edge apps or want to install something more obscure that's not in the repos.  It's really only going to help you if you have some curiosity to learn a little more about the system you're using.  Linux is the ultimate power users/hacker os.  The command line stuff should be for fun hacking, use the repositories if you want things to 'just work' quickly.

-bt

edit: lol, I didn't realize this was resurrected from months ago.

---

### Post by fixerdave on 2009-02-06
Just wanted to add my thanks for this quick tutorial - it came up at the top of my Google search.

All I was looking for was a quick example of "what do they mean when they say compile from source?" This tutorial fit the bill just fine.  Now, I've got the source for the package I'm interested it, its dependencies, and I'm well on my way to figuring out the rest.  Thank you.

Oh, and off-topic but as a professional Windows tech that makes a living installing and supporting software, I firmly believe Ubuntu is way, way, way easier to install software -- just hit the check-box and then OK.  It makes the Windows EULA-hell/option-overload OK, OK, OK, OK...  look totally stupid.  I can get a complete (apps included) install of Ubuntu up and running with less than 5% of the effort involved with Windows, just because I don't have to sit there going OK, OK, OK.  Best of all, Ubuntu has an OPTIONAL command-line interface that offers huge amounts of power.  And, if I really want to, I can download the source, modify it or some compile options, and then make my own package, which is not off-topic at all :)

David (an Ubuntu convert, can you tell?)

---

### Post by tyeo098 on 2009-04-19
Idk why people are nay-saying your tut.
With this tut I installed qemu!

Thanks alot!

---

### Post by Funnnny on 2009-04-19
You should only remember 3 line of code, which are widely using in most of program here:
```

./configure
make
sudo make install

```
Most of program will install, if you can get it to work, just read the readme, or Install file, or just ask here.

---

### Post by brian_hayward on 2009-05-05
I realize this post is going to deviate from the subject but does Linux/Ubuntu have a spokesperson?  If not, I nominate Funnnny for the job.  Pretty sure she would raise a lot of attention for the group.

---

### Post by hardinej on 2009-05-28
I don't know if you'll see this pay or not but I thought it was useful. I needed a new version of something that had to be compiled from source and the sudo apt-get build-dep oldVersion tip was helpful for me. I'm still new and I didn't know that was an option.

---

### Post by mtinman on 2009-06-28
./configure
make
sudo make install

Works fine when you have a configure script in the source package, but what does one do with an older source package that does not contain the configure script? Keep in mind that I do not know yet how to make my own configure script...

---

### Post by samh785 on 2009-10-23
I find it interesting that it can only be *very insightful *or *confusing as hell*. :P No middle ground?

I did find it fairly easy to understand however, and I applaud you on the effort to make a how-to on the subject.

---

### Post by skarychinezeguie on 2010-01-20
i know i should ask the writer instead of you guys but can anyone tell me how to compile this source in 9.1? i've never compiled anything in linux before and the terminal confuses me. i just want to run this app to use the fan speed tool, not the overclocking portion.

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

i checked out the readme and got as far as this
> First you have to do ./autogen.sh to create the configure script and
other build files.

After running autogen.sh you need to run the configure script to 
generate Makefiles to build NVClock. By default the script tries to
locate GTK / QT and if found it enables building of the GTK / QT GUIs.i took this as launch the autogen.sh by double clicking. the terminal popped up and flashed a few OK's and then went away. so i went on to double click configure which did the same. flashed some stuff that looked ok and then gone.

skipping on down i get to
> Once NVClock is configured run the commands below to compile and install it:
make
make installi assume however since the terminal didn't stay open that i need to some how navigate back to that directory in a new terminal window to run the make and make install commands. any help would be greatly appreciated.

on a side note, is there a compiler tool with a GUI, you know, for those silly windows users who want to switch away from windows to linux. ;)

---

### Post by mister_playboy on 2010-01-20
> **Funnnny said:**
> You should only remember 3 line of code, which are widely using in most of program here:
```

./configure
make
sudo make install

```
Most of program will install, if you can get it to work, just read the readme, or Install file, or just ask here.

That's exactly what I recently figured out.  I was always frustrated by the lack of specific instructions in README files, and I thought "they don't mention these steps because it's assumed everyone already knows what it is."

Well, I didn't figure it out until I had been using Linux for nearly a year, and I'm sure I'm not alone in that.

---

### Post by skarychinezeguie on 2010-01-20
ok, well could you just gimme a quick step-by-step for this instance? like:

1.open terminal
2. type .... to go here
3. then run these 3 commands like this ....

i appreciate your empathy and quick response. i really wanna see ubuntu give os x and windows a run for their [COLOR=Green]$MONEY$[/COLOR]. I've already started adding to the ubuntu wiki's. i found some differences in my experience than what was described in the tutorial so i described my alternative, more windows-like, example.

if we all work together, in no time we'll be playing games and running windows apps better than they can.

---

### Post by bcoffield on 2010-02-26
Awesome post!  Very helpful!  Thank you!

---

### Post by pawtracks on 2010-05-09
> **pay said:**
> Howto Compile Source Code on Ubuntu
 
One thing that I have noticed is a lot of new users to Ubuntu have trouble when it comes to compilling source code. Hopefully, after this guide you will see it as the rather simple task that it really is. First thing, make sure that you have the basic compillers, otherwise you won't be able to compile anything. Open up the terminal and type in ```
sudo aptitude install build-essential
```A few other tools that can come in usefull are automake1.9, libtoolize, subversion, cvs and checkinstall.
 
Now we are on to the fun stuff:) I'll use an example of compilling mplayer (gui) with x264, xvid and ffmpeg support. There are a few ways to download the source and compile it so I will show multiple ways to do each section.
 
Part 1 – Compilling XviD
Firstly, download the source code. There are a few ways to do this.
 
1) Using apt
```
apt-get source xvid
```
 
2)Browsing the website and extracting it
```
wget http://downloads.xvid.org/downloads/xvidcore-1.1.2.tar.bz2
tar jxvf xvidcore-1.1.2.tar.bz2
```(note: for a tar.gz archive use tar zxvf <archive>)
 
3) Using developer cvs/svn repositories
```
cvs -d:pserver:anonymous@cvs.xvid.org:/xvid login    #(just type enter)
 cvs -d:pserver:anonymous@cvs.xvid.org:/xvid co xvidcore
```
 
Now make sure that you have all the dependencies needed to compile the code.```
sudo apt-get build-dep xvid
```will download everything you need (Make sure that you have the deb-src repo enabled). If you get errors while configureing about a missing library or package, install that package;)
 
Secondly, configure the source code. For cvs it is slightly different (for xvid anyway, normally the readme will give clues). For cvs only run ```
./bootstrap.sh
```before ./configure. Now change the directory to where you have extracted the source code to```
cd ${xvidcore}/build/generic
```Now the hard part. Picking what options you want to compile the source code with. My recommened way is ```
./configure CFLAGS="-march=athlon64 -O2 -pipe -mtune=athlon64” CHOST="x86_64-pc-linux-gnu"  MAKEOPTS="-j2" –prefix=/usr
``` This ./configure command will result in optimised code, which should be faster but may make debugging almost impossible. Don't open a new bug report unless if you compile it generically (ie ./configure –prefix=/usr). Here's a list of CFLAGS recommened for different processors. [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)
For more information on CFLAGS look here [http://gcc.gnu.org/onlinedocs/gcc-3.4.1/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc-3.4.1/gcc/Optimize-Options.html)
 
Now Compile the source with make```
make
```
 
Once that finishes without any errors you will have the program compilled in that directory. You can use it to make sure that it works as expected before installing it. There are a few ways to intall the software. A simple```
sudo make install
``` will install it as is. Using checkinstall you can make a debian file with```
sudo checkinstall -D make install
sudo dpkg -i <package>.deb
```Also you can make a more generic debian file with```
sudo dpkg-buildpackage
```However, it will just compile a generic package without optimisations. Also```
sudo apt-get –build source
``` will make a generic debian package of the source code. Hopefully there is someone that has found this information useful. Recommendations and constructive cristisms are encouraged.
 
TO BE CONTINUED with x264, ffmpeg with enabling features (xvid and x264 support) and mplayer with a gui and codec support. Epic How To:) little bit confusing tho :confused:

---

### Post by CvdW on 2010-05-24
My hat off to the people that take the time to try and assist the world - such as the author of this How-To, thank you!
As to the people that feel compelled to write negative, non-constructive comments - here are some thoughts for you.

[LIST]
[*]It takes you about a minute to jot down your negative, snide little remark.
[*]It takes a How-To author hundreds of minutes to write a decent How-To that isn't filled with errors.
[*]How-To authors invariably get slammed for their work by other people (such as you) that could "obviously" do a much better job - but don't.
[*]The bottom line is this - if you have nothing constructive to say then say nothing.
[/LIST]

To Pay, I realize you are unlikely to ever see this post but thank you for your effort. Keep up the good work and how about an update?

---

### Post by Clubjob on 2010-08-30
When i type in one of the commands then it gives me no output of what happende and just went back to 
```
andee@andee-laptop:~/client$
```
in terminal.

Any advise on what is wrong?

---

### Post by robnils on 2011-02-06
Probably not a great idea to keep this thread going on for so long but I decided to post anyway in the event it may help someone eventually who stumbled on it from Google (like I did). 

Thought the article was good, really enjoyed reading it. Maybe you could edit it and explain the parameters you used in configure but other than that, pretty helpful! 

I'm surprised no one has mentioned this but anyone new to this should read the Ubuntu article:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Really informative and easy to read and afterwards you'll understand this how-to much better.

@ [skarychinezeguie]("http://ubuntuforums.org/member.php?u=1000567"):

Open terminal.
Use "cd" to change directory to where you've extracted your source files (extract the file by right-clicking on it and selecting Extract here). Say it's in the Home folder. For me, it would be: cd /home/rob/foo/, where "foo" is the name of the folder that the source files are in. It's important that folder hierarchy is preserved so that commands used point to the right locations. From there, run the three commands mentioned. That's the basic three steps you asked for. But read the link I gave because there's more to it than that, and you need to have a lot of other things installed for this to work. 

Just a bit of advice to save someone from any needless searching.

---

### Post by lokino on 2011-07-06
I've snipped my post to put it in a newer topic later. PLEASE DELETE

---

### Post by hayesaustin on 2012-06-16
2011_0719_rt3070_V2.5.0.3_DPO.b2z
was downloaded from ralink to install a wifi adapter into linux and these were the drivers.. after the read me, the makefile.. f**k Trying to compile source code in .b2z files!! were is our "automatic compiling of .b2z folders" [installer software application] automation that will turn them into .deb?!? i dont understand terminal luanguage?!? The .EXE was there to make it EASY!! [[automatic compiling of .b2z folders, will become an automation Software building application]] any sorce .b2z that you get, should automatically be compiled with this new Compiling Software... What the F**K?!? *Face, Palm..
 
Automatic .b2z compiling and installing application...
does this Exist?
 
 
Q: a computer does what?
A: it makes the advanced sh*t simple..
..The EXE, hmm wonder why windows is the most chosen.

---

### Post by steamer360 on 2013-07-17
Arggh I need to compile Wine source code. Anyone know how to do this?:confused:

---

### Post by deadflowr on 2013-07-17
> **steamer360 said:**
> Arggh I need to compile Wine source code. Anyone know how to do this?:confused:

[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)

---

### Post by oldos2er on 2013-07-19
Old thread closed.

---

