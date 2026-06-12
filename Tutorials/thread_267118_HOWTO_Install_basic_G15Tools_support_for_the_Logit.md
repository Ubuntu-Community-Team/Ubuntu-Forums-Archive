---
title: "HOWTO: Install basic G15Tools support for the Logitech G15"
date: 2006-09-28
forum: Tutorials
---

### Post by drdnl on 2006-09-28
**[SIZE="5"]Major Edit:[/SIZE]**

[COLOR="Red"][SIZE="6"]I haven't really had time to update this thread to reflect more recent changes. Don't follow the instructions below as they are practically ancient. See [here]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285") for the latest installation tips and debs(FEISTY)[/SIZE]
[/COLOR]

















































please scroll down for information on getting amaroK to play nice with the g15 lcd.

My turn to do something back for this community, stuff tagged with * are optional steps possibly required to get this running (most likely they are on 6.06 Dapper)

First off, install libusb-dev* and libdaemon-dev using Synaptic or the terminal

```
sudo apt-get install libusb-dev libdaemon-dev
```

(*I had some kind of weird dependancy problem with xsane and ubuntu desktop with libusb-dev, simply do a search for "libusb-dev debian" and download/install, you'll know it works when it warns you about an older version in the repos)

Then, download the attachment and install libg15, g15daemon, libg15render and g15composer_1.0.1 (in that order)

```
**Edit:** If you want to run the latest version of G15composer (which handles it own pipe) you can get them [here]("http://www.ubuntuforums.org/showpost.php?p=1637309&postcount=62")

It should be mostly backwards compatible except for the aforementioned pipe handling, remove any mention of (for example) mknod $pipe p from any script you wish to run. In addition, any pipes left behind by other scripts should be removed or it will complain.
```

next, try running g15daemon

if properly installed it will probably complain:

```
g15daemon: error while loading shared libraries: libg15.so.1: cannot open shared object file: No such file or directory
```

to solve that run:

```
sudo gedit /etc/ld.so.conf
``` and insert ```
/usr/local/lib
``` at the top of the file. Now run ```
sudo ldconfig
```

Now lets see if it'll work:

```
sudo g15daemon
```

If you now have a gigantic clock showing on your lcd, CONGRATULATIONS!

Of course, many, many thanks to all the developers at [http://g15tools.sourceforge.net/](http://g15tools.sourceforge.net/) !

I'll be updating this post as I discover more functions, of course all help is greatly appreciated.

Edit:

If you want to have the demon autorun on startup try running (BE CAREFUL) ```
sudo visudo
``` Change the user part and add the following to the end of the file: ```
[COLOR="Red"]user[/COLOR] ALL= NOPASSWD: /usr/local/sbin/g15daemon . *If you use the packages posted later on in this thread it'll be /usr/sbin/g15daemon
``` and press ctrl+x to exit. Press Y to accept, it will check for syntax mistakes and if it finds one it will ask you "What now?" Simply press E and make the necessary changes.

After this go to System->Preferences->Sessions and add sudo g15daemon to the list

Next, getting some useful data on the screen. To get you all started try typing

```
echo 'TL "Hello" "World"' > ~/g15lcd
g15composer ~/g15lcd
```

Now please SOMEONE, make a decent amarok script with an analizer, track info and progress bar so we have a linux alternative for g15plugin for winamp in windows. :)

Hope this helps someone,
D

[SIZE="3"]Amarok and the Logitech G15[/SIZE]

This is surprisingly easy these days after some efforts from guitoo and Anuerysm9 plus the tiniest bit of packing effort on my end. Provided the lcd is fully functioning with a running clock you can download the following scripts:

[amarok-g15-dcop_cli.ubuntu.amarokscript.tar.gz]("http://www.ubuntuforums.org/attachment.php?attachmentid=17192&stc=1&d=1160410939")

This is Aneurysm9's script, it is a modified version of his original script designed to run without dependancies. It displays artist name plus song info and a wonderful song progress bar. If you are using ubuntu (very likely) make sure to get this version. The change made is adding the word "truetype" in the font location. The original can be found attached to this post below.

or 

[GentooG15Amarok(fixed).amarokscript.tar.gz]("http://www.ubuntuforums.org/attachment.php?attachmentid=17191&stc=1&d=1160410498")

Another no dependancy script made by guitoo, simpler than Aneurysm9's but very reliable , simple and easy on the eyes. Gives a little more track info in the form of track number and album.

Download either script and install it into amarok by opening amarok -> tools -> script manager. Select the option install script, point it to the downloaded *.amarokscript.tar.gz and select ok. It should return a "script installed ok" after which you select the script in the list and press "run". G15Composer should show up and a few moments later (sometimes it takes a track change) the song info should pop up. As long as you leave the script running within amarok/script manager it will automatically turn on and off along with the player itself.

On a sidenote, aneurysm9's original scipt can be found on the next page of this post. It is supposedly more cpu efficient but I have never been able to resolve its dependancies so I cannot offer any advice on installation.

Enjoy!

[SIZE="4"]**Troubleshooting:**[/SIZE] 

If you run sudo G15Deamon and it complains about a return value make sure to run ```
modprobe uinput
``` 
People who previously installed G15Lcd will not have this problem.

[SIZE="4"]**Big Edit**[/SIZE]

Turns out I made a mistake and should have been clearer about creating a pipe, not a file, to read data from.

> **Aneurysm9 said:**
> Will everyone who is seeing g15composer eating 100% of their cycles please ensure that they are telling g15composer to read from a pipe and not a regular file.  You can create a pipe with "mknod /path/to/pipe p" (replacing /path/to/pipe with whatever you really want, I use /var/run/lcdpipe) and run g15composer with "g15composer /path/to/pipe".  If you tell it to read from a regular file it will simply read the file over and over again, eating all of your cycles because there's always something for it to read.  With a pipe there's only something to read when you put something there so most of the time it's waiting for something to do.

---

### Post by subpar on 2006-09-29
I followed the instructions to the t, and I got the following error when I tried to run g15daemon.

```
subpar@gargamel:~/tmp$ sudo g15daemon
Something went wrong. Couldnt get return value from daemon process

```

Also, /etc/lib.so.conf was completely empty when I edited it, but it didn't give me that error until I changed the contents. Any clues on what I did wrong/what's going on?

---

### Post by drdnl on 2006-09-29
Hi, /etc/lib.so.conf is empty when you edit it, did you run sudo ldconfig afterwards? check the .conf for any (spelling) errors. I assume G15Daemon gave the library related error before you edited the .conf and afterwards this new one regarding return values. I've had that return value error but it came with not running sudo... What kind of system are you running?

Edit: umm, /etc/lib.so.conf? hope you meant /etc/ld.so.conf :)

Edit: Dont forget to run (sudo?) ```
modprobe uinput
```

---

### Post by subpar on 2006-09-29
Double checked everything (yes, I even checked to make sure I edited ld.so.conf instead), and this is everything I tried:

```
subpar@gargamel:~$ sudo g15daemon
Something went wrong. Couldnt get return value from daemon process
subpar@gargamel:~$ modprobe uinput
FATAL: Error inserting uinput (/lib/modules/2.6.15-27-386/kernel/drivers/input/misc/uinput.ko): Operation not permitted
subpar@gargamel:~$ sudo modprobe uinput
subpar@gargamel:~$

```

I'm running i386, and if you need actual hardware specs, they can be found [here]("https://secure.newegg.com/NewVersion/WishList/MySavedWishDetail.asp?ID=3670283").

---

### Post by drdnl on 2006-09-29
try running sudo g15daemon again after having run sudo modprobe uinput

---

### Post by aqwabawks on 2006-09-30
Well, I managed to get it to work, it displays a clock at the moment, but I was wondering, how would I go about binding say the Play/Forward/Rewind/Stop keys to say an application like Amarok?

---

### Post by drdnl on 2006-09-30
You dont need the daemon to do so, simply go into system->preferences->keyboard shortcuts and amarok->settings->global shortcuts and fiddle with them till it works. It takes a little trial and error but as a hint: in gnome settings my stop key has a value of 0x04 and in Amarok it has a value of XF86Audiostop

Actually, these keys working where a major factor in my switch to linux, I was willing to not have an lcd for a while (this is 4 months ago) but I wanted at least the mediakeys, its not a cheap keyboard after all.

So again, just fiddle with it, if you get any feedback from pressing the buttons in gnome settings that means you're close to getting it to work.

---

### Post by Thunderstriker on 2006-09-30
i managed to install it but it should support libgraphlcd does anyone know how to get this working?

---

### Post by Dawnrazor on 2006-10-01
Great, now we need something for the G-Keys :)

---

### Post by drdnl on 2006-10-01
The G-Keys are working just fine, try setting one in keyboard shortcuts. There's a slight bug though, it doesnt capture all keypresses (yet) so you have to hold it for a moment longer than a simple keypress. But I'm pretty sure you can't record G-Keys yet.

---

### Post by drdnl on 2006-10-01
My turn to ask a question :), does anyone else here have 100% cpu usage when running g15composer listening to a pipe? (g15composer ~/g15lcd for example). I'd like to start trying out programming for amarok but I dont want to run software that uses up that amount of resources. I'm guessing maybe the polling interval is set too high? Any solutions would be greatly appreciated.

---

### Post by Thunderstriker on 2006-10-01
yeah my cpu goes up to 90% to

---

### Post by bstock on 2006-10-01
I have a dual-core, and 1 of my cores spikes to full CPU usage. I would guess the program is running some kind of loop to output to the LCD, but I haven't looked at the code or anything. It would be cool to see some better outputs for this, as it could be very useful when used in the proper applications.

---

### Post by Aneurysm9 on 2006-10-02
Hello,

I'm one of the g15tools developers, so hopefully I can answer some questions.  I have working packages built for Dapper and the package structure is in the svn repository so future versions will have the debian directory in the tarball.  Unfortunately, I don't have hosting space for them and I don't want to clutter up the sourceforge files page with packages for every distro.  If anyone has hosting space and would be willing to set up a repository for them, or add them to an existing repo, that would be greatly appreciated.  They're attached, though without the source .gz files as that would put the attachment over the forum's limit.  If someone wants to put them in a repo, let me know and I'll send the sources as well.

I've also attached an Amarok script that I've been working on that uses g15composer.  It's not the greatest, but it displays artist and track info as well as a progress bar and time info.  You may need to edit it and change the location of $PIPE if you use something other than /var/run/lcdpipe.  

As for processor usage, I'm not seeing that here, but I'm running Gentoo on this machine.  I'll bring the G15 down to one of the Dapper boxes tonight or tomorrow and see if I can reproduce the problem.

WRT recording and playing back G-key macros, it's not yet possible but should be fairly simple to implement as a G15daemon client if anyone is so inclined.

Edit:

With the Amarok script, you may also need to change the font that is loaded if it's in a different location or not available, or if you just want a different font. You'll also need DCOP::Amarok::Player installed.

I have found that starting Amarok with the script running but no media playing causes g15composer to start chewing processor cycles.  My guess would be that it's because some of the fields aren't populated and g15composer is choking on one of the commands that doesn't have all the arguments it should.  I'll look into that some more.

Edit 2:
Ok, the problem was lack of data in some fields.  I've worked around it in the script, but I'll look into making sure that g15composer checks for complete data as well as this could be what's causing problems for some of you.  The new script is attached and should work.

Edit 3:

We've tracked down the problem with g15composer using all available cycles.  Please ensure that you're telling g15composer to read from a pipe and not a regular file.  You can make a new pipe with "mknod lcdpipe p".  That will give you a pipe called "lcdpipe" in the current directory.  Then run "g15composer lcdpipe" and you can then give it commands such as "echo 'TL "this is a test"' > lcdpipe" and it will output to the LCD.

---

### Post by Aneurysm9 on 2006-10-02
> **Thunderstriker said:**
> i managed to install it but it should support libgraphlcd does anyone know how to get this working?

You will need to apply the patch to graphlcd 1.3 from the g15daemon tarball and rebuild graphlcd or use graphlcd-svn where the patch is already applied.

---

### Post by drdnl on 2006-10-03
Aneurysm9, thank you very much for all the work so far. I'll be trying out the packages and the script when i get back later today. Hopefully the cpu bug will be squashed soon,

Regards,
D

---

### Post by drdnl on 2006-10-03
Congratulations Aneurysm9, you have the distinction of creating the hardest script I've ever had to install :) Nonetheless I'm still grateful, even with my very limited coding abilities I can see that it should be quite a nice script once up and running.

At the moment my problem is not being able to install DCOP::Amarok::Player properly, I had to fix some earlier dependancy problems but this last one eludes me:

```
make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/1....ok 2/89ERROR: Multiple available KDE sessions!
Please specify the correct session to use with --session or use the
--all-sessions option to broadcast to all sessions.
t/1....NOK 4
#     Failed test (t/1.t at line 14)
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.
ERROR: Multiple available KDE sessions!
Please specify the correct session to use with --session or use the
--all-sessions option to broadcast to all sessions.
t/1....NOK 5
#     Failed test (t/1.t at line 16)
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.
# Looks like you planned 89 tests but only ran 85.
t/1....dubious
        Test returned status 6 (wstat 1536, 0x600)
DIED. FAILED tests 4-5, 86-89
        Failed 6/89 tests, 93.26% okay
Failed Test Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1.t          6  1536    89   10  11.24%  4-5 86-89
 (55 subtests UNEXPECTEDLY SUCCEEDED).
Failed 1/1 test scripts, 0.00% okay. 6/89 subtests failed, 93.26% okay.
make: *** [test_dynamic] Error 6
daniel@ubuntu:~/DCOP-Amarok-Player-0.036$
```

I'm running XGL/Compix on ubuntu dapper 6.06 (Gnome), I tried make test --all-sessions but that didn't work. With some hackish fumbling i managed to install dcop player but of course if it didnt pass the tests its not going to work, this is the output from your script:

```
ERROR: Multiple available KDE sessions!
Please specify the correct session to use with --session or use the
--all-sessions option to broadcast to all sessions.
```

On a sidenote, is DCOP::Amarok::Player necessary? this [old script]("http://www.aaue.dk/~janoc/personal/linux/soft/g15amarok.pl") for g15lcd manages without (but is of course much simpler).

-D

Edit: In the hope that maybe I just made a stupid mistake I installed the script directly into Amarok after I realized that that might be what I had to do. Unfortunately it complains about the same "which session?" stuff.

---

### Post by Nappateemu on 2006-10-03
How to install XMMS plug-in for Ubuntu and G15Daemon?
I found the sources from sourceforge, but after installing g15tools from .deb files they don't seem to work...

---

### Post by Aneurysm9 on 2006-10-03
> **Nappateemu said:**
> How to install XMMS plug-in for Ubuntu and G15Daemon?
I found the sources from sourceforge, but after installing g15tools from .deb files they don't seem to work...

The XMMS plugin isn't handled by the Makefile from g15daemon, you need to first install g15daemon (including libg15daemon-client-dev if you're using the debs) and then build the XMMS plugin from the source.

---

### Post by Aneurysm9 on 2006-10-03
drdnl,

If you want, you can remove the dependency on DCOP::Amarok::Player, but I would expect that it then would be more resource intensive as you would need to use the cli dcop client, starting a new session for each bit of data you want and perhaps parsing some of the results.  Usage dropped for me from 7% down to about 3% after switcing to DCOP::Amarok::Player rather than the cli dcop client.

If you want to do it, that script that you linked should provide guidance, just replace the $amarok->(etc) lines with calls to the cli dcop client.

---

### Post by Nappateemu on 2006-10-03
> **Aneurysm9 said:**
> The XMMS plugin isn't handled by the Makefile from g15daemon, you need to first install g15daemon (including libg15daemon-client-dev if you're using the debs) and then build the XMMS plugin from the source.
Ok... I think I'm just going to stick with Amarok. I didn't quite understand the Amarok plug-in installation either, any help? :oops:

---

### Post by Aneurysm9 on 2006-10-03
> **Nappateemu said:**
> Ok... I think I'm just going to stick with Amarok. I didn't quite understand the Amarok plug-in installation either, any help? :oops:

First you'll need to install DCOP::Amarok::Player, which you can get with cpan or by downloading the sources for DCOP, DCOP::Amarok, and DCOP::Amarok::Player and installing them in order.  Then you install the script from the Amarok script manager, just point it to the tarball that I attached to an earlier post.  If you don't have g15composer reading from /var/run/lcdpipe, right click on the script in the script manager and select edit and change the location of $PIPE to wherever g15composer is reading from.  Change the font as well if you need to, I think it may be in a different location on Breezy, that script was written on a Gentoo system.  Then start the script from the script manager and you're good to go.

Edit:

The font is indeed in a different location, add /truetype/ after /usr/share/fonts and before ttf-bitstream....

---

### Post by Aneurysm9 on 2006-10-03
I can't seem to get g15composer to chew cycles simply by starting it up on Breezy.  Have those of you seeing that problem tried the packages I posted last night?  If so, are all of you using AMD64?  I don't have and AMD64 install to test with, sorry.  Perhaps if one of you has some debugging experience you can try to trace it out with profiling or valgrind.

---

### Post by Thunderstriker on 2006-10-03
thx for all the info i'm running amarok on gnome dont supose the scipt can work on gnome ?

---

### Post by Aneurysm9 on 2006-10-03
> **Thunderstriker said:**
> thx for all the info i'm running amarok on gnome dont supose the scipt can work on gnome ?

Yup, works fine.  I'm running Amarok on Gnome myself.

---

### Post by Thunderstriker on 2006-10-03
damn than i do something wrong i DCOP make test did work DCOP::Amarok butt the DCOP::Amarok::Player gave error

#     Failed test (t/1.t at line 14)
#          got: ''
#     expected: '0'
t/1....NOK 4# *** Amarok needs to be open.

#     Failed test (t/1.t at line 16)
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.

when i run the script is just starts with no errors but there notting on the display

---

### Post by Aneurysm9 on 2006-10-03
> **Thunderstriker said:**
> damn than i do something wrong i DCOP make test did work DCOP::Amarok butt the DCOP::Amarok::Player gave error

#     Failed test (t/1.t at line 14)
#          got: ''
#     expected: '0'
t/1....NOK 4# *** Amarok needs to be open.

#     Failed test (t/1.t at line 16)
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.

when i run the script is just starts with no errors but there notting on the display

I got the same when I tried to install it on Breezy, even with Amarok running.  I didn't get that on Gentoo.  On Breezy, I just skipped the make test portion and it worked fine.  There won't by any display if DCOP::Amarok::Player isn't installed because it won't have any data (though it probably should error in that case)  Did you point $PIPE to the pipe on your system that g15composer is reading from?  Did you update the font path, if not you'll only get the progress bar and time info.

---

### Post by OnoA on 2006-10-04
Hello gents!

First of all, let me say Thank you so much for all the work you put into this  :)

Aneurysm9, I tried to install your .debs and the amarok script.
It seems to be running all right (no error messages anywhere ;))
but all I get on the lcd is rubbish.

The total time displayed is right, but the "time into the song" keeps on changing about 10 times per second, sometimes displaying the right value, most of the time it doesn't.
Same goes for the bar. And I do not have a "artist" or "title" displayed at all :( ](*,) 

----
I had the g15tooles installed from source, before using your debs. Could that be part of the problem?

I also had to "force install CPAN::Amarok::Player" but it looks like that is working fine...

Any ideas, what could be wrong?


By the way, my cpu load goes up to 70-90% too, when running g15composer.


Thanks!

Philipp

---

### Post by Nappateemu on 2006-10-04
Ok, now that the LCD is working, how do I use the G-buttons.
Someone could tell me step-by-step how to program for example so, that when I press G13 it writes "Hello everybody".

And another matter, are the next/previous/pause... buttons usable with g15tools?

---

### Post by Aneurysm9 on 2006-10-04
OnoA, 

That should not be possible.  The progress info is handled in a separate thread that sleeps for one second after every update.  It shouldn't be able to change more than once per second.  As for artist and title, you will need to change the path to the font that's loaded somewhere near the top to reflect a font available on your system.  You should have the bitstream fonts installed as I think they're part of the base install.  The script was written on a Gentoo system, however, so you will need to add "/truetype/" before "ttf-bitstream" in the font path.

I'm still not sure what's causing the cpu usage problems.  Can you give me some more info about your system?  Are you using an AMD64 or i386 install?  

Nappateemu,

Good to hear that you have the LCD working.  Currently, there is not a g15daemon client that allows recording and playing back macros like the windoze software does.  It should be fairly trivial to do so, should someone be so inclined, but so far nobody has coded one.

As for the media keys, they should be usable with or without g15daemon.  Try the gnome keyboard settings applet or the counterpart if you're using KDE.

---

### Post by drdnl on 2006-10-04
Aneurysm9, is there any way to "dumb down" the current Amarok script to make it more accessible to ex-windoze users? I've gotten pretty good at figuring out linux but sometimes a simple binary would be nice. The clock currently built into g15 daemon works great, could similar Amarok support be built into it? It would be fantastic to simply load up G15Daemon and have automatic Amarok support. It would probably also reduce the cpu/mem overhead.

If none of this dumbing down or building in is possible could you maybe release a second script with no dependancies? Sorry to have to ask but I'm really lost with Perl.

Either way, thank you for the help.

(and yes, I also run an AMD64 single core in case I had forgotten to mention that. Oh, and I'm running your debs, so it cant be a faulty checkinstall)

---

### Post by Aneurysm9 on 2006-10-04
Unfortunately, there's not much that can be done to make the current script simpler.  The only thing that could be done would be to use the cli DCOP client and remove the dependence on DCOP::Amarok::Player, but that would increase CPU overhead, not decrease it.  The support can't really be built into g15daemon because of the way Amarok scripts work, nor would I want to as we want to keep a clean separation of the daemon and the clients.  The clock is only there to let you know that it's working.  I've been thinking about rewriting the script as a C++ program to use DCOP natively, but that will take a while as I've never used DCOP with C++.

I'm thinking that maybe there's a problem with AMD64 systems because of int size mismatches.  I'll look into it but there's not a lot I can do as I don't have an AMD64 system myself.  If that is the problem, it will also require rewriting the entire g15tools chain, so it will take a while to fix.

---

### Post by Noneus on 2006-10-05
Does anyone know howto use the G buttons in KDE? In GNOME I could bind them. But I don't use GNOME. Any thoughts?

---

### Post by drdnl on 2006-10-05
Aneurysm9, good to hear you're thinking of solutions. If you'd like we could set up a day where you log into my machine with nxclient and do some debugging if possible (non-admin/root of course). This should make it possible for you to "have" an AMD64. PM me if you're interested.

Either way I'm looking forward to watching the developments unfold,

And Noneus, no idea, sorry (Gnome user)

---

### Post by Aneurysm9 on 2006-10-05
I've been talking with some people testing on Gentoo where ebuilds for the g15tools have just made it into the portage tree and they tell me that there are no problems with AMD64 systems on their end.  It may be something that is only exposed on Ubuntu, or systems other than Gentoo, such as the malloc issue was with g15composer.  If drdnl gets me access to his box I'll see what I can do to figure out where the problem is.

drdnl, 

I forgot to mention in the PM that I would also like to have screen installed if you don't have it already, it's a lifesaver when working on remote machines (or locally for that matter).

---

### Post by drdnl on 2006-10-06
Aneurysm9,
turns out ubuntu does no notification of pm's so you must have missed mine (I know i missed yours until i noticed the forum message last night). Check your pm's :)

-D

---

### Post by Aneurysm9 on 2006-10-06
Will everyone who is seeing g15composer eating 100% of their cycles please ensure that they are telling g15composer to read from a pipe and not a regular file.  You can create a pipe with "mknod /path/to/pipe p" (replacing /path/to/pipe with whatever you really want, I use /var/run/lcdpipe) and run g15composer with "g15composer /path/to/pipe".  If you tell it to read from a regular file it will simply read the file over and over again, eating all of your cycles because there's always something for it to read.  With a pipe there's only something to read when you put something there so most of the time it's waiting for something to do.

---

### Post by Aneurysm9 on 2006-10-07
I have released an new version of g15composer, 1.1, that prevents the problem seen here where g15composer will eat all of your CPU cycles if told to read from a regular file.  It will now exit if it is not reading from a named pipe.  This release also enables control of the LCD contrast and brightness as well as the M1-M3 LEDs.  Attached is a .deb for Dapper and I'm going to build an Edgy VM right now to build Edgy packages.

---

### Post by Aneurysm9 on 2006-10-07
Here are the packages for Edgy.

---

### Post by drdnl on 2006-10-08
Packages for Edgy seem to be running but I can no longer get this script to run:

Edit: solved

```
#!/bin/sh
BASEDIR="${HOME}/.kde/share/apps/amarok/scripts-data"
PIPE=${BASEDIR}/pipe
EXEC=${BASEDIR}/

size()
{
    if [ $1 -gt 32 ]; then
   SIZE=S
    else
   if [ $1 -gt 20 ]; then
       SIZE=M
   else
       SIZE=L
   fi
    fi
}

terminate()
{
    rm $PIPE
    kill -9 $PID
    exit 0
}

mknod $PIPE p
g15composer $PIPE &
PID=$!

trap terminate 1 2 5 15

while [ 1 ]
do
read input
if [ "$input" == "trackChange" ];then
    echo "MC 1" > $PIPE
   
    ARTIST="`dcop amarok player artist`"
    size ${#ARTIST}
    echo "TO 0 0 $SIZE 1 \"$ARTIST\"" > $PIPE
   
    TITLE="`dcop amarok player title`"
    size ${#TITLE}
    echo "TO 0 18 $SIZE 1 \"$TITLE\"" > $PIPE
       
    ALBUM="`dcop amarok player album`"
    TRACK="`dcop amarok player track`"
    ALBTRA="($ALBUM - $TRACK)"
    size ${#ALBTRA}
    echo "TO 0 35 $SIZE 1 \"$ALBTRA\"" > $PIPE
   
    echo "MC 0" > $PIPE
    #out="$ARTIST\" \ \"$TITLE\" \ \"($ALBUM - $TRACK)"
    #echo "TO 0 0 M 1 \"$out\"" > $PIPE
fi
done
```

It complains about "[: 56: ==: unexpected operator
[: 56: ==: unexpected operator", anyone?

There's good news though, for those dapper users the attached .tar.gz should work just fine without dependancies. Just download the file to your desktop, open amarok, tools -> script manager -> install script, point it to your desktop and double click the script. Now just select it from the list and press Run. The nice thing about it is that it opens a g15composer and pipe and closes it when done.

Edit: Seems that the script had a "=" to many, if you have the same problem I had simply download and install the fixed script.
Edit: And of coure, full credit for these scripts go to guitoo who wrote them for this [thread]("http://forums.gentoo.org//viewtopic-t-490492-postdays-0-postorder-asc-start-0.html")

---

### Post by OnoA on 2006-10-08
> **Aneurysm9 said:**
> 
That should not be possible.  The progress info is handled in a separate thread that sleeps for one second after every update. It shouldn't be able to change more than once per second.


That's right, I tailed the pipefile, and your script writes in there about once per second. Still, The lcd updates more often.

> **Aneurysm9 said:**
> 
  As for artist and title, you will need to change the path to the font that's loaded somewhere near the top to reflect a font available on your system.  You should have the bitstream fonts installed as I think they're part of the base install.  The script was written on a Gentoo system, however, so you will need to add "/truetype/" before "ttf-bitstream" in the font path.


Been there, done that ;-) I adjusted the path to Vera at the very beginning, so that does not seem to be the problem, or, at least not the path.

> **Aneurysm9 said:**
> 
I'm still not sure what's causing the cpu usage problems.  Can you give me some more info about your system?  Are you using an AMD64 or i386 install?  

i386, Kubuntu 6.06, What else do you wanna know? 

cheers,
Philipp

---

### Post by Aneurysm9 on 2006-10-08
Onoa,

Can you try g15composer-1.1?  It sounds like maybe you're having it loop over a regular file.

---

### Post by OnoA on 2006-10-08
Solved it! I'm stupid ;-)

Thanks!

---

### Post by rbu on 2006-10-08
Hi Aneurysm9,

what do you think about packaging the amarok-g15-perl.pl together with the actual application? By that, you would
1) have it under version control
2) ease installation for most users (it could by default be installed into /usr/share/g15composer/examples or contrib)

One would also have a central point for neat scripts to use it, I've seen a few of them around the Gentoo Forums, too.

--robert

---

### Post by Aneurysm9 on 2006-10-08
I've added the amarok scripts to g15composer-svn.  I've also converted my script to use the CLI dcop client so people who can't get DCOP::Amarok::Player working can still use it.  Here's the converted script:

```
#!/usr/bin/perl -w

use strict;
use threads;
use threads::shared;

my $pipe = "$ENV{HOME}/.g15amaroklcdpipe";

my $mknod = system("mknod $pipe p");

my $G15Cpid : shared = open(G15COMPOSER, "| g15composer $pipe");

my $vol : shared = `dcop amarok player getVolume`;
chomp $vol;
my $tmpStatus = `dcop amarok player status`;
chomp $tmpStatus;
my $status  :  shared = ( $tmpStatus > 1 ) ? 1 : 0;

open(PIPE, ">>$pipe");
print PIPE "FL 0 10 \"/usr/share/fonts/ttf-bitstream-vera/Vera.ttf\"\n";

sub volUpdate {
        print PIPE "PC 0\n";
        print PIPE "TO 0 10 2 1 \"Volume\"\n";
        print PIPE "DB 3 27 157 35 2 $vol 100 3\n";
}

while($status == 0) {
        $tmpStatus = `dcop amarok player status`;
        $status = ( $tmpStatus > 1 ) ? 1 : 0;
        sleep 1;
}

my $artist : shared = `dcop amarok player artist`;
my $title : shared = `dcop amarok player title`;
my $album : shared = `dcop amarok player album`;
my $trackTotalSecs : shared = `dcop amarok player trackTotalTime`;
my $trackCurSecs : shared = `dcop amarok player trackCurrentTime`;
my $trackTotalTime : shared = `dcop amarok player totalTime`;
my $trackCurTime : shared = `dcop amarok player currentTime`;
chomp $artist;
chomp $title;
chomp $album;
chomp $trackTotalSecs;
chomp $trackCurSecs;
chomp $trackTotalTime;
chomp $trackCurTime;

&initScreen();

$SIG{TERM} = \&bye;

my $progressThread = threads->create(\&progress);
$progressThread->detach();

while(1) {
        $_ = <STDIN>;
        chomp $_;
        if ( /trackChange/ ) {
                $artist = `dcop amarok player artist`;
                $title = `dcop amarok player title`;
                $album = `dcop amarok player album`;
                $trackTotalSecs = `dcop amarok player trackTotalTime`;
                $trackTotalTime = `dcop amarok player totalTime`;
                $trackCurSecs = `dcop amarok player trackCurrentTime`;
                $trackCurTime = `dcop amarok player currentTime`;
                chomp $artist;
                chomp $title;
                chomp $album;
                chomp $trackTotalSecs;
                chomp $trackCurSecs;
                chomp $trackTotalTime;
                chomp $trackCurTime;
                initScreen();
                $artist = `dcop amarok player artist`;
                $title = `dcop amarok player title`;
                $album = `dcop amarok player album`;
                $trackTotalSecs = `dcop amarok player trackTotalTime`;
                $trackTotalTime = `dcop amarok player totalTime`;
                $trackCurSecs = `dcop amarok player trackCurrentTime`;
                $trackCurTime = `dcop amarok player currentTime`;
                chomp $artist;
                chomp $title;
                chomp $album;
                chomp $trackTotalSecs;
                chomp $trackCurSecs;
                chomp $trackTotalTime;
                chomp $trackCurTime;
                initScreen();
        } elsif ( /engineStateChange/ ) {
                if( /playing/ ) {
                        $status = 1;
                        initScreen();
                } elsif ( /pause/ ) {
                        $status = 0;
                } else {
                        $status = 0;
                }
        } elsif( /volumeChange/ ){
                m/: (\d+)/;
                $vol = $1;
                $status = 0;
                &volUpdate();
                $status = 1;
        }
        exit if( /exit/ );
        &bye() if( /kill/ );
}

sub initScreen {
        print PIPE "PC 0\n";
        print PIPE "DR 0 0 159 43 1 1\n";
        print PIPE "DR 3 22 157 40 1 0\n";
        print PIPE "PB 3 22 157 24 0\n";
        print PIPE "FP 0 15 0 0 0 1 \"$artist\"\n";
        print PIPE "FP 0 9 0 15 0 1 \"$title\"\n";
        print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
        print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
}

sub progress {
        while(1) {
                if($status > 0) {
                        $trackCurSecs = `dcop amarok player trackCurrentTime`;
                        $trackCurTime = `dcop amarok player currentTime`;
                        chomp $trackCurSecs;
                        chomp $trackCurTime;
                        print PIPE "PB 5 27 155 35 0 1 1\n";
                        print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
                        print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
                } elsif($status == -1) {
                        return;
                }
                sleep 1;
        }
}

sub bye {
        $status = -1;
        sleep 2;
        print PIPE "PC 0\n";
        system("kill 15 $G15Cpid");
        close(PIPE);
        close(G15COMPOSER);
        $mknod = system("rm $pipe");
        exit 0;
}

```

The script now creates its own pipe and runs g15comopser from within the script.

You can get the D::A::P version [here]("http://svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-perl.pl?revision=112") and the CLI dcop version [here]("http://svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl?revision=113").

---

### Post by drdnl on 2006-10-09
updated first post with details on how to install amarok support for the lcd.

---

### Post by Aneurysm9 on 2006-10-15
Would everyone be so kind as to go take the poll at [http://ubuntuforums.org/showthread.php?t=277518](http://ubuntuforums.org/showthread.php?t=277518)  Thanks.

---

### Post by daihenka on 2006-10-16
I've struck a problem with Aneurysm9's dcop_cli amarok script.  It doesn't display Artist/Title information but displays everything else. (This is with Kubuntu 6.06.1.  I'll test it tomorrow with Ubuntu 6.06.1)

Things I've checked:
* path to the vera font (which is correct)
* upgrading g15composer from 1.0.1 to 1.1.1 (source compile) - no artist/title info displayed
* upgrading g15composer from 1.0.1 to 1.1.1 (1.1.1 deb) - wouldn't run g15composer

Anyone have any ideas on this?  I'm stumped. ](*,) 

Guitoo's script worked, but no progress bar/time information.  I'll most probably hack at Guitoo's version tomorrow, but not tonight.

I've also hacked together some init scripts for g15daemon and g15composer (/dev/g15lcd pipe).  
They are pretty basic and based off the gentoo init scripts, but I can post them here if anyone wants.

---

### Post by Aneurysm9 on 2006-10-16
Daihenka,

Did you install libg15render from source or from my debs?  If you installed from source you need to configure with --enable-ttf to have font support.  The debs are built that way so g15composer from the debs won't work with libg15render from source without ttf support.  If you post the init scripts I'll put them into future debs.

---

### Post by daihenka on 2006-10-16
Everything was installed from debs to start with.  

The only one that wasn't from a deb was g15composer 1.1.1 as the deb didn't work for me and you included the source for it.

I'm going to install Edgy sometime today and remove kubuntu (hate the feel of kde).  After I've installed Edgy, I'll make up some init scripts for it as well and post them here with the Dapper init scripts.

---

### Post by Aneurysm9 on 2006-10-16
It sure sounds like libg15render doesn't have ttf support.  I probably should have made g15composer report an error when ttf support is disabled.  Can you try sending the "FL 0..." line from the script to the pipe after the script is running?  It's only sent once at the top of the script and if something is keeping that from getting through to the composer you'll get no artist/title info as there won't be any font loaded in slot 0.

---

### Post by daihenka on 2006-10-16
I sent it "FL 0 10 "/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf"" to the pipe and no luck.  I'll build libg15render from source instead and test it again.

I'll test this on Ubuntu Dapper and post the results soon as well.

Another thing that you might need to look into with g15composer is that when you turn off the lighting on the keyboard with lightbulb button, the MR button is still lit up.  This only happens when g15composer is running.

---

### Post by Aneurysm9 on 2006-10-16
The light on the MR button is coming from g15daemon, it's an indication that there are active clients connected to the daemon.  I would presume that the M1-M3 buttons would stay lit as well, they do under windows.

Let me know if you have any success after building libg15render from source.  I've got to figure out a way to make autoconf refuse to build g15composer with ttf support without it also being present in libg15render.  I tried before but it didn't work as expected.  Any autotools wizards out there?!?

---

### Post by daihenka on 2006-10-16
Ok just got it displaying the Artist/Title!

I grabbed the latest code from the svn repos and compiled both libg15render-1.1.1 and g15composer-1.1 with --enable-ttf.  It now works :D 
The display looks so much better now! CPU usage is very low.

Thanks for the help with that Aneurysm9. I'll post the init scripts soon.

Have you been able to figure out how to implement the LCD buttons? (the black ones above the multimedia buttons) The MR button doesn't seem to like being pressed too many times.  

If I knew c++ better, I would try and help out.  Anyways, I'm off to install Ubuntu Edgy to make the init scripts for it.

---

### Post by Aneurysm9 on 2006-10-16
Good to hear that you got it working.  The LCD buttons work fine, they're used in my lcdproc driver in the new 5.1 release of lcdproc.  I know what you're saying about the MR button, mine tends to stick occasionally, as if it's a little too big for the hole it's in.  As far as I know, my lcdproc driver is the only one using the LCD buttons, I use the round button for enter, so maybe I'll talk with mlampard about moving the g15daemon swap screen button from MR.  That would also leave MR available for the same use as under windows whenever macro recording and playback software is written for linux.

---

### Post by daihenka on 2006-10-16
Yeah, that would be great if it goes ahead for the LCD switch button.
I'll be happy to test out any changes that are made on Edgy and Dapper. 

Over the next couple of weeks, I'll try and code up some display scripts for the LCD that will act as daemons with init scripts.  Thats the only way I can see it working (but greatly pollutes the system with init scripts imo) unless an amarok script manager style application is made for g15composer.  I'll have a think about it, and see what I can do to help with that.

---

### Post by Aneurysm9 on 2006-10-16
That's a great idea.  Instead of launching an instance of g15composer for each script, add a command to create a new screen.  That way, one script can handle multiple screens without loading multiple copies of g15composer.

---

### Post by daihenka on 2006-10-16
Attached are the init scripts that I created.  

[LIST]
[*]Extract them into /etc/init.d/
[*]Create a group called g15lcd and add yourself and any others that you want to access the composer pipe that is created.
[*]Add them to the default runlevel (update-rc.d g15daemon defaults 20 / update-rc.d g15composer defaults 21)
[/LIST]

I'm not a guru on the runlevels and such and I know I have stuffed up the shutdown process (where g15composer doesn't stop on shutdown). I'll look into this soon.  

The g15daemon init script will automatically modprobe uinput (just incase its not in the module autoloads)

To start g15daemon:
sudo /etc/init.d/g15daemon start 
and to stop g15daemon:
sudo /etc/init.d/g15daemon stop

The g15composer init script will create the pipe called /dev/g15lcd and sets the group ownership to g15lcd.

To start g15composer:
sudo /etc/init.d/g15composer start
and to stop g15composer:
sudo /etc/init.d/g15composer stop

Feel free to modify them to suit your needs.  It would have been nice if ubuntu had a better init scripting environment (similar to gentoo).  Maybe upstart will be decent when they provide more information on it for edgy.

---

### Post by Aneurysm9 on 2006-10-19
I have released g15composer-2.0. The big highlight is that a new screen can be created programmatically. Full details are available at [https://sourceforge.net/forum/forum.php?forum_id=624770](https://sourceforge.net/forum/forum.php?forum_id=624770) Please let me know if you run into any problems as I've changed a lot of things under the hood even though the interface is stable.

Packages will follow as soon as I have a chance to integrate the init scripts.

---

### Post by daihenka on 2006-10-19
Nice work Aneurysm.  I'll try and have a good play around with G15composer over the weekend when I get sometime.

---

### Post by drdnl on 2006-10-19
Great work, will be looking forward to the scripts created. Is there a special place for all these scripts to be saved? Maybe we should ask the current g15forum.com to open up a linux subsection. In fact, think i'll try and ask right now...

-D

---

### Post by Aneurysm9 on 2006-10-19
Attached are Dapper debs for g15composer-2.0 and g15daemon-1.2.1 with the init scripts included.  I've modified the location of the pipe used by g15composer to /dev/g15composer from /dev/g15lcd to remain consistent with the scripts already in use on Gentoo.  This way, scripts like my Amarok script that want to create a new screen don't have to change the location of the control pipe for each distro.  

I'll do the same for Edgy once I get back to the system with the Edgy VM on it.

Edit:

Here are g15composer-2.1 debs for Dapper and Edgy.  The Edgy tarball also includes g15daemon with the init script included.

---

### Post by daihenka on 2006-10-24
I've just started to port some of my work related status monitors across to display on the G15 LCD.  So nice and smooth! :D

Thank you G15Tools team (Especially Aneurysm9) for your time and effort that you have put in so far!

---

### Post by Aneurysm9 on 2006-10-24
If you're writing scripts for g15composer, you may want to use the full syntax for commands with optional components such as PB.  I'm rewriting g15composer with flex and bison and I'm not sure yet whether I'll be able to handle variable length commands.  I think it can be done, but if it can't, it will ease the transition if you're using the full syntax.

---

### Post by daihenka on 2006-10-24
Thanks for the heads up... I'll check out the SVN repos tonight and have a play with the g15composer-ng branch.

---

### Post by Aneurysm9 on 2006-10-25
Can I get some volunteers to try out this version of g15composer?  It should be fully compatible with g15composer-2.1 with the exception that what were previously optional arguments are now mandatory.  I'll work on that some more tomorrow (today?!?) but I'd like to get a few eyes on it as it is.   Thanks.

---

### Post by daihenka on 2006-10-25
I've downloaded g15composer-3.0 and it doesn't seem to like your example tail.pl on my edgy system.  Always exits with "Error: Could not create FIFO /home/sean/.g15tailpipe, aborting".

For some reason since version 2.1 onwards when opening a g15composer active FIFO pipe, g15composer dies (MR light is turned off and the g15composer screen is closed). Version 2.0 is fine though.  Maybe that could be a problem in itself?

This happens on both dapper and edgy.

---

### Post by daihenka on 2006-10-25
I'm currently writing a PHP class to support g15composer. Currently working with v2.0 since 2.1+ doesn't like me :(

Most of the applications I'm working with are php-based.

---

### Post by Aneurysm9 on 2006-10-25
Arg, sorry about that.  tail.pl wasn't supposed to be in the distfile, it's not working yet.  That error happens when the FIFO already exists.  As of 2.1, g15composer handles FIFO creation and deletion.  The pipe you give it to read from must not exist when started.  There was a message about it in the ChangeLog, but it's probably kinda cryptic, I'll add more detailed info to README.  

I don't know if it's possible to wrap a C library in PHP, but you may want to look into wrapping libg15render rather than g15composer if it's possible.  You'd then also need a g15daemon wrapper, but there are perl and python wrappers already for that you can look at to get started.  However you do it, if you want me to include the wrapper with future versions send it along when you're finished.

---

### Post by drdnl on 2006-10-26
Edited first post to reflect availability of g15composer 2.1 debs (including edgy) and quick tips regarding use.

---

### Post by Aneurysm9 on 2006-10-26
I have released g15composer-3.0.  This release reimplements g15composer using flex and bison.  As a result, some command syntax has changed slightly.  See the README for details.

Edit 2: disregard that last edit.  I noticed another bug with right justified text that I fixed and made a quick 3.0.1 release.

---

### Post by shadowhywind on 2006-10-29
Thanks for the wonderful HOWTO! But i am having some slight problems. I have the time being displayed on the lcd. But the MR and M1-3 lights are not on. Also, can we program the G keys like we do in windows , mini-macros? or just strictly hotkeys?

---

### Post by Aneurysm9 on 2006-10-29
The M1-M3 lights are application controlled.  The MR light will come on when a g15daemon client is connected.  Currently, the G keys function as normal extra keys that can be assigned as hotkeys.  Mlampard is planning a rewrite of g15daemon that will include macro recording and playback.

---

### Post by bodhi.zazen on 2006-10-31
Nice How-to drdnl

This thread has been added to the UDSF wiki.

[HOWTO: Install basic G15Tools support for the Logitech G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by drdnl on 2006-10-31
Thank you bodhi.zazen, i feel quite honoured. But of course the majority of the credit should go to the developers at [http://g15tools.sourceforge.net/](http://g15tools.sourceforge.net/) , without them all this would not be possible. I'll make sure to update the thread sometime soon with new versions when I have more time. I am however happy to see few problem posts in this thread, that means it works.

-D

---

### Post by ChadMC on 2006-11-02
is there a g15composer-3.0 .deb file? I can't find one.

---

### Post by drdnl on 2006-11-02
Sorry but no, haven't gotten around to it yet, you can follow the original howto or install the updated debs later in the thread (page 6 or so?)

Regards,
D

---

### Post by ChadMC on 2006-11-02
Well I'm having some problems getting some things to work. I have it to where it shows the Large Clock on the LCD. But when I install the amarok script and run it, it instantly stops running. Also on the g15tools website there is a bunch of screenshots of different thigns you can do, like the weather and other stuff. Is there a place to download these scripts somewhere or a tutorial?

---

### Post by Aneurysm9 on 2006-11-02
Here's a deb for g15composer 3.0.1 (it says 3.0, but it has the fixes from .1)  The amarok scripts that were posted earlier won't work with >=g15composer-2.1 because of how FIFO handling changed.  Attached are updated scripts that will work with 2.1 and 3.0.  The lcdmetar.pl script is part of lcdproc.  The latest version, 5.1, includes the g15 driver.  If you use VDR, graphlcd-svn includes a g15 driver.

---

### Post by ChadMC on 2006-11-02
Thanks for the packages. This is the first time I ran a amarok script without it crashing or giving me errors in the Output Log. However, it still isn't showing in my LCD screen. All I see is the clock. I installed the deb file you just posted and the amarok script as well.

What am I doing wrong? The MR light is off. g15composer and g15daemon is running

---

### Post by ChadMC on 2006-11-02
Some more info..
I'm running edgy eft, also running Beryl/nvidia.
x86 version

---

### Post by Aneurysm9 on 2006-11-02
Can you try stopping the script in the Script Manager, removing $HOME/.g15amaroklcdpipe, and restarting the script?  G15composer will fail to create a new screen if the FIFO already exists.

---

### Post by ChadMC on 2006-11-02
That did the trick. However it is only showing the track playing time. Is it supposed to show the Artist and Track name too? If so, it's not and it's just blacked out at the top. I'm thinking it has something to do with the fonts, but I'm not sure what to do about it.

---

### Post by drdnl on 2006-11-02
Hi,

I too had it running for a moment but not artist/track... Any chance you could release as an amarokscript.tar.gz with self starting g15composer etc.? I tried to do it myself but to no avail, either way thank you for g15composer 3.0, any interesting end user features?

-D

---

### Post by Aneurysm9 on 2006-11-02
Oh yeah, the font path needs to be changed for ubuntu, gotta add truetype/ before ttf-bitstream-vera.  It shouldn't need to start its own instance of g15composer as the composer is now multi-threaded and can handle screen creation.  There is an init script with the debs that will start the composer listening on /var/run/g15composer.  The script now sends an "SN $pipe" command to /var/run/g15composer that causes g15composer to create $pipe and display a new screen reading from that pipe.  The "SC" command at the end closes the display and removes the pipe.  This should be more efficient than having multiple instances of g15composer running as it is only in memory once.  If the init script isn't working for you, let me know, but you can get the same effect in the meantime with "g15cmposer -b /var/run/g15composer"  There will not be a display when g15composer starts (because of the -b argument) so that /var/run/g15composer only listens for "SN" and "SC" commands.  The "SC" command should be sent to the pipe for the screen you want to close.  Sending "SC" to the initial pipe will close all screens and terminate g15composer.

There aren't really any new features, g15composer-3.0 is simply a rewrite from the old C++ codebase that was essentially a rudimentary lexer and parser to now use flex and bison to generate a proper lexer and parser.  I did this because the old code didn't have any significant error handling capability and I thought it would be easier to leverage flex and bison than to reinvent the wheel.  I did slip in one new capability, more an extension of previous features than a new feature in its own right, allowing text placed with "TO" to be right justified.  I'll eventually add the same to libg15render for TTF text.

---

### Post by ChadMC on 2006-11-02
That fixed it. Thanks.

Are there any other scripts or anything to use the LCD screen for? I've tried searching but can't find anything. I've seen screenshots of people showing the weather on there. Any place to get things like that?

---

### Post by Aneurysm9 on 2006-11-02
lcdproc-5.1, [http://www.lcdproc.org](http://www.lcdproc.org), has a driver for the g15.  With that you can use any of the lcdproc scripts that are out there, like the lcdmetar.pl script shown in the screenshot on the g15tools homepage.

---

### Post by ChadMC on 2006-11-02
Thats exactly what I need. Thanks once again. I guess there isn't any .deb files for the newest version that has the g15 driver in it?

I'll try compiling from source, but I usually screw something up when I do that.

---

### Post by Aneurysm9 on 2006-11-02
It's pretty easy, the only catch is to give --enable-drivers=g15 to ./configure.

---

### Post by ChadMC on 2006-11-03
I got it working nicely now. Thanks for the help.

Sorry to keep posting questions.. but now that I have LCDproc running, Amarok won't show up in the LCD now. Is it possible to have them both running at once? If I press the MR key, it just switches between LCDproc and the Big Clock. I've tried deleting the .g15amaroklcdpipe file and then running it again, but it dodn't work. If only the plugin was just in LCDproc =)

---

### Post by DigitalHighlander on 2006-11-03
Wow. great script for Amarok, or so it seems, but..... lol any way to get it supported for the xine engine?  I know, always gotta be one whiner.

---

### Post by Aneurysm9 on 2006-11-03
Sounds like maybe g15composer isn't running.  Try "ps aux | grep g15" to see if it shows up.  There are some amarok scripts for lcdproc, but I don't like them as well as mine (though I may be biased) since they're just plain text.  It's pretty amazing what a couple of rounded boxes and centered TTF text can do.

As for the script working with the xine engine, it should work with any engine.  It gets its data from Amarok via DCOP, which should be the same regardless which engine Amarok is using.

---

### Post by ChadMC on 2006-11-03
Well, it seems like everything is working after I restarted. Not sure what happened there. Oh well, it all works.

Now... to work out all the problems.. ](*,) 
Can you please tell me how or direct me to a howto on how to get all of this to run on startup? Just putting all this stuff in my Session startup doesn't work. I have to run "modprobe uinput" every time I restart. So I need all these commands, I just don't know where to put this. I used to know how to write a startup script, but it's been awhile since I've used linux and I can't remember how to do it. I need all these commands...

sudo modprobe uinput
sudo g15daemon
LCDd
lcdproc

Should I write a startup script for all that stuff, or is there a better place to put all those. I think my problem is the sudo parts. I don't think they work by putting sudo in my session startup.

EDIT:

Nevermind, after a little googling I wrote a startup script and now all is well.

---

### Post by KernelJunkie on 2006-11-08
i tried this stuff on my g15 but the composer won't see the pipe or something.

sword@sword-laptop:~$ mknod /home/sword/lcdpipe p
sword@sword-laptop:~$ g15composer /home/sword/lcdpipe
Error: Could not create FIFO /home/sword/lcdpipe, aborting
sword@sword-laptop:~$


hope u can help me with this.

greets 
KernelJunkie

---

### Post by drdnl on 2006-11-08
Sounds like you have g15composer 2.1 or 3.* running, it handles its own pipe so type rm /home/sword/lcdpipe and then run g15composer /home/sword/lcdpipe

Should work, let me know,

D

---

### Post by KernelJunkie on 2006-11-08
this is what i get:

sword@sword-laptop:~$ g15composer lcdpipe



...

and after i did the command it doesn't do anything.
what must i do to make a text on the screen?

greets
KernelJunkie

---

### Post by Aneurysm9 on 2006-11-08
try it this way instead: g15composer pipe &
so that it will go to the background.  You can then echo commands to the pipe, such as: echo 'TL "Hello World"' > pipe

The commands are detailed in the README file.

---

### Post by KernelJunkie on 2006-11-09
hey,

i found something wicked.
if i start World of Warcraft, login ,and start playing with one of my characters ,the whole world freezes and i can only move my mouse a bit.
is that a fault of the keyboard itself or the g15daemon?

i hooked this g15 keyboard on a Asus Z7000c laptop.

plz help because i wanna be able to play again :)

greetings,
KernelJunkie

---

### Post by Aneurysm9 on 2006-11-09
I don't have WoW myself, so I can't really debug such a problem, but I seem to remember hearing that it had native support for the G15.  If that's the case, it may attempt to communicate with the LCD directly if it finds one attached, which could conflict with g15daemon.  If this only happens with the keyboard attached or with g15daemon running, I would suggest trying to get info from Blizzard about how the G15 support works and whether it can be disabled.

---

### Post by Anaximander Thales on 2006-11-12
Having problems with the amarok script myself.

I've so far attempted to everything listed in the thread to get it working.  I noticed in one post that there should be a g15composer 'init script' (which I'm assuming should be g15composer.pid?) in /var/run -- and that it should be there if installed from the .debs.

I did not install from the debs, plus I have an error that says:

print() on closed filehandle CPIPE (on line 17)

so I'm assuming that this is part of my problem.

So, how would I get that init script in to /var/run?

Also, do I need to have 'g15composer lcdpipe' kick off on start up, or will the amarok script take care of this when I start amarok?  If I do, what's the best way to autostart it.

I have tried having it start in autostart applications (I'm running XFCE4), and it does kick off, but I get the FIFO error when I try to send anything to the pipe -- very frustrating.  If I kill the pipe, and restart it, everything works fine.  I don't know if list order has anything to do with execution order, but when I run 'ps aux | grep g15,' the g15composer always appears before the g15daemon when I restart.  It appears after when I kill it and restart it.

Thanks for any help.

---

### Post by Aneurysm9 on 2006-11-12
The init script would be /etc/init.d/g15composer, which when started should create /var/run/g15composer, which is a pipe where g15composer listens for new screen commands.  If you didn't install from debs, then you should start g15composer as "g15composer -b /var/run/g15composer" in order to use the amarok script or modify the script to suit your environment.  G15composer needs to be running before you start the amarok script.

---

### Post by Anaximander Thales on 2006-11-13
Okay -- just so I'm clear.

Run 'sudo g15composer -b /var/run/g15composer'
then I should be able to run amarok and run the dcop_cli script and see the output on the screen.

---

### Post by Aneurysm9 on 2006-11-13
That should do it.  Make sure that neither /var/run/g15composer nor $HOME/.g15amaroklcdpipe exist before starting g15composer and the script respectively.  G15composer will refuse to operate on a FIFO that already exists to prevent against interfering with another instance of g15composer.

---

### Post by Anaximander Thales on 2006-11-13
Aneurysm9 -- thank you for all the information.

I know I'm not dense, I'm just not getting this to work.  it's not just your script, the other script, guitoo's? (GentooG15Amarok) script, is also not working.

I have made headway on it though.  Prior to your help, nothing would occur.

Now, g15composer pops up (on start up of amarok) and I can flip between that and the clock (which I couldn't do before your help).  However, in either script nothing is displayed.  The screen blanks as if it's trying to write something, but nothing occurs.

I read that I needed g15render needed to be configured with --enable-ttf, so I uninstalled g15composer and g15render and attempted to configure g15render with ttf support, but it errored out on the make portion (sudo make).  The version I have is 1.1.1.

However, if I send something to the pipe, it has no problem displaying.

---

### Post by Aneurysm9 on 2006-11-13
can you paste the error from make on libg15render?  Even if you don't have ttf support compiled in the script should display a box, the progess bar and the time.  TTF is only used for the artist and track name.  I don't know about guitoo's script, but with mine it won't display anything until amarok is playing to avoid sending commands with missing data.

---

### Post by Anaximander Thales on 2006-11-13
I believe I have attached the configure output and the make output.

---

### Post by Aneurysm9 on 2006-11-14
> checking whether to enable FreeType2 support... ./configure: line 18740: freetype-config: command not found

That looks like the problem there.  Do you have the freetype dev packages installed?

---

### Post by Anaximander Thales on 2006-11-14
all right -- new problem.  I'm feeling completely useless now and my field of work is in computer science and tech support.  Although I know my limits on the *nix environments.  This has been a great learning experience for me.

Drdnl -- I'd be happy to make some notes or even help out if you'd like to make this a complete newbies guide to installing the g15 keyboard.

I didn't have the freetype dev install.  Here is what I installed (and only installed) and below that is my procedure:
freetype2         (thought I needed this)
libttf2           (installed with freetype2)
libfreetype6-dev  (realized this one on 2nd read)
zlib1g-dev        (installed with libfreetype6-dev)

attempted to install libg15render-1.1.1
completed with two warnings (at the end about preprocessor)
2 attached files for that.

attempted to install g15composer-3.0.1
completed but with a bunch of warnings (can't remember).
2 attached files for that.

attempted to start the g15composer and recieved error:
   g15composer:
   error while loading shared libraries:
   libg15render.so.1:
   cannot open shared object file: No such file or directory

So -- what next?

---

### Post by Aneurysm9 on 2006-11-14
The libg15render build looks ok.  Those two warnings from configure are to be expected, they have something to do with using macros in an #include statement.  It seems that g15composer was not configured with --enable-ttf, which you'll need if you want to use my amarok script.  As for not finding libg15render.so.1, do you have /usr/local/lib in /etc/ld.so.conf?  If not, add it and run ldconfig.

---

### Post by Anaximander Thales on 2006-11-15
alright -- everything seems to be working now.  Had an issue with having lcdproc loaded, but once I removed it, everything seemed to work.  I suppose that I'll need a shutdown script that closes out g15composer and removes the g15composer pipe from /var/run so that nothing errors out on the next start up?

I guess now I just need to look at the link for all the different formatting commands so I can see what the script is actually doing.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-17
hey guys i need some help with the amarok scrpit. im running edgy kubuntu and i've got the LCD displaying the clock and when i run amarok i can get the progress bar to display on the lcd but not the track name - artist name. i double checked that truetype\ was in the script and it is. but the track info still isnt loading.

i've installed all of this as per the first post in this HOWTO.

thanks for you help.

---

### Post by Aneurysm9 on 2006-11-17
The first question would be whether you have bitstream vera installed.  I think it's installed by default but it can't hurt to check.  The next most likely culprit is that libg15render or g15composer weren't configured with --enable-ttf.  Rebuild them with ttf support and try again.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-18
hey thanks for the quick reply, yeah the fonts are installed. sorry im a newb and not up to compiling my own yet, the files i installed are the packages in the first post so if they have the font enabled then it should be the same on this end.

---

### Post by Aneurysm9 on 2006-11-18
Try libg15render and g15composer from the tarball attached.  I'm not sure whether the ones on the front page are the ones that I built or not.  These should have ttf support enabled.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-18
wow, thankyou for all your help so far! i installed all the packages you gave me but now the amarok script only runs for a second and when i check the error log for the amarok plugin i get this:

mknod: `/home/cameron/.g15amaroklcdpipe': File exists
Error: Could not create FIFO /home/cameron/.g15amaroklcdpipe, aborting

thankyou for you help

---

### Post by Aneurysm9 on 2006-11-18
That would be because the way g15composer deals with pipes has changed.  Delete /home/cameron/.g15amaroklcdpipe and use the current script that you can get from here: [http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl?revision=158](http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl?revision=158)

Then start g15composer with /etc/init.d/g15composer and start Amarok.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-18
im really sorry but how do i get amarok to load the script you gave me, its not finding the file in the script manager.

newbie question i know

---

### Post by Aneurysm9 on 2006-11-18
look under /home/cameron/.kde/share/apps/amarok/scripts/ you can just copy the new file into there.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-18
hey i've moved the script into there but its not showing up in the script manager.

---

### Post by Aneurysm9 on 2006-11-18
that's strange.  Is there an "amarok-g15" subfolder under there?  If so, try moving the script into there.

---

### Post by &lt;StAiNlEsS&gt; on 2006-11-18
nah there isn't, i've tried installing the old sript and just overwriting the file and that didnt work either.

---

### Post by Aneurysm9 on 2006-11-19
That's odd.  Try editing the script from within Amarok's script manager, deleting the text from the old script and pasting in the text from the new one.

---

### Post by Louie on 2006-11-19
Hello there. I installed the thinks you said. But when I try to start the g15daemon it says;

louie@louie:~$ sudo g15daemon 
An Error Occurred - 3 : ( Unable to configure the linux kernel UINPUT driver ) received

Do you know why?

---

### Post by ChadMC on 2006-11-19
Did you try
```
sudo modprobe uinput
```

---

### Post by Louie on 2006-11-19
No I didn't, but I can see a HUGE clock on my G15 now. THANK YOU! :)

---

### Post by Louie on 2006-11-19
Hmm, my clock work perfectly. Ive also installed the script for amarok. But when I load the first one in the script manager in amarok it stops directly. And when I try the second version I only get the text "G15Composer" on my LCD screen. Whats wrong then? It would be nice to see my tracks ;P

---

### Post by Aneurysm9 on 2006-11-19
My current amarok script will display "G15Composer" until amarok starts playing.  If you're still seeing that after Amarok starts playing then that might be a problem.  Can you try this command when you have the "G15Composer" display:  echo 'TL "This is a test"' > $HOME/.g15amaroklcdpipe

If g15composer is working you'll see "This is a test" on the LCD.  If you do then it's an issue with the amarok script, if you don't it's g15composer.

---

### Post by drdnl on 2006-11-20
Hi Aneurysm9, I've been using your amarok script for quite some time now and it works better than the original one except for the fact that whilst g15composer now handles its own pipe it doesnt always handle it in a user friendly manner. For some reason my amarok never seems to close properly thus removing the pipe so when i start it up again I need to (every time) stop the amarok script, delete the pipe myself and then start it again. From here on it will work fine till I restart Amarok.

My question is, would it be possible for either g15composer or your script to simply use or delete any existing pipe? I'm pretty sure there's no vital data in a pipe that could be lost.

Anyone else have this problem?

Regards,
D

---

### Post by Aneurysm9 on 2006-11-20
I don't want g15composer to do it because it could overwrite a pipe that is in use by another script.  The same thing can happen if a script, but I guess the amarok script is the kind of script where it's only likely to be run once at a time.  If you want to avoid those issues, you could add "unlink $pipe;" before the SN command to create the pipe, making sure that it's not there before it's used.

---

### Post by Zypher3001 on 2006-11-22
I have installed g15composer 3.0.1, lcdproc 0.5.1, g15daemon 1.2.6a, libdaemon 0.10, and libg15 1.0.  I ran modprobe uinput and then ran g15daemon as root.  My LCD says g15 4 Linux daemon loaded, but I never see and clock and I can't get the script that I want to use to display anything on the screen even after I run g15composer /home/[username]/lcdpipe.  Any ideas as to how I can try and troubleshoot this problem?

Thanks.

---

### Post by mlampard on 2006-11-22
I'm not sure what happened here.  Can you try running g15daemon with the --debug option, which should help narrow down the problem.

---

### Post by KClaisse on 2006-11-22
I need help.
I got the LCD clock working, now I am trying to get Amarok to work.
I don't have DCOP so I donloaded DCOP, DCOP:Amarok, DCOP::Amarok::Player and tried to install them.
It says that I can't build DCOP because I don't have ExtUtils::MakeMaker, but when I try to build MakeMaker it says
```

Checking if your kit is complete...
Looks good
Could not open '': No such file or directory at lib/ExtUtils/MM_Unix.pm line 2697.

```

i am so lost.

---

### Post by Aneurysm9 on 2006-11-22
KClaisse,

you can use the dcop_cli version of the amarok script.  It uses the cli dcop client from kde rather than the perl modules that some have trouble building.

---

### Post by KClaisse on 2006-11-23
OK I got it working for the most part. Here's how.
I added this to /etc/sudoers (at the end)
(kyle is the my username)
```

kyle ALL= NOPASSWD: /usr/sbin/g15daemon
kyle ALL= NOPASSWD: /usr/local/bin/g15composer
kyle ALL= NOPASSWD: /sbin/modprobe

```

then I created this script to start when gnome starts (added under sessions).
```

#!/bin/bash
sudo /sbin/modprobe saa7134 card=3 tuner=39
sleep 1s
#
sudo /sbin/modprobe uinput
sleep 1s
#
sudo /usr/sbin/g15daemon
sleep 1s
#
sudo g15composer -b /var/run/g15composer &


```
It seems the sleep 1s is necessary for everything to work properly. Without it things don't start right.

Now the only problem left is this output from the amarok script:
```

Can't exec "/home/kyle/.g15amaroklcdpipe": No such file or directory at /home/kyle/.kde/share/apps/amarok/scripts/amarok-g15-dcop_cli.pl line 9.

```

I'm think of changing
```

my $pipe = "$ENV{HOME}/.g15amaroklcdpipe";

```
to
```

my $pipe = "/var/run/g15composer";

```
But I don't want to mess anything up. As of now it actually works.

Will that change remove this error without hurting anythng?

---

### Post by Zypher3001 on 2006-11-23
Here is the output I got from running g15daemon --debug

Found g15, trying to open it
Trying to detach drive currentl attached: "usbhid"
Success, detached the driver
Debug: usbhid
Done opening the keyboard
g15daemon 1.2.6a loaded

I still only got the "G15 4 Linux daemon loaded" output on my LCD.

One question I have...  I know I should get the clock as soon as the daemon starts, but I noticed that once I run g15composer, it creates the pipe, but when I run ps -el I don't see g15composer running as a process in the listing.  I only see g15daemon.  Shouldn't the composer still be running?

---

### Post by Aneurysm9 on 2006-11-23
KClaisse,

It looks like maybe you're using an older version of the amarok script.  You can get the current version here: [http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/tags/g15composer-3.0/examples/amarok-g15-dcop_cli.pl?revision=160](http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/tags/g15composer-3.0/examples/amarok-g15-dcop_cli.pl?revision=160)

changing $pipe to /var/run/g15composer won't work since g15composer is only listening there for SN commands and doesn't create a screen for it (because of the -b argument on the command line).

Zypher3001,

It sounds like g15composer may be causing your problem then.  Are you starting g15composer as soon as you start g15daemon?  Does g15daemon show the clock if you don't start g15composer?  Are you using an AMD64 system?

---

### Post by drdnl on 2006-11-23
Edit: FFS :), its working fine now, no idea what was wrong with it earlier. I'll post a message if it happens again. Having worked on g15tools/daemon for a while now, what are the chances the amarok script will get some eyecandy? (equalizer/analyzer)

Hey Aneurysm9, thanks for the unlink, now that it removes the pipe it gets rid of one particularly tedious step :) Just one little issue, my amarok (1.4.4 on gnome) never starts the script on startup. It shuts the script down properly and displays a little play button next to the script in the script manager but no running script anywhere. A quick stop/start in script manager fixes this quickly but it would be nice if it where automatic. Any idea's? I have checked the MR button in order to see if it was "hiding" on another page/tab but no luck.

Regards,
D

---

### Post by Zypher3001 on 2006-11-23
Aneurysm9  	

I never see the g15daemon clock on the lcd.  I do wait for a minute before I start g15composer.  And yes, I am using an AMD64 system.  I just tried the old version of g15composer that I still had also with no luck.

---

### Post by Aneurysm9 on 2006-11-23
I dunno about getting an analyzer going for Amarok.  The DCOP interface doesn't provide any frequency or PCM data from which to create an analyzer or oscilloscope.  I'll look into the libvisual visualization system to see if maybe it can be done that way.  I've been playing with the XMMS plugin from g15daemon and now that I've got a grip on how that works it should be fairly easy to recreate it for Amarok.  As for the script not starting on startup, I've not a clue.  I've got 1.4.4 on gnome as well and it starts automatically as would be expected for me.  You'll probably have to ask around on the Amarok lists for an answer to that one.

---

### Post by Aneurysm9 on 2006-11-23
Hmm.  If the clock never shows up even without starting g15composer then it is g15daemon that's not working right.  Are you building g15daemon from svn?  If so, can you jump back to about rev. 60 and, if that works, try a binary search forward until you find the change that broke things for you.

---

### Post by drdnl on 2006-11-23
Oh I'm sorry if I didnt make it entirely clear, amarok is working fine now (with auto-start scripts). Haven't rebooted yet though, I'll have to test that later :)

About the analyzer, it would truly be great if we linux users also have the option of a g15 analyzer but if DCOP doesnt supply it I understand if maybe it is quite a bit harder to do. I'm not a programmer, at most a tinkerer, but all those analyzers built into Amarok (and the plugin based ones) have to get their info from somewhere :)

Either way, g15 support is maturing nicely. I wonder whether all this work would provide a good base for linux support if Logitech (hypothetically) released a G25 with colour screen etc.

Excellent work!

---

### Post by Aneurysm9 on 2006-11-23
The Amarok visualizations are either libvisual or xmms plugins.  There's an xmms plugin that comes with g15daemon that might work (though it won't provide artist or track info due to the way Amarok handles xmms plugins).  I'm looking at the code for some of the libvisual plugins right now, but there's a whole bunch of private data types that don't seem to be very well documented so it could take a while before I grok it enough to actually do something with it.

We've tried to make things so that it should be relatively simple to extend support to other keyboards with LCD displays, though none of us have anything other than the G15 so we can't really test that theory.  For libg15render, color support should be simply a matter of modifying g15r_setPixel since all the other functions end up calling that one.  That would enable, i.e, drawing a red circle rather than just black or white, but things like gradients would be a bit more complex.  G15daemon should likewise be capable of supporting additional hardware in the next release now that it's based on plugins.  All that would need to be done (hopefully) would be to write a plugin to handle the new LCD interface.

---

### Post by drdnl on 2006-11-23
Well, if you get it to work (or anyone else for that matter) i'll buy you a big "thank you" beer (via paypal)

Should be interesting to watch the developments,

-D

---

### Post by rasta_freak on 2006-11-23
Hi everyone. My small tribute for g15 packages.
I'm using g15daemon_1.2.1 on Kubuntu 6.10.
This is nice clock client for G15. Please try it and tell...

---

### Post by Aneurysm9 on 2006-11-23
rasta_freak,

Thanks.  Good to see other people programming for the G15.  Can you share the source for your clock client?  I use Gentoo with my G15 so I'd like it compiled for my system.  Plus, any nifty new features could be incorporated into the g15daemon clock plugin in the next version, if you are willing to release the source under the GPL.

---

### Post by rasta_freak on 2006-11-24
Sure, here it is. I wonder about performance issues, please take a look and tell.

---

### Post by Aneurysm9 on 2006-11-24
That is very nice.  I was hoping when I put in g15r_drawCircle that someone would use it to make a nice analog clock.  Would you mind if I worked this into the clock plugin for the upcoming version of g15daemon?

---

### Post by rasta_freak on 2006-11-24
No, please do. I love my G15 keyboard, and I love even more that linux not only supports it, it kicks it's *** :) Thank you for all your work.

---

### Post by Aneurysm9 on 2006-11-24
Thank you very much.  I've got it integrated into the clock plugin for what will be g15daemon-2.0.  It was even easier than I thought.  It's in trunk/g15daemon-wip as of rev 195 if you want to check it out.  I've dropped the load meter because I'd like to keep the clock simply a clock.  There are other options, such as lcdproc, for load meters.  I did like that you used mode_xor for the text in the meter though.  I had played with that with my amarok script but had trouble getting it to work right.  Maybe I'll try it again sometime.  I think I'll need to change the bar type though.

As for performance issues, I don't see any.  My system isn't ancient, but it's over three years old and it doesn't even break a sweat drawing the clock.  Drawing the clock face to a static canvas will surely save some cycles on systems where it's important.  Other than that, I'm not sure I see where speed could be improved unless it's in the math which isn't my strong suit.

---

### Post by dreadbrazen on 2006-11-25
Hey guys, just got my g15 keyboard and have been playing around with it.  I have everything working properly, except for when I go to run any scripts.  I get this error:

Error, could not create FIFO /home/brazen/.g15amaroklcdpipe aborting

So....  I'm still a little unfamiliar with this sort of technology (piping and such).  Help me out a little?

Great work, by the way.  I'm loving everything you guys are putting into this.  I'm using Edgy EFT (6.10).  It would be good to note that media keys work out-of-the-box in Kubuntu and amarok.

---

### Post by Aneurysm9 on 2006-11-25
The most likely cause for that is that $HOME/.g15amaroklcdpipe already exists.  Delete it and try again.

---

### Post by V-ernie-R on 2006-11-26
I made a little Start/Stop script for the g15daemon. Maybe its usefull to you guys too.

> **rasta_freak said:**
> Hi everyone. My small tribute for g15 packages.
I'm using g15daemon_1.2.1 on Kubuntu 6.10.
This is nice clock client for G15. Please try it and tell...

I made also one for the clock client. Thank you for the nice client rasta_freak :) 

Just put the files somewhere in your home folder and make shortcuts to the scripts. I added also two icons for the scripts. Run the script once to start   the g15daemon, run it again to kill the daemon. The same goes for the clock script.

---

### Post by Aneurysm9 on 2006-12-02
I've released g15composer-3.0.2 as an interim release before 3.1, adding improved FIFO handling and the ability to set the effective UID for the g15composer process.  I'm doing this because g15composer-3.1 will include new features from libg15render-1.2 and I'm holding off on that until g15daemon-2.0, which now uses libg15render, so we can get all the improvements in one release.

FIFO handling is now greatly improved.  If a FIFO does not exist, it will be created.  If it exists, but there is no process reading from it, g15composer will start reading from it.  If it exists and another process is reading from it, or g15composer is unable to create or open the FIFO, g15composer will error and exit as appropriate.  Also, when invoked, g15composer will attempt to open /var/run/g15composer for writing, if another g15composer instance is listening there, g15composer will ask that instance to open a new screen rather than have multiple instances loaded simultaneously.

Changing the effective UID may provide some security against misbehaving scripts and g15composer errors.  It is currently only recommended for single user systems due to the potential for permission problems if not correctly configured on multi-user systems.

Debs for edgy are attached.

---

### Post by NZ-Wanderer on 2006-12-07
Hi all, Brand new G15 user here, just got it couriered to me today.. :D :D 
Got it all up and working in XP and Vista, now gonna try to get it working in Kubuntu..
Have read all 16 pages, downloaded all the files in the pages and got totally lost (which isn't unusual for me) so am going to follow the instructions on page One and ignore everything else..

Hopefully I can do this......

---

### Post by Aneurysm9 on 2006-12-07
User-friendliness may not be the strong suit of this software, but other people have managed to do it, with help or without, so I'm sure you'll be able to do it too.  If you have any questions, just ask, someone will more than likely have an answer.  Best of luck.

---

### Post by NZ-Wanderer on 2006-12-07
Thanks for that...

Will see how I go, struck a problem but finally figured out my downloader had double named the extensions, so have renamed the files and will try to carry on :)

> **Aneurysm9 said:**
> User-friendliness may not be the strong suit of this software, but other people have managed to do it, with help or without, so I'm sure you'll be able to do it too.  If you have any questions, just ask, someone will more than likely have an answer.  Best of luck.

---

### Post by Aneurysm9 on 2006-12-07
It looks like the info on the first page is a bit out of date.  I'm updating it over at the UDSF, [http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15).  Here's a tarball with current debs for each of the tools.

---

### Post by NZ-Wanderer on 2006-12-07
Thanks for that :) - looks like I have to go through it all again.. - BTW, I actually got the clock showing up... :mrgreen: :mrgreen: 

I did have one tiny problem tho, I can't use your composer 3.0.2.1 as the file gives me an error when trying to use the packet manager, it says that I am using libc6 2.3.6-0ubuntu20 whereas composer needs >=2.4.1 and that file isn't in the respositories.

Ok, I off to redo the later files you included :)

PS: I didn't need to do the autorun part either, for some reason Kubuntu autostarts it, and I get the clock showing up when I get to my password prompt.

> **Aneurysm9 said:**
> It looks like the info on the first page is a bit out of date.  I'm updating it over at the UDSF, [http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15).  Here's a tarball with current debs for each of the tools.

---

### Post by Aneurysm9 on 2006-12-07
Yeah, looks like you're using dapper and the packages I just built are for edgy.  If you feel comfortable building from source, you can do it that way, or I can put together a dapper VM to build packages if you prefer.

---

### Post by NZ-Wanderer on 2006-12-07
Ohhh if you would do it I would appreciate it.. - I just thought I would be smart and install using that command you listed on that page you redone... - Man did I get a shock... - I got:

```
john@kubuntu:/media/Go-Between/linux-g15/untared-files$ sudo dpkg -i libg15_1.1-
1_i386.deb libg15render_1.1.1-1_i386.deb libg15daemon-client_1.2.6a-1_i386.deb g
15daemon_1.2.6a-1_i386.deb g15composer_3.0.2-1_i386.deb
(Reading database ... 176866 files and directories currently installed.)
Preparing to replace libg15 1.0-1 (using libg15_1.1-1_i386.deb) ...
Unpacking replacement libg15 ...
Preparing to replace libg15render 1.1-1 (using libg15render_1.1.1-1_i386.deb) ..
.
Unpacking replacement libg15render ...
dpkg: warning - unable to delete old directory `/usr/local/lib': Directory not e
mpty
dpkg: warning - unable to delete old directory `/usr/local': Directory not empty
Preparing to replace libg15daemon-client 1.2.1-2 (using libg15daemon-client_1.2.
6a-1_i386.deb) ...
Unpacking replacement libg15daemon-client ...
Preparing to replace g15daemon 1.2.1-2 (using g15daemon_1.2.6a-1_i386.deb) ...
 * Stopping G15 Daemon...                                                [ ok ]
Unpacking replacement g15daemon ...
Preparing to replace g15composer 2.1-1 (using g15composer_3.0.2-1_i386.deb) ...
 * Stopping G15 Composer...                                              [ ok ]
Unpacking replacement g15composer ...
dpkg: dependency problems prevent configuration of libg15:
 libg15 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 libg15 depends on libusb-0.1-4 (>= 2:0.1.12); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1.
dpkg: error processing libg15 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libg15render:
 libg15render depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 libg15render depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 libg15render depends on libg15; however:
  Package libg15 is not configured yet.
dpkg: error processing libg15render (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libg15daemon-client:
 libg15daemon-client depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 libg15daemon-client depends on libg15; however:
  Package libg15 is not configured yet.
dpkg: error processing libg15daemon-client (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g15daemon:
 g15daemon depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 g15daemon depends on libg15; however:
  Package libg15 is not configured yet.
 g15daemon depends on libusb-0.1-4 (>= 2:0.1.12); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1.
 g15daemon depends on libg15daemon-client (= 1.2.6a-1); however:
  Package libg15daemon-client is not configured yet.
dpkg: error processing g15daemon (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g15composer:
 g15composer depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 g15composer depends on libg15render; however:
  Package libg15render is not configured yet.
 g15composer depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15composer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libg15
 libg15render
 libg15daemon-client
 g15daemon
 g15composer
john@kubuntu:/media/Go-Between/linux-g15/untared-files$

```

Now I really don't know what to do.... ](*,) ](*,) 

If there is an easy way to tell me how to build from source I would give it a go to save you making a VM...

> **Aneurysm9 said:**
> Yeah, looks like you're using dapper and the packages I just built are for edgy.  If you feel comfortable building from source, you can do it that way, or I can put together a dapper VM to build packages if you prefer.

---

### Post by Aneurysm9 on 2006-12-07
What you'll need to do is download the latest distfiles for libg15, libg15render, g15daemon and g15composer.  You can get them from [http://g15tools.sourceforge.net/](http://g15tools.sourceforge.net/).  Extract all of them, then build them in order.  Go into the directory and configure the package with ./configure --prefix=/usr then build it with make and install with sudo make install.  Lig15render and g15composer can be built with truetype font support if you add --enable-ttf to the configure line.  You may need to install libfreetype6-dev to use truetype fonts.

---

### Post by NZ-Wanderer on 2006-12-07
Hmmmm I'll try anything once...

So I get the files, put them all into a temp folder.
cd to the temp folder (then you sort of lost me, do I:
then do a ./configure --prefix=/usr on each of the files??? eg: ./configure --prefix=/usr libg15

If you could type each of the commands I need to do I could follow that real easy :-D (I good at following commands)

> **Aneurysm9 said:**
> What you'll need to do is download the latest distfiles for libg15, libg15render, g15daemon and g15composer.  You can get them from [http://g15tools.sourceforge.net/](http://g15tools.sourceforge.net/).  Extract all of them, then build them in order.  Go into the directory and configure the package with ./configure --prefix=/usr then build it with make and install with sudo make install.  Lig15render and g15composer can be built with truetype font support if you add --enable-ttf to the configure line.  You may need to install libfreetype6-dev to use truetype fonts.

---

### Post by Aneurysm9 on 2006-12-07
sure, first we'll install libfreetype6-dev if you don't have it:
```

sudo apt-get install libfreetype6-dev
```

then we'll extract all the files (assuming we're in a directory containing only the tar.bz2 files you've downloaded):
```

tar jxvf *.bz2
```

Now we have directories for each tarball and we want to build them in order.  Since we're doing the same thing for each directory we'll use a for loop to cut down on typing :)

```
for package in libg15-1.1.0 libg15render-1.1.1 g15daemon-1.2.6a g15composer-3.0.2
do;
cd $package
./configure --prefix=/usr --enable-ttf
make
sudo make install
cd ..
done

```
And that should do it.

---

### Post by NZ-Wanderer on 2006-12-07
Ok, I checked and the libfreetype6-dev is already installed..

While I was waiting I have grabbed the files and extracted them into a folder called sources. (I ended up with the following folders:)

g15composer-3.0.2
g15daemon-1.2.6a
g15lcd-1.2
libg15-1.1.0
libg15render-1.1.1

Is this correct so far??

If so, where do I put that loop?? paste it into terminal??

---

### Post by Aneurysm9 on 2006-12-07
So far so good.  We don't need g15lcd-1.2, that's the original program that the other tools reimplement.  Paste the for loop into a shell and it should start building each package.

---

### Post by NZ-Wanderer on 2006-12-07
oops, something not right.. - I pasted the lines into terminal like you said and got the following:

ohn@kubuntu:/media/Go-Between/linux-g15/sources/sources$ for package in libg15-1.1.0 libg15render-1.1.1 g15daemon-1.2.6a g15composer-3.0.2
> do;
bash: syntax error near unexpected token `;'
john@kubuntu:/media/Go-Between/linux-g15/sources/sources$ cd $package
john@kubuntu:~$ ./configure --prefix=/usr --enable-ttf
bash: ./configure: No such file or directory
john@kubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
john@kubuntu:~$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
john@kubuntu:~$

---

### Post by Aneurysm9 on 2006-12-07
oops, serves me right for trying to give instructions from memory.  Remove the ; and it should work.

---

### Post by NZ-Wanderer on 2006-12-07
Should I have done that in root terminal instead of normal terminal?? cause it got a few errors (not allowed etc)

Here is part of the output for you to look at, I can't understand it... (couldn't put it all in cause it was too long...)

```
john@kubuntu:/media/Go-Between/linux-g15/sources/sources$ for package in libg15-1.1.0 libg15render-1.1.1 g15daemon-1.2.6a g15composer-3.0.2
> do
> cd $package
> ./configure --prefix=/usr --enable-ttf
> make
> sudo make install
> cd ..
> done
chmod: changing permissions of `conf6657.sh': Operation not permitted
chmod: changing permissions of `conf6657.file': Operation not permitted
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... no, using cp -p
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... chmod: changing permissions of `.': Operation not permitted
yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
chmod: changing permissions of `libtool': Operation not permitted
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... chmod: changing permissions of `.': Operation not permitted
yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
chmod: changing permissions of `libtool': Operation not permitted
checking for main in -lusb... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for an ANSI C-conforming const... yes
checking for memset... yes
configure: creating ./config.status
chmod: changing permissions of `./config.status': Operation not permitted
chmod: changing permissions of `conf10052.sh': Operation not permitted
chmod: changing permissions of `conf10052.file': Operation not permitted
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/libg15-1.1.0'
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT libg15.lo -MD -MP -MF ".deps/libg15.Tpo" -c -o libg15.lo libg15.c; \
        then mv -f ".deps/libg15.Tpo" ".deps/libg15.Plo"; else rm -f ".deps/libg15.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT libg15.lo -MD -MP -MF .deps/libg15.Tpo -c libg15.c  -fPIC -DPIC -o .libs/libg15.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT libg15.lo -MD -MP -MF .deps/libg15.Tpo -c libg15.c -o libg15.o >/dev/null 2>&1
/bin/sh ./libtool --tag=CC --mode=link gcc  -g -O2   -o libg15.la -rpath /usr/lib -version-info 1:0:0 libg15.lo  -lusb
gcc -shared  .libs/libg15.o  /usr/lib/libusb.so  -Wl,-soname -Wl,libg15.so.1 -o .libs/libg15.so.1.0.0
(cd .libs && rm -f libg15.so.1 && cp -p libg15.so.1.0.0 libg15.so.1)
cp: preserving times for `libg15.so.1': Operation not permitted
make[1]: *** [libg15.la] Error 1
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/libg15-1.1.0'
make: *** [all] Error 2
/bin/sh ./libtool --tag=CC --mode=link gcc  -g -O2   -o libg15.la -rpath /usr/lib -version-info 1:0:0 libg15.lo  -lusb
rm -fr  .libs/libg15.so.1 .libs/libg15.so.1.0.0
gcc -shared  .libs/libg15.o  /usr/lib/libusb.so  -Wl,-soname -Wl,libg15.so.1 -o .libs/libg15.so.1.0.0
(cd .libs && rm -f libg15.so.1 && cp -p libg15.so.1.0.0 libg15.so.1)
(cd .libs && rm -f libg15.so && cp -p libg15.so.1.0.0 libg15.so)
ar cru .libs/libg15.a  libg15.o
ranlib .libs/libg15.a
creating libg15.la
(cd .libs && rm -f libg15.la && cp -p ../libg15.la libg15.la)
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/libg15-1.1.0'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libg15.la' '/usr/lib/libg15.la'
/usr/bin/install -c .libs/libg15.so.1.0.0 /usr/lib/libg15.so.1.0.0
(cd /usr/lib && { cp -p -f libg15.so.1.0.0 libg15.so.1 || { rm -f libg15.so.1 && cp -p libg15.so.1.0.0 libg15.so.1; }; })
(cd /usr/lib && { cp -p -f libg15.so.1.0.0 libg15.so || { rm -f libg15.so && cp -p libg15.so.1.0.0 libg15.so; }; })
/usr/bin/install -c .libs/libg15.lai /usr/lib/libg15.la
/usr/bin/install -c .libs/libg15.a /usr/lib/libg15.a
ranlib /usr/lib/libg15.a
chmod 644 /usr/lib/libg15.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
ldconfig: /usr/lib/libg15.so.1 is not a symbolic link

----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'libg15.h' '/usr/include/libg15.h'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/libg15-1.1.0'
chmod: changing permissions of `conf10565.sh': Operation not permitted
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... no, using cp -p
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
chmod: changing permissions of `libtool': Operation not permitted
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
chmod: changing permissions of `libtool': Operation not permitted
checking whether to enable FreeType2 support... yes
checking for writePixmapToLCD in -lg15... yes
checking for ceil in -lm... yes
checking for an ANSI C-conforming const... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking ft2build.h usability... yes
checking ft2build.h presence... no
configure: WARNING: ft2build.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: ft2build.h: proceeding with the compiler's result
checking for ft2build.h... yes
checking for ANSI C header files... (cached) yes
checking for memset... yes
configure: creating ./config.status
chmod: changing permissions of `./config.status': Operation not permitted
chmod: changing permissions of `conf13747.sh': Operation not permitted
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/libg15render-1.1.1'
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT text.lo -MD -MP -MF ".deps/text.Tpo" -c -o text.lo text.c; \
        then mv -f ".deps/text.Tpo" ".deps/text.Plo"; else rm -f ".deps/text.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT text.lo -MD -MP -MF .deps/text.Tpo -c text.c  -fPIC -DPIC -o .libs/text.o
text.c: In function 'g15r_renderString':
text.c:92: warning: comparison between pointer and integer
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT text.lo -MD -MP -MF .deps/text.Tpo -c text.c -o text.o >/dev/null 2>&1
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT pixel.lo -MD -MP -MF ".deps/pixel.Tpo" -c -o pixel.lo pixel.c; \
        then mv -f ".deps/pixel.Tpo" ".deps/pixel.Plo"; else rm -f ".deps/pixel.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT pixel.lo -MD -MP -MF .deps/pixel.Tpo -c pixel.c  -fPIC -DPIC -o .libs/pixel.o
pixel.c: In function 'g15r_drawBar':
pixel.c:324: warning: incompatible implicit declaration of built-in function 'ceil'
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT pixel.lo -MD -MP -MF .deps/pixel.Tpo -c pixel.c -o pixel.o >/dev/null 2>&1
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT screen.lo -MD -MP -MF ".deps/screen.Tpo" -c -o screen.lo screen.c; \
        then mv -f ".deps/screen.Tpo" ".deps/screen.Plo"; else rm -f ".deps/screen.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT screen.lo -MD -MP -MF .deps/screen.Tpo -c screen.c  -fPIC -DPIC -o .libs/screen.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT screen.lo -MD -MP -MF .deps/screen.Tpo -c screen.c -o screen.o >/dev/null 2>&1
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT font_6x4.lo -MD -MP -MF ".deps/font_6x4.Tpo" -c -o font_6x4.lo font_6x4.c; \
        then mv -f ".deps/font_6x4.Tpo" ".deps/font_6x4.Plo"; else rm -f ".deps/font_6x4.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_6x4.lo -MD -MP -MF .deps/font_6x4.Tpo -c font_6x4.c  -fPIC -DPIC -o .libs/font_6x4.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_6x4.lo -MD -MP -MF .deps/font_6x4.Tpo -c font_6x4.c -o font_6x4.o >/dev/null 2>&1
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT font_7x5.lo -MD -MP -MF ".deps/font_7x5.Tpo" -c -o font_7x5.lo font_7x5.c; \
        then mv -f ".deps/font_7x5.Tpo" ".deps/font_7x5.Plo"; else rm -f ".deps/font_7x5.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_7x5.lo -MD -MP -MF .deps/font_7x5.Tpo -c font_7x5.c  -fPIC -DPIC -o .libs/font_7x5.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_7x5.lo -MD -MP -MF .deps/font_7x5.Tpo -c font_7x5.c -o font_7x5.o >/dev/null 2>&1
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2 -MT font_8x8.lo -MD -MP -MF ".deps/font_8x8.Tpo" -c -o font_8x8.lo font_8x8.c; \
        then mv -f ".deps/font_8x8.Tpo" ".deps/font_8x8.Plo"; else rm -f ".deps/font_8x8.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_8x8.lo -MD -MP -MF .deps/font_8x8.Tpo -c font_8x8.c  -fPIC -DPIC -o .libs/font_8x8.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -I/usr/include/freetype2 -g -O2 -I/usr/include/freetype2 -MT font_8x8.lo -MD -MP -MF .deps/font_8x8.Tpo -c font_8x8.c -o font_8x8.o >/dev/null 2>&1
/bin/sh ./libtool --tag=CC --mode=link gcc -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2   -o libg15render.la -rpath /usr/lib -version-info 1:0:0 text.lo pixel.lo screen.lo font_6x4.lo font_7x5.lo font_8x8.lo -lfreetype -lm -lg15
gcc -shared  .libs/text.o .libs/pixel.o .libs/screen.o .libs/font_6x4.o .libs/font_7x5.o .libs/font_8x8.o  /usr/lib/libfreetype.so -lm /usr/lib/libg15.so -L/usr/lib  -Wl,-soname -Wl,libg15render.so.1 -o .libs/libg15render.so.1.0.0
(cd .libs && rm -f libg15render.so.1 && cp -p libg15render.so.1.0.0 libg15render.so.1)
cp: preserving times for `libg15render.so.1': Operation not permitted
make[1]: *** [libg15render.la] Error 1
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/libg15render-1.1.1'
make: *** [all] Error 2
/bin/sh ./libtool --tag=CC --mode=link gcc -g -O2 -I/usr/include/freetype2  -g -O2 -I/usr/include/freetype2   -o libg15render.la -rpath /usr/lib -version-info 1:0:0 text.lo pixel.lo screen.lo font_6x4.lo font_7x5.lo font_8x8.lo -lfreetype -lm -lg15
rm -fr  .libs/libg15render.so.1 .libs/libg15render.so.1.0.0
gcc -shared  .libs/text.o .libs/pixel.o .libs/screen.o .libs/font_6x4.o .libs/font_7x5.o .libs/font_8x8.o  /usr/lib/libfreetype.so -lm /usr/lib/libg15.so -L/usr/lib  -Wl,-soname -Wl,libg15render.so.1 -o .libs/libg15render.so.1.0.0
(cd .libs && rm -f libg15render.so.1 && cp -p libg15render.so.1.0.0 libg15render.so.1)
(cd .libs && rm -f libg15render.so && cp -p libg15render.so.1.0.0 libg15render.so)
ar cru .libs/libg15render.a  text.o pixel.o screen.o font_6x4.o font_7x5.o font_8x8.o
ranlib .libs/libg15render.a
creating libg15render.la
(cd .libs && rm -f libg15render.la && cp -p ../libg15render.la libg15render.la)
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/libg15render-1.1.1'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libg15render.la' '/usr/lib/libg15render.la'
/usr/bin/install -c .libs/libg15render.so.1.0.0 /usr/lib/libg15render.so.1.0.0
(cd /usr/lib && { cp -p -f libg15render.so.1.0.0 libg15render.so.1 || { rm -f libg15render.so.1 && cp -p libg15render.so.1.0.0 libg15render.so.1; }; })
(cd /usr/lib && { cp -p -f libg15render.so.1.0.0 libg15render.so || { rm -f libg15render.so && cp -p libg15render.so.1.0.0 libg15render.so; }; })
/usr/bin/install -c .libs/libg15render.lai /usr/lib/libg15render.la
/usr/bin/install -c .libs/libg15render.a /usr/lib/libg15render.a
chmod 644 /usr/lib/libg15render.a
ranlib /usr/lib/libg15render.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
ldconfig: /usr/lib/libg15render.so.1 is not a symbolic link

ldconfig: /usr/lib/libg15.so.1 is not a symbolic link

----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'libg15render.h' '/usr/include/libg15render.h'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/libg15render-1.1.1'
chmod: changing permissions of `conf15121.sh': Operation not permitted
chmod: changing permissions of `conf15121.file': Operation not permitted
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... no, using cp -p
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... chmod: changing permissions of `.': Operation not permitted
yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
chmod: changing permissions of `libtool': Operation not permitted
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... chmod: changing permissions of `.': Operation not permitted
yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
chmod: changing permissions of `libtool': Operation not permitted
checking for ranlib... (cached) ranlib
checking for daemon_log in -ldaemon... yes
checking for initLibG15 in -lg15... yes
checking for sin in -lm... yes
checking for pthread_mutex_init in -lpthread... yes
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking for linux/uinput.h... yes
checking for arpa/inet.h... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking for libg15.h... yes
checking for struct uinput_user_dev.id... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking for size_t... yes
checking whether gcc needs -traditional... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for strftime... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strerror... yes
configure: creating ./config.status
chmod: changing permissions of `./config.status': Operation not permitted
chmod: changing permissions of `conf19086.sh': Operation not permitted
chmod: changing permissions of `conf19086.file': Operation not permitted
config.status: creating Makefile
config.status: creating g15daemon/Makefile
config.status: creating libg15daemon_client/Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
Making all in libg15daemon_client
make[2]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT g15daemon_net.lo -MD -MP -MF ".deps/g15daemon_net.Tpo" -c -o g15daemon_net.lo g15daemon_net.c; \
        then mv -f ".deps/g15daemon_net.Tpo" ".deps/g15daemon_net.Plo"; else rm -f ".deps/g15daemon_net.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -MT g15daemon_net.lo -MD -MP -MF .deps/g15daemon_net.Tpo -c g15daemon_net.c  -fPIC -DPIC -o .libs/g15daemon_net.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -MT g15daemon_net.lo -MD -MP -MF .deps/g15daemon_net.Tpo -c g15daemon_net.c -o g15daemon_net.o >/dev/null 2>&1
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o libg15daemon_client.la -rpath /usr/lib -version-info 1:2:0 g15daemon_net.lo  -lpthread -lm -lg15 -ldaemon
gcc -shared  .libs/g15daemon_net.o  -lpthread -lm /usr/lib/libg15.so -L/usr/lib /usr/lib/libdaemon.so  -Wl,-soname -Wl,libg15daemon_client.so.1 -o .libs/libg15daemon_client.so.1.0.2
(cd .libs && rm -f libg15daemon_client.so.1 && cp -p libg15daemon_client.so.1.0.2 libg15daemon_client.so.1)
cp: preserving times for `libg15daemon_client.so.1': Operation not permitted
make[2]: *** [libg15daemon_client.la] Error 1
make[2]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
make: *** [all] Error 2
Making install in libg15daemon_client
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o libg15daemon_client.la -rpath /usr/lib -version-info 1:2:0 g15daemon_net.lo  -lpthread -lm -lg15 -ldaemon
rm -fr  .libs/libg15daemon_client.so.1 .libs/libg15daemon_client.so.1.0.2
gcc -shared  .libs/g15daemon_net.o  -lpthread -lm /usr/lib/libg15.so -L/usr/lib /usr/lib/libdaemon.so  -Wl,-soname -Wl,libg15daemon_client.so.1 -o .libs/libg15daemon_client.so.1.0.2
(cd .libs && rm -f libg15daemon_client.so.1 && cp -p libg15daemon_client.so.1.0.2 libg15daemon_client.so.1)
(cd .libs && rm -f libg15daemon_client.so && cp -p libg15daemon_client.so.1.0.2 libg15daemon_client.so)
ar cru .libs/libg15daemon_client.a  g15daemon_net.o
ranlib .libs/libg15daemon_client.a
creating libg15daemon_client.la
(cd .libs && rm -f libg15daemon_client.la && cp -p ../libg15daemon_client.la libg15daemon_client.la)
make[2]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libg15daemon_client.la' '/usr/lib/libg15daemon_client.la'
/usr/bin/install -c .libs/libg15daemon_client.so.1.0.2 /usr/lib/libg15daemon_client.so.1.0.2
(cd /usr/lib && { cp -p -f libg15daemon_client.so.1.0.2 libg15daemon_client.so.1 || { rm -f libg15daemon_client.so.1 && cp -p libg15daemon_client.so.1.0.2 libg15daemon_client.so.1; }; })
cp: `libg15daemon_client.so.1.0.2' and `libg15daemon_client.so.1' are the same file
(cd /usr/lib && { cp -p -f libg15daemon_client.so.1.0.2 libg15daemon_client.so || { rm -f libg15daemon_client.so && cp -p libg15daemon_client.so.1.0.2 libg15daemon_client.so; }; })
/usr/bin/install -c .libs/libg15daemon_client.lai /usr/lib/libg15daemon_client.la
/usr/bin/install -c .libs/libg15daemon_client.a /usr/lib/libg15daemon_client.a
ranlib /usr/lib/libg15daemon_client.a
chmod 644 /usr/lib/libg15daemon_client.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
ldconfig: /usr/lib/libg15render.so.1 is not a symbolic link

ldconfig: /usr/lib/libg15daemon_client.so.1 is not a symbolic link

ldconfig: /usr/lib/libg15.so.1 is not a symbolic link

----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

```

---

### Post by NZ-Wanderer on 2006-12-07
heres the rest of it

```

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'g15daemon_client.h' '/usr/include/g15daemon_client.h'
make[2]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/libg15daemon_client'
Making install in g15daemon
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/g15daemon'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT lcdclient_test.o -MD -MP -MF ".deps/lcdclient_test.Tpo" -c -o lcdclient_test.o lcdclient_test.c; \
        then mv -f ".deps/lcdclient_test.Tpo" ".deps/lcdclient_test.Po"; else rm -f ".deps/lcdclient_test.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o g15daemontest  lcdclient_test.o ../libg15daemon_client/libg15daemon_client.la -lpthread -lm -lg15 -ldaemon
mkdir .libs
gcc -g -O2 -o .libs/g15daemontest lcdclient_test.o  ../libg15daemon_client/.libs/libg15daemon_client.so -lpthread -lm /usr/lib/libg15.so /usr/lib/libusb.so /usr/lib/libdaemon.so
creating g15daemontest
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT g15_net.o -MD -MP -MF ".deps/g15_net.Tpo" -c -o g15_net.o g15_net.c; \
        then mv -f ".deps/g15_net.Tpo" ".deps/g15_net.Po"; else rm -f ".deps/g15_net.Tpo"; exit 1; fi
g15_net.c: In function ‘process_client_cmds’:
g15_net.c:126: warning: assignment from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT g15_uinput.o -MD -MP -MF ".deps/g15_uinput.Tpo" -c -o g15_uinput.o g15_uinput.c; \
        then mv -f ".deps/g15_uinput.Tpo" ".deps/g15_uinput.Po"; else rm -f ".deps/g15_uinput.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT utility_funcs.o -MD -MP -MF ".deps/utility_funcs.Tpo" -c -o utility_funcs.o utility_funcs.c; \
        then mv -f ".deps/utility_funcs.Tpo" ".deps/utility_funcs.Po"; else rm -f ".deps/utility_funcs.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT linked_lists.o -MD -MP -MF ".deps/linked_lists.Tpo" -c -o linked_lists.o linked_lists.c; \
        then mv -f ".deps/linked_lists.Tpo" ".deps/linked_lists.Po"; else rm -f ".deps/linked_lists.Tpo"; exit 1; fi
linked_lists.c: In function ‘lcdnode_remove’:
linked_lists.c:126: warning: comparison of distinct pointer types lacks a cast
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libg15daemon_client/    -g -O2 -MT gfx_primitives.o -MD -MP -MF ".deps/gfx_primitives.Tpo" -c -o gfx_primitives.o gfx_primitives.c; \
        then mv -f ".deps/gfx_primitives.Tpo" ".deps/gfx_primitives.Po"; else rm -f ".deps/gfx_primitives.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o g15daemon  g15_net.o g15_uinput.o utility_funcs.o main.o linked_lists.o gfx_primitives.o  -lpthread -lm -lg15 -ldaemon
gcc -g -O2 -o g15daemon g15_net.o g15_uinput.o utility_funcs.o main.o linked_lists.o gfx_primitives.o  -lpthread -lm /usr/lib/libg15.so /usr/lib/libusb.so /usr/lib/libdaemon.so
make[2]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/g15daemon'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'g15daemon' '/usr/sbin/g15daemon'
/usr/bin/install -c g15daemon /usr/sbin/g15daemon
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/g15daemon'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a/g15daemon'
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
make[2]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/doc/g15daemon-1.2.6a" || mkdir -p -- "/usr/share/doc/g15daemon-1.2.6a"
 /usr/bin/install -c -m 644 'FAQ' '/usr/share/doc/g15daemon-1.2.6a/FAQ'
 /usr/bin/install -c -m 644 'README.usage' '/usr/share/doc/g15daemon-1.2.6a/README.usage'
 /usr/bin/install -c -m 644 'README' '/usr/share/doc/g15daemon-1.2.6a/README'
 /usr/bin/install -c -m 644 'ChangeLog' '/usr/share/doc/g15daemon-1.2.6a/ChangeLog'
 /usr/bin/install -c -m 644 'TODO' '/usr/share/doc/g15daemon-1.2.6a/TODO'
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/share/doc/g15daemon-1.2.6a/AUTHORS'
 /usr/bin/install -c -m 644 'NEWS' '/usr/share/doc/g15daemon-1.2.6a/NEWS'
 /usr/bin/install -c -m 644 'LICENSE' '/usr/share/doc/g15daemon-1.2.6a/LICENSE'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 '././Documentation/g15daemon.1' '/usr/share/man/man1/g15daemon.1'
test -z "/usr/share/man/man3" || mkdir -p -- "/usr/share/man/man3"
 /usr/bin/install -c -m 644 '././Documentation/g15daemon_client_devel.3' '/usr/share/man/man3/g15daemon_client_devel.3'
make[2]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15daemon-1.2.6a'
chmod: changing permissions of `conf20263.sh': Operation not permitted
chmod: changing permissions of `conf20263.file': Operation not permitted
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for bison... no
checking for byacc... no
checking whether to enable FreeType2 support... checking for g15r_ttfLoad in -lg15render... yes
yes
checking for g15_send in -lg15daemon_client... yes
checking for g15r_initCanvas in -lg15render... yes
checking for pthread_create in -lpthread... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for sys/stat.h... (cached) yes
checking libg15.h usability... yes
checking libg15.h presence... yes
checking for libg15.h... yes
checking libg15render.h usability... yes
checking libg15render.h presence... no
configure: WARNING: libg15render.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: libg15render.h: proceeding with the compiler's result
checking for libg15render.h... yes
checking g15daemon_client.h usability... yes
checking g15daemon_client.h presence... yes
checking for g15daemon_client.h... yes
checking for an ANSI C-conforming const... yes
configure: creating ./config.status
chmod: changing permissions of `./config.status': Operation not permitted
chmod: changing permissions of `conf21406.sh': Operation not permitted
chmod: changing permissions of `conf21406.file': Operation not permitted
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15composer-3.0.2'
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -I/usr/include/freetype2 -MT g15composer.o -MD -MP -MF ".deps/g15composer.Tpo" -c -o g15composer.o g15composer.c; \
        then mv -f ".deps/g15composer.Tpo" ".deps/g15composer.Po"; else rm -f ".deps/g15composer.Tpo"; exit 1; fi
g15composer.c: In function ‘threadEntry’:
g15composer.c:123: warning: passing argument 1 of ‘fclose’ makes pointer from integer without a cast
g15composer.c:147: warning: passing argument 1 of ‘pthread_exit’ makes pointer from integer without a cast
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -I/usr/include/freetype2 -MT g15composer.tab.o -MD -MP -MF ".deps/g15composer.tab.Tpo" -c -o g15composer.tab.o g15composer.tab.c; \
        then mv -f ".deps/g15composer.tab.Tpo" ".deps/g15composer.tab.Po"; else rm -f ".deps/g15composer.tab.Tpo"; exit 1; fi
g15composer.y: In function ‘yyparse’:
g15composer.y:433: warning: pointer targets in passing argument 2 of ‘g15r_renderString’ differ in signedness
g15composer.y:450: warning: pointer targets in passing argument 2 of ‘g15r_renderString’ differ in signedness
g15composer.y:467: warning: pointer targets in passing argument 2 of ‘g15r_renderString’ differ in signedness
g15composer.y:490: warning: pointer targets in passing argument 2 of ‘g15r_renderString’ differ in signedness
g15composer.y:493: warning: pointer targets in passing argument 2 of ‘g15r_renderString’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -I/usr/include/freetype2 -MT g15composer.lex.o -MD -MP -MF ".deps/g15composer.lex.Tpo" -c -o g15composer.lex.o g15composer.lex.c; \
        then mv -f ".deps/g15composer.lex.Tpo" ".deps/g15composer.lex.Po"; else rm -f ".deps/g15composer.lex.Tpo"; exit 1; fi
g15composer.l: In function ‘yylex’:
g15composer.l:63: warning: assignment makes integer from pointer without a cast
gcc  -g -O2 -I/usr/include/freetype2   -o g15composer  g15composer.o g15composer.tab.o g15composer.lex.o  -lpthread -lg15render -lg15daemon_client
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15composer-3.0.2'
make[1]: Entering directory `/media/Go-Between/linux-g15/sources/sources/g15composer-3.0.2'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'g15composer' '/usr/bin/g15composer'
test -z "/usr/share/doc/g15composer-3.0.2" || mkdir -p -- "/usr/share/doc/g15composer-3.0.2"
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/share/doc/g15composer-3.0.2/AUTHORS'
 /usr/bin/install -c -m 644 'ChangeLog' '/usr/share/doc/g15composer-3.0.2/ChangeLog'
 /usr/bin/install -c -m 644 'COPYING' '/usr/share/doc/g15composer-3.0.2/COPYING'
 /usr/bin/install -c -m 644 'NEWS' '/usr/share/doc/g15composer-3.0.2/NEWS'
 /usr/bin/install -c -m 644 'README' '/usr/share/doc/g15composer-3.0.2/README'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 '././doc/g15composer.1' '/usr/share/man/man1/g15composer.1'
make[1]: Leaving directory `/media/Go-Between/linux-g15/sources/sources/g15composer-3.0.2'
john@kubuntu:/media/Go-Between/linux-g15/sources/sources$  
```

---

### Post by Aneurysm9 on 2006-12-07
Looks like everything is ok.  Those errors might happen if the user building the packages doesn't own the files it's building from.  It looks like everything built and installed fine though.

---

### Post by NZ-Wanderer on 2006-12-07
Ummm so what do I do now?? - or don't I have to do anything else??

Anyway, thanks very much, that's the very first thing I have ever built from source, usually I try to find something in the package managers... :)

> **Aneurysm9 said:**
> Looks like everything is ok.  Those errors might happen if the user building the packages doesn't own the files it's building from.  It looks like everything built and installed fine though.

---

### Post by Aneurysm9 on 2006-12-07
Now you can start g15daemon (sudo g15daemon) and g15composer (g15composer ~/g15lcd&) and start finding things to do with the lcd.  You can get lcdproc,  which you'll have to build from source, but it should be easy now that you've done it before.  Same thing, download, extract, configure, make, install.  The configure step is the only one that really changes.  For lcdproc, drop the --enable-ttf and add --enable-drivers=g15 since we want to build the g15 driver.  Then start LCDd and lcdproc.  Check out [http://lcdproc.omnipotent.net/](http://lcdproc.omnipotent.net/)

---

### Post by NZ-Wanderer on 2006-12-07
Ummmm I still got the time displayed on the G15 (withoput starting anything)... does that mean it starting automatically without me telling it to??

will see if I can do the other stuff you mentioned and will check out that web site..

Thanks again for you help and your patience :)

> **Aneurysm9 said:**
> Now you can start g15daemon (sudo g15daemon) and g15composer (g15composer ~/g15lcd&) and start finding things to do with the lcd.  You can get lcdproc,  which you'll have to build from source, but it should be easy now that you've done it before.  Same thing, download, extract, configure, make, install.  The configure step is the only one that really changes.  For lcdproc, drop the --enable-ttf and add --enable-drivers=g15 since we want to build the g15 driver.  Then start LCDd and lcdproc.  Check out [http://lcdproc.omnipotent.net/](http://lcdproc.omnipotent.net/)

---

### Post by Aneurysm9 on 2006-12-08
You can restart g15daemon to be sure you're running the current version.  

sudo killall g15daemon && sudo g15daemon

---

### Post by NZ-Wanderer on 2006-12-08
Thanks for that, I had to alter the time in Kubuntu cause something had made it go wrong, and couldn't figure out how to get the time changed on the keyboard, your kill command fixed it perfectly :) :)

I got this when I did it.

john@kubuntu:/$ sudo killall g15daemon && sudo g15daemon
Password:
Process 4805 died: No such process; removing PID file. (/var/run/g15daemon.pid)
john@kubuntu:/$

> **Aneurysm9 said:**
> You can restart g15daemon to be sure you're running the current version.  
sudo killall g15daemon && sudo g15daemon

---

### Post by Aneurysm9 on 2006-12-08
Looks like g15daemon had died, but was still displaying the clock.  That can happen if g15daemon doesn't exit cleanly and with older versions of libg15/g15daemon even when they did exit cleanly.  Now, when g15daemon exits, you should see the logitech logo again.

---

### Post by NZ-Wanderer on 2006-12-08
Hmmm, I just did it again to see what happens, and got the following:

john@kubuntu:~$ sudo killall g15daemon && sudo g15daemon
g15daemon: no process killed
john@kubuntu:~$

Does this mean I did something wrong in my instalation yesterday??

I did try to put the clock on that was mentioned a few pages back, but got lots of errors cause I didn't have the right files (I concluded that it had been done for edgy) - could that have maybe stuffed something up?

Hmmm looks like the clock has stopped on the keyboard, might have to reboot the computer...

Soon as I get the clock working properly I want to see if I can get the G keys working, cause I got big plans for those (saving lots of typing in commands into terminal etc :) :)

Ohwell, off to reboot computer to get clock working again...

On a side note: it seems kinda wierd that I get the clock coming up on the keyboard, but I have never actually typed in the commands to get it to auto start or anything, it just appears..

Regards - John...

Update, rebooted computer, and up came the G15 for Linux logo and then the time even before I had a chance to type in my password to login :) :)

---

### Post by Aneurysm9 on 2006-12-08
> Update, rebooted computer, and up came the G15 for Linux logo and then the time even before I had a chance to type in my password to login

Cool.  Does that mean everything's working for you?  The G keys probably won't be useful for much except extra keys to bind to window manager functions right now, but mlampard is working on macro support for the new version of g15daemon.  Not sure when it'll be out, still got to get all the features in and then some time for bughunting, but it's coming.

---

### Post by NZ-Wanderer on 2006-12-09
Well I took the plunge and updated today to Kubuntu Edgy.. - the first thing I did after rebooting was grab your little clock to see if it would install now...
Thank you very much, the clock looks and works great on my Keyboard :) :)

> **rasta_freak said:**
> Hi everyone. My small tribute for g15 packages.
I'm using g15daemon_1.2.1 on Kubuntu 6.10.
This is nice clock client for G15. Please try it and tell...

---

### Post by NZ-Wanderer on 2006-12-09
Yup, everything seems to be great now.. - I rebooted after loading that little clock I mentioned in the previous thread, and it loaded up before I had the chance to type in my password on login (saw the  BIG clock for a second before the other clock came up)

I get the sign "g15composer" come up when I load Amarok, but when I start a mp3 the g15 just goes blank, but I not worrying about that at present...

I'll be nice and patient and not ask about the G keys since you say it's on the way sometime :mrgreen: 

Thanks for all the help, it's much appreciated..

> **Aneurysm9 said:**
> Cool.  Does that mean everything's working for you?  The G keys probably won't be useful for much except extra keys to bind to window manager functions right now, but mlampard is working on macro support for the new version of g15daemon.  Not sure when it'll be out, still got to get all the features in and then some time for bughunting, but it's coming.

---

### Post by ChadMC on 2006-12-11
I recently reinstalled Ubuntu, and I'm trying to get lcdproc working again. I'm compiling it from source. And I'm doing a ./configure --enable-drivers=g15

But when I try to run LCDd, I get this error:
```
Could not open driver module server/drivers/g15.so: server/drivers/g15.so: cannot open shared object file: No such file or directory
Driver [g15] binding failed
Could not load driver g15
There is no output driver
Critical error while initializing, abort.
```

I've tried this multiple times with no luck. I've even tried the CVS nightly build. Same result. What am I doing wrong? There is no g15.so file on my computer.

---

### Post by Aneurysm9 on 2006-12-11
Check the driver path in /etc/LCDd.conf (/usr/local/etc/LCDd.conf if you didn't specify --prefix=/usr).  I have  DriverPath=/usr/local/lib/lcdproc/ because I used the default --prefix of /usr/local.

---

### Post by Giblet5 on 2006-12-12
I just got my G15 and I've read through every posting. Ever. Anywhere.

My g15daemon is running (no errors).

My g15composer is running with the default /var/run/g15composer fifo.

I have rebooted (having modified /etc/modules to load uinput).

My g15 lcd displays the Logitech logo and nothing else.

ps -ef | grep g15
shows me that the daemon and composer are running.

Echoing commands out to the fifo causes no errors and doesn't change the LCD display.

It works fine in Vista.

Any ideas?

---

### Post by ChadMC on 2006-12-12
> **Aneurysm9 said:**
> Check the driver path in /etc/LCDd.conf (/usr/local/etc/LCDd.conf if you didn't specify --prefix=/usr).  I have  DriverPath=/usr/local/lib/lcdproc/ because I used the default --prefix of /usr/local.

It's like it's not creating any drivers folder anywhere. I tried --prefix=/usr this time and there is no /usr/lib/lcdproc folder. Doing a search for g15.so turns up nothing.. I'm not sure what's going on, but it's not installing it correctly. My DriverPath defaults to server/drivers in the LCDd.conf

edit: okay there is a /usr/lib/lcdproc folder but it's empty.

---

### Post by Aneurysm9 on 2006-12-12
Do you get anything in your logs that might be helpful?  What's /proc/bus/usb/devices have to say for itself?

---

### Post by Aneurysm9 on 2006-12-12
ChadMC,

server/drivers won't work for DriverPath, gotta change it to the actual path.   try doing "sudo make install" in the lcdproc-5.1/server/drivers directory to see if that installs the driver.  If not, check to see if g15.so is even being created in the build dir.

---

### Post by ChadMC on 2006-12-12
> **Aneurysm9 said:**
> ChadMC,

server/drivers won't work for DriverPath, gotta change it to the actual path.   try doing "sudo make install" in the lcdproc-5.1/server/drivers directory to see if that installs the driver.  If not, check to see if g15.so is even being created in the build dir.

It didn't do anything. I tried doing a --enable-drivers=all and then did a 'sudo make install' inside the server/drivers folder, and it installed a bunch of drivers, but it didn't install the g15.so driver...

EDIT: okay, here's the problem.. I just don't know how to fix it. Check this out..
```
configure: checking for which drivers to compile...
checking g15daemon_client.h usability... no
checking g15daemon_client.h presence... no
checking for g15daemon_client.h... no
configure: WARNING: The g15 driver needs g15daemon_client.h
checking libg15render.h usability... no
checking libg15render.h presence... no
checking for libg15render.h... no
configure: WARNING: The g15driver needs libg15render.h

```

ONE MORE EDIT:
I fixed it! I just needed some of the dev packages installed that are included in the first post on here.

---

### Post by Giblet5 on 2006-12-12
> **Aneurysm9 said:**
> Do you get anything in your logs that might be helpful?  What's /proc/bus/usb/devices have to say for itself?

I dunno if you meant me, or someone else, so I'll reply!

/proc/bus/usb/devices has this on the G15:
T:  Bus=05 Lev=03 Prnt=06 Port=00 Cnt=01 Dev#=  8 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c221 Rev= 1.70
S:  Manufacturer=Logitech
S:  Product=Logitech Gaming Keyboard
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

---

### Post by Aneurysm9 on 2006-12-13
ChadMC, yeah, sorry.  I use Gentoo so I tend to forget that some people need the dev packages to get things to work right.

Giblet, There should be another one with ProdID c222, can you post that segment too?

---

### Post by Giblet5 on 2006-12-13
[QUOTE=Giblet, There should be another one with ProdID c222, can you post that segment too?[/QUOTE]

Sure, and I really appreciate the help.

T:  Bus=05 Lev=02 Prnt=03 Port=02 Cnt=01 Dev#=  6 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c223 Rev= 1.03
S:  Manufacturer=Logitech
S:  Product=Logitech G15 Keyboard
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=05 Lev=03 Prnt=06 Port=00 Cnt=01 Dev#=  8 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c221 Rev= 1.70
S:  Manufacturer=Logitech
S:  Product=Logitech Gaming Keyboard
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=05 Lev=03 Prnt=06 Port=03 Cnt=02 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c222 Rev= 1.03
S:  Manufacturer=G15 Keyboard
S:  Product=G15 Keyboard
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbfs
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=1ms
E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=1ms

T:  Bus=05 Lev=02 Prnt=03 Port=03 Cnt=02 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c506 Rev=16.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 50mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

---

### Post by Aneurysm9 on 2006-12-13
Ok, looks good so far.  It looks like libg15 has attached to the device.  Is there anything in /var/log/messages from g15daemon?

---

### Post by Giblet5 on 2006-12-14
> **Aneurysm9 said:**
> Ok, looks good so far.  It looks like libg15 has attached to the device.  Is there anything in /var/log/messages from g15daemon?

kernel: [17195605.028000] usb 1-3.3.4: usbfs: process 29901 (g15daemon) did not claim interface 0 before use

Hmmm. That would be correct; g15daemon starts long after the interface is in use... And?

(Wish I had time to just learn how the USB subsystem works...)

---

### Post by Aneurysm9 on 2006-12-14
I haven't seen that one before.  Try asking mlampard over at the g15daemon forums on sf.net.  He'll probably know more about why it might do that than me.  [http://sourceforge.net/forum/?group_id=172261](http://sourceforge.net/forum/?group_id=172261)

---

### Post by mlampard on 2006-12-14
"process 29901 (g15daemon) did not claim interface 0 before use" is a bug in g15daemon <=1.2.6a, which has been fixed in the SVN versions.  The actual cause is likely that libusb couldnt access the /proc/bus/usb/ mountpoint.  If you check the contents of that directory, does it contain anything?  If not, you'll have to mount it manually:

mount -t usbfs none /proc/bus/usb

Please let me know if that doesnt fix it for you.
Cheers.

---

### Post by Giblet5 on 2006-12-15
> **mlampard said:**
> "process 29901 (g15daemon) did not claim interface 0 before use" is a bug in g15daemon <=1.2.6a, which has been fixed in the SVN versions.  The actual cause is likely that libusb couldnt access the /proc/bus/usb/ mountpoint.  If you check the contents of that directory, does it contain anything?  If not, you'll have to mount it manually:

mount -t usbfs none /proc/bus/usb

Please let me know if that doesnt fix it for you.
Cheers.

Thanks for the help Aneurism9!

Yes, it does, mlampard:

~$ ls /proc/bus/usb
001  002  003  004  005  devices

Testing whether it exists at the point where g15daemon starts, I verified the mount, ran g15daemon -k and then started g15daemon again. Same message in /var/log/messages and no change to the g15's LCD (Logitech logo).

Is that fix in the svn for g15daemon, or for libg15?

Do you have the subversion urls handy for those newer bits? I'll go ahead and build them anew.

Current:
G15Daemon version 1.2.6a - Loaded & Running
compiled with libg15 version 1.100

Many thanks folks!

---

### Post by mlampard on 2006-12-15
Giblet5:
Use libg15-1.1.1 or libg15 svn version available via
svn co https://g15tools.svn.sourceforge.net/svnroot/g15tools/trunk/libg15 libg15

Current g15daemon 1.2 svn version is available from
svn co https://g15daemon.svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon g15daemon

Once compiled and installed, run g15daemon with the --debug option, and it should/will tell us what is wrong.

---

### Post by Giblet5 on 2006-12-15
> **mlampard said:**
> Giblet5:
Use libg15-1.1.1 or libg15 svn version available via
svn co [https://g15tools.svn.sourceforge.net/svnroot/g15tools/trunk/libg15](https://g15tools.svn.sourceforge.net/svnroot/g15tools/trunk/libg15) libg15

Current g15daemon 1.2 svn version is available from
svn co [https://g15daemon.svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon](https://g15daemon.svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon) g15daemon

Once compiled and installed, run g15daemon with the --debug option, and it should/will tell us what is wrong.

Thanks.

G15Daemon version 1.2svn - Loaded & Running
compiled with libg15 version 1.100

I verified that libg15.so was 1.1.1 but the version still shows up as 1.100. Without looking into it too deeply, I suspect this line:
#define LIBG15_VERSION 1100
in libg15.h

I still have the Logitech logo, and commands to the g15composer fifo do nothing. I haven't rebooted yet...

The only message in /var/log/messages was:
kernel: [17193667.408000] input: G15 Extra Keys as /c
lass/input/input8

I'll reboot when I do lunch.

Thanks again!

Update:
No joy. The --debug option doesn't help much; the output is:
root@puddles:/# g15daemon --debug
g15daemon 1.2svn loaded

And it waits for exit/interrupt.

---

### Post by mlampard on 2006-12-15
> **Giblet5 said:**
> 
G15Daemon version 1.2svn - Loaded & Running
compiled with libg15 version 1.100

I verified that libg15.so was 1.1.1 but the version still shows up as 1.100. Without looking into it too deeply, I suspect this line:
#define LIBG15_VERSION 1100
in libg15.h

Yep, that looks likely.

libg15 has debugging as well, the current version needs a define to enable it. Would you uncomment the #define DEBUG at the top of libg15.c in the libg15 directory, and make && make install?  Running g15daemon --debug will hopefully have a bit more output, if the problem is there.  Generally speaking, both libg15 and g15daemon only display debugging messages if a problem was detected, so little or no output can be regarded as a good thing, in most cases.

What versions of the kernel & libusb are you running?

---

### Post by Giblet5 on 2006-12-18
> **mlampard said:**
> Yep, that looks likely.

libg15 has debugging as well, the current version needs a define to enable it. Would you uncomment the #define DEBUG at the top of libg15.c in the libg15 directory, and make && make install?  Running g15daemon --debug will hopefully have a bit more output, if the problem is there.  Generally speaking, both libg15 and g15daemon only display debugging messages if a problem was detected, so little or no output can be regarded as a good thing, in most cases.

What versions of the kernel & libusb are you running?

I'm on Edgy (2.6.10-17).

The problem appears to be caused by plugging the USB cable from my KVM into an external hub. I moved the KVM cable to the back of the PC (2nd USB 2.0 controller) and all is well. The KVM is, itself, a USB hub. Apparently, that doesn't work (Port->hub->hub->kbd/hub).

I added a root cron job that restarts the daemon every five minutes. Now, when I switch to another system and switch back, it eventually starts displaying stats again.

That could be corrected in g15daemon if there were some way to detect the usb disconnect notifications. I can see them in dmesg.

Thanks for all the help, mlampard. My laziness(using the hub vs plugging it into an unused USB controller) got the best of me. Again.

---

### Post by mlampard on 2006-12-18
ok, thanks for the info Giblet5.  Are your hubs/kvm self-powered? ie, do they have a power brick plugged into them?  The g15 as been known to have problems when plugged into kvm switches (even on windows, apparently), and it needs a reasonable amount of power, which may account for some of the weirdness you're seeing :)

Current libg15 & g15daemon svn versions (as of yesterday) have basic support for automatically reconnecting the keyboard on disconnect - perhaps you might find that a better solution than the cron job.

---

### Post by Giblet5 on 2006-12-18
> **mlampard said:**
> ok, thanks for the info Giblet5.  Are your hubs/kvm self-powered? ie, do they have a power brick plugged into them?  The g15 as been known to have problems when plugged into kvm switches (even on windows, apparently), and it needs a reasonable amount of power, which may account for some of the weirdness you're seeing :)

Current libg15 & g15daemon svn versions (as of yesterday) have basic support for automatically reconnecting the keyboard on disconnect - perhaps you might find that a better solution than the cron job.

Yeah. I have a 2A brick hanging off the KVM.  The keyboard won't work at all without it.  The hub and the LCD in the G15 appear to be the culprits.  The G15, when you enable the hub, draws 400ma, and that isn't even powering the LCD or LEDs yet.

Wait til they release that color LCD model... Yikes.

---

### Post by NZ-Wanderer on 2006-12-18
I have a little problem, I had to reinstall Edgy and therefore everything else...
I followed all the steps I did last time, but when I type sudo g15daemon I get:

john@Kubuntu:~$ sudo g15daemon
Password:
An Error Occurred - 3 : ( Unable to configure the linux kernel UINPUT driver ) received
john@Kubuntu:~$

What have I done wrong please???

---

### Post by mlampard on 2006-12-19
NZ-Wanderer: have you loaded the uinput driver into the kernel?  Try running "modprobe uinput" as root, then running g15daemon again.

---

### Post by NZ-Wanderer on 2006-12-19
Thank you, that worked perfectly :) :) - I now have the big clock again....

> **mlampard said:**
> NZ-Wanderer: have you loaded the uinput driver into the kernel?  Try running "modprobe uinput" as root, then running g15daemon again.

---

### Post by gbesso on 2006-12-26
Is it just me or does this not work with the 2.6.19.1 kernel?

---

### Post by mlampard on 2006-12-26
Versions of libg15 prior to 1.1.1 have problems with kernels later than 2.6.17 - are you using an earlier version?  If you're running the latest version, please post the output of g15daemon -d to the g15daemon forums at sourceforge.

---

### Post by KClaisse on 2006-12-27
Well my system recently dumped and now I find myself reinstalling this again. ](*,) 

Much easier this time though.
I got the scripts to start at boot and g15composer and g15daemon are working just fine.

The only problem I have now, is the amarok script doesn't show the artist, album, or track name. I thought it was supposed to. 

[This is the script I used](http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/tags/g15composer-3.0/examples/amarok-g15-dcop_cli.pl?revision=219)

EDIT:
Also, the script gives this error:
```

 Error: syntax error, unexpected T_NUMBER
Error: syntax error, unexpected T_NUMBER, expecting T_STRING or T_NEWLINE

```

---

### Post by Aneurysm9 on 2006-12-27
Kclaisse:

That looks like the script that shipped with g15composer-3.0.  it's been updated a bit since then.  Pleas try the version from svn head here [http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl?revision=207](http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl?revision=207).  Also, on ubuntu you need to modify the font path by adding "truetype/" between "...fonts/" and "ttf-bitstream..." at line 23.  That's probably why it's not showing the artist or album.  Not sure about those errors, unfortunately g15composer's error handling isn't very informative right now, I'll look into making it give line numbers or something like that.

---

### Post by Spatulas on 2007-01-03
Hey, I compiled everything with ttf support (./configure --enable-ttf), but I still can't get ttf fonts to display.  Can anyone help?

---

### Post by Aneurysm9 on 2007-01-03
Do you get any error messages when you attempt to print with a ttf font?

---

### Post by Spatulas on 2007-01-03
> **Aneurysm9 said:**
> Do you get any error messages when you attempt to print with a ttf font?

I'm not sure how I would tell if I got any errors, as the script that's trying to use the fonts automatically starts g15daemon for me, and is a amarok plugin.

---

### Post by Aneurysm9 on 2007-01-03
You can comment out the code that starts g15composer in the script and start g15composer manually in a terminal window before you start the script.  That should let you see any errors in the terminal window.  Which amarok script are you trying to use?

---

### Post by Spatulas on 2007-01-03
> **Aneurysm9 said:**
> You can comment out the code that starts g15composer in the script and start g15composer manually in a terminal window before you start the script.  That should let you see any errors in the terminal window.  Which amarok script are you trying to use?

I'm using an amalgamation of the latest script and revision 158 of the script from here:
[http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl](http://g15tools.svn.sourceforge.net/viewvc/*checkout*/g15tools/trunk/g15composer/examples/amarok-g15-dcop_cli.pl)
Also modified it a bit.  Here's the thing though; if I don't start g15composer EXACTLY the way I do in the script (I have it run a custom sh script) it doesn't work with the pipe correctly, so I can't see and errors.  I'm playing with it, but no luck so far.

---

### Post by Spatulas on 2007-01-03
Scratch that, got it working outside of the script.  No errors that I could see.

EDIT: Erm, by got it working, I mean I got the g15composer runing outside of the script.  Still no fonts.

EDIT2: Oops.  It seems that my install has my truetype fonts in a different location than what is specified in the script.  Changed the path to thefont, and all worked.  Thanks for the help.

---

### Post by PhilippHD on 2007-01-09
My problem sounds pretty similar.
When runnign amarok the lcd shows the track progress, total track length and the progress bar. Everything else is missing. The font-path is specified correctly.
When using g15composer and the echo-command I can write stuff on the display. Clock is working too.

I got, made and (force) installed DCOP::Amarok::Player via cpan as root. Still I'm not sure it's configured correctly. There's nowhere in amarok where i can find and activate it. Also when running test DCOP::Amarok::Player in cpan it tells me it's "NOT OK".
On the other hand, the track-progress can be displayed, so this information has to come from somewhere, too.

Here's the script I'm currently using: (last changed 9. Oct. 2006)
```

#!/usr/bin/perl -w

use strict;
use threads;
use threads::shared;

my $pipe = "$ENV{HOME}/.g15amaroklcdpipe";

my $mknod = system("mknod $pipe p");

my $G15Cpid : shared = open(G15COMPOSER, "| g15composer $pipe");

my $vol : shared = `dcop amarok player getVolume`;
chomp $vol;
my $tmpStatus = `dcop amarok player status`;
chomp $tmpStatus;
my $status  :  shared = ( $tmpStatus > 1 ) ? 1 : 0;

open(PIPE, ">>$pipe");
print PIPE "FL 0 10 \"/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf\"\n";

sub volUpdate {
	print PIPE "PC 0\n";
	print PIPE "TO 0 10 2 1 \"Volume\"\n";
	print PIPE "DB 3 27 157 35 2 $vol 100 3\n";
}

while($status == 0) {
	$tmpStatus = `dcop amarok player status`;
	$status = ( $tmpStatus > 1 ) ? 1 : 0;
	sleep 1;
}

my $artist : shared = `dcop amarok player artist`;
my $title : shared = `dcop amarok player title`;
my $album : shared = `dcop amarok player album`;
my $trackTotalSecs : shared = `dcop amarok player trackTotalTime`;
my $trackCurSecs : shared = `dcop amarok player trackCurrentTime`;
my $trackTotalTime : shared = `dcop amarok player totalTime`;
my $trackCurTime : shared = `dcop amarok player currentTime`;
chomp $artist;
chomp $title;
chomp $album;
chomp $trackTotalSecs;
chomp $trackCurSecs;
chomp $trackTotalTime;
chomp $trackCurTime;

&initScreen();

$SIG{TERM} = \&bye;

my $progressThread = threads->create(\&progress);
$progressThread->detach();

while(1) {
	$_ = <STDIN>;
	chomp $_;
	if ( /trackChange/ ) {
		$artist = `dcop amarok player artist`;
		$title = `dcop amarok player title`;
		$album = `dcop amarok player album`;
		$trackTotalSecs = `dcop amarok player trackTotalTime`;
		$trackTotalTime = `dcop amarok player totalTime`;
		$trackCurSecs = `dcop amarok player trackCurrentTime`;
		$trackCurTime = `dcop amarok player currentTime`;
		chomp $artist;
		chomp $title;
		chomp $album;
		chomp $trackTotalSecs;
		chomp $trackCurSecs;
		chomp $trackTotalTime;
		chomp $trackCurTime;
		initScreen();
		$artist = `dcop amarok player artist`;
		$title = `dcop amarok player title`;
		$album = `dcop amarok player album`;
		$trackTotalSecs = `dcop amarok player trackTotalTime`;
		$trackTotalTime = `dcop amarok player totalTime`;
		$trackCurSecs = `dcop amarok player trackCurrentTime`;
		$trackCurTime = `dcop amarok player currentTime`;
		chomp $artist;
		chomp $title;
		chomp $album;
		chomp $trackTotalSecs;
		chomp $trackCurSecs;
		chomp $trackTotalTime;
		chomp $trackCurTime;
		initScreen();
	} elsif ( /engineStateChange/ ) {
                if( /playing/ ) {
                        $status = 1;
			initScreen();
                } elsif ( /pause/ ) {
                        $status = 0;
                } else {
                        $status = 0;
                }
        } elsif( /volumeChange/ ){
                m/: (\d+)/;
                $vol = $1;
		$status = 0;
		&volUpdate();
		$status = 1;
        }
	exit if( /exit/ );
	&bye() if( /kill/ );
}

sub initScreen {
	print PIPE "PC 0\n";
	print PIPE "DR 0 0 159 43 1 1\n";
	print PIPE "DR 3 22 157 40 1 0\n";
	print PIPE "PB 3 22 157 24 0\n";
	print PIPE "FP 0 15 0 0 0 1 \"$artist\"\n";
	print PIPE "FP 0 9 0 15 0 1 \"$title\"\n";
	print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
	print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
}

sub progress {
	while(1) {
		if($status > 0) {
			$trackCurSecs = `dcop amarok player trackCurrentTime`;
			$trackCurTime = `dcop amarok player currentTime`;
			chomp $trackCurSecs;
			chomp $trackCurTime;
			print PIPE "PB 5 27 155 35 0 1 1\n";
			print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
			print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
		} elsif($status == -1) {
			return;
		}
		sleep 1;
	}
}
	
sub bye {
	$status = -1;
	sleep 2;
	print PIPE "PC 0\n";
	system("kill 15 $G15Cpid");
	close(PIPE);
	close(G15COMPOSER);
	$mknod = system("rm $pipe");
	exit 0;
}


```

Hope, you guys can help me out.
Thanks in advance.

---

### Post by sgleo87 on 2007-01-13
I installed the g15daemon a few weeks ago and everything is running fine. Now I decided it would be nice if I could get the display to show tracks I play in amarok so I did a search in the forums and arrived at this thread. I followed the instructions on the first page and downloaded the amarok-g15-dcop_cli.ubuntu.amarokscript.tar.gz and installed the script in amarok and ran in. Unfortunately even after an hour or so of playing music nothing shows up in my LCD display besides the clock from the g15daemon. Is there any other way to get it working or did I screw up somewhere? Help! :cry:

---

### Post by Jeff59 on 2007-01-13
sgleo87:  try this from earlier in the thread 

> Try it this way instead: g15composer pipe &
so that it will go to the background. You can then echo commands to the pipe, such as: echo 'TL "Hello World"' > pipe.  

I also have 2 problems with Amaork 

1) I get the progress bar in the LCD screen but no song titles .

2) This is the most madding.  I can play MP# and see them no problem but when I put an Audio CD in it won't read it.

Any one who can tell me what I'm doing wrong would make my day.  Thanks

---

### Post by Jeff59 on 2007-01-15
I also have 2 problems with Amaork and G15

1) I get the progress bar in the LCD screen but no song titles .

2) This is the most madding. I can play MP3 and see them no problem but when I put an Audio CD in it won't read it.


Any one who can tell me what I'm doing wrong would make my day. Thanks

I also have figuered out an easy way of using the G-keys utilizing Xbinding if anyones interested.

---

### Post by drdnl on 2007-01-15
1) You didnt fix truetype, search through this topic with "truetype" and you'll find your answer. Think its also mentioned in the txt that coems with your amarokscript. (sorry, lazy, fixing my own beryl problems right now :))

2) Waaaaaay off topic, no idea, sorry... Try a different thread.

---

### Post by NZ-Wanderer on 2007-01-15
You found a way to use the G keys??????????

Now that would be great to know, I been wanting to setup G keys to automatically put commands into Terminal.. :)
Wish I could help you with your display problems, but alas I still can't get the clock to come up automatically when I load Kubuntu, so I no help to you...

> **Jeff59 said:**
> I also have 2 problems with Amaork and G15
1) I get the progress bar in the LCD screen but no song titles .
2) This is the most madding. I can play MP3 and see them no problem but when I put an Audio CD in it won't read it.
Any one who can tell me what I'm doing wrong would make my day. Thanks
I also have figuered out an easy way of using the G-keys utilizing Xbinding if anyones interested.

---

### Post by Jeff59 on 2007-01-16
NZ-Wanderer  Here is the information you requested on programing the G-keys

[HTML]How to set up your “G” keys or another Keys you want to bind a command or string to.

1.System >Administration>Synaptic Manage   Select (xbindkeys) and (xbindkeys-config) Install

2.System >Preferences>Sessions>Start Programs  -Add (xbindkeys) command to startup

3.Create empty file with text editor and name it “.xbindkeysrc” store it in your home /your name folder

4.ctl>Shift>Backspace

5.Open terminal and type “sudo  xbindkeys-config”

6.This will open up an editor that will find your keys and build the command, it stores the information in the file we just created.  Remember to use Save&Apply&Exit before closing

You now can program your keys to anthing.  Good Luck[/HTML]

Now I hope someone can help me with getting the LED showing the text from songs in Amorok.  I recompiled with the text option and still all I see is the status bar and song length.

I'm starting to wonder if this really works.

---

### Post by drdnl on 2007-01-16
Ok, assuming you have the [latest]("http://ubuntuforums.org/showpost.php?p=1858582&postcount=157") version of all the various components installed (follow the howto: for order in which to install) 

Assuming you are running Ubuntu,
Assuming you have g15daemon running and g15composer with arguments /usr/bin/g15composer -b /var/run/g15composer
Assuming you see a big clock on your display

This should work: 

```
#!/usr/bin/perl -w

use strict;
use threads;
use threads::shared;

my $pipe = "$ENV{HOME}/.g15amaroklcdpipe";

my $rmmknod = system("rm $pipe");
my $mknod = system("mknod $pipe p");

my $G15Cpid : shared = open(G15COMPOSER, "| g15composer $pipe");

my $vol : shared = `dcop amarok player getVolume`;
chomp $vol;
my $tmpStatus = `dcop amarok player status`;
chomp $tmpStatus;
my $status  :  shared = ( $tmpStatus > 1 ) ? 1 : 0;

#open(CPIPE, ">>$controlPipe");
#unlink $pipe;
#print CPIPE "SN \"$pipe\"\n";
#close(CPIPE);

open(PIPE, ">>$pipe");
print PIPE "FL 0 10 \"/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf\"\n";

sub volUpdate {
	print PIPE "PC 0\n";
	print PIPE "TO 0 10 2 1 \"Volume\"\n";
	print PIPE "DB 3 27 157 35 2 $vol 100 3\n";
	print PIPE "MC 1\n";
}

while($status == 0) {
	$tmpStatus = `dcop amarok player status`;
	$status = ( $tmpStatus > 1 ) ? 1 : 0;
	sleep 1;
}

my $artist : shared = `dcop amarok player artist`;
my $title : shared = `dcop amarok player title`;
my $album : shared = `dcop amarok player album`;
my $trackTotalSecs : shared = `dcop amarok player trackTotalTime`;
my $trackCurSecs : shared = `dcop amarok player trackCurrentTime`;
my $trackTotalTime : shared = `dcop amarok player totalTime`;
my $trackCurTime : shared = `dcop amarok player currentTime`;
chomp $artist;
chomp $title;
chomp $album;
chomp $trackTotalSecs;
chomp $trackCurSecs;
chomp $trackTotalTime;
chomp $trackCurTime;

&initScreen();

$SIG{TERM} = \&bye;

my $progressThread = threads->create(\&progress);
$progressThread->detach();

while(1) {
	$_ = <STDIN>;
	chomp $_;
	if ( /trackChange/ ) {
		$artist = `dcop amarok player artist`;
		$title = `dcop amarok player title`;
		$album = `dcop amarok player album`;
		$trackTotalSecs = `dcop amarok player trackTotalTime`;
		$trackTotalTime = `dcop amarok player totalTime`;
		$trackCurSecs = `dcop amarok player trackCurrentTime`;
		$trackCurTime = `dcop amarok player currentTime`;
		chomp $artist;
		chomp $title;
		chomp $album;
		chomp $trackTotalSecs;
		chomp $trackCurSecs;
		chomp $trackTotalTime;
		chomp $trackCurTime;
		initScreen();
		$artist = `dcop amarok player artist`;
		$title = `dcop amarok player title`;
		$album = `dcop amarok player album`;
		$trackTotalSecs = `dcop amarok player trackTotalTime`;
		$trackTotalTime = `dcop amarok player totalTime`;
		$trackCurSecs = `dcop amarok player trackCurrentTime`;
		$trackCurTime = `dcop amarok player currentTime`;
		chomp $artist;
		chomp $title;
		chomp $album;
		chomp $trackTotalSecs;
		chomp $trackCurSecs;
		chomp $trackTotalTime;
		chomp $trackCurTime;
		initScreen();
		bringToFront();
	} elsif ( /engineStateChange/ ) {
                if( /playing/ ) {
                        $status = 1;
			initScreen();
                } elsif ( /pause/ ) {
                        $status = 0;
                } else {
                        $status = 0;
                }
        } elsif( /volumeChange/ ){
                m/: (\d+)/;
                $vol = $1;
		$status = 0;
		&volUpdate();
		$status = 1;
        }
	exit if( /exit/ );
	&bye() if( /kill/ );
}

sub bringToFront {
	print PIPE "MP 0\n";
	sleep 3;
	print PIPE "MP 2\n";
}

sub initScreen {
	print PIPE "PC 0\n";
	print PIPE "DR 0 0 159 43 1 1\n";
	print PIPE "DR 3 22 157 40 0 1\n";
	print PIPE "PB 3 22 157 24 0\n";
	print PIPE "FP 0 15 0 0 0 1 \"$artist\"\n";
	print PIPE "FP 0 9 0 15 0 1 \"$title\"\n";
	print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
	print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
	print PIPE "MC 1\n";
}

sub progress {
	while(1) {
		if($status > 0) {
			$trackCurSecs = `dcop amarok player trackCurrentTime`;
			$trackCurTime = `dcop amarok player currentTime`;
			chomp $trackCurSecs;
			chomp $trackCurTime;
			print PIPE "PB 5 27 155 35 0 1 1\n";
			print PIPE "DB 3 27 157 35 2 $trackCurSecs $trackTotalSecs 3\n";
			print PIPE "TO 0 35 0 1 \"    $trackCurTime / $trackTotalTime    \"\n";
			print PIPE "MC 1\n";
		} elsif($status == -1) {
			return;
		}
		sleep 1;
	}
}
	
sub bye {
	$status = -1;
	sleep 2;
	print PIPE "SC\n";
	close(PIPE);
	exit 0;
}

```

It circumvents the CPIPE which for whatever reason simply would not work on my box and it has the truetype issue pre-fixed.
If does doesn't work, then you need to be clearer on what's wrong.

BTW, here's my Xmodmap that I've been using for a couple months, works perfectly when turning the cube with g keys. Ignore the pointer bit, its for my Logitech MX518

put "xmodmap $HOME/.Xmodmap" without the "" in your sessions (startup)

```
pointer = 1 2 3 4 5 8 9 6 7

keycode 144 = XF86AudioPrev 
keycode 153 = XF86AudioNext 
keycode 164 = XF86AudioStop 
keycode 162 = XF86AudioPlay 
keycode 184 = XF86Launch0 
keycode 93 = XF86Launch1 
keycode 131 = XF86Launch2 
keycode 247 = XF86Launch3 
keycode 177 = XF86Launch4  
keycode 152 = XF86Launch5 
keycode 190 = XF86Launch6 
keycode 208 = XF86Launch7 
keycode 129 = XF86Launch8 
keycode 130 = XF86Launch9 
keycode 231 = XF86LaunchA 
keycode 209 = XF86LaunchB 
keycode 210 = XF86LaunchC 
keycode 136 = XF86LaunchD 
keycode 220 = XF86LaunchE 
keycode 143 = XF86LaunchF 
keycode 246 = XF86iTouch 
keycode 251 = XF86Calculater 
keycode 137 = XF86Support 
keycode 138 = XF86Word 
keycode 182 = XF86Messenger 
keycode 183 = XF86WebCam 
keycode 132 = XF86Pictures 
keycode 170 = XF86VendorHome 
keycode 219 = XF86WWW 
keycode 249 = XF86ToDoList 
keycode 205 = XF86Calendar
```

---

### Post by NZ-Wanderer on 2007-01-16
Many thanks for that info, will give it a go once I find out how to exactly add something to the startup (seems even tho I do have a Session Manager under "system Settings/Advanced/" in Kubuntu, I cannot figure out any way to edit it at all...)
Looks like Kubuntiu doesn't have any way of adding or editing startup stuff (which is why I can't get G15daemon to start automatically either)

> **Jeff59 said:**
> NZ-Wanderer  Here is the information you requested on programing the G-keys

---

### Post by Jeff59 on 2007-01-17
Check this link out it should answer your question.

 [http://suseroot.com/suse-linux-tweaks/load-startup.php]("http://suseroot.com/suse-linux-tweaks/load-startup.php")

You can also edit the etc/inid.d/rc.local file and add the command at the bottom.  Not a big fan of Kubuntu, I ran it for a month then when back to Ubuntu which in my opinion is the best Linux distro going.

---

### Post by Jeff59 on 2007-01-17
drdnl,  Thanks for the help I have done a complete reinstall of the debs per your directions.  Everything runs and I see the clock.  A couple of things did not work as directed in the how to:

When I change souder file 

user ALL= NOPASSWD: /usr/sbin/g15daemon

and add "System->Preferences->Sessions and add sudo g15daemon to the list" nothing happens at reboot.

  I had to put the  "g15daemon" in the etc/init.d/rc.local file to get it to auto start. Should I be not concerned about that?

The following is were I think I might be having the problem with the LCD and I'm not sure if I set it up right. 

[HTML]Assuming you have g15daemon running and g15composer with arguments /usr/bin/g15composer -b /var/run/g15composer[/HTML]

I started this in the terminal with the " g15composer usr/bin/g15composer -b /var/run/g15composer" command.  I'm not sure if thats what you meant.  Also my g15lcd file and pipe are located in my home/user folder is that right?


In something off the subject can you read and play audio CD's from your Amarok install, my says "Could not read Audio CD"?  

Thanks again for your help.

---

### Post by drdnl on 2007-01-17
Hmm strange, well, if you have a clock then all is fine, doesn't really matter how you did it :)

check your system monitor, after installing the deb you prob. already have g15composer running, if not run "sudo /etc/init.d/g15composer start". Also, you should have a g15daemon running.

Basically, open the system monitor, sort it by name (alphabetically) and check the g15*'s. Kill any unneeded ones which you might have opened whilst experimenting, just leave the two I mentioned. (g15daemon and g15composer)

Now, install the attached file into Amarok and run it (under scripts manager) and play a mp3, stuff should show up...

About cd's, mine didnt work either, try seraching the 'net for it.

oh, and try deleting ~/.g15amaroklcdpipe

---

### Post by Jeff59 on 2007-01-17
drdnl,  Still no luck with the LCD and Amaork.  I think it might br your first suggestion but I'm not quite sure what I was suppose to fix.

> 1) You didn't fix truetype, search through this topic with "truetype" and you'll find your answer. Think its also mentioned in the txt that comes with your amarokscript. (sorry, lazy, fixing my own beryl problems right now )

Things I Know.

 I know the pipe works, because when I send direct text it shows on the Screen.

I'm sure your script is right because the song progress bars and timer show. 

It has to be the truetype problem that I screwed up.  Could you be more detailed about this fix.  Thanks again. :confused:

---

### Post by drdnl on 2007-01-17
Progress bar and timer is a symptom of no truetype. This is the font you should be using: /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf

The script I just attached has truetype setup properly, but check anyway (amarok -> scripts -> edit)

Thins you can try in order:

1) Check its there/its existance
2) check its permissions (are you allowed to read it?)
3) if not, edit the script (amarok -> scripts -> edit) and try a different font
4) you need to have ttf font support, this should be included in the debs, try uninstalling everything and reinstalling it all (from the archive)
5) I'm running out of ideas, contact one of the devs at sourceforge,

Good luck!

Regards,
D

---

### Post by akshoslaa on 2007-01-26
Quick question... are there any scripts aside from the various tweaks of that amarok script? Is there any decent documentation to get me started with something other than 'Hello World'?

---

### Post by Aneurysm9 on 2007-01-26
There doesn't seem to be a whole lot of script development going on.  The latest g15composer has a manpage that details all of the commands that can be sent.  I'm not sure if I've posted debs of libg15render-1.2 and g15composer-3.1, if I haven't I'll do so this weekend.  There's also complete api documentation for libg15render if you prefer to program directly to the library at [http://g15tools.sf.net/docs-g15r](http://g15tools.sf.net/docs-g15r).  There aren't really any programming or script writing tutorials, but looking at the source for the amarok script and the various g15daemon plugins using libg15render should give you an idea of what's needed.

---

### Post by akshoslaa on 2007-01-27
Thanks, I was guessing alot of reverse engeering of the amarok script was probably going to be the way to go - but it was worth asking.

libg15render is probably a bit beyond me for now, haven't touched C in years. stdio.h is about he extent of my abilities there :P but I didn't think of there being a man for g15composer (which is in the version I'm running, so that's all good) so that gives me a really good starting point.

If I come up with anything useful I'll be sure to post it somewhere :)

---

### Post by akshoslaa on 2007-01-29
Aneurysm9 - sorry to bug you, but I'm assuming your the same Aneurysm9 as on the sourceforge page. I've got a couple of questions about g15composer and I'm trying to track down someone to ask without overly hijacking an ubuntu thread that's fairly unrelated to my questions. The sourceforge forums and mailing lists look unused... is there a forum/list specifically for g15 somewhere I could try, or any way I can contact you (or one of the other devs)?

---

### Post by Aneurysm9 on 2007-01-29
The g15tools forums on sf.net are pretty well unused, but not unusable, if you want to post there, go ahead.  The dev lists are also pretty well zero traffic, but I think both mlampard and myself are subscribed to both dev lists.  Otherwise, you can email me at mirabeaj $at$ gmail.com

---

### Post by Jeff59 on 2007-02-01
drdnl, Well I finally got Amarok working with the script and now have the song titles.  I'm not sure which of three things I did that fixed it but I will list them in case anyone else is having the same problem.  I also was able to get the Audio cd to read and play.

First I reinstalled the G15 tools and daemon using this script that I updated from an earlyer post.  saves a lot of time.  Thanks Aneurysm9  for the original

Download and unpack the files to a folder then switch to that folder and run this.

> sudo for package in libg15-1.2.1 libg15render-1.2 g15daemon-1.2.6a g15composer-3.1
do;
cd $package
./configure --prefix=/usr --enable-ttf
make
sudo make install
cd ..
done


This is what I think did it.  I think the permissions were wrong for accessing the font files.

> Make sure to replace "myusername" with your user name! 

sudo chown -R myusername:myusername /home/myusername/.*

Then I added these in Adept, not sure if this helped or not:
xine-ui
xinetd

To get Audio CD to play  go to:

>  Amarok >Configure>Engine and change default devices to /dev/hdc 

and it should work.  Hope this helps

---

### Post by drdnl on 2007-02-02
Congratulations, enjoy your finally functional logitech g15 keyboard, it was my final piece of hardware that needed to be "fixed" before I could fully use linux.  Took you a long time though ;)

Good to hear we could help someone out,

Regards,
D

---

### Post by cd1680 on 2007-02-06
Im confused on how to change the sudo file.

In the howto it said to Change the user part and add the following to the end of the file:
user ALL= NOPASSWD: /usr/sbin/g15daemon

I don't know exactly what it means by "change the user part"

can someone post the entire visudo file here? thanks!

---

### Post by Aneurysm9 on 2007-02-06
Change the part that says "user" in that line to match your UNIX username, i.e.:
cd1680 ALL = NOPASSWD: /usr/sbin/g15daemon

---

### Post by cd1680 on 2007-02-06
I got everything to work except that the LCD doesn't display the artist and song name. I tried searching through truetype solutions but it seems that my truetype font directory is correct and I have permission to read it. I followed the steps at [http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15) and used all the files attached there. Can someone help?

---

### Post by Aneurysm9 on 2007-02-06
There's an open bug report on SF.net that I've been meaning to address that might be related to some people being unable to use TTF support.  It should express itself as a segfault, but I've seen weirder things happen.  I'll try to take a closer look at it this weekend.  It will probably require an update to both libg15render and g15composer as the libg15render API will likely change.

---

### Post by cd1680 on 2007-02-06
thanks alot. I just didn't know what I was doing wrong as it seemed like I was following every direction that the page said.

ps. do the files in the linked page have ttf enabled? could that be the problem?

---

### Post by thomasmayer on 2007-02-07
hi

has anyone tried to get the z-10 speakers display working and succeeded?
i tried to add the device in the libg15.c but it doesn't work.
however i don't know if my setup works generally as i don't have a g15 keyboard to test it.

---

### Post by Aneurysm9 on 2007-02-07
The debs that I have built do have TTF support enabled.  I can't speak to any others.  

As for the z-10, I don't have any to work with so I don't know.  There's OS X support for them  from [http://www.entropy.ch/software/macosx/lcdtool/](http://www.entropy.ch/software/macosx/lcdtool/) which I'm picking through the code for to try to get the G15 working on OS X.  Changing the device ID doesn't work there either, so maybe when I figure out the G15 on OS X, the reverse will get the z-10 working on Linux.

---

### Post by Alex74447 on 2007-02-10
Does this work on dapper? It wont let me isntall because of some dependency errors, and then when I go to the synaptics it gives me broken files for all the G15 related downloads.

---

### Post by Aneurysm9 on 2007-02-10
I don't have a dapper system anymore to build packages on, so you'll have to build it yourself if you want the latest versions of the g15tools, but they do all have the packaging structure in SVN and the release tarballs so you can easily build your own.

---

### Post by zszafran on 2007-02-16
Okay, I have absolutely no idea what I am doing wrong.

First off I am running Edgy Eft.

I have downloaded the sources and run the command...
```
for package in libg15-1.2.1 libg15render-1.2 g15daemon-1.2.7 g15composer-3.1; do cd $package; ./configure --prefix=/usr --enable-ttf; make; sudo make install; cd ..; done
```
...without any errors or problems. 

I am able to run the command "sudo g15daemon" with no errors.

From what I understand, I should see a clock in my LCD after I run the above command? Well right now I see nothing. I have attempted the guide at [http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15) , which also did not work for me....

Any ideas?

---

### Post by mlampard on 2007-02-16
First, run 'sudo modprobe uinput', then try running g15daemon again.  If it still fails
please post the output of 'sudo g15daemon --debug 2'

[edit]
Also, if you have the g15 plugged into a hub, please try plugging it directly into the PC instead - the g15 has known problems when a hub is in the way.

Thanks

---

### Post by zszafran on 2007-02-17
It was my USB Hub that was the problem. Thanks for the help.

---

### Post by klanman8908 on 2007-02-17
I recently got a g15 keyboard and would like to use it on Linux.  I have installed the g15tools and everything is working great.  The clock shows and the g-keys work.  I'm using xbindkeys to configure what the keys do.  I have figured out if i have 3 config files for xbindkeys, 1 for each m button (1-3) then I can press say m2 button have it rename the current file to xbindkeysrc.m1 then rename xbindkeysrc.m2 to xbindkeysrc and restart xbindkeys.  This allows me to have 3 banks of the g1-18 keys like in windows, all with different functions. I hope you were able to follow that.  The question I have I hope is simple, how do i light up the orange  LEDs for the m keys so that I can tell which config file is being used?

---

### Post by mlampard on 2007-02-17
> **thomasmayer said:**
> hi

has anyone tried to get the z-10 speakers display working and succeeded?
i tried to add the device in the libg15.c but it doesn't work.
however i don't know if my setup works generally as i don't have a g15 keyboard to test it.

libg15 in g15tools svn now has z-10 speaker support.  I'll create a new release in the next couple of days, but you are welcome to try the svn code until then.

Mike

---

### Post by mlampard on 2007-02-18
> **klanman8908 said:**
> I'm using xbindkeys to configure what the keys do.  I have figured out if i have 3 config files for xbindkeys, 1 for each m button (1-3) then I can press say m2 button have it rename the current file to xbindkeysrc.m1 then rename xbindkeysrc.m2 to xbindkeysrc and restart xbindkeys.  This allows me to have 3 banks of the g1-18 keys like in windows, all with different functions. I hope you were able to follow that.  The question I have I hope is simple, how do i light up the orange  LEDs for the m keys so that I can tell which config file is being used?

Probably the simplest way to provide the functionality you want is to install g15daemon 1.9, and g15macro from the g15daemon homepage.  G15macro is a g15daemon client which allows macro record and playback, and creates three separate 'palettes' of keys selectable via the 'M'keys.  You could use xbindkeys to create hotkeys for any of those keys while g15macro is running.  Please note, g15macro requires functionality only available in g15daemon 1.9, and wont work with current versions of g15daemon 1.2 series.

Mike

---

### Post by jinx099 on 2007-02-20
I just got a logitech G11 (not 15) and all I want are the macro keys to work.  Will G15tools work on a G11?

---

### Post by mlampard on 2007-02-20
Yes.  Using a recent version of libg15, g15daemon will work just fine with the G11 keyboard.

---

### Post by Dawnrazor on 2007-02-20
Someone has an Ubuntu Package for g15daemon 1.90 ?

I am not able to make one :(

./configure and make, there are no errors, but after a
sudo checkinstall it comes an error

> dawn@dawn:~/Desktop/g15/g15daemon-1.9.0$ sudo checkinstall 
Password:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Bereite Paket-Dokumentation vor...OK

Bitte geben Sie eine Beschreibung f&#65533;r das Paket ein.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@dawn ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ g15daemon ]
3 -  Version: [ 1.9.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ g15daemon-1.9.0 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Geben Sie die betreffende Nummer ein, um die Vorgaben zu &#65533;ndern: 

Installing with make install...

========================= Installation results ===========================
Making install in libg15daemon_client
make[1]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/libg15daemon_client'
make[2]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/libg15daemon_client'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libg15daemon_client.la' '/usr/lib/libg15daemon_client.la'
/usr/bin/install -c .libs/libg15daemon_client.so.1.0.2 /usr/lib/libg15daemon_client.so.1.0.2
(cd /usr/lib && { ln -s -f libg15daemon_client.so.1.0.2 libg15daemon_client.so.1 || { rm -f libg15daemon_client.so.1 && ln -s libg15daemon_client.so.1.0.2 libg15daemon_client.so.1; }; })
(cd /usr/lib && { ln -s -f libg15daemon_client.so.1.0.2 libg15daemon_client.so || { rm -f libg15daemon_client.so && ln -s libg15daemon_client.so.1.0.2 libg15daemon_client.so; }; })
/usr/bin/install -c .libs/libg15daemon_client.lai /usr/lib/libg15daemon_client.la
/usr/bin/install -c .libs/libg15daemon_client.a /usr/lib/libg15daemon_client.a
ranlib /usr/lib/libg15daemon_client.a
chmod 644 /usr/lib/libg15daemon_client.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'g15daemon_client.h' '/usr/include/g15daemon_client.h'
make[2]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/libg15daemon_client'
make[1]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/libg15daemon_client'
Making install in g15daemon
make[1]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/g15daemon'
make[2]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/g15daemon'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'g15daemon' '/usr/sbin/g15daemon'
/usr/bin/install -c g15daemon /usr/sbin/g15daemon
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'g15daemon.h' '/usr/include/g15daemon.h'
/usr/bin/install: Setzen der Zugriffsrechte für „/usr/include/g15daemon.h“: No such file or directory
make[2]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/g15daemon'
make[1]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/g15daemon'
Making install in plugins
make[1]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/plugins'
make[2]: Betrete Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/plugins'
test -z "/usr/share/g15daemon/plugins" || mkdir -p -- "/usr/share/g15daemon/plugins"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'g15plugin_uinput.la' '/usr/share/g15daemon/plugins/g15plugin_uinput.la'
/usr/bin/install -c .libs/g15plugin_uinput.so /usr/share/g15daemon/plugins/g15plugin_uinput.so
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_uinput.so': No such file or directory
/usr/bin/install -c .libs/g15plugin_uinput.lai /usr/share/g15daemon/plugins/g15plugin_uinput.la
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_uinput.la': No such file or directory
/usr/bin/install -c .libs/g15plugin_uinput.a /usr/share/g15daemon/plugins/g15plugin_uinput.a
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_uinput.a': No such file or directory
ranlib /usr/share/g15daemon/plugins/g15plugin_uinput.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'g15plugin_tcpserver.la' '/usr/share/g15daemon/plugins/g15plugin_tcpserver.la'
/usr/bin/install -c .libs/g15plugin_tcpserver.so /usr/share/g15daemon/plugins/g15plugin_tcpserver.so
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_tcpserver.so': No such file or directory
/usr/bin/install -c .libs/g15plugin_tcpserver.lai /usr/share/g15daemon/plugins/g15plugin_tcpserver.la
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_tcpserver.la': No such file or directory
/usr/bin/install -c .libs/g15plugin_tcpserver.a /usr/share/g15daemon/plugins/g15plugin_tcpserver.a
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_tcpserver.a': No such file or directory
ranlib /usr/share/g15daemon/plugins/g15plugin_tcpserver.a
ranlib: could not create temporary file whilst writing archive: No more archived files
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'g15plugin_clock.la' '/usr/share/g15daemon/plugins/g15plugin_clock.la'
/usr/bin/install -c .libs/g15plugin_clock.so /usr/share/g15daemon/plugins/g15plugin_clock.so
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_clock.so': No such file or directory
/usr/bin/install -c .libs/g15plugin_clock.lai /usr/share/g15daemon/plugins/g15plugin_clock.la
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_clock.la': No such file or directory
/usr/bin/install -c .libs/g15plugin_clock.a /usr/share/g15daemon/plugins/g15plugin_clock.a
/usr/bin/install: setting permissions for `/usr/share/g15daemon/plugins/g15plugin_clock.a': No such file or directory
ranlib /usr/share/g15daemon/plugins/g15plugin_clock.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[2]: *** [install-libLTLIBRARIES] Fehler 1
make[2]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/plugins'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/home/dawn/Desktop/g15/g15daemon-1.9.0/plugins'
make: *** [install-recursive] Fehler 1

****  Installation failed. Aborting package creation.


---

### Post by mlampard on 2007-02-20
oops :(

Does adding usr/share/g15daemon/* to the debian/g15daemon.install file fix the problem?  I'm afraid I'm not running a debian-based distro on my devel machines, and can't test/create packages at the moment.  If adding that line solves the problem, I'll create a new bugfix release of 1.90 tonight.

---

### Post by Arcolite on 2007-02-23
I'm having problems already, I haven't even got as far as the G15Tools install yet.

I've got as far as "sudo g15daemon" when i get the following error...

```
g15daemon: error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory
```

...but if I run "sudo apt-get install libusb-dev libdaemon-dev" it doesn't install anything and says they are already installed.

So far I've followed the guide exactly (I'm AMD64, so I did use --force-architecture when I installed the first packages.

I've been following [http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15](http://doc.gwos.org/index.php/G15Tools_support_for_the_Logitech_G15)

---

### Post by jinx099 on 2007-02-23
First, I want to say thank you to the G15tools developers.

I am using a G11 and G15 tools mostly works.  Theres a few things I need to get worked out however.

The firstis g15macro is kinda flakey.  When I map a macro to a Gkey, and then I use the macro, keys are repeated.  For example, when I map G16 to ctrl-T for a new firefox tab, and I press G16, a new tab pops up alright, but then in the address box it looks like t key is being held down as it repeats.  Same thing for Shift-Ctrl-T for a new terminal tab.  This is in Fedora Core 6 btw.

In Ubuntu 7.04 alpha, I cant get g15macro compiled.  ./configure complains about Xorg XTest not being installed.  I opened up synaptic and searched for xtest and found what I thought was it, but after installing it, I still got the same complaint.  I had this happen in FC6 too, but I solved the issue by installing " software development".  Is this a feisty package problem or something else?

Thanks!  I really want to get these macro keys working!

---

### Post by Dawnrazor on 2007-02-24
> **jinx099 said:**
> First, I want to say thank you to the G15tools developers.

I am using a G11 and G15 tools mostly works.  Theres a few things I need to get worked out however.

The firstis g15macro is kinda flakey.  When I map a macro to a Gkey, and then I use the macro, keys are repeated.  For example, when I map G16 to ctrl-T for a new firefox tab, and I press G16, a new tab pops up alright, but then in the address box it looks like t key is being held down as it repeats.  Same thing for Shift-Ctrl-T for a new terminal tab.  This is in Fedora Core 6 btw.

In Ubuntu 7.04 alpha, I cant get g15macro compiled.  ./configure complains about Xorg XTest not being installed.  I opened up synaptic and searched for xtest and found what I thought was it, but after installing it, I still got the same complaint.  I had this happen in FC6 too, but I solved the issue by installing " software development".  Is this a feisty package problem or something else?

Thanks!  I really want to get these macro keys working!

Give me your g15daemon 1.90
and i give you the compiled feisty g15 macro :)
[ATTACH]26025[/ATTACH]

---

### Post by jinx099 on 2007-02-24
> **Dawnrazor said:**
> Give me your g15daemon 1.90
and i give you the compiled feisty g15 macro :)
[ATTACH]26025[/ATTACH]

hmmm, the deb installed fine, but g15macro didnt appear to do anything.  I also managed to get it compiled from source in Feisty too with the same result (I just needed the standard xorg-dev packages installed to get it to compile, duh!).

---

### Post by Dawnrazor on 2007-02-24
> **jinx099 said:**
> hmmm, the deb installed fine, but g15macro didnt appear to do anything.  I also managed to get it compiled from source in Feisty too with the same result (I just needed the standard xorg-dev packages installed to get it to compile, duh!).

Yes we need G15daemon 1.90, but look some Post above
I am not able to compile it
and also i have not the folder  **usr/share/g15daemon/**

---

### Post by po0f on 2007-02-24
Dawnrazor,

Have you tried `sudo mkdir /usr/share/g15daemon/plugins`?  I believe I had to manually create the directory for it to install the plugins in.

---

### Post by Dawnrazor on 2007-02-24
> **po0f said:**
> Dawnrazor,

Have you tried `sudo mkdir /usr/share/g15daemon/plugins`?  I believe I had to manually create the directory for it to install the plugins in.

oh im stupid :lolflag: 
Yes that helped  :)

but now i have an error message
```
Sorry, cant connect to the G15daemon
```

---

### Post by jinx099 on 2007-02-24
> **Dawnrazor said:**
> oh im stupid :lolflag: 
Yes that helped  :)

but now i have an error message
```
Sorry, cant connect to the G15daemon
```

You need to start g15daemon first.

```
sudo g15daemon
```

---

### Post by Dawnrazor on 2007-02-25
> **jinx099 said:**
> You need to start g15daemon first.

```
sudo g15daemon
```

:lolflag: 

for sure :D it is started :D

---

### Post by jinx099 on 2007-03-01
I just got everything compiled from source on a fresh Edgy installation and I'm still having the g15macro issue.

devs any suggestions?  Is this a known issue?

---

### Post by mlampard on 2007-03-01
try running g15daemon 1.90 with the --debug option, and run g15macro in another window - g15daemon should find and load the network plugin then sit in the foreground waiting.  If it does and g15macro still doesnt work (no M1 LED and no g15macro logo flashing on at startup) please post the output of both on the g15daemon forums at sourceforge.

Mike

---

### Post by jinx099 on 2007-03-02
> **mlampard said:**
> try running g15daemon 1.90 with the --debug option, and run g15macro in another window - g15daemon should find and load the network plugin then sit in the foreground waiting.  If it does and g15macro still doesnt work (no M1 LED and no g15macro logo flashing on at startup) please post the output of both on the g15daemon forums at sourceforge.

Mike

To clarify, I have a G11, not a G15.  When I run g15macro the M1 key lights up and switches correctly when I press another M.  The MR key lights up when I press it and *seems to* record the macro correctly.  The problem is when I use the macro, 1 or more keys in the macro are repeated forever.  For example when I map a new console tab (shift-ctrl-T), a new tab opens, but in the console, I get "tttttttttttttttttttttttttttttttttttttttttttttttttttt" until I press an unmapped G key.

Here is my g15daemon window:

```
$ sudo g15daemon --debug
usb_set_debug: Setting debugging level to 1 (on)
usb_os_init: Found USB VFS at /dev/bus/usb
libg15: Found 1 supported devices
libg15: Trying to find Logitech G15
libg15: Logitech G15 not found
libg15: Trying to find Logitech G11
libg15: Found Logitech G11, trying to open it
libg15: Done opening the keyboard
g15daemon 1.9.0 loaded

Loading plugin /usr/share/g15daemon/plugins/g15plugin_uinput.so
registered plugin "Linux UINPUT Keyboard Output"
Loading plugin /usr/share/g15daemon/plugins/g15plugin_tcpserver.so
Loading plugin /usr/share/g15daemon/plugins/g15plugin_clock.so
registered plugin "LCDServer"
registered plugin "Clock"
Client is taking over keystate
Client has taken over keystate
```

I currently dont have a sourceforge account, but I may create one soon to help you devs.

---

### Post by mlampard on 2007-03-02
Ah, I see.  This is likely to be a bug in the way g15macro sends keypress/release events to X11, and how the various toolkits use these events.  When I wrote g15macro, I tested it pretty heavily with kde but only once with gnome.  If you would like to help me in debugging this I'd appreciate it.  

Mike

---

### Post by drdnl on 2007-03-02
For anyone who cares, attached are the latest amd64 debs with ttf support. If it doesnt work right away you probably need to follow some steps from the starting post.

For anyone wanting to compile them themselves, turns out you need libfreetype6 (maybe -dev, can't remember) installed for ttf support.

Found a possible bug though, if I run the audacious *or* xmms plugin (with visualization) the entire thing hangs, it doesnt crash, it hangs and only an old fashioned ctrl+c in the terminal helps. Anyone?

-D

---

### Post by jinx099 on 2007-03-02
> **mlampard said:**
> Ah, I see.  This is likely to be a bug in the way g15macro sends keypress/release events to X11, and how the various toolkits use these events.  When I wrote g15macro, I tested it pretty heavily with kde but only once with gnome.  If you would like to help me in debugging this I'd appreciate it.  

Mike

Yes I would like to help in debugging.  Can you reproduce this bug in gnome with a G15?  I'd like to know if its an issue only with the G11.

---

### Post by westis78 on 2007-03-04
> **jinx099 said:**
> For example when I map a new console tab (shift-ctrl-T), a new tab opens, but in the console, I get "tttttttttttttttttttttttttttttttttttttttttttttttttttt" until I press an unmapped G key.


I'm having he same problem with my G11 (on 64bit edgy using gnome) too. It's like the key releases aren't recorded properly. Nobody using a G15 is having the same problem?

---

### Post by jinx099 on 2007-03-12
Is the G11/macro problem being worked on, or do I need to report it on sourceforge?  I'd really like to help out the development process if I can.

---

### Post by gbesso on 2007-03-18
I can reproduce this problem with my G15

---

### Post by serge lorich on 2007-03-28
good day to all of you!

all this evening i am digging internet to solve one question.

if i unplug and replug g15 keyboard, daemon won't work with it until killing and restarting.

and internet is quiet about this issue.


by the way. ubuntu 6.06. issue is for both daemon versions - 1.90 and 1.27 :confused:

---

### Post by po0f on 2007-03-29
serge lorich,

This is all **UNTESTED**, but I don't think it will break anything if it doesn't work.

You can write a udev rule [color="red"][1][/color] to handle events that happen on your computer, in your case, unplugging/replugging your G15.  A simple rule that should work:

```
# Put the following in /etc/udev/rules.d/19-local.rules
# You'll need sudo access
SYSFS{../name}=="Logitech Logitech Gaming Keyboard", SYMLINK+="input/g15", RUN+="/usr/local/bin/g15daemon-hotplug"
```

The preceding just tells udev that `/usr/local/bin/g15daemon-hotplug` should be run when your G15 is either plugged or unplugged.  The symlink is an added bonus, the device entry will also be available as /dev/input/g15.

Now, for /usr/local/bin/g15daemon-hotplug:

```
#!/bin/bash
# start/stop g15daemon when plugged/unplugged
case $ACTION in
        "add")
                # G15 being plugged, start g15daemon
                sudo g15daemon
                ;;
        "remove")
                # G15 being unplugged, kill g15daemon
                sudo g15daemon -k
                ;;
        *)
                exit 0
                ;;
esac
```

(Remember to set execute for the script.)

You can test it by running:

```
$ ACTION="remove" g15daemon-hotplug
```

from a terminal.

ACTION is an environment variable that is available when programs are run because of udev.  ACTION will be set to either "add" or "remove", depending on if you're plugging or unplugging your G15, respectively.

You'll have to restart udev or just reboot your computer for the changes to take effect.

I don't know if the above script will actually work, since running `g15daemon` requires sudo access.  If you can let me know whether it works or not, that'd be great.  :)

_References_:
[color="red"][1][/color] [Writing udev rules](http://reactivated.net/writing_udev_rules.html)

---

### Post by drdnl on 2007-03-29
> **po0f said:**
> serge lorich,

I don't know if the above script will actually work, since running `g15daemon` requires sudo access.  If you can let me know whether it works or not, that'd be great.  :)



If you follow the sudo visudo commands in the starting/first post (of this thread) you'll no longer need to type in a password when running "sudo g15daemon" (not sure about the sudo g15daemon -k though, might need to add an extra rule for that) thus circumventing the quoted problem.

Hope this helps.

---

### Post by po0f on 2007-03-29
drdnl,

I never bothered following the howto myself, I just downloaded and installed the necessary libraries/programs.  ;)


[EDIT]

Ok, I can't seem to get udev to play nice.  I believe there is a way to make it work though.  Navigate to System->Preferences->Removable Drives and Media (on Feisty) and click on the "Input" tab.  Check the box next to the keyboard icon.  For the command to run, type in "/usr/local/bin/g15daemon-restart".  Now for _that_ script:

```
#!/bin/bash

sudo g15daemon -k
sleep 2
sudo g15daemon
```

Make sure it's executable.  (`chmod +x /usr/local/bin/g15daemon-restart`)

I tested it, it works, have fun.  :)

---

### Post by serge lorich on 2007-04-03
thank you for your solutions but none of them are working.
a pretty one solution using gnome's properties aren't suitable for me.
i want to dig these rules deeper than gnome :)
and previous one - using udev - works strange too. 

if i will apply that rules for udev to another distro - with normal root - will be everything ok ?

the next questions.
* while testing g15composer i found one issue. g15composer falls when i load bitmap to the same slot three times. maybe it is possible to free previously alloc'ed memory?
* the second question is about internationalization in g15tools. i mean utf-8 support for TTF fonts.

---

### Post by po0f on 2007-04-04
serge lorich,

Yeah, I would like a udev solution to this as well, but I don't have much experience writing udev rules.  That rules in theory should work, it even checks out with `udevtest` as well.  I really don't know why it's not working though.

Btw, why are you unplugging your keyboard?  It seems to be a lot more useful when it's plugged in.  ;)

---

### Post by nuklehed on 2007-04-06
I wasn't getting any errors with the g15daemon or composer, but I wasn't seeing anything change on my G15's LCD. After much ado, I found the problem lied in the fact that my G15 was plugged into my monitor. After plugging it directly into my PC (not thru a hub), it works as I thought it should. Hope this helps somebody that might have the same issue.

---

### Post by serge lorich on 2007-04-10
> **po0f said:**
> serge lorich,

Yeah, I would like a udev solution to this as well, but I don't have much experience writing udev rules.  That rules in theory should work, it even checks out with `udevtest` as well.  I really don't know why it's not working though.

Btw, why are you unplugging your keyboard?  It seems to be a lot more useful when it's plugged in.  ;)

i will try "udev solution" on another platform and post here results.

as for me - system should work correctly, and replug is usual action.
udev is cool, but rules are enough crazy.
maybe i don't have enough experience in administrating sysfs. i am a programmer but it is hard enough for me to understand that syntax :)

---

### Post by serge lorich on 2007-04-12
good day to all of you again.

toying with libg15render's sources i made UNICODE support for it.
solution is not too beautiful but it works with my cyrillic fonts without any additional actions from user.
output from console thru Composer works rightly...

if Render's authors are interested in this fix, please contact me.
my questions on sourceForge are not answered.

---

### Post by Aneurysm9 on 2007-04-12
> **serge lorich said:**
> the next questions.
* while testing g15composer i found one issue. g15composer falls when i load bitmap to the same slot three times. maybe it is possible to free previously alloc'ed memory?
* the second question is about internationalization in g15tools. i mean utf-8 support for TTF fonts.

I'll take a look at the g15composer issue, I probably did forget to free memory somewhere.  Can you get a backtrace when it fails or provide more detail on how it fails?  As for internationalization, I don't have any experience doing that sort of thing, if you do I'd be greatly appreciative of patches.

Just saw your post that you have UTF8 working.  I'd love to see the patch.  Sorry for not responding sooner, I've got another project that I'm actually being paid for (and, thus, the payor's expectation of quick results) that's taking most of my time now.  There are a couple of other minor fixes for libg15render that need to get pushed out too, so if you can get a patch to me this weekend, I'll see if I can get a new release out quickly.

---

### Post by MachineHead on 2007-04-15
Hello people,

Is there any amd 64 bit support for the G15?
I'm on Kubuntu 6.10 Edgy.

Thanks!
MachineHead

---

### Post by drdnl on 2007-04-16
Yes, I posted them some pages back. I'll have a look for it in a bit and I'll edit this post.

Did you even look for them? Two pages back I posted the debs :)
[http://ubuntuforums.org/showthread.php?p=2236531&highlight=amd64#post2236531](http://ubuntuforums.org/showthread.php?p=2236531&highlight=amd64#post2236531)

---

### Post by drdnl on 2007-04-16
Howto: Compile the necessary debs in Ubuntu (7.04, probably the others as well)

download all the necessary files at sourceforge to your desktop [here]("http://sourceforge.net/project/showfiles.php?group_id=172261") and [here]("http://sourceforge.net/project/showfiles.php?group_id=167869")

You want g15composer, libg15, libg15render and g15daemon. The rest is optional, play with them once its all working.

Lets take care of dependencies:

```
sudo apt-get install build-essential libfreetype6-dev libdaemon-dev libusb-dev libttf-dev checkinstall
```

temporarily take care of uinput:

sudo modprobe uinput

(Once this is all working make sure to type sudo nano /etc/modules into a terminal and put uinput at the end of the file. This will ensure it loads automatically on boot)

extract all the archives onto your desktop (right click, extract)
(or in terminal type tar -xf *name archive*)

and run the script, check for errors directly above the step "create default documentation" in between compilations to make sure your dependencies are ok. When it asks you to name the package simply type in the full name, libg15-1.2.2 for example and it will fill in the details:

```
for package in libg15-1.2.2 libg15render-1.2 g15daemon-1.2.7 g15composer-3.1; do cd $package; ./configure --prefix=/usr --enable-ttf; make; sudo checkinstall make install; cd ..; done
```

Please, use a little common sense when it comes to the version numbers. Just check to make sure the folders on your desktop match the version numbers in the mini-script above.

Follow the above steps and you should have built all the packages with ttf support, try typing sudo g15daemon and a clock should pop up. 

If you want to have the daemon autorun on startup try running (BE CAREFUL)

```
sudo visudo
```

Change the user part and add the following to the end of the file:

```
user ALL= NOPASSWD: /usr/sbin/g15daemon
```  

and press ctrl+x to exit. Press Y to accept, it will check for syntax mistakes and if it finds one it will ask you "What now?" Simply press E and make the necessary changes.

After this go to System->Preferences->Sessions and add sudo g15daemon to the list

And if you really, really can't figure it out I attached the compiled debs for 7.04 386

Ps.  I take no credit for the above mini-script, I simply found it somewhere and find it extremely useful. Thanks to whoever made it.

Edit:

Also attached is a script for amarok, save it to you Desktop. Now simply open Amarok -> Tools -> Script Manager -> Install script -> select  amarok-g15-dcop_cli.pl.amarokscript.tar.gz -> install -> run it from the list (its under general). It should work immediately ***if*** you had g15daemon running (the clock).

---

### Post by MachineHead on 2007-04-16
Hi there drdnl,

Thanks for your reply.
I didn't search the pages by hand no.
I googled for g15 drivers and found this thread.
Just couldn't find any mentioning about amd 64 architecture.

Thanks for your reply, I'll remember to flip a few pages in the future.

btw, isn't i386 32-bit architecture?
It's my first go on Kubuntu so I'm pretty impressed I got most of what I need set up at the moment :)

I'll work on my keyboard later, for my work concerns me at the moment ;)

Regards,
MachineHead

---

### Post by drdnl on 2007-04-16
You're welcome,

Just to be clear, the 6.10 amd64 debs are two pages back. The debs I just posted are indeed i386 for 7.04, if you need 7.04 you can compile them with the above.

Hang in there, Linux is absolutely worth the learning curve (1 year and still a happy ubuntu user). I now use my pc in ways which were practically impossible before and have learned alot in the meantime.

Good luck and feel free to post if you have problems,
D

---

### Post by Spartan.II.117 on 2007-04-17
alright, i need a little help here. i installed the 7.04 debs in the above post, but i cant seem to get g15composer to work properly i've tried the mkmod to create a pipe, but it still holds the command line until i use ctrl+c to exit it manually, an i missing something? also i'm trying to figure out how to build a scxript to work with exaile, so if i could get some info about interacting with g15 composer that wouls be great.

---

### Post by sirel2 on 2007-04-20
Here is a possible fix for the repeating macro issue.  The problem occurs when HAVE_X11_EXTENSIONS_XTEST_H is true and is caused because the last character that is pressed never sends the release to X11.   

I modified my g15macro.c to always record a key release (but only display it for the special keys).  Your mileage might vary and I have only tested this for a short while, but it seems stable enough...  

I followed the directions in [http://ubuntuforums.org/showthread.php?p=2461304]("http://ubuntuforums.org/showthread.php?p=2461304") 
to get the g15daemon running using the **1.9.0 pre 2.0** version of g15daemon.

```

void xkey_handler(XEvent *event) {

    static unsigned long lasttime;
    unsigned char keytext[256];
    unsigned int keycode = event->xkey.keycode;
    int press = True;
    int display = True;

    if(event->type==KeyRelease){ // we only do keyreleases for some keys
      pthread_mutex_lock(&x11mutex);
      KeySym key = XKeycodeToKeysym(dpy, keycode, 0);
      pthread_mutex_unlock(&x11mutex);
        switch (key) {
            case XK_Shift_L:
            case XK_Shift_R:
            case XK_Control_L:
            case XK_Control_R:
            case XK_Caps_Lock:
            case XK_Shift_Lock:
            case XK_Meta_L:
            case XK_Meta_R:
            case XK_Alt_L:
            case XK_Alt_R:
            case XK_Super_L:
            case XK_Super_R:
            case XK_Hyper_L:
            case XK_Hyper_R:
                break;
            default: 
                display = False;
                break;
        }
        press = False;
    }
    if(recording){
        current_recording.recorded_keypress[rec_index].keycode = keycode;
        current_recording.recorded_keypress[rec_index].pressed = press;
        current_recording.recorded_keypress[rec_index].modifiers = event->xkey.state;
        if(rec_index==0)
            current_recording.recorded_keypress[rec_index].time_ms=0;
        else
            current_recording.recorded_keypress[rec_index].time_ms=g15daemon_gettime_ms() - lasttime;
        rec_index++;

        /* now the default stuff */
        pthread_mutex_lock(&x11mutex);        
        XUngrabKeyboard(dpy,CurrentTime);
        pthread_mutex_unlock(&x11mutex);

        if(display == True) {
           fake_keyevent(keycode,press,event->xkey.state);
        }

        pthread_mutex_lock(&x11mutex);
        XGrabKeyboard(dpy, root_win, True, GrabModeAsync, GrabModeAsync, CurrentTime);
        XFlush(dpy);

        strcpy((char*)keytext,XKeysymToString(XKeycodeToKeysym(dpy, keycode, 0)));
        pthread_mutex_unlock(&x11mutex);        

        if(display == True) {
           if(0==strcmp((char*)keytext,"space"))
               strcpy((char*)keytext," ");
           strcat((char*)recstring,(char*)keytext);
           g15r_renderString (canvas, (unsigned char *)recstring, 0, G15_TEXT_MED, 80-((strlen((char*)recstring)/2)*5), 22);
           g15_send(g15screen_fd,(char *)canvas->buffer,G15_BUFFER_LEN);
        }

    }else
        rec_index=0;

        lasttime = g15daemon_gettime_ms();
}
```

Also, I moved the save routine to write out the configuration every time a new macro is recorded.  
```

void *Lkeys_thread() {
...
                default:
                    if(keystate >=G15_KEY_G1 && keystate <=G15_KEY_G18){
                        if(recording==1){
                            record_complete(keystate);
                            recording = 0;
                             pthread_mutex_lock(&x11mutex);
                             XUngrabKeyboard(dpy,CurrentTime);
                             XFlush(dpy);

                             /* Write configuration every time a macro is recorded*/
                             config_fd = open(configpath,O_CREAT|O_WRONLY|O_SYNC,0600);
                             write(config_fd,mstates[0],sizeof(mstates_t));
                             write(config_fd,mstates[1],sizeof(mstates_t));
                             write(config_fd,mstates[2],sizeof(mstates_t));
                             close(config_fd);

                             pthread_mutex_unlock(&x11mutex);
                        } else {
                            macro_playback(keystate);
                        }
                    }
                    break;
            }
            keystate = 0;
        }
    }
    return NULL;
}


```


The diff is as follows:  (diff -w)
```

72d71
< char configpath[1024];
442,446d440
<     config_fd = open(configpath,O_CREAT|O_WRONLY|O_SYNC,0600);
<     write(config_fd,mstates[0],sizeof(mstates_t));
<     write(config_fd,mstates[1],sizeof(mstates_t));
<     write(config_fd,mstates[2],sizeof(mstates_t));
<     close(config_fd);
472d465
<     int display = True;
495,496c488
<                 display = False;
<                 break;
---
>                 return;
497a490
> 
515d507
<         if(display == True) {
517d508
<         }
522d512
< 
525,526d514
< 
<         if(display == True) {
532d519
<         }
611a599
>     char configpath[1024];


```

---

### Post by sgleo87 on 2007-04-22
Now that I've upgraded to feisty I installed the g15daemon again and everything went fine but I couldn't get libg15render to install with -enable-ttf.

output for "./configure --enable ttf:
```
sandra@sandra-desktop:~/Desktop/libg15render-1.2$ ./configure -enable-ttf
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking whether to enable FreeType2 support... ./configure: line 19905: freetype-config: command not found
yes
checking for writePixmapToLCD in -lg15... yes
checking for ceil in -lm... yes
checking for an ANSI C-conforming const... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking ft2build.h usability... no
checking ft2build.h presence... no
checking for ft2build.h... no
checking for ANSI C header files... (cached) yes
checking for memset... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```

output for "make"
```
sandra@sandra-desktop:~/Desktop/libg15render-1.2$ make
make  all-am
make[1]: Entering directory `/home/sandra/Desktop/libg15render-1.2'
if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -O2   -g -O2  -MT text.lo -MD -MP -MF ".deps/text.Tpo" -c -o text.lo text.c; \
        then mv -f ".deps/text.Tpo" ".deps/text.Plo"; else rm -f ".deps/text.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -g -O2 -MT text.lo -MD -MP -MF .deps/text.Tpo -c text.c  -fPIC -DPIC -o .libs/text.o
In file included from text.c:19:
libg15render.h:16:22: error: ft2build.h: No such file or directory
libg15render.h:17:10: error: #include expects "FILENAME" or <FILENAME>
libg15render.h:18:10: error: #include expects "FILENAME" or <FILENAME>
In file included from text.c:19:
libg15render.h:47: error: expected specifier-qualifier-list before 'FT_Library'
text.c: In function 'g15r_renderString':
text.c:109: warning: comparison between pointer and integer
text.c: In function 'g15r_ttfLoad':
text.c:154: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:155: error: 'g15canvas' has no member named 'ttf_face'
text.c:157: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:158: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:160: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:163: error: 'g15canvas' has no member named 'ftLib'
text.c:163: error: 'g15canvas' has no member named 'ttf_face'
text.c:166: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:170: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:171: error: 'g15canvas' has no member named 'ttf_face'
text.c:173: error: 'g15canvas' has no member named 'ttf_face'
text.c:174: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c: At top level:
text.c:179: error: expected ')' before 'face'
text.c:191: error: expected ')' before 'face'
text.c:209: error: expected ')' before 'face'
text.c:221: error: expected ')' before 'face'
text.c:233: error: expected declaration specifiers or '...' before 'FT_Bitmap'
text.c: In function 'draw_ttf_char':
text.c:236: error: 'FT_Int' undeclared (first use in this function)
text.c:236: error: (Each undeclared identifier is reported only once
text.c:236: error: for each function it appears in.)
text.c:236: error: expected ';' before 'char_x'
text.c:237: error: expected ';' before 'x_max'
text.c:238: error: expected ';' before 'y_max'
text.c:239: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tmpbuffer'
text.c:239: error: 'tmpbuffer' undeclared (first use in this function)
text.c:242: error: 'g15canvas' has no member named 'ftLib'
text.c:242: error: 'charbitmap' undeclared (first use in this function)
text.c:244: error: 'char_y' undeclared (first use in this function)
text.c:244: error: 'q' undeclared (first use in this function)
text.c:244: error: 'y_max' undeclared (first use in this function)
text.c:245: error: 'char_x' undeclared (first use in this function)
text.c:245: error: 'p' undeclared (first use in this function)
text.c:245: error: 'x_max' undeclared (first use in this function)
text.c: At top level:
text.c:252: error: expected declaration specifiers or '...' before 'FT_Face'
text.c: In function 'draw_ttf_str':
text.c:254: error: 'FT_GlyphSlot' undeclared (first use in this function)
text.c:254: error: expected ';' before 'slot'
text.c:261: error: 'face' undeclared (first use in this function)
text.c:262: error: 'FT_LOAD_RENDER' undeclared (first use in this function)
text.c:262: error: 'FT_LOAD_MONOCHROME' undeclared (first use in this function)
text.c:263: error: 'FT_LOAD_TARGET_MONO' undeclared (first use in this function)
text.c:264: error: 'slot' undeclared (first use in this function)
text.c:265: error: too many arguments to function 'draw_ttf_char'
text.c: In function 'g15r_ttfPrint':
text.c:288: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:290: error: 'g15canvas' has no member named 'ttf_face'
text.c:292: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:294: error: 'g15canvas' has no member named 'ttf_face'
text.c:295: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:297: warning: incompatible implicit declaration of built-in function 'printf'
text.c:300: error: 'g15canvas' has no member named 'ttf_face'
text.c:301: error: 'g15canvas' has no member named 'ttf_fontsize'
text.c:303: error: 'g15canvas' has no member named 'ttf_face'
text.c:305: error: 'g15canvas' has no member named 'ttf_face'
text.c:307: error: 'g15canvas' has no member named 'ttf_face'
text.c:307: error: too many arguments to function 'draw_ttf_str'
make[1]: *** [text.lo] Error 1
make[1]: Leaving directory `/home/sandra/Desktop/libg15render-1.2'
make: *** [all] Error 2


```

I had the g15daemon running with amarok and ttf enabled before in dapper and didn't have any problems. Does anybody have any ideas what could be causing this error?

---

### Post by Teh Dust on 2007-04-23
I had my g15 running nice and smooth in 6.10 now, in 7.04 I have the lcd working fine but my global media keys will no longer work  in Amarok.

When I enter them everything seems to register, XF86AudioPrev, Pause, Stop, Next and such.

However, when I press these buttons they do nothing at all.

Any ideas on what exactly is going on?

Edit: Turns out the problem was just a simple conflict with gnome and amarok. 
This thread here is what helped me.
[http://ubuntuforums.org/showthread.php?t=397629]("http://ubuntuforums.org/showthread.php?t=397629")

---

### Post by torena on 2007-04-25
> **Aneurysm9 said:**
> Here's a deb for g15composer 3.0.1 (it says 3.0, but it has the fixes from .1)  The amarok scripts that were posted earlier won't work with >=g15composer-2.1 because of how FIFO handling changed.  Attached are updated scripts that will work with 2.1 and 3.0.  The lcdmetar.pl script is part of lcdproc.  The latest version, 5.1, includes the g15 driver.  If you use VDR, graphlcd-svn includes a g15 driver.

Sadly I followed the installation instructions from the very first post of this thread.  Somewhere along the line, I'm guessing when I 'mknod lcdpipe p', I screwed up the way that g15composer handles FIFO now.  I got to the point where I was using the (old, original) amarok script and I at least was getting time/status bar of my songs in amarok.  I killed the g15composer process and tried to restart it with 'g15composer ~/g15lcd&' but that's when I began receiving "Error: No usable FIFO /root/g15lcd, aborting."  I tried deleting g15lcd since you said the newer version of g15composer has to create it's own FIFO file to read from, but when I run 'g15composer ~/g15lcd&' it hangs.  Even now, when I've got the updated amarok script running, my LCD display shows G15Composer with no backlight and it hasn't done anything since. :confused:

---

### Post by drdnl on 2007-04-25
sglee:

Think you forgot to install libfreetype6-dev (or something like that, if not, look in synaptic)

Actually, more specifically, I think you forgot to "enable-ttf" *all* the needed dependencies. Try following my compilation instructions [one page back.]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285")

torena:

don't follow those instructions, they are "ancient". Instead, make sure g15daemon and g15composer are installed.

Now run sudo g15daemon in a terminal and leave it open (you should have a clock)

Install the attached file into amarok: Go to Tools -> script manager, click on install, select the attached file and install it. Now select it from the list under general and run it. Things should work, if not, remove all the installed g15 stuff (you did use debs or checkinstall right?) and follow my installation link above.

Have fun,
D

run g15daemon "sudo g15daemon"

---

### Post by torena on 2007-04-25
Well I wiped all g15 stuff off my box.  I even used your preconfigured debs this time so I could eliminate my placenta brain (ha ha pregnant joke ;)).  I've got the clock (yay!) but sadly the amarok script is not working (boo!).  What should I try now?

---

### Post by drdnl on 2007-04-25
Hi, sorry for the amarokscript. I ripped it straight out of the latest g15composer forgetting that I've been using a custom version all this time. Attached to the post ABOVE your post just now (post #293) is the same version I have been using for months now. Try installing it into amarok and running it with the clock displaying (g15daemon switched on)

If it doesnt work delve into the tar.gz and extract the script, open a terminal, switch to the dir (desktop?) and run it: ./210-amarok-g15-dcop_cli.pl

That way it will give you (error) output which you can post here for us to look at.

Good luck, I'm going to sleep now :)

---

### Post by torena on 2007-04-25
My husband just laughed as I did a happy dance in my chair. :D  It works.  Thank you so much. :D :D

---

### Post by drdnl on 2007-04-26
Very happy to have been able to help you out :D

Now make sure you add uinput to /etc/modules and follow the visudo/session steps to make g15daemon autostart. You should now have a fully automatic amarok equipped g15, enjoy :)

---

### Post by nisukka on 2007-04-28
Somehow my system doesn't autorun the daemon (I have to manually type sudo g15daemon (and password) in terminal to run it). Perhaps I got this part wrong:
> **drdnl said:**
> 
If you want to have the daemon autorun on startup try running (BE CAREFUL)

```
sudo visudo
```

Change the user part and add the following to the end of the file:

```
user ALL= NOPASSWD: /usr/sbin/g15daemon
```  

and press ctrl+x to exit. Press Y to accept, it will check for syntax mistakes and if it finds one it will ask you "What now?" Simply press E and make the necessary changes.

After this go to System->Preferences->Sessions and add sudo g15daemon to the list



How exactly should I modify the file after typing sudo visudo? I tried adding the line (as in the guide) to the end of the file but do I have to do any other modifications?
The text editor suggests that I save the file to /etc/sudoers.tmp. Is this correct? Should it be without the .tmp?
Could you show an example modified file?

---

### Post by Reinhardt on 2007-04-29
> **nisukka said:**
> Somehow my system doesn't autorun the daemon (I have to manually type sudo g15daemon (and password) in terminal to run it). Perhaps I got this part wrong:


How exactly should I modify the file after typing sudo visudo? I tried adding the line (as in the guide) to the end of the file but do I have to do any other modifications?
The text editor suggests that I save the file to /etc/sudoers.tmp. Is this correct? Should it be without the .tmp?
Could you show an example modified file?

I made a silly mistake and had a problem similar to yours.  Here is what I did wrong (in case you did it too) - I copied the instructions verbatim in my sudoers.tmp file.  Instead, you need to change the username to your actual username, ie, user ALL= NOPASSWD: /usr/sbin/g15daemon will become for user reinhardt:

 ```
reinhardt ALL=NOPASSWD: /usr/sbin/g15daemon
```

---

### Post by Spartan.II.117 on 2007-04-29
ok, i've got the g15 figured out i think, but now lcdproc wont load the g15 driver, it worked once then now it wont start
any ideas?

---

### Post by Reinhardt on 2007-04-29
I am having a problem similar to Spartan.  I installed g15-daemon 1.9.0 and the clock works great (nice improvement over the giant numbers only).  However, after installing lcdproc 0.5.2 from a deb (made it following instructions from the tar), I can't get it to interact with my G15 keyboard.  If I run the /etc/init.d scripts nothing seems to happen, and if I run the regular programs from a terminal I can see a black box that will display different information like CPU but this info never displays on the G15 LCD.  Also, my MR and M1-M3 buttons are not lit up - are they supposed to be?  I believe MR is supposed to be used to select different lcdproc screens.

---

### Post by Spartan.II.117 on 2007-04-29
i think mine had to do with the fact that it tried to start with my system and g15 daemon was'nt running (i'm just guessing here, i fixed my autorun problem but havent restarted yet to test) i recompiled lcdproc with the:

```
./configure --enable-driver=g15
sudo make install
```
and that fixed it for the moment, we'll see wat happens when i restart.

P.S. DRNDL you might want to put a note with your debs that you still have to edit th visudo file for it to work properly.

---

### Post by nisukka on 2007-04-30
> **Reinhardt said:**
> I made a silly mistake and had a problem similar to yours.  Here is what I did wrong (in case you did it too) - I copied the instructions verbatim in my sudoers.tmp file.  Instead, you need to change the username to your actual username, ie, user ALL= NOPASSWD: /usr/sbin/g15daemon will become for user reinhardt:

 ```
reinhardt ALL=NOPASSWD: /usr/sbin/g15daemon
```
Yes, I made the same mistake. Now it is working. Thanks for the help!
Maybe this should be added to the guide so anyone as newbie as me won't make the same mistake?

---

### Post by fadenb on 2007-04-30
Hi.

I installed all the g15 stuff without problems.
but when i start lcdproc the lcd backlight is switching on and off.
is this a problem of lcdproc or the g15?

THX

---

### Post by Aneurysm9 on 2007-04-30
> **fadenb said:**
> Hi.

I installed all the g15 stuff without problems.
but when i start lcdproc the lcd backlight is switching on and off.
is this a problem of lcdproc or the g15?

THX

Actually, neither.  lcdproc will flash the backlight when the load average exceeds a threshold set in one of the config files.  You can either adjust the threshold or change the LCDd backlight setting to always on rather than application control.

---

### Post by fadenb on 2007-04-30
> **Aneurysm9 said:**
> Actually, neither.  lcdproc will flash the backlight when the load average exceeds a threshold set in one of the config files.  You can either adjust the threshold or change the LCDd backlight setting to always on rather than application control.

thx. that "fixed" it.

---

### Post by Spartan.II.117 on 2007-04-30
How do i get LCDd to restart without causing driver issues? iverytime i use sudo killall LCDd, then it cant start and i have to rebuild it.

---

### Post by Reinhardt on 2007-04-30
I finally got LCDd + lcdproc to work.  I was editing the wrong .conf file and didn't notice - the /etc one instead of the /etc/lcdproc/ conf files....  Why did it bother to install the same .conf files in the /etc directory? ;p  Also, what is with the lame heart beat?  At least you can turn it off via the G1 config, but it is still annoying.


> **Spartan.II.117 said:**
> How do i get LCDd to restart without causing driver issues? iverytime i use sudo killall LCDd, then it cant start and i have to rebuild it.

By rebuild, do you mean you have to re-make/install from the tarball again (sorry, new to linux)??   I am having no problems restarting LCDd whenever I have any problems - if the server wont start up again I can just reboot and it will work just fine.  About half the time when I kill the process, I can even restart LCDd without rebooting.  I either ended the program by closing it under system processes or by using the kill command.  However, I don't think I ever used killall, just kill so maybe I didn't get rid of all the processes.

---

### Post by Spartan.II.117 on 2007-05-01
yes i do mean using make install in the directory
here is the message i get:
```
jordan@jordan-desktop:~$ LCDd
Could not open driver module server/drivers/g15.so: server/drivers/g15.so: cannot open shared object file: No such file or directory
Driver [g15] binding failed
Could not load driver g15
There is no output driver
Critical error while initializing, abort.
```

any suggestions?

---

### Post by fadenb on 2007-05-01
> **Spartan.II.117 said:**
> yes i do mean using make install in the directory
here is the message i get:
```
jordan@jordan-desktop:~$ LCDd
Could not open driver module server/drivers/g15.so: server/drivers/g15.so: cannot open shared object file: No such file or directory
Driver [g15] binding failed
Could not load driver g15
There is no output driver
Critical error while initializing, abort.
```

any suggestions?

Hi.

did you run lcdprocs ./configure with the --enable-driver=g15 option?
if yes check if you have libg15render installed correctly.
i had to copy the g15.so from server/drivers/g15.so manually to the directory specified in the config file.

---

### Post by Bertrand Russel on 2007-05-01
I installed g15daemon but my alt-tab key still doesn't work. Nor does my <esc> key. How do I fix this?

---

### Post by Spartan.II.117 on 2007-05-01
> **fadenb said:**
> Hi.

did you run lcdprocs ./configure with the --enable-driver=g15 option?
if yes check if you have libg15render installed correctly.
i had to copy the g15.so from server/drivers/g15.so manually to the directory specified in the config file.
not after killing the process no, but i had before and the process worked, then i did sudo killall LCDd and it wouldent come back that's when it gave me that message, so i restarted and still got that measage then i did make install in the lcd proc folder and still got the message and then i re configured and re installed but am now scared to restart my computer  because i'll have to re-install all over. any ideas? 

also when my computer starts the lcd goes blank but does not show the clock untill i run sudo g15daemon, i modified the visudo according to the instructions above (including using my own username) so i'm not sure what to do about that (i suspect they are related and fixing this problem will cause LCDd to start cleanly on boot)

---

### Post by Bertrand Russel on 2007-05-01
Why hasn't the g15 keyboard been included in synaptic? It seems like all the parts needed for inclusion are here yet this painful manual process is still confusing most of us. Can't some ubuntu deity take 10 minutes and make it right?

---

### Post by Aneurysm9 on 2007-05-01
I wholeheartedly agree that the g15tools should be included in the repository.  They're already in the Gentoo tree and the build infrastructure is there for Ubuntu/Debian.  I'm not sure how the process works for Ubuntu though.  There's a proposal on the Launchpad site [https://blueprints.launchpad.net/ubuntu/+spec/logitech-g15-keyboard-drivers](https://blueprints.launchpad.net/ubuntu/+spec/logitech-g15-keyboard-drivers) for including them, but it doesn't seem to have received any attention.  Perhaps it's a "squeeky wheel gets the grease" kind of thing and the user community needs to start sqeeking! :)

---

### Post by Aneurysm9 on 2007-05-01
Spartan,

Did you edit /usr/local/etc/LCDd.conf, or wherever it is on your system?  You need to specify the full path to the directory where the drivers are stored.

---

### Post by Spartan.II.117 on 2007-05-01
how do i find out the path where the drivers are stored? and why does it work right after a make install but not after that.

---

### Post by TeeEff on 2007-05-08
Hi every ones,

I'm a beginner on Ubuntu and perl script and I would like to write perl script to manage the G15 lcd screen. 
After writing 
```
sudo nohup g15composer ~/g15lcd
echo 'TL "Hello" "World"' > ~/g15lcd
```

Hello \n World is write on the lcd screen.

Then I call this perl script :
```
#!/usr/bin/perl -w

use strict;
use DateTime;

my $user = "$ENV{USER}";

print "TL \"Hello $user\"\n";
sleep 2;

print "TL \"\" \"Bye $user\"\n";
sleep 2;
exit 0;
```

with  perl g15-perl.pl
TL "Hello teeeff"
TL "" "Bye teeeff"
is write on the console with 2 sec between the 2 lines .

but when I call perl g15-perl.pl > ~/g15lcd
The 2 lines are written on the lcd screen only at the end of the script. 

I would like to write script to display the time on the LCD screen with a while 1 loop with a sleep 1 but that don't seem to works. 
Any idee ?

---

### Post by Aneurysm9 on 2007-05-08
The better approach would be to have perl print directly to the g15lcd pipe.  Check out the Amarok example script that comes with g15composer for functioning examples, but basically it's:

open(PIPE, ">>$pipe");
print PIPE "TL \"Hello $ENV{USER}\"\n";

obviously $pipe needs to be set to the path to the pipe where g15composer is listening.

---

### Post by Spartan.II.117 on 2007-05-08
can anyone tell me where they found the g15 drivers after make install? i dont know where to look for server/drivers/.

---

### Post by TeeEff on 2007-05-09
> **Aneurysm9 said:**
> The better approach would be to have perl print directly to the g15lcd pipe.  Check out the Amarok example script that comes with g15composer for functioning examples, but basically it's:

open(PIPE, ">>$pipe");
print PIPE "TL \"Hello $ENV{USER}\"\n";

obviously $pipe needs to be set to the path to the pipe where g15composer is listening.

Thank's Aneurysm9 but it's the same :( 
See my new script :
```
#!/usr/bin/perl -w

use strict;

my $user = "$ENV{USER}";
my $pipe = "$ENV{HOME}/g15lcd";
open(PIPE, ">>$pipe");

print "Hello $user\n";
print PIPE "TL \"Hello $user\"\n";
sleep 2;

print "Bye $user\n";
print PIPE "TL \"\" \"Bye $user\"\n";

sleep 2;

close(PIPE);
exit 0;
```

When I start it ( perl g15-perl.pl), Hello teeeff is displayed in the console then 2 sec after Bye teeeff and 2 sec after I take back control of the console and the 2 lines are displayed on the lcd only at this moment. It's like if g15composer don't run during the perl script.

I'm starting g15composer like this :
```
sudo nohup g15composer ~/g15lcd &
```
on the same console
What's wrong ?

---

### Post by TeeEff on 2007-05-09
I have done some other tests and it's seems that the pipe is readable only when is closed.
when I open the pipe before writing and close it after, that works

But it's not like this on the Amarok script. :confused:

---

### Post by Aneurysm9 on 2007-05-09
strange, though I do remember having similar trouble with a script I tried writing to tail dmesg output.  The only thing that seems even remotely likely connected to this is that the amarok script opens and closes another pipe before opening the pipe it normally writes to.  Maybe try opening a pipe, printing something random to it, and closing it before you try to write to the g15composer pipe.

As for the location of the lcdproc drivers, I'm not sure and I'm on my macbook right now so I can't check, but the first places I would look are under /usr/lib and /usr/local/lib for LCDd or lcdproc directories.

---

### Post by Dawnrazor on 2007-05-15
Hi

i have a problem with G15 macro

maybe i have the String "abc" on the G1 key and now i press the G1 key, then the output is abccccccccccccccccccccccccccccc... until i press the enter key

any idias?

---

### Post by Aneurysm9 on 2007-05-15
Dawnrazor,

That's a known issue.  I believe mlampard is working on it.  Sorry I can't tell you more.

---

### Post by sirel2 on 2007-05-16
For the repeating key fix, look at a post I made earlier on how to patch the source: [http://ubuntuforums.org/showthread.php?p=2461304](http://ubuntuforums.org/showthread.php?p=2461304)

I've been running it now for a couple weeks and it seems to work fine.

---

### Post by Dawnrazor on 2007-05-17
> **sirel2 said:**
> For the repeating key fix, look at a post I made earlier on how to patch the source: [http://ubuntuforums.org/showthread.php?p=2461304](http://ubuntuforums.org/showthread.php?p=2461304)

I've been running it now for a couple weeks and it seems to work fine.

Hey Thx that works !!!! :)

for all others they want to try this
dont forget
```
char configpath[1024];
```
in Line 72 :)

---

### Post by kanzie on 2007-06-05
I just cant figured out how I can get my g15 keyboard to work with WoW (World of Warcraft), neither the macro-keys, nor the LCD. Any takers?

---

### Post by spamalam on 2007-06-17
hello, i followed the instructions in the first post, there's a big clock on my keyboard, however i can't output to the screen:

% **g15daemon**
*An Error Occurred - 3 : ( Unable to configure the linux kernel UINPUT driver ) received*
% **modprobe uinput**
% **g15daemon**
% **g15daemon -version**
[i]G15Daemon version 1.2.7 - Loaded & Running
compiled with libg15 version 1.201[/i]
% **g15daemon**
[i]g15daemon is already running.  Use 'g15daemon -k' to kill the daemon before running again.
Exiting now[/i]

So its running, now:

% **echo 'TL "Hello" "World"' > ~/g15lcd**
% **g15composer ~/g15lcd**
[I]Error: No usable FIFO /root/g15lcd, aborting.
Segmentation fault
[/I]
thanks

---

### Post by drdnl on 2007-06-17
Don't follow the original post, its outdated. Follow [this one instead]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285")

-D

---

### Post by spamalam on 2007-06-17
does this not work with AMD64? :(  I get architecture errors :(

---

### Post by drdnl on 2007-06-17
I posted the amd64 debs somewhere, try a "search this thread" or compile them yourself with the above link.

---

### Post by kanzie on 2007-06-20
So basically it is not possible to use the LCD with WoW the way the keyboard really is marketed for? I tried it in windows and it is great. But the only way to sent statistics to the screen is through the g15daemon which requires me to send shell-commands, which I cant through LUA-scripts...or?

---

### Post by Aneurysm9 on 2007-06-20
I've never worked with lua, but if it can open a file and write to it then you can use g15composer.  As for using Windows programs on Linux and having the LCD work as it would under Windows, not likely to happen.  It would probably be possible to write a replacement for the Windows utils from Logitech, but the license on their SDK wouldn't allow us to do that.  It would require clean-room reverse engineering and even then I'm not really sure how useful it would be.

---

### Post by news-blitz on 2007-06-28
This is my first post and I'm desperate by now so please help me with this.
I've got my G15 LCD screen to work and it's showing the clock; the " echo 'TL "Hello" "World"' > ~/g15lcd
" works too.
I'm using:
Ubuntu 7.04 and nVidia drivers;
g15composer 3.1-1;
g15daemon 1.2.7-1;
g15display 1.0.1;
g15lcd 1.2-3;
libg15 1.2.2-1;
libg15render 1.2-1.

So please tell me how to get the G1-18 and M1-3, MR work!
I've tried installing with wine but that's no good. I'm new to linux and I want to make the macros to work. The Amarok script is working too using 210-amarok-g15-dcop_cli.pl. Please Help.
Thank You!!!

---

### Post by Aneurysm9 on 2007-06-28
Macro key support is still sortof a work in progress.  You'll need to get g15daemon-1.9 and g15macro from svn and compile them yourself.

---

### Post by jusmurph on 2007-06-29
Does this work on the AMD64 Arch?

---

### Post by news-blitz on 2007-06-29
> **Aneurysm9 said:**
> Macro key support is still sortof a work in progress.  You'll need to get g15daemon-1.9 and g15macro from svn and compile them yourself.

Thanks for your answer! Can you tell me how to compile them? Because when I install g15daemon-1.9-1.src.rpm using alien to make it .deb I can't type g15daemon in the terminal it says command not found.



coolwatch@Desktop:~/Desktop$ sudo alien -d g15daemon-1.9.0-1.src.rpm
Password:
g15daemon_1.9.0-2_i386.deb generated
coolwatch@Desktop:~/Desktop$ g15daemon
bash: g15daemon: command not found
coolwatch@Desktop:~/Desktop$ 

The same with the source. Thank You!

**_Got it working. Nice clock, but are there any more applets for this?_**

---

### Post by news-blitz on 2007-06-29
> **sirel2 said:**
> Here is a possible fix for the repeating macro issue.  The problem occurs when HAVE_X11_EXTENSIONS_XTEST_H is true and is caused because the last character that is pressed never sends the release to X11.   

I modified my g15macro.c to always record a key release (but only display it for the special keys).  Your mileage might vary and I have only tested this for a short while, but it seems stable enough...  

I followed the directions in [http://ubuntuforums.org/showthread.php?p=2461304]("http://ubuntuforums.org/showthread.php?p=2461304") 
to get the g15daemon running using the **1.9.0 pre 2.0** version of g15daemon.

```

void xkey_handler(XEvent *event) {

    static unsigned long lasttime;
    unsigned char keytext[256];
    unsigned int keycode = event->xkey.keycode;
    int press = True;
    int display = True;

    if(event->type==KeyRelease){ // we only do keyreleases for some keys
      pthread_mutex_lock(&x11mutex);
      KeySym key = XKeycodeToKeysym(dpy, keycode, 0);
      pthread_mutex_unlock(&x11mutex);
        switch (key) {
            case XK_Shift_L:
            case XK_Shift_R:
            case XK_Control_L:
            case XK_Control_R:
            case XK_Caps_Lock:
            case XK_Shift_Lock:
            case XK_Meta_L:
            case XK_Meta_R:
            case XK_Alt_L:
            case XK_Alt_R:
            case XK_Super_L:
            case XK_Super_R:
            case XK_Hyper_L:
            case XK_Hyper_R:
                break;
            default: 
                display = False;
                break;
        }
        press = False;
    }
    if(recording){
        current_recording.recorded_keypress[rec_index].keycode = keycode;
        current_recording.recorded_keypress[rec_index].pressed = press;
        current_recording.recorded_keypress[rec_index].modifiers = event->xkey.state;
        if(rec_index==0)
            current_recording.recorded_keypress[rec_index].time_ms=0;
        else
            current_recording.recorded_keypress[rec_index].time_ms=g15daemon_gettime_ms() - lasttime;
        rec_index++;

        /* now the default stuff */
        pthread_mutex_lock(&x11mutex);        
        XUngrabKeyboard(dpy,CurrentTime);
        pthread_mutex_unlock(&x11mutex);

        if(display == True) {
           fake_keyevent(keycode,press,event->xkey.state);
        }

        pthread_mutex_lock(&x11mutex);
        XGrabKeyboard(dpy, root_win, True, GrabModeAsync, GrabModeAsync, CurrentTime);
        XFlush(dpy);

        strcpy((char*)keytext,XKeysymToString(XKeycodeToKeysym(dpy, keycode, 0)));
        pthread_mutex_unlock(&x11mutex);        

        if(display == True) {
           if(0==strcmp((char*)keytext,"space"))
               strcpy((char*)keytext," ");
           strcat((char*)recstring,(char*)keytext);
           g15r_renderString (canvas, (unsigned char *)recstring, 0, G15_TEXT_MED, 80-((strlen((char*)recstring)/2)*5), 22);
           g15_send(g15screen_fd,(char *)canvas->buffer,G15_BUFFER_LEN);
        }

    }else
        rec_index=0;

        lasttime = g15daemon_gettime_ms();
}
```

Also, I moved the save routine to write out the configuration every time a new macro is recorded.  
```

void *Lkeys_thread() {
...
                default:
                    if(keystate >=G15_KEY_G1 && keystate <=G15_KEY_G18){
                        if(recording==1){
                            record_complete(keystate);
                            recording = 0;
                             pthread_mutex_lock(&x11mutex);
                             XUngrabKeyboard(dpy,CurrentTime);
                             XFlush(dpy);

                             /* Write configuration every time a macro is recorded*/
                             config_fd = open(configpath,O_CREAT|O_WRONLY|O_SYNC,0600);
                             write(config_fd,mstates[0],sizeof(mstates_t));
                             write(config_fd,mstates[1],sizeof(mstates_t));
                             write(config_fd,mstates[2],sizeof(mstates_t));
                             close(config_fd);

                             pthread_mutex_unlock(&x11mutex);
                        } else {
                            macro_playback(keystate);
                        }
                    }
                    break;
            }
            keystate = 0;
        }
    }
    return NULL;
}


```


The diff is as follows:  (diff -w)
```

72d71
< char configpath[1024];
442,446d440
<     config_fd = open(configpath,O_CREAT|O_WRONLY|O_SYNC,0600);
<     write(config_fd,mstates[0],sizeof(mstates_t));
<     write(config_fd,mstates[1],sizeof(mstates_t));
<     write(config_fd,mstates[2],sizeof(mstates_t));
<     close(config_fd);
472d465
<     int display = True;
495,496c488
<                 display = False;
<                 break;
---
>                 return;
497a490
> 
515d507
<         if(display == True) {
517d508
<         }
522d512
< 
525,526d514
< 
<         if(display == True) {
532d519
<         }
611a599
>     char configpath[1024];


```

Request:

[B]I've got the repeating macro problem, got the first 2 parts done, but what do I have to do with that 
"The diff is as follows" code because I'm new to this?????. Can I make the g15deamon keep the settings, because every time I restart it get's back to that huge clock not the clock and date display that I want?? Please help. [/B]
Thank You and all the developers!!!

---

### Post by miragul on 2007-06-29
I now have my G15 working on my laptop with Feisty, since I have a USB KVM I need hotplug support and so I thought I would post a complete howto for Feisty + G15.
Currently there are no pre-packaged utilities for 64 bit OS, if you have amd64 architecture you will have to compile your own packages, if you have 32 bit OS then follow this guide.

1.  Install dependencies: 
[INDENT]sudo apt-get install libusb-dev libdaemon-dev[/INDENT]
2.  Download [http://ubuntuforums.org/attachment.php?attachmentid=20721&d=1165545285](http://ubuntuforums.org/attachment.php?attachmentid=20721&d=1165545285) (you might have to register)
3.  Extract by using: 
[INDENT]tar -jxf g15tools.debs.tar.bz2[/INDENT]
4.  Install packges: 
[INDENT]sudo dpkg -i libg15_1.1-1_i386.deb libg15render_1.1.1-1_i386.deb libg15daemon-client_1.2.6a-1_i386.deb g15daemon_1.2.6a-1_i386.deb g15composer_3.0.2-1_i386.deb[/INDENT]
5. Auto load module uinput at startup by issuing the following command:
[INDENT]sudo echo "uinput" >> /etc/modules[/INDENT]
6. Locate the name for your G15 (they differ based on versions and layouts,  this sample uses a 105 key layout), do this by first hotplugging your keyboard and then do: 
[INDENT]cat /var/log/messages | grep G15[/INDENT]
6.1 Look for two lines like these, and located a dev path like /class/input/inpu23:
[INDENT]Jun 29 09:42:03 earl-laptop kernel: [  848.932000] input: **G15 Keyboard G15 Keyboard **as **/class/input/input23**
Jun 29 09:42:03 earl-laptop kernel: [  848.932000] input,hiddev98: USB HID v1.11 Keypad [**G15 Keyboard G15 Keyboard**] on usb-0000:00:1d.1-2.1.4[/INDENT]
6.2  Verify the device name of the keyboard by using the device path: 
[INDENT]udevinfo -a -p YOUR_DEV_PATH (example: udevinfo -a -p /class/input/input40)[/INDENT]
6.3 Find the Id's from a section similar to this one:
[INDENT]looking at device '/class/input/input147':
    KERNEL=="input147"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{uniq}==""
    ATTR{phys}=="usb-0000:00:1d.1-2.1.4/input0"
    ATTR{name}=="**G15 Keyboard G15 Keyboard**"

7. Write a UDEV rule to run activate the g15daemon on demand when hotplugged, use the idProduct and idVendor numbers as shown here:
[INDENT]echo 'SYSFS{../name}=="G15 Keyboard G15 Keyboard", SYMLINK+="input/g15", RUN+="/usr/local/bin/g15daemon-hotplug"' >> /etc/udev/rules.d/98-logitech.rules[/INDENT]
8. Edit g15daemon-hotplug and make it look like the following example : sudo gedit  /usr/local/bin/g15daemon-hotplug
[INDENT] 
#!/bin/bash
# start/stop g15daemon when plugged/unplugged
case $ACTION in
[INDENT]        "add")
            [INDENT]    # G15 being plugged, start g15daemon
                sudo g15daemon -k &
                sleep 1;sudo g15daemon &
                ;;[/INDENT]
        "remove")
            [INDENT]    # G15 being unplugged, kill g15daemon
                sudo g15daemon -k &
                ;;[/INDENT]
        *)
         [INDENT]       exit 0
                ;;[/INDENT][/INDENT]
esac

[/INDENT]
9. sudo /etc/init.d/udev restart

---

### Post by news-blitz on 2007-06-30
Can someone please help me with this? I've got the repeating macro problem and I don't know how to solve it. I've got the first 2 parts given by sirel2 but I don't know what to do with that diff -w. Please help me!
Thanks in advance!

---

### Post by Aneurysm9 on 2007-06-30
> **news-blitz said:**
> Can someone please help me with this? I've got the repeating macro problem and I don't know how to solve it. I've got the first 2 parts given by sirel2 but I don't know what to do with that diff -w. Please help me!
Thanks in advance!

man patch

---

### Post by news-blitz on 2007-07-01
> **Aneurysm9 said:**
> man patch

Can you please tell me how can I do that? I'm new to this and I don't know.

---

### Post by jusmurph on 2007-07-01
anthonii@smurph:~$ sudo g15daemon
An Error Occurred - 3 : ( Unable to configure the linux kernel UINPUT driver ) received



I get the above error.

---

### Post by Aneurysm9 on 2007-07-02
news-blitz:

*man* is a program that displays manual pages for other programs.  *patch* is a program that modifies a set of files based on a patchfile created by *diff*.  Since your question was how to make use of the diff that had been posted earlier, I thought I'd teach you how to fish rather than simply feed you for a day.  At a console, type "man patch" and you will get information on the *patch* program and how to use it.

jusmurph:

Looks like you don't have the uinput module loaded.  try: sudo modprobe uinput

---

### Post by news-blitz on 2007-07-02
I tried to patch the file and this is what I got:
> 
patch g15macro.c g15macro-patch
patching file g15macro.c
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 FAILED at 72.
Hunk #2 FAILED at 441.
Hunk #3 FAILED at 466.
Hunk #4 FAILED at 488.
Hunk #6 FAILED at 508.
Hunk #7 FAILED at 509.
Hunk #8 succeeded at 512 (offset -1 lines).
Hunk #9 FAILED at 514.
Hunk #10 FAILED at 519.
Hunk #11 succeeded at 598 (offset -1 lines).
8 out of 11 hunks FAILED -- saving rejects to file g15macro.c.rej

And g15macro-patch is:
> 72d71
< char configpath[1024];
442,446d440
<     config_fd = open(configpath,O_CREAT|O_WRONLY|O_SYNC,0600);
<     write(config_fd,mstates[0],sizeof(mstates_t));
<     write(config_fd,mstates[1],sizeof(mstates_t));
<     write(config_fd,mstates[2],sizeof(mstates_t));
<     close(config_fd);
472d465
<     int display = True;
495,496c488
<                 display = False;
<                 break;
---
>                 return;
497a490
> 
515d507
<         if(display == True) {
517d508
<         }
522d512
< 
525,526d514
< 
<         if(display == True) {
532d519
<         }
611a599
>     char configpath[1024];

Thanks Aneurysm9, but really, I don't know how to do it. :(

---

### Post by Andy Pallett on 2007-07-02
Hi All,
I've gone through this entire thread but I still can't fix my G15 problem.

As far as I can see, I've installed all the correct packages. I have a large clock on my screen so I'm assuming there isn't a problem with the install packages. The problem is I can't get the Amarok script to work. I install the script (Found here: [http://www.ubuntuforums.org/attachment.php?attachmentid=17192&stc=1&d=1160410939&](http://www.ubuntuforums.org/attachment.php?attachmentid=17192&stc=1&d=1160410939&)) and nothing happens when I start the script. The clock just stays on the LCD screen and nothing appears to happen.

Any troubleshooting advice would be great :) (I'm running ubuntu 7.04)

Thanks,
Andy

---

### Post by Spartan.II.117 on 2007-07-02
does the MR button Light up? does pressing the MR button switch over to the amarok script?

---

### Post by news-blitz on 2007-07-06
Can someone please help me with that manual patch so I can get the g15macro work properly without that repeating problem?
Thanks!

---

### Post by Andy Pallett on 2007-07-07
> **Spartan.II.117 said:**
> does the MR button Light up? does pressing the MR button switch over to the amarok script?

The MR button isn't lit up, neither is M1 - But the Clock is still present and working on the screen.

Odd :(

---

### Post by zszafran on 2007-07-13
Okay everything was easy enough to install and works great. I have been looking everywhere for a way to get beep-media-player to display track information on my g15, but I havent been able to find anything. I was hoping that maybe someone could point me in the right direction here. Thanks in advance.

---

### Post by Crinos512 on 2007-07-13
> **drdnl said:**
> 
And if you really, really can't figure it out I attached the compiled debs for 7.04 386


I appreciate the debs, however I get an error "wrong architecture" ...I am running AMD64. you would not happen to have a compiled version for AMD64 would you? :)

EDIT:
I see that you have [here]("http://ubuntuforums.org/showthread.php?p=2236531&highlight=amd64#post2236531") now that I have read some more :)  can you verify they work on Feisty?

---

### Post by Aneurysm9 on 2007-07-13
If BMP can use xmms visualization plugins, you can use the xmms plugin for track info, etc.  Otherwise, someone will need to write a plugin for BMP or port the xmms plugin.

---

### Post by BlueStreak on 2007-07-14
I tried the script and everything seemed fine up til here:  

> *****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@mike-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ / ]
3 -  Version: [ 20070714 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ / ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

Can someone help with that?

---

### Post by Aneurysm9 on 2007-07-14
BlueStreak,

It looks like you're running checkinstall from / rather than from the source directory for whatever package you're trying to build.   Check that you're in the right path before you start the script.

---

### Post by BlueStreak on 2007-07-14
If I understand, you mean that since the packages are on my desktop I need to run the script from the desktop path, correct?  I tried that and got the same result.  I ran it from /home/mike/Desktop  which is where the files are.

---

### Post by Crinos512 on 2007-07-20
how do I ensure g15daemon runs on startup without having to **sudo** the command?

---

### Post by Spartan.II.117 on 2007-07-22
none of my special keys are working (MR, the ones under the LCD)

---

### Post by po0f on 2007-07-23
Crinos512,

Add it to /etc/rc.local:

```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Start up g15daemon
modprobe uinput || exit 1
/usr/local/sbin/g15daemon -s || exit 1

exit 0
```

It requires the full path to the g15daemon executable to start, your location may be different from mine.  :)

Oh, and I don't have any other fancy stuff working with it, just the clock.  If there are any other commands needed to get it started, just add them here as well, making sure to put them **before** (above) the `exit 0` line, which should be the last one in that script.


BlueStreak,

Yes, but are the actual source files scattered all over your Desktop, or are they in another directory in ~/Desktop?  Make sure you are in the correct directory before running `sudo checkinstall`.

---

### Post by Spartan.II.117 on 2007-07-23
i guess i should post my problem more clearly: i have re-installed ubuntu recently and re-installed the debs, but now none of the black keys under the lcd, nor the mr button work. is there any special configuration necessary for this?

---

### Post by BlueStreak on 2007-07-29
Thanks!  Put the files in their own directory on the desktop instead of scattered around like you said and it worked great.  Now just can't get the multimedia keys to work w/ Amarok.  I configured them in 'keyboard shortcuts' and 'global shortcuts' within Amarok.  The keys match in both places but nothing seems to be happening.

Nevermind, got 'em working!

---

### Post by Lattyware on 2007-08-10
I just wrote a script to put xChat highlights onto the G15's screen, thought I'd share it :D It's a plugin for xChat and requires working G15tools.
[http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz](http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz)

---

### Post by TakeshiKovacs on 2007-08-11
> **Lattyware said:**
> I just wrote a script to put xChat highlights onto the G15's screen, thought I'd share it :D It's a plugin for xChat and requires working G15tools.
[http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz](http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz)

I just downloaded your script, loaded it into xchat, it says: xChat G15 Keyboard Hilighter Plugin Ready! but it won't write anything into that g15in file that is specified at the beginning of your script. Any ideas what could be wrong?

---

### Post by Lattyware on 2007-08-12
> **TakeshiKovacs said:**
> I just downloaded your script, loaded it into xchat, it says: xChat G15 Keyboard Hilighter Plugin Ready! but it won't write anything into that g15in file that is specified at the beginning of your script. Any ideas what could be wrong?

Hmm... sounds odd. First of all, try downloading again, I've updated it to version V1.2, which does a few things better, like starting G15Composer automatically, which I think was probably you r problem, had you started G15Composer?

With the new version, just make sure that the two paths at the start of the script do not exist yet, and you have permissions to write to wherever it is. It should work if you have the clock going. The files should not exist (because one isn't actually a file, but rather a pipe), until the script is run. If it works, you don't need to keep deleting the files or anything.

So, after a lot of rambling:
Re-download here: [http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz](http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz)
Extract into the ~/xchat2/ directory, as you would any other plugin. Make sure it loads. I added a startup screen which displays from starting it to your first highlight, so it should be obvious straight away. If it still doesn't work:
Make sure the files specified at the start are not there ('/tmp/g15in' and '/tmp/g15out' if I remember correctly) and that the script can write there. Try changing the location to somewhere else (the files can be anywhere and called anything) if it still doesn't work.

Edit: I have another version coming soon which uses pipes properly, and should work a lot better in general. Watch this space.

So yes, I have updated to V1.2 - which works great for me. It now automatically starts and kills G15Composer as you start and close xChat, which is far more efficient than the old way. I also added a new startup screen, and a few more config options. This is still a very hackish script. I'm sure I'm not doing it the way it's meant to be done, but it works for me (and I presume others), and that's the main thing.

I'm considering attempting a plugin for Deluge-Torrent next. There is a lack for stuff supporting the G15 under linux, I want to see that change.

---

### Post by Lattyware on 2007-08-13
Edit: Yet another upgrade to 2.5 - Same link, added a few new features like the ability to flash the LCD's backlight when you get highlighted (really grabs your attention well.).

OK, I just upgraded the file ([http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz]("http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz"))  To V2.0.

This is a complete rewrite, and is a hell of a lot better. There are reasons why the old one may not have worked for some, so this should work a lot  better. It includes loads more features, here is an extract from the comments in the source:

V2.0 is much, much better than the origonal. It uses pipes properly, fixes some critical bugs, and is a lot better in every way due to the fact the actual python it is made in is a lot cleaner and nicer to use. It also has a proper config file (~/home/.xchat2/HG15/config.txt). The config allows full customisation of what is sent to the screen, with a number of variables.

Not noted there is I included the ability to send queries to the screen even if you are not highlighted by it.

Just download and follow the readme to install.

It's all my code again, and it's GPL3d.

I will probably update soon with any fixes I find, and any extra variables I add to make the string sent to the screen more customizable.

Please tell me about anything you find, difficulties you have, or if it works.

---

### Post by Spartan.II.117 on 2007-08-14
i'm trying to write a script for the media player exaile to show data on the g15, but i have no idea where to start, i've attached a plug-in (perl script) that can get the data out of exaile, i just don't know how to get it into the g15. can anyone give me any pointers?

---

### Post by Lattyware on 2007-08-14
> **Spartan.II.117 said:**
> i'm trying to write a script for the media player exaile to show data on the g15, but i have no idea where to start, i've attached a plug-in (perl script) that can get the data out of exaile, i just don't know how to get it into the g15. can anyone give me any pointers?

Check out [http://perl.active-venture.com/pod/perlipc-pipes.html](http://perl.active-venture.com/pod/perlipc-pipes.html)
and do a 'man G15Composer' - also remember you have to pass a newline after the command to get it to do the command, that one got me to begin with.

All you have to do is pass the right commands, it takes some getting used to, but is easy enough. If you check out my script, you can get the idea, it's in python, but It might help you understand. Look at the lcdconnection class - that's the important bit.

---

### Post by Spartan.II.117 on 2007-08-14
wow, i did not understand a thing on that link... btw i am not a coder, i was just trying to hack together a script that would get my data to the g15, i don't care if i have to use lcdproc (which i have running for a bunch of folding at home scripts distributed throughout our network.) i just want data without having to turn on my monitor.

---

### Post by Lattyware on 2007-08-14
> **Spartan.II.117 said:**
> wow, i did not understand a thing on that link... btw i am not a coder, i was just trying to hack together a script that would get my data to the g15, i don't care if i have to use lcdproc (which i have running for a bunch of folding at home scripts distributed throughout our network.) i just want data without having to turn on my monitor.
OK, basically you need to add something like this to your script: and then make sure g15composer is listening to .g15input. Simple as that.
    chdir; # go home
    $FIFO = '.g15input';

    while (1) {
	unless (-p $FIFO) {
	    unlink $FIFO;
	    system('mknod', $FIFO, 'p')
		&& die "can't mknod $FIFO: $!";
	}

	# next line blocks until there's a reader
	open (FIFO, "> $FIFO") || die "can't write $FIFO: $!";
	print FIFO "<insert commands from man g15composer";
	close FIFO;
	sleep 2;    # to avoid dup signals
    }

---

### Post by Futsuriai on 2007-08-17
Hello,

Anyone else getting that the amarok script slowly displaces itself across the screen? It may be in this thread but I have not been able to find it. 

Thanks :)

Also something I found useful when everything seemed installed but the amarok script wouldn't run is removing .g15amaroklcdpipe and reinstalling g15composer and the script

---

### Post by Aneurysm9 on 2007-08-17
Futsuriai:

It's a known issue.  I've seen it with lcdproc as well.  It seems to occur under heavy load and is probably related to the way g15daemon handles screen data coming over the wire.  There's no fix for it currently.

---

### Post by flugheim on 2007-08-18
hi
when trying to load the xchat script i get this:
>  Prefrences Loaded
 Error in sys.excepthook:
 Traceback (most recent call last):
   File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
     import apport.report, apport.fileutils
   File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
     from apport.report import Report
   File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
     from problem_report import ProblemReport
   File "/var/lib/python-support/python2.5/problem_report.py", line 17, in <module>
     from email.MIMEMultipart import MIMEMultipart
 ImportError: No module named email.MIMEMultipart
 
 Original exception was:
 Traceback (most recent call last):
   File "/home/flugheim/.xchat2/G15H.py", line 304, in <module>
     lcd = lcdconnection(prefs)
   File "/home/flugheim/.xchat2/G15H.py", line 113, in __init__
     self.pipe = os.open(prefs.value("path"), os.O_WRONLY)
   File "/home/flugheim/.xchat2/G15H.py", line 168, in errorhandle
     raise IOError, "Couldn't open!"
 IOError: Couldn't open!
 Error loading module /home/flugheim/.xchat2/G15H.py

---

### Post by Lattyware on 2007-08-18
OK, that means it cannot open the pipe to G15Composer.

Make sure that G15composer is working ('g15composer /tmp/g15in' works), and that G15Daemon is running when you start the script (you have a clock on the screen when you start xChat).

If g15composer does not work, try changing the file you are using for the pipe (try /home/user/g15in say, or anything you can write to) and see if it will work then. If it does, change the path in the config file to reflect this.

When you start it g15composer should not be running, as it is started by the script. If for some reason 'g15composer /tmp/g15in' works and the script doesn't while G15Daemon is running, then you can allways add that command to sessions to start it at boot, and then turn off starting and stopping g15composer in the config file.

Hope that makes it work, if not, feel free to contact me here or via any IM service. And also, do tell me if you get it working.

---

### Post by flugheim on 2007-08-18
The daemon is running, but the output of g15composer is not good:
> flugheim@flugheim-laptop:~$ g15composer /tmp/g15in
g15composer: error while loading shared libraries: libg15render.so.1: cannot open shared object file: No such file or directory


ps: added you in msn

---

### Post by Lattyware on 2007-08-18
Yeah... Sounds like a problem with your G15Tools install, have you tried reinstalling them from source?

---

### Post by flugheim on 2007-08-18
Hi
i thought i should try to do a clean install, som i uninstalled all the g15 stuff, but now after installing g15daemon and libg15, i get this:
> flugheim@flugheim-laptop: $ g15daemon 
An Error Occurred - 1 : ( Unable to write to PID file ) received


---

### Post by Lattyware on 2007-08-20
Odd.. Sorry, I don't know enough about G15tools to tell you your problem there, best to wait for someone who is actually on the team making them.

---

### Post by tomcat-55 on 2007-08-26
Tried everythin to get this working but just wont. Im running it on 32 bit Fawn. Cant get it to display anythng.

> g15daemon: error while loading shared libraries: libg15.so.1: cannot open shared object file: No such file or directory


---

### Post by robynhub on 2007-09-04
Hello everyone! I'm another developer of g15tools and g15daemon projects.
In the past weeks i' ve worked a lot on the xmms and audacious plugins 
and now are pretty stable so...

Here there are debs for the xmms and audacious plugin of g15daemon. Enjoy it!

Take a look:

[[IMG]http://img372.imageshack.us/img372/5907/screenshotgl5.th.png[/IMG]](http://img372.imageshack.us/my.php?image=screenshotgl5.png)

[[IMG]http://img465.imageshack.us/img465/5248/webcam1188983318gj7.th.png[/IMG]](http://img465.imageshack.us/my.php?image=webcam1188983318gj7.png)

(Thanks to VON_CAPO for the images)

NOTE: Works better if you use the latest version of g15daemon (aka g15daemon-wip aka g15daemon 2.0). You can download it on [http://sourceforge.net/projects/g15daemon](http://sourceforge.net/projects/g15daemon)
This new version have hi-speed refresh timing that is a perfect marriage with those plugins. :D

NOTE: For compatibility reasons i've removed all dipendence from others packages. But they need g15daemon e libg15render installed!

If you want compile it from source, it can be found at:
[http://sourceforge.net/project/showfiles.php?group_id=172261](http://sourceforge.net/project/showfiles.php?group_id=172261)

Tell me if something goes wrong.

I'm try to understand how submit those packages (g15tools and g15daemon too) to the official ubuntu repos. Anyone have an idea?

Bye.

---

### Post by VON_CAPO on 2007-09-05
I tried to install **g15daemon-xmms_2.5.2-1_i386.deb**, but I was getting the following error:

"Error: Dependency is not satisfiable: **libg15daemon-client**"

I googled it, but I did not find any link to download it.

---

### Post by robynhub on 2007-09-05
> **VON_CAPO said:**
> I tried to install **g15daemon-xmms_2.5.2-1_i386.deb**, but I was getting the following error:

"Error: Dependency is not satisfiable: **libg15daemon-client**"

I googled it, but I did not find any link to download it.

I've removed all the dipendencies in the packages. try the new one.

Of course you did't find it! :D No one has build that packages before me! :D 
Those packages were build 2 days ago!

Tell me if not work.

---

### Post by aussiedini on 2007-09-05
Thanks Robynhub, fan...freakin...tastic

---

### Post by VON_CAPO on 2007-09-05
It works!!!   \\:D/

Take a look:

[[IMG]http://img372.imageshack.us/img372/5907/screenshotgl5.th.png[/IMG]](http://img372.imageshack.us/my.php?image=screenshotgl5.png)

[[IMG]http://img465.imageshack.us/img465/5248/webcam1188983318gj7.th.png[/IMG]](http://img465.imageshack.us/my.php?image=webcam1188983318gj7.png)

Bravo!!! =D>

By the way, is there any possibility to use sharp fonts?

---

### Post by robynhub on 2007-09-05
> **VON_CAPO said:**
> It works!!!   \\:D/

Take a look:

snip.

Bravo!!! =D>

By the way, is there any possibility to use sharp fonts?

Unfortunately no. The number of pixel are fixed :D
I'm glad you like it. There is lot of work on it. :)

ps. Works better if you use the latest version of g15daemon (aka g15daemon-wip aka g15daemon 2.0). You can download it on [http://sourceforge.net/projects/g15daemon](http://sourceforge.net/projects/g15daemon)
pps. Have you checked the configuration and about dialogs?

Feedbacks wellcome!

---

### Post by VON_CAPO on 2007-09-05
> **robynhub said:**
> U
ps. Works better if you use the latest version of g15daemon (aka g15daemon-wip aka g15daemon 2.0). You can download it on [http://sourceforge.net/projects/g15daemon](http://sourceforge.net/projects/g15daemon)
pps. Have you checked the configuration and about dialogs?

Feedbacks wellcome!
I will give a try to this new version; but,  because I am a little bit lazy, to install from the terminal does not appeal to me like a DEB file. :lolflag:

About the configuration files: I found the directory **/usr/share/doc/g15daemon** with a lot of  info. I will take a look.

---

### Post by VON_CAPO on 2007-09-07
> **robynhub said:**
> Works better if you use the latest version of g15daemon (aka g15daemon-wip aka g15daemon 2.0). You can download it on [http://sourceforge.net/projects/g15daemon](http://sourceforge.net/projects/g15daemon)
Feedbacks wellcome!

Today XMMS was freezing at startup, so, I did  ---> **sudo g15daemon -k**  (to kill the G15 daemon)
I started XMMS again and it was running fine.

Then I decided to follow your advise and to install the new version **g15daemon-1.9.0.tar.bz2** and VOILA!
XMMS is working smoothly again.

By the way, I was playing with the configuration dialog for the LCD screen... you did a superb job. :)

---

### Post by Spartan.II.117 on 2007-09-07
anyone want to greate debs of the new packages for amd64? i'm still a noob and dont want to mess anything up (this message brought to you by a machene that went down yesterday due to pebkac)

---

### Post by VON_CAPO on 2007-09-07
> **Spartan.II.117 said:**
> anyone want to greate debs of the new packages for amd64? i'm still a noob and dont want to mess anything up (this message brought to you by a machene that went down yesterday due to pebkac)
As you can see here ---> **[http://sourceforge.net/project/showfiles.php?group_id=172261](http://sourceforge.net/project/showfiles.php?group_id=172261)** , all the files are **"Platform-Independent"**, they will work in any AMD64.

Here ---> **[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)** , you can find out how to install those files.

It is not difficult. :)

---

### Post by Spartan.II.117 on 2007-09-08
where do i find libg15?

---

### Post by sgleo87 on 2007-09-09
> **drdnl said:**
> sglee:

Think you forgot to install libfreetype6-dev (or something like that, if not, look in synaptic)

Actually, more specifically, I think you forgot to "enable-ttf" *all* the needed dependencies. Try following my compilation instructions [one page back.]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285")

After following the new instructions I was finally able to install all the packages with --enable ttf successfully.
But even when using the new amarok script I still have the same problem: clock works but not the amarok script. I can see "g15 composer" in the display and then the time bar but no artist and title, just black. 
I even checked the directory that the script uses for the true type fonts and they are all there so that can't be the problem....does anybody have any ideas on how to solve this? :confused:

---

### Post by Lattyware on 2007-09-13
Just to note I updated (a while back) my [G15 Highlighter Script]("http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz") to v2.6 - which includes a number of things. I've had it running stably at this version, and I think it incorporates all features I could want, and has not had any problems. If you want a feature or have a problem, please contact me, and I'd be happy to see about implementing/fixing it.

v2.6 allows a lot more fine-tuning of what goes on via the config file - you can change the way it works a lot.

Hope that someone gets some use out of it. I must say, I find it great, even if I do say so myself.

---

### Post by VON_CAPO on 2007-09-13
> **Lattyware said:**
> Just to note I updated (a while back) my [G15 Highlighter Script]("http://lattyware.co.uk/OtherFiles/G15Highlighter.tar.gz") to v2.6 - which includes a number of things. I've had it running stably at this version, and I think it incorporates all features I could want, and has not had any problems. If you want a feature or have a problem, please contact me, and I'd be happy to see about implementing/fixing it.

v2.6 allows a lot more fine-tuning of what goes on via the config file - you can change the way it works a lot.

Hope that someone gets some use out of it. I must say, I find it great, even if I do say so myself.
I installed your script, but I have no idea how to make it to work.
I am not a coder, and most of the settings in the config file are beyond my comprehension.  I mean, they are commented, but it is not enough for a simple user like me. :confused:

Anyway, I will show how is the problem:

I loaded XChat
[[IMG]http://img401.imageshack.us/img401/6813/71707228qh3.th.png[/IMG]](http://img401.imageshack.us/my.php?image=71707228qh3.png)

Your script took over the LCD sceen
First the splash
[[IMG]http://img401.imageshack.us/img401/709/webcam1189720590zr8.th.png[/IMG]](http://img401.imageshack.us/my.php?image=webcam1189720590zr8.png)

and next this
[[IMG]http://img208.imageshack.us/img208/6858/webcam1189720437qp2.th.png[/IMG]](http://img208.imageshack.us/my.php?image=webcam1189720437qp2.png)

and nothing else happens.

Also, if I start XMMS your script is wiped out from the screen and the XMMS script takes over. 
Is there some way to switch among scripts?

---

### Post by Aneurysm9 on 2007-09-16
> **VON_CAPO said:**
> Also, if I start XMMS your script is wiped out from the screen and the XMMS script takes over. 
Is there some way to switch among scripts?

They should all be using g15daemon, so you can switch between them with either MR or L1, depending on how you started g15daemon.

---

### Post by VON_CAPO on 2007-09-17
> **Aneurysm9 said:**
> They should all be using g15daemon, so you can switch between them with either MR or L1, depending on how you started g15daemon.

Thank you for your answer.
Those buttons are not enabled in my keyboard. 
And I am confess I did not read the whole thread (40 pages is a lot).
But I will search into it to find how to do it.
Thanks for the info . :)

---

### Post by Lattyware on 2007-09-22
OK, the script is working fine, by the looks of it. When you get highlighted (someone says your name, or anything on the highlight list in your preferences) it should appear on the screen. The freenode version request shows up as the script shows PMs.

As to the config, I'm sure most would be happy with the default settings. You will find better explanations here though:

[http://www.lattyware.co.uk/G15H/](http://www.lattyware.co.uk/G15H/)

---

### Post by mmafterme on 2007-09-30
Regarding this: [http://ubuntuforums.org/showpost.php...&postcount=289](http://ubuntuforums.org/showpost.php...&postcount=289) I'm completely retarded because I don't know what to do with the additions to the related g15macro.c file. I konw that adding the lines directly into the file doesn't work so what do I do?

---

### Post by Aneurysm9 on 2007-09-30
> **mmafterme said:**
> Regarding this: [http://ubuntuforums.org/showpost.php...&postcount=289](http://ubuntuforums.org/showpost.php...&postcount=289) I'm completely retarded because I don't know what to do with the additions to the related g15macro.c file. I konw that adding the lines directly into the file doesn't work so what do I do?

You mangled that URL when you copied it, so I can't see the post tow which you were referring, but I assume you're talking about the patch for g15macro.c.  You'll need to use the patch utility.  Typical syntax is something like:

```
patch -p0 < g15macro.patch
```

You may need to change -p0 to -p1 or -p2, depending on how the patch was created.  You'll most likely need to run it from within the directory where g15macro.c is stored.  Also, have you checked the latest SVN version of g15macro?  I think mlampard may have already applied this patch there.

---

### Post by obsrv on 2007-10-23
Where can I find g15 debs 64bit?

---

### Post by johnt91 on 2007-11-04
hi, i have installed the g15 components according to this; [http://ubuntuforums.org/showpost.php?p=2461304&postcount=285](http://ubuntuforums.org/showpost.php?p=2461304&postcount=285), and i am trying to use the new amarok script, but i only see the progress/time bar, no track names.

amarok coughs up this

Name "main::G15COMPOSER" used only once: possible typo at /home/john/.kde/share/apps/amarok/scripts/210-amarok-g15-dcop_cli.pl line 12.

any ideas

running

ubuntu 7.10 x64

jt

---

### Post by drdnl on 2007-11-07
Hi Johnt91,

that usually has to do with missing truetype support, try searching this thread for truetype and you should be able to figure it out.

Also, use the amarok script from the post you installed from, it's "pre-fixed"

---

### Post by Chebyshev on 2007-11-08
I don't know if anyone else has written one yet and I don't want to dig through this entire thread, but I have a working g15 plugin for Exaile written.

[http://ubuntuforums.org/showthread.php?t=607407](http://ubuntuforums.org/showthread.php?t=607407)

---

### Post by Spartan.II.117 on 2007-11-09
when i try to compile g15daemon for gutsy it tells me that libg15 is missing. where do i find that?

also i the project dead? there have been no updates to most components since February..

---

### Post by Aneurysm9 on 2007-11-14
You probably need libg15-dev if you're installing from packages.  If not, the source is all at g15tools.sf.net.  The project isn't dead, libg15 1.2.3 was released yesterday.  The other components are fairly stable and haven't needed new releases.  G15daemon 2.0 is still a work in progress but is fully functional if you wish to compile from SVN.

---

### Post by Anaximander Thales on 2007-11-16
I'll ask this here as there is no thread out there other than support questions for G15 -- but if the starters/maintainers of this thread would prefer me to split this off I will.

I'd like to set up the top row of the media keys (the round button, and four rectangles above the actual multimedia keys) as content sensitive buttons.  By this I mean, when a certain screen is displayed, pressing one of these buttons will change what content is on there.

Currently, I have the amarok script (from this thread), a kaffeine script I wrote from the amarok script, and a script that's displaying system information.  When the sys info is displayed, I'd like to be able to set these keys to flip through information.  I know the MR button will change the screens on the LCD, but I'd prefer not to have 5 different screens running to display this information.

So, to sum the question up to its simplest form -- is there a command line method to see which screen is currently displaying.  Can I query the pipe to see if it's being read, or is there a switch I can set in render that I could capture some piece of information?

Also, I could have sworn I saw some way to set the Round button (top left round button on the LCD panel set of keys) as the key to press to flip through screens instead of the MR button -- is this possible to do with the libG15* packages, or was I just dreaming this?

---

### Post by hejki on 2007-11-23
> **zszafran said:**
> Okay everything was easy enough to install and works great. I have been looking everywhere for a way to get beep-media-player to display track information on my g15, but I havent been able to find anything. I was hoping that maybe someone could point me in the right direction here. Thanks in advance.

just tested it out today and found out that it actually works, partially :). you just need to
```
sudo mkdir /usr/lib/bmp/Visualization; sudo cp /usr/lib/xmms/Visualization/libg15daemon_xmms_spectrum.* /usr/lib/bmp/Visualization/
```
shows the name of currently playing song + the spectrum, BUT you cannot configure it via bmp - it crashes :P
but it works as long as the default looks pleases you :)

---

### Post by Aneurysm9 on 2007-11-23
Anaximander Thales:

Currently, g15composer does not relay keypress information to scripts.  Pipes are a unidirectional communications channel except in some non-standard configurations that can't be expected to be available.  If you wish to have your program react to keypresses you will need to use g15daemon and libg15render directly.  You can look at the lcdproc driver or the xmms plugin for an example.  You could also look into implementing your script as an lcdproc client which would have the added benefit of making it available to people who use other LCD screens supported by lcdproc.

---

### Post by Nicram on 2007-11-27
Hardy has [packages for g15]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=g15&searchon=names&subword=1&version=all&release=all") in universe repo
it works in gutsy :)

---

### Post by scuz on 2007-11-28
Quick question, is there any way for plugins to snag on to "normal" keys? Namely I want to get at the media keys and volume wheel, but it looks to me like those are part of the "regular" keyboard and not handled with libg15.

Anybody know of a way to get at these keys via global shortcuts or something? If so any ideas on examples of global shortcuts in c code? Preferably something non gnome or kde specific :\

I'm working on an Amarok plugin right now(it's going slowly as I don't have my G15 yet so I can't actually test anything I've written :>) and I'd like to make it so that the plugin itself handles the keypresses for the media keys, so if I have another plugin up I can control other things, rather then just putting the global shortcuts in Amarok.

---

### Post by Aneurysm9 on 2007-11-28
Scuz:

That depends on how you're writing your plugin.  As you say, libg15/g15daemon doesn't handle the media keys so you'll need to find another way to do it.  If you're writing your plugin in C you can look at the g15daemon_XMMS plugin to see how they're handled there.  Otherwise, you're at the mercy of your scripting language.

---

### Post by scuz on 2007-11-28
> **Aneurysm9 said:**
> Scuz:

That depends on how you're writing your plugin.  As you say, libg15/g15daemon doesn't handle the media keys so you'll need to find another way to do it.  If you're writing your plugin in C you can look at the g15daemon_XMMS plugin to see how they're handled there.  Otherwise, you're at the mercy of your scripting language.

Awesome :D That's exactly what I want, thanks!

---

### Post by scuz on 2007-11-30
So I just got my G15 today, having a bit of a problem. Whenever I hit MR my computer hard locks and I have to reboot. Any ideas?

Edit: I'm running 1.9g15daemon 1.2.3libg15. It seems to randomly crash when I use the extra buttons in general, but the MR button does it every time. Should I grab 2.0 from svn? Or back down to the last version?

---

### Post by Aneurysm9 on 2007-11-30
Good news everyone!  G15Tools now has it's own forum at [http://www.g15tools.com/forum/](http://www.g15tools.com/forum/)

scuz:

That's a new one for me.  Try posting at the new forum and I'm sure mlampard will be there to help debug.

---

### Post by Tsume on 2007-12-12
(I'm not posting at the new forum because my password doesn't have a number and I don't like having to remember 600 different passwords)

I cannot get g15daemon-1.9.1 to install on my AMD64 gutsy.  

```
Installing with make install...

========================= Installation results ===========================
Making install in libg15daemon_client
make[1]: Entering directory `/home/tsumeone/Desktop/g15daemon-1.9.1/libg15daemon_client'
make[2]: Entering directory `/home/tsumeone/Desktop/g15daemon-1.9.1/libg15daemon_client'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libg15daemon_client.la' '/usr/lib/libg15daemon_client.la'
/usr/bin/install -c .libs/libg15daemon_client.so.1.0.2 /usr/lib/libg15daemon_client.so.1.0.2
/usr/bin/install: setting permissions for `/usr/lib/libg15daemon_client.so.1.0.2': No such file or directory

```

From the no such file or directory error it's all downhill and it eventually fails.

Why?  I'm following [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) and also previously tried using the script posted here to do the same, and got the same result.  Is 1.9.1 broken?

---

### Post by Aneurysm9 on 2007-12-12
That looks like the kind of problem you would have if you were lacking permission to write to /usr/lib.  How did you invoke make install?  You should be using `sudo make install` or running `make install` as root.

---

### Post by Tsume on 2007-12-12
I rebooted and it magically worked- go figure =P

I have a feeling I did what you said, forgetting the sudo part.  That sounds like something I'd do.

---

### Post by Frozen-Solid on 2007-12-26
Okay so I've been trying to get my new G15 working with Amarok and am having some issues.

For starters I've gotten all the g15 things installed and running.  I even started up the x-chat script to show hilights and that runs fine.  I can open a pipe to g15compser and send text no problem.

Amarok, however, is giving me issues.  I've tried both scripts and am having an issue with both of them:

For the first... I'm getting the error "This Perl hasn't been configured and built properly for the threads module to work.  (The 'useithreads' configuration option hasn't been used.)" when I try to run a script.  

For the second (the Gentoo one) I see G15Composer show up on my LCD screen, but nothing is ever sent to it.  The G15Composer text eventually just disappears leaving a blank screen.  I can manually send text through the pipe created with the script... but the script itself isn't sending anything.

Can anyone offer some tips to help me out here?

---

### Post by paratox on 2007-12-27
i don`t get the amarok script to work or ttf support, i don`t know.
i get the following errror:

[PHP]paratox@paratox:~/scripts$ ./amarok-g15
g15composer - PID: 6206
g15composer: symbol lookup error: g15composer: undefined symbol: g15r_ttfLoad
[/PHP]

i`ve installed from the actual sources with [PHP]./configure --prefix=/usr --enable-ttf[/PHP]
followed the actual howto, all necessary packages are installed.

os: kubuntu 7.10 gutsy

help me, please. can`t find a solution for this problem, already working days on it.

---

### Post by Aneurysm9 on 2007-12-27
Paratox:

libg15render didn't build with TTF support.  The configure check should have failed, can you paste the output of ./configure --enable-ttf?

---

### Post by ironstorm on 2007-12-29
I'm not too sure anyone cares at this point (looks like all the scripts use CLI)...  But I solved a few problems with DCOP::Amarok::Player.   It still doesn't install on my system, but it does briefly playing a song before failing.

Here are the steps:
```
sudo cpan install DCOP
sudo cpan install DCOP::Amarok
export DCOPSERVER=`dcopserver --serverid 2>&1` # get $USER's DCOP server
sudo chown -R $USER:$USER ~/.cpan && cpan install DCOP::Amarok::Player # sudo will fail authentication protocols, so must run as $USER... 
```

This fails out on PlayPause and Stop tests:
> Prepending /home/ged/.cpan/build/junoscript-perl-6.4I0/blib/arch /home/ged/.cpan/build/junoscript-perl-6.4I0/blib/lib to PERL5LIB.
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/1....ok 1/89
#   Failed test '   PlayPause'
#   in t/1.t at line 14.
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.
t/1....NOK 5
#   Failed test '   Stop'
#   in t/1.t at line 16.
#          got: ''
#     expected: '0'
# *** Amarok needs to be open.
t/1....ok 6/89# Looks like you planned 89 tests but only ran 85.
# Looks like you failed 2 tests of 85 run.
t/1....dubious
        Test returned status 2 (wstat 512, 0x200)
DIED. FAILED tests 4-5, 86-89
        Failed 6/89 tests, 93.26% okay
Failed Test Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1.t          2   512    89   10  11.24%  4-5 86-89
 (55 subtests UNEXPECTEDLY SUCCEEDED).
Failed 1/1 test scripts, 0.00% okay. 6/89 subtests failed, 93.26% okay.
make: *** [test_dynamic] Error 2
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force


My system is Kubuntu 7.10 Gutsy / AMD64...  

The machine is a fast dual core2, so maybe this is something of a timing issue rather then a real bug?

-G

---

### Post by ironstorm on 2007-12-29
Apply this patch to ~/.cpan/build/DCOP-Amarok-Player-0.036/1.t: 
```

--- 1.t~        2006-04-03 23:12:45.000000000 -0400
+++ 1.t 2007-12-29 15:56:20.000000000 -0500
@@ -11,10 +11,10 @@
        skip( "Only works when amarok is installed", 6 )
                unless ( `amarok --version` );

-       is( $player->playPause(), 0, "   PlayPause" ) or
-               diag( "*** Amarok needs to be open." );
-       is( $player->stop(),      0, "   Stop" ) or
-               diag( "*** Amarok needs to be open." );
+#      is( $player->playPause(), 0, "   PlayPause" ) or
+#              diag( "*** Amarok needs to be open." );
+#      is( $player->stop(),      0, "   Stop" ) or
+#              diag( "*** Amarok needs to be open." );
 }

 can_ok( $player, 'playPause' );
```

then `cd ~/.cpan/build/DCOP-Amarok-Player-0.036 && sudo make install`

And it will install...    The old script fails to open lcdpipe, but that's a g15 thing not a DCOP/Amarok thing.

---

### Post by HmKaY on 2007-12-29
I installed eveything, the clock is working perfectly.

But, I installed the amarok support scripts. The first one only shows on the display the time, and everything else is black. The second script shows a blank LCD-screen.

Are there any new scripts? I dont want to scroll thru the whole 42 pages in this thread... Sorry when the question is asked so often. :(

---

### Post by jedson3 on 2007-12-30
Hi --

I went through all the revised steps up to "./configure --prefix=..." etc for each of the four files. Each of the steps for each of the files looked like it was working. But when I type "sudo g1daemon" I get the message, "An Error Occured -2:(unabel to initialize keyboard) received." And I still can't get Kate to run, which is what got me started with this. 

jedson

---

### Post by dethredic on 2007-12-30
Ok, I got the clock working but it is ~58 secs behind my ubuntu clock.

Also, can I make the screen do anything more than a clock?

---

### Post by cdean on 2008-01-02
'Twould be great to see these 43 pages summed into a succinct HOWTO post. 

The packages are in hardy, so that's a win, but what will need to be configured after installing those packages?

I should also note that one can install libg15-1, libg15render1, libg15daemon, libg15daemon-client1, and g15composer on Gutsy from Hardy's repos without a problem. There's not just much function to it available in packages other than one for MPD and one for Audacious. Rhythmbox support would be nice, since it's the default audio player (at least in Gutsy), but I'm sure that's on someone's TODO list.

---

### Post by paratox on 2008-01-02
> **Aneurysm9 said:**
> Paratox:

libg15render didn't build with TTF support.  The configure check should have failed, can you paste the output of ./configure --enable-ttf?

i`ve installed the attached debs of the howto and now it works.

---

### Post by ThunderRd on 2008-01-20
Could someone take a look this output and tell me what is going wrong?

I have g15daemon-1.2.7 running fine, but now I see there is a 1.9.4 with more features; I tried to install it but this is the result...

I used the install script in this post:
[http://ubuntuforums.org/showpost.php?p=2461304&postcount=285](http://ubuntuforums.org/showpost.php?p=2461304&postcount=285)

Thanks.  File attached.

EDIT:  SOLVED
Mike helped me on the G15 forum; 

> 
Does adding the following three lines to the g15daemon-1.9.4/debian/g15daemon.install file help?
-----Add the following-----
usr/lib/g15daemon/*/plugins/*
usr/include/*
usr/share/doc/g15daemon*/*

---

### Post by syxbit on 2008-01-29
> **Reinhardt said:**
> I made a silly mistake and had a problem similar to yours.  Here is what I did wrong (in case you did it too) - I copied the instructions verbatim in my sudoers.tmp file.  Instead, you need to change the username to your actual username, ie, user ALL= NOPASSWD: /usr/sbin/g15daemon will become for user reinhardt:

 ```
reinhardt ALL=NOPASSWD: /usr/sbin/g15daemon
```

HAHAHA
i just did that myself :)
thanks

---

### Post by markop72 on 2008-02-28
Hello

I`m sorry if i ask something that was already discused but i have some trouble with my g15 when i play WoW. 
Everytime i log in the Game and start to walk or do something, my char starts to walk arround. 
It seems for me like a key hangs and dont stop to send commands. I have installed g15 Daemon & g15 Macro. 
I have this problem only with WoW.
Is there anybody in here who has an idea which solves my problem?

Thanks for any help

PS: sry for my bad english, i`m swiss

---

### Post by survient on 2008-03-04
Ok I have g15daemon, g15macro and xbindkeys all running. I checked my .xbindkeysrc file and have been using xbindkeys -k to detect the correct codes to use. My M1-3 keys will change and xbindkeys picks up on every Macro key I push. I was able to get xbindkeys to open apps when I used ctrl + alt + m, however it's not popping up apps or whatnot when I use the macro keys. I don't see why it shouldn't work at this point, unless gnome's native hotkey system is interfering, in which I don't know how to disable it. Any help on this would be appreciated. I have a G11 btw.

---

### Post by dccrens on 2008-04-10
OK, I have everything (G15 LCD G15 Stats, G15Macro, etc) working. Even the Amarok script is great. G15Stats displays. The M1, M2, M3 keys and the MR Key all seems to work and light up. My only issue now is how do you assign a macro to the G1-G18 keys. I can hit the MR button and then type a command in a terminal window and assign that to the G1-18 keys. But how do I assign starting an application to the key (without opening a term window)? Any help?

---

### Post by dccrens on 2008-04-15
Bump... Anyone reading this thread?

---

### Post by TheKeyMaker on 2008-04-18
Worked for me! Thanks!  Great post!

---

### Post by cdukes on 2008-04-21
Wow, what a huge pain in the *** this was...
I'm sharing my compiled .deb packages (but note they are for 64bit Gutsy)

Here's a quick summary of what I learned:

The instructions are mostly correct, except that reading 300 threads sucks.

* Someone mentioned that the hardy repos are available and work - it didn't work for me

* if you get errors about g15.so missing from /usr/lib/lcdproc then you need to recompile lcdproc like so:

(directory) lcdproc-0.5.2$
```

./configure --prefix=/usr --enable-drivers=all; make; sudo checkinstall make install

```

Be sure to edit your LCDd.conf and change the driver to g15 and make sure the path to the library reflects your inistall (either /usr/lib/lcdproc or /usr/local/lib/lcdproc)

---

### Post by MachineHead on 2008-04-21
Hi cdukes,

I'm running Hardy x64 at home and I did get the G15 progs from the repositories.
I just entered Synaptic and searched for G15.
And since I'm such an extreme expirienced Ubuntu user (not) I just installed them all :lolflag:

I do get a nice clock on my G15 LCD now, I can even switch between clock lay-outs.
But I really would like to have my media keys functional (Play, pause, next track, prev track, stop)

-MachineHead

---

### Post by Spartan.II.117 on 2008-04-21
could someone who understands python (preferably the dev), help me get the exaile plug in to display text? i have the msttcorefonts installed. if it uses those.

---

### Post by dccrens on 2008-04-21
Still looking for info on how to use G15Macro to launch GUI based programs. Havent found anything yet but I am looking on a couple of other boards too. If anyone knows please share. 

> **dccrens said:**
> OK, I have everything (G15 LCD G15 Stats, G15Macro, etc) working. Even the Amarok script is great. G15Stats displays. The M1, M2, M3 keys and the MR Key all seems to work and light up. My only issue now is how do you assign a macro to the G1-G18 keys. I can hit the MR button and then type a command in a terminal window and assign that to the G1-18 keys. But how do I assign starting an application to the key (without opening a term window)? Any help?

---

### Post by theacoustician on 2008-04-27
I was trying to use G15daemon in hopes it would work with my Logitech MX5000 (hey, they both had LCDs) and it didn't work out as I had hoped. I installed G15daemon and its dependencies using Synaptic on my Hardy 64bit system just fine, but when I attempted to remove them, I'm met with an error. Moving to the terminal, I can remove all the dependencies, but g15daemon refuses to give up. I even tried a "-f remove" and I'm still met with this error :
```

Code: Select all
    (Reading database ... 110163 files and directories currently installed.)
    Removing g15daemon ...
    Stopping g15daemon: /usr/sbin/g15daemon: error while loading shared libraries: libg15render.so.1: cannot open shared object file: No such file or directory
    invoke-rc.d: initscript g15daemon, action "stop" failed.
    dpkg: error processing g15daemon (--remove):
    subprocess pre-removal script returned error exit status 127
    Starting g15daemon: /usr/sbin/g15daemon: error while loading shared libraries: libg15render.so.1: cannot open shared object file: No such file or directory
    invoke-rc.d: initscript g15daemon, action "start" failed.
    dpkg: error while cleaning up:
    subprocess post-installation script returned error exit status 127
    Errors were encountered while processing:
    g15daemon
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```


This is terribly annoying as whenever I run Synaptic or apt-get, it throws out errors about g15daemon being broken. Help?

---

### Post by theacoustician on 2008-04-29
Bumping for my question above.  Does anyone care that there's an uninstallable file sitting in the official repositories?

---

### Post by MachineHead on 2008-04-30
Hey theacoustician,

I installed the same files as mentioned by you from the repositories.
While I'm running Hardy 8.04 aswell, I don't understand why it wouldn't work for you.
I cannot decipher the print-out you give from the console, but I can tell you that most things work with the G15 board and the usual files on the repositorie.
Might be they ain't to friendly with the MX5000?

-MachineHead

---

### Post by theacoustician on 2008-04-30
> **MachineHead said:**
> Hey theacoustician,

I installed the same files as mentioned by you from the repositories.
While I'm running Hardy 8.04 aswell, I don't understand why it wouldn't work for you.
I cannot decipher the print-out you give from the console, but I can tell you that most things work with the G15 board and the usual files on the repositorie.
Might be they ain't to friendly with the MX5000?

-MachineHead

Are you running a 32 bit system of a 64 bit?

I was a little bummed that it didn't work on the MX5000 since I heard that it would allow the hotkeys to work, but no worries.  The troublesome part now is I can neither remove nor reinstall g15daemon to get it off my system.  That simply makes no sense.  Worse still is I can't upgrade or do anything because all package managers seem hung up on the fact I have a broken package in my set.  I'm about at the point of reinstalling from scratch, but that just seems ridiculous.

---

### Post by MachineHead on 2008-05-01
> **theacoustician said:**
> Are you running a 32 bit system of a 64 bit?

I was a little bummed that it didn't work on the MX5000 since I heard that it would allow the hotkeys to work, but no worries.  The troublesome part now is I can neither remove nor reinstall g15daemon to get it off my system.  That simply makes no sense.  Worse still is I can't upgrade or do anything because all package managers seem hung up on the fact I have a broken package in my set.  I'm about at the point of reinstalling from scratch, but that just seems ridiculous.

Hey there,

I'm running x64 edition of Ubuntu Hardy 8.04.
Further more I'm an absolute console noob leeching on other people's console greatness :lolflag:
So I can't give you any advice on how to remove that motherfragger from your system :P
Just reinstall, it won't lose you any data would it?

-MachineHead

---

### Post by ProbablyX on 2008-05-18
Hello, I have Hardy-repo-packages too, w/o G-keys working.

As I was trying to find out why the G-keys aren't recognized, while play/stop are, and LCD, I detected this:

> 
g15daemon -v
G15Daemon version 1.9pre - Not Running
compiled with libg15 version 1.201


Shouldn't the daemon be running by default?!

UP: Sorry, it was because I didnt sudo :)

---

### Post by dccrens on 2008-05-19
Anyone every get G15Macro fully working? I seem to have it working and can record keystrokes at a terminal. Next question is how do you record launching an application from a GUI/Icon? Is this possible? Or, does it only work for keystrokes at a term?

---

### Post by maxxwizard on 2008-05-26
> **cdean said:**
> 'Twould be great to see these 43 pages summed into a succinct HOWTO post. 

The packages are in hardy, so that's a win, but what will need to be configured after installing those packages?

I should also note that one can install libg15-1, libg15render1, libg15daemon, libg15daemon-client1, and g15composer on Gutsy from Hardy's repos without a problem. There's not just much function to it available in packages other than one for MPD and one for Audacious. Rhythmbox support would be nice, since it's the default audio player (at least in Gutsy), but I'm sure that's on someone's TODO list.

i would definitely love rhymthbox support. i just switched to linux and i have no clue how to program a script for the g15daemon, haha.

---

### Post by pyrr on 2008-06-23
> **theacoustician said:**
> I was trying to use G15daemon in hopes it would work with my Logitech MX5000 (hey, they both had LCDs) and it didn't work out as I had hoped. I installed G15daemon and its dependencies using Synaptic on my Hardy 64bit system just fine, but when I attempted to remove them, I'm met with an error. Moving to the terminal, I can remove all the dependencies, but g15daemon refuses to give up. I even tried a "-f remove" and I'm still met with this error :

(snip)

This is terribly annoying as whenever I run Synaptic or apt-get, it throws out errors about g15daemon being broken. Help?

This annoyed me for the past month or two as well (Kubuntu Hardy, 64-bit). I saw your post here after trying to force dpkg (with the same result), obviously this thread has been no help to you or anyone else regarding this issue.

I decided just to go all loose-cannon on this crappy daemon. I went through the places where applications live, can't remember specifically which directories I found g15daemon in, but I deleted all instances of it I could find in the /usr/* and /etc directories, and then deleted all softlinks in the /etc/rc.*  directories. After that, dpkg ran happily and made it go away, no more errors.

NB: Running Konqueror (or whatever the Gnome equivalent of it might be) as root in a file manager capacity makes it easy to search and destroy. Exercise caution though!

---

### Post by unimatrix on 2008-06-26
I have a weirder problem. When I try to login in KDM/Kubuntu 8.04 x86_64 with my G15 keyboard, whatever button I press (except the G buttons which obviously don't work) the screen **disappears** for a moment and no letter is written. Please don't tell me I'm the only one with a weird problem again...

I tried removing the g15daemon and libg15-1 packages and everything that goes with it, but still no luck.

EDIT: I just figured out this has nothing to do with logitech G15... happens with all keyboards. I think it was the latest xorg update or something.

---

### Post by Rabix on 2008-06-30
Hi, 

I would like to associate a function to the G-key. something like G1=shutdown/startup
Does anybody have any ideas ?

I skim through the topic but couldn't find anything.

Thanks,

---

### Post by soulsedition on 2008-07-01
I've got the same problem, can't remove g15daemon. i found a post somewhere where you add 2 words to the g15daemon file and then you can uninstall it. I can't find it now, ARGH! any help out there?

---

### Post by Zodiac64 on 2008-08-05
I would love if anyone could make a script to show playing-info from Rhythmbox on the Logitech G15 with G15Daemon.

Thanks in advance!

---

### Post by hoozey on 2008-08-21
> **markop72 said:**
> Hello

I`m sorry if i ask something that was already discused but i have some trouble with my g15 when i play WoW. 
Everytime i log in the Game and start to walk or do something, my char starts to walk arround. 
It seems for me like a key hangs and dont stop to send commands. I have installed g15 Daemon & g15 Macro. 
I have this problem only with WoW.
Is there anybody in here who has an idea which solves my problem?

Thanks for any help

PS: sry for my bad english, i`m swiss

I also had this problem. It seems that for some reason the numlock key is always being triggered (I think by xbindkeys). By default in WoW, numlock is the autorun key, so everytime a G-key is used your character starts or stops running. I'm not sure how to stop the numlock triggering (ideas, anyone?), so I just changed autorun to a different key.

---

### Post by rb1205 on 2008-10-06
I just bought this keyboard, and find it awesome. I was looking for a plugin in rhythmbox that writes the song's details on the keyboard's LCD.  I [found]("http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg05157.html") a plugin wrote by Ender, which however was very crude. I edited it a little to make it more exhaustive and user-friendly.

Now should be ok for a every day usage. It displays details of the song being played (title, artist, album, genre), plus a time bar and some more eye candies here and there. No spectrum bars or anything like that at the moment, sorry, and no configuration window.

If you want to try it, unpack the archive in your /bin/lib/rhythmbox/plugins directory (make sure that, avter the unpacking, you have a new directory called /bin/lib/rhythmbox/LogitechG15).  To use it, just enable the plugin from the plugin configuration window in rhythmbox. That's all. 

If this doesn't work for you, i'd be glad if you can run rhythmbox from your console and send me any error message you get. 

BTW, to use this you'll need g15daemon up and running AND g15composer (both available as packages in the standard hardy repository).

---

### Post by MadEgg on 2008-10-18
Just crossposting with the G15 forum but I'm not sure where the problem lies.

Anyway, I have been able to get this keyboard functioning normal, except for a small problem with the XF86AudioStop and the Super_L/left meta/windows key.

Both keys work properly if I don't use g15macro. But the XF86AudioStop keycode changes to XF86AudioLowerVolume when g15macro is loaded. And the keycode the Super_L key sends changes according to which set of macro's is loaded, it is XF86Messenger on M1, F29 on M2 and scaron(&#353;) on M3.

Apparently the super_l key gets treated as G17, while my G15 keyboard only has G1 to G6 (it is a G15 v2). So I tried setting G17 to Super_L in the g15macro.conf but the program just completely ignores this and uses the defaults instead.

If I enter 'g15macro -d' to dump the configuration to stdout, the configuration file even gets overwritten with the default values.

Anyone knows a way to fix this?

---

### Post by MadEgg on 2008-10-22
Anyone knows how to make this work on a G15 v2?

---

### Post by MadEgg on 2008-10-23
Right, I wrote a patch for g15-macro-1.0.3 to support V2 keyboards as well. The main difference is the addition of a command line flag --second (-2) that reduces the number of remapped keys from 18 to 6, and also fixes the keycodes for the multimedia keys which seem to be different on the v2 keyboard(but I'm not completely sure, that could be just my configuration, someone should try it out).

Hope this is of help to someone, i'll also submit the patch on the project page as well.

---

### Post by jaem on 2008-11-01
@MadEgg: Thanks!  I just got my G15 v2 today (replacing one of those Old-School Beige Compaq Keyboards Of Fail), and was wondering why the macro keys weren't working.  So far, your patch works flawlessly.

---

### Post by RatSAT on 2008-11-04
> **MadEgg said:**
> Right, I wrote a patch for g15-macro-1.0.3 to support V2 keyboards as well. The main difference is the addition of a command line flag --second (-2) that reduces the number of remapped keys from 18 to 6, and also fixes the keycodes for the multimedia keys which seem to be different on the v2 keyboard(but I'm not completely sure, that could be just my configuration, someone should try it out).

Hope this is of help to someone, i'll also submit the patch on the project page as well.

I have an original Logitech G15  with G1 - G18, but also have the problem with the left windows button. It doesn't seem to do anything anymore, but when inspecting the g15macro debugging info it seems to behave as G17. Will this patch work for me as well?

---

### Post by MadEgg on 2008-11-05
> **RatSAT said:**
> I have an original Logitech G15  with G1 - G18, but also have the problem with the left windows button. It doesn't seem to do anything anymore, but when inspecting the g15macro debugging info it seems to behave as G17. Will this patch work for me as well?

Have you set up your keyboard as 'G15 keyboard using G15daemon' in your keyboard settings? It seems like a wrong keymap has been loaded or something.

Anyway, while this patch may help fix the problem of the left meta key, it will disable your G7 to G18 keys so this might not be what you want.

---

### Post by RatSAT on 2008-11-08
> **MadEgg said:**
> Have you set up your keyboard as 'G15 keyboard using G15daemon' in your keyboard settings? It seems like a wrong keymap has been loaded or something.
Yes I have, and it seems to be working fine, clock and multimedia keys work. After starting g15macro the left meta key stops working, even if I kill g15macro and then restart g15daemon.

Also, how can I run g15macro in the background? Making a script and starting it with update-rc doesn't work, adding it to rc.local doesn't work. Running it manually in a terminal works, but as soon as I close the terminal g15macro gets killed. I'd like to autostart it when I boot my computer so it's always available.

---

### Post by MadEgg on 2008-11-10
> **RatSAT said:**
> Yes I have, and it seems to be working fine, clock and multimedia keys work. After starting g15macro the left meta key stops working, even if I kill g15macro and then restart g15daemon.

Also, how can I run g15macro in the background? Making a script and starting it with update-rc doesn't work, adding it to rc.local doesn't work. Running it manually in a terminal works, but as soon as I close the terminal g15macro gets killed. I'd like to autostart it when I boot my computer so it's always available.

What I have done is, to make different profiles for different users possible, running g15macro as user and not as root. 

To achieve this I have created a script:

```

#!/usr/bin/bash

/usr/bin/g15macro --second &

```

and placed that in ~/.kde/Autostart/ (made executable of course). I use the --second here because I've got the v2 keyboard, you won't be needing that one (unless it gets your meta key functioning properly and you are fine with sacrificing 12 G-keys)

This also shows how you can run g15macro in the background, simply by adding an ampersand to the end of the command line.

If you're running gnome, you can go to System->Preferences->Sessions and add the script you created to the list with the button on the side.

---

### Post by Grubbles on 2008-11-11
MadEgg, how do I install that patch you created?  I'm also wondering how I create macros, once I have everything working.  Thanks.

---

### Post by MadEgg on 2008-11-12
Basic instructions to get this to work:

```

mkdir ~/tmp
cd ~/tmp
wget http://downloads.sourceforge.net/g15daemon/g15macro-1.0.3.tar.bz2
wget http://ubuntuforums.org/attachment.php?attachmentid=89419
tar xjvf g15macro-1.0.3.tar.bz2
bunzip2 g15macro-g15v2.patch.bz2
cd g15-macro-1.0.3/
patch -p1 < ../g15macro-g15v2.patch
./configure
make
make install

```

This might not even work if you don't have the proper build tools installed, you need at least the build-essential package, and it depends on libg15daemon-client-dev and probably others to build.


Anyway, to make this all easier, I tried building an Ubuntu package with the patched binary in it. This is the first deb package I have ever build so I'm not sure if it will work for you, but you're free to try. I've attached the package to this post, so you can download that and install it by double clicking on it.

Please let me know whether it works or not if you try it!

---

### Post by MadEgg on 2008-11-12
Creating macros is covered on the g15tools.com website as well, but it's really simple. First you chose the macro-set you which to record to by pressing either M1, M2 or M3 on your keyboard. Then press the MR key to start recording, which should then start to glow. Press all the keys (slowly) which you would like to bind to a G-key. After you pressed all the keys, press the G-key you would like to bind it to. The display will tell you that it has actually saved the macro.

Strange thing I have encountered is that sometimes the recorded macros are remembered between different runs of g15macro, and sometimes they are lost between different runs. I'm not sure what causes this, but it seems the developers @ g15tools.com are not doing too much to this package so maybe I'll dive deeper into the program and see what I can do.

---

### Post by Grubbles on 2008-11-12
Thanks, MadEgg, your instructions worked flawlessly.  Sorry, I couldn't test the package you created--I'm running 64bit.

I have two more questions, though.  Is there a way I can stop the lcd from toggling?--and can I use my G keys to open programs without having Konsole open?

Thanks again.

---

### Post by mikeize on 2009-01-09
Hi there.  I just installed everything 'g15 related' from synaptic, and found that it all pretty much works fine.  That is, I can toggle between time/date modes or system info on the LCD.  Also, for Rhythmbox, the media keys all work, except the 'stop' key lowers the volume (instead of stopping).  Also, is there anyway to make the media keys work with other programs (esp Amarok and VLC)?

As far as making macros... it works fine I think, but with one problem: I want to macro "Alt_LF2geditReturn" for example, to run gedit... but it doesn't work.  Even trying just "Alt_LF2" to bring up the run program box results in nothing.  Is there a way to make this work?  Thanks.

---

### Post by keteflips on 2009-01-12
I have the same problem with the Super_L key

¿Someone have a solution?

Thanks all dudes :)

---

### Post by mikeize on 2009-01-19
*bump*

Still haven't figured out how to run programs with these keys...  I've tried messing with xmodmap, and xev...  the keys seem to have values associated with them--I can even assign them to shortcuts with xbindkeys-config... but they don't work!  Surely someone has figured this out, no?  Still hoping...

-mike

---

### Post by newbie- on 2009-02-17
i have g15 and i have clock and xchat highlighter on it,
where i can find config file what to edit to change lcd text,
about uptime and everything???

i cant find that file..
hope someone can help me.

sorry my bad english..

i use crunchbang but thats probalty same as ubuntu.

---

### Post by Lummoxx on 2009-02-18
I've been stumped by the fact that g15macro was supposed to be running in order for the G keys to work.  In all the reading I did, nowhere did I find anything that said that...or not that I saw.

Now, how do you get it to save the settings after you've programmed the G keys?  The first time I did it, after a reboot, it didn't save, and I had to assign the G keys again.

Thanks.

---

### Post by keteflips on 2009-02-19
> **MadEgg said:**
> Basic instructions to get this to work:

```

mkdir ~/tmp
cd ~/tmp
wget http://downloads.sourceforge.net/g15daemon/g15macro-1.0.3.tar.bz2
wget http://ubuntuforums.org/attachment.php?attachmentid=89419
tar xjvf g15macro-1.0.3.tar.bz2
bunzip2 g15macro-g15v2.patch.bz2
cd g15-macro-1.0.3/
patch -p1 < ../g15macro-g15v2.patch
./configure
make
make install

```

This might not even work if you don't have the proper build tools installed, you need at least the build-essential package, and it depends on libg15daemon-client-dev and probably others to build.


Anyway, to make this all easier, I tried building an Ubuntu package with the patched binary in it. This is the first deb package I have ever build so I'm not sure if it will work for you, but you're free to try. I've attached the package to this post, so you can download that and install it by double clicking on it.

Please let me know whether it works or not if you try it!

OMG

You are my good.

THANKS!!!!  :D:D:D:D:D:D:D

---

### Post by Predatorian on 2009-05-30
how do i remove this package/daemon, because now im getting errors with apt-get

i keept getting this error:

```
E: /var/cache/apt/archives/libg15-1_1.2.6-1_amd64.deb: trying to overwrite `/usr/lib/libg15.so.1.0.0', which is also in package libg15
```

---

### Post by cdean on 2009-06-01
> **Predatorian said:**
> how do i remove this package/daemon, because now im getting errors with apt-get

i keept getting this error:

```
E: /var/cache/apt/archives/libg15-1_1.2.6-1_amd64.deb: trying to overwrite `/usr/lib/libg15.so.1.0.0', which is also in package libg15
```

Try
```
sudo apt-get remove libg15
```
or
```
sudo dpkg -r libg15
```

---

### Post by Predatorian on 2009-06-01
thank you. i thought i did the first one, but the dpkg helped. thank you again.

---

### Post by weedlewonk on 2010-03-27
How to save macros with G15 macro:
Ubuntu 9.10

run this in a terminal:
```
sudo g15macro
```

then, without leaving the terminal, enter your macros:

Press the MR button
type your macro
press the G key

Once you've entered all your macros, press Ctrl-c.  Your macros are now saved.  Relaunch g15macro (Alt-F2 g15macro) and you're good to go!

To check and see if your macros have been saved, go to:

/home/<USER>/.g15macro

and open the file :

g15macro.conf

It should display something like:

[HTML]Codes for MKey 1
Key G1:
	a Down 16
	a Up 16
	l Down 16
	l Up 16
	l Down 16
	l Up 16
	e Down 16
	e Up 16
	n Down 16
	n Up 16
	1 Down 16
	1 Up 16[/HTML]

(this would type "allen1")

Enjoy saved macros everyone!:D

---

### Post by ktamm on 2010-04-10
I am just wondering if ANYONE figure out how to get the g-keys to launch an application? I can get the macros to work fine, however I am having no luck getting the g-keys to launch programs :(

---

### Post by pyrforos on 2010-04-14
i have the same problem...
Is it possible to get the g-keys to launch an application?

---

### Post by weedlewonk on 2010-04-14
I haven't been able to figure that out, however, it is possible to have single or multiple key strokes launch programs in Ubuntu without g15macro.  I'm using 9.10 (soon to be 10.04), but I'm thinking it should be the same for most other versions.  The way to do it is to use the built in Keyboard Shortcuts manager.

1. Open the Keyboard Shortcuts GUI from the System/Preferences Menu

2. Click Add (this will add a custom shortcut to the bottom of the list)

3. Give it a name and enter the command.

for the commands, it will take the same action as though you entered the name of the program into the Run Application GUI (Alt + F2) or in a terminal.  For example.

I use this command to run Google Chrome:
```
google-chrome
```

or, I use this command to open my Downloads folder:
```
nautilus /home/USER/Downloads
```

or, I use this to open a terminal:
```
terminal
```

If you're not sure what command to use, but it shows up in the Applications Menu, you can find the command by going to the Main Menu GUI (under System/Preferences), selecting the program you want to create a shortcut for, and clicking on Properties (or just double-click on the Name or Icon).

Now that you've given your shortcut a name and told it the command, click Apply.

4. New shortcuts will be disabled by default.  To activate it, find your new shortcut (usually at the very bottom of the list) and click on the word "Disabled"

5. Now, enter your keystrokes.  For single button action, I recommend the / * - or + keys on the keypad as personally I rarely use them.  Optionally you can do key combinations.  For example, I have Alt + F3 as a shortcut to open a terminal and Alt + D will open my downloads folder.

I hope this guide helps.

Sad things to note:

Setting a G key macro to a custom shortcut will not launch a program.  (Such as creating a macro for a G key of Alt + A and a keyboard shortcut of Alt + A)

The Keyboard Shortcuts program will not recognize the G keys, so you can't use them as shortcuts in and of themselves.

Happy Shortcutting :biggrin:

---

### Post by Ariskos on 2010-05-07
Hello people!
Could you please update the How-To guide for the ubuntu 10.04 and include the new releases of g15composer,render,lib. etc .. ?
Thanks a lot !!

---

### Post by Recon20k on 2010-06-05
i get the following error message when trying to install:

sudo apt-get install libusb-dev libdaemon-dev


Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-dev is already the newest version.
libdaemon-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up g15daemon (1.9.5.3-8ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas?

---

### Post by Recon20k on 2010-06-05
> **drdnl said:**
> For anyone who cares, attached are the latest amd64 debs with ttf support. If it doesnt work right away you probably need to follow some steps from the starting post.

For anyone wanting to compile them themselves, turns out you need libfreetype6 (maybe -dev, can't remember) installed for ttf support.

Found a possible bug though, if I run the audacious *or* xmms plugin (with visualization) the entire thing hangs, it doesnt crash, it hangs and only an old fashioned ctrl+c in the terminal helps. Anyone?

-D

i tried to install this and get he following message:

> 
/tmp/g15composer_3.1-1_amd64.deb could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.


then i try:

 chown bmosullivan tmp

> 
chown: changing ownership of `tmp': Operation not permitted


---

### Post by Sutur on 2010-10-21
> **Recon20k said:**
> i get the following error message when trying to install:

sudo apt-get install libusb-dev libdaemon-dev


Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-dev is already the newest version.
libdaemon-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up g15daemon (1.9.5.3-8ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas?

I'm having this issue as well can someone please chime in?

---

### Post by WitchMaster on 2011-10-04
Hello everyone!

I installed the g15daemon on my ubuntu yesterday but after ~15 minutes the computer freezes/crashes and i have to manually restart it.

I previously installed it on Linux Mint and i had the same problem and that's why i installed ubuntu (i believed it was a linux mint issue).

Is there any solution to my problem? I dont feel comfortable at all using ubuntu without the lcd screen of my Logitech G510 and the backlight colour.

Thanks.

---

