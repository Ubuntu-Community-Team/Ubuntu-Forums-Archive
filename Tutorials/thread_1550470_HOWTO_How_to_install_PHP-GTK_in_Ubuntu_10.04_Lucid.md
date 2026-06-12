---
title: "HOWTO: How to install PHP-GTK in Ubuntu 10.04 Lucid Lynx"
date: 2010-08-11
forum: Tutorials
---

### Post by bastones on 2010-08-11
[COLOR="Blue"]**Just tested, this works on Ubuntu 10.10 Maverick Meerkat as well.**[/COLOR]

I have had to Google search to be able to install PHP-GTK completely, and I'm going to correlate everything into this how-to here. Hope it helps. 

First, we need to install all the prerequisites to installing PHP-GTK:

```
sudo apt-get install build-essential subversion php5-cli php5-dev libgtk2.0-dev libglade2-dev
```

Then we need to get the Cairo PHP extension (required to install PHP-GTK):

```
cd ~/Downloads
svn co http://svn.php.net/repository/pecl/cairo/trunk pecl-cairo
cd pecl-cairo
phpize
./configure
make
sudo make install
```

Then we need to do the following step in order for the ./buildconf and ./configure commands to work when we're at the stage of installing PHP-GTK, the reason is (according to others), the newer libtool.m4 has been split into different files. To make PHP-GTK ./buildconf and ./configure to work (and subsequently get PHP-GTK installed), we need to concatenate the different files back into the libtool.

```
cd /usr/share/aclocal
sudo cp libtool.m4 libtool.m4~backup
sudo chmod 777 libtool.m4
(start line) sudo cat lt~obsolete.m4 ltoptions.m4 ltsugar.m4 ltversion.m4 >>libtool.m4 (end line)
sudo chmod 644 libtool.m4
```

You're almost there. However, we need to get the latest SVN version of PHP-GTK - if you get PHP-GTK source from PHP-GTK website, you will get an error similar to this:

**error: duplicate ‘static’**

...when running the *make* command. In PHP-GTK 2.0.1, this macro expands simply to “static”. This was because the ZEND_BEGIN_ARG_INFO() macros at the time didn’t mark the variables as static. This was introduced in 5.2.9. So it stands that if you compile PHP-GTK 2.0.1 against PHP 5.2.9 or later, you will get that duplicate static error. In the SVN repoistory, this was fixed. (thanks: [http://devlog.mahcuz.com/2010/08/php-gtk-compile-error-duplicate-static/](http://devlog.mahcuz.com/2010/08/php-gtk-compile-error-duplicate-static/))

To counter this problem, we obviously get the latest SVN version:

```
cd ~/Downloads
svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk
cd php-gtk
./buildconf
./configure
make
sudo make install
```

Once we've done that - we need to do a few more things (although, PHP-GTK is now installed :)).

In Ubuntu 10.04, /etc/php5/cli/conf.d/ and /etc/php5/apache2/conf.d/ are symlinks to /etc/php5/conf.d/, so we need to fix that:

```
sudo rm /etc/php5/cli/conf.d
sudo mkdir /etc/php5/cli/conf.d
sudo cp /etc/php5/conf.d/*.ini /etc/php5/cli/conf.d/

```

Now we need to add the PHP-GTK and Cairo extensions to the php.ini file for PHP to recognise them: run *php-config* and find (near the start) the extension_dir line. It may say something like (or exactly like) this:

```
--extension-dir     [/usr/lib/php5/20090626+lfs]
```

That's where your PHP-GTK and Cairo files are that php.ini need to know about.

To find where your php.ini file is, go to Places -> Computer then select File System from the left. Click Go->Search For Files and search for your php.ini file. You may find two. Open each one and in gedit, look at application title bar and you'll see where the php.ini file is from. If it's in a cli directory, that's the one you need to add the extensions line in. Close it, bring the Terminal window back up and type:

```
sudo gedit /etc/php5/cli/php.ini
```

**(modify to where your php.ini file is, if applicable)**

Press CTRL + F and type Dynamic Extensions, you'll see a list of information about extensions and "commands" but with semi-colons at the start of them - these are comments. Just above where it says "Module Settings" wrapped around semi-colons, add the following;

```
extension=php_gtk2.so
extension=cairo.so
```

This tells PHP what these files are called for PHP-GTK and Cairo within the extension_dir it's already aware of.

Once done, now it's time to test the PHP-GTK installation. Back in Terminal, type: php ~/Downloads/php-gtk/demos/phpgtk2-demo.php and a PHP-GTK application should load up.

If you have any problems, feel free to post. I'm sure someone will help :).

---

### Post by ogilvierothchild on 2010-09-01
This post works perfectly.

Note that if you try "make test", all the tests will fail, however the installed binary works fine on my system.

You can test a bit after the full install by saving the following lines in a file called hello.php then running "php ./hello.php".

> <?php
if (!class_exists('gtk')) {
 die("Please load the php-gtk2 module in your php.ini\r\n");
}

$wnd = new GtkWindow();
$wnd->set_title('Hello world');
$wnd->connect_simple('destroy', array('gtk', 'main_quit'));

$lblHello = new GtkLabel("Just wanted to say\r\n'Hello world!'");
$wnd->add($lblHello);

$wnd->show_all();
Gtk::main();
?>


---

### Post by naripela on 2010-09-20
Thank you very much bastones!!
This post is just perfect!

---

### Post by ubunthor on 2010-09-26
Thank you, bastones, you're a hero. I solely registered in order to tell you this. :D

Tried to run [Phoronix Test Suite]("http://www.phoronix-test-suite.com/") and couldn't get the GUI working because PHP-GTK wasn't installed on my Ubuntu 10.04. The Phoronix site wasn't any help at all, so I was lucky to find your tutorial. I followed it from A to Z and what can I say? Despite my being a Linux n00b, it just worked, as does the Phoronix GUI. Beautiful.

Thanks again.

---

### Post by acovaleda on 2010-09-30
Bastones. It is a very useful tutorial. Thanks to you PHP-GTK is running perfect in my Ubuntu. Last night, I installed PHP-GTK in windows vista. Naturally is easier in Windows.

---

### Post by bastones on 2010-09-30
> **acovaleda said:**
> Bastones. It is a very useful tutorial. Thanks to you PHP-GTK is running perfect in my Ubuntu. Last night, I installed PHP-GTK in windows vista. Naturally is easier in Windows.

It is so much easier to do this via Windows due to the precompiled binaries available for Windows systems, and you can easily just have a command line script that executes the PHP-GTK file under the php_win.exe file and it'll run just like a usual GUI application. On Linux and Mac OS X you could probably do similar but you would have to rely that they have PHP-GTK installed, etc.

I'm glad I have helped you guys and I'm surprised I was even able to figure this all out myself...I'm not too much into the Terminal myself :). However some other guy from the PHP-GTK IRC channel in FreeNode was able to partly help find out the *make* command problem. Unlike some other IRC channels the people in #phpgtk were helpful and courteous :).

I am going to install Ubuntu 10.10 in a virtual machine on my computer and test whether the instructions I have given works line by line. Will update this thread over the next few days :).

---

### Post by cfriisha on 2010-10-03
> **bastones said:**
> It is so much easier to do this via Windows due to the precompiled binaries available for Windows systems, and you can easily just have a command line script that executes the PHP-GTK file under the php_win.exe file and it'll run just like a usual GUI application. On Linux and Mac OS X you could probably do similar but you would have to rely that they have PHP-GTK installed, etc.

Actually I find running the programs even easier in Linux/OS-X as you can just put this as the first line:

#! /usr/bin/php

and set the file executable.

How nice it would be if php-gtk was part of the standard repository for Ubuntu. :)

---

### Post by bastones on 2010-10-04
> **cfriisha said:**
> Actually I find running the programs even easier in Linux/OS-X as you can just put this as the first line:

#! /usr/bin/php

and set the file executable.

How nice it would be if php-gtk was part of the standard repository for Ubuntu. :)

Ah, I actually forgot about that! So I guess it's as easy on Windows and Mac/Linux then :p. I heard you can also archive PHP-GTK programs into PHP PHAR archives but I'm not sure whether they'd run like executables on Linux/Mac (i.e. you double click it and it runs through PHP straight away with no extra work needed).

---

### Post by bastones on 2010-10-06
[COLOR="Blue"][SIZE="3"]Just tested on Ubuntu 10.10, same instructions apply and works on Ubuntu 10.10 Maverick Meerkat :).[/SIZE][/COLOR]

---

### Post by trozamon on 2010-10-17
Bastones, thank you so much.

---

### Post by karaksi on 2010-10-27
hey bastones ,thanks alot this article worked with me greatly ..but as soon as i try to use 
mysql functions its reports an error "Call to undefined function mysql_connect()" 
so i would be grateful if  illustrate how to solve this problem 
Thanks :)

---

### Post by NumPy on 2010-10-28
> **karaksi said:**
> hey bastones ,thanks alot this article worked with me greatly ..but as soon as i try to use 
mysql functions its reports an error "Call to undefined function mysql_connect()" 
so i would be grateful if  illustrate how to solve this problem 
Thanks :)

Hey Karaksi, 
Sounds like you need the mysql.so extension installed. 
Type:

```

sudo apt-get install php5-mysql

```
That will install the library for utilizing mysql functions in PHP.

---

### Post by gotmonkey on 2010-11-06
Thanks! I have been trying to get the gui working for PTS. Your posting made it happen

---

### Post by Bobhuber on 2010-11-24
There is now a simple .deb install file to do all this here >
Make sure you download the correct version for your system (32bit-64bit)
[http://www.phoronix-test-suite.com/misc/php5-gtk-lucid/](http://www.phoronix-test-suite.com/misc/php5-gtk-lucid/)

---

### Post by marrusl on 2010-12-03
The 64-bit deb also seems to work fine on 10.10.

Edit:  Nice find!

---

### Post by cyborgspiders on 2011-03-04
Instructions work perfectly well for Debian 6.0. Very well written. Thank you for your attention to detail.


:popcorn::KS:KS:KS:KS:KS:popcorn:

---

### Post by cyborgspiders on 2011-03-14
Keep up the good work.

---

### Post by olandesevolante on 2011-06-14
Many thanks for having taken the effort to figure this out. I am building my new workstation on 10.10 and php-gtk2 is absolutely essential for me.

For those who'd like some icing on the cake, it is possible to extend php-gtk2 with additional libraries, to wit: [GtkExtra]("http://gtkextra.sourceforge.net/"), GtkSourceview, and [Libsexy]("http://www.chipx86.com/w/index.php/Libsexy").

The latter two can be obtained through Synaptic. Note that you must install the header files too, pick the libraries with the **dev** suffix. GtkSourceview is available in two versions, 1.x is the one you need.

GtkExtra must be compiled from source. This fails however, **make** complains about a function (gtkItemEntry::gtk_entry_reset_im_context()) being declared as static while the same function in the parent class was not, which is something apparently *not done* in C. :-)
My attempted fix was to remove the static keyword from the function declaration/definition in the appropriate source file (gtkitementry.c), which may have introduced a bug but at least it compiles...

For those who want to try for themselves, use version 2.1.2 - the older 2.1.1 version throws a lot more errors.
Untar the source in ~/Downloads (or wherever you find convenient).
```

cd Downloads/gtk+extra-2.1.2
./buildconf
./configure
make
sudo make install

```If **make** does not throw the above mentioned error (might depend on the version of gtk you have) then Bob's your uncle. If it does, one might attempt the above mentioned fix. Note that the offending static keyword must be removed in two locations, once near the top of the file (function declaration) and a second time further down (function definition).

After this little bit of surgery, the library should now compile. I haven't thoroughly tested it however, so I don't guarantee it doesn't introduce some bug. If someone who is more practical with C and the innards of gtk has a more appropriate fix I'd sure be delighted to hear about it.

Having compiled GtkExtra, and installed GtkSourceView and LibSexy with their respective header files, one can now compile php-gtk with these extensions by adding the following flags to **configure**:

```

./configure --with-extra --with-libsexy --with-sourceview

```

Thus the results of a 24-hour crash course in compiling and source code voodoo. One's never too old to learn. Caffeine sure helps though. ;-)

---

### Post by afugit on 2011-06-19
After several hours of trying, reading tutorials, getting into some of the source to find the issues, this worked completely flawlessly on 11.04.  Thanks and cheers!

---

### Post by afhx on 2011-07-17
Many thanks. A first-rate set of instructions.You say you did a google search to piece all this together; I very much  appreciate your efforts.

---

### Post by Somberlain on 2011-08-18
in 11.04 cairo can be installed through pecl
> sudo apt-get install php-pear
sudo pecl install cairo-0.2.0

---

### Post by gastoncs on 2011-09-10
Thank you very much bastones!!
It Was very helpful, I have being trying to install it for a long time..

---

### Post by ytene on 2011-10-18
Bastones ... Passing Gurus...

I hit a snag with with these instructions (running 10.04 AMD64) and, to my complete and utter amazement (I'm a complete numpty) I managed to fix the problem... This is what happened... 

1. Got the packages ... all OK

2. Copy in PECL-CAIRO from Subversion... all OK 
(I saw "Checked out revision 318190")

3. phpize... all OK 
(I saw:-

Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626)

4. ./configure... not OK
First time through I hit an error [Warning] relating to re2c.
I did this:-

sudo apt-get re2c

and the warning went away...

5. ./configure
This now runs through, without apparent error, and with the last 4 lines being:-

configure: creating ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing libtool commands

This seems OK...

6. make... not OK
I get an error message on line 647 of cairo_surface.c (partially truncated at front):-

Downloads/pecl-cairo/cairo_surface.c: In function ‘php_cairo_get_surface_ce’:
Downloads/pecl-cairo/cairo_surface.c:647: error: ‘CAIRO_SURFACE_TYPE_RECORDING’ undeclared (first use in this function)
Downloads/pecl-cairo/cairo_surface.c:647: error: (Each undeclared identifier is reported only once
Downloads/pecl-cairo/cairo_surface.c:647: error: for each function it appears in.)

When I check the relevant section of the source file (cairo_surface.c) I see the following (in part):

==========================================================================
#ifdef CAIRO_HAS_SVG_SURFACE
		case CAIRO_SURFACE_TYPE_SVG:
			type = cairo_ce_cairosvgsurface;
			break;
#endif

**#ifdef CAIRO_HAS_PS_SURFACE**
		case CAIRO_SURFACE_TYPE_PS:
			type = cairo_ce_cairopssurface;
			break;
#endif

**#ifdef CAIRO_HAS_PS_SURFACE**
		case CAIRO_SURFACE_TYPE_RECORDING:
			type = cairo_ce_cairorecordingsurface;
			break;
#endif
==========================================================================

If you look closely at the above source code, you can see that the ifdef statements don't look right... 

Solution:

Copy the offending file (cairo_surface.c) and go to line 646. Change it from this:

#ifdef CAIRO_HAS_PS_SURFACE 

[which you should see appears in the script twice, duh] to this:

#ifdef CAIRO_HAS_RECORDING_SURFACE

Save the file, and re-run the make. It should work OK. I can't promise there won't be more errors ahead, but I thought this might help...

---

### Post by ytene on 2011-10-18
Bastones et al,

Successfully running installation.

Thank you so much for taking the time to write guidance notes that were clear enough even for this numpty to follow...

I did try and look for any clues as to the reason for the error I saw with the Cairo file but didn't find any. I wonder if I was unlucky enough to catch an unstable release? I'll see if I can find somewhere to report what happened...

Cheers!

---

### Post by iduas on 2012-01-16
Thanks to bastones and ytene
I had an erroneous cairo_surface.c:

```
#ifdef CAIRO_HAS_PS_SURFACE
		case CAIRO_SURFACE_TYPE_RECORDING:
			type = cairo_ce_cairorecordingsurface;
			break;
```
instead of

```
#ifdef CAIRO_HAS_RECORDING_SURFACE
		case CAIRO_SURFACE_TYPE_RECORDING:
			type = cairo_ce_cairorecordingsurface;
			break;
```

Will PHP-GTK be included in future releases of ubuntu?

---

### Post by ytene on 2012-06-05
iduas,

I saw exactly the same issue as yours. It turns out that there was an error in the uploaded source versions. I managed to implement the same fix as you identified, so I also filed a bug report, offering up my hack as a work-around. 

I got an email back acknowledging and confirming that the error had been corrected. 

Wish I'd seen your post though!

---

### Post by ytene on 2012-06-05
All, if you're interested in experimenting with PHP-GTK with the latest release (12.04, Precise Pangolin at the time of writing), then you will be pleased to know that bastones original how-to seems to work perfectly.

Just one little point to watch for...

I had already installed Apache2, MySQL and PHP before following the guidelines in this thread. When I got to the point where I was searching for the php.ini file, my system advised me that there were two such files in my environment:-

/etc/php5/cli/php.ini

and

/etc/php5/apache2/php.ini

To make this work, make your ini file edits only to the first of these - i.e. the ini file in the /cli/ folder. Leave the /apache2/ version un-touched. It may be obvious to most, but just in case... you only need to edit the one file.

If you do make an edit to the /apache2/ file by mistake, your first clue to this should be when you can't get a web-based PHP script to work as expected, and in your Apache log files you see PHP related errors...

Check in 

/var/log/apache2/error.log

and look for something like this:-

[Tue Jun 05 13:17:50 2012] [error] [client 127.0.0.1] PHP Fatal error:  php-gtk: Could not open display in Unknown on line 0

The "php-gtk" reference is your hint, and this is likely what you'll see if you edit the wrong file. Back it out and you should see both web and thick client scripts working perfectly.

I hope this helps...

---

### Post by Kamilin on 2012-08-14
[FONT=Palatino Linotype][SIZE=4][COLOR=Red]I just tested this on ubuntu 12.04 works fine :D[/COLOR][/SIZE][/FONT] :guitar:

---

### Post by bastones on 2012-08-17
**You can follow the instructions for Ubuntu 12.04: They work perfectly.**

Hi everyone,

I appreciate the warm response from everyone regarding this howto. I am hoping one day someone is going to develop a binary that makes it easy to install and make use of PHP-GTK applications on Linux distributions, but as of now, Ubuntu does not ship with PHP-GTK because there is not enough support for it nor considering the constraints of the size of a standard CD would it be considered "essential" or "important".

Speaking of the installation steps I posted here a few years ago, the same steps work perfectly in Ubuntu 12.04 - I have tested this myself. Although certain steps are not necessary it seems, and I wanted to make the howto much cleaner, and I can't modify the original post anymore - so I've posted the howto here: [How to install PHP-GTK on Ubuntu 12.04 / in Debian?]("http://forums.eukhost.com/f15/how-install-php-gtk-ubuntu-12-04-debian-17378/") with better explanations and easier to follow instructions. Either way, both instructions give the same end result - a working installation of PHP-GTK :).

Hope this helps.

---

### Post by steveray100 on 2012-08-27
and search for your php.ini file. You may find two. Open each one and in  gedit, look at application title bar and you'll see where the php.ini  file is from. If it's in a cli directory, that's the one you need to add  the extensions line in.

if I understand this correctly,which I probably don't, I am supposed to add this line to the php.ini file?

--extension-dir     [/usr/lib/php5/20090626+lfs]

and if so do I just copy and paste?
 Help! I'm kinda over my head here.

wait, is this correct?:

this is in the php.ini file:
**************************

; Directory in which the loadable extensions (modules) reside.
; [http://php.net/extension-dir](http://php.net/extension-dir)
; extension_dir = "./"
; On windows:
; extension_dir = "ext"

so I  should uncomment the line "extension_dir"  and add the path? 
extension_dir ="./usr/lib/php5/20090626+lfs"

NEVER MIND !  I figured it out!  Solution: no need to do anything with "extension_dir" listing in Php.ini file.
I want to thank bastone for the most LUCID directions/tutorial I think I've ever come accross for something so complicated for a newbie like me!

---

### Post by grandsatrap on 2012-09-22
I can't get it to work. I followed all of the instructions (on Ubuntu 10.04) but it fails here. Please help.

**Error in ./configure in php-gtk**

```
/home/griffin/php-gtk>./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... gawk
checking for PHP-GTK support... yes, shared
checking for PHP executable... found version 5.3.2-1ubuntu4.18
checking for gawk... (cached) gawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.24.1)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.20.1)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -pthread -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for cairo >= 1.4.0... yes
checking CAIRO_CFLAGS... -D_REENTRANT -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12  
checking CAIRO_LIBS... -lcairo  
checking for cairo php extension... yes
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... yes
checking LIBGLADE_CFLAGS... -pthread -D_REENTRANT -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -pthread -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
creating main/php_gtk_ext.c
./configure: line 12049: LTOPTIONS_VERSION: command not found
./configure: line 12050: LTSUGAR_VERSION: command not found
./configure: line 12051: LTVERSION_VERSION: command not found
./configure: line 12052: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12127: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12127: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'
/home/griffin/php-gtk>make
make: *** No targets specified and no makefile found.  Stop.
/home/griffin/php-gtk>

```

---

### Post by ubungus on 2012-11-19
bastones you are a legend....if they gave out Nobel prizes for Ubuntu...you'd get my vote for one...

You just saved me a load of time....

---

