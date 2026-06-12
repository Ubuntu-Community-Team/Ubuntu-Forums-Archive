---
title: "[Howto] Compile &amp; Install Osmo Organizer"
date: 2007-11-17
forum: Tutorials
---

### Post by Onyros on 2007-11-17
[Osmo]("http://clay.ll.pl/osmo/") is a great little organizer (or as they put it "A Handy Personal Organizer"), with a nifty tabbed display which integrates a Calendar with Tasks, Contacts and Notes in a single app.

Here's a (post-configured) screenshot - default config looks godawful, with HUGE fonts and horrible colours.

[IMG]http://img62.imageshack.us/img62/5062/screeniebd7.png[/IMG]

Now, Osmo still isn't pre-compiled or distributed in binary format, so if you want to try it out, you'll have to get your hands dirty. Not too much, it's pretty easy.

1.
First things first, so... we have to go and get the source --> [here]("https://sourceforge.net/project/showfiles.php?group_id=206587") (that's Osmo's sourceforge)

When I wrote this [Howto] latest version was v0.1.6. (updated - 20071224)

2.
Let's open up a terminal, and extract the source with the following command (make sure you *cd* to the folder to where you downloaded the .tar.gz file)

```
tar xvf osmo-0.1.6.tar.gz
```

And then *cd* into the created folder with Osmo's source code.

3.
It's time to satisfy the app's dependencies. From reading Osmo's homepage, we know it depends on libxml2 and libgtk2.0 ( version >= 2.10 ). Ubuntu's Gutsy repos satisfy those dependencies, but chances are you won't have the -dev packages installed for compiling. Just to make sure we use the terminal to

```
sudo aptitude install libxml2 libxml2-dev libgtk2.0-dev libgettext-ruby1.8
```

That should bring a few extra packages attached, if you didn't have them installed previously. If you can afford an extra 15MB of downloads and around 50MB of HDD space, go ahead and do it. You can always remove both those -dev packages and the extra stuff after compiling Osmo.

N.B.: libgettext-ruby1.8 has been reported by a few people to be a, probably, unexpected dependency. It's happened a few times due to an internationalization dependency regarding package "msgfmt" which is included in libgettext-ruby1.8. So if compilation throws out a "msgfmt" error, be sure to include mentioned package ;)

N.B.2: Version 0.1.6 released the 24th December added iCalendar file support. Both libical and libical-dev are not present in Gutsy's repos, though they are in Hardy's and haven't been backported (at least not to my knowledge). Those two packages are needed to have iCalendar's support enabled, so only Hardy users will be able to take advantage of that specific new feature.

4.
When you have all dependencies lined up, it's a pretty straightforward process.

```
./configure
```

it shouldn't throw around any errors, if all went well until now. And then, to finish it off...

```
make && sudo make install
```

or *alternatively* you can use checkinstall instead (which will add the app to Synaptic, making it easier to manage/remove later on)

```
make && sudo checkinstall -D
```

(Checkinstall will also upgrade the old installed version, should you decide to compile a newer one)

That way it'll also create a .deb file for you to keep and install on other machines you may have.

*Et voilá!*

Launch Osmo at the terminal to test it out (just type "osmo" and it'll launch immediately, and create the appropriate launcher for your specific DE. Enjoy your new private virtual secretary. :)

I'm using it specifically with Claws-Mail and it's only too bad they don't share/synchronize the address book, looks like something I'll be requesting (as well as the ability to copy notes from one day to another). Take a look at the date calculator, it's pretty... *handy*, as well!

---

### Post by wildkarde on 2007-11-20
Thanks for this howto.  Unfortunately it did not work for me.

I had to also install libgettext-ruby1.8 and (just cause) libgettext-ruby-util.

It needed msgfmt.

Awesome program.  Just wish it could be minimized to tray.    EDIT::  In due time it will.

---

### Post by Scruffynerf on 2007-11-21
Excellent. Have just installed following the howto and all is good.

This is just about the lightest and one of the easiest calendar/organizer apps I've seen!

---

### Post by Onyros on 2007-11-21
> **wildkarde said:**
> Thanks for this howto.  Unfortunately it did not work for me.

I had to also install libgettext-ruby1.8 and (just cause) libgettext-ruby-util.

It needed msgfmt.

Awesome program.  Just wish it could be minimized to tray.    EDIT::  In due time it will.That's odd! During the compilation it doesn't ask for any of those, and they're not listed anywhere as dependencies, I really can't replicate that problem here. Were you installing anything else at the same time, had installed something which dependencies weren't met?

I know Ubuntu's version of Kazehakase (as an example) has those as dependencies, but it doesn't make sense for Osmo. (In my view it doesn't for Kazehakase, they should be recommended, but that's a whole different story).

Anyone else who had that problem?

---

### Post by wildkarde on 2007-11-21
During the ./configuration, it doesn't ask for it.  But when it was time to do the make install it kept failing because of a program 'msgfmt' not being present.  Later on today, i'll remove the package and try to duplicate the process.

---

### Post by Onyros on 2007-11-21
> **wildkarde said:**
> During the ./configuration, it doesn't ask for it.  But when it was time to do the make install it kept failing because of a program 'msgfmt' not being present.  Later on today, i'll remove the package and try to duplicate the process.Thanks, mate ;)

msgfmt is indeed part of the gettext packages, so it may have something to do with localization? Are you using something different from UTF-8 in your system? Something a little more "exotic", perhaps?

Lemme know how it went, so I can post any corrections the Howto may need!

---

### Post by wildkarde on 2007-12-01
Sorry for the late late reply.

I removed the package, the osmo directory and the packages ' libgettext-ruby1.8 libgettext-ruby-util'.

Following your advice, I checked on my language settings and it complained that there were some packages missing.  It did its thing and afterwards I tried to compile osmo again.  

It worked and did not ask for the package as it had done before.

---

### Post by KaroSHiv0n on 2007-12-01
Thanks for this i got it working although i did have to add the extra packages too, nice proggie!

---

### Post by Onyros on 2007-12-04
Ah, glad you guys got it working! If you can pinpoint the necessary additional packages, let me know so I can add them to the how-to :)

BTW, new version out (I missed version 0.1.3! edit: never mind, it skipped from 0.1.2 to 0.1.4), it's at v0.1.4 and it's looking cooler and with a few more goodies (tray icon!, birthday browser, current time display, etc)

---

### Post by KaroSHiv0n on 2007-12-04
I added all the packages mentioned above and tried compiling after each but it wouldent work for me until msgfmt. was installed so maybe thats the one needed?

---

### Post by wildkarde on 2007-12-05
To avoid confusion as it's happening to more people, perhaps you should add that package to the how-to.  It doesn't hurt and will guarantee that the package compiles successfully.

---

### Post by Skorzen on 2007-12-06
Excellent HowTo and good tool.

---

### Post by Onyros on 2007-12-06
> **wildkarde said:**
> To avoid confusion as it's happening to more people, perhaps you should add that package to the how-to.  It doesn't hurt and will guarantee that the package compiles successfully.Done! Actual dependency is "libgettext-ruby1.8", because "msgfmt" is distributed with it, and not on its own (at least in Gutsy's repos).

---

### Post by Onyros on 2007-12-06
> **Skorzen said:**
> Excellent HowTo and good tool.Thanks, mate (for the first part); be sure to send a note to the software's author, he'll surely appreciate it :)

---

### Post by wildkarde on 2007-12-10
There's a new version out.

---

### Post by Onyros on 2007-12-10
> **wildkarde said:**
> There's a new version out.Yep, Howto was updated 6 days ago to update the version, and 3 days ago to include libgettext-ruby1.8 as a dependency ;)

---

### Post by wildkarde on 2007-12-10
Oh.  Opps, didn't notice. :)

---

### Post by Onyros on 2007-12-23
[Osmo]("http://clay.ll.pl/osmo/") version 0.1.6 released :D (Howto updated)

---

### Post by ubifrost on 2008-01-15
When I did ./configure, I got error message:-
'configure: error: cannot find sources (src/contacts.c) in . or ..'

any ideas?

---

### Post by Onyros on 2008-01-15
Looks like you're missing a few things in your source folder. Are you sure your download of the source code was complete, or are you sure you untar'ed the source code completely?

Take a look at Osmo's source code folder, inside /src and let me know what's inside :)

---

### Post by BuffaloX on 2008-01-22
This is the coolest calendar I have tried in Linux yet.
Very clever set of features, simple yet extremely useful.

Two things are bugging me a bit,
I only have one color to choose from in the "select day color" menu.
And only one group - "none" - when i add contacts.

Anyone had better luck?

---

### Post by Onyros on 2008-01-22
Hey there, BuffaloX :)

I'm not sure what you mean with "select day color" menu, is it this?

[[IMG]http://img297.imageshack.us/img297/8619/markeddayxi2.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=markeddayxi2.jpg)

When I press that option, a dialog opens in which I can choose whichever colour I want for a marked day.

Regarding the second one, you have to add Contact Groups first in Osmo's options:

[[IMG]http://img297.imageshack.us/img297/8369/addcontactjf6.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=addcontactjf6.jpg)

If you have already inserted a few contacts there, all you have to do is edit them and assign them to a group.

BTW, I've been playing around with a simple Osmo port to ITOS2008 on the Nokia N800 (just playing around with, not creating the port per se), it'll be a great addition to its apps roster, I'll try posting a few pics later tonight :)

---

### Post by BuffaloX on 2008-01-22
Thanks Onyros 

That was exactly what I meant, :)
Now both colors and groups work.
I don't know how I missed that there are separate options for calendar tasks contacts and general. :confused:

Hmm I only got a couple of hours sleep last night, I think I'll blame that. :p

Thanks again for very nice quick and useful reply. :popcorn:

---

### Post by Onyros on 2008-01-23
I'm glad I could help! :)

And heree's Osmo running in my N800! Still a few things not fully working, like the tray icon implementation, but overall it's a great app to have on an internet tablet.

---

### Post by BuffaloX on 2008-01-23
Cool that you can make it work on your N800.
Hurray for open source. :guitar:
(And programmers that can figure it out.)
If I buy some similar gadget, I'll be sure to pick one that runs Linux.

I hit on another small issue, I hope it's just me overseeing the obvious.
If I start Osmo manually it starts minimized and with tray as I want it to.
But if  I add Osmo to sessions and reboot, Osmo starts maximized and without the tray icon:confused:

(edit)
I tried to start it through a bash script, with same results, also tried adding sleep 5 to no avail.
I´d really like to have it auto startup in tray...
Bash script works when called manually, but when included in sessions,Osmo has no icon and starts maximized.

---

### Post by Onyros on 2008-01-25
> **BuffaloX said:**
> Cool that you can make it work on your N800.
Hurray for open source. :guitar:
(And programmers that can figure it out.)
If I buy some similar gadget, I'll be sure to pick one that runs Linux.

I hit on another small issue, I hope it's just me overseeing the obvious.
If I start Osmo manually it starts minimized and with tray as I want it to.
But if  I add Osmo to sessions and reboot, Osmo starts maximized and without the tray icon:confused:

(edit)
I tried to start it through a bash script, with same results, also tried adding sleep 5 to no avail.
I´d really like to have it auto startup in tray...
Bash script works when called manually, but when included in sessions,Osmo has no icon and starts maximized.That's strange, indeed. Maybe you have to start Osmo with any cheat codes, instead? When you mention that you added it to your sessions, I suppose you're using GNOME, right?

I don't have GNOME installed right now, but I'll look into it and try helping you with that (if only I could find Osmo's man page... :P)

Starting it through .xinitrc (I'm using Awesome WM) works without any problems, so that's strange enough to warrant a bug report ;)

---

### Post by BuffaloX on 2008-01-25
Yes I use Gnome, 

I filed a bug report about same time I wrote about it here.
No reply yet.

However another bug about lack of a save option, in which I suggest that changes are saved immediately, have got response that save at user defined intervals will be included in next version.

So nice features are planned for next version too. :)

---

### Post by BuffaloX on 2008-01-27
Increasing the delay to 10 secs. did the trick.
I just never imagined such a long delay could be needed for Gnome to be ready.

---

### Post by sinim on 2008-08-06
I am getting hung up after ./configure it claims libnotify 0.4.4 cannot be found. I looked and it is installed, any ideas?

---

### Post by wiseguy on 2008-08-13
> **sinim said:**
> I am getting hung up after ./configure it claims libnotify 0.4.4 cannot be found. I looked and it is installed, any ideas?

Same here.

---

### Post by Beth1957 on 2008-09-06
Nice one; thanks!

---

### Post by buivietkhoa1919upg on 2008-09-21
> **sinim said:**
> I am getting hung up after ./configure it claims libnotify 0.4.4 cannot be found. I looked and it is installed, any ideas?

i had got same error with libnotify, 

after that i reinstalled it and installed the libnotify-dev, it worked for me

---

### Post by TheFrenchDetective on 2008-10-14
Hi.  I downloaded your 2.0 version and followed your instructions, but was unsuccessful.  When I ran the ./configure command I got a "configure error:  libnotify >= 0.4.4 couldn't be found".  When I ran the "make && sudo make install" command, I received "make: *** No targets specified and no makefile found.  Stop."  It's a shame, because the program looks like what I am looking for.  Any answers???

---

### Post by Jacob Collstrup on 2008-11-18
> **sinim said:**
> I am getting hung up after ./configure it claims libnotify 0.4.4 cannot be found. I looked and it is installed, any ideas?

I got that same error...is this thread getting updated anymore?

Jacob

---

### Post by Onyros on 2008-11-18
Hi there, guys. I'm sorry I won't be able to help you out with this, as I no longer have any computer with Ubuntu installed (since Hardy) and won't be able to reproduce the build environment - I'm strictly using Arch right now.

I think GetDeb is your best choice for Osmo, I remember them having a package there it will probably still work with Intrepid.

Take care :)

---

### Post by Eastisle on 2008-11-24
> **Jacob Collstrup said:**
> I got that same error...is this thread getting updated anymore?

Jacob

Hi, the libnotify issue can be solved by:

sudo apt-get install libnotify1 libnotify-dev



This got it working for me, or you can use synaptic as suggested a few posts ago.

---

### Post by Azhtabak on 2009-03-14
I think it's ok to dredge this up for questions?

I saw this tutorial yesterday and thought the program looked interesting, so I decided to have a go at it - however, I'm having a problem. When I use ```
make && sudo checkinstall -D
``` it starts making, then cuts out later on, giving me 'Error 1' and 'Error 2' and doesn't work. I've checked all the deps that I can see from the thread and I think I have them all?

Output:
```

azhtabak@azhtabak-laptop:~/osmo-0.2.6$ make && sudo checkinstall -D
make  all-recursive                                                
make[1]: Entering directory `/home/azhtabak/osmo-0.2.6'            
Making all in src                                                  
make[2]: Entering directory `/home/azhtabak/osmo-0.2.6/src'        
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar.o -MD -MP -MF .deps/calendar.Tpo -c -o calendar.o calendar.c                                                                               
mv -f .deps/calendar.Tpo .deps/calendar.Po                                      
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_calc.o -MD -MP -MF .deps/calendar_calc.Tpo -c -o calendar_calc.o calendar_calc.c                                                           
mv -f .deps/calendar_calc.Tpo .deps/calendar_calc.Po                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_fullyear.o -MD -MP -MF .deps/calendar_fullyear.Tpo -c -o calendar_fullyear.o calendar_fullyear.c                                           
mv -f .deps/calendar_fullyear.Tpo .deps/calendar_fullyear.Po                    
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_ical.o -MD -MP -MF .deps/calendar_ical.Tpo -c -o calendar_ical.o calendar_ical.c                                                           
mv -f .deps/calendar_ical.Tpo .deps/calendar_ical.Po                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_jumpto.o -MD -MP -MF .deps/calendar_jumpto.Tpo -c -o calendar_jumpto.o calendar_jumpto.c                                                   
mv -f .deps/calendar_jumpto.Tpo .deps/calendar_jumpto.Po                        
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_notes.o -MD -MP -MF .deps/calendar_notes.Tpo -c -o calendar_notes.o calendar_notes.c                                                       
mv -f .deps/calendar_notes.Tpo .deps/calendar_notes.Po                          
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_print.o -MD -MP -MF .deps/calendar_print.Tpo -c -o calendar_print.o calendar_print.c                                                       
mv -f .deps/calendar_print.Tpo .deps/calendar_print.Po                          
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_timeline.o -MD -MP -MF .deps/calendar_timeline.Tpo -c -o calendar_timeline.o calendar_timeline.c                                           
mv -f .deps/calendar_timeline.Tpo .deps/calendar_timeline.Po                    
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_utils.o -MD -MP -MF .deps/calendar_utils.Tpo -c -o calendar_utils.o calendar_utils.c                                                       
mv -f .deps/calendar_utils.Tpo .deps/calendar_utils.Po                          
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT calendar_widget.o -MD -MP -MF .deps/calendar_widget.Tpo -c -o calendar_widget.o calendar_widget.c                                                   
mv -f .deps/calendar_widget.Tpo .deps/calendar_widget.Po                        
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT check_events.o -MD -MP -MF .deps/check_events.Tpo -c -o check_events.o check_events.c                                                               
mv -f .deps/check_events.Tpo .deps/check_events.Po                              
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts.o -MD -MP -MF .deps/contacts.Tpo -c -o contacts.o contacts.c                                                                               
contacts.c: In function &#8216;contacts_map_location_cb&#8217;:                             
contacts.c:902: warning: format not a string literal and no format arguments    
mv -f .deps/contacts.Tpo .deps/contacts.Po                                      
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts_birthdays.o -MD -MP -MF .deps/contacts_birthdays.Tpo -c -o contacts_birthdays.o contacts_birthdays.c                                       
mv -f .deps/contacts_birthdays.Tpo .deps/contacts_birthdays.Po                  
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts_import.o -MD -MP -MF .deps/contacts_import.Tpo -c -o contacts_import.o contacts_import.c                                                   
mv -f .deps/contacts_import.Tpo .deps/contacts_import.Po                        
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts_import_csv.o -MD -MP -MF .deps/contacts_import_csv.Tpo -c -o contacts_import_csv.o contacts_import_csv.c                                   
mv -f .deps/contacts_import_csv.Tpo .deps/contacts_import_csv.Po                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts_export.o -MD -MP -MF .deps/contacts_export.Tpo -c -o contacts_export.o contacts_export.c                                                   
mv -f .deps/contacts_export.Tpo .deps/contacts_export.Po                        
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT contacts_items.o -MD -MP -MF .deps/contacts_items.Tpo -c -o contacts_items.o contacts_items.c                                                       
mv -f .deps/contacts_items.Tpo .deps/contacts_items.Po                          
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT gui.o -MD -MP -MF .deps/gui.Tpo -c -o gui.o gui.c                   
mv -f .deps/gui.Tpo .deps/gui.Po                                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c               
main.c: In function &#8216;main&#8217;:                                                     
main.c:207: warning: format not a string literal and no format arguments        
mv -f .deps/main.Tpo .deps/main.Po                                              
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT notes.o -MD -MP -MF .deps/notes.Tpo -c -o notes.o notes.c           
mv -f .deps/notes.Tpo .deps/notes.Po                                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT notes_items.o -MD -MP -MF .deps/notes_items.Tpo -c -o notes_items.o notes_items.c                                                                   
mv -f .deps/notes_items.Tpo .deps/notes_items.Po                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui.o -MD -MP -MF .deps/options_gui.Tpo -c -o options_gui.o options_gui.c                                                                   
mv -f .deps/options_gui.Tpo .deps/options_gui.Po                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui_calendar.o -MD -MP -MF .deps/options_gui_calendar.Tpo -c -o options_gui_calendar.o options_gui_calendar.c                               
mv -f .deps/options_gui_calendar.Tpo .deps/options_gui_calendar.Po              
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui_contacts.o -MD -MP -MF .deps/options_gui_contacts.Tpo -c -o options_gui_contacts.o options_gui_contacts.c                               
mv -f .deps/options_gui_contacts.Tpo .deps/options_gui_contacts.Po              
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui_general.o -MD -MP -MF .deps/options_gui_general.Tpo -c -o options_gui_general.o options_gui_general.c                                   
mv -f .deps/options_gui_general.Tpo .deps/options_gui_general.Po                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui_notes.o -MD -MP -MF .deps/options_gui_notes.Tpo -c -o options_gui_notes.o options_gui_notes.c                                           
mv -f .deps/options_gui_notes.Tpo .deps/options_gui_notes.Po                    
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_gui_tasks.o -MD -MP -MF .deps/options_gui_tasks.Tpo -c -o options_gui_tasks.o options_gui_tasks.c                                           
mv -f .deps/options_gui_tasks.Tpo .deps/options_gui_tasks.Po                    
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT options_prefs.o -MD -MP -MF .deps/options_prefs.Tpo -c -o options_prefs.o options_prefs.c                                                           
mv -f .deps/options_prefs.Tpo .deps/options_prefs.Po                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT stock_icons.o -MD -MP -MF .deps/stock_icons.Tpo -c -o stock_icons.o stock_icons.c                                                                   
mv -f .deps/stock_icons.Tpo .deps/stock_icons.Po                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT tasks.o -MD -MP -MF .deps/tasks.Tpo -c -o tasks.o tasks.c           
mv -f .deps/tasks.Tpo .deps/tasks.Po                                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT tasks_items.o -MD -MP -MF .deps/tasks_items.Tpo -c -o tasks_items.o tasks_items.c                                                                   
mv -f .deps/tasks_items.Tpo .deps/tasks_items.Po                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT tasks_print.o -MD -MP -MF .deps/tasks_print.Tpo -c -o tasks_print.o tasks_print.c                                                                   
mv -f .deps/tasks_print.Tpo .deps/tasks_print.Po                                
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT utils.o -MD -MP -MF .deps/utils.Tpo -c -o utils.o utils.c           
mv -f .deps/utils.Tpo .deps/utils.Po                                            
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT utils_gui.o -MD -MP -MF .deps/utils_gui.Tpo -c -o utils_gui.o utils_gui.c                                                                           
utils_gui.c: In function &#8216;utl_gui_create_dialog&#8217;:                               
utils_gui.c:356: warning: format not a string literal and no format arguments   
utils_gui.c:371: warning: format not a string literal and no format arguments   
utils_gui.c:385: warning: format not a string literal and no format arguments   
utils_gui.c:399: warning: format not a string literal and no format arguments   
mv -f .deps/utils_gui.Tpo .deps/utils_gui.Po                                    
gcc -DHAVE_CONFIG_H -I. -I..  -DLOCALEDIR=\"/usr/local/share/locale\"  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2 -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED   -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12       -MT utils_time.o -MD -MP -MF .deps/utils_time.Tpo -c -o utils_time.o utils_time.c                                                                       
mv -f .deps/utils_time.Tpo .deps/utils_time.Po                                  
gcc  -g -O2  -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12         -o osmo calendar.o calendar_calc.o calendar_fullyear.o calendar_ical.o calendar_jumpto.o calendar_notes.o calendar_print.o calendar_timeline.o calendar_utils.o calendar_widget.o check_events.o contacts.o contacts_birthdays.o contacts_import.o contacts_import_csv.o contacts_export.o contacts_items.o gui.o main.o notes.o notes_items.o options_gui.o options_gui_calendar.o options_gui_contacts.o options_gui_general.o options_gui_notes.o options_gui_tasks.o options_prefs.o stock_icons.o tasks.o tasks_items.o tasks_print.o utils.o utils_gui.o utils_time.o   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   -lxml2  -L//lib -lnotify -lgtk-x11-2.0 -ldbus-glib-1 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgmodule-2.0 -ldbus-1 -lgobject-2.0 -lglib-2.0
notes_items.o: In function `notes_enter_password':
/home/azhtabak/osmo-0.2.6/src/notes_items.c:1041: undefined reference to `gui_create_dialog'
collect2: ld returned 1 exit status
make[2]: *** [osmo] Error 1
make[2]: Leaving directory `/home/azhtabak/osmo-0.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/azhtabak/osmo-0.2.6'
make: *** [all] Error 2
azhtabak@azhtabak-laptop:~/osmo-0.2.6$

```

---

### Post by Helekryl on 2009-05-14
Open the file "notes_items.c" and change the function name "gui_create_dialog" (string #1041) to "utl_gui_create_dialog".^_^

---

### Post by Rahzizzle on 2009-07-15
Yeah, Helekryl is right, I figured it out on my own but that'll fix it.

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for nice howto.

---

### Post by mosaabJ on 2009-11-05
It all goes fine with me until I get to the final step where I don't know what happens wrong anyway this what happens after I enter this ```
make && sudo checkinstall -D

```
**[COLOR="DarkOrange"]The following happens[/COLOR]**
```
mosaab@mosaab-desktop:~$ make && sudo checkinstall -D
make: *** No targets specified and no makefile found. Stop.
mosaab@mosaab-desktop:~$ cd osmo-0.2.8
bash: cd: osmo-0.2.8: No such file or directory
mosaab@mosaab-desktop:~$ cd osmo-0.2.8
bash: cd: osmo-0.2.8: No such file or directory
mosaab@mosaab-desktop:~$ cd osmo-0.2.8
bash: cd: osmo-0.2.8: No such file or directory
mosaab@mosaab-desktop:~$ clear
mosaab@mosaab-desktop:~$ cd /home/mosaab/Desktop/osmo-0.2.8
mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ make && sudo checkinstall -D
make  all-recursive
make[1]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
Making all in src
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/src'
Making all in data
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in icons
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in pixmaps
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
Making all in sounds
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in po
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
make[1]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
[sudo] password for mosaab: 
sudo: checkinstall: command not found
mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ make && sudo check install -D
make  all-recursive
make[1]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
Making all in src
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/src'
Making all in data
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in icons
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in pixmaps
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
Making all in sounds
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in po
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
make[1]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
sudo: check: command not found
mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ make && sudo install -D
make  all-recursive
make[1]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
Making all in src
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/src'
Making all in data
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in icons
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in pixmaps
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
Making all in sounds
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in po
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
make[1]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
install: missing file operand
Try `install --help' for more information.
mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ make && sudo install -Dclear
make  all-recursive
make[1]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
Making all in src
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/src'
Making all in data
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in icons
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in pixmaps
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
Making all in sounds
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in po
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
make[1]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
install: invalid option -- 'l'
Try `install --help' for more information.
mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ clear

mosaab@mosaab-desktop:~/Desktop/osmo-0.2.8$ make && sudo checkinstall -D
make  all-recursive
make[1]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
Making all in src
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/src'
Making all in data
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in icons
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons/scalable'
make[4]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/icons'
Making all in pixmaps
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/pixmaps'
Making all in sounds
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data/sounds'
make[3]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/data'
Making all in po
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8/po'
make[2]: Entering directory `/home/mosaab/Desktop/osmo-0.2.8'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
make[1]: Leaving directory `/home/mosaab/Desktop/osmo-0.2.8'
sudo: checkinstall: command not found

```

---

### Post by Imaginary-r4e- on 2010-02-26
I get the following problem when trying:
```
anton@nti-laptop:~$ ./configure
bash: ./configure: No such file or directory

```
Does anyone know how to fix this?

---

### Post by doublewitt on 2010-03-24
You can also download the .deb package from links on their home page. A "deb" package is a simple "click & install"...

---

### Post by pierreu1 on 2010-12-05
I really like the way Osmo is set up! It is simple, but effective! HOWEVER, is there a way to force the calendar to AUTOMATICALLY open at log-in! I have a big desktop, so I would love it to be open to kind of see what is my weekly or monthly events quickly. It would be even better if the events were open as well or if there was an option to do so.

---

### Post by dingd0ng on 2012-03-28
Awesome - I've compiled my first piece of software! Thanks for this clear and simple tutorial.

---

