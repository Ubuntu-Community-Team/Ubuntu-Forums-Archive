---
title: "synaptic will not run with kernel 3.5.0-3-AMD64bit"
date: 2012-07-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-03
Synaptic  will not run. I was able to file a bug but now ff is very sluggish.
That is an Acer Extensa 4420 AMD athelon X2 Dual Core 64bit.

Just awful performance.

Ati Radeon Xpress 1250

 I am not sure if this can be considered a kernel panic but it worked swell with Precise 32bit (not64bit)

---

### Post by QIII on 2012-07-03
Even from the terminal with gksudo?

I could swear I had used it, but maybe not since the latest Alpha.

---

### Post by ScislaC on 2012-07-03
Working here when launched from a terminal.

---

### Post by kyleabaker on 2012-07-03
I've not been able to open ANY applications in Kernel 3.5.x and have been booting in 3.4 instead. Every application that I try to open times out or something and crashes. Whats worse is that the network manager doesn't load either so I can't even file a bug.

---

### Post by ventrical on 2012-07-03
gksu synaptic worked ok . Thanks.

it is still very touchy and unstable.

Here is the bug that I filed so far.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1020653](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1020653)

---

### Post by balloons on 2012-07-03
Is this something more endemic? If we can get some bugs filed, I'll make sure to mention it and have a look. I'm seeing more and more threads like this in regards to the 3.5 kernel. Open some bugs and subscribe me to them if you think they need more attention than they are getting. Thanks!

---

### Post by ronacc on 2012-07-03
> **guitara said:**
> Is this something more endemic? If we can get some bugs filed, I'll make sure to mention it and have a look. I'm seeing more and more threads like this in regards to the 3.5 kernel. Open some bugs and subscribe me to them if you think they need more attention than they are getting. Thanks!

filing bugs is kind of hard when even apport is buggy . I spen't 6 hours sunday trying to get a bug filed on the then current daily . as kyleabaker said everything about the 3.5.0-x kernel is a disaster .

and when after 6 frustrating hours I finally got apport to finish reporting a bug it was rapidly marked invalid because apport had mangled the bug .

---

### Post by philinux on 2012-07-03
> **guitara said:**
> Is this something more endemic? If we can get some bugs filed, I'll make sure to mention it and have a look. I'm seeing more and more threads like this in regards to the 3.5 kernel. Open some bugs and subscribe me to them if you think they need more attention than they are getting. Thanks!

Been running just fine on acer 1410 with 64 bit.

---

### Post by ronacc on 2012-07-03
> **philinux said:**
> Been running just fine on acer 1410 with 64 bit.

its got to be hardware specific , on my amd64 sys it's been nothing but crashes since 3.5.0-1 , on my one install that has all the old kernels if I boot into one of the 3.4 kernels everything is ok

---

### Post by coffeecat on 2012-07-03
Synaptic is OK for me with:

```
coffeecat@Vaio-QuantalAlpha:~$ uname -a
Linux Vaio-QuantalAlpha 3.5.0-3-generic #3-Ubuntu SMP Mon Jul 2 16:49:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by kyleabaker on 2012-07-03
> **ronacc said:**
> its got to be hardware specific , on my amd64 sys it's been nothing but crashes since 3.5.0-1 , on my one install that has all the old kernels if I boot into one of the 3.4 kernels everything is ok

I'm also running on amd64 hardware. That very well could be the common link.

---

### Post by QIII on 2012-07-03
I am using a Phenom II x6 1100T with no problems at all...

So maybe not AMD specific.

Then again, I am using Xubuntu.

---

### Post by mc4man on 2012-07-03
> **ventrical said:**
> Synaptic  will not run. I was able to file a bug but now ff is very sluggish.
That is an Acer Extensa 4420 AMD athelon X2 Dual Core 64bit.

Just awful performance.

Ati Radeon Xpress 1250

 I am not sure if this can be considered a kernel panic but it worked swell with Precise 32bit (not64bit)
If synaptic won't open 'normally' but does thru terminal (pkexec synaptic or gksudo) then check the end of ~/.xsession-errors for a couple of obvious lines.
Has been happening every once & a while on 12.10  - in this case, (here), it's not synaptic but the auth window (polkit) that's failing to open.
I forget the error - should be obvious

---

### Post by ventrical on 2012-07-03
> **mc4man said:**
> If synaptic won't open 'normally' but does thru terminal (pkexec synaptic or gksudo) then check the end of ~/.xsession-errors for a couple of obvious lines.
Has been happening every once & a while on 12.10  - in this case, (here), it's not synaptic but the auth window (polkit) that's failing to open.
I forget the error - should be obvious

I think your right here .. but apport will not record or report this. Apport seems to be sleeping in most cases or there seem to be a sideXside. However it worked fine with kernel 3.4 set ..(still does) so whats changed with the kernel anyways?

---

### Post by ventrical on 2012-07-03
> **QIII said:**
> I am using a Phenom II x6 1100T with no problems at all...

So maybe not AMD specific.

Then again, I am using Xubuntu.

I guess it would just depend if you are running the 32 bit iso or the 64 bit iso.. (kernel) because the problem seems to be with the 64bit installs.

---

### Post by QIII on 2012-07-03
64 bit here.

Hmmm...

Dang it!  Nothing ever seems wrong for me!  No fair!

---

### Post by ScislaC on 2012-07-03
> **mc4man said:**
> If synaptic won't open 'normally' but does thru terminal (pkexec synaptic or gksudo) then check the end of ~/.xsession-errors for a couple of obvious lines.
Has been happening every once & a while on 12.10  - in this case, (here), it's not synaptic but the auth window (polkit) that's failing to open.
I forget the error - should be obvious

Doesn't look like it's trying a GUI authentication method by looking at the error...

Error creating textual authentication agent: Error opening current controlling terminal for the process (`/dev/tty'): No such device or address

---

### Post by ventrical on 2012-07-03
> **QIII said:**
> 64 bit here.

Hmmm...

Dang it!  Nothing ever seems wrong for me!  No fair!

Xubuntu is a fine piece of work and runs a lot lighter than Unity or Ubuntu as a whole. Umm... you did notice the topic header <ubuntu> did you not ? :) I'm not trying to be smart .. I'm just trying to stay on the same page...  :)

and that is one  monster of a processor you have there :)

---

### Post by QIII on 2012-07-03
Then again, I did say "Then again, I am using Xubuntu."

Which might be part of the puzzle?  Kernel or DE?

OK.  OK.  I'll check this out on Ubuntu tonight.

---

### Post by balloons on 2012-07-03
> **ronacc said:**
> filing bugs is kind of hard when even apport is buggy . I spen't 6 hours sunday trying to get a bug filed on the then current daily . as kyleabaker said everything about the 3.5.0-x kernel is a disaster .

and when after 6 frustrating hours I finally got apport to finish reporting a bug it was rapidly marked invalid because apport had mangled the bug .

I feel your pain. I've been downgrading apport to the precise version just to report the bugs I'm encountering (though nothing quite as serious as what your seeing). If you can't report the bug, manually enter it and describe the problem, or come here as you've done :-) Either way do feel free to let me know if it's something that isn't getting attention but needs it. I'm happy to help if I can.

---

### Post by ventrical on 2012-07-03
> **guitara said:**
> I feel your pain. I've been downgrading apport to the precise version just to report the bugs I'm encountering (though nothing quite as serious as what your seeing). If you can't report the bug, manually enter it and describe the problem, or come here as you've done :-) Either way do feel free to let me know if it's something that isn't getting attention but needs it. I'm happy to help if I can.


Hey .. thanks guitara .. I never thought of downgrading apport. That's a swift idea! :)

---

### Post by mc4man on 2012-07-03
> **ScislaC said:**
> Doesn't look like it's trying a GUI authentication method by looking at the error...

Error creating textual authentication agent: Error opening current controlling terminal for the process (`/dev/tty'): No such device or address
That is there error - how it relates to the pokit auth box don't know but it does

If for instance you where to remove the need to auth, then synaptic will always open normally (from icon, menu, ect.

Ex.
```
gksudo gedit /var/lib/polkit-1/localauthority/50-local.d/package-manager.pkla
```
use - 
```
[Install package synaptic]
Identity=unix-group:sudo
Action=com.ubuntu.pkexec.synaptic
ResultActive=yes

```

---

### Post by ventrical on 2012-07-03
> **QIII said:**
> Then again, I did say "Then again, I am using Xubuntu."

Which might be part of the puzzle?  Kernel or DE?

OK.  OK.  I'll check this out on Ubuntu tonight.


I would be interested to see how Unity 3D runs on that Phenom. You could download ubuntu-desktop-amd64.iso alpha 2, then fully upgrade and please get back.

Thanks.

It may prove to be something to do with Unity .. but apport is right out in left field atm..so I am assuming that we just don't know.. at least I don't.

edit:

I am going to hazard an assumption  and say that your phenom will work ok with Ubuntu64bit with Unity becuase there may be extra handling routines that can bypass the sideXside .. whatever it may be at the moment. It may even be a non-bug and perhaps only a adapter card driver issue.

---

### Post by philinux on 2012-07-03
> **mc4man said:**
> If synaptic won't open 'normally' but does thru terminal (pkexec synaptic or gksudo) then check the end of ~/.xsession-errors for a couple of obvious lines.
Has been happening every once & a while on 12.10  - in this case, (here), it's not synaptic but the auth window (polkit) that's failing to open.
I forget the error - should be obvious

Indeed. On the acer 1410 it asks for password straight away from clicking the launcher. I had to do a fix broken and decided to use synaptic this aft.  Had to do that a lot lately too.

---

### Post by ronacc on 2012-07-03
here it seems to happen much more with unity than with G-S  . I may have more to do with the gpu than the cpu , I have no "built in" gpu like many newer AMD's so my video is nvidia 7600 gs and nvidia-current driver . or it may have to do with the mobo chipset .so many people are having contradictory experiences it may take awhile to sort this one out .

---

### Post by ventrical on 2012-07-03
Ok.. I installed   <fvwm-crystal> which is an alternate DE. Synaptic came right up - no problem !

During the install these packages were removed:

Removed the following packages:
nvidia-common
python3-aptdaemon.pkcompat
ubuntu-desktop
ubuntu-drivers-common

It perplexes me that there was a nvidia-common with an Ati Radeon adapter card. Perhaps this means nothing but it appears that there is a problem with Unity or compiz that is causing these problems with amd64bit with Ati cards.

---

### Post by ventrical on 2012-07-03
> **ronacc said:**
> here it seems to happen much more with unity than with G-S  . I may have more to do with the gpu than the cpu , I have no "built in" gpu like many newer AMD's so my video is nvidia 7600 gs and nvidia-current driver . or it may have to do with the mobo chipset .so many people are having contradictory experiences it may take awhile to sort this one out .


ronacc,

I installed fvwm-crystal from synaptic and now it is working very fast, synaptic comming etc.. so far so good.

---

### Post by ronacc on 2012-07-03
> **ventrical said:**
> ronacc,

I installed fvwm-crystal from synaptic and now it is working very fast, synaptic comming etc.. so far so good.

thanks I'm d/l'ing that now . although as I noted above G-S gets rid of most of the problem for me although I haven't updated today yet , too much real work to do , I'll get that taken care of while I'm at it .

---

### Post by ventrical on 2012-07-03
I just installed gnome-shell about 15 minutes ago. I get the infinite apport loop. Otheriwse it is a little more functional than Unity. G-S behaves like a sort of android app .. almost turns my laptop into  a tablet pc :)

---

### Post by ventrical on 2012-07-03
Gnome-classic willnot allow me to move the windows with my mouse. I m currently using gnome-no-effects and it seems to be somewhat stable, although the networking is very buggy.. long waits to connect to the internet.

This kernel64 is having a rough time on this: Acer Extensa 4420 64amd athlonX2.

---

### Post by ronacc on 2012-07-03
I give up , installing fvwm-crystal made things even worse for me , I now can't even get an update/upgrade to complete from a text console and as it stands recovery mode is useless . I'll try tomorrows daily and see if thats any better .

---

### Post by jerrylamos on 2012-07-03
You people are doing a lot better than I am.  amd64 3.5.0-3 boots up to a frozen desktop with the external keyboard going through endless resets.  Acer Aspire 5253 wide screen notebook.

Jerry

p.s. with 3.5.0-2 I do get synaptic errors but it will still run a little bit - not about to try anything until the frozen desktop gets better.

---

### Post by jerrylamos on 2012-07-03
Pile of updates this morning, EST, busted so booted the old kernel.  Annoying, the old kernel doesn't show up in Grub menu so I had to change "3" to "2" in the Grub menu to boot.

Another whole pile of updates this evening, "3" boots now, and synaptic came up without a wimper.

Jerry

---

### Post by mc4man on 2012-07-03
The most common, possibly only reason for synaptic not to launch is the above mentioned error (easy to see - if synaptic doesn't launch check tail end of ~/.xsession-errors

In that case has nothing to do with the kernel or even synaptic, when synaptic won't launch from icon other related activities requiring auth from a pop up  will also fail

Also many times this ^ will go away on a log out/in or restart, then re-occur at some point

---

### Post by ventrical on 2012-07-04
> **ronacc said:**
> I give up , installing fvwm-crystal made things even worse for me , I now can't even get an update/upgrade to complete from a text console and as it stands recovery mode is useless . I'll try tomorrows daily and see if thats any better .

Sorry to hear about that ronacc. I thought it would help.

---

### Post by ventrical on 2012-07-04
> **mc4man said:**
> The most common, possibly only reason for synaptic not to launch is the above mentioned error (easy to see - if synaptic doesn't launch check tail end of ~/.xsession-errors

In that case has nothing to do with the kernel or even synaptic, when synaptic won't launch from icon other related activities requiring auth from a pop up  will also fail

Also many times this ^ will go away on a log out/in or restart, then re-occur at some point


How to I get to ./xsession-errors again?

Nautilus is completely dysfunctional.

---

### Post by mc4man on 2012-07-04
> **ventrical said:**
> How to I get to ./xsession-errors again?

Nautilus is completely dysfunctional.

it's a hidden file in your home folder

---

### Post by jerrylamos on 2012-07-04
> **ventrical said:**
> How to I get to ./xsession-errors again?
In a terminal session from home directory you can do:

less .xsession-errors

to browse it, or do

cp .xsession-errors xsession-errors
chmod 666 xsession-errors

to attach the non-hidden xsession-errors to a bug report.

Jerry

---

### Post by cariboo on 2012-07-04
ventrical, try mc in a termial. :-)

---

### Post by ventrical on 2012-07-04
OK.. thanks ... I looked at the file and  it basically has this at the end:

(nautilus:1801): Gtk-CRITICAL **: gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_action_set_sensitive: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1801): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

** (nautilus:1801): CRITICAL **: nautilus_window_get_ui_manager: assertion `NAUTILUS_IS_WINDOW (window)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_ui_manager_remove_ui: assertion `GTK_IS_UI_MANAGER (manager)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_ui_manager_remove_action_group: assertion `GTK_IS_UI_MANAGER (manager)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


But here is the top part of the file:

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
Initializing composite options...done
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
Initializing opengl options...done
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
Initializing decor options...done
compiz (core) - Info: Loading plugin: text
compiz (core) - Info: Starting plugin: text
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: water
compiz (core) - Info: Starting plugin: water
Initializing water options...done
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: put
compiz (core) - Info: Starting plugin: put
Initializing put options...done
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
Initializing vpswitch options...done
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
Initializing gnomecompat options...done
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
Initializing move options...done
compiz (core) - Info: Loading plugin: firepaint
compiz (core) - Info: Starting plugin: firepaint
Initializing firepaint options...done
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
Initializing place options...done
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
Initializing animation options...done
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
Initializing wobbly options...done
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Initializing resize options...done
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
Initializing cube options...done
compiz (core) - Info: Loading plugin: td
compiz (core) - Info: Starting plugin: td
Initializing td options...done
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
Initializing scale options...done
compiz (core) - Info: Loading plugin: scaleaddon
compiz (core) - Info: Starting plugin: scaleaddon
Initializing scaleaddon options...done
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
Initializing expo options...done
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
Initializing rotate options...done
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell

(compiz:1787): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Initializing unityshell options...done
compiz (core) - Warn: Attempted to restack relative to 0x1200007 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x12000d6 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x12000d9 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x12000dc which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x12000e2 which is not a child of the root window or a window compiz owns
compiz (core) - Warn: Attempted to restack relative to 0x12000e5 which is not a child of the root window or a window compiz owns
Setting Update "rain_delay"
Setting Update "title_wave"
Setting Update "speed"
Setting Update "timestep"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_animated"
Setting Update "active_opacity"
Setting Update "inactive_opacity"
Setting Update "zoom_button"
Setting Update "exit_button"
Setting Update "zoom"
Setting Update "keyboard_focus"
Setting Update "execute_command"
Setting Update "alt_tab_prev"
Setting Update "show_minimized_windows"
Setting Update "panel_opacity"
Setting Update "launcher_opacity"
Setting Update "icon_size"
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:2053): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(nautilus:1801): Gtk-CRITICAL **: gtk_label_set_ellipsize: assertion `GTK_IS_LABEL (label)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_widget_get_preferred_size: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_label_set_ellipsize: assertion `GTK_IS_LABEL (label)' failed

(nautilus:1801): Gtk-CRITICAL **: gtk_widget_get_preferred_size: assertion `GTK_IS_WIDGET (widget)' failed

```

and in between is a very large verbose data about the (nautilus:1801):Gtk-CRITICAL

---

### Post by ventrical on 2012-07-04
> **cariboo907 said:**
> ventrical, try mc in a termial. :-)

Thanks for the reminder Cariboo.  Never even thought about that..geesh.

---

### Post by ronacc on 2012-07-04
tried today's daily , installer crashed twice . oh well theres always tomorrow .

---

### Post by DougieFresh4U on 2012-07-04
Synaptic just fine here on 
AMD64 5200 x2core
ATI HD Radeon 3200
complete up to date

---

