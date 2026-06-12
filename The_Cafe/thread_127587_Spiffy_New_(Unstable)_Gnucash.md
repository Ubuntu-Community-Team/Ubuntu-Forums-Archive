---
title: "Spiffy New (Unstable) Gnucash"
date: 2006-02-09
forum: The Cafe
---

### Post by kleeman on 2006-02-09
Gnucash has always had a very ugly interface imho. The new version though is nice with gnome2. I managed to build it on breezy after a few false starts. Here is a screenshot. I can put the deb up if anyone is interested but be warned it is very unstable.

---

### Post by Brunellus on 2006-02-09
that's a hell of an expense breakdown.  

New Shirt: $ 16.05
Rent:  $3,206.99

Free software:  Priceless.

There are some things money can buy.  For everything else, there's GNU.

---

### Post by kleeman on 2006-02-09
What's the old saying?
Location Location Location
Oh and a crappy new shirt!

---

### Post by Stormy Eyes on 2006-02-09
It's about time they started using GTK2.x in GNUcash.

---

### Post by waldorf on 2006-02-09
When is it expected to be stable and when will it be in the ubuntu repositories?

---

### Post by kverde on 2006-02-09
Any tips on how to install this would be appreciated.

---

### Post by zenwhen on 2006-02-09
Please provide the .deb

---

### Post by Greg T. on 2006-02-09
A few false starts, indeed. 

There's apparently an issue with Breezy's version of g-wrap that caused my attempt to compile GnuCash to exit with an error. The issue is described here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=323462](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=323462) 

I found the fixed version of these files from a Debian repository:

[http://rpmseek.com/rpm/g-wrap_1.9.6-3_i386.html?hl=com&cbn=0:G:0:2230419:0:0:0](http://rpmseek.com/rpm/g-wrap_1.9.6-3_i386.html?hl=com&cbn=0:G:0:2230419:0:0:0)
[http://rpmseek.com/rpm-dl/libgwrap-runtime0-dev_1.9.6-3_i386.html?hl=com&cs=libgwrap-runtime0-dev:PN:0:0:0:0:2230423](http://rpmseek.com/rpm-dl/libgwrap-runtime0-dev_1.9.6-3_i386.html?hl=com&cs=libgwrap-runtime0-dev:PN:0:0:0:0:2230423)
[http://rpmseek.com/rpm/libgwrap-runtime0_1.9.6-3_i386.html?hl=com&cs=libgwrap-runtime0:PN:0:0:0:0:2230425](http://rpmseek.com/rpm/libgwrap-runtime0_1.9.6-3_i386.html?hl=com&cs=libgwrap-runtime0:PN:0:0:0:0:2230425)

That allowed me to compile, but GnuCash crashed on startup with the message: 

> <unnamed port>: In procedure scm-error in expression (scm-error (quote misc-error) #f ...):
<unnamed port>: no code for module (g-wrap gw standard)

---

### Post by kleeman on 2006-02-09
Grab the deb from here:

[http://www.yourfilelink.com/get.php?fid=22569](http://www.yourfilelink.com/get.php?fid=22569)

No guarantees about unmet dependencies. My system is pretty loaded up with libraries coz I like to compile ;-). If you do have unmet dependencies  look here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and use the search the contents of packages on the missing library to find out which packages you need to install.

---

### Post by kleeman on 2006-02-09
BTW be careful with your old financial records from earlier versions of gnucash. This is a development unstable pile of .... so might bork your precious records!

---

### Post by UbuWu on 2006-02-10
[QUOTE=kleeman]If you do have unmet dependencies  look here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and use the search the contents of packages on the missing library to find out which packages you need to install.[/QUOTE]

Easier way:

sudo dpkg -i *packagename*.deb
sudo apt-get -f install

The first command will give an error about missing dependencies, the second will download and install them and complete the installation. Can't get much easier ;)

---

### Post by Greg T. on 2006-02-10
kleeman's deb worked for me. I tried it after upgrading to Dapper last night.

---

### Post by denisesballs on 2006-02-10
I had the same issues with the gw wrapper when try to compile from source which can be seen here:

```
o .libs/gw-engine.o
cc1: warnings being treated as errors
gw-engine.c: In function 'gw__tmp426_xaccQueryAddDateMatch_wrapper':
gw-engine.c:16599: warning: 'gw__scm_extras[0]' is used uninitialized in this function
make[5]: *** [gw-engine.lo] Error 1
make[5]: Leaving directory `/home/jesse/systems/gnucash-1.9.0/src/engine'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/jesse/systems/gnucash-1.9.0/src/engine'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/jesse/systems/gnucash-1.9.0/src/engine'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jesse/systems/gnucash-1.9.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jesse/systems/gnucash-1.9.0'
make: *** [all] Error 2
```

Using the deb though, I get an error when starting and it won't open, anyone know why?

```
jesse@breezydump:~/systems/gnucash-1.9.0$ sudo dpkg -i ../gnucash-1.9.0_1.9.0-1_i386.deb
Selecting previously deselected package gnucash-1.9.0.
(Reading database ... 133221 files and directories currently installed.)
Unpacking gnucash-1.9.0 (from .../gnucash-1.9.0_1.9.0-1_i386.deb) ...
Setting up gnucash-1.9.0 (1.9.0-1) ...
jesse@breezydump:~$ gnucash
gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.1: cannot open shared object file: No such file or directory
```

EDIT!!!

I'm a retard:

Installed the following packages:
libbz2-dev (1.0.2-7ubuntu2)
libgsf-1-dev (1.12.3-3ubuntu3)
libgsf-gnome-1 (1.12.3-3ubuntu3)
libgsf-gnome-1-dev (1.12.3-3ubuntu3)

Open fine now. Thanks for the deb!

---

### Post by Oni-Dracula on 2006-02-10
me too, denisesballs... I just realized that when I read your post

Palm -> Forehead....

---

### Post by kverde on 2006-02-11
Seems to be working for me...  No crashes yet.  This is MUCH better than the old interface imho.  

Can you put up .debs here of the updated versions as they get released?  Or better yet, point me to how I can take the source and create my own (and even post them here)?

Thanks for the help!

---

### Post by charlieg on 2006-02-15
**denisesballs:** I don't think you need to install the -dev packages.

I'm having trouble getting that .deb to work on Dapper.

I installed the relevant guile packages and had to make a couple of libgsf symlinks in /usr/lib to get it to run.  I went through the setup taking the default options and once the setup druid had run it's course I hit a problem:
```
charlie@ubuntu-lap1:~$ gnucash
ERROR: In procedure primitive-load-path:
ERROR: Unable to find file "slib/init/guile.init" in load path
```
Any ideas?

---

### Post by charlieg on 2006-02-15
Hmm... slib and guile-slib look like they need to make an appearance!  Trying it...

EDIT: Yup, working good.

---

### Post by charlieg on 2006-02-20
Any prospect of a .deb for 1.9.1?

---

### Post by kleeman on 2006-02-20
I'll give it a whirl....
Looks like a ton of bugfixes in there

Edit: OK it compiled fine and runs OK although I can't generate piecharts for some reason. Oh well development version.....

Here's the deb:


[http://www.yourfilelink.com/get.php?fid=31943](http://www.yourfilelink.com/get.php?fid=31943)

---

### Post by sdb2028 on 2006-02-21
try'd to install gnucash with both apt-get and synaptic, got this error both times:

E: lilypond-data: subprocess post-installation script returned error exit status 1

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libart2_1.4.2-20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libart2_1.4.2-20_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnomeui32_1.4.2-20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnomeui32_1.4.2-20_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnorba27_1.4.2-20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnorba27_1.4.2-20_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/gnome-libs-data_1.4.2-20_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/gnome-libs-data_1.4.2-20_all.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnome32_1.4.2-20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libgnome32_1.4.2-20_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libzvt2_1.4.2-20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-libs/libzvt2_1.4.2-20_i386.deb)
  Size mismatch


Any suggestions?

---

### Post by DigitalDuality on 2006-02-21
glad to see the interface upgraded :)

that being said... i do have one big complaint with linux apps...

it gets really old seeing apps named K____, Gnu____. or G___  

/pettiness

---

### Post by kleeman on 2006-02-21
Try a different repository (replace us by de in your /etc/apt/sources.list file as root)

---

### Post by sdb2028 on 2006-02-22
Thanks for your suggestion to try different repository, it didn't work.
Said it wasn't available or obsoleted and was refered to by another package.

---

### Post by charlieg on 2006-02-23
[QUOTE=DigitalDuality]glad to see the interface upgraded :)

that being said... i do have one big complaint with linux apps...

it gets really old seeing apps named K____, Gnu____. or G___  

/pettiness[/QUOTE]
If it was petty, why say it?

---

### Post by DigitalDuality on 2006-02-23
same reason you just said what you just did.

i felt like it

---

### Post by jimjawn on 2006-02-24
This is pretty nice.  The interface and chart of accounts gets a little crazy but damn if this isn't like 100 times better than the last version of gnucash that I used a couple of years ago.

For installation on breezy with the common edited /etc/apt/sources.list

sudo dpkg -i gnucash-1.9.0_1.9.0-1_i386.deb
sudo apt-get install gnucash

That got it working for me.  Hope that helps.

---

### Post by yoyoned on 2006-02-26
I had to run the following to get the posted dep to work in dapper.
```

cd /usr/lib
ln -s libgsf-1.so.113.0.3 libgsf-1.so.1
ln -s libgsf-gnome-1.so.113.0.3 libgsf-gnome-1.so.1

```

---

### Post by shamrock_uk on 2006-02-27
Thanks yoyoned! You've just saved me some dependency head-scratching!

Much obliged for the .deb, kleeman.

---

### Post by kleeman on 2006-02-27
[QUOTE=yoyoned]I had to run the following to get the posted dep to work in dapper.
```

cd /usr/lib
ln -s libgsf-1.so.113.0.3 libgsf-1.so.1
ln -s libgsf-gnome-1.so.113.0.3 libgsf-gnome-1.so.1

```[/QUOTE]
Not surprised by that. On breezy the dependencies were pretty tricky to work out to get this darned thing to compile.

---

### Post by kleeman on 2006-03-08
New Development version out 1.9.2 Seems more stable. Nice interface but I can't get the pie charts working yet Doh!

Grab the deb for Ubuntu here:

[http://www.yourfilelink.com/get.php?fid=43363](http://www.yourfilelink.com/get.php?fid=43363)

Enjoy!

---

### Post by spiritraveller on 2006-03-18
Thanks for packaging this kleeman.

The following is what I had to do to get it running on a currently up-to-date Dapper desktop.

```
sudo apt-get install slib guile-1.6-slib libgsf-1-113 libgsf-gnome-1-113 libgnutls11 libgwrapguile1 libltdl3 libofx2c2a

cd /usr/lib

sudo ln -s libgsf-1.so.113.0.99 libgsf-1.so.1
sudo ln -s libgsf-gnome-1.so.113.0.99 libgsf-gnome-1.so.1
```

A window came up talking about gconf search paths.  Selecting "install in home directory" was the best option.  When I selected the other option, the first start dialogue didn't come up.  That's the window that asks if you want to start the tutorial (doesn't work), set up new accounts, or import your QIF files.

So far, this looks like a vast improvement over the old gnucash.

---

### Post by kleeman on 2006-03-22
New development release 1.9.3. Seems a bit more stable to me and my pie and bar charts are working nicely and I am able to open the old stable gnucash accounts.

Get it while it's hot:

 [http://www.yourfilelink.com/get.php?fid=55184](http://www.yourfilelink.com/get.php?fid=55184)

---

### Post by grendel_khan on 2006-03-23
I'm building it myself (on a Breezy system) so I can install it in parallel with my older, stable version of gnucash. I'm getting this build error with 1.9.3 and the current SVN version:

In file included from /usr/include/gtk-2.0/gtk/gtk.h:60,
                 from gnc-gobject-utils.c:29:
/usr/include/gtk-2.0/gtk/gtkclist.h:155: error: syntax error before 'GMemChunk'
cc1: warnings being treated as errors
/usr/include/gtk-2.0/gtk/gtkclist.h:155: warning: no semicolon at end of struct or union
/usr/include/gtk-2.0/gtk/gtkclist.h:156: warning: type defaults to 'int' in declaration of 'cell_mem_chunk'
/usr/include/gtk-2.0/gtk/gtkclist.h:156: warning: data definition has no type or storage class
/usr/include/gtk-2.0/gtk/gtkclist.h:245: error: syntax error before '}' token
In file included from /usr/include/gtk-2.0/gtk/gtk.h:68,
                 from gnc-gobject-utils.c:29:
/usr/include/gtk-2.0/gtk/gtkctree.h:110: error: field 'clist' has incomplete type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:152,
                 from gnc-gobject-utils.c:29:
/usr/include/gtk-2.0/gtk/gtkstatusbar.h:68: error: syntax error before 'GMemChunk'
/usr/include/gtk-2.0/gtk/gtkstatusbar.h:68: warning: no semicolon at end of struct or union
/usr/include/gtk-2.0/gtk/gtkstatusbar.h:82: error: syntax error before '}' token
make[4]: *** [gnc-gobject-utils.lo] Error 1
make[4]: Leaving directory `software/gnucash-1.9.3/src/core-utils'
make[3]: *** [all] Error 2
make[3]: Leaving directory `software/gnucash-1.9.3/src/core-utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `software/gnucash-1.9.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `software/gnucash-1.9.3'
make: *** [all] Error 2

I have libgtk2.0-dev 2.8.6-0ubuntu2.1 installed. Did anyone else run into this problem, and did you find a way of solving it?

EDIT: This also happens with 1.9.1 and 1.9.2. Something I did with my installation must have mucked it up. Does anyone have any idea what happened? I found this error on a page explaining that [someone needed to install gtk+](http://forums.vidalinux.com/viewtopic.php?p=9244&sid=90550efd79d23fb99891ed6bdbe27ad8).

EDIT 2: Oh. Somehow I had upgraded my libglib to 2.10.1-0ubuntu1, the dapper version (and libgdiplus as well), so that I could build autopano-sift. Why did I do that? Installing dapper packages on breezy leads to tears. Terrible, terrible tears. Let this be a lesson to me. I'm not deleting this post so that other people can fix the issue if they do the same thing, but my problem is solved, and gnucash now builds properly.

---

### Post by Tom^ on 2006-03-29
kleeman, I got the gnucash 1.9.3 working with Dapper when I installed libgwrapguile1. Without it gnucash complained about lack of libgwrap-wct.so.1

Update: and guile-1.6-slib needed to be installed too.

---

### Post by andrewski on 2006-04-06
kleeman, version 1.9.4 has been released.  Could you upgrade the package? ;)

---

### Post by kleeman on 2006-04-06
No worries. Here you go:

[http://www.yourfilelink.com/get.php?fid=70626](http://www.yourfilelink.com/get.php?fid=70626)

Works very nicely now....

---

### Post by andrewski on 2006-04-06
Awesome.  You rock.

---

### Post by spiritraveller on 2006-04-08
[QUOTE=grendel_khan]I'm building it myself (on a Breezy system) so I can install it in parallel with my older, stable version of gnucash.[/QUOTE]

You don't need to build it yourself for that.  The package installs into /usr/local, so you can install it in parallel with the older gnucash, with no problems.

---

### Post by dpm on 2006-04-10
Hi,

I just wanted to share my experiences installing kleeman's deb package on my Breezy system. Since the deb itself has no dependency information, it was a bit tricky for me to get it working, so I thought I'd post what I did in the hope that it can help someone else.

So, I started by installing some necessary dependencies (I found out which ones I needed by trial and error):
  
```
apt-get install slib libofx2 libgwrapguile1 libgsf-gnome-1 libgwrap-runtime0 libgnutls10
``` 
Once the dependencies were resolved, I installed the package itself:

```
dpkg -i gnucash-1.9.4_1.9.4-1_i386.deb
``` 
After that, I got the first error trying to run gnucash from the command line:

```
ERROR: Could not find slib/require.scm in  ("/usr/share/guile" "/usr/local/share/gnucash/guile-modules" "/usr/local/share/gnucash/scm" "" "/usr/share/guile/site" "/usr/share/guile/1.6" "/usr/share/guile" ".")
``` 
which I solved by creating a link to slib in /usr/share/guile/1.6:

```
cd /usr/share/guile/1.6
``` ```
sudo ln -s /usr/share/slib/
``` 
After running gnucash from the command line and going through the setup, gnucash failed halfway through the process of loading with the following message:

```
ERROR: In procedure open-file:
``` ```
ERROR: Permission denied: "/usr/share/guile/1.6/slibcat"
``` 
After googling a bit, I found out that a way of creating slibcat is by running gnucash as root. So I ran

```
sudo gnucash
``` 
then I chose to skip the setup process and finally exit gnucash.

After that, I could run gnucash as a normal user without (apparent) problems.

Any comments/corrections on these "instructions" for gnucash will be more than welcome. And needless to say, many thanks to kleeman for providing us with the deb package.

Cheers.

---

### Post by andrewski on 2006-04-10
[quote=desp]I just wanted to share my experiences installing kleeman's deb package on my Breezy system. Since the deb itself has no dependency information, it was a bit tricky for me to get it working, so I thought I'd post what I did in the hope that it can help someone else.

So, I started by installing some necessary dependencies (I found out which ones I needed by trial and error):
  
```
apt-get install slib libofx2 libgwrapguile1 libgsf-gnome-1 libgwrap-runtime0 libgnutls10
```[/quote]
Thanks for the how-to.  My question is why the package doesn't have any dependency info.  I think if the dependencies are resolved correctly, the rest of your instructions are unnecessary.  (I installed some mentioned elsewhere in this thread, and didn't have to do anything else.)

---

### Post by dpm on 2006-04-10
[quote=andrewski] I think if the dependencies are resolved correctly, the rest of your instructions are unnecessary. (I installed some mentioned elsewhere in this thread, and didn't have to do anything else.)[/quote] 
I also think that having the dependency info in the package would make things easier, although I'm not sure if that would automatically solve all the problems I encountered. Other people may have other problems as well.

Basically, having the dependency info would have the same effect as running 'apt-get install <all-necessary-dependencies>' before installing the package, but nothing more (please someone more knowledgeable correct me if I'm wrong).

There are some *-dev dependencies mentioned in this thread which I did not want to install. Generally you only need this kind of packages when compiling from source. I only wanted to install the absolutely necessary runtime dependencies (since my filesystem is full enough without unnecessary packages...)

Finally, these somewhat rudimentary "how-to" I put together applies to Breezy only, which is what I'm running. I see from your avatar that you are running Dapper, which is a completely different story. 

Anyway, thanks for your input, bit by bit we'll get this whole thing moving. I can't wait for a stable release with gtk2 support... The more users get this development version running, the better for the project.

Cheers.

---

### Post by andrewski on 2006-04-10
> **desp]Basically, having the dependency info would have the same effect as running 'apt-get install <all-necessary-dependencies>' before installing the package, but nothing more (please someone more knowledgeable correct me if I'm wrong).[/quote]
...except that when you manually install them, they aren't stored as being installed only as a dependency of something else.  If you ever try to use a tool like deborphan to clean up orphaned packages, IIRC these aren't accounted for.  Not a big deal, but something that should be addressed IMO.

[quote=desp]Finally, these somewhat rudimentary "how-to" I put together applies to Breezy only, which is what I'm running. I see from your avatar that you are running Dapper, which is a completely different story.[/quote]
True said:**
>  Anyway, thanks for your input, bit by bit we'll get this whole thing moving. I can't wait for a stable release with gtk2 support... The more users get this development version running, the better for the project.
Indeed!  What would really help would be for us users to report any bugs we find.  That's the key for us users to helping get this thing stable and released!  Wahoo for community!

---

### Post by kleeman on 2006-04-10
This package was created by checkinstall hence the absence of dependency info. Given that it is still a development series piece of software I am reluctant to try a proper kosher deb yet.

---

### Post by kleeman on 2006-04-20
New development version is out. Sounds like it is getting close to a 2.0.0 stable release- a lot of bugfixes. Works well for me. You have to hand it to the gnucash developers: after a period of relative inactivity they have really sprung to life. Perhaps the threat of kmymoney has concentrated their minds.... Get it here:

[http://www.yourfilelink.com/get.php?fid=84662](http://www.yourfilelink.com/get.php?fid=84662)

---

### Post by kleeman on 2006-05-18
BETA RELEASE! Looking really good. Final (version 2.0.0) is not far off now (week or two?). Here is the breezy deb:

[http://www.yourfilelink.com/get.php?fid=105057](http://www.yourfilelink.com/get.php?fid=105057)

---

### Post by andi5 on 2006-05-20
You might also check [http://packages.debian.org/unstable/gnome/gnucash](http://packages.debian.org/unstable/gnome/gnucash), in case you have not already done so :)

---

### Post by spiritraveller on 2006-05-20
thanks andi5.  I built some debs for dapper drake from the sources for the debian unstable package.  Since it comes from the debian source, the dependencies are already defined in the package.

[gnucash_1.9.6-3_i386.deb]("http://www.yourfilelink.com/get.php?fid=106376")
[gnucash-common_1.9.6-3_all.deb]("http://www.yourfilelink.com/get.php?fid=106378")

I don't know if it will work on Breezy.

---

### Post by kleeman on 2006-06-06
Version 1.9.7 (second beta) is out. Release is imminent. Here is a Dapper deb for those interested:

[http://www.yourfilelink.com/get.php?fid=115454](http://www.yourfilelink.com/get.php?fid=115454)

---

### Post by dabear on 2006-06-06
[QUOTE=kleeman]Version 1.9.7 (second beta) is out. Release is imminent. Here is a Dapper deb for those interested:

[http://www.yourfilelink.com/get.php?fid=115454](http://www.yourfilelink.com/get.php?fid=115454)[/QUOTE]
please tell me if this version have ful/almost full compilance with flash7? Also, is the firefox plugin in the same package?

---

### Post by andrewski on 2006-06-06
[quote=kleeman]Release is imminent.[/quote] :twisted: This just sounded too portentous to pass up.

Thanks for the packages kleeman; you rock! \\:D/

---

### Post by ScislaC on 2006-06-06
[QUOTE=kleeman]Version 1.9.7 (second beta) is out. Release is imminent. Here is a Dapper deb for those interested:

[http://www.yourfilelink.com/get.php?fid=115454](http://www.yourfilelink.com/get.php?fid=115454)[/QUOTE]


Kleeman, I have been unable to get any of the Gnucash 1.9x series running on my box... until now. THANK YOU!!!  :D

---

### Post by rjcsc on 2006-06-07
[QUOTE=kleeman]Version 1.9.7 (second beta) is out. Release is imminent. Here is a Dapper deb for those interested:

[http://www.yourfilelink.com/get.php?fid=115454](http://www.yourfilelink.com/get.php?fid=115454)[/QUOTE]


I have this error:

gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory


Can someone help me?  ](*,)

---

### Post by andrewski on 2006-06-07
[quote=rjcsc]I have this error:

gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory[/quote]

A few things mentioned earlier in the thread:
[quote=UbuWu]sudo dpkg -i *packagename*.deb
sudo apt-get -f install

The first command will give an error about missing dependencies, the second will download and install them and complete the installation. Can't get much easier.[/quote]

[quote="denisesballs"] Installed the following packages:
libbz2-dev (1.0.2-7ubuntu2)
libgsf-1-dev (1.12.3-3ubuntu3)
libgsf-gnome-1 (1.12.3-3ubuntu3)
libgsf-gnome-1-dev (1.12.3-3ubuntu3)[/quote]

Post back if you have any more trouble; I can't recall which helped me, and I'm not at my system at the moment.

---

### Post by spiritraveller on 2006-06-08
Here is version 1.9.7 repackaged for Ubuntu from the Debian source package.  Since these are built from official Debian packages, all of the dependencies are defined, and they should be a piece of cake to install with the gui installer.  Either double-click after downloading, or open them directly from firefox.


Just be sure to install gnucash-common first, because gnucash depends on it.

[gnucash-common_1.9.7-1_all.deb](http://www.yourfilelink.com/get.php?fid=116644)
[gnucash_1.9.7-1_i386.deb](http://www.yourfilelink.com/get.php?fid=116643)
[checksums.md5](http://www.yourfilelink.com/get.php?fid=116645)

Oh, by the way, these will replace gnucash 1.8.x if you have it installed.  As they come from Debian, they install into the main system rather than /usr/local.

And if you are unsure about installing something that a stranger gives you on the internet, try building them yourself... you will have to add the Debian Unstable source repository in /etc/apt/sources.list:
```
deb-src http://ftp.us.debian.org/debian/ unstable main
```

And the rest is [not all that difficult](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-sourcepkgs).

---

### Post by andrewski on 2006-06-08
[quote=spiritraveller]Here is version 1.9.7 repackaged for Ubuntu from the Debian source package.  Since these are built from official Debian packages, all of the dependencies are defined, and they should be a piece of cake to install with the gui installer.[/quote]

Indeed; thanks! =D>

---

### Post by btdown on 2006-06-11
Wow looks good and got it to work using the debs above. Any idea when 2.0 is going to break?

Also, is anyone using Gnucash to manage accounting for a small business? I'd like to open up a consulting firm on the side and thought Gnucash might be the best Linux option.

Thanks 
BT

---

### Post by kleeman on 2006-06-12
Here's some relevant info:

[http://lwn.net/Articles/184630/](http://lwn.net/Articles/184630/)

---

### Post by kleeman on 2006-06-19
Release Candidate for 2.0 now out. Here is a Dapper deb:

[http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb](http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb)

To make 2.0 a good release please report bugs to:

[http://bugzilla.gnome.org/enter_bug.cgi?product=GnuCash](http://bugzilla.gnome.org/enter_bug.cgi?product=GnuCash)

---

### Post by forrestcupp on 2006-06-19
[QUOTE=kleeman]Release Candidate for 2.0 now out. Here is a Dapper deb:

[http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb](http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb)

[/QUOTE]

Where did you get 2.0?  I just looked at their website, and it still said the latest is 1.9.7

---

### Post by kleeman on 2006-06-19
The latest version is 1.9.8 and if you read the announcement this is designated as a release candidate for 2.0. The final version should be out in a couple of weeks or so....

---

### Post by bruce89 on 2006-06-19
I updated Wikipedia with the news. (I always update software releases)

---

### Post by kleeman on 2006-06-19
And as a special bonus for Ubunteros here are some very comprehensive beta docs for the upcoming 2.0 release:

[http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-docs-1.9.0_1.9.0-1_i386.deb](http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-docs-1.9.0_1.9.0-1_i386.deb)

---

### Post by waldorf on 2006-06-19
Wow, very spiffy indeed!

Question: when I open the application it takes close to five minutes to open. Any thoughts or similar experiences?

---

### Post by kleeman on 2006-06-19
Wierd! Mine takes 5 seconds max. Is it doing anything? Execute at the command line and see if you can discover anything....

---

### Post by waldorf on 2006-06-19
[QUOTE=kleeman]Wierd! Mine takes 5 seconds max. Is it doing anything? Execute at the command line and see if you can discover anything....[/QUOTE]
I get this:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

and then after 5 minutes or so I get this:

gnucash: [M] "Found Finance::Quote version "1.08

and then gnucash will open up in all its new spiffiness.

I dunno?

---

### Post by kleeman on 2006-06-19
The error messages you are seeing seem to be coming up a lot lately in Ubuntu (search the forums and launchpad)  and according to some people are caused by a bad wacom driver see here:

[http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930)

Nothing to do with gnucash specifically I don't think......

---

### Post by forrestcupp on 2006-06-19
I know you can print checks with gnucash, but does anyone know if it is possible to print a complete check on blank checkstock with your MIRC routing number, and account number and everything?  If it's not possible, does anyone know of a Linux program that can do that?

---

### Post by xxbartosxx on 2006-06-19
Hi,
I get these error:
> gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory
Any ideas?
Installed libgsf-bin, but still the same error
grts Bart

---

### Post by waldorf on 2006-06-19
[QUOTE=kleeman]The error messages you are seeing seem to be coming up a lot lately in Ubuntu (search the forums and launchpad)  and according to some people are caused by a bad wacom driver see here:

[http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930)

Nothing to do with gnucash specifically I don't think......[/QUOTE]
hmmm. Thanks. I guess I'll sit tight. Its not a huge deal.

---

### Post by kleeman on 2006-06-19
[QUOTE=xxbartosxx]Hi,
I get these error:

Any ideas?
Installed libgsf-bin, but still the same error
grts Bart[/QUOTE]

Try
sudo apt-get install libgsf-1-113

---

### Post by waldorf on 2006-06-20
[QUOTE=kleeman]Release Candidate for 2.0 now out. Here is a Dapper deb:

[http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb](http://www.math.nyu.edu/faculty/kleeman/dapper/gnucash-1.9.8_1.9.8-1_i386.deb)

To make 2.0 a good release please report bugs to:

[http://bugzilla.gnome.org/enter_bug.cgi?product=GnuCash](http://bugzilla.gnome.org/enter_bug.cgi?product=GnuCash)[/QUOTE]
where can i get the gnucash-common that goes with this?

---

### Post by forrestcupp on 2006-06-20
[QUOTE=waldorf]where can i get the gnucash-common that goes with this?[/QUOTE]

I'd like to know this, too.  I had to go back to v. 1.9.7 because I couldn't find the appropriate common file

---

### Post by kleeman on 2006-06-20
This is a standalone deb which installs a seperate package (with 1.9.8 appended) to your regular dapper gnucash and gnucash-common packages. To execute the 1.9.8 version use:

/usr/local/bin/gnucash

There is no conflict it just puts the files in a different location to the usual dapper gnucash packages. Someone else above issued REPLACEMENT gnucash and gnucash-common packages for 1.9.7. This was not me.

---

### Post by andi5 on 2006-07-06
Feel free to update

[http://wiki.gnucash.org/wiki/Ubuntu](http://wiki.gnucash.org/wiki/Ubuntu)
[http://wiki.gnucash.org/wiki/BreezyBadgerInstallation](http://wiki.gnucash.org/wiki/BreezyBadgerInstallation)

Me personally would love to see GnuCash 2.0 be available in Dapper, but this will not be possible, right? Maybe someone someday starts to host a really cool dapper-updates or such :) ... Edgy frightens me...

---

### Post by andrewski on 2006-07-06
[quote=andi5]Me personally would love to see GnuCash 2.0 be available in Dapper, but this will not be possible, right? Maybe someone someday starts to host a really cool dapper-updates or such :) ... Edgy frightens me...[/quote]
dapper-backports?

---

### Post by andi5 on 2006-07-06
](*,) 
thanks a lot :KS somehow i did not see that one

---

### Post by kleeman on 2006-07-10
Unstable no more :D :D :D Version 2.0.0 has been released. Get the deb (with hbci compiled in) here:

[http://www.yourfilelink.com/get.php?fid=133508](http://www.yourfilelink.com/get.php?fid=133508)

and the documentation here:

[http://www.yourfilelink.com/get.php?fid=133506](http://www.yourfilelink.com/get.php?fid=133506)

Note that these debs are installed side by side with the dapper gnucash (from the 1.* series)
and must be executed with

/usr/local/bin/gnucash

If you have dependency issues when installing these debs (use "sudo dpkg -i DEBNAME.deb") please read the entire thread to find solutions.

Also make sure you deinstall earlier 1.9 series debs (use synaptic to find them).

---

### Post by ScislaC on 2006-07-10
> **kleeman said:**
> Note that these debs are installed side by side with the dapper gnucash (from the 1.* series)
and must be executed with

/usr/local/bin/gnucash


Is there any particular reason why you still want them to install side-by-side rather than replacing the 1.* series?

---

### Post by kleeman on 2006-07-10
> **ScislaC said:**
> Is there any particular reason why you still want them to install side-by-side rather than replacing the 1.* series?

No none. The reason I did this was because the Debian infrastructure is not in place yet so I used checkinstall to generate debs. A better long term solution would be a backport.

For those interested I generated a new deb with ofx import and directconnect capability (i.e. get your data directly from your bank). To set it up you need to do two things which aren't obvious:

1) Launch  Tools---> HBCI Setup and on the second page of the wizard launch the aqhbci wizard with the ofx option checked 

2) There is a bug in the aqofx package meaning a library is misplaced. To fix do the following

cd /usr/lib

sudo ln -s /usr/lib/aqbanking/plugins/0/providers/aqofxconnect.so.1.0.1 libaqofxconnect.so.0

Works then.

Here is the new deb:

[http://www.yourfilelink.com/get.php?fid=133573](http://www.yourfilelink.com/get.php?fid=133573)

Disclaimer: I take no responsibility for any usage of this software.

---

### Post by dpm on 2006-07-10
Thank you, thank you, thank you, thank you!!!

I've just installed your .deb and GnuCash 2.0.0 with HBCI is working like a charm.

The last version I had installed was 1.9.5, compiled from source, and it was a bit of a pain to get HBCI with AqBanking working. Now with the checkinstall .deb, I only had to install the package and re-run the HBCI wizard and everything worked -the re-run seemed to be required simply because my HBCI settings were removed after I uninstalled gnucash-1.9.5.

Cheers.

---

### Post by kleeman on 2006-07-10
> **desp said:**
> Thank you, thank you, thank you, thank you!!!

I've just installed your .deb and GnuCash 2.0.0 with HBCI is working like a charm.

The last version I had installed was 1.9.5, compiled from source, and it was a bit of a pain to get HBCI with AqBanking working. Now with the checkinstall .deb, I only had to install the package and re-run the HBCI wizard and everything worked -the re-run seemed to be required simply because my HBCI settings were removed after I uninstalled gnucash-1.9.5.

Cheers.
No worries ;-)

---

### Post by djaya2 on 2006-07-10
> **kleeman said:**
> No none. The reason I did this was because the Debian infrastructure is not in place yet so I used checkinstall to generate debs. A better long term solution would be a backport.

For those interested I generated a new deb with ofx import and directconnect capability (i.e. get your data directly from your bank). To set it up you need to do two things which aren't obvious:

1) Launch  Tools---> HBCI Setup and on the second page of the wizard launch the aqhbci wizard with the ofx option checked 

2) There is a bug in the aqofx package meaning a library is misplaced. To fix do the following

cd /usr/lib

sudo ln -s /usr/lib/aqbanking/plugins/0/providers/aqofxconnect.so.1.0.1 libaqofxconnect.so.0

Works then.

Here is the new deb:

[http://www.yourfilelink.com/get.php?fid=133573](http://www.yourfilelink.com/get.php?fid=133573)

Disclaimer: I take no responsibility for any usage of this software.
Thanks for making this package.  I just installed it and, unfortunately, I get the following error when I run '/usr/local/bin/gnucash':

gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory

Any ideas?  (I'm using Kubuntu Dapper, don't have any previous versions of GnuCash installed.  Have been trying unsuccessfully to get Quicken 2006 running through wine and would love to use a linux app instead.)  Thanks.

---

### Post by kleeman on 2006-07-10
Try
sudo apt-get install libgsf-gnome-1-113

You must not have some gnome libraries installed because you have Kubuntu

---

### Post by djaya2 on 2006-07-10
Thanks.  That worked---and got me to another library I don't have.  This time the error is that 'libgnutls.so.11' is missing.  Is there a way I can derive the names of the packages from the error messages so I don't have to keep bugging you with questions?  (Before I posted, I had tried 'sudo apt-get install libsf-gnome-1.so.113', but that guess was slightly off.  Now, for the new error, I've tried 'sudo apt-get install libgnutls-11', but that doesn't work.)  Thanks again . . .

---

### Post by andrewski on 2006-07-10
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libgnutls.so.11&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libgnutls.so.11&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386)

Generally, I try to search p.u.c and can usually find the package I'm looking for.

---

### Post by djaya2 on 2006-07-10
Yeah, I managed to find the next couple by search in Adept.  I guess that works well enough.  But there's no standard convention so that you don't have to search/guess?

---

### Post by ScislaC on 2006-07-10
[QUOTE=kleeman]No none. The reason I did this was because the Debian infrastructure is not in place yet so I used checkinstall to generate debs. A better long term solution would be a backport.[/QUOTE]

K... that makes sense. :)

[QUOTE=kleeman]Here is the new deb:

[http://www.yourfilelink.com/get.php?fid=133573](http://www.yourfilelink.com/get.php?fid=133573)[/QUOTE]

First off, thanks... it installed fine and runs like a charm! :) 

For some reason I don't have that HCBI stuff in the Tools menu though... just 4 entries and that's not one of them. In case it matters, I did only install this package and not the one posted earlier. Any ideas?

---

### Post by djaya2 on 2006-07-10
Okay, sorry to keep peppering this thread with questions.  I got past all the library problems but now have others.  On my first run, the program started to walk through a setup process but crashed in the middle.  Now, when I run, it crashes right after the splash screen shows.  The terminal gives this output:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: No such file or directory
ERROR: In procedure primitive-load-path:
ERROR: Unable to find file "slib/init/guile.init" in load path


Thanks again and sorry again . . .

---

### Post by kleeman on 2006-07-10
> **ScislaC said:**
> K... that makes sense. :)



First off, thanks... it installed fine and runs like a charm! :) 

For some reason I don't have that HCBI stuff in the Tools menu though... just 4 entries and that's not one of them. In case it matters, I did only install this package and not the one posted earlier. Any ideas?

Fire up synaptic and search for libaqbank and install those packages (there are a few). Then search for hbci and install the one package there. 

I'm assuming this is why you don't see the menu item. With my system I have five entries in the menu.

---

### Post by dpm on 2006-07-10
> **djaya2 said:**
> Thanks.  That worked---and got me to another library I don't have.  This time the error is that 'libgnutls.so.11' is missing.  Is there a way I can derive the names of the packages from the error messages so I don't have to keep bugging you with questions?  (Before I posted, I had tried 'sudo apt-get install libsf-gnome-1.so.113', but that guess was slightly off.  Now, for the new error, I've tried 'sudo apt-get install libgnutls-11', but that doesn't work.)  Thanks again . . .

```
sudo apt-get install libgnutls11
``` 
without the hyphen should work

For a list of package dependencies required by gnucash 2.0.0, have a look at the debian package in the unstable distribution. The link is for version 1.9.8, but the dependencies should be the same for 2.0.0: [http://packages.debian.org/unstable/gnome/gnucash](http://packages.debian.org/unstable/gnome/gnucash)

I reckon if you install libgnome2-0, it should pull most of the dependencies via apt for you.

Cheers

---

### Post by kleeman on 2006-07-10
> **djaya2 said:**
> Okay, sorry to keep peppering this thread with questions.  I got past all the library problems but now have others.  On my first run, the program started to walk through a setup process but crashed in the middle.  Now, when I run, it crashes right after the splash screen shows.  The terminal gives this output:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: No such file or directory
ERROR: In procedure primitive-load-path:
ERROR: Unable to find file "slib/init/guile.init" in load path


Thanks again and sorry again . . .
Try installing slib. As andrewski said above try searching with the ubuntu packages website to find the files you are missing (guile.init here)

---

### Post by djaya2 on 2006-07-10
Great.  Appears to be working fine now, and I have a much better idea what to do if I have more problems.  Thanks!!!!!

---

### Post by mazirian on 2006-07-10
Thanks for generating the packages so quickly.  I've been a gnucash user for a couple years now and I've been hesitating to update to the gnc2 tree for months now.  I think I'll make the plung tonight.

---

### Post by ScislaC on 2006-07-10
[QUOTE=kleeman]Fire up synaptic and search for libaqbank and install those packages (there are a few). Then search for hbci and install the one package there. 

I'm assuming this is why you don't see the menu item. With my system I have five entries in the menu.[/QUOTE]

Kleeman... You have officially earned the highly coveted "best friend of the week" status with me. :) That was what was missing... (haven't set it up yet, but I have the entry in the menu now). Thank you so very much!

---

### Post by farang.geek on 2006-07-10
Hi everyone! the developers of GnuCash just released 2.0 Stable!  Yahoo! now if anyone can just provide a DEB for this.... :D

---

### Post by wikki on 2006-07-10
I"ve got the 2.0 deb installed, but I don't see the the options to setup the online downloads.  Maybe i'm not looking in the right place?

---

### Post by wikki on 2006-07-10
> **wikki said:**
> I"ve got the 2.0 deb installed, but I don't see the the options to setup the online downloads.  Maybe i'm not looking in the right place?

nevermind I was just missing the aqbanking libs.

I don't see the ofx checkbox though.  Looks like I might need the 0.8.1 version of libofx.  But their doesn't seem to be a deb for that.  I really hate to have too much crap compiled and installed manually.  

What are the chances that this stuff will be updated and dropped into ubuntu?

---

### Post by kleeman on 2006-07-10
> **wikki said:**
> nevermind I was just missing the aqbanking libs.

I don't see the ofx checkbox though.  Looks like I might need the 0.8.1 version of libofx.  But their doesn't seem to be a deb for that.  I really hate to have too much crap compiled and installed manually.  

What are the chances that this stuff will be updated and dropped into ubuntu?
No I have 0.8.0 the standard dapper version. Open synaptic and search on ofx. You should find 4 packages. Install them all. If you have them already then you are overlooking the wizard checkbox somehow. Have another close look...

---

### Post by wikki on 2006-07-11
> **kleeman said:**
> No I have 0.8.0 the standard dapper version. Open synaptic and search on ofx. You should find 4 packages. Install them all. If you have them already then you are overlooking the wizard checkbox somehow. Have another close look...

Excellent, I see it now.  Now if I could only find out what the settings for Wachovia are. 

btw thanks for the package kleeman, good work!!

---

### Post by Phred on 2006-07-11
> **spiritraveller said:**
> Here is version 1.9.7 repackaged for Ubuntu from the Debian source package.  Since these are built from official Debian packages, all of the dependencies are defined, and they should be a piece of cake to install with the gui installer.  Either double-click after downloading, or open them directly from firefox.


Just be sure to install gnucash-common first, because gnucash depends on it.

[gnucash-common_1.9.7-1_all.deb](http://www.yourfilelink.com/get.php?fid=116644)
[gnucash_1.9.7-1_i386.deb](http://www.yourfilelink.com/get.php?fid=116643)
[checksums.md5](http://www.yourfilelink.com/get.php?fid=116645)

Oh, by the way, these will replace gnucash 1.8.x if you have it installed.  As they come from Debian, they install into the main system rather than /usr/local.

And if you are unsure about installing something that a stranger gives you on the internet, try building them yourself... you will have to add the Debian Unstable source repository in /etc/apt/sources.list:
```
deb-src http://ftp.us.debian.org/debian/ unstable main
```

And the rest is [not all that difficult](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-sourcepkgs).

Here is version 2.0 repackaged for Ubuntu from the Debian source package :
[gnucash-common_2.0.0-1_all.deb](http://c.chez.fred.free.fr/gnucash-common_2.0.0-1_all.deb)
[gnucash_2.0.0-1_i386.deb](http://c.chez.fred.free.fr/gnucash_2.0.0-1_i386.deb)
[MD5SUM](http://c.chez.fred.free.fr/MD5SUM)

---

### Post by andi5 on 2006-07-11
Thanks Phred! :KS 

Can you provide a gnucash-docs package too? The other in this thread was prefixed /usr/local and so is not available from inside the app (imho).

For a backport the package has to be in edgy, right? But it does not seem to compile due to dependencies, maybe somebody with know-how wants to fix that? [-(

---

### Post by Phred on 2006-07-12
> **andi5 said:**
> Thanks Phred! :KS 

Can you provide a gnucash-docs package too? The other in this thread was prefixed /usr/local and so is not available from inside the app (imho).

For a backport the package has to be in edgy, right? But it does not seem to compile due to dependencies, maybe somebody with know-how wants to fix that? [-(

Here is gnucash-doc repackaged for Ubuntu from the Debian source package :
[gnucash-docs_1.9.0-1_all.deb](http://c.chez.fred.free.fr/gnucash-docs_1.9.0-1_all.deb)

Enjoy :)

---

### Post by rbalfour on 2006-07-18
I have to say. the new version looks sweet.

---

### Post by jknotzke on 2006-07-21
Thanks for the debs..

    Has anyone gotten online banking to work? If so, how ?

    Thanks again

    Justin

---

### Post by sbaron59 on 2006-07-26
Need some additional help

I followed much of this and the other Gnucash 2.0 threads
Thanks for all the help supplied
Ver 2.0 is working mostly but I can not get the online banking menu item to show up in the tools menu
All of the deps seem to be met
Where can I look to find out why this is not functioning ??

---

### Post by kleeman on 2006-07-26
> **sbaron59 said:**
> Need some additional help

I followed much of this and the other Gnucash 2.0 threads
Thanks for all the help supplied
Ver 2.0 is working mostly but I can not get the online banking menu item to show up in the tools menu
All of the deps seem to be met
Where can I look to find out why this is not functioning ??
Fire up synaptic and search for packages with aqbank in them. Install them all. Also search for packages with ofx in them. Install these as well.

---

### Post by sbaron59 on 2006-07-26
Done this already
As I said I have followed the entire thread and others on this.
All deps have been filled.
There must be a scientific way to look at a log file or something to understand what is not working. I just don't know where to look.

---

### Post by kleeman on 2006-07-27
> **sbaron59 said:**
> Done this already
As I said I have followed the entire thread and others on this.
All deps have been filled.
There must be a scientific way to look at a log file or something to understand what is not working. I just don't know where to look.
Beyond my expertise I'm afraid (I only compiled the package). Best thing to do is ask on the users list (gmane.comp.gnome.apps.gnucash.user). I subscribe to this using thunderbird. If you mail to the list you get a return mail to join and then your message appears.

---

### Post by dpm on 2006-07-27
> **sbaron59 said:**
> Need some additional help
[...]
I followed much of this and the other Gnucash 2.0 threads


What kind of protocol is your bank using? OFX or HBCI?

If I'm not mistaken, I think you have to have installed all the *-dev packages for online banking **before** you compile (i.e. rebuild the .deb package) GnuCash 2.0 with online support.

> **sbaron59 said:**
> All of the deps seem to be met
Exactly which dependencies did you install for online banking?

> **sbaron59 said:**
>  Where can I look to find out why this is not functioning ??
You can always ask at the Gnucash mailing list ([https://lists.gnucash.org/mailman/listinfo/gnucash-user](https://lists.gnucash.org/mailman/listinfo/gnucash-user) or [https://lists.gnucash.org/mailman/listinfo/gnucash-devel](https://lists.gnucash.org/mailman/listinfo/gnucash-devel)) or at the aqbanking mailing list ([http://www.aquamaniac.de/aqbanking/](http://www.aquamaniac.de/aqbanking/))

Cheers.

---

### Post by sbaron59 on 2006-07-27
Now I'm confused
The posts on page 9 of this thread indicate that the deb avail on that link have the online banking compiled in ??

---

### Post by dpm on 2006-07-27
> **sbaron59 said:**
> Now I'm confused
The posts on page 9 of this thread indicate that the deb avail on that link have the online banking compiled in ??

You didn't answer any of the questions. Unless you provide some more information, it will be quite difficult to help you. Only you can tell us what you did, we cannot read your mind.

> **sbaron59 said:**
> I followed much of this and the other Gnucash 2.0 threads

What does that mean? Exactly which steps did you follow to install or rebuild the GnuCash package?

---

### Post by sbaron59 on 2006-07-27
I installed this deb with the package installer and verifed all other packages discussed in this entire thread were installed including some I probably didn't need such as DEV types, I did not compile anything


Since the HBCI item is not in the menu I can not perform the balance of the instructions.

Originally Posted by kleeman  View Post
No none. The reason I did this was because the Debian infrastructure is not in place yet so I used checkinstall to generate debs. A better long term solution would be a backport.

For those interested I generated a new deb with ofx import and directconnect capability (i.e. get your data directly from your bank). To set it up you need to do two things which aren't obvious:

1) Launch Tools---> HBCI Setup and on the second page of the wizard launch the aqhbci wizard with the ofx option checked

2) There is a bug in the aqofx package meaning a library is misplaced. To fix do the following

cd /usr/lib

sudo ln -s /usr/lib/aqbanking/plugins/0/providers/aqofxconnect.so.1.0.1 libaqofxconnect.so.0

Works then.

Here is the new deb:

[http://www.yourfilelink.com/get.php?fid=133573](http://www.yourfilelink.com/get.php?fid=133573)

Disclaimer: I take no responsibility for any usage of this software.

---

### Post by kleeman on 2006-07-27
Did you try these debs instead by dolson which have dependencies?

[http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/)

---

### Post by sbaron59 on 2006-07-28
Thanks - these work 
Not sure which made the difference as I reinstalled both.
This set seems good all functions appear to be functioning.

In this dead time though I have been taking a look at MoneyDance.
For the $30 this may be a better deal, This program looks to be better designed and has all required functions.

---

### Post by Silver Streak on 2006-07-28
I just compiled Gnucash on my computer, and I went through the setup thing. Now, however, I'm getting two errors that someone else that posted on the first page also got:
```
<unnamed port>: In procedure scm-error in expression (scm-error (quote misc-error) #f ...):
<unnamed port>: no code for module (g-wrap gw standard)
```

Does anyone know how to fix these errors? They're preventing me from using Gnucash.

SS

---

### Post by andi5 on 2006-07-28
Please take a look at [http://wiki.gnucash.org/wiki/FAQ](http://wiki.gnucash.org/wiki/FAQ)

---

### Post by hdbender on 2006-08-28
Hallo, I'm Heinz-Dieter Bender,
using GC 2.0 on my notebook. 
It is okay there, but when I tried to install it on a brand new PC, I received the message:
< conflicts with installed package gnucash >
When I newly installed Kubuntu Dapper on this PC, it was together with 
GC 1.8.12.
This programm is running, it can also read the data files from the 2.0 version of my notebook, that I stored on an external harddisk.
But installing version 2.0 - automatically using gdebi installer - is not possible.
I'm using an ASRock mainboard and AMD64 cpu.
I placed a second hard disk with WIN 98 installed, but it don't boot, because the mainboard wants WIN 2000 or higher. I need WIN only for printing, because there is a f... Lexmark printer X7170, which don't like any cooperation with linux.
What can I do to solve the problem?
For any help I thank you in advance - hdbender

---

### Post by kleeman on 2006-08-28
Remove the old gnucash packages first

---

### Post by coolcar on 2007-10-11
Hi,

These links take me nowhere ! I was looking to install GNUCash 2.0 on Dapper.

Any Clues ? Thanks

---

### Post by coolcar on 2007-10-11
> **Phred said:**
> Here is gnucash-doc repackaged for Ubuntu from the Debian source package :
[gnucash-docs_1.9.0-1_all.deb](http://c.chez.fred.free.fr/gnucash-docs_1.9.0-1_all.deb)

Enjoy :)

This link takes me nowhere. I was looking to upgrade to GNUCash 2.0 on Dapper. Any clues ?

Thanks !

---

### Post by lhtown on 2007-10-11
You can grab it from getdeb.net

I would suggest uninstalling anything you download from them before you upgrade your system to a new version to avoid any possible problems.

---

### Post by coolcar on 2007-10-11
> **lhtown said:**
> You can grab it from getdeb.net

I would suggest uninstalling anything you download from them before you upgrade your system to a new version to avoid any possible problems.

Hi Looked for GNUCash on [http://www.getdeb.net/search.php?keywords=gnucash]("http://www.getdeb.net/search.php?keywords=gnucash") for "Dapper" and got nothing.

Thanks for the suggestion anyway. I will keep looking.

---

