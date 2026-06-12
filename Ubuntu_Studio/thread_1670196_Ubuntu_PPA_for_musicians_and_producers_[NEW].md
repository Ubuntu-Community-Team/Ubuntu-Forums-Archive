---
title: "Ubuntu PPA for musicians and producers [NEW]"
date: 2011-01-18
forum: Ubuntu Studio
---

### Post by falkTX on 2011-01-18
Hi there community!

The KXStudio Team got bigger and now has a new set of PPAs, ready for usage!
These new PPAs support all Ubuntu versions since Lucid (ie. Lucid, Maverick, Natty, Oneiric and Precise).

EDIT: I've put the repositories information on my website:
[http://kxstudio.sourceforge.net/KXStudio:Repositories#Ubuntu](http://kxstudio.sourceforge.net/KXStudio:Repositories#Ubuntu)

SPECIAL NOTES:
 - The Music PPA is empty for now (it's big uploads and my network sucks)


Please report any issues, and enjoy! :D

---

### Post by JC Cheloven on 2011-01-18
Most useful thing for audio-inclined users.
Thanks a million again :)
JC

---

### Post by Scott L on 2011-01-18
Awesome initiative falktx, you are a great asset to the Ubuntu audio community!

---

### Post by falkTX on 2011-01-19
> **Scott L said:**
> Awesome initiative falktx, you are a great asset to the Ubuntu audio community!

Many thanks!

It means a lot coming from you... :D

---

### Post by falkTX on 2011-01-22
Hi there everyone,

I've been working with VST support recently, so I wanted to clarify a few things.

The PPA now has a 'vstsdk2.3' and 'vstsdk2.4' packages, but they are actually empty.
The reason for those packages to exist is to make it easier for anyone who wants to compile anything with VST support.
The packages have a readme that clarifies how to get a proper 'vstsdk2.4' deb with the header files included.

This is the way archlinux is doing it right now, and I believe it's a good idea.
We have those packages as 'placeholders' for the real debs any user can create.

You may ask "Why are you bothering with VST when other standards are open?"
Well, here are some of the reasons I do it:
- VST is probably the most widely used format in Audio Production (although not in Linux). Outside people are used to hear "VST" and it's good to know that Linux supports it too.
- VST is the currently only standard (working on Linux) that provides host<->plugin time sync.
- There are a lot of VSTs out there, they just need to be recompiled for Linux...
- JUCE only provides VST plugin support as of now (there's DSSI too, but it's not official/ready)

I'm also working on a VST plugin right now, to be able to use Linux apps/plugins within Wine applications (through Jack-MIDI).
More details on that later...

---

### Post by cutOff on 2011-01-22
> **falkTX said:**
> Hi there everyone,

I've been working with VST support recently, so I wanted to clarify a few things.

The PPA now has a 'vstsdk2.3' and 'vstsdk2.4' packages, but they are actually empty.
The reason for those packages to exist is to make it easier for anyone who wants to compile anything with VST support.
The packages have a readme that clarifies how to get a proper 'vstsdk2.4' deb with the header files included.

This is the way archlinux is doing it right now, and I believe it's a good idea.
We have those packages as 'placeholders' for the real debs any user can create.

You may ask "Why are you bothering with VST when other standards are open?"
Well, here are some of the reasons I do it:
- VST is probably the most widely used format in Audio Production (although not in Linux). Outside people are used to hear "VST" and it's good to know that Linux supports it too.
- VST is the currently only standard (working on Linux) that provides host<->plugin time sync.
- There are a lot of VSTs out there, they just need to be recompiled for Linux...
- JUCE only provides VST plugin support as of now (there's DSSI too, but it's not official/ready)

I'm also working on a VST plugin right now, to be able to use Linux apps/plugins within Wine applications (through Jack-MIDI).
More details on that later...

hi, just to say yo, thanks for your great work. Keep it up! cheers ;)

---

### Post by maghoxfr on 2011-01-23
thank you very much for all the hard work falkTX!

---

### Post by maghoxfr on 2011-01-26
falkTX: what nvidia drivers do you recommend for the 2.6.33-7-rt kernel? Because I seem not not be able o find the right ones for me. I have an account that I use for audio with no graphics effects whatsoever and it always run smooth. But for the general account, I want some eye-candy because other people use it also and everything is so slow that makes me crazy!
Thanks

---

### Post by falkTX on 2011-01-26
> **maghoxfr said:**
> falkTX: what nvidia drivers do you recommend for the 2.6.33-7-rt kernel? Because I seem not not be able o find the right ones for me. I have an account that I use for audio with no graphics effects whatsoever and it always run smooth. But for the general account, I want some eye-candy because other people use it also and everything is so slow that makes me crazy!
Thanks

I don't own a nvidia card, and the new PPAs dont have drivers on it, yet.
From what I know about nvidia, latest version is not always the best.

Give me some time so I can prepare the realtime kernels (31 and 33).
Tell I'll start working on the drivers.

Please be patient...

---

### Post by maghoxfr on 2011-01-26
> **falkTX said:**
> I don't own a nvidia card, and the new PPAs dont have drivers on it, yet.
From what I know about nvidia, latest version is not always the best.

Give me some time so I can prepare the realtime kernels (31 and 33).
Tell I'll start working on the drivers.

Please be patient...

Sure man, no rush! I'll keep trying on the meantime.
Thanks for the time!

---

### Post by falkTX on 2011-01-26
Updates

**1 - Mumble with Jack support! [Main PPA]**
This is actually my piece of work. I made a patch for it and send upstream.
Please report any issues.


**2 - Calf plugins, Git [Latest PPA]**
The awesome calf plugins, git release.
Install 'calf-plugins-git', it will replace the stable 'calf-plugins'


Enjoy!

---

### Post by mango42 on 2011-01-27
[QUOTE="falkTX"]I don't own a nvidia card, and the new PPAs dont have drivers on it, yet.
From what I know about nvidia, latest version is not always the best.[/QUOTE]

Then how come your KXStudio is the very first UbuntuStudio offering that not only recognizes my partly broken SLI setup, chooses the right card AND gives me full 1920x1200 resolution with the -rt kernel but also gets me on the net via wifi without a murmur and without all that nm-applet hoohaa? 

A most impressive USB flash drive set-up and installation, falkTX. Thank you so much for your sustained efforts! :KS

Finding Qtractor and Reaper demo already installed was a major bonus, even if the latter doesn't find/recognise wineasio just yet...

One issue common to all the Studio offerings is an inability to see whether the internal soundcard (nVidia CK804?) on this amd64 machine has an IRQ conflict - it does (xrun central!), but once I'm 'up to speed' on **rtprio** ops, I *should* be able to solve that one as well.

However, now it appears that you've teamed up with ffado.org & AutoStatic's super-helpful packaging, I have every confidence that firewire will work in KXStudio, ;-) 

Hey, I might even get to like KDE, once I've got over the 'windoze lookalike' aspects...

Once again, thanks very much for providing a clueless user with most of the fine tunings already built in to **[KXStudio]("http://kxstudio.sourceforge.net/")**

---

### Post by falkTX on 2011-01-27
> **mango42 said:**
> Then how come your KXStudio is the very first UbuntuStudio offering that not only recognizes my partly broken SLI setup, chooses the right card AND gives me full 1920x1200 resolution with the -rt kernel but also gets me on the net via wifi without a murmur and without all that nm-applet hoohaa? 

A most impressive USB flash drive set-up and installation, falkTX. Thank you so much for your sustained efforts! :KS

Finding Qtractor and Reaper demo already installed was a major bonus, even if the latter doesn't find/recognise wineasio just yet...

One issue common to all the Studio offerings is an inability to see whether the internal soundcard (nVidia CK804?) on this amd64 machine has an IRQ conflict - it does (xrun central!), but once I'm 'up to speed' on **rtprio** ops, I *should* be able to solve that one as well.

However, now it appears that you've teamed up with ffado.org & AutoStatic's super-helpful packaging, I have every confidence that firewire will work in KXStudio, ;-) 

Hey, I might even get to like KDE, once I've got over the 'windoze lookalike' aspects...

Once again, thanks very much for providing a clueless user with most of the fine tunings already built in to **[KXStudio]("http://kxstudio.sourceforge.net/")**

Hey there, thanks for the nice words.

The LiveDVD does not auto-register wineasio, so you need to run 'regsvr32 wineasio.dll' manually. You also need to run this if you change wineasio versions (between normal and beta)

It sucks for me, that I only have a crappy laptop, so I cant test out cool stuff like firewire devices... I just put the configuration that worked for me, and hoped it would work for others too.

btw, I also spoke to the TangoStudio guys. They'll help in too (packaging only)

And you don't have to use KDE if you dont want to, at least that's one of my next goals - to make PPAs suitable for everyone, everywhere; the user shouldn't had to stick to a specific distro or Desktop Environment...
Lot of work to do...

---

### Post by mango42 on 2011-01-28
[QUOTE="falkTX"]The LiveDVD does not auto-register wineasio, so you need to run 'regsvr32 wineasio.dll' manually.[/QUOTE]

Thanks for the tip - saves some head scratching ;-)

I'll be sure to keep a close watch on your website about how to change WM's :popcorn:

---

### Post by falkTX on 2011-01-29
I have some great news!

Based on Abogani's work, I was able to prepare a realtime kernel.
It's v2.6.31, and it's available in the kernel PPA for Lucid, Maverick and Natty!!

If you have the PPAs, just run:
```
sudo apt-get update
sudo apt-get install linux-image-2.6.31-12-realtime linux-headers-2.6.31-12-realtime
```

You can now get a realtime kernel in Maverick and Natty too!

To enable rtirq script, just run:
```
update-rc.d rtirq defaults 50 10
```
(this is activated in KXStudio by default)

The update will probably fail to compile some drivers for now, but I plan to address this issue very soon.


In other news, 'clementine-svn' and 'hydrogen-svn' packages have been ported to these new PPAs.

---

### Post by AutoStatic on 2011-01-30
Thanks, but I have had bad experiences with 2.6.31 real-time kernels from Abogani on my notebook and netbook. 2.6.33 real-time kernels work much better. I'd focus on that kernel version and drop 2.6.31 real-time. Just my 2¢ ;)

Best,

Jeremy

---

### Post by maghoxfr on 2011-01-30
> **AutoStatic said:**
> Thanks, but I have had bad experiences with 2.6.31 real-time kernels from Abogani on my notebook and netbook. 2.6.33 real-time kernels work much better. I'd focus on that kernel version and drop 2.6.31 real-time. Just my 2¢ ;)

Best,

Jeremy

I agree with Jeremy here, only based on my experience with those kernels I had better results with the 2.6.33 ones.

---

### Post by dentex on 2011-01-30
Hi FalkTX,
I'm an old UbuntuStudio user and a very old "Windows audio applications user" who quit some time ago. Now I hope to have again the time and opportunity to make some audio stuff. This is where I have to thank you for all the work you put in KXStudio, that I'm trying these days and that I find AMAZING. It could even make me to get used to KDE.
And here comes my question: 
is it possible adding your PPA to a standard Ubuntu (or Mint, in my case) to have all the goodies you put in KXStudio (VST in primis) available in a gnome environment?
Thanks a lot.

---

### Post by falkTX on 2011-01-31
> **AutoStatic said:**
> Thanks, but I have had bad experiences with 2.6.31 real-time kernels from Abogani on my notebook and netbook. 2.6.33 real-time kernels work much better. I'd focus on that kernel version and drop 2.6.31 real-time. Just my 2¢ ;)

Best,

Jeremy

Don't worry, I plan to upload v2.6.33-realtime soon (the uploads are big..., plus x3 for lucid,maverick and natty).
We should all thanks 'munny' for his SSH server that allows me to upload big things like kernels. ;)

---

### Post by falkTX on 2011-01-31
> **dentex said:**
> Hi FalkTX,
I'm an old UbuntuStudio user and a very old "Windows audio applications user" who quit some time ago. Now I hope to have again the time and opportunity to make some audio stuff. This is where I have to thank you for all the work you put in KXStudio, that I'm trying these days and that I find AMAZING. It could even make me to get used to KDE.
And here comes my question: 
is it possible adding your PPA to a standard Ubuntu (or Mint, in my case) to have all the goodies you put in KXStudio (VST in primis) available in a gnome environment?
Thanks a lot.

Hi,

The "old" repos are compatible with Ubuntu Lucid, but are mostly useful to KDE users...

These news ones should work in any setup, for anyone using Ubuntu or derivates, like Linux Mint.
Just use the version that matches your distro.

You'll notice that the new PPAs are still missing a lot of stuff from the "old" one; you just have to be patient on this...

---

### Post by dentex on 2011-01-31
> **falkTX said:**
> These news ones should work in any setup, for anyone using Ubuntu or derivates, like Linux Mint.
Just use the version that matches your distro
OK, thanks.
> 
You'll notice that the new PPAs are still missing a lot of stuff from the "old" one; you just have to be patient on this...No problem for this, I appreciate very much your hard work. I'll be checking this thread or the KXStudio site for any news.

EDIT: I sent you an email @gmail on this topic; please ignore it as it's redundant.

---

### Post by AutoStatic on 2011-01-31
Hopefully I manage to set up pbuilder environments for lucid, maverick and natty this week on a server here at work so that I can start packaging for the KX Studio PPA too. If there's a need for it I can create SSH accounts on that server so that other members of the PPA can use it too to test packages.

Best,

Jeremy

---

### Post by falkTX on 2011-02-01
> **AutoStatic said:**
> Hopefully I manage to set up pbuilder environments for lucid, maverick and natty this week on a server here at work so that I can start packaging for the KX Studio PPA too. If there's a need for it I can create SSH accounts on that server so that other members of the PPA can use it too to test packages.

Best,

Jeremy

that would be very nice!

I dont have network at home, so I usually have to hope packages will compile fine on the launchpad server (sometimes I forgot a build dependency...)

and I need to say... my laptop just broke, again... :(
Same reason as before, so I'm counting on a new one now (warranty ends in 2 months, if this keeps happening, I'll have to pay the repairs next time...)

---

### Post by AutoStatic on 2011-02-02
Ok, pbuilder environments are created, I've read the docs so I should be ready to go... :shock:

---

### Post by vervelover on 2011-02-02
@ FalkTX

Hi, sorry to bother you again with this, but it seems that in your new kxstudio repos for Lucid the dssi-vst package (festige and fst are not there yet) still has a mandatory wine 1.3 dependency..

---

### Post by tehk on 2011-02-04
where's ardour3 ?! Doesn't seem to be in the KxStudio PPAs. :confused::confused::confused:

---

### Post by el.shupacabras on 2011-02-08
Hi everyone! :D

Let me first thank you for the extraordinary work they do for the community ;)

I want to change a Maverick, but I have a problem with "Gladish" fails to start

from the console the error is

```
segmentation violation
```

The error is mine for missing any dependencies?

---

### Post by rusk911 on 2011-02-08
[]("http://ubuntuforums.org/member.php?u=1240095")> where's ardour3 ?! Doesn't seem to be in the KxStudio PPAs.

Why you need it packaged? ardour3 changes every day and session file format isn't frozen at the moment as I know. It means that session you created this week may not work next week. You should build Ardour3 by yourself for testing purposes only.

---

### Post by falkTX on 2011-02-09
> **vervelover said:**
> @ FalkTX

Hi, sorry to bother you again with this, but it seems that in your new kxstudio repos for Lucid the dssi-vst package (festige and fst are not there yet) still has a mandatory wine 1.3 dependency..

Please be patient, my laptop is broken...

I'll be using a netbook in the meantime, with a fresh 10.04 install (no KXStudio), to make sure the PPAs are working fine.

---

### Post by falkTX on 2011-02-09
> **tehk said:**
> where's ardour3 ?! Doesn't seem to be in the KxStudio PPAs. :confused::confused::confused:

It's not anymore, the KXStudio PPAs are being deprecated.
Packages in the old PPAs are being deleted in favor of the new PPAs.
[I](Have you read the news: ?
[http://kxstudio.sourceforge.net/index.php?option=com_content&view=section&layout=blog&id=2&Itemid=2](http://kxstudio.sourceforge.net/index.php?option=com_content&view=section&layout=blog&id=2&Itemid=2))[/I]

Please check the first post for more info.
Feel free to ask anything that you feel I missed...

Direct link to ardour3 packages:
[https://launchpad.net/~kxstudio-team/+archive/latest/+sourcepub/1403722/+listing-archive-extra](https://launchpad.net/~kxstudio-team/+archive/latest/+sourcepub/1403722/+listing-archive-extra)
REMEMBER: Unstable software!

---

### Post by falkTX on 2011-02-09
> **el.shupacabras said:**
> Hi everyone! :D

Let me first thank you for the extraordinary work they do for the community ;)

I want to change a Maverick, but I have a problem with "Gladish" fails to start

from the console the error is

```
segmentation violation
```

The error is mine for missing any dependencies?

hm... strange...

please open a terminal and run:
```
gdb gladish
# press 'r', and enter
# wait until it crashes
# press 'bt' and enter
```

than post the output of the last 'bt' thing.

---

### Post by falkTX on 2011-02-09
> **AutoStatic said:**
> Ok, pbuilder environments are created, I've read the docs so I should be ready to go... :shock:

Nice!

Can you try making a test upload?
I'm not sure if the upload permissions are ok, I just want to be sure...

thanks

---

### Post by AutoStatic on 2011-02-09
Will do tomorrow. For months I've been picking my nose at work and now it is getting slightly busier.

---

### Post by el.shupacabras on 2011-02-09
> **falkTX said:**
> hm... strange...

please open a terminal and run:
```
gdb gladish
# press 'r', and enter
# wait until it crashes
# press 'bt' and enter
```than post the output of the last 'bt' thing.

thanks for answer Falk

```
cristian@cristian-System-Product-Name:~$ gdb gladish
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
Para las instrucciones de informe de errores, vea:
<http://www.gnu.org/software/gdb/bugs/>...
Leyendo símbolos desde /usr/bin/gladish...(no se encontraron símbolos de depuración)hecho.
(gdb) r
Starting program: /usr/bin/gladish 
[Depuración de hilo usando libthread_db enabled]
Loading glade from /usr/share/ladish/gladish.ui
[Nuevo Thread 0xb5149b70 (LWP 1804)]
[Nuevo Thread 0xb4948b70 (LWP 1805)]
JACK appeared
JACK started
menu_set_jack_latency() detects change
JACK latency changed: 512 samples
Initial studio appear
refresh_internal() called
refresh_internal() called
canvas::clear()
canvas::client_appeared(1, "Hardware Capture")
graph_proxy_dict_entry_get: reply signature is '' but expected signature is 's'
graph_proxy_dict_entry_get: reply signature is '' but expected signature is 's'
module_location_changed(id =   1, x = 1446,0, y = 1129,0)
canvas::port_appeared(1, 1, "capture_1")
canvas::port_appeared(1, 2, "capture_2")
canvas::client_appeared(2, "Hardware Playback")
graph_proxy_dict_entry_get: reply signature is '' but expected signature is 's'
graph_proxy_dict_entry_get: reply signature is '' but expected signature is 's'
module_location_changed(id =   2, x = 1413,0, y = 1257,0)
canvas::port_appeared(2, 3, "playback_1")
canvas::port_appeared(2, 4, "playback_2")
canvas_cls::on_realize

Program received signal SIGSEGV, Segmentation fault.
0x0806591a in ?? ()
(gdb) bt
#0  0x0806591a in ?? ()
#1  0x0805c4b3 in ?? ()
#2  0x0805cbeb in ?? ()
#3  0x001c893c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#4  0x001b9412 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#5  0x001cf595 in ?? () from /usr/lib/libgobject-2.0.so.0
#6  0x001d09bc in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#7  0x001d0e62 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#8  0x00b4a945 in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
#9  0x00a283a0 in gtk_menu_shell_activate_item ()
   from /usr/lib/libgtk-x11-2.0.so.0
#10 0x016f45a0 in ?? () from /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
#11 0x00952325 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x00986824 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x016f45ed in ?? () from /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
#14 0x0094e1ad in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x00986824 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x016f4d32 in ?? () from /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
#17 0x016f4e03 in ?? () from /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
#18 0x00231fcc in ?? () from /lib/libglib-2.0.so.0
---Type <return> to continue, or q <return> to quit---

```

---

### Post by el.shupacabras on 2011-02-09
Falk thanks for the tip, I will not lose more time.

 I will try to solve in the forum of my language (Spanish)

 you are a great contribution to the community! ;)

---

### Post by Excds on 2011-02-09
falkTX: Thanks for the great work you're doing with all this. KXStudio is fantastic!

Now for the questions:
If I want to setup a clean machine with the new PPA:s instead of installing KXStudio (I'm more of a gnome user...), how do I make sure that jack is the default for everything? Yes, install pulse-jack, but is there some additional configuration?

Additional question: falkTX and Autostatic, I'd like to get involved with these projects and help out. My problem is that I haven't worked with QT development and such before, so I'd like to know a bit about the development setups you guys are using. More specifically what you're using for editing and debugging.

---

### Post by falkTX on 2011-02-10
> **Excds said:**
> falkTX: Thanks for the great work you're doing with all this. KXStudio is fantastic!

Now for the questions:
If I want to setup a clean machine with the new PPA:s instead of installing KXStudio (I'm more of a gnome user...), how do I make sure that jack is the default for everything? Yes, install pulse-jack, but is there some additional configuration?


Haha, I'm still looking on how-to do it myself...
But expect some meta-packages on the new kxstudio repo to handle this situation soon.

> **Excds said:**
> Additional question: falkTX and Autostatic, I'd like to get involved with these projects and help out. My problem is that I haven't worked with QT development and such before, so I'd like to know a bit about the development setups you guys are using. More specifically what you're using for editing and debugging.
To be honest here, I'm the only one developing KXStudio right now.
AutoStatic is here more to help with packaging.

You can help by looking at some project and help it's development.
What we need most right now, are patches for jack-session and LADISH lv1 support.
(for example, I made a patch for rosegarden LADISH lv1, and I maintain my own fst+ladish branch now) 

Currently all my coding is for "Cadence", a set of apps for jack and linux (although it can work on Windows and Mac too).
[http://repo.or.cz/w/cadence.git](http://repo.or.cz/w/cadence.git)
All you need to install it is (development packages of) python, python-qt4 and dbus.
I'll soon create a website for it and I hope to release a beta/alpha of this soon...

The 'Catia' and 'Claudia' tools should work fine by now.

Random screenshots of some Cadence utilities:
[http://img251.imageshack.us/img251/1184/scr001.jpg](http://img251.imageshack.us/img251/1184/scr001.jpg)
[http://img35.imageshack.us/img35/7760/scr002y.jpg](http://img35.imageshack.us/img35/7760/scr002y.jpg)
[http://img547.imageshack.us/img547/1218/scr003.jpg](http://img547.imageshack.us/img547/1218/scr003.jpg)

What do you think?

---

### Post by Excds on 2011-02-10
> **falkTX said:**
> You can help by looking at some project and help it's development. What we need most right now, are patches for jack-session and LADISH lv1 support. (for example, I made a patch for rosegarden LADISH lv1, and I maintain my own fst+ladish branch now)

How is jack-session supposed to work and what apps are implementing it now?

> **falkTX said:**
>  Currently all my coding is for "Cadence", a set of apps for jack and linux (although it can work on Windows and Mac too).
[http://repo.or.cz/w/cadence.git](http://repo.or.cz/w/cadence.git)
All you need to install it is (development packages of) python, python-qt4 and dbus.
I'll soon create a website for it and I hope to release a beta/alpha of this soon...

The 'Catia' and 'Claudia' tools should work fine by now.

Random screenshots of some Cadence utilities:
[http://img251.imageshack.us/img251/1184/scr001.jpg](http://img251.imageshack.us/img251/1184/scr001.jpg)
[http://img35.imageshack.us/img35/7760/scr002y.jpg](http://img35.imageshack.us/img35/7760/scr002y.jpg)
[http://img547.imageshack.us/img547/1218/scr003.jpg](http://img547.imageshack.us/img547/1218/scr003.jpg)

What do you think?

It looks nice. I'm a little curios though about Catia, since it seems to be a subset of Claudia. What is it for?

Also, the Klaudia application had all the application loading. Is that also going to be a part of Claudia?

---

### Post by AutoStatic on 2011-02-11
> **falkTX said:**
> Nice!

Can you try making a test upload?
I'm not sure if the upload permissions are ok, I just want to be sure...

thanksCheck, uploaded abGate and it got accepted and it built ok too for all three releases.

Best,

Jeremy

---

### Post by el.shupacabras on 2011-02-11
**Possible bug "Gladish"**

could not start the application on Ubuntu 10.10 (Netbook Edition)

But the problem disappeared on the 10.10 (Desktop Edition)
 
I'm not registered "launchpad"

because my English is very bad language

I appreciate if someone can inform

**Another issue**,

until the legal point is a soundfont?

I made a collection of various synthesizers (hardwares and virtuals)

and I would like to share them through a PPA,

Greetings! :)

---

### Post by falkTX on 2011-02-12
> **Excds said:**
> How is jack-session supposed to work and what apps are implementing it now?



It looks nice. I'm a little curios though about Catia, since it seems to be a subset of Claudia. What is it for?

Also, the Klaudia application had all the application loading. Is that also going to be a part of Claudia?

Catia is a JACK patchbay, with a2jmidid integration.
Recently I added support for port aliases, so you can rename jack ports now!
This is one of the tools that work on Windows.

And yes, all the stuff from the "old" Klaudia app is part of Claudia now. Just go to settings, database, and set it to kxstudio.
Restart Claudia and check out menu app->add new...

---

### Post by falkTX on 2011-02-12
> **AutoStatic said:**
> Check, uploaded abGate and it got accepted and it built ok too for all three releases.

Best,

Jeremy

Awesome!

For now, I'll try to get all available DSSI plugins uploaded,
then I'll work on linuxsampler (and dependencies), based on packages from TangoStudio.


and btw, hm... err... it's "KXStudio", not "KX Studio" ;)

---

### Post by falkTX on 2011-02-12
> **el.shupacabras said:**
> **Possible bug "Gladish"**

could not start the application on Ubuntu 10.10 (Netbook Edition)

But the problem disappeared on the 10.10 (Desktop Edition)
 
I'm not registered "launchpad"

because my English is very bad language

I appreciate if someone can inform

**Another issue**,

until the legal point is a soundfont?

I made a collection of various synthesizers (hardwares and virtuals)

and I would like to share them through a PPA,

Greetings! :)

hm... the bug seems to be about the ubuntu's appmenu, not ladish itself.
My guess is that the appmenu does not support disabled menus...

soundfonts can only go to launchpad if they are Creative Commons, with permission to modify.
My guess is that 99% of soundfonts does not meet this requirement :(

---

### Post by AutoStatic on 2011-02-12
> **falkTX said:**
> and btw, hm... err... it's "KXStudio", not "KX Studio" ;)Ok, thanks, I'll keep it in mind for future uploads.

---

### Post by rusk911 on 2011-02-12
i have some questions about claudia.

First, it not appears in gnome menu.

Then, shutting down gladish I leave laditray and studio working, but closing claudia main window destroys tray icon and studio...

Then, pulse-jack autostart not works (may be isn't implemented yet?).

Then every couple seconds I have this message in terminal where claudia runs:

Traceback (most recent call last):
  File "/usr/share/cadence/src/patchcanvas.py", line 932, in updateCurrentTime
    self.line.setColor(QColor(color, color, 255))
AttributeError: 'CanvasBezierLine' object has no attribute 'setColor'


Last question about klaudia. I installed ardour2 from new ppa, but it not listed in klaudia...

---

### Post by rusk911 on 2011-02-13
And another
I has BIG troubles last night with new kxstudio ppa-s in maverick. Actually I don't know what happens. Seems like audio enviroinment from kxstudio removed me some gnome parts because of dependencies... After installing all jack and pulse stuff and rebooting gnome won't allow me to login... I boot into recovery console, removed all new ppa-s and reinstall ubuntu-desktop meta package...

How I did it? Actually don't remember all... First I removed all old kxstudio lucid ppa-s, removed jack, ladish and all known audio stuff, clear apt cache, add new ppa-s with maverick distro in url, installed all known audio packages and their dependencies. After some work around claudia described in previous post I decided to reboot and gnome showed me only login screen. I can login in terminal, but not in gnome... All night I googled login issues but it doesn't help. Only reinstall ubuntu-desktop solved problem...

---

### Post by el.shupacabras on 2011-02-14
[QUOTE=falkTX]

soundfonts can only go to launchpad if they are Creative Commons, with permission to modify.
My guess is that 99% of soundfonts does not meet this requirement :([/QUOTE]

Hi Falk, I guess format "gig " should be the same as the "sf2" as to leave

Is not there a native format for linux?

8 years I've been doing this compilation :(

---

### Post by AutoStatic on 2011-02-14
It's not about the format, it's about the content. Unless you recorded all the content yourself and released it under a CC license you're allowed to upload it to Launchpad.

Best,

Jeremy

---

### Post by falkTX on 2011-02-14
> **rusk911 said:**
> And another
I has BIG troubles last night with new kxstudio ppa-s in maverick. Actually I don't know what happens. Seems like audio enviroinment from kxstudio removed me some gnome parts because of dependencies... After installing all jack and pulse stuff and rebooting gnome won't allow me to login... I boot into recovery console, removed all new ppa-s and reinstall ubuntu-desktop meta package...

How I did it? Actually don't remember all... First I removed all old kxstudio lucid ppa-s, removed jack, ladish and all known audio stuff, clear apt cache, add new ppa-s with maverick distro in url, installed all known audio packages and their dependencies. After some work around claudia described in previous post I decided to reboot and gnome showed me only login screen. I can login in terminal, but not in gnome... All night I googled login issues but it doesn't help. Only reinstall ubuntu-desktop solved problem...

Please note that the Cadence apps and tools are being developed, so it's just normal that things don't work.
The 'cadence' deb in the kxstudio ppa is old, the best way to test these tools is to get the last git snapshot yourself:
```
git clone git://repo.or.cz/cadence.git
```
It still has a long way to go before an alpha/beta is released...

---

### Post by Excds on 2011-02-16
> **falkTX said:**
> Catia is a JACK patchbay, with a2jmidid integration.
Recently I added support for port aliases, so you can rename jack ports now!

a2jmidid and port aliases? Nice++

Hmm, do these port aliases then show up properly in ladish sessions (ok, I haven't gotten all the terminology of this fully sorted in my head yet...) so I can connect them there, or?

> **falkTX said:**
>  And yes, all the stuff from the "old" Klaudia app is part of Claudia now. Just go to settings, database, and set it to kxstudio.
Restart Claudia and check out menu app->add new...

Ah, I'll have to check that out then. :-)

---

### Post by falkTX on 2011-02-16
> **Excds said:**
> a2jmidid and port aliases? Nice++

Hmm, do these port aliases then show up properly in ladish sessions (ok, I haven't gotten all the terminology of this fully sorted in my head yet...) so I can connect them there, or?
Port aliases are just alternate names to jack ports.
The real port name is not changed. Jack support 2 aliases per port.
Right click on a port and select "info" to check them.

Sadly ladish does not support this. It also doesnt support "real" port flags and latency info (also used in the port information dialog).

---

### Post by el.shupacabras on 2011-02-17
Hello! sorry to bother,,

 I have a shame to be so ignorant

 I have moved to 10.10 and applications, both as a Ardour, Muse and Qtractor  not detect the effects of package

 "zynadd"

 lack any application package to recognize the effects lv2?

or has to do with location paths?

 Greetings community!

---

### Post by Pablo_F on 2011-02-17
Hi, 

sudo updatedb
locate zynadd | grep lv2

---

### Post by el.shupacabras on 2011-02-17
> **Pablo_F said:**
> Hi, 

sudo updatedb
locate zynadd | grep lv2

Tanks Pablo F

---

### Post by satanselbow on 2011-02-18
Ah man - this thread / project is real music to my ears :P

As a long time computer musician (on the eternally broken windows) who has been equally frustrated and disappointed with previous ubuntu musician related support / apps it great to see the massive advances being made :KS

I can realistically see Windows biting the dust on my workhorse machine now that  - I take my hat, jacket and pants off in salute to you all :guitar:

---

### Post by emoguitarist06 on 2011-02-19
I am 100% new to audio production but I want know would everyone here suggest I install
KXStudio
as opposed to
Ubuntu Studio?

I have no preference for gnome or kde so that doesn't matter

ALSO PLEASE SEED PEOPLE :) :)

---

### Post by falkTX on 2011-02-21
> **emoguitarist06 said:**
> I am 100% new to audio production but I want know would everyone here suggest I install
KXStudio
as opposed to
Ubuntu Studio?

I have no preference for gnome or kde so that doesn't matter

ALSO PLEASE SEED PEOPLE :) :)

You should know that:

Ubuntu + PPAs + KDE + minor tweaks = KXStudio

so, any option is ok.

KXStudio is only available for Lucid though...

---

### Post by maghoxfr on 2011-02-21
[Quote="falkTX"]You should know that:

Ubuntu + PPAs + KDE + minor tweaks = KXStudio

so, any option is ok.

KXStudio is only available for Lucid though...[/Quote]

Hi falkTX, how could I get an insight of what those minor tweaks are? I'd really appreciate some info there.

Thanks

---

### Post by emoguitarist06 on 2011-02-22
> **falkTX said:**
> You should know that:

Ubuntu + PPAs + KDE + minor tweaks = KXStudio

so, any option is ok.

KXStudio is only available for Lucid though...

Installing KXStudio right now!
It's beautiful by the way :)

---

### Post by aaronLund on 2011-02-23
I've used 8.04 for the past 2 years and was never able to get anything going recording-wise.  

Made my first (non gtk record my desktop) recording in KXStudio last night using VLC into Audacity.  

But boy do I hate kde so far......holy shite!

Either way, nice work FalkTX.

---

### Post by emoguitarist06 on 2011-02-23
> **aaronLund said:**
> But boy do I hate kde so far......holy shite!

Either way, nice work FalkTX.

I feel you there! I'm trying to convert my self from Ubuntu 10.10 but KDE feels so awkard and the keyboard shortcuts I'm used to don't work and no offense FalkTX but the desktop theme makes is it extremely hard to read text in boxes in firefox... I'm trying though... I'm taking it slow tonight

---

### Post by sgx on 2011-02-23
Kde4 is surely dreadful, but the kde 3.5.10 is much better, and so much easier to configure, and with more relevant options, instead of baffling eyecandy.

Fortunately, the Trinity project has advanced kde 3.5, now at 3.5.12, and
it's a pleasure to use.

E17 is also fine for window manager, fast and full of useful options, and nice themes if one so desires. The KX Studio looks to be a winner, the future looks bright! Once Jack 2 and RT kernels get settled, its going to
be a great audio environment. :)

---

### Post by aaronLund on 2011-02-24
Firefox won't respect my cursor choice either.....driving me nuts.

I'm ecstatic that Jack, VLC, Audacity, etc. all work but, again, I've never seen such crappy UIs before.  Absolutely unbelievable.

By the way, even though Audacity works it's "Dark Theme" (that must be KDE-speak for "pure garbage") makes it 100% unreadable.  (Yes, 100%...there's no way anybody could see the text.)

I'm curious how something like this makes it through any test pass whatsoever??

I apologize for the negativity but I miss the Gnome!

---

### Post by sgx on 2011-02-24
> **aaronLund said:**
> Firefox won't respect my cursor choice either.....driving me nuts.

I'm ecstatic that Jack, VLC, Audacity, etc. all work but, again, I've never seen such crappy UIs before.  Absolutely unbelievable.

By the way, even though Audacity works it's "Dark Theme" (that must be KDE-speak for "pure garbage") makes it 100% unreadable.  (Yes, 100%...there's no way anybody could see the text.)

I'm curious how something like this makes it through any test pass whatsoever??

I apologize for the negativity but I miss the Gnome!
You should be able to install what you like, and choose the environment to start from the login manager. The Gnome packages should be in almost any debian repository. 

There is usually a kde option for non kde apps to use kde colors/theme.
This can be turned off, so audacity will be the normal light grays, and blue soundwaves.

---

### Post by falkTX on 2011-02-25
Hey guys, I hear you...

I want to support Gnome for future versions of KXStudio, just give me some time.
(Probably for 11.04, which should be ready around 11/05)

I want to release a final Lucid version for now (10.04.4) with all the new updates, then I'll start working on the new stuff (new website, new apps, etc)


I also got the Firefox color issues...
It seems that, although the user can choose any color-scheme, some apps don't work work fine with it...
This is one of the reasons I'm considering the next theme to be bright.
Also probably replacing Firefox with Chrome ;)


Once I have something ready/decided, I'll let you guys know

---

### Post by maghoxfr on 2011-02-25
Why not chromium?

---

### Post by aaronLund on 2011-02-25
Is there any reason that updates are not happening for me anymore?

I'm getting a constant "waiting for service to start" under 'Getting updates - KpackageKit' and a constant "waiting for other tasks" under 'Getting distribution upgrade information' and a "waiting for authentication" under 'refreshing package cache'.  This is all under Kpackagekistmarticon.

I did a restart and that didn't seem to help.

---

### Post by aaronLund on 2011-02-25
.....more to the story.

Just got this error too:

Error Type: 
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')

---

### Post by falkTX on 2011-02-26
> **aaronLund said:**
> .....more to the story.

Just got this error too:

Error Type: 
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')

I noticed the PPAs been offline sometimes, but I'm not sure why this happens...
If launchpad has any problems with the software on it, I would already been contacted, which is not the case.

I'll ask the Ubuntu devs about this

---

### Post by emoguitarist06 on 2011-02-26
> **falkTX said:**
> I noticed the PPAs been offline sometimes, but I'm not sure why this happens...
If launchpad has any problems with the software on it, I would already been contacted, which is not the case.

I'll ask the Ubuntu devs about this

Is this also related to my problem? I always get this error when I run "sudo apt-get update"
```
W: Failed to fetch http://ppa.launchpad.net/kxstudio-team/music/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kxstudio-team/music/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by aaronLund on 2011-02-27
emo.

have you tried:

sudo apt-get update
sudo apt-get dist-upgrade

and when there is a problem:
sudo apt-get install -f 

this is straight from an irc chat with guitarman.  

hope it's ok to share from there.

---

### Post by emoguitarist06 on 2011-02-27
> **aaronLund said:**
> emo.

have you tried:

sudo apt-get update
sudo apt-get dist-upgrade

and when there is a problem:
sudo apt-get install -f 

this is straight from an irc chat with guitarman.  

hope it's ok to share from there.

Nope it didn't work
I ran update and I still got the 404 error
upgrade only upgraded python for me
and install -f didn't give any results

---

### Post by falkTX on 2011-02-27
> **emoguitarist06 said:**
> Is this also related to my problem? I always get this error when I run "sudo apt-get update"
```
W: Failed to fetch http://ppa.launchpad.net/kxstudio-team/music/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kxstudio-team/music/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

That is my error, I was hoping to upload some music samples very soon, but it never happened.
Basically this error means the PPA is empty (the 'music' one).

I'll upload a dummy package there just to fix this, then some day soon I'll upload real stuff

---

### Post by emoguitarist06 on 2011-02-27
> **falkTX said:**
> That is my error, I was hoping to upload some music samples very soon, but it never happened.
Basically this error means the PPA is empty (the 'music' one).

I'll upload a dummy package there just to fix this, then some day soon I'll upload real stuff

Awesome & Thanks, no more errors :)

P.S.
I look forward to the gnome version of KXStudio
(no rush though, I'm sure it's hard work)

---

### Post by aaronLund on 2011-02-28
Emo,

Keep on keepin on in regards to kde.

I hate to admit it but it's really starting to grow on me.

And I'm a gnome guy (was a gnome guy??) through and through.

---

### Post by el.shupacabras on 2011-02-28
[COLOR=#000000][FONT=Times New Roman][FONT=arial]Hello, undoubtedly the work of Falk's awesome.

KXStudio not wasted.

But my team really shows differences between Gnome and KDE

KX I have installed on a partition, but I have to deal withUbuntuStudio, with the PPA's Falk

Semprom 2.7, 1GB Ram[/FONT][/FONT][/COLOR]

---

### Post by bobhamil on 2011-03-03
[falkTX]("http://ubuntuforums.org/member.php?u=423496"), 
I have been using my Presonus Firestudio on Ubuntu for two years, and KXStudio has been by far the easiest release to setup and use.   In particular because it has Ardour, Reaper, and especially Jack2 already, so I simply compile FFADO.   Other distros, only had Jack1, which then required uninstalling all DAW/audio in order to install Jack2 and re-install DAW's.  
GREAT JOB!
I'll post the instructions to get non FFADO supported interfaces set up once I solve the "dual monitor setup get's lost on reboot problem".  (I think I need a xorg.conf, but each of the programs that's supposed to meake one for me has failed).   This may related to getting an error message that an xserver isn't running, when I run LinReaper or try compiling 64bit Wine?.  
[falkTX]("http://ubuntuforums.org/member.php?u=423496"), I'm not expecting you to look for answers for me on these things, I'm just reporting how it's working.  Anyone with any suggestions please jump right in.  

So far the performance is the same as I got with Reaper in 32-bit WXP.  (I may have a confict on the Firewire IRQ)(maybe need RTIRQ?).  My quad-core never gets close to capacity, but I get x-runs if I exceed 18 tracks with an acceptable latency for live mixing, which I do frequently, so I always use a console for monitors and FOH backup.  

I have been able to add and run a Nugen EQ in VST.  GREAT!!

Reaper only sees 16 of my 26 input channels Jacks sees all 26, and I can patch in Jack the missing inputs into existing ones, but I can't get all 26 at once in REAPER.  

Again, thank you for this well setup distro!!  

I'll post Presonus and Non-FFADO supported DICE interface setup instructions soon, or message me.  

Bob Hamil

---

### Post by falkTX on 2011-03-04
> **bobhamil said:**
> [falkTX]("http://ubuntuforums.org/member.php?u=423496"), 
I have been using my Presonus Firestudio on Ubuntu for two years, and KXStudio has been by far the easiest release to setup and use.   In particular because it has Ardour, Reaper, and especially Jack2 already, so I simply compile FFADO.   Other distros, only had Jack1, which then required uninstalling all DAW/audio in order to install Jack2 and re-install DAW's.  
GREAT JOB!
I'll post the instructions to get non FFADO supported interfaces set up once I solve the "dual monitor setup get's lost on reboot problem".  (I think I need a xorg.conf, but each of the programs that's supposed to meake one for me has failed).   This may related to getting an error message that an xserver isn't running, when I run LinReaper or try compiling 64bit Wine?.  
[falkTX]("http://ubuntuforums.org/member.php?u=423496"), I'm not expecting you to look for answers for me on these things, I'm just reporting how it's working.  Anyone with any suggestions please jump right in.  

So far the performance is the same as I got with Reaper in 32-bit WXP.  (I may have a confict on the Firewire IRQ)(maybe need RTIRQ?).  My quad-core never gets close to capacity, but I get x-runs if I exceed 18 tracks with an acceptable latency for live mixing, which I do frequently, so I always use a console for monitors and FOH backup.  

I have been able to add and run a Nugen EQ in VST.  GREAT!!

Reaper only sees 16 of my 26 input channels Jacks sees all 26, and I can patch in Jack the missing inputs into existing ones, but I can't get all 26 at once in REAPER.  

Again, thank you for this well setup distro!!  

I'll post Presonus and Non-FFADO supported DICE interface setup instructions soon, or message me.  

Bob Hamil

I also have been experienced issue when using 2 monitors (laptop and external VGA). but that monitor broke, so I couldn't do any more testing with it...
I remember some years ago, using the NVIDIA tool for this, and it worked fine. You don't really need an NVIDIA card to make that app work... :)

As for the REAPER/Wine port issue, I'm working on it.
It needs an updated WineASIO, and some tweaks (I'll post here the instructions when ready).

---

### Post by falkTX on 2011-03-18
Hey guys, I got some fresh news!

1 - **realtime-33 kernel has been added to the kernel PPA**
For lucid, maverick and natty. Natty 64bit build failed, to be fixed soon.
This means I can now start working the the driver+patches (at least for NVIDIA and ATI), be patient...

2 - **Some basic VST plugins are now available, and Qtractor was compiled with proper VST support**
The new plugins include 'mda-vst' pack, 'tal-plugins-vst' pack and 'wolpertinger-vst' packages. These packages may conflict a little with the old PPA, but I'm aware of it and fixing it right now.
The TAL plugins are pretty damn good, take a look at the official page - [http://kunz.corrupt.ch/](http://kunz.corrupt.ch/)

3 - **New PPA was added, named 'broken'**
This will contain broken, unstable, un-tested, or never released stuff (like code coming from svn/git, but never made as a tarball release).
For now it contains some (working) JUCED plugins - [http://code.google.com/p/juced/](http://code.google.com/p/juced/) - including JOST (both standalones and VSTs).

Some other packages were added too, including:
- jacker (with ladish lv1 support)
- so-synth-lv2 [by AutoStatic]
- zynaddsubfx-dssi
- wineasio (0.9.0)

The 'latest' PPA was also updated (Ardour3.0-prealpha, Blender2.5, etc).

And finally, I've updated my own tools too (Jack2-Simple-Config and Klaudia).

Enjoy!

---

### Post by falkTX on 2011-03-18
@bobhamil:
For WineASIO, the new update brought a nice way to configure it.
Update, run an ASIO app at least once, then open the registry ('regedit').
In Current-User\Software\Wine\WineASIO you will find keys you can tweak to change how WineASIO behaves.

See '/usr/share/doc/wineasio/README.gz' for more information about it.

---

### Post by binger on 2011-03-21
You say that Maverick and Natty are now supported.  I am curious if this is still an issue:
[http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

---

### Post by falkTX on 2011-03-21
> **binger said:**
> You say that Maverick and Natty are now supported.  I am curious if this is still an issue:
[http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Someone else has to do the testing, I'm still on Lucid...

But, afaik, Maverick suffers from this.
Natty, with lowlatency kernel from abogani, doesn't (but you'll strictly need that kernel)

If I can get the latest lowlatency to work in Maverick, then it should "fix" it.

---

### Post by ailo.at on 2011-03-21
> **binger said:**
> You say that Maverick and Natty are now supported.  I am curious if this is still an issue:
[http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Actually, I don't think the issue was ever present on Maverick. It has to do with the kernel version.
Since 2.6.38 there is a fix to that problem, and I believe it was introduced somewhere as late as 2.6.37. 
So, it used to be a problem on Natty's generic kernel, but not anymore.
So, AFAIK, no Ubuntu system is presently affected.

---

### Post by falkTX on 2011-03-25
More good news!

Added to the 'latest' PPA:
- Ardour3.0 alpha2 (as 'ardour30': *exact* version as published by Ardour devs!)
- Qtractor (as 'qtractor-svn': latest SVN, most lv2-gtk issues are fixed)
- OpenOctave2 (as 'oomidi-git': not latest build, but gives you a chance to try this amazing app)

Added a couple more VSTs - 'axonlib-vst' [in broken ppa], 'foo-yc20-vst' and 'hybridreverb2-vst'.
All these ^ plugins are Linux native.

NVIDIA drivers are now available, compatible with realtime kernels (Lucid and Maverick).
Only 260.19 version for now (as 'nvidia-current'). Other NVIDIA versions and ATI will come soon.

Enjoy!

---

### Post by bobhamil on 2011-03-25
Hello all, 

Thanks for the info Falktx, I haven't tried much lately, but recent questions from another user has prompted me to get posted the instructions that I have even though they need editing.  If we wait for me to edit...

These are also posted at:
[http://bobhamil.com/PreSonus/](http://bobhamil.com/PreSonus/)

I need to add to these that other DICE chip interfaces can also use these instructions with the addition of using Gscanbus to find out their own vendor and product numbers.  

Bob Hamil

---

### Post by Excds on 2011-03-28
FalkTX: What's happened to the kxstudio site?

---

### Post by vervelover on 2011-03-31
@FalkTX

Hi,
I'm having issues with pulse-jack after updating to the latest release of flashplayer: I can't hear flash audio anymore, but it used to work flawlessy before the update! Is it a known issue or is it just me? I'm on Ubuntu 10.04 with almost all the updates from your ppas installed.
Thanks
Alessio

---

### Post by falkTX on 2011-03-31
hey guys,

the KXStudio website is currently being worked on.
Right now it's not a good time to install KXStudio, as the main changes are just getting uploaded (Gnome compatibility, etc)

All should be fine for the next Ubuntu release 11.04 though

@vervelover:
I'm preparing 'flashplayer-jack' package, so it should solve flash audio issues once and for all.
I'll let you know when it's ready

---

### Post by Excds on 2011-04-01
> **falkTX said:**
> hey guys,

the KXStudio website is currently being worked on.
Right now it's not a good time to install KXStudio, as the main changes are just getting uploaded (Gnome compatibility, etc)

All should be fine for the next Ubuntu release 11.04 though


Ok, so you're recommending Natty as the Ubuntu version of choice to install? I've just got a new work laptop and I'm just in the process of creating a Mavering USB stick...

Anyway I'd be happy to provide bug testing for the new changes. Anything special you need looked into?

---

### Post by falkTX on 2011-04-01
> **Excds said:**
> Ok, so you're recommending Natty as the Ubuntu version of choice to install? I've just got a new work laptop and I'm just in the process of creating a Mavering USB stick...

Anyway I'd be happy to provide bug testing for the new changes. Anything special you need looked into?

well, the new KXStudio will be heavily based on 'Cadence'.
The PPA packages of it are not always up-to-date, so using/checking the git code is recommended:
[http://repo.or.cz/w/cadence.git](http://repo.or.cz/w/cadence.git)
```
git clone git://repo.or.cz/cadence.git
make
python src/cadence.py
```

Notes:
1 - The 'tools' section requires install via 'make install'
2 - 'Audio plugins PATH' does not work yet.

---

### Post by Excds on 2011-04-02
> **falkTX said:**
> well, the new KXStudio will be heavily based on 'Cadence'.

So, was that a yes or no to either Natty or Maverick? :-)

I'll try Maverick and see the state of cadence.

---

### Post by falkTX on 2011-04-02
> **Excds said:**
> So, was that a yes or no to either Natty or Maverick? :-)

I'll try Maverick and see the state of cadence.

Once time comes, I'll make some nice Natty based ISOs (at least Gnome and KDE).

Note that all versions will have "build your own studio" thing.
Still need to think about this a bit, but the idea is to provide a minimal/command-line-only install ISO that users can use as a base to install whatever they like.

---

### Post by sgx on 2011-04-04
Hi, I think a barebones iso including a full apt-dpkg-synaptic install
would be a good option, even if a lightweight WM was required. Even
a windows user can figure out synaptic.
Cheers

---

### Post by maghoxfr on 2011-04-04
> **sgx said:**
> Hi, I think a barebones iso including a full apt-dpkg-synaptic install
would be a good option, even if a lightweight WM was required. Even
a windows user can figure out synaptic.
Cheers

Agree, the command line otion would kill me.

---

### Post by falkTX on 2011-04-05
> **maghoxfr said:**
> Agree, the command line otion would kill me.

Really?
It's not that hard...

Let's make a quick test, pretending we've downloaded and installed the ISO.

**Step 1** - Connect to internet:
A) Via cable, run
```
sudo dhclient
```
B) Via wireless, do something like:
```
cnetworkmanager -C "NetworkName" --wpa-key="blahblah"
```

**Step 2** - Install your favourite desktop:
```
sudo apt-get update
sudo apt-get install kxstudio-desktop-[gnome|kde|xcfe]
```

**Step 3** - Reboot to get the desktop GUI, then you can install new stuff using Synaptic or whatever.


Is this that really hard?

---

### Post by sgx on 2011-04-05
It's not hard, but I would love a 'synaptic only' distro, (which I
should just remaster on my own anyway) because of precision, just installing what I want/need. I only use a dozen or so apps on a regular basis, so an apt-get update and install is vast overkill
for me. But most users like holding the thick end of the bat :)
Cheers

---

### Post by maghoxfr on 2011-04-06
> **falkTX said:**
> Really?
It's not that hard...

Let's make a quick test, pretending we've downloaded and installed the ISO.

**Step 1** - Connect to internet:
A) Via cable, run
```
sudo dhclient
```
B) Via wireless, do something like:
```
cnetworkmanager -C "NetworkName" --wpa-key="blahblah"
```

**Step 2** - Install your favourite desktop:
```
sudo apt-get update
sudo apt-get install kxstudio-desktop-[gnome|kde|xcfe]
```

**Step 3** - Reboot to get the desktop GUI, then you can install new stuff using Synaptic or whatever.


Is this that really hard?

Well...put it that way and it's not that hard! But if you didn't tell me I wouldnt' have known that! I do some command line, but it's not my strength. Thanks for that.

---

### Post by falkTX on 2011-04-07
> **maghoxfr said:**
> Well...put it that way and it's not that hard! But if you didn't tell me I wouldnt' have known that! I do some command line, but it's not my strength. Thanks for that.

I agree that this install method should come with instructions.
Maybe pack a REAME and the ISO together in a tar.gz file?

---

### Post by sgx on 2011-04-09
> **falkTX said:**
> I agree that this install method should come with instructions.
Maybe pack a REAME and the ISO together in a tar.gz file?
I would both include adequate noobie docs, as well as have them as
a separate download, and also posted online, so users see how to unpack everything from within windows, how to burn the iso, usb
install, and basic synaptic usage etc
Cheers

---

### Post by rusk911 on 2011-04-09
For noobs it SHOULD be one big knob called "install it". And little "advansed install" menu for DE choosing radio buttons.

---

### Post by matt_symes on 2011-04-11
> For noobs it SHOULD be one big knob called "install it". And little "advansed install" menu for DE choosing radio buttons.

Agreed.

---

### Post by vervelover on 2011-04-12
What about adding k-meter to one of your ppas?

[http://mzuther.github.com/out/kmeter/](http://mzuther.github.com/out/kmeter/)

---

### Post by Excds on 2011-04-23
What's the current status of the repositories? What's happening with the project? It's been awfully quite here for a little while. :-/

Oh, and I'm also having trouble with installing with the current repositories. Anything broken? Anyone else having troubles, or is it just me?

---

### Post by falkTX on 2011-04-25
> **Excds said:**
> What's the current status of the repositories? What's happening with the project? It's been awfully quite here for a little while. :-/

Oh, and I'm also having trouble with installing with the current repositories. Anything broken? Anyone else having troubles, or is it just me?

Well, my laptop broke some days ago, and I've been quite busy with other stuff (coding and family)

The PPAs may become a little "unstable" right now as the work for Natty is finalized.
Everything should be ok after Natty is released.

---

### Post by el.shupacabras on 2011-04-27
Only "Gladish" and "Laditray"do not work but because of "Unity"
Replacement "Gladish"with "Carla"
the rest works smoothly!
thanks falk

---

### Post by danmbox on 2011-04-29
falkTX, I have Ubuntu Lucid with my own backported and fixed lash3 (from my PPA) and so I can't install some of your packages (e.g. zynaddsubfx, nonsequencer depend on liblash2 which conflicts). You could look at lash3 and lashwrap packages from my PPA [1], they have some obvious fixes that I also reported on Launchpad. I get a lot of mileage from lash and lashwrap.

This, of course, if you still intent to support Lucid.

[1] [https://launchpad.net/~danmbox/+archive/ppa](https://launchpad.net/~danmbox/+archive/ppa)

BTW, is this "the" place to talk about kxstudio? Kudos for putting up kxstudio.sourceforge.net, but it's still missing links to a bug tracker, mailing list and / or forum so it's not clear where to go.

---

### Post by falkTX on 2011-04-30
> **danmbox said:**
> falkTX, I have Ubuntu Lucid with my own backported and fixed lash3 (from my PPA) and so I can't install some of your packages (e.g. zynaddsubfx, nonsequencer depend on liblash2 which conflicts). You could look at lash3 and lashwrap packages from my PPA [1], they have some obvious fixes that I also reported on Launchpad. I get a lot of mileage from lash and lashwrap.

This, of course, if you still intent to support Lucid.

[1] [https://launchpad.net/~danmbox/+archive/ppa](https://launchpad.net/~danmbox/+archive/ppa)

BTW, is this "the" place to talk about kxstudio? Kudos for putting up kxstudio.sourceforge.net, but it's still missing links to a bug tracker, mailing list and / or forum so it's not clear where to go.

hey there,
the lash situation is kinda sad now, as in ubuntu lucid it uses lash.so.2 but on maverick+ lash.so.3

I've been very very busy lately, but my intention is to completely remove lash in favour of ladish (using ladish-compat for apps that depends on lash).
^ This is the same thing debian-multimedia is doing right now.

The webpage is far from complete, again cause I've been busy...
please report any bugs regarding packages in here:
[https://bugs.launchpad.net/kxstudio](https://bugs.launchpad.net/kxstudio)

I may not reply right away, but it's good to report bugs, as it will be a reminder to me.

Things should be back on track really soon though.


PS: I would like to avoid PPA duplications please.
The KXStudio PPAs are managed by a team, so I can grant you access if you just follow some basic rules (to keep consistency). PM if interested.

---

### Post by danmbox on 2011-05-02
> **falkTX said:**
> hey there,
the lash situation is kinda sad now, as in ubuntu lucid it uses lash.so.2 but on maverick+ lash.so.3

That's what I'm saying -- it would be simpler to have lash3 everywhere (so long as you haven't killed it completely). As I've shown in my PPA, it's possible to backport lash3 to Lucid (and rebuild the packages that depend on it).

> **falkTX said:**
> I've been very very busy lately, but my intention is to completely remove lash in favour of ladish (using ladish-compat for apps that depends on lash).
^ This is the same thing debian-multimedia is doing right now.
Yes, I noticed you build packages with +nolash when you can. But it's not always possible -- e.g. for zynaddsubfx. So it's worthwhile to bring lucid to lash3 level.

What is ladish-compat? I can't find such a package.

> **falkTX said:**
> The webpage is far from complete, again cause I've been busy...
please report any bugs regarding packages in here:
[https://bugs.launchpad.net/kxstudio](https://bugs.launchpad.net/kxstudio)


OK. And a forum / mailing list? Is *this* thread the place for discussions?

> **falkTX said:**
> PS: I would like to avoid PPA duplications please.
The KXStudio PPAs are managed by a team, so I can grant you access if you just follow some basic rules (to keep consistency). PM if interested.

OK. I've been backporting audio apps myself since Ubuntu Hardy, so I like your project. I'll send you a PM.

It's hard to completely avoid PPA duplication (e.g. due to our divergent lash policies), but converging as much as possible would be good. That's the reason I posted, in fact.

Do you also talk to the Debian Multimedia team? We should keep close to their versions as well.

---

### Post by falkTX on 2011-05-02
> **danmbox said:**
> That's what I'm saying -- it would be simpler to have lash3 everywhere (so long as you haven't killed it completely). As I've shown in my PPA, it's possible to backport lash3 to Lucid (and rebuild the packages that depend on it). I did backport lash3 before (in the old PPA), but then I started using ladish's lash implementation *(read more below)*, which introduced different lash sonames for different ubuntu versions

> **danmbox said:**
> Yes, I noticed you build packages with +nolash when you can. But it's not always possible -- e.g. for zynaddsubfx. So it's worthwhile to bring lucid to lash3 level.
LASH is deprecated and no longer developed. JACK-session and/or ladish are the way to go. Using ladish's compatible lash headers and lib, we can build apps that need lash, but using ladish implementation.

> **danmbox said:**
> 
What is ladish-compat? I can't find such a package.
 Take a look at: [http://git.debian.org/?p=pkg-multimedia/ladish.git;a=summary](http://git.debian.org/?p=pkg-multimedia/ladish.git;a=summary)
If you didn't know already, ladish will support lash at some time, but for now it has a placeholder (liblash.so.*) that is (almost) completely compatible to lash.
(It has his own headers that you can use to compile against)

> **danmbox said:**
> OK. And a forum / mailing list? Is *this* thread the place for discussions?
I though of that before, but since I don't have network at home it would me hard for me to answer or at least check the conversation there.
I should have net in my house by now, but there's always something that ruins my plans...

> **danmbox said:**
> OK. I've been backporting audio apps myself since Ubuntu Hardy, so I like your project. I'll send you a PM.

It's hard to completely avoid PPA duplication (e.g. due to our divergent lash policies), but converging as much as possible would be good. That's the reason I posted, in fact. I think we can come in an agreement here.
Are you still using LASH for audio projects? or is it just a matter of software compilation?
If it is the second, it could be solved with debian's ladish-compat, which I totally agree with.

> **danmbox said:**
> Do you also talk to the Debian Multimedia team? We should keep close to their versions as well.
I'm not a member of the debian multimedia team, neither I had tried to be, yet. It's still the network thing, as I want to get network first before trying to get in.

---

### Post by danmbox on 2011-05-02
> **falkTX said:**
> Are you still using LASH for audio projects? or is it just a matter of software compilation?
If it is the second, it could be solved with debian's ladish-compat, which I totally agree with.

I'm using jack1, lash and lash_wrap. That way I can save a list of the apps running under jack (including non-lash command-line apps using lash_wrap). Then I can restore them when needed. Futhermore, apps like jack-rack and jack-mixer save their state in the LASH project.

If I could find something equivalent I might switch to ladish. But from what I see

* most apps have no idea about jack-session

* ladish requires jack2, and furthermore is not supported by jack-rack and jack-mixer (they won't save their states under ladish)

I'll look into jack2, though I don't really want to switch yet.

---

### Post by falkTX on 2011-05-02
> **danmbox said:**
> I'm using jack1, lash and lash_wrap. That way I can save a list of the apps running under jack (including non-lash command-line apps using lash_wrap). Then I can restore them when needed. Futhermore, apps like jack-rack and jack-mixer save their state in the LASH project.

If I could find something equivalent I might switch to ladish. But from what I see

* most apps have no idea about jack-session

* ladish requires jack2, and furthermore is not supported by jack-rack and jack-mixer (they won't save their states under ladish)

I'll look into jack2, though I don't really want to switch yet.

ladish does *not* require jack2, but jackdbus.
jack1 doesn't have dbus support by default, you'll have to use a patch.
the author of jackdbus says:
> jackdbus for jack1 exists but is not accepted upstream for various reasons. (...)
the jack1 version of jackdbus is less used and thus less tested mainly because of decreasing motivation to improve it because of upstream rejections.
For me, jack2 is really the way to go. the (proper and tested) jackdbus implementation and multi-core support are 2 very strong points for jack2.

and btw:
> LADI Session Handler is a rewrite of  LASH. 
*(more at [http://ladish.org/wiki/ladi](http://ladish.org/wiki/ladi))*

LADISH is way better than LASH, here are some reasons why:
 - Any good jack app will work with ladish (level 0)
 - No need to link to a library (uses SIGUSR1 to save, which means no soname issues)
 - You can set-up 'studios' (pre-configured jack setups) and load them at any time
 - project files are totally system independant, so you can move them between PCs (not a easy thing to do with LASH)
 - a2jmidid support (to what is possible to achieve with it)
 
ladish has an official GUI "gladish" that provides all the ladish features.
I'm however developing a tool that extends it. It combines my jack-tools, patchbay, and the 'Klaudia' like add-new-application style.

ladish could use some more documentation and some video tutorials though...
I plan to make some videos, but just not right now.
the official tutorial is this one -> [http://ladish.org/wiki/tutorial](http://ladish.org/wiki/tutorial)
(it doesn't mention rooms and projects, which is new in ladish v0.3)

---

### Post by falkTX on 2011-05-02
@danmbox I forgot to tell you this, but I'll soon add jack1 support to the PPAs (and thus kxstudio).
I'll package jack1 in a separate PPA and make it replace the default jack2 in the main PPA.
The jack1 ppa is already created: (no packages on it yet)
[https://launchpad.net/~kxstudio-team/+archive/jack1](https://launchpad.net/~kxstudio-team/+archive/jack1)

Some apps will be rebuild for better compatibility, at least qjackctl and wine stuff.
The jack1 version in there will have jackdbus enabled, as it is needed for KXStudio and my tools.

PS: for conversation, we can use IRC, server irc.freenode.net, channel #kxstudio
Keep in mind that I'm offline most of the time...

---

### Post by danmbox on 2011-05-04
> **falkTX said:**
> @danmbox I forgot to tell you this, but I'll soon add jack1 support to the PPAs (and thus kxstudio).
I'll package jack1 in a separate PPA and make it replace the default jack2 in the main PPA.

I've been trying to understand & solve the jack1 vs. jackd2 situation in Lucid vs. Natty vs. KXStudio Lucid for the last day. Let's take an app like ardour. Natty's ardour depends on libjack-jackd2-0 | libjack0-0.116. This libjack0-0.116 is a new virtual package that both Natty's jack1 and Natty's jack2 provide. Therefore Natty allows you to install ardour with either jackd1 or jackd2. 

In fact, if you build any app against the Natty version of libjack-dev (or libjack-jack2-dev), it will automatically depend on that virtual package as an alternative, letting the user install either jack1 or jack2. It works via a shlibs file.

However, KXStudio Lucid's ardour depends on libjack0 and not the virtual package libjack0-0.116, which suggests you built it with a pre-transition libjack-dev. It will not allow me to install jack2.

So, I don't think you really need to build separately against jack1. You need to build against a "modern" (Natty or Debian) version of either libjack-dev or libjack-jack2-dev, and everything will be fine. Your packages will be installable on both jack1 and jack2 systems.

---

### Post by danmbox on 2011-05-04
As an aside: I solved the problems on my system by hacking the jackd2 source package to remove a Conflicts: line, then creating a dummy libjack0 deb using the equivs tool (apt-get install equivs). This allows me to install jackd2 (compiled from the hacked package) and uninstall jack1, without breaking any "old" jack apps.

I will see how jack2 works for me. If it's fine I'll probably switch to Ladish (though I don't like it that many packages have to be altered to build against Ladish instead of lash).

---

### Post by falkTX on 2011-05-04
let me try to make this clear:

JACK2 is in the KXStudio-Team PPAs as default and *only* JACK version.
the real lib files are stored in libjack0 and libjack-jackd2-0 has nothing.

I did ported the code from debian to allow libjack0|libjack-jackd2-0, although in the PPA libjack-jackd2-0 is a dummy package that depends on libjack0.
(some apps still need to be rebuild to catch this recent 'fix').

The thing is, whatever the user installs, jackd/jackd2/etc/etc, when using the KXStudio-Team PPA, it will *always* get jack2, as it is currently overriding any other jack packages in the system.
This is my way of fixing the jack-debian mess, and it works pretty fine.

The only problem now is the people that still want jack1.
For that single reason I created the jack1 PPA, and I'll soon package it.
(the jack1 ppa is empty for now)
When the user adds this jack1 PPA, jack1 will (again) forcedly override any jack version in the system, replacing the jack2.

^ This way we can safely have 2 jack versions without any conflict at all.
The only conflict that may happen is when we enabled the jack1 ppa and want to revert back to the default jack2.


tell me if this is clear enough (I know my english is not the best...)

---

### Post by danmbox on 2011-05-04
OK, so we both hacked the jackd2 source packages, but in different ways... I've described mine (pretty simple, just remove a Conflicts: and create an empty libjack0 package). Now let me try to understand yours.

Tell me, what did you not like about the Natty (or Sid) jack solutions? If you need jackd2 for KXStudio, why not depend directly on it, in whatever packages need that (e.g. ladish)?

---

### Post by falkTX on 2011-05-04
> **danmbox said:**
> OK, so we both hacked the jackd2 source packages, but in different ways... I've described mine (pretty simple, just remove a Conflicts: and create an empty libjack0 package). Now let me try to understand yours.

Tell me, what did you not like about the Natty (or Sid) jack solutions? If you need jackd2 for KXStudio, why not depend directly on it, in whatever packages need that (e.g. ladish)?

well, I got lot of issues when using jack2 in Natty.
everything works fine with jack1 (since is what is being compiled against, although they hack the shlibs for libjack0|libjack-jackd2-0).

you're using jack1 in ubuntu, so i'm not sure you tested this.

the issues I got were mostly in Wine and non-free apps like Renoise and energyXT2.
Wine simply refused to start (complaining about libs misconfiguration), while the non-free apps just crashed.

Wine is kinda ok since it can be recomplied, but not possible with Renoise...

I first tried some different approaches to the situation, until I got where I am now - jack2 as default replacing everything else.
I don't know of any special reason why we should stick to jack1, so I made the change.

---

### Post by danmbox on 2011-05-04
Right -- I've just installed jackd2 today. It will take me a few days to see how it works.

I trust the jackd1 code base more until I understand jackd2. You know that jackd2 is not an updated version of jackd1, but a rewrite, right?

I see indeed that wine doesn't seem to like the jack driver (winecfg starts, but test sound failed). I don't know if it worked before (with jack1) or not.

---

### Post by Excds on 2011-05-05
About the tal-plugins-vst package. Are the presets for noisemaker included somehow? The deb only contains the .so files. Checked out the svn source (and yes, I'm right now very tired and haven't read it), but I didn't see anything obvious that would be a bunch of preset files.

---

### Post by Excds on 2011-05-06
Note to self: Don't post on forums when being tired enough that the brain approaches dyslexia...

In other words, never mind... :-)

On topic: When I upgraded my laptop to natty, added the KXStudio PPA:s and installed the meta packages I got a dependency problem while installing. The missing dependency was rtirq-init. Something you missed?

---

### Post by vervelover on 2011-05-06
Hi FalkTK,

I just installed the 2.6.33-29 rt kernel on Lucid from kxstudio kernel ppa, but fglrx won't build anymore on it, even the rt-patched version in your repos doesn't work. Would be nice to have a 2.6.31-pae rt kernel, at the moment I'm forced to lowlatency because of ATI drivers but would really like to try a rt-pae kernel with my system.
Thanks
Alessio

---

### Post by falkTX on 2011-05-06
> **Excds said:**
> About the tal-plugins-vst package. Are the presets for noisemaker included somehow? The deb only contains the .so files. Checked out the svn source (and yes, I'm right now very tired and haven't read it), but I didn't see anything obvious that would be a bunch of preset files.

There is a simple problem with these presets, for example check this one:
[http://www.emergeaudio.com/freepresets.html](http://www.emergeaudio.com/freepresets.html)
Download and you'll get in the readme:
> You may not modify, sell, distribute or transfer the SOFTWARE.
:(

---

### Post by falkTX on 2011-05-06
> **Excds said:**
> Note to self: Don't post on forums when being tired enough that the brain approaches dyslexia...

In other words, never mind... :-)

On topic: When I upgraded my laptop to natty, added the KXStudio PPA:s and installed the meta packages I got a dependency problem while installing. The missing dependency was rtirq-init. Something you missed?

Ubuntu has different packages between versions, so keeping a single meta-package to handle them all does not always work.

I'll check this 'rtirq-init' package right now

---

### Post by falkTX on 2011-05-06
> **vervelover said:**
> Hi FalkTK,

I just installed the 2.6.33-29 rt kernel on Lucid from kxstudio kernel ppa, but fglrx won't build anymore on it, even the rt-patched version in your repos doesn't work. Would be nice to have a 2.6.31-pae rt kernel, at the moment I'm forced to lowlatency because of ATI drivers but would really like to try a rt-pae kernel with my system.
Thanks
Alessio

Please note that I didn't package any of the kernels, they are based on this ppa:
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)
I simply modded the packages a little to make them installable (and "runable") in all Ubuntu versions.

This means rt-31-pae will not be available, just rt-33-pae.

I already patched the nvidia drivers, just give me some time to take care of the ATI ones
(this should be ready by tomorrow, so please report back then)

---

### Post by esantidp on 2011-05-06
Hi, 

I'm having problems with the ppa in lucid.

Here's the info

eggie@ubuntu:~$ sudo add-apt-repository ppa:kxstudio-team/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A809F6C307B583133B3891B287538FEDDF8063EB
gpg: requesting key DF8063EB from hkp server keyserver.ubuntu.com
gpg: key DF8063EB: "Launchpad PPA for KXStudio Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
eggie@ubuntu:~$ sudo apt-get update
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/kxstudio-team-ppa-lucid.list

---

### Post by falkTX on 2011-05-06
> **esantidp said:**
> Hi, 

I'm having problems with the ppa in lucid.

Here's the info

eggie@ubuntu:~$ sudo add-apt-repository ppa:kxstudio-team/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A809F6C307B583133B3891B287538FEDDF8063EB
gpg: requesting key DF8063EB from hkp server keyserver.ubuntu.com
gpg: key DF8063EB: "Launchpad PPA for KXStudio Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
eggie@ubuntu:~$ sudo apt-get update
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/kxstudio-team-ppa-lucid.list

This is a known ubuntu bug (and very stupid actually...)

just open '/etc/apt/sources.list.d/kxstudio-team-ppa-lucid.list' and remove the (empty) line starting with 'n'

Does anyone knows a definitive fix for this?

---

### Post by rusk911 on 2011-05-08
Just tryed Cadence. Glad to see ALSA-JACK option there. I have been removed PulseAudio at all. But ALSA-JACK is not working in Cadence. The node appears in Claudia but no sound produced and Audacious won/t start to play.. Logs tool is not working too. So I continue using laditray.

---

### Post by falkTX on 2011-05-09
> **rusk911 said:**
> Just tryed Cadence. Glad to see ALSA-JACK option there. I have been removed PulseAudio at all. But ALSA-JACK is not working in Cadence. The node appears in Claudia but no sound produced and Audacious won/t start to play.. Logs tool is not working too. So I continue using laditray.

hm... can you run 'jack_logs' in a terminal and post here the output?

and which Ubuntu version/architecture are you using? (to test alsa2jack thing)

---

### Post by falkTX on 2011-05-09
Good News!

I was able to make the ATI + rt-33 patch this weekend.
Already in the repos (ppa:kxstudio-team/kernel), please test ;)

Also, the lowlatency kernel ( 2.6.38 ) is now installable in Lucid and Maverick.

(everything seems to work fine for me. if it doesn't for you, please say so)

---

### Post by rusk911 on 2011-05-10
jack_logs told me this error:

terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc

~$ uname -a
Linux test-laptop 2.6.38-8-lowlatency #42+all1~maverick1-Ubuntu SMP PREEMPT Fri Apr 29 23:04:35 UTC 20 i686 GNU/Linux

Ubuntu 10.10 32 bit.

---

### Post by vervelover on 2011-05-10
@FalkTX

just tried you updated fglrx driver with kernel 2.6.33-29 rt-pae in your ppa, but it doesn't install (gives an error while building the module for the kernel), had to revert to 2.6.32..

---

### Post by falkTX on 2011-05-10
> **vervelover said:**
> @FalkTX

just tried you updated fglrx driver with kernel 2.6.33-29 rt-pae in your ppa, but it doesn't install (gives an error while building the module for the kernel), had to revert to 2.6.32..

really?
I got it working (building) on lucid and natty.
I didn't test the rt-pae though...

did you used the driver from the kernel repo?
version = 2:8.841-0ubuntu1+rt1~lucid1

it won't work with any other driver version...

---

### Post by vervelover on 2011-05-12
Yes I only installed the driver and the kernel from KXSTUDIO kernel ppa, I'm on Lucid 32 bit, fglrx won't install, I'm also afraid it's because of the pae kernel.. it works no problem with lowlatency-pae though..

---

### Post by falkTX on 2011-05-12
> **vervelover said:**
> Yes I only installed the driver and the kernel from KXSTUDIO kernel ppa, I'm on Lucid 32 bit, fglrx won't install, I'm also afraid it's because of the pae kernel.. it works no problem with lowlatency-pae though..

it should work just fine with the lowlatency, the problem is just the realtime.

if it's not too much to ask, can you try removing the rt-pae and install just the normal one?
thanks

---

### Post by falkTX on 2011-05-12
I've written some more stuff on website (finally!), mainly the help:install section:
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help](http://kxstudio.sourceforge.net/mediawiki/index.php/Help)

I'm not confident enough to call this a release, but it's installable now (and works fine).

I'll update the 1st post of this thread to point there too

---

### Post by vervelover on 2011-05-13
@ FalkTK

I just tried with kernel 2.6.33-29 rt and fglrx doesn't install as well..

---

### Post by Excds on 2011-05-13
Hmm, another question about tal noisemaker. When I was less tired I realized that to change patches I should use qtractor's track settings. Only problem is that changing patches didn't work. With other plugins it works fine, but not noisemaker.

Anyone having the same problems?

---

### Post by falkTX on 2011-05-18
> **vervelover said:**
> @ FalkTK

I just tried with kernel 2.6.33-29 rt and fglrx doesn't install as well..

Please try to drop by in IRC, so we can talk real-time.
irc.freenode.net, #kxstudio

thanks

---

### Post by aaronLund on 2011-05-18
Allow me to spam the board with my very first all-Linux edited video (did it in kdenlive).  

Falktx, kxstudio is truly the best thing around.

[http://www.youtube.com/watch?v=gmfaXnjT5g0](http://www.youtube.com/watch?v=gmfaXnjT5g0)

Many thanks.

---

### Post by barisurum on 2011-05-19
I've a problem! After I switched alsa bridge support to pulseaudio to work with kdenlive, then I switched it back to jack and now no alsa application has sound even if I connect jackp to output! The error in the log is:

> ERROR: Unknown destination port in attempted (dis)connection src_name [jack_P-01:out_000] dst_name [alsa_pcm:playback_1]

FalkTX a little help here :(

edit: I solved it by manually editing .asoundrc and changing jack input-output port names to system:playback_1 and 2

---

### Post by wbm on 2011-05-19
Hello, in regards to Kernels, what is the difference between these and which one should be used for audio recording? Can I install only one?
Thank you! I am in the process of upgrading from a fresh Kubuntu 11.04 to KXStudio via the new web instructions.


[LIST]
[*]kxstudio-kernel-generic
[*]kxstudio-kernel-generic-pae *(32bit only)*
[*]kxstudio-kernel-preempt *(10.04 64bit only)*
[*]kxstudio-kernel-lowlatency
[*]kxstudio-kernel-realtime
[*]kxstudio-kernel-realtime-31
[/LIST]

---

### Post by falkTX on 2011-05-20
> **barisurum said:**
> I've a problem! After I switched alsa bridge support to pulseaudio to work with kdenlive, then I switched it back to jack and now no alsa application has sound even if I connect jackp to output! The error in the log is:



FalkTX a little help here :(

edit: I solved it by manually editing .asoundrc and changing jack input-output port names to system:playback_1 and 2

hey there, sorry for any issues on this (I though this was already fixed, seems like it's not :()

Can you please give me details about your system?
(ubuntu version, architecture, and alsa version)

thanks

---

### Post by falkTX on 2011-05-20
> **wbm said:**
> Hello, in regards to Kernels, what is the difference between these and which one should be used for audio recording? Can I install only one?
Thank you! I am in the process of upgrading from a fresh Kubuntu 11.04 to KXStudio via the new web instructions.


[LIST]
[*]kxstudio-kernel-generic
[*]kxstudio-kernel-generic-pae *(32bit only)*
[*]kxstudio-kernel-preempt *(10.04 64bit only)*
[*]kxstudio-kernel-lowlatency
[*]kxstudio-kernel-realtime
[*]kxstudio-kernel-realtime-31
[/LIST]

you should try the kernel that works best for you.

generic is as it says - "generic".
this one comes by default in Ubuntu.

lowlatency is the same as generic, just with some minor kernel settings tweaked (clock frequency).
as the name says, it's focused for "low-latency", but not as good as realtime.

if realtime works for you (it has some major problems with natty right now), use it.
just don't experiment too much when using the realtime kernel (you may crash the system  easily...)

My personal recommendation is to use lowlatency most of the time, but to try realtime when you need something more cpu/disk intensive (like recording).

sadly the real-time kernel is getting old (latest stable kernel is 2.6.39, and realtime is 2.6.33) and does not work for everybody...

---

### Post by wbm on 2011-05-20
> **falkTX said:**
> you should try the kernel that works best for you.

generic is as it says - "generic".
this one comes by default in Ubuntu.

lowlatency is the same as generic, just with some minor kernel settings tweaked (clock frequency).
as the name says, it's focused for "low-latency", but not as good as realtime.

if realtime works for you (it has some major problems with natty right now), use it.
just don't experiment too much when using the realtime kernel (you may crash the system  easily...)

My personal recommendation is to use lowlatency most of the time, but to try realtime when you need something more cpu/disk intensive (like recording).

sadly the real-time kernel is getting old (latest stable kernel is 2.6.39, and realtime is 2.6.33) and does not work for everybody...

Thank you.
2 more follow up questions:
what is a -pae kernel (lot's of contradicting info on the web)
what si the difference between :

[LIST]
[*]kxstudio-kernel-realtime
[*]kxstudio-kernel-realtime-31
[/LIST]
Thanks!!!

---

### Post by falkTX on 2011-05-20
> **wbm said:**
> Thank you.
2 more follow up questions:
what is a -pae kernel (lot's of contradicting info on the web)
what si the difference between :

[LIST]
[*]kxstudio-kernel-realtime
[*]kxstudio-kernel-realtime-31
[/LIST]
Thanks!!!

PAE is a kernel extension that allows to use more than 4Gb of RAM in a 32bit system.
There were some people saying it caused slowdown, but a recent Phoronix benchmark proved those assumptions were false.
I'm not sure about this, but I think Apple/MacOS uses PAE by default...
You should use it if you're on 32bit and have a pc with >4gb RAM.

the realtime vs realtime-31 is just about the kernel version.
"realtime" is the most recent realtime kernel (2.6.33), and "realtime-31" is the old 2.6.31.

Not sure how much useful the *-31 really is now...

---

### Post by wbm on 2011-05-20
> **falkTX said:**
> PAE is a kernel extension that allows to use more than 4Gb of RAM in a 32bit system.
There were some people saying it caused slowdown, but a recent Phoronix benchmark proved those assumptions were false.
I'm not sure about this, but I think Apple/MacOS uses PAE by default...
You should use it if you're on 32bit and have a pc with >4gb RAM.

the realtime vs realtime-31 is just about the kernel version.
"realtime" is the most recent realtime kernel (2.6.33), and "realtime-31" is the old 2.6.31.

Not sure how much useful the *-31 really is now...

Thank you!!!
Now patiently awaiting the ISOs :)

---

### Post by tanndo on 2011-05-20
Hi,

I've got to step 3 from 
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help:Install:FromUbuntu](http://kxstudio.sourceforge.net/mediawiki/index.php/Help:Install:FromUbuntu)

I started off with ubuntu 10.04.2 (i.e. gnome)
Now just installed kxstudio-desktop-kde4
It asked me which display manager I wanted as default, gdm or kdm .
I Choose kdm which I assume is right as I'll be using Kde?
Later could I also install 
  kxstudio-desktop-gnome
and then choose at login gnome or kde ? E.g. If it turns out 
I prefer gnome to KDE

In step 4 I guess I only need 
  kxstudio-meta-all
?
I'm just dipping my toes in the water so to speak, e.g. planning on
using audacity and ardour initially. Whats in all the other ...-meta's?
e.g. kxstudio-meta-advanced and kxstudio-meta-non-free ? Please point
me to URL if its documented online.

I guess I can leave the kernel for now but later if I try
  sudo apt-get install kxstudio-kernel-realtime
and it is no good, how can I get back to the safety of
  kxstudio-kernel-generic
I guess it's allreay "installed" but how to enable ?
And finally if I decided to stick with KDE is there a way of removing
all the gnome stuff as I'm a bit short on disk space.

Sorry for all the Questions in one. It's late, I'm tired, need sleep,
Will leave kxstudio-meta-all to install overnight and check back in morning.
T

---

### Post by jflesher on 2011-05-20
I'm at a stand still with the sound preference (gnome-volume-control) that got replaced during install of KXStudio; it removed the ability to change my input and output; which makes it worthless; since this is the main function of this program; how do I fix this? Can I go back to the original version? If so how. 

I don't like the changes it made to nautilus; anyway to go back to the original version of this also?

I can not test it; since I can not change my input or output device; also this makes my computer worthless for any sound related work I do. I have many devices attached; the default is a mic and speakers; not the ones I need to use to test this with.

Update: I relieve now that this is due to the newer Gnome components;  which I do not like at all; its time I drop Gnome all together; I do not  like the direction its heading; like its trying to me more like  Windoze.

I duplicated this with this thread [http://ubuntuforums.org/showthread.php?p=10843042#post10843042](http://ubuntuforums.org/showthread.php?p=10843042#post10843042) so ignore this one; thanks.

---

### Post by jflesher on 2011-05-21
Where do you file bugs?

sudo apt-get remove -y  kxstudio-default-settings

The following packages were automatically installed and are no longer required:
  kxstudio-artwork-kdm kxstudio-artwork kxstudio-artwork-wallpaper kde-style-qtcurve qtcurve libkdecorations4 gtk2-engines-qtcurve kxstudio-menu kxstudio-artwork-icons oxygen-cursor-theme-extra kxstudio-artwork-ksplash kwin-style-qtcurve oxygen-icon-theme-complete
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kxstudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 709 kB disk space will be freed.
(Reading database ... 407250 files and directories currently installed.)
Removing kxstudio-default-settings ...
sed: can't read /etc/kde4/kdm/kdmrc: No such file or directory
dpkg: error processing kxstudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kxstudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can not uninstall this till you fix this one.

Update: I'm uninstalling it to see if I can get back to an earlier version of Gnome, gnome-volume-control 2.32 sucks, I want version 2.26 or at least a version before it started to suck, so I can switch my input device, I know there is another way to do this; I have been using Linux from the beginning, seems we had to edit a file back then; but I do not see that file any more.  

Thanks.

---

### Post by oneillkza on 2011-05-21
Bugs can be reported here: [https://bugs.launchpad.net/kxstudio/](https://bugs.launchpad.net/kxstudio/)

But since it seems to be mainly FalkTX working on them, and he reads this thread too, he'll probably take a look at it soon one way or the other.

---

### Post by falkTX on 2011-05-22
> **tanndo said:**
> Hi,

I've got to step 3 from 
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help:Install:FromUbuntu](http://kxstudio.sourceforge.net/mediawiki/index.php/Help:Install:FromUbuntu)

I started off with ubuntu 10.04.2 (i.e. gnome)
Now just installed kxstudio-desktop-kde4
It asked me which display manager I wanted as default, gdm or kdm .
I Choose kdm which I assume is right as I'll be using Kde?
Later could I also install 
  kxstudio-desktop-gnome
and then choose at login gnome or kde ? E.g. If it turns out 
I prefer gnome to KDE

In step 4 I guess I only need 
  kxstudio-meta-all
?
I'm just dipping my toes in the water so to speak, e.g. planning on
using audacity and ardour initially. Whats in all the other ...-meta's?
e.g. kxstudio-meta-advanced and kxstudio-meta-non-free ? Please point
me to URL if its documented online.

I guess I can leave the kernel for now but later if I try
  sudo apt-get install kxstudio-kernel-realtime
and it is no good, how can I get back to the safety of
  kxstudio-kernel-generic
I guess it's allreay "installed" but how to enable ?
And finally if I decided to stick with KDE is there a way of removing
all the gnome stuff as I'm a bit short on disk space.

Sorry for all the Questions in one. It's late, I'm tired, need sleep,
Will leave kxstudio-meta-all to install overnight and check back in morning.
T

I've been quite busy lately, so I haven't documented everything yet.

I'll write down some more info tomorrow.

---

### Post by falkTX on 2011-05-22
> **jflesher said:**
> Where do you file bugs?

sudo apt-get remove -y  kxstudio-default-settings

The following packages were automatically installed and are no longer required:
  kxstudio-artwork-kdm kxstudio-artwork kxstudio-artwork-wallpaper kde-style-qtcurve qtcurve libkdecorations4 gtk2-engines-qtcurve kxstudio-menu kxstudio-artwork-icons oxygen-cursor-theme-extra kxstudio-artwork-ksplash kwin-style-qtcurve oxygen-icon-theme-complete
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kxstudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 709 kB disk space will be freed.
(Reading database ... 407250 files and directories currently installed.)
Removing kxstudio-default-settings ...
sed: can't read /etc/kde4/kdm/kdmrc: No such file or directory
dpkg: error processing kxstudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kxstudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can not uninstall this till you fix this one.

Update: I'm uninstalling it to see if I can get back to an earlier version of Gnome, gnome-volume-control 2.32 sucks, I want version 2.26 or at least a version before it started to suck, so I can switch my input device, I know there is another way to do this; I have been using Linux from the beginning, seems we had to edit a file back then; but I do not see that file any more.  

Thanks.

Please be patient here, the mixer thing happens because Ubuntu focus on PulseAudio, but KXStudio uses JACK.
This doesn't work right sometimes...

On previous KXStudio (KDE 10.04.3) I had a custom Phonon and KMix that could handle this situation.
I'll make the same thing for KDE Maverick and Natty soon, but I'm not sure how this is possible in Gnome for now.

A simple trick is to open a terminal and run 'alsamixer'.
You can also simply turn off JACK by default, by running 'cadence' and uncheck the "Auto-Start JACK at Login" option.

Regarding Nautilus... well, I really feel like the original Nautilus sucks, so I "upgraded" it to Nautilus-Elementary.
I'll put instructions on how to revert this tomorrow too.


btw, thanks for the report of *-def-settings unistall.
To fix it, run this:
```
sudo touch /etc/kde4/kdm/kdmrc
```
And you can then safely remove it.
I'll fix this soon

---

### Post by stanlea on 2011-05-23
Installation report :
Installation Ubuntu Studio 11.04 64 bits ok
Adding KSstudio PPAs ok
So far all works fine, except... Reaktor  :)  I know it's a win app, but I'd like to keep it, if possible.
QSampler is installed, but not LinuxSampler. So I took the LinuxSampler package from TangoStudio, but it installs another version of Qsampler that doesn't work with KX. So I forced the KXstudio Qsampler re-installation. They work well together.


I have 2 questions :

1 how to fire the realtime kernel ? its version number is lesser than the generic one, and it doesnt appears on the grub list, even if it's installed

2 How to get rid of the black KX studio scheme ? I dislike black a lot...

Not big problems, though.

---

### Post by falkTX on 2011-05-23
> **stanlea said:**
> Installation report :
Installation Ubuntu Studio 11.04 64 bits ok
Adding KSstudio PPAs ok
So far all works fine, except... Reaktor  :)  I know it's a win app, but I'd like to keep it, if possible.
QSampler is installed, but not LinuxSampler. So I took the LinuxSampler package from TangoStudio, but it installs another version of Qsampler that doesn't work with KX. So I forced the KXstudio Qsampler re-installation. They work well together.


I have 2 questions :

1 how to fire the realtime kernel ? its version number is lesser than the generic one, and it doesnt appears on the grub list, even if it's installed

2 How to get rid of the black KX studio scheme ? I dislike black a lot...

Not big problems, though.


hey there


I'll download and try to make Reaktor work. I'll let you know if I got it to work.
(I think I should probably make a general "how to wine apps in kxs" article...)

thanks to remind me of point #1, that's a very frequent question.
I put the answer in the kx page:
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub](http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub)

to completely change the theme, you'll need to change it in 3 places.
Command-line apps to configure style follow up:
 -> gnome-appearance-properties (Gnome)
 -> qtconfig (Qt)
 -> systemsettings (KDE)

If you use a gnome theme, set Qt and KDE style to GTK+.

---

### Post by tanndo on 2011-05-23
Hi,

managed to get stuff installed via

  sudo apt-get dist-upgrade
  sudo apt-get install kxstudio-desktop-kde4
  sudo apt-get install kxstudio-meta-all

There looks to be some great stuff here but personally I couldn't
get comfortable with the KDE theme, especially the black.
So went back to gnome login, gdm via
  
  sudo dpkg-reconfigure gdm

but oh dear it all looked horrible :(
Found how to reset gnome via 

  cd
  rm -rf .gnome .gnome2 .gconf .gconfd .metacity
  sudo /etc/init.d/gdm restart

And now Gnome looks ok-ish but fired up audacity and no menus,
just underscores _, and missing text like "OK" in dialogs,
e.g. unusable,
Any ideas how to fix ?
Thanks

---

### Post by falkTX on 2011-05-23
> **tanndo said:**
> Hi,

managed to get stuff installed via

  sudo apt-get dist-upgrade
  sudo apt-get install kxstudio-desktop-kde4
  sudo apt-get install kxstudio-meta-all

There looks to be some great stuff here but personally I couldn't
get comfortable with the KDE theme, especially the black.
So went back to gnome login, gdm via
  
  sudo dpkg-reconfigure gdm

but oh dear it all looked horrible :(
Found how to reset gnome via 

  cd
  rm -rf .gnome .gnome2 .gconf .gconfd .metacity
  sudo /etc/init.d/gdm restart

And now Gnome looks ok-ish but fired up audacity and no menus,
just underscores _, and missing text like "OK" in dialogs,
e.g. unusable,
Any ideas how to fix ?
Thanks

are you not comfortable just with the theme or also kde?


let's say you want the default theme in Ubuntu ('Ambiance').

1 - open up 'gnome-appearance-properties' and set the theme to Ambiance
(if you don't have ambiance in the theme list, install 'ubuntu-artwork')

2 - open up 'qtconfig' and set the style to GTK+
(if you don't have qtconfig, install "qt4-qtconfig")

3 - open up 'systemsettings', and go to appearance. then change:
Style -> GTK+
Colors -> any bright scheme is ok. you can download the actual ambiance color-scheme if you want
Icons -> Ubuntu
Gtk Theme -> Ambiance

then logoff and login again and the theme is completely changed.

---

### Post by sgx on 2011-05-24
> **falkTX said:**
> hey there


I'll download and try to make Reaktor work. I'll let you know if I got it to work.
(I think I should probably make a general "how to wine apps in kxs" article...)

thanks to remind me of point #1, that's a very frequent question.
I put the answer in the kx page:
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub](http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub)

to completely change the theme, you'll need to change it in 3 places.
Command-line apps to configure style follow up:
 -> gnome-appearance-properties (Gnome)
 -> qtconfig (Qt)
 -> systemsettings (KDE)

If you use a gnome theme, set Qt and KDE style to GTK+.
Hi, sometimes the newest wine breaks a shiny new wineasio.
Not specific to any distro.
Wine 1.3xxx and wineasio 8.xxx may need to be 1.2xxx and 7.xxx
if vst problems become common.

Also, Qt, and xorg are sometimes a poor team when drawing both a windows app gui, and qjackctl gui, so getting a working jackd command,
and using jp1 (from linuxdsp) for connections, can be a system speedup
for jackd/wine/vst users.
Cheers

---

### Post by sgx on 2011-05-24
> **stanlea said:**
> Installation report :
Installation Ubuntu Studio 11.04 64 bits ok
Adding KSstudio PPAs ok
So far all works fine, except... Reaktor  :)  I know it's a win app, but I'd like to keep it, if possible.
QSampler is installed, but not LinuxSampler. So I took the LinuxSampler package from TangoStudio, but it installs another version of Qsampler that doesn't work with KX. So I forced the KXstudio Qsampler re-installation. They work well together.


I have 2 questions :

1 how to fire the realtime kernel ? its version number is lesser than the generic one, and it doesnt appears on the grub list, even if it's installed

2 How to get rid of the black KX studio scheme ? I dislike black a lot...

Not big problems, though.

Not on a ubuntu system, but I had to roll back wineasio to a 7.xxx
in order to use a vsthost, or to run standalone windows versions.
I have the Reaktor Player, and demo, and way too many ensembles,
so the NI bot chides me for not reviewing downloaded ensembles :)
Cheers

---

### Post by falkTX on 2011-05-24
For Wine / WineASIO / Windows VSTs, my personal experience is that Wine1.3 is better.
But you guys are right regarding wineasio 0.8.x, which doesn't seem to work well...

There was an issue in the WineASIO code that broke JACK2 support (which is used in KXStudio).
I've been informed by the author of WineASIO himself, and he made a fix.

I already package the latest version of WineASIO for the PPAs, here's a link:
[https://launchpad.net/~kxstudio-team/+archive/ppa/+sourcepub/1740577/+listing-archive-extra](https://launchpad.net/~kxstudio-team/+archive/ppa/+sourcepub/1740577/+listing-archive-extra)

It works fine for me.

---

### Post by falkTX on 2011-05-24
> **sgx said:**
> Also, Qt, and xorg are sometimes a poor team when drawing both a windows app gui, and qjackctl gui, so getting a working jackd command,
and using jp1 (from linuxdsp) for connections, can be a system speedup
for jackd/wine/vst users.
Cheers

If you have 'ppa:kxstudio-team/kxstudio' ppa enabled, install 'catia' and run it (my own tool).
It's a patchbay just like patchage, but with some more advanced features.

Although it's Qt, I force the app to use Raster paiting, which loads/works much faster.
You can also use it in OpenGL too (check the options), but it doesn't always work...

---

### Post by tanndo on 2011-05-24
> **falkTX said:**
> are you not comfortable just with the theme or also kde?


let's say you want the default theme in Ubuntu ('Ambiance').

1 - open up 'gnome-appearance-properties' and set the theme to Ambiance
(if you don't have ambiance in the theme list, install 'ubuntu-artwork')

2 - open up 'qtconfig' and set the style to GTK+
(if you don't have qtconfig, install "qt4-qtconfig")

3 - open up 'systemsettings', and go to appearance. then change:
Style -> GTK+
Colors -> any bright scheme is ok. you can download the actual ambiance color-scheme if you want
Icons -> Ubuntu
Gtk Theme -> Ambiance

then logoff and login again and the theme is completely changed.

May re-try KDE but for learning audio apps, think I'll stick to gnome
which I know better.
Foolwed your advice: great, looking very gnome like again but still no text in audacity,
e.g. no menus, no text on dialogs. Could be font problem ? Was going to tru and uninstall audacity then reinstall via synaptic but it said it
would also need to remove kxstudio-meta-all and kxstudio-meta-audio
so I didn't do it.
Anything else I can try ?

---

### Post by stanlea on 2011-05-24
Maybe you can try to re-install it via Synaptic.

I checked here after several themes changes and color tweakings : no problems.

---

### Post by tanndo on 2011-05-24
Tried re-install but no joy :(
I can access the menus e.g. alt-F brings up file menu
but there is no text on it. Just lots of  _ where keyboard accelerators
are!

Looking for some audacity error/debug logs but all I could find
was this from dpkg.log:

2011-05-24 22:33:05 configure audacity 1.3.12-8~lucid2 1.3.12-8~lucid2
2011-05-24 22:33:05 status unpacked audacity 1.3.12-8~lucid2
2011-05-24 22:33:05 status half-configured audacity 1.3.12-8~lucid2
2011-05-24 22:33:05 status installed audacity 1.3.12-8~lucid2

Does this look right, "half configured" !!!

Maybe I could remove these two (as not using KDE right now):
  kxstudio-desktop-kde4
  kxstudio-meta-all
then reinstall
  kxstudio-meta-all
Worth a try ?

---

### Post by sgx on 2011-05-24
[http://packages.debian.org/unstable/sound/audacity](http://packages.debian.org/unstable/sound/audacity)

I would use synaptic to uninstall audacity, then download and install
this version, manually,

dpkg -i audacityxxx.deb

which probably will fail, asking for various dependencies, perhaps lib gtk2.0-0, libwxbase2.8 and libwxgtk2.8, maybe a few codecs etc,
so add them manually to the same command

dpkg -i audacityxxx.deb libwxgtk2.8xxx.deb etc

but I would not update any c libraries, as this will probably break your system. Better to try some live dvds of other distros first.

Installing the extra fonts in synaptic surely won't hurt, if you have the disk-space.
Cheers

---

### Post by falkTX on 2011-05-24
Note that Ubuntu now uses the "GlobalMenu" by default...
The normal Gnome session does not use it, but still, there's a chance it's still removing the menus

does any other Gtk app has this issue?

it's safe to uninstall any kxstudio meta-package, you can just install them again later.

---

### Post by stanlea on 2011-05-25
Hi since today's update, jack does not start. I checked the settings, nothing changed.

Any other failure ?

---

### Post by falkTX on 2011-05-25
> **stanlea said:**
> Hi since today's update, jack does not start. I checked the settings, nothing changed.

Any other failure ?

hm... what was updated?

---

### Post by stanlea on 2011-05-25
??? alsa, jack, wineasio, and lot of KX stuff 

In fact after several reboots, it works... mysteries of computing machines

So no problem so far, except with... Audacity, but I'll tell you later.

---

### Post by falkTX on 2011-05-25
> **stanlea said:**
> ??? alsa, jack, wineasio, and lot of KX stuff 

In fact after several reboots, it works... mysteries of computing machines

So no problem so far, except with... Audacity, but I'll tell you later.

hehe, I update the PPA frequently, it's hard to know which specific app/lib was updated...

One thing I noticed is that when JACK get a version update (like in 1.9.6->1.9.7), I need to reboot or else JACK won't work at all...
I guess that happened to you too?

regarding Audacity, I'll rebuild the PPA package, just in case.

---

### Post by bobhamil on 2011-05-29
falkTX, 
  Thank you for the ongoing efforts.
 I just went to try this on a machine with the new debian Xfce 201104 32bit.      
When trying to get Kxstudio by ppa, in Synaptic, I get this set of errors: 
 Ignoring file 'kxstudio-team--debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-kxstudio-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
 Ignoring file 'kxstudio-team-ppa-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team--debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-kxstudio-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-ppa-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Failed to fetch [http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/source/Sources](http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/source/Sources)  404  Not Found 
 Failed to fetch [http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/binary-i386/Packages](http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/binary-i386/Packages)  404  Not Found Some index files failed to download. They have been ignored, or old ones used instead.   

I got the ppa line"ppa:kxstudio-team/" from this page: [http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Repositories](http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Repositories)    
I tried "ppa:kxstudio-team" also, thinking the / at the end was the problem, but got only slightly different errors.     
Am I doing something wrong? 
    Thanks,  Bob Hamil

---

### Post by stanlea on 2011-05-29
Hi bob, quote from the KXstudio site :

> Ubuntu is the official supported distro.
The main reason is the PPAs. PPAs are supposed to support Debian soon... 

So maybe there's something to do, but the main reason is that you're using a Debian and not Ubuntu.

---

### Post by falkTX on 2011-05-29
> **bobhamil said:**
> falkTX, 
  Thank you for the ongoing efforts.
 I just went to try this on a machine with the new debian Xfce 201104 32bit.      
When trying to get Kxstudio by ppa, in Synaptic, I get this set of errors: 
 Ignoring file 'kxstudio-team--debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-kxstudio-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
 Ignoring file 'kxstudio-team-ppa-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team--debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-kxstudio-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Ignoring file 'kxstudio-team-ppa-debian.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
Failed to fetch [http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/source/Sources](http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/source/Sources)  404  Not Found 
 Failed to fetch [http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/binary-i386/Packages](http://ppa.launchpad.net/kxstudio-team//ubuntu/dists/debian/main/binary-i386/Packages)  404  Not Found Some index files failed to download. They have been ignored, or old ones used instead.   

I got the ppa line"ppa:kxstudio-team/" from this page: [http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Repositories](http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Repositories)    
I tried "ppa:kxstudio-team" also, thinking the / at the end was the problem, but got only slightly different errors.     
Am I doing something wrong? 
    Thanks,  Bob Hamil

The answer to this problem is very simple - KXStudio does not support Debian.

Though if someone is willing to offer a good host plan, I can manually rebuild the packages against it...

---

### Post by bobhamil on 2011-05-30
Thanks for the help guys, 
I hope I'm a better sound engineer than I am a Linux user.  I waste so incredibly much time on dead ends like this - trying to use the wrong ppa's on the wrong disto...duh!!!  
I've wasted another hour trying to write this and ask more questions, but the forum logs me out with no warning.  I only find out when I try to preview post, and it asks me to log in, but when I do, what I've written is gone.  If I use the back button to try to get back to what I've written, it's still gone!!!!  
If I write in gedit, paste it into the forum page and can see it in the forum screen, use preview post, it says I have to write something in order to preview anything... ARRRRG! 

I'll try asking questions in short posts so there's not time to get logged out...

Thanks again, 
Bob Hamil

---

### Post by bobhamil on 2011-05-30
I have a 32 bit kxstudio dvd, but don't see it anymore on sourceforge.  I notice as I watch this forum that there's been lots of changes since burning the dvd in Feb.  If I install the 32 bit dvd will it update to the current kxstudio?  
Thanks, 
Bob

---

### Post by bobhamil on 2011-05-30
falkTX, 
What does "offer a good host plan" require?  
I suppose if I have to ask, I probably don't have much help to offer. 
 But I have a website, is that what you mean.  
Bob

---

### Post by stanlea on 2011-05-30
Hi again bob

As you can read on KX site, the best way is to install first Ubuntu (I suggest Ubuntu Studio Natty last version), and then follow step by step the instructions given on the site. KXstudio is now a "rolling" distribution, so there is no more CD or DVD, it's just a bunch of PPAs on top of Ubuntu, doing what it is supposed to do.

So things are more easy.

---

### Post by falkTX on 2011-05-31
> **bobhamil said:**
> falkTX, 
What does "offer a good host plan" require?  
I suppose if I have to ask, I probably don't have much help to offer. 
 But I have a website, is that what you mean.  
Bob

A good hosting plan would need to handle high traffic and all that stuff...
(I'm not used to the internet-server world yet...)

I don't really think it's possible. Take a look at GetDeb/PlayDeb - [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)
They host a private repository (not PPAs) and I know they had some really difficulties in the past.
The total size of the PPAs is > 6Gb right now, and (I think) a lot of people use it daily.
Not sure how this can compare to GetDeb, but the point is:
Host a complete repository takes a lot of bandwidth and is not cheap at all...

---

### Post by rusk911 on 2011-06-04
can you remove pulseaudio dependency from cadence-tools?

---

### Post by falkTX on 2011-06-04
> **rusk911 said:**
> can you remove pulseaudio dependency from cadence-tools?

I guess I can tweak the code a bit and make it a recommends...

Do you hate pulseaudio that much?
You can simply disable it...

---

### Post by vervelover on 2011-07-04
On my machine, ardourvst crashes if I remove a VST while audio is still playing. This happens with EVERY vst I tried, and can be triggered every time. Using latest wineasio, latest ardour, jack2, wine 1.2 from falkTK repo (thanks for removing the wine 1.3 dependancy!) on ubuntu 10.04 lowlat kernel. It has always been like that even with previous versions of ardour/wineasio/wine, is there a way to fix this behaviour?

---

### Post by falkTX on 2011-07-04
> **vervelover said:**
> On my machine, ardourvst crashes if I remove a VST while audio is still playing. This happens with EVERY vst I tried, and can be triggered every time. Using latest wineasio, latest ardour, jack2, wine 1.2 from falkTK repo (thanks for removing the wine 1.3 dependancy!) on ubuntu 10.04 lowlat kernel. It has always been like that even with previous versions of ardour/wineasio/wine, is there a way to fix this behaviour?

Are you in 32bit or 64bit?

ArdourVST is crashy, I really recommend using wine1.3 with it.
I can try a recompile, but it probably won't change anything...

---

### Post by vervelover on 2011-07-04
I was using wine 1.3 and it was the same, but it wasn't the very latest version from your repo, which I'll try asap. Now with the latest wineasio 0.9 from git everything is a bit better though, and I found the crash doesn't really happen every time I remove a plugin, just if I put more than one on a track, and sometimes just randomly, but ardourvst has always been like that for me it's not your repo's fault don't waste time on that, just wondered if there was a fix I wasn't aware of.

Anyway, I don't remember if I already told you but thank you for your outstanding work, it's vastly thanks to it if I could build and run a professional recording studio here in Italy based on Ubuntu and Ardour, have a look:

[www.sonicstudio.it](www.sonicstudio.it)

---

### Post by falkTX on 2011-07-04
> **vervelover said:**
> I was using wine 1.3 and it was the same, but it wasn't the very latest version from your repo, which I'll try asap. Now with the latest wineasio 0.9 from git everything is a bit better though, and I found the crash doesn't really happen every time I remove a plugin, just if I put more than one on a track, and sometimes just randomly, but ardourvst has always been like that for me it's not your repo's fault don't waste time on that, just wondered if there was a fix I wasn't aware of.

Anyway, I don't remember if I already told you but thank you for your outstanding work, it's vastly thanks to it if I could build and run a professional recording studio here in Italy based on Ubuntu and Ardour, have a look:

[www.sonicstudio.it](www.sonicstudio.it)

I try to keep wine+asio updated, but busy life doesn't always allow that...
(Right now the repo is only 1 wine release behind. WineASIO is updated)

Mixing Linux and Windows app together is never a good thing.
Ardour3+VST may work better though, but since it's not even Beta I haven't cared about it yet.

I'll rebuild ArdourVST anyway, maybe the new wine1.3 brings some fixes...?


PS: If you really appreciate my work, you can always consider a donation. Go to kxstudio.sf.net, at the bottom of the page.

---

### Post by vervelover on 2011-07-04
With the latest wine 1.3 from your repo I get less crashes! I get an error when I quit the session but don't know if it's wine or wineasio, anyway I just hit close and everything is fine. Yes I know that windows software with linux is not a good thing but unfortunately it is my only choice because of a few plugins I really need and have no linux equivalent.. I'll donate to kxstudio as soon as my financial situation is a bit better, luckly it won't take too long..:guitar:

---

### Post by falkTX on 2011-07-04
> **vervelover said:**
> With the latest wine 1.3 from your repo I get less crashes!
Cool!
I've send ArdourVST to be rebuild, now without optimizations (may use more CPU but will have less crashes).
It will take some time to build though...

> **vervelover said:**
> I'll donate to kxstudio as soon as my financial situation is a bit better, luckly it won't take too long..:guitar:
No problem, I know these are not easy days and everyone has a lot of stuff to take care of.

Free software is free software.

---

### Post by danmbox on 2011-08-15
Quiet around here these days -- where has everybody gone?

Anyway, I see that the drobilla-lad package from bleeding-edge kxstudio doesn't actually contain ingen, because it doesn't get built due to missing lv2 extensions.

I've packaged the required LV2 extensions in my PPA, [https://launchpad.net/~danmbox/+archive/ppa/]("https://launchpad.net/~danmbox/+archive/ppa/") as lv2-extensions-experimental and ingen now builds and works (along with machina and the other stuff). falkTX, you may want to do something similar and build-depend on it in drobilla-lad, otherwise the package is not very useful.

---

### Post by falkTX on 2011-08-15
> **danmbox said:**
> Quiet around here these days -- where has everybody gone?

Anyway, I see that the drobilla-lad package from bleeding-edge kxstudio doesn't actually contain ingen, because it doesn't get built due to missing lv2 extensions.

I've packaged the required LV2 extensions in my PPA, [https://launchpad.net/~danmbox/+archive/ppa/]("https://launchpad.net/~danmbox/+archive/ppa/") as lv2-extensions-experimental and ingen now builds and works (along with machina and the other stuff). falkTX, you may want to do something similar and build-depend on it in drobilla-lad, otherwise the package is not very useful.

Oh, many thanks!

I was planning to do that soon, but any help is always appreciated.
I'll update it ASAP

---

### Post by OolongBrothers on 2011-08-21
Hi falkTX and the KXStudio team,

much respect for your work in the Linux Audio world. KXStudio on natty is actually the first time I got my Thinkpad R61 (with that cursed Ricoh FW controller) to work with my Focusrite Saffire LE. I have had crazy Xruns on this setup before, even on rt kernels.

Of course, I had not tried it in a while (last time somewhere around jaunty) and a lot has changed since then (new FW stack, jack2, ladish, FST). So I know it's not like the KXStudio team magically made everything work for me. But still I associate the joy over my setup working for the first time - and hence my resurrected interest in Linux Audio - with KXStudio. Furthermore I really like the KXStudio approach of not trying to be a distro, the tight integration idea and the KXStudio applications. The Linux Audio landscape is not quite the same any more since I looked last time; and it definitely made huge strides. IMHO that is mainly down to integration.

To get to the practical point of this post: Before the site overhaul, when I first installed KXStudio, I saw a Paypal donation button on the frontpage, which I wanted to come back to after installation. But then it was gone. Any plans on re-upping the Paypal thing? Or are you looking into other alternatives like Flattr donations? I'd be happy to shoot KXStudio a humble sum as appreciation for the great work.

Best regards,
oolongbrothers

---

### Post by sgx on 2011-08-21
> **falkTX said:**
> I try to keep wine+asio updated, but busy life doesn't always allow that...
(Right now the repo is only 1 wine release behind. WineASIO is updated)

Mixing Linux and Windows app together is never a good thing.
Ardour3+VST may work better though, but since it's not even Beta I haven't cared about it yet.

I'll rebuild ArdourVST anyway, maybe the new wine1.3 brings some fixes...?


PS: If you really appreciate my work, you can always consider a donation. Go to kxstudio.sf.net, at the bottom of the page.

"Mixing Linux and Windows app together is never a good thing" :confused: Perhaps you mean 'is inherently problematic'? ;)

That is the whole point of developing/using wine, wineasio, ardour-vst etc, to be able to use great and time-tested audio tools from the windows mainstream, alongside, and with the many fine linux audio tools. Until a demonstrably better solution appears, Reaper in a wine/wineasio environment is by far the best DAW one can use in a linux system. Although semantically, I consider linux to >be< a DAW
in it's own right, and Reaper one of many useful sub-components of the whole.
2012 is shaping up to be a great year for linux based musicians. The soft economy, with fierce competition among commercial vendors, means
software will be more affordable, and the new and improving linux
software and integration, will make it easily accessible. 
Full featured Ubuntu/KX Studio, AVLinux, Fedora-CCRMA, PureDyne, Studio4, and Remix-OS, (and many barebones distros) waiting to be configured as personal recording studios, means a happy future. Now
if the admins would just put up a decent 'sticky' showing how to
use jackd/qjackctl, all would be singing and dancing :)

---

### Post by falkTX on 2011-08-30
Just to give you guys the heads up - **The PPAs now support Oneiric**.

Also, I finally made the JACK1 PPA work, so you no longer have to be using JACK2 if you don't want to. Just enable 'ppa:kxstudio-team/jack1' and update.
A ppa-purge should work fine if you want to revert it (just make sure you uninstall 'jack1' meta-package first)

---

### Post by aaronLund on 2011-08-30
Dumb question time (that was probably answered elsewhere but I can't find it).....

Do they work in Natty?

---

### Post by falkTX on 2011-08-30
> **aaronLund said:**
> Dumb question time (that was probably answered elsewhere but I can't find it).....

Do they work in Natty?

Yes, the first page says clearly:
> These new PPAs support all Ubuntu versions since Lucid (ie. Lucid, Maverick, Natty and Oneiric).

If you have any issues, please do report!
It's impossible to me to test 8 setups (lucid, maverick, natty and oneiric for 32bit and 64bit), so I depend on user reports to fix broken things.
I made a cleanup recently and there should be no issues, but I'm human so...

---

### Post by stanlea on 2011-09-01
I have an issue with the very last update of Festige : vsti's don't show up and don't work (any mode).

---

### Post by falkTX on 2011-09-01
> **stanlea said:**
> I have an issue with the very last update of Festige : vsti's don't show up and don't work (any mode).

I pushed my latest changes for festige, to give users a chance to try.
heh, seems like it's not working properly (but already fixed in Git)

I'll update it ASAP, thanks for the report

---

### Post by stanlea on 2011-09-02
> **falkTX said:**
> I pushed my latest changes for festige, to give users a chance to try.
heh, seems like it's not working properly (but already fixed in Git)

I'll update it ASAP, thanks for the report


Thanks.

Another report : all bristol synths crashes in claudia. (Natty)

---

### Post by falkTX on 2011-09-03
> **stanlea said:**
> Thanks.

Another report : all bristol synths crashes in claudia. (Natty)

I'm still finishing up the last festige details, but a final version should be out later today.

regarding bristol, does it work at all? or just crashes in claudia?

---

### Post by stanlea on 2011-09-04
> **falkTX said:**
> I'm still finishing up the last festige details, but a final version should be out later today.

Thanks. Will there be a transport feature to send clock to vsti's ?

> **falkTX said:**
> regarding bristol, does it work at all? or just crashes in claudia?

Bristol works fine with monobristol started from command line, but crashes when called by claudio. A GUI problem I thonk, because a black windows opends and then disappear and then the plugin is marked inactive.

---

### Post by falkTX on 2011-09-04
> **stanlea said:**
> Thanks. Will there be a transport feature to send clock to vsti's ?
I copied code from latest Ardour3.0 SVN, and it's supposed to work (on internal fst).
I never tested it though...

Anyway, the final festige is now released, and pushed to the PPA.
You'll see an update in a few hours (launchpad is taking a long time to compile...)


> **stanlea said:**
> Bristol works fine with monobristol started from command line, but crashes when called by claudio. A GUI problem I thonk, because a black windows opends and then disappear and then the plugin is marked inactive.

Please try in "klaudia" (not claudia), to add them to a ladish studio/room.
claudia is a bit outdated now (I've been working on other things lately)

---

### Post by vervelover on 2011-09-05
festige 1.0 complains about jack not being started, but it is! 

Is there a place to pick up old packages from your repo so that if something goes wrong I can revert to the old .deb (if it's not in the cache anymore)?

---

### Post by falkTX on 2011-09-05
> **vervelover said:**
> festige 1.0 complains about jack not being started, but it is!
ah damn...
I guess the currently implementation only supports jack dbus mode only.

> **vervelover said:**
> Is there a place to pick up old packages from your repo so that if something goes wrong I can revert to the old .deb (if it's not in the cache anymore)?

just start jack using dbus methods for now (laditools, cadence, jack2-simple-config, or qjackctl with dbus enabled).

I'll remove the 'jack is started' check and release v1.0.1

---

### Post by mwinthrop on 2011-09-05
Hi - I recently downloaded and installed the KXStudio system (audio portions at this point) on a USB memory stick, which had Ubuntu Studio 11.04 installed and running.  The installation went smoothly and I have been experimenting with some of the programs.  I have been impressed with what I see so far.  I would like to complement falkTX and the KXStudio team who have created a remarkable system.  I particularly like how there are so many different pieces of software that so integrated together!

I am planning to install the PPAs onto my main computer, given my experience so far.  However, I do have one question, relating to the way fonts are being displayed (at least on my system).  I am finding the fonts are kind of difficult for me to read as compared to the defaults in Ubuntu Studio.  I find that the fonts in Firefox are particularly difficult to read, though basically is legible, but I get fatigued very quickly!  It is like the charters are very thin and some are somewhat blurry.  Is there some way for me to revert back to the original Ubuntu Studio fonts and display?  In the KXStudio welcome screen, if I don't select the "Update Theme" box, would that allow me to continue using the original Ubuntu Studio fonts and perhaps allow Firefox to be easier to see?

Being that I am so new to using Linux, I am not sure how to fix this or if I did something wrong in the installation.  I am not sure if I should remove something or adjust something.  Thanks in advanced for any suggestions.

---

### Post by falkTX on 2011-09-05
> **mwinthrop said:**
> Hi - I recently downloaded and installed the KXStudio system (audio portions at this point) on a USB memory stick, which had Ubuntu Studio 11.04 installed and running.  The installation went smoothly and I have been experimenting with some of the programs.  I have been impressed with what I see so far.  I would like to complement falkTX and the KXStudio team who have created a remarkable system.  I particularly like how there are so many different pieces of software that so integrated together!

I am planning to install the PPAs onto my main computer, given my experience so far.  However, I do have one question, relating to the way fonts are being displayed (at least on my system).  I am finding the fonts are kind of difficult for me to read as compared to the defaults in Ubuntu Studio.  I find that the fonts in Firefox are particularly difficult to read, though basically is legible, but I get fatigued very quickly!  It is like the charters are very thin and some are somewhat blurry.  Is there some way for me to revert back to the original Ubuntu Studio fonts and display?  In the KXStudio welcome screen, if I don't select the "Update Theme" box, would that allow me to continue using the original Ubuntu Studio fonts and perhaps allow Firefox to be easier to see?

Being that I am so new to using Linux, I am not sure how to fix this or if I did something wrong in the installation.  I am not sure if I should remove something or adjust something.  Thanks in advanced for any suggestions.

There's a little problem here that is that apps use different GUI toolkits, so you'll need to configure your font/theme in 3 different places.

If you're on KDE, the systemsettings provide most of the things you need, under appearance (and Gnome will follow it's settings).

For other desktops, you'll need:
'gnome-appearance-properties' for Gtk2 apps
'qt4-qtconfig' for Qt4 apps
'systemsettings' for KDE apps


The welcome screen will only change settings to kxstudio defaults, but not revert back.

---

### Post by mwinthrop on 2011-09-05
> There's a little problem here that is that apps use different GUI  toolkits, so you'll need to configure your font/theme in 3 different  places.

If you're on KDE, the systemsettings provide most of the things you  need, under appearance (and Gnome will follow it's settings).

For other desktops, you'll need:
'gnome-appearance-properties' for Gtk2 apps
'qt4-qtconfig' for Qt4 apps
'systemsettings' for KDE apps


The welcome screen will only change settings to kxstudio defaults, but not revert back.O.K. I think I have found a satisfactory to work with this.  Thanks.

---

### Post by vervelover on 2011-09-07
@falk

thanks for your reply, you're always the best! I'll test and report asap

---

### Post by vervelover on 2011-09-07
I enabled the dbus-interface in qjackctl but festige is still complaining about jack not being started..

---

### Post by falkTX on 2011-09-07
> **vervelover said:**
> I enabled the dbus-interface in qjackctl but festige is still complaining about jack not being started..

my bad, I forgot to update the PPAs for the new festige 1.0.1

update now and report back how it works.

---

### Post by vervelover on 2011-09-07
It works perfectly now even with no dbus option. Thanks!!

---

### Post by stanlea on 2011-09-07
Does anyone has success with transport in festige ? I don't.

---

### Post by falkTX on 2011-09-07
> **stanlea said:**
> Does anyone has success with transport in festige ? I don't.

Which plugin loads in festige that has time support?
(using fst, not dssi-vst)

I tried a few, but I never got the GUI to show up.
If you found one, please post and I'll see what I can do about the jack<->plugin sync.

---

### Post by stanlea on 2011-09-07
Try series from this page :

[http://www.xoxos.net/vst/vst.html#midi](http://www.xoxos.net/vst/vst.html#midi)

or

stepchild

from this one :

[http://www.gersic.com/plugins/hosted/subminimal/](http://www.gersic.com/plugins/hosted/subminimal/)

---

### Post by falkTX on 2011-09-07
> **stanlea said:**
> Try series from this page :

[http://www.xoxos.net/vst/vst.html#midi](http://www.xoxos.net/vst/vst.html#midi)

or

stepchild

from this one :

[http://www.gersic.com/plugins/hosted/subminimal/](http://www.gersic.com/plugins/hosted/subminimal/)

I noticed a few missing bits in the base fst code, so I added it from my Carla host project.
Plugins are now requesting for tempo, but I have no idea how to check if these plugins got tempo or not (gui is not very intuitive...)
I guess I should read the docs now...

I'll keep you posted about this

---

### Post by PC_load_letter on 2011-09-07
Let me just say, thank you, thank you, thank you!
For whatever the reasons were, I had a ton of problems with MIDI and the default Jack in Ubuntu Studio Lucid 32bit + wineasio. 

I added your PPAs, updated & upgraded and I'm almost problem free. I have one problem that some Windows VSTs (the free ones from [www.u-he.com](www.u-he.com)) do not show any fonts in the GUI. I noticed they are all using a custom ttf font supplied with them, I put it everywhere where Wine should be able to see and use it to no avail. This problem was not there in Feisty-Gutsy days, so it may be a new issue with Wine. 

Anyway, thanks again.

---

### Post by falkTX on 2011-09-07
> **PC_load_letter said:**
> Let me just say, thank you, thank you, thank you!
For whatever the reasons were, I had a ton of problems with MIDI and the default Jack in Ubuntu Studio Lucid 32bit + wineasio. 

I added your PPAs, updated & upgraded and I'm almost problem free. I have one problem that some Windows VSTs (the free ones from [www.u-he.com](www.u-he.com)) do not show any fonts in the GUI. I noticed they are all using a custom ttf font supplied with them, I put it everywhere where Wine should be able to see and use it to no avail. This problem was not there in Feisty-Gutsy days, so it may be a new issue with Wine. 

Anyway, thanks again.

I'm just a guy who likes music and knows a bit of programming and a bit of packaging too.
*JACK2 should be praised*

For the fonts, if they are *.ttf files, just put them in ~/.fonts and restart the app.
If they are not *.ttf, then I don't know what to do, it's probably a Wine issue.

---

### Post by mwinthrop on 2011-09-07
> I'm just a guy who likes music and knows a bit of programming and a bit of packaging too.Yes, but you do seem to do this very well!

I installed KXStudio on my main system yesterday and succeeded (many thanks for the PPAs).  I have actually installed the system twice now: once on a USB memory stick to experiment/understand the system and on my main computer.  I realized yesterday that I did have one error occur during the installation,which might be a bug, so I thought I should let you know.  My system is the 64 bit version of Ubuntu Studio 11.04 running on a Dual Core Intel Core system.

I completed the installation using the terminal window and using the approach recommended on the KXStudio web site.  The error occurred in the step where I ran the command "sudo apt-get dist-upgrade" or right at the beginning.  In both installations I seemed to have had this error and I saved all of the text that was written in the terminal.  On my USB stick, I received the following error (only copying relevant text):

Preparing to replace jackd 5 (using .../jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb) ...
Unpacking replacement jackd ...
dpkg: error processing /var/cache/apt/archives/jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb (--unpack):
 trying to overwrite '/etc/bash_completion.d/jackd', which is also in package jackd2 1.9.6~dfsg.1-5ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

----------------------------------------------------
Errors were encountered while processing:
 /var/cache/apt/archives/jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

On my main system, I received these error messages:

Preconfiguring packages ...
(Reading database ... 249819 files and directories currently installed.)
Preparing to replace jackd 5 (using .../jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb) ...
Unpacking replacement jackd ...
dpkg: error processing /var/cache/apt/archives/jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb (--unpack):
 trying to overwrite '/etc/bash_completion.d/jackd', which is also in package jackd2 1.9.6~dfsg.1-5ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

---------------------------------------------------
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/jackd_6%3a1.9.7~dfsg-1+kxstudio3~natty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was able to repair the error by running the Ubuntu Software Center, which offered to repair broken dependencies it detected.  Note the "Unknown media type in type" errors only occurred when I updated my main system.  Afterward, I was able to continue the upgrade process and my system appears to be running O.K. in KXStudio, though I have only tested a few programs so far on my newest installation.  On my USB stick installation, I have tried more programs and they always seemed to work.  Anyway, I thought I would post my experience as it appears I had the same error appear twice.

---

### Post by falkTX on 2011-09-07
@mwinthrop:
I did my best to try to avoid these kind of things, but it's not always possible...
I apologize for any inconvenience.

but anyway, a simple:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install -f
```
Will always do the trick here.

I'll see if it's possible to fix this for new users, thanks for the report!


@stanlea:
I was able to get transport working!
Please tell me your ubuntu version and architecture (32 or 64bit), and I'll post a deb for you to test :p

---

### Post by mwinthrop on 2011-09-07
> I did my best to try to avoid these kind of things, but it's not always possible...
I apologize for any inconvenience

No worries and this was not troublesome to me.  I very much like your work!

---

### Post by PC_load_letter on 2011-09-08
> **falkTX said:**
> I'm just a guy who likes music and knows a bit of programming and a bit of packaging too.
*JACK2 should be praised*

For the fonts, if they are *.ttf files, just put them in ~/.fonts and restart the app.
If they are not *.ttf, then I don't know what to do, it's probably a Wine issue.

Thanks man, I tried your suggestion to no avail, I even copied the .ttf file to /usr/share/fonts/truetype/ and restarted, nothing changed. You could try it yourself, Zebralette is one sweet sounding synth I'm almost tempted to install Windows just to be able to use it properly, here: [http://www.u-he.com/cms/Zebralette](http://www.u-he.com/cms/Zebralette)

---

### Post by stanlea on 2011-09-08
> **falkTX said:**
> 

@stanlea:
I was able to get transport working!
Please tell me your ubuntu version and architecture (32 or 64bit), and I'll post a deb for you to test :p

Cool ! Natty 64 bits.

---

### Post by falkTX on 2011-09-08
> **stanlea said:**
> Cool ! Natty 64 bits.

Too slow!
I already released festige 1.0.2 with fixed transport :guitar:

update and tell me if it works for you now

---

### Post by stanlea on 2011-09-09
Actually, it doesn't, but let me tell you the way I do : starting cadence with jack and midi, starting claudia, calling festige and yoshimi, pluging a vst with transport to yoshimi, starting transport : nothing.

---

### Post by falkTX on 2011-09-09
> **stanlea said:**
> Actually, it doesn't, but let me tell you the way I do : starting cadence with jack and midi, starting claudia, calling festige and yoshimi, pluging a vst with transport to yoshimi, starting transport : nothing.

I tested the implementation with a vst metronome plugin that displayed the tempo, and it was fine.

This will send BPM, sample postion, and time signature (4/4, 3/4, etc).
Bar/Beat is not sent, as I found no easy way to do it.

If the plugin is smart enough, that information should be enough to get it rolling.

You should not test it with catia/claudia though. Although they provide transport, there's no beat/bar and time-signature.
If you want to do a real test, please start Ardour, Hydrogen, Qtractor, or any other host that can handle jack transport properly, and then start your plugin. It should work this way.

---

### Post by stanlea on 2011-09-10
So is this correct :
- lauching cadence
- lauching Ardour (with Klaudia or from menu)
- lauching Festige -> start vst metronome
- start transport in ardour

????

---

### Post by falkTX on 2011-09-10
> **stanlea said:**
> So is this correct :
- lauching cadence
- lauching Ardour (with Klaudia or from menu)
- lauching Festige -> start vst metronome
- start transport in ardour

????

kinda, cadence and klaudia are not needed at all for this.

just start some daw with [proper] transport support, and then the VST.
transport will be sent to the vst

---

### Post by stanlea on 2011-09-11
> **falkTX said:**
> kinda, cadence and klaudia are not needed at all for this.

just start some daw with [proper] transport support, and then the VST.
transport will be sent to the vst

No way. What vst did you use for the test ? And as I told you before, I changed my settings in wine audio from jack to alsa in order to have midi in reaktor. Could this be the point ?

---

### Post by falkTX on 2011-09-11
> **stanlea said:**
> No way. What vst did you use for the test ? And as I told you before, I changed my settings in wine audio from jack to alsa in order to have midi in reaktor. Could this be the point ?

This will depend on the plugin.
I did my test with this one:
[http://www.dehaupt.com/SynthEdit/DH_Metronome.htm](http://www.dehaupt.com/SynthEdit/DH_Metronome.htm)

basically, if the plugin _requires_ bar/beat information, it will not work.

the implementation sends BPM, sample position and time signature, but not bar/beats (VST complicates this a bit).

some plugins can work fine without bar/beat info, others don't.

---

### Post by mwinthrop on 2011-09-11
Hi - I am experimenting with Rosegarden and am having trouble.  Specifically, I have tried a very simple case of importing a midi file and then saving the file as a Rosegarden file.  When I close Rosegarden, reopen it, and then try to reload the Rosegarden file I just saved, Rosegarden reads the file and then closes.  I have tried different midi files and nothing seems to work.  I thought there might be something set wrong, so I reran the KXStudio welcome and reset everything.  However, this did not fix the problem.  I can't figure out if this is a bug with Rosegarden, something related to KXStudio, or maybe something odd about my computer.  Rosegarden itself seems to run as long as I don't save and try to reload my work.

I am running the AMD64 bit version of KXStudio on Ubuntu Studio 11.04.  Any ideas of what could be wrong?

---

### Post by falkTX on 2011-09-11
> **mwinthrop said:**
> Hi - I am experimenting with Rosegarden and am having trouble.  Specifically, I have tried a very simple case of importing a midi file and then saving the file as a Rosegarden file.  When I close Rosegarden, reopen it, and then try to reload the Rosegarden file I just saved, Rosegarden reads the file and then closes.  I have tried different midi files and nothing seems to work.  I thought there might be something set wrong, so I reran the KXStudio welcome and reset everything.  However, this did not fix the problem.  I can't figure out if this is a bug with Rosegarden, something related to KXStudio, or maybe something odd about my computer.  Rosegarden itself seems to run as long as I don't save and try to reload my work.

I am running the AMD64 bit version of KXStudio on Ubuntu Studio 11.04.  Any ideas of what could be wrong?

I just tested it on Ubuntu 11.10, save&load works fine.

please run "rosegarden" in a terminal, make it crash, and look for any suspicious messages in the terminal.
do you have any experience in debugging?

---

### Post by mwinthrop on 2011-09-11
I do have some experience with debugging, though I have only started using Linux in the last couple months, so I am still learning about it.

I have just performed some tests that are providing some odd behavior.  I previously installed KXStudio on a memory stick (USB Installation), so I fired up Rosegarden there.  Unlike the installation (Main Installation) on my hard disk, I am able to create, save, and reload the Rosegarden file from a midi file.  I also determined I could load the Rosegarden file I saved from the installation that is not working.

Next, I went back to my main installation and found I could load the save created by  the USB Installation.  Next, I loaded the main Installation save and it worked, which was strange.  Next I closed Rosegarden and tried loading Main Installation and sometimes I can load it and sometimes I can't.  Here is the error I received from the terminal window (just showing the last few lines of lots of terminal output):

[generic]  CompositionModelImpl::computeSegmentRect: x  0 , y  289  startTime  0 , endTime  15 , w  0 , h  22 

[generic]  CompositionModelImpl::computeSegmentRect: x  0 , y  313  startTime  0 , endTime  15 , w  0 , h  22 

[generic]  CompositionModelImpl::computeSegmentRect: x  0 , y  337  startTime  0 , endTime  15 , w  0 , h  22 

[generic]  CompositionModelImpl::computeSegmentRect: x  0 , y  361  startTime  0 , endTime  15 , w  0 , h  22 

[generic]  drawRect: rect is  QRect(0,1 32487x21) 

Segmentation fault

So I think there is something different between my USB Installation and my Main Installation, but don't see what it is yet.  The USB Installation was more clean than the Main Installation when I installed KXStudio.  I thought there might be a graphics card issue, but both installations are using the same graphics driver.  I think I have definitely proven to myself that there is something odd going on with my computer . . .

---

### Post by falkTX on 2011-09-11
Those messages are not errors, the app just crashes (segmentation fault).

You must have a different set-up between your systems (different Ubuntu versions or architecture?)
Please give me details about the crashy system (OS, arch, HW, etc)

rosegarden is probably built without debug information, but we can try anyway:
```
gdb rosegarden
# press 'r' to start the app and force a crash
# press 'bt'

```

Post here the output please.

---

### Post by mwinthrop on 2011-09-11
Sorry if my emails were confusing. Here are more details:

The hardware for my computer is a Dell 1555 with a 500GB hard drive, which I am dual booting Ubuntu Studio 11.04 and Windows 7. The graphics card is an ATI Mobility Radeon HD 4500 Series and I am using the ATI Linux proprietary drivers. I am running Ubuntu Studio 11.04 and experimented with it for a month or two before I installed KXStudio on it. I am calling this my Main Installation and this is the system where Rosegarden is crashing.

The USB Installation is a 16 Gig memory stick where I have installed Ubuntu Studio 11.04 and KXStudio. I am able to boot the USB stick using my Dell 1555, so the hardware is all the same except for where I am booting from. I am also running the same ATI proprietary driver. In theory, the software should all be the same as what is on my hard drive, but something appears to be different between the two setups. When I boot from the memory stick, Rosegarden seems to be able to save and load information without trouble.

I ran the commands you requested (see attachment). It would appear that Rosegarden is intermittent on my "Main System." I can sometimes load the saved files and sometimes not.

Note: I attached a text file to this post because the message editor for the forum kept changing parts of my message to various "Smilies" faces!

---

### Post by mwinthrop on 2011-09-11
I have continued experimenting with Rosegarden and strangely, it seems to be working again.  Specifically, files that I had saved before can now be loaded.  One thing I noticed was Rosegarden was reporting my graphics was running in safe mode.  I uninstalled and reinstalled my graphics drivers.  Also, I set Rosegarden graphics to safe mode, restarted Rosegarden, and then set it to fast mode in the preferences.  After restarting Rosegarden, it stopped telling me it was running in graphics safe mode.  I think that may have helped, but I am not sure of that.  At any rate, my test of saving a midi file and loading it seemed to work more often then it did and now does not seem to be failing.  Further, a Rosegarden piano concerto file I created from an imported MIDI that I could not load at all I can now load.

The only other thing I can think of is I was attempting yesterday to connect Rosegarden to Linuxsampler and Pianoteq to play the piano concerto instruments.  I was making connections through Claudia and was not sure if I should connect using Jack MIDI or ALSA MIDI, so I tried different ways of making the connections and also was making changes in Linuxsampler and Pianoteq.  I read somewhere in Rosegarden documentation that I should make connections via Rosegarden rather than using an external connector (i.e. Jack or maybe Claudia) and was trying that after I tried some of the other ways.  I wonder if I unraveled something and slowly managed to bring it back (no idea how)?  I am making connections now using Rosegarden's MIDI connectors and am not trying any of the other methods, which might have improved things.  I also had to set Pianoteq to only listen to one MIDI input, which is a2jmidid, rather than listening to all midi inputs (i.e. midi through and multiple Rosegarden outputs).

If this problem comes back (maybe I just have wishful thinking that it is gone), I will post again.

---

### Post by stanlea on 2011-09-13
Hi again

Given our last posts, could you tell us what is actually the best combination for KXstudio.

I tried Klaudia but it sends nothing to gladish. So, should I stay with Cadence or try another way of starting jack? I'm a bit confused now. How do you do it yourself ?

---

### Post by falkTX on 2011-09-13
> **stanlea said:**
> Hi again

Given our last posts, could you tell us what is actually the best combination for KXstudio.

I tried Klaudia but it sends nothing to gladish. So, should I stay with Cadence or try another way of starting jack? I'm a bit confused now. How do you do it yourself ?

Cadence, when installed, auto-starts JACK at login by default.

I usually configure JACK with cadence, or using 'jack_settings' directly.
After all being set, my trick is:
```
cadence-session-start -s
```
Which will force all audio stuff to stop, and start JACK again (this is the command that candence uses for starting JACK on login).

Klaudia has a small bug that prevents ladish usage on some setups, a fix will come soon.

---

### Post by vervelover on 2011-09-15
Just randomly testing fst and dssi-vst, I discovered fst is strangely not able to handle any vst plugin that is based on the juced (or jost) platform, while dssi-vst can do that. I'm talking about any Loomer plugins in their win exe version, or even the free hybridreverb plugin in the win exe format. 

ArdourVST can't handle those plugins as well, only dssi-vst seems to be able to do it.

Also, I tried to test Klaudia, but it complains about Jack not being started just like fst did before the latest update.

Just some bug reporting here :guitar:

---

### Post by mwinthrop on 2011-09-19
Rosegarden continues to be working for me - my save/load problem has gone away - just thought I would report this.  On another note, I own an old copy of Garritan Personal Orchestra (GPO version 3 I think) which uses Kontact Player version 2.  I installed it under Wine with no trouble.  I can run GPO in Wine from your repository, but I only get one volume level (very loud and a buzzing sound!) so something is not quite right there.  Fortunately, FeSTige does not have this issue and seems to run GPO nicely, so I don' need to run directly in Wine.  I have no idea if the newest version of GPO would work, but the old one does.  I would like to complement you,  falkTX, on FeSTige and let you know of this success.  Thank you very much for the work you have done.

---

### Post by stanlea on 2011-09-20
Another strange thing : transport doesn't work in Hydrogen (KX repos). I get sound while programming the patterns, but no way to loop it. Composite works.

---

### Post by falkTX on 2011-09-20
> **stanlea said:**
> Another strange thing : transport doesn't work in Hydrogen (KX repos). I get sound while programming the patterns, but no way to loop it. Composite works.

One thing I noticed about Hydrogen is that we need to specifically set audio driver to JACK in order to see the "tranport slave/master" button led.
So, try setting your driver to JACK and restart Hydrogen.

Composite is JACK only, so it works by default.

---

### Post by falkTX on 2011-09-20
> **mwinthrop said:**
> Rosegarden continues to be working for me - my save/load problem has gone away - just thought I would report this.  On another note, I own an old copy of Garritan Personal Orchestra (GPO version 3 I think) which uses Kontact Player version 2.  I installed it under Wine with no trouble.  I can run GPO in Wine from your repository, but I only get one volume level (very loud and a buzzing sound!) so something is not quite right there.  Fortunately, FeSTige does not have this issue and seems to run GPO nicely, so I don' need to run directly in Wine.  I have no idea if the newest version of GPO would work, but the old one does.  I would like to complement you,  falkTX, on FeSTige and let you know of this success.  Thank you very much for the work you have done.

I think we should really consider Wine as just a step to help our transition to Linux, and not a solution.
Wine stuff can break at anytime (although I'm not gonna update Wine anymore, sticked at 1.3.24 for the JACK audio).

No denying that it's great when it works though...

---

### Post by stanlea on 2011-09-20
> **falkTX said:**
> One thing I noticed about Hydrogen is that we need to specifically set audio driver to JACK in order to see the "tranport slave/master" button led.
So, try setting your driver to JACK and restart Hydrogen.

Composite is JACK only, so it works by default.

Nope, Hydrogen is set to jack of course, and that little black triangle on the top of the pattern doesn't move. I tried jack transport, hydrogen transport, various combinations, no way.

---

### Post by falkTX on 2011-09-20
> **stanlea said:**
> Nope, Hydrogen is set to jack of course, and that little black triangle on the top of the pattern doesn't move. I tried jack transport, hydrogen transport, various combinations, no way.

report a bug to the hydrogen devs then ;)

---

### Post by mwinthrop on 2011-09-20
> **falkTX said:**
> I think we should really consider Wine as just a step to help our transition to Linux, and not a solution.
Wine stuff can break at anytime (although I'm not gonna update Wine anymore, sticked at 1.3.24 for the JACK audio).

No denying that it's great when it works though...

Agreed that Wine is not a general solution.  I would prefer to use Linux native programs.  The only orchestra library I have found that Linux can use directly via Linuxsampler is Sonatina Symphonic Orchestra (SSO), which I am also looking at.   Incidentally, it was my desire to try out Linuxsampler that led me to your repositories in the first place.  I don't plan to go out and get Windows programs hoping they will work in Wine, but in this case I happen to have one that does work, so I might as well go ahead and use it.  Will have to keep in mind it might not always work in the future.

---

### Post by falkTX on 2011-09-26
I just updated 'klaudia' to handle non-jackdbus setups, and also some other small fixes.
can someone (that previously klaudia wasn't working on) test the update?

thanks!

---

### Post by stanlea on 2011-09-27
I updated, but I use jack or all, and I had no specific bugs; since last build, Klaudia sended correctly the apps to ladish.

---

### Post by jsevi83 on 2011-10-17
I installed fmit for Oneiric and it's not showing up in Unity applications. I checked and the .desktop file is in /usr/share/mimelnk/application, instead of the usual /usr/share/applications. Is there any chance to have it changed?

---

### Post by falkTX on 2011-10-17
> **jsevi83 said:**
> I installed fmit for Oneiric and it's not showing up in Unity applications. I checked and the .desktop file is in /usr/share/mimelnk/application, instead of the usual /usr/share/applications. Is there any chance to have it changed?

no, the source package for fmit (in kxstudio ppas) is the same from lucid to oneiric.
what were you using before?

---

### Post by jsevi83 on 2011-10-18
I was using fmit 0.97 from the official repositories. In that package the .desktop file was in /usr/share/applications. I don't know if it's a problem with Unity, but fmit doesn't show in my applications Unity lense.

---

### Post by falkTX on 2011-10-18
> **jsevi83 said:**
> I was using fmit 0.97 from the official repositories. In that package the .desktop file was in /usr/share/applications. I don't know if it's a problem with Unity, but fmit doesn't show in my applications Unity lense.

then this is probably a change in upstream's tarball.

a simple:
```
sudo cp /usr/share/mimelnk/application/fmit.desktop /usr/share/applications
```
will solve it for you

---

### Post by jsevi83 on 2011-10-18
Alright, thank you. I was also trying to update qsampler to 0.2.2.30 (I believe it's revision 2277), but wasn't successful building the package. I also think linuxsampler 1.0 revision 2277 has some improvements in the use of SFZ soundfonts. Maybe if you have time you could update them.

---

### Post by falkTX on 2011-10-18
> **jsevi83 said:**
> Alright, thank you. I was also trying to update qsampler to 0.2.2.30 (I believe it's revision 2277), but wasn't successful building the package. I also think linuxsampler 1.0 revision 2277 has some improvements in the use of SFZ soundfonts. Maybe if you have time you could update them.

Sure, I'll do that soon.

I'm running Arch now, so I need to prepare the chroots first.
But it should be all set later today.

---

### Post by stanlea on 2011-10-19
> **falkTX said:**
> Sure, I'll do that soon.

I'm running Arch now, so I need to prepare the chroots first.
But it should be all set later today.

Thanks, falkTX. Will you tell us how good is Arch with KStudio ? I'd switch if I was sure I could (after a correct installation, of course) have a working DAW like the one I have based on Ubuntu 10.04. 

Cheers

Stanlea

---

### Post by falkTX on 2011-10-19
> **stanlea said:**
> Thanks, falkTX. Will you tell us how good is Arch with KStudio ? I'd switch if I was sure I could (after a correct installation, of course) have a working DAW like the one I have based on Ubuntu 10.04. 

Cheers

Stanlea

You can already do _everything_ in Arch without KXStudio.
My KXStudio work on Arch will just be a repository, and make the apps work nicely there (/etc/rc.d/ changes, and some other misc stuff)

I recommend to first install it on a VM for testing.

---

### Post by jsevi83 on 2011-10-26
I think Ardour 3.0 alpha 10 was released on the 17th of August, so it's more than two months now. Since then Ardour got native linux VST plugin support, and many bugfixes. Do you think you could update it in your "latest ppa", or you prefer to wait for the beta release?

---

### Post by falkTX on 2011-10-26
> **jsevi83 said:**
> I think Ardour 3.0 alpha 10 was released on the 17th of August, so it's more than two months now. Since then Ardour got native linux VST plugin support, and many bugfixes. Do you think you could update it in your "latest ppa", or you prefer to wait for the beta release?

Neither I or Ardour devs want people using this development version "just to try it".
You should only use it if you plan to debug and report bugs.
The version I put in the (Latest) PPA is the raw Ardour alpha10 debug tarball build, just adapted to be a DEB.

That being said, wait for the beta, or maybe Alpha11.

---

### Post by jsevi83 on 2011-10-26
Ok, I don't want "just to try it", I just want to use it. I've been using the alphas since the beginning, with good results. I just thought the current development version is more stable than alpha 10, but it's true you need to compile it instead of copying the tarball build.

I don't think I should only use it to debug, there are lots of users who prefer a "quite stable alpha" than a "quite unstable release". Why don't you want people to use it unless it's for debugging? Didn't you compile Ardour 3 even before the alphas were released?

---

### Post by falkTX on 2011-10-26
> **jsevi83 said:**
> Ok, I don't want "just to try it", I just want to use it. I've been using the alphas since the beginning, with good results. I just thought the current development version is more stable than alpha 10, but it's true you need to compile it instead of copying the tarball build.

I don't think I should only use it to debug, there are lots of users who prefer a "quite stable alpha" than a "quite unstable release". Why don't you want people to use it unless it's for debugging? Didn't you compile Ardour 3 even before the alphas were released?

I'm just trying to avoid wars with the Ardour devs.

Paul Davids words follow:
> No Linux distribution should be packaging Ardour3 at this time.
(...)
we have not asked (and are not asking) for people not comfortable with
debuggers and other tracing tools to be using ardour3 at this time.

> i'm angry because i've said all the way through ardour3 development
that packaging of any kind doesn't make any sense. i'm upset that
someone would give users a 2nd-rate experience by making them think
that they had received an "important" version of ardour3 rather than
just another svn commit that will be out of date in a few hours.

I hope you get the point, I'm just trying to avoid any problems.
The versions in the PPAs (until not RC) will be always the exact copy of the official tarballs.

---

### Post by jsevi83 on 2011-10-26
Sure, I get the point, better not to have wars with the Ardour devs :D
I don't mean to disappoint Paul, I respect his opinion, but I think some svn ppa are very useful and performing better than stable released versions. Since I'm not using Ardour2 for quite a while (I need midi support), I will find a way to install Ardour3 from svn, as it's surely better (and less outdated) than the alpha10. Thanks for your time and explanations anyway.

---

### Post by falkTX on 2011-10-27
> **jsevi83 said:**
> Sure, I get the point, better not to have wars with the Ardour devs :D
I don't mean to disappoint Paul, I respect his opinion, but I think some svn ppa are very useful and performing better than stable released versions. Since I'm not using Ardour2 for quite a while (I need midi support), I will find a way to install Ardour3 from svn, as it's surely better (and less outdated) than the alpha10. Thanks for your time and explanations anyway.

The ardour page has info about compiling:
[http://ardour.org/building_ardour3](http://ardour.org/building_ardour3)

To install all dependencies, run:
```
sudo apt-get build-dep ardour2 # Get basic dependencies
sudo apt-get install liblilv-dev libsuil-dev # Get new LV2 libs

```

This is the way to go, but please don't share any pre-compiled binaries or build scripts.

---

### Post by jsevi83 on 2011-10-27
Thanks a lot, and don't worry, I won't share it. Do you know if I need Steinberg vst headers to build Ardour with native linux vst support?

---

### Post by falkTX on 2011-10-27
> **jsevi83 said:**
> Do you know if I need Steinberg vst headers to build Ardour with native linux vst support?

Not needed, the vestige header takes care of it nicely for now

---

### Post by caj.nordstrom@pp.nic.fi on 2011-10-27
I have an 64 bit oneiric 11.10 ubuntu system with kxstudio add ons.
I would like to use the ardourvst-32bit package, but it seems to be broken at the moment for Oneiric. Is this the situation or have I understood something wrong? Are there any chances that it will be corrected in the near future?

---

### Post by falkTX on 2011-10-27
> **caj.nordstrom@pp.nic.fi said:**
> I have an 64 bit oneiric 11.10 ubuntu system with kxstudio add ons.
I would like to use the ardourvst-32bit package, but it seems to be broken at the moment for Oneiric. Is this the situation or have I understood something wrong? Are there any chances that it will be corrected in the near future?

I didn't care too much about ArdourVST because it's mostly unusable with common VSTs.
It's a hell to get this working on 64bit too...

So, ArdourVST is no longer available on Oneiric (Lucid has 32bit+64bit, Maverick and Natty have 32bit only, Oneiric has none).

You can use FeSTige and leave Ardour stable (no more Wine deps).
Is this something really important?

---

### Post by sgx on 2011-10-28
> **caj.nordstrom@pp.nic.fi said:**
> I have an 64 bit oneiric 11.10 ubuntu system with kxstudio add ons.
I would like to use the ardourvst-32bit package, but it seems to be broken at the moment for Oneiric. Is this the situation or have I understood something wrong? Are there any chances that it will be corrected in the near future?What type vst do you want to use?
Synth, ampsim?, fx? I can test some free ones using fst if I have a clue. Cheers

---

### Post by caj.nordstrom@pp.nic.fi on 2011-10-28
> **sgx said:**
> What type vst do you want to use?
Synth, ampsim?, fx? I can test some free ones using fst if I have a clue. Cheers

I has looked for a good native reverb that can be used directly as an Ardour plugin, but in my opinion the ones I have found are not good at least for acoustic music. They don't sound natural. Do you know about good ones?
According to my first test Ambience vst plugin sounds much better and the setup is much more easy to manage if you can handle all the effects from one application.

---

### Post by falkTX on 2011-10-28
> **caj.nordstrom@pp.nic.fi said:**
> I has looked for a good native reverb that can be used directly as an Ardour plugin, but in my opinion the ones I have found are not good at least for acoustic music. They don't sound natural. Do you know about good ones?
According to my first test Ambience vst plugin sounds much better and the setup is much more easy to manage if you can handle all the effects from one application.

You should really try the maximum linux native plugins first, instead of going to Wine/Windows solutions.

Have you tried the latest Calf? (calf-plugins-git package)
One great reverb plugin is IR.lv2, just get some nice IR files and use them with it.

---

### Post by sgx on 2011-10-28
> **caj.nordstrom@pp.nic.fi said:**
> I has looked for a good native reverb that can be used directly as an Ardour plugin, but in my opinion the ones I have found are not good at least for acoustic music. They don't sound natural. Do you know about good ones?
According to my first test Ambience vst plugin sounds much better and the setup is much more easy to manage if you can handle all the effects from one application.
Hi, I checked some reverbs tonight, (but not Ambience) using guitar in a qtractor audio track, or just lv2 and jack-rack on a guitar audio input in qjackctl. Results are subjective, not conclusive :)

Calf reverb was the best sounding to me, and had many configuration options, in a great gui.

Invada early-reflelection had nice room sizing and positioning,
but sounded a bit thinner than Calf, perhaps due to operator skillset?
Someone knowing a specific room/sound to pursue, might do far better.

guitarix freeverb was also good, but with few options.

The TAP reverberator had lots of options, and reverb types, but I ran out of steam. Will have to discover if the reverb 'types', are more
than just presets.

The most beautiful reverb I have heard, is Cavernous, from the
free version of Line6 Podfarm

My favorite windows reverbs are from TAL, and those are now ported to
linux. So I must find a way to use them, qtractor, lv2 rack, jack-rack did not find them, perhaps a qtractor/ardour stable version
with compiled vst support is needed. They sound quite different from Calf, but I will keep them in use.

For lack of better words, Calf seems like a space, the others like
a sound within a space.

Tried the IR lv2, and with many IR .wavs, it had a very pleasing
accoustic presence. Definitely a keeper. Must-not-horde-IRs
:popcorn:

---

### Post by falkTX on 2011-10-28
Qtractor can load VSTs just fine (if you're using the kx PPAs, you get everything pre-compiled).

I'm working on LV2 versions at the moment, and it should not take too long.
(I'll be also releasing my own plugins using the same toolkit as TAL, ie Juce)

---

### Post by sgx on 2011-10-28
Thanks for your work on the TAL synths and plugins! I think I used
a sid repo to install qtracktor, so I'll replace it with the one from KX this weekend:popcorn:

---

### Post by stanlea on 2011-10-29
> **falkTX said:**
> Qtractor can load VSTs just fine (if you're using the kx PPAs, you get everything pre-compiled).

I'm working on LV2 versions at the moment, and it should not take too long.
(I'll be also releasing my own plugins using the same toolkit as TAL, ie Juce)

Your own plugins ? Seems a good new. :guitar:

---

### Post by wbm on 2011-10-29
Hi, maybe I can ask this here.
My new computer will arrive in three days.
What should I install for audio recording?

Ubuntu 11.10 plus KXStudio? 

Ubuntu Studio 11.10 (if that is even final)?

Dream Studio 11.04?

Should I go 32 or 64 bit? It's a new machine with 8Gb of Ram.

How about the kernel for audio. As far as I can tell there is no real time or low latency kernel for any 11.10 distributions yet.

Falk, I tried Arch and failed miserably. I think I'd rather stick with some Ubuntu flavor.
Thanks!

---

### Post by jsevi83 on 2011-11-01
Hi, I was trying linuxsampler from your ppa, and it asks to install jackd (actually, a different version that the one I have installed). As linuxsampler can work both with alsa and jackd, I think jackd should not be a dependency, but a recommended package.

On the other hand, I found a nice utility (probably you already know it) called playitslowly. I don't know if it fits in your ppa...

---

### Post by sgx on 2011-11-01
> **wbm said:**
> Hi, maybe I can ask this here.
My new computer will arrive in three days.
What should I install for audio recording?

Ubuntu 11.10 plus KXStudio? 

Ubuntu Studio 11.10 (if that is even final)?

Dream Studio 11.04?

Should I go 32 or 64 bit? It's a new machine with 8Gb of Ram.

How about the kernel for audio. As far as I can tell there is no real time or low latency kernel for any 11.10 distributions yet.

Falk, I tried Arch and failed miserably. I think I'd rather stick with some Ubuntu flavor.
Thanks!Hi, I would google your soundcard/chip with
the various linux audio versions, and look for signs of success.
Then do the search with various kernels. When a linux version and kernel both have positive feedback, you're in the honey tree. :D
Cheers

---

### Post by falkTX on 2011-11-12
> **jsevi83 said:**
> Hi, I was trying linuxsampler from your ppa, and it asks to install jackd (actually, a different version that the one I have installed). As linuxsampler can work both with alsa and jackd, I think jackd should not be a dependency, but a recommended package.

On the other hand, I found a nice utility (probably you already know it) called playitslowly. I don't know if it fits in your ppa...

afaik, jackd is a recommends, not a dependency. can you try:
```
sudo apt-get install --no-install-recommends linuxsampler
```

Please note though:
 - Using these PPAs, JACK will be upgraded *always* to JACK2. It's the version I use and fully support (1.9.7 + custom patches). It doesn't matter if you install jackd1 or whatever; in these PPAs, JACK2 will *always* be used.
 - If you want JACK1, enable the JACK1 PPA and update. This will make JACK *always* be JACK1, even if you install jackd2.

I think that was clear already, if not, there you go.
This PPA approach I believe it's the best possible. The current Debian way of handling JACK (jackd1 and jackd2) is confusing and leads to trouble in some cases, specially for commercial apps and Wine.
My way forces JACK2, but still makes JACK1 installable at the same time, without any package conflicts.

---

### Post by jrisreal on 2011-11-13
ohmigoodness!  thanks man!

---

### Post by mwinthrop on 2011-11-16
Hi - This is not a critical thing, but I was recently playing around with the various Juced programs that are part of KXStudio and found that none of these programs could find my sound card.  When I go to the options for any of the different programs and select "audio settings", I can choose either ALSA or JACK.  If I choose JACK, there are no outputs to select (i.e. only the none option is available).  If I select ALSA, I can select one sound card, but it is not the right one (i.e. my computer has 2 sound cards, but I can only select the one I don't use).  All other sound programs related to KXStudio do not have any trouble like this, so I am guessing there is something incorrect in a configuration file related to Juced programs.  I wanted to play around with HybridReverb2, also, which has the same issue (maybe this is a Juced based program, too).  I am not sure where to look or what I would do to correct the problem if I knew where to look, so I thought I would ask for help.  Thanks in advance and if I have not said so lately, I continue to enjoy using KXStudio capabilities.

---

### Post by falkTX on 2011-11-16
> **mwinthrop said:**
> Hi - This is not a critical thing, but I was recently playing around with the various Juced programs that are part of KXStudio and found that none of these programs could find my sound card.  When I go to the options for any of the different programs and select "audio settings", I can choose either ALSA or JACK.  If I choose JACK, there are no outputs to select (i.e. only the none option is available).  If I select ALSA, I can select one sound card, but it is not the right one (i.e. my computer has 2 sound cards, but I can only select the one I don't use).  All other sound programs related to KXStudio do not have any trouble like this, so I am guessing there is something incorrect in a configuration file related to Juced programs.  I wanted to play around with HybridReverb2, also, which has the same issue (maybe this is a Juced based program, too).  I am not sure where to look or what I would do to correct the problem if I knew where to look, so I thought I would ask for help.  Thanks in advance and if I have not said so lately, I continue to enjoy using KXStudio capabilities.

This is a strange behaviour. I assume you have JACK started and fully working, correct?

Please give me system details (os, arch, which repos you're using and basic HW too).
And what do you use to start JACK? Cadence (ie, jackdbus), QJackCtl (for jackd), or other?

thanks

---

### Post by mwinthrop on 2011-11-16
Yes - I have Jack working without trouble and set up for my machine to give me reasonable xrun free latency when using my MIDI keyboard.  My computer is running the 64 bit version of Ubuntu 11.04.  My computer is a Dell 1555 Studio laptop.  I have the Dell supplied internal sound card (which is what I normally use) and one associated with my ATI graphics card, which is the one I don't use (have never tried it and never needed it).  The graphics card is using the ATI supplied Linux driver and it works fine at least for displaying graphics.  Alsa recognizes both sound cards from what I can see (observed in Gnome ALSA Mixer).  I let Cadence start up Jack and it runs fine.  I use Cadence and Catia as my primary tools.  My primary instrument is Pianoteq and this program runs with no trouble using Jack.  I let Cadence start JACK and A2J Midi Bridge.  I have Pulse-Jack turned off (I don't seem to need it for the programs I run), though this program runs without complaint  when I turn it on.  Cadence seems to run without any problems.  I use Klaudia to start most KXStudio programs.  I have verified that programs such as Yoshimi and  ZynAddSubFX work without trouble.  Other programs such as Flash video, VLC, etc. all work as expected.

Edit - Guess I should add I am using most of the KXStudio repos and the Ubuntu standard repos, so I don't think there is anything unusual going on there.

---

### Post by falkTX on 2011-11-19
> **mwinthrop said:**
> Yes - I have Jack working without trouble and set up for my machine to give me reasonable xrun free latency when using my MIDI keyboard.  My computer is running the 64 bit version of Ubuntu 11.04.  My computer is a Dell 1555 Studio laptop.  I have the Dell supplied internal sound card (which is what I normally use) and one associated with my ATI graphics card, which is the one I don't use (have never tried it and never needed it).  The graphics card is using the ATI supplied Linux driver and it works fine at least for displaying graphics.  Alsa recognizes both sound cards from what I can see (observed in Gnome ALSA Mixer).  I let Cadence start up Jack and it runs fine.  I use Cadence and Catia as my primary tools.  My primary instrument is Pianoteq and this program runs with no trouble using Jack.  I let Cadence start JACK and A2J Midi Bridge.  I have Pulse-Jack turned off (I don't seem to need it for the programs I run), though this program runs without complaint  when I turn it on.  Cadence seems to run without any problems.  I use Klaudia to start most KXStudio programs.  I have verified that programs such as Yoshimi and  ZynAddSubFX work without trouble.  Other programs such as Flash video, VLC, etc. all work as expected.

Edit - Guess I should add I am using most of the KXStudio repos and the Ubuntu standard repos, so I don't think there is anything unusual going on there.

Pianoteq, Loomer and Renoise are also Juce based applications.
Do these work on your system?

---

### Post by mwinthrop on 2011-11-19
Yes, Pianoteq does work and this is a program I have purchased.  I don't have Loomer or Reaper on my computer, and I have never tried these.  Is it worth me trying to download these programs (demo versions)?  I probably won't use these programs normally, but if it helps, I could try them.  

I have Pianoteq installed separately from the KXStudio installation.  Basically, I downloaded the 64 bit linux version, placed it in a directory and run it directly using a "Launcher".  Not sure if that is the best way to install it, but it works.

Here are programs that do not allow me to select my soundcard using the audio settings:

JOST
Highlife
Nekobee
Peggy2000
Vex
BitMangler
EQinox
HybridReverb2

The audio settings in the programs do allow me to see midi ports and I can select these.  When I select an active midi input (i.e. a2jmidid or Midi Through for example in HybridReverb2), then a HybridReverb2 box will appear in Catia, which allows me to connect the program to other midi ports, though I cannot tell if the connections work.  The port is green, which I think means ALSA is being used.  If I don't have a midi box checked, then the program will disappear from Catia.  I assume this is because the program does not have any available ports, including any sound related ports, so Catia has nothing to show.  The one soundcard option I can choose with ALSA (HDA ATI HDMI), which is the soundcard I don't use, does not result in anything being displayed in Catia.  However, the DSP Load jumps around quite a bit, which leads me to believe HybridReverb2 is processing something.  When I switch my soundcard option to none, the DSP Load drops down to 2-3% load.

Other programs I try do not behave this way, though I have not tried all of the programs in the KXStudio suite (there are a lot of them!).  However, everything I have tried has worked.  For example, the Bristol programs seem to work without trouble.

I also have Ubuntu 11.04 and KXStudio installed on a 16 GB bootable thumbdrive.  I booted my computer from the thumbdrive and experienced the same behavior.  I wonder if I am doing something wrong with these programs?

---

### Post by falkTX on 2011-11-22
> **mwinthrop said:**
> Yes, Pianoteq does work and this is a program I have purchased.  I don't have Loomer or Reaper on my computer, and I have never tried these.  Is it worth me trying to download these programs (demo versions)?  I probably won't use these programs normally, but if it helps, I could try them.  

I have Pianoteq installed separately from the KXStudio installation.  Basically, I downloaded the 64 bit linux version, placed it in a directory and run it directly using a "Launcher".  Not sure if that is the best way to install it, but it works.

Here are programs that do not allow me to select my soundcard using the audio settings:

JOST
Highlife
Nekobee
Peggy2000
Vex
BitMangler
EQinox
HybridReverb2

The audio settings in the programs do allow me to see midi ports and I can select these.  When I select an active midi input (i.e. a2jmidid or Midi Through for example in HybridReverb2), then a HybridReverb2 box will appear in Catia, which allows me to connect the program to other midi ports, though I cannot tell if the connections work.  The port is green, which I think means ALSA is being used.  If I don't have a midi box checked, then the program will disappear from Catia.  I assume this is because the program does not have any available ports, including any sound related ports, so Catia has nothing to show.  The one soundcard option I can choose with ALSA (HDA ATI HDMI), which is the soundcard I don't use, does not result in anything being displayed in Catia.  However, the DSP Load jumps around quite a bit, which leads me to believe HybridReverb2 is processing something.  When I switch my soundcard option to none, the DSP Load drops down to 2-3% load.

Other programs I try do not behave this way, though I have not tried all of the programs in the KXStudio suite (there are a lot of them!).  However, everything I have tried has worked.  For example, the Bristol programs seem to work without trouble.

I also have Ubuntu 11.04 and KXStudio installed on a 16 GB bootable thumbdrive.  I booted my computer from the thumbdrive and experienced the same behavior.  I wonder if I am doing something wrong with these programs?

In Juce-based plugins, ALSA MIDI only show it's ports when you connect something from it's GUI. You can use/connect-to the midi-through port to make it visible, then do the connections.

Please try Renoise and some Loomer plugins, since they are also Juce based. I need to know if this is only fixed in Pianoteq or not.

---

### Post by mwinthrop on 2011-11-22
O.K. - I tried the demos for Renoise and Loomer String.  Both of these  programs seem to work.  They both automatically connected to the system  playback ports.  I ran Renoise and it did a fairly long search for plug  ins and then crashed.  I reran the program and it went through the  search again and then it ran O.K.  I was able to play 3 different demo  songs, successfully.  I ran Loomer String and created a midi port by  checking "midi-through" in the audio options.  I connected Jack-Keyboard  to the midi in port and was able to play sounds.

There is a  definite difference between Loomer String and the other programs.   Loomer String puts a box into Catia with 4 inputs and 2 outputs and has  the words "String JACK" in the heading.  This is when I have JACK  selected as the audio device type.  If I select ALSA as the audio device  type, Loomer String gives me no outputs.  For the Juced based programs  that come with KXStudio (I randomly selected Peggy2000), if I select  Jack for the audio device type, I get "none" as my only output option.   If I select ALSA for the audio device type, I get "HDA ATI HDMI" as my  output option (which is a soundcard I don't use) or I can select "none".

I  just tried a different experiment where I tried setting Renoise to ALSA  instead of JACK.  Renoise told me another program was using the  soundcard (i.e. Jack).  I realized I need to turn Jack off for programs  to be able to see my main soundcard.  In hindsight, this is obvious and  explains why I could not see my main soundcard previously. I am feeling  silly I did not think of that earlier.  As soon as I turned off JACK, my  main soundcard showed up in the different applications (for ALSA only).

I  tried running some of the Juced programs and they do connect to my  sound card using ALSA when JACK is off.  The "Test" button creates  sound.  I was able to connect to a few of them (Nekobee and Loomer  String) with my electric piano and play sounds.  One of them (Peggy  2000) consistently crashes when I press any key on my electric  keyboard.  Anyway, my conclusion is the issue I have with the Juced  programs does not affect Renoise, Loomer, or Pianoteq, but does affect  the open source Juced programs I previously posted about in KXStudio at  least with  my hardware.  I see now this problem has something to do  with recognizing or working through JACK.

---

### Post by falkTX on 2011-11-22
> **mwinthrop said:**
> O.K. - I tried the demos for Renoise and Loomer String.  Both of these  programs seem to work.  They both automatically connected to the system  playback ports.  I ran Renoise and it did a fairly long search for plug  ins and then crashed.  I reran the program and it went through the  search again and then it ran O.K.  I was able to play 3 different demo  songs, successfully.  I ran Loomer String and created a midi port by  checking "midi-through" in the audio options.  I connected Jack-Keyboard  to the midi in port and was able to play sounds.

There is a  definite difference between Loomer String and the other programs.   Loomer String puts a box into Catia with 4 inputs and 2 outputs and has  the words "String JACK" in the heading.  This is when I have JACK  selected as the audio device type.  If I select ALSA as the audio device  type, Loomer String gives me no outputs.  For the Juced based programs  that come with KXStudio (I randomly selected Peggy2000), if I select  Jack for the audio device type, I get "none" as my only output option.   If I select ALSA for the audio device type, I get "HDA ATI HDMI" as my  output option (which is a soundcard I don't use) or I can select "none".

I  just tried a different experiment where I tried setting Renoise to ALSA  instead of JACK.  Renoise told me another program was using the  soundcard (i.e. Jack).  I realized I need to turn Jack off for programs  to be able to see my main soundcard.  In hindsight, this is obvious and  explains why I could not see my main soundcard previously. I am feeling  silly I did not think of that earlier.  As soon as I turned off JACK, my  main soundcard showed up in the different applications (for ALSA only).

I  tried running some of the Juced programs and they do connect to my  sound card using ALSA when JACK is off.  The "Test" button creates  sound.  I was able to connect to a few of them (Nekobee and Loomer  String) with my electric piano and play sounds.  One of them (Peggy  2000) consistently crashes when I press any key on my electric  keyboard.  Anyway, my conclusion is the issue I have with the Juced  programs does not affect Renoise, Loomer, or Pianoteq, but does affect  the open source Juced programs I previously posted about in KXStudio at  least with  my hardware.  I see now this problem has something to do  with recognizing or working through JACK.

Thanks for all your testing. I'm not sure what's wrong though, but I have 1 theory - new code regression.

Please check if there are any differences between 'eqinox' (old code) and 'juce_pitcher' (new code).
They don't need to make sound, just need to know if there are differences in the audio settings.
(Packages needed are 'juced-plugins' and 'distrho-plugin-ports'. Make sure you set device to JACK, close the settings, and open them again)

thanks

---

### Post by mwinthrop on 2011-11-26
O.K. - I installed distrho-plugin-ports and ran juced_pitcher in the terminal.  The behavior of juced_pitcher and Equinox (which was already installed on my system) seemed to be the same.  Juced_pitcher did not work correctly with Jack.  When I turned off Jack, I could connect juced_pitcher to my soundcard through Alsa, I was able to hear the test tone through my speakers.  I think Jack may have a setting or something about the way it is setup (at least on my computer) that is incompatible with the open source Juced programs.  Not sure what it could be, though.

---

### Post by falkTX on 2011-11-26
> **mwinthrop said:**
> O.K. - I installed distrho-plugin-ports and ran juced_pitcher in the terminal.  The behavior of juced_pitcher and Equinox (which was already installed on my system) seemed to be the same.  Juced_pitcher did not work correctly with Jack.  When I turned off Jack, I could connect juced_pitcher to my soundcard through Alsa, I was able to hear the test tone through my speakers.  I think Jack may have a setting or something about the way it is setup (at least on my computer) that is incompatible with the open source Juced programs.  Not sure what it could be, though.

I'm not sure about it either...

But I plan to get a new version of the DISTRHO ports out very soon, so keep an eye for updates. It probably won't change much though.

---

### Post by Jaybyrrd on 2011-12-03
FalkTX Can you please help me.. I have installed KX Studio exactly as the instructions say to, and now wine continuously does this.

wine regedit

wine: Virtual Memory Exhausted


I do not know what to do..

---

### Post by falkTX on 2011-12-03
> **Jaybyrrd said:**
> FalkTX Can you please help me.. I have installed KX Studio exactly as the instructions say to, and now wine continuously does this.

wine regedit

wine: Virtual Memory Exhausted


I do not know what to do..

Just add yourself to the audio group. The PPAs include a special version of Wine, Wine-RT, more info - [http://repo.or.cz/w/wine-rt.git/blob/wine-rt:/README.WINE-RT](http://repo.or.cz/w/wine-rt.git/blob/wine-rt:/README.WINE-RT)

Simply run:
```
sudo addgroup `whoami` audio
```

and re-login

---

### Post by skyemoor on 2011-12-27
As a new UbuntuStudio user (barely more than a novice Ubuntu user), I may represent the kind of person who will want to understand how to utilize KXStudio, so I'll jump in here with a little background and a few questions. With my systems engineering background, I'll start with the Use Cases (User Stories) that are driving my quest here with priorities (PRI) on a scale of 1 to 5 (1 highest);

1. (PRI 1) Wife wants to record segments of her madrigal group rehearsals to package up a audio file to have the members work on (likely 6 files each rehearsal). (Audacity expected to be used for this)

2. (PRI 2) Record the daughters' vocals for purposes of them hearing how they sound and making adjustments
(Audacity expected to be used for this)

3. (PRI 2) Record the madrigal group in the 'studio' and live
(will likely use Audacity initially, then transition to Ardor)
 
4. (PRI 2) Multi track recordings of the daughters' voices
(will likely use Audacity initially, then transition to Ardor)

5. (PRI 2) Recording tool for all family members to enable composition of works that include vocal tracks, some acapello, others with instrumentals from sampled (natural and simple generated) sources. (Expect to use Rose Garden, Ardor, Jack, Virtual keyboard with perhaps other apps)

6. (PRI 3) True MIDI tool for all family members to enable composition of works that include vocal tracks, some acapello, others with instrumentals from sampled and other generated sources such as Hydrogen, etc. (Expect to use Rose Garden, Ardor, Jack, Virtual Keyboard, Hydrogen, with perhaps other apps)

Family use skill levels: 
[LIST=1]
[*]The wife is ...ah... techno-lite, so I will likely teach her the basics of Audacity and leave it at that for the time being (until she sees the rest of us composing).
[*]The daughters (15 and 13 yr) are reasonably tech-absorbent, though might reach mindlock if there are too many obstacles for them to overcome.
[*]I'm a former Java Architect now a principal systems engineer who is used to integration 'challenges', though am not really hands on at this stage (55yrs). As a lead guitarist, I never had to learn MIDI, so will be starting from scratch. Any suggestions on how to do this in a manner that gives an understanding within the context of RoseGarden, ZynSubAddFX, Hydrogen, etc would be very helpful.
[/LIST]
I've downloaded Ubuntu Studio 11.10 on a Dell 630 and spent the last week learning how to crawl (initially just trying to get a sound to come out). Currently, I am able to;

[LIST]
[*]Record and playback on Audacity
[*]Play simple sounds via VirtualKeyboard, Jack, ZnyAddSubFX
[*]Play simple compositions via RoseGarden, Jack, ZnyAddSubFX
[*]Play simple drum channels via hydrogen (though not MIDI synchronized)
[/LIST]

(For background purposes) I used to play in club bands (lead guitar) during college (up from high school bands that used to perform at school events), and had a year of audio engineering as part of my engineering school electives. Back then, it was all analog, so I understand the concept of patchbays, master channels, etc. I don't, however, plan to spend a lot of time trying to figure out what works and what doesn't. I'm wondering if KXStudio will reduce the quirks with putting together a studio with the priorities noted above.

I'm not sure I yet understand when to use PulseAudio, Gnome-ALSA-mixer, and/or anything else (though I do see PA suppressed when JACK is loaded).

My questions;

Should I continue to use the stock UbuntuStudio release (with occasional tweaks and additions like Audacity), or would going the KXStudio route be recommended? 

I also have a work laptop (Dell Latitude E6520, 4G RAM, Dual Quad Core, NVIDIA HD Audio) with an 80G partition I've been planning to install Ubuntu on. One alternative could be to go the route of using this laptop to trial KXStudio on. If so (and I find KXStudio to be the preferred approach), I could use this as the means to test new releases/updates before updating the family laptop so that there are no squalls and squawks if an update breaks a link somewhere. Thoughts?

P.S. FalkTX, I've read about 12 of the first pages of this thread, and the last 5, and congratulate you on building on an environment to enable the significantly enhanced creative pursuits of many others. Obrigado por sua contribuição substancial para a humanidade!

---

### Post by maghoxfr on 2011-12-27
> **skyemoor said:**
> As a new UbuntuStudio user (barely more than a novice Ubuntu user), I may represent the kind of person who will want to understand how to utilize KXStudio, so I'll jump in here with a little background and a few questions. With my systems engineering background, I'll start with the Use Cases (User Stories) that are driving my quest here with priorities (PRI) on a scale of 1 to 5 (1 highest);

1. (PRI 1) Wife wants to record segments of her madrigal group rehearsals to package up a audio file to have the members work on (likely 6 files each rehearsal). (Audacity expected to be used for this)

2. (PRI 2) Record the daughters' vocals for purposes of them hearing how they sound and making adjustments
(Audacity expected to be used for this)

3. (PRI 2) Record the madrigal group in the 'studio' and live
(will likely use Audacity initially, then transition to Ardor)
 
4. (PRI 2) Multi track recordings of the daughters' voices
(will likely use Audacity initially, then transition to Ardor)

5. (PRI 2) Recording tool for all family members to enable composition of works that include vocal tracks, some acapello, others with instrumentals from sampled (natural and simple generated) sources. (Expect to use Rose Garden, Ardor, Jack, Virtual keyboard with perhaps other apps)

6. (PRI 3) True MIDI tool for all family members to enable composition of works that include vocal tracks, some acapello, others with instrumentals from sampled and other generated sources such as Hydrogen, etc. (Expect to use Rose Garden, Ardor, Jack, Virtual Keyboard, Hydrogen, with perhaps other apps)

Family use skill levels: 
[LIST=1]
[*]The wife is ...ah... techno-lite, so I will likely teach her the basics of Audacity and leave it at that for the time being (until she sees the rest of us composing).
[*]The daughters (15 and 13 yr) are reasonably tech-absorbent, though might reach mindlock if there are too many obstacles for them to overcome.
[*]I'm a former Java Architect now a principal systems engineer who is used to integration 'challenges', though am not really hands on at this stage (55yrs). As a lead guitarist, I never had to learn MIDI, so will be starting from scratch. Any suggestions on how to do this in a manner that gives an understanding within the context of RoseGarden, ZynSubAddFX, Hydrogen, etc would be very helpful.
[/LIST]
I've downloaded Ubuntu Studio 11.10 on a Dell 630 and spent the last week learning how to crawl (initially just trying to get a sound to come out). Currently, I am able to;

[LIST]
[*]Record and playback on Audacity
[*]Play simple sounds via VirtualKeyboard, Jack, ZnyAddSubFX
[*]Play simple compositions via RoseGarden, Jack, ZnyAddSubFX
[*]Play simple drum channels via hydrogen (though not MIDI synchronized)
[/LIST]

(For background purposes) I used to play in club bands (lead guitar) during college (up from high school bands that used to perform at school events), and had a year of audio engineering as part of my engineering school electives. Back then, it was all analog, so I understand the concept of patchbays, master channels, etc. I don't, however, plan to spend a lot of time trying to figure out what works and what doesn't. I'm wondering if KXStudio will reduce the quirks with putting together a studio with the priorities noted above.

I'm not sure I yet understand when to use PulseAudio, Gnome-ALSA-mixer, and/or anything else (though I do see PA suppressed when JACK is loaded).

My questions;

Should I continue to use the stock UbuntuStudio release (with occasional tweaks and additions like Audacity), or would going the KXStudio route be recommended? 

I also have a work laptop (Dell Latitude E6520, 4G RAM, Dual Quad Core, NVIDIA HD Audio) with an 80G partition I've been planning to install Ubuntu on. One alternative could be to go the route of using this laptop to trial KXStudio on. If so (and I find KXStudio to be the preferred approach), I could use this as the means to test new releases/updates before updating the family laptop so that there are no squalls and squawks if an update breaks a link somewhere. Thoughts?

P.S. FalkTX, I've read about 12 of the first pages of this thread, and the last 5, and congratulate you on building on an environment to enable the significantly enhanced creative pursuits of many others. Obrigado por sua contribuição substancial para a humanidade!

I would recommend you to get qjackctl and qtractor (has midi and automation). It's more powerful than audacity and simpler to use than ardour. Also instead of zynnaddsubfx, yoshimi is a fork of it but it's neater. Phasex and amsynth are cool also. For effects the calf plugins are great and you can get qsynth or fluidsynth to play soundfonts.

I'm not an expert at all, but you can find great advise on this forums as well as on linuxmusicians.org.

---

### Post by falkTX on 2011-12-28
> **skyemoor said:**
> My questions;

Should I continue to use the stock UbuntuStudio release (with occasional tweaks and additions like Audacity), or would going the KXStudio route be recommended? 

KXStudio right now just mean additional apps and PPAs, so you still have you system exactly as it was before the 'update'.
KXStudio is not supposed to break anything, just to update your packages. If any problem occurs, please say so. I'm already doing work for 12.04 so I'm not testing/using any 10.04<->11.04 versions. I rely on user reports for those.

> **skyemoor said:**
> I also have a work laptop (Dell Latitude E6520, 4G RAM, Dual Quad Core, NVIDIA HD Audio) with an 80G partition I've been planning to install Ubuntu on. One alternative could be to go the route of using this laptop to trial KXStudio on. If so (and I find KXStudio to be the preferred approach), I could use this as the means to test new releases/updates before updating the family laptop so that there are no squalls and squawks if an update breaks a link somewhere. Thoughts?
As I said, KXStudio should not break anything, otherwise consider it a bug.
My recommendation is to get UbuntuStudio or any other variant you like (Lubuntu, Kubuntu, maybe even LinuxMint), and add the KX repos.
The 'kxstudio-default-settings' package should do the magic settings for you, you are not forced to install anything else.

> **skyemoor said:**
> P.S. FalkTX, I've read about 12 of the first pages of this thread, and the last 5, and congratulate you on building on an environment to enable the significantly enhanced creative pursuits of many others. Obrigado por sua contribuição substancial para a humanidade!

Many thanks for your nice words, I really hope to be doing some good here :P

---

### Post by falkTX on 2011-12-28
> **maghoxfr said:**
> I would recommend you to get qjackctl and qtractor (has midi and automation). It's more powerful than audacity and simpler to use than ardour. Also instead of zynnaddsubfx, yoshimi is a fork of it but it's neater. Phasex and amsynth are cool also. For effects the calf plugins are great and you can get qsynth or fluidsynth to play soundfonts.
Cadence and it's tools are meant to fully replace qjackctl. It was made on a time when you only used jack to make music, and stop it for everything else. With Cadence (and the KXStudio project in general), work has been done to allow jack to run all the time.
The main Cadence app is not yet ready though (alpha-1 release), I hope it will be for 12.04...

Yoshimi development has been stopped, and now patches are being merged to the main ZynAddSubFX code. Once a 2.4.2/2.5.0 gets out, it will contain most of the forked code.
 
> **maghoxfr said:**
> I'm not an expert at all, but you can find great advise on this forums as well as on linuxmusicians.org.
Totally agree, linuxmusicians is a great source of linux-audio information.
Direct link to wiki -> [http://wiki.linuxmusicians.com/doku.php](http://wiki.linuxmusicians.com/doku.php)

---

### Post by sgx on 2011-12-29
It's good to hear that zyn and Yoshimi are uniting, I hope the
two velocity controls from the main Yoshimi gui will be implemented in
zyn, they are very useful!.
Cheers

---

### Post by jannytra on 2012-01-14
Hello, first of all, I would like to congratulate to falkTX for creating and maintaining such a nice and useful collection of software for music and other types of multimedia :)

I myself decided to give Linux a try about music - I play guitar using my computer for amp simulations and other kinds of effects, having my guitar connected to my laptop through an USB interface. I am using Windows 7 (Cubase LE 5) for that right now, but as I said, I would like to try it in Linux - to be exact, in my Ubuntu 10.04 system which I set up. I already tried connecting my USB sound card and it was successfully recognized, so I guess I have "green" to continue trying :)

I would like to ask about installing KXStudio - for now, I would just like to add needed apps (JACK2, FeSTige, Wine, LADISH, Claudia, Klaudia) without changing my desktop environment, at least for now before I switch to 12.04. Plus I would like to install the lowlatency kernel provided in PPAs. Could you please give me any hints how to do this properly so that I would not kill my system?

Maybe, as I already said, I would try changing the whole desktop environment when I switch to another distribution, butlater, I would not like to reinstall my system right now :)

Thanks in advance :)

---

### Post by stanlea on 2012-01-14
I use 10.04 with the KX repositories without problem. Just add the repositories in your database and you're done. See here :

[http://kxstudio.sourceforge.net/KXStudio:Repositories](http://kxstudio.sourceforge.net/KXStudio:Repositories)

---

### Post by jannytra on 2012-01-15
OK, thank you for your feedback. Just one more question - do I need to install the KXStudio desktop as suggested here in this manual:

[http://kxstudio.sourceforge.net/Help:Ubuntu:Upgrade](http://kxstudio.sourceforge.net/Help:Ubuntu:Upgrade)

to get things work properly? Or would that just change my desktop?

---

### Post by reteo on 2012-01-15
> **jannytra said:**
> I would like to ask about installing KXStudio - for now, I would just like to add needed apps (JACK2, FeSTige, Wine, LADISH, Claudia, Klaudia) without changing my desktop environment, at least for now before I switch to 12.04. Plus I would like to install the lowlatency kernel provided in PPAs. Could you please give me any hints how to do this properly so that I would not kill my system?

I put together a tutorial on my blog that gives a basic rundown of adding the PPAs and setting up without adding all the UI glitter and desktop environment stuff.  Unfortunately, all the UI stuff seems to be bunched together with the system tweaks, so I've included the steps to manually set the tweaks for decent system performance.

You can find it at [http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html](http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html)

I don't know if this is even near what the official word is, but it's worked for me so far.

---

### Post by jannytra on 2012-01-15
Thank you for the tips, I installed software today and will test it in several days.

---

### Post by sgx on 2012-01-15
> **reteo said:**
> I put together a tutorial on my blog that gives a basic rundown of adding the PPAs and setting up without adding all the UI glitter and desktop environment stuff.  Unfortunately, all the UI stuff seems to be bunched together with the system tweaks, so I've included the steps to manually set the tweaks for decent system performance.

You can find it at [http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html](http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html)

I don't know if this is even near what the official word is, but it's worked for me so far.
'Official' was banned unanimously by voters in 2009.
Both of us voted :popcorn:

---

### Post by reteo on 2012-01-16
Well, then, I wish to contest the vote... as I wasn't able to make it unanimous among three. :P:popcorn:

---

### Post by sgx on 2012-01-16
Your vote counts as seven, so it's a landslide.
Parliament quakes in fear :)

---

### Post by reteo on 2012-01-21
Yay me! :KS

---

### Post by jannytra on 2012-01-27
Hello, I am back with one problem I have. I reinstalled my Ubuntu 10.04 32bit, because many things changed after upgrading the system after adding kxstudio repositories. Therefore I installed 3rd OS - again Ubuntu 10.04 32bit and decided to build kxstudio from that. Everything went smooth, I followed guide to upgrade ubuntu system from kxstudio website. I installed **kxstudio-desktop-gnome**, changed the main menu to my likes. Jack running fine, I even managed to create my first studio in Claudia, inserted VST plugins and was able to play guitar through an USB audio interface.

But I problem occured. I tried to install the lowlatency kernel (**kxstudio-kernel-lowlatency**), but I got 2 error messages - **fglrx** and **bcmwl-kernel-source** failed to install or upgrade :( Any ideas what to do?

---

### Post by falkTX on 2012-01-27
> **jannytra said:**
> Hello, I am back with one problem I have. I reinstalled my Ubuntu 10.04 32bit, because many things changed after upgrading the system after adding kxstudio repositories. Therefore I installed 3rd OS - again Ubuntu 10.04 32bit and decided to build kxstudio from that. Everything went smooth, I followed guide to upgrade ubuntu system from kxstudio website. I installed **kxstudio-desktop-gnome**, changed the main menu to my likes. Jack running fine, I even managed to create my first studio in Claudia, inserted VST plugins and was able to play guitar through an USB audio interface.

But I problem occured. I tried to install the lowlatency kernel (**kxstudio-kernel-lowlatency**), but I got 2 error messages - **fglrx** and **bcmwl-kernel-source** failed to install or upgrade :( Any ideas what to do?

the lowlatency kernel in lucid is 2.6.38, way after the official 2.6.32 meant for it.
It's not easy to fix, so I advise you to use the generic (or preempt) kernel for the moment.
When 12.04 arrives, a new lowlatency kernel will emerge, and all modules should build just fine with it.

---

### Post by jannytra on 2012-01-27
> **falkTX said:**
> the lowlatency kernel in lucid is 2.6.38, way after the official 2.6.32 meant for it.
It's not easy to fix, so I advise you to use the generic (or preempt) kernel for the moment.
When 12.04 arrives, a new lowlatency kernel will emerge, and all modules should build just fine with it.

thanks for the info, I will stay with the generic kernel - anyway, I had  only very occasional xruns and the performance was good, I had quite  many effects running, so I think it will not be problem :)

just to make sure - it is enough to remove all packages related to the  lowlatency kernel via Synaptic Package Manager and the kernel will be  gone, right?

---

### Post by falkTX on 2012-01-27
> **jannytra said:**
> thanks for the info, I will stay with the generic kernel - anyway, I had  only very occasional xruns and the performance was good, I had quite  many effects running, so I think it will not be problem :)

just to make sure - it is enough to remove all packages related to the  lowlatency kernel via Synaptic Package Manager and the kernel will be  gone, right?

Yes, but use right-click and select "complete removal", so it really removes old config files.

---

### Post by aaronLund on 2012-02-16
falktx,

RE:  Flash vids/youtube with no sound.

Missed you in irc the other night.  You said:


> is asoundrc set to jack or pulseaudio mode?

Here it is.

```
pcm.!default {
    type plug
    slave { pcm "pulse" }
}

pcm.pulse {
    type pulse
}

ctl.mixer0 {
    type hw
    card 0
}

```

Looks like it recently changed which I'm sure I had a hand in but, to be honest, I have yet to fully understand this file and wtf it's actually doing.  Does this get re-written depending on what else is being used?  Because I haven't touched it in some time.

Just to recap, sound works fine everywhere else.  It's just flash vids that aren't working.

Thanks for any advice.

---

### Post by aaronLund on 2012-02-16
Hmmm.....

I dug around in my email since I knew I had this problem once before and fixed it.  Found an older version (.bak) of .asoundrc.

Simply replaced "alsa_pcm" with "system" and all's well.

My questions about this file still stand though.  Namely, "What the hell changes this file?"

So anyone should feel free to drop some science.  Thanks!

[FONT="Arial Black"][SIZE="4"]My working .asoundrc file[/SIZE][/FONT]

```

     
    pcm.jack {
        type jack
        playback_ports {
            0 system:playback_1
            1 system:playback_2
        }
        capture_ports {
            0 system:capture_1
            1 system:capture_2
        }
    }
     
    ctl.mixer0 {
        type hw
        card 0
    }

```

---

### Post by CivilizationII on 2012-02-17
Lot of thanks for the link of KXStudio.

I like very much the replacement of jack 2 by jack 1 since i have many xruns with jack 2

---

### Post by maghoxfr on 2012-02-18
> When 12.04 arrives, a new lowlatency kernel will emerge, and all modules should build just fine with it.

I need to update my Ubuntu, but I was kind of reluctant to upgrade it to the current 11.10. Would it be better to wait for the 12.04?

Thanks

---

### Post by falkTX on 2012-02-18
> **maghoxfr said:**
> I need to update my Ubuntu, but I was kind of reluctant to upgrade it to the current 11.10. Would it be better to wait for the 12.04?

Thanks

There's no point to update to 12.04 just yet, most things are not ready.

---

### Post by maghoxfr on 2012-02-18
> **falkTX said:**
> There's no point to update to 12.04 just yet, most things are not ready.

SOrry, I meant to wait for the official release in April. SHould I stick to my 10.04 until 12.04 is released, or shuold I upgrade now to 11.10? I want to upgrade for several reasons, but the main thing for me is that the audio repos work. If not, I have no problem in sticking to my ol' 10.04.

THanks

---

### Post by falkTX on 2012-02-18
> **maghoxfr said:**
> SOrry, I meant to wait for the official release in April. SHould I stick to my 10.04 until 12.04 is released, or shuold I upgrade now to 11.10? I want to upgrade for several reasons, but the main thing for me is that the audio repos work. If not, I have no problem in sticking to my ol' 10.04.

THanks

If you already have a working setup, keep it (wherever version it is).

If you're going for a new install, and planning to update afterwards, install 11.04 for the moment. When 12.04 arrives, do a _fresh install_ again.

---

### Post by maghoxfr on 2012-02-18
> **falkTX said:**
> If you already have a working setup, keep it (wherever version it is).

If you're going for a new install, and planning to update afterwards, install 11.04 for the moment. When 12.04 arrives, do a _fresh install_ again.

Thank you falkTX. For the advice and the awesome work you keep doing.

---

### Post by jannytra on 2012-02-25
Hello, I'd like to have a question. I have setup KXStudio over Ubuntu 10.04 32bit and it is quite all working. I am able to play drums in Hydrogen and use Claudia to create sessions - I play guitar and I use VST plugins - therefore I am using festige.

But I have a problem. Sometimes, Claudia crashes while starting a studio. This is my procedure: create studio, add festige and add 4 VSTs - I save states of those plugs to /.ladish/festige folder.

So to my problem - with any reason I could come up, sometimes Claudia crashes while starting such a studio, and after system restart, that exact studio starts just fine :( am I doing something wrong?

---

### Post by sgx on 2012-02-26
try saving the session with just one of each of the 4 vsts
If it fails with one, but works with the other three, you see
the villain. Now try saving a session with 2 of the vsts,
then three. (*You'll get an idea if it is Claudia beta, or
something else.)

If there is one vst that is problematic, find a similar competitor,
or just load it manually after the session starts, and delete it before
saving the session.

LePou, and Serina Experiment, offer excellent guitar vsts,
and are very affordable ;)

[http://lepouplugins.blogspot.com/](http://lepouplugins.blogspot.com/)

[http://www.theserinaexperiment.net](http://www.theserinaexperiment.net)

---

### Post by jannytra on 2012-02-26
Hi, thanks yor your suggestion. But I am a little bit sceptic, because as I said - the very same session starts sometime fines, and sometimes crashes. But you are right, that it coulb be caused by 1 plugin all the time :) I will give it a try in next few days and will see results I get :) and you are right, Lepou and TSE plugs are aresome, Le456 is maybe my most favourite one :)

---

### Post by shimoda on 2012-04-01
Hi!

I'm using pulse-jack with no probs, but I think since last update of flash player plugin, I get no sound from youtube videos. I must stop jack to hear it... Anyone with same problem? Any ideas to solve it?

EDIT: I temporaly solved it downgrading flash plugin

---

### Post by vervelover on 2012-04-07
@shimoda

same issue here! But how did you downgrade flash? I can't do it via synaptics and I can't find the old .deb anymore..

---

### Post by stanlea on 2012-04-08
@falktx : any news ? still working on next stable ubuntu ?

cheers

---

### Post by shimoda on 2012-04-13
> **vervelover said:**
> @shimoda

same issue here! But how did you downgrade flash? I can't do it via synaptics and I can't find the old .deb anymore..

sorry vervelover, I had not seen your message until now. I downloaded flash version 11.1.102.63 from adobe, here:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Then I unziped it and copied only the file "libflashplayer.so"(I don't remember it's folder. You can search where is your version and overwrite it)

---

### Post by falkTX on 2012-04-27
The PPAs are now fully compatible with 12.04! :guitar:

There quite a few package tweaks in there, Debian seems to like to build packages with debug enabled (bad thing I say, we want max performance possible!), so you'll notice some ...+nodebug1 or +fixed1 package "updates".

Enjoy!
[http://kxstudio.sourceforge.net/KXStudio:Repositories](http://kxstudio.sourceforge.net/KXStudio:Repositories)


PS: Note that there is a new 'plugins' PPA, which only provides audio plugins and _doesn't depend on the main repo_.
Install 'calf-plugins-git' and enjoy those awesome plugins!

---

### Post by maghoxfr on 2012-04-27
> **falkTX said:**
> The PPAs are now fully compatible with 12.04! :guitar:

There quite a few package tweaks in there, Debian seems to like to build packages with debug enabled (bad thing I say, we want max performance possible!), so you'll notice some ...+nodebug1 or +fixed1 package "updates".

Enjoy!
[http://kxstudio.sourceforge.net/KXStudio:Repositories](http://kxstudio.sourceforge.net/KXStudio:Repositories)


PS: Note that there is a new 'plugins' PPA, which only provides audio plugins and _doesn't depend on the main repo_.
Install 'calf-plugins-git' and enjoy those awesome plugins!

Wow awesome job FalkTx!

---

### Post by aaronLund on 2012-04-29
So I'm doing a clean install of 12.04 (long time 10.04 user) and am having trouble getting the ppas to deliver anything.

Perhaps the rules are different now with the 'Software Center' and all but, now that I've got the PPAs there (I can see them in 'Software Sources') what do I need to do to get everything I'm accustomed to (Ardour, Clementine, Cadence, etc.)?

Do I now need to install all of these programs one by one (i.e. manually) in the Software Center.

This new fangled Unity et al. frightens and confuses me.

;-)

Thanks.

---

### Post by falkTX on 2012-04-29
great news! ardour3 (beta, latest svn) is now on the 12.04 latest PPA.
that and also the latest qtractor-svn and ingen-svn too :P

@aaronLund: I use Synaptic, and it's still available to install in 12.04 if you want it.
The bottom-left of it has a "Origin" option that separates packages from repositories, so you can know what a repository/PPA contains.

---

### Post by shupacabras on 2012-05-03
Hi all

Claudia crash at start Ubuntu 12.04

Console error
```
cristian@cristian-System-Product-Name:~$ claudia
Using JACK2, version 1.9.8

(claudia.py:4309): Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
«trap» para punto de parada/seguimiento (`core' generado)
cristian@cristian-System-Product-Name:~$ 

```

Sorry for my bad english
Regards

---

### Post by falkTX on 2012-05-03
> **shupacabras said:**
> Hi all

Claudia crash at start Ubuntu 12.04

Console error
```
cristian@cristian-System-Product-Name:~$ claudia
Using JACK2, version 1.9.8

(claudia.py:4309): Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
«trap» para punto de parada/seguimiento (`core' generado)
cristian@cristian-System-Product-Name:~$ 

```

Sorry for my bad english
Regards

Seems to be related to the systray module, I'll check this soon.
(Thanks for the report!)

For now use:
```
env DESKTOP_SESSION=beh claudia
```

---

### Post by shupacabras on 2012-05-04
thanks falk =)

---

### Post by jannytra on 2012-05-07
Hello, I would like to make a clean 12.04 install. I would like to avoid Unity, because it would not be suitable for audio work. I am intending to create some drum loops and hopefully play guitar through Windows VSTs :)

Is Xubuntu suitable for building KXStudio over it? XFCE desktop seems pretty nice :) And if yes, shall I install 32bit or 64bit?

Thanks in advance.

---

### Post by falkTX on 2012-05-07
> **jannytra said:**
> Hello, I would like to make a clean 12.04 install. I would like to avoid Unity, because it would not be suitable for audio work. I am intending to create some drum loops and hopefully play guitar through Windows VSTs :)

Is Xubuntu suitable for building KXStudio over it? XFCE desktop seems pretty nice :) And if yes, shall I install 32bit or 64bit?

Thanks in advance.

Use 64bit if you can, UbuntuStudio is the prefered base for a KXStudio upgrade.

Note: There are specific KXStudio forums now, here:
[http://linuxmusicians.com/viewforum.php?f=47](http://linuxmusicians.com/viewforum.php?f=47)

---

### Post by jannytra on 2012-05-09
> **falkTX said:**
> Use 64bit if you can, UbuntuStudio is the prefered base for a KXStudio upgrade.

Note: There are specific KXStudio forums now, here:
[http://linuxmusicians.com/viewforum.php?f=47](http://linuxmusicians.com/viewforum.php?f=47)

Thanks for the reply :) I will check those as soon as possible.

Just a quick question - does UbuntuStudio now have a QUI installation enviroment like Ubuntu/Xubuntu? I would not like to have troubles installing UbuntuStudio, because my drive partitioning is quite complicated (Windows 7 + Ubuntu + KXStudio) I would like to be sure that I will be able to choose partitions properly like during Ubuntu installation :)

---

### Post by falkTX on 2012-05-09
The latest UbuntuStudio 12.04 has a Live-DVD + installer, the "old" method of installing (via alternate DVD) is no longer available.

---

### Post by jannytra on 2012-05-09
thanks a lot for that info :) I will grab that DVD as soon as possible - better after my school exams, playing with audio in Linux would keep me away from studying :p

---

### Post by vervelover on 2012-05-10
Hi falkTX,

just trying you repos on ubuntu 12.04 64bit, everything looks great except 2 things: I can't install wine amd64 (I get a dependency error), and festige seems to be 32bit only (it asks me to install festige-backend:i386), is it normal? Everything else is fantastic!

Thanks
Alessio

---

### Post by Jimmy Eggs on 2012-05-14
Hi falk. Thanks for graciously making Ubuntu Studio even better.

I'm just wondering: what happened to Ardour3? It seems to be missing from the Latest PPA. I'm guessing it has something to do with the broken package errors I got when I tried to install it a few days ago. I figured it was a dependency problem or something on my side at the time.

Thanks again for your contributions. I probably wouldn't be making music right now without your hard work.

---

### Post by falkTX on 2012-05-14
> **Jimmy Eggs said:**
> Hi falk. Thanks for graciously making Ubuntu Studio even better.

I'm just wondering: what happened to Ardour3? It seems to be missing from the Latest PPA. I'm guessing it has something to do with the broken package errors I got when I tried to install it a few days ago. I figured it was a dependency problem or something on my side at the time.

Thanks again for your contributions. I probably wouldn't be making music right now without your hard work.

please read this - [http://linuxmusicians.com/viewtopic.php?f=47&t=8049](http://linuxmusicians.com/viewtopic.php?f=47&t=8049)
I forgot to remove ardour3 has dependency in the meta-packages, thanks for the reminder.

---

### Post by Jimmy Eggs on 2012-05-14
Thanks for the fill-in falk! Didn't realize you were putting up with cranky devs for us.

---

### Post by shupacabras on 2012-05-21
hi all

anyone working on any projects similar to
melodine studio, or v-vocal (sonar) or cubase tool (wavewarp or something)?

I want to get rid of wine, I tried native linux alternatives, but they are very intrusive (all correct)

I venture to use a pre-pre-pre-alpha =)

Greetings and congratulations for the work

---

### Post by falkTX on 2012-05-22
> **shupacabras said:**
> hi all

anyone working on any projects similar to
melodine studio, or v-vocal (sonar) or cubase tool (wavewarp or something)?

I want to get rid of wine, I tried native linux alternatives, but they are very intrusive (all correct)

I venture to use a pre-pre-pre-alpha =)

Greetings and congratulations for the work

Can you give more details on what specific features you need? (not an app-clone, that will never happen).
Simple things are possible, entire apps that mimic your windows ones not.

---

### Post by shupacabras on 2012-05-22
> **falkTX said:**
> Can you give more details on what specific features you need? (not an app-clone, that will never happen).
Simple things are possible, entire apps that mimic your windows ones not.

Hi Falk

Maybe one standalone player with sync jack or plug-in
in which you can manually correct the tuning of a note / s you want.

There are several applications under Windows, it actually all work similarly (Melodyne, v-vocal, Cubase has a tool but not the name, and of course also Protools)

the closest thing I tasted was "zita-t1," but you have to play the melody while not perfect, but when no midi melody automatically tunes

if you could automatically detect and transcribe the melody midi, would be a solution, but did not find tool

If "sonic-visualizer" export to midi tone analyzer results, would be a way to sulucion

fix for now, if not much, one part on another track, but there are times that the singer is not good to do miracles and can tomarun couple of hours to correct a few minutes

ever used, Celemony melodine studio? can use a demo under wine 1.0

I hope you understand, my English is not good

Kind regards =)

---

### Post by babarosa on 2012-05-22
@FalkTx

Thank you very much for your efforts - your apps work very fine for me both for 32bit and 64bit. Where would we be without you portuguese people (Rui and you)?

@shupacabras

Try "waon" - [http://waon.sourceforge.net/](http://waon.sourceforge.net/)

Compiling it is quite easy

---

### Post by shupacabras on 2012-05-22
> **babarosa said:**
> @FalkTx

Thank you very much for your efforts - your apps work very fine for me both for 32bit and 64bit. Where would we be without you portuguese people (Rui and you)?

@shupacabras

Try "waon" - [http://waon.sourceforge.net/](http://waon.sourceforge.net/)

Compiling it is quite easy

Tanks babarosa

---

