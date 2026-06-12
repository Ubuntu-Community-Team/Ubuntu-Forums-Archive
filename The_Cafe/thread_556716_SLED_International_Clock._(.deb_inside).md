---
title: "SLED International Clock. (.deb inside)"
date: 2007-09-21
forum: The Cafe
---

### Post by MetalMusicAddict on 2007-09-21
Some have asked for it so here's a proper **_Gutsy_** .deb built properly (no checkinstall) by one of the Ubuntu Studio packagers.

Used [https://launchpad.net/intlclock](https://launchpad.net/intlclock) as the source. This is great for people working on projects where people are spread out. :)

For people who want to build it yourself the build-deps are: debhelper (>= 5), autotools-dev, libedataserverui1.2-dev, libecal1.2-dev, libpanel-applet2-dev, librsvg2-dev, libxml-parser-perl

---

### Post by starcraft.man on 2007-09-21
Looks neat, will give it a go when I install the Gutsy Beta on Thursday (hosed my Alpha yesterday so I'm just waiting a few days).

Anyway, thanks in advance :D.

---

### Post by Nano Geek on 2007-09-21
Could you tell me what the build-deps are for this?
Thanks

---

### Post by MetalMusicAddict on 2007-09-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> Could you tell me what the build-deps are for this?
Thanks

I can't ATM but I can have them posted tomorrow. You need it to build a Feisty .deb?

---

### Post by Nano Geek on 2007-09-21
> **MetalMusicAddict said:**
> I can't ATM but I can have them posted tomorrow. You need it to build a Feisty .deb?No, I would just like to know so I could build it from source. 
Thanks

---

### Post by MetalMusicAddict on 2007-09-21
Build-Depends: debhelper (>= 5), autotools-dev, libedataserverui1.2-dev, libecal1.2-dev, libpanel-applet2-dev, librsvg2-dev, libxml-parser-perl

---

### Post by Nano Geek on 2007-09-21
Hey, thanks a lot.
:guitar:

---

### Post by Lord Illidan on 2007-09-26
How did you get it to compile? In this thread, : [http://ubuntuforums.org/showthread.php?p=3428689](http://ubuntuforums.org/showthread.php?p=3428689) I couldn't get it to even ./configure

---

### Post by 23meg on 2007-09-26
Doesn't work in my Gutsy installation; nothing new appears in the "Add To Panel" window.

---

### Post by Lord Illidan on 2007-09-26
> **23meg said:**
> Doesn't work in my Gutsy installation; nothing new appears in the "Add To Panel" window.

Delete your clock, and look for International Clock under Miscellaneous.

---

### Post by 23meg on 2007-09-26
No, there's no such thing.

---

### Post by Lord Illidan on 2007-09-26
I dunno ](*,)

Come on, 23meg, you know the rules, give us more information to work on :P

---

### Post by Forlong on 2007-09-26
> **23meg said:**
> No, there's no such thing.
You're sure it installed fine? What gives
```
dpkg -l | grep intlclock
```

---

### Post by | MM | on 2007-09-26
@23meg

This is what i had to do...

Delete your old clock.  add clock again.

Bring up the clock preferences (right click preferences) > Locations tab

Check box affirm: Show locations and show map.


Voila!

---

### Post by 23meg on 2007-09-26
> **Forlong said:**
> You're sure it installed fine? What gives
```
dpkg -l | grep intlclock
```
Yes.
```
ii  intlclock                                  1.0-1ubuntu0                  a world clock applet for the GNOME desktop.

```

---

### Post by 23meg on 2007-09-26
> **| MM | said:**
> @23meg

This is what i had to do...

Delete your old clock.  add clock again.

Bring up the clock preferences (right click preferences) > Locations tab

Check box affirm: Show locations and show map.


Voila!

There's no "Locations" tab, since I don't have the new applet anywhere, just the old Clock applet.

---

### Post by b0nz0 on 2007-09-26
You must killall gnome-panel and after international clock appears in Miscellaneus.

---

### Post by 23meg on 2007-09-26
I did try that, but it didn't help. 

I rebooted, and it works now. Probably to do with Bonobo.

---

### Post by Lord Illidan on 2007-09-26
> **b0nz0 said:**
> You must killall gnome-panel and after international clock appears in Miscellaneus.
I didn't have to do that...strange eh!

---

### Post by Nano Geek on 2007-09-26
Could someone tell me how they got it to compile in Gutsy? I have tried and tried, and it crashes on ./configure. ```
configure: error: cannot run /bin/bash ./config.sub
```I would greatly apreciate it if someone could point me in the right direction.

Thanks

---

### Post by Forlong on 2007-09-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> Could someone tell me how they got it to compile in Gutsy? I have tried and tried, and it crashes on ./configure. ```
configure: error: cannot run /bin/bash ./config.sub
```
Yeah, we already had this in the other thread. The current code seems to lack certain files.
You'll just have to wait till it gets updated - it has alrready been reported btw: [https://answers.launchpad.net/intlclock/+question/14020](https://answers.launchpad.net/intlclock/+question/14020)

---

### Post by Nano Geek on 2007-09-26
> **Forlong said:**
> Yeah, we already had this in the other thread. The current code seems to lack certain files.
You'll just have to wait till it gets updated - it has alrready been reported btw: [https://answers.launchpad.net/intlclock/+question/14020](https://answers.launchpad.net/intlclock/+question/14020)I wonder how the OP compiled it then?

---

### Post by Forlong on 2007-09-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> I wonder how the OP compiled it then?
That was four days ago, bazaar code gets usually updated on a daily basis.

---

### Post by Lord Illidan on 2007-09-26
> **Forlong said:**
> Yeah, we already had this in the other thread. The current code seems to lack certain files.
You'll just have to wait till it gets updated - it has alrready been reported btw: [https://answers.launchpad.net/intlclock/+question/14020](https://answers.launchpad.net/intlclock/+question/14020)

Yes, I took the liberty of reporting it. Perhaps the OP managed to get it to compile?

---

### Post by Lord Illidan on 2007-09-26
> **Forlong said:**
> That was four days ago, bazaar code gets usually updated on a daily basis.

But the most recent commit here was 5 days ago : [https://code.launchpad.net/intlclock/](https://code.launchpad.net/intlclock/)

---

### Post by Forlong on 2007-09-26
> **Lord Illidan said:**
> But the most recent commit here was 5 days ago : [https://code.launchpad.net/intlclock/](https://code.launchpad.net/intlclock/)
Then he compiled it two days before he posted here (sorry, I'm running out of ideas :mrgreen:)

---

### Post by MetalMusicAddict on 2007-09-26
Ill get my guy to look at this and make a new .deb if need be.

Also, word on the street is this will be in Gnome 2.22.

---

### Post by ButteBlues on 2007-09-26
Works on my Gutsy.  No need to reboot or anything.

---

### Post by subzero1266 on 2007-09-29
is there any way to install this on feisty? thanks :)

---

### Post by n3tfury on 2007-09-29
how configurable size-wise is this?  the measly screenshot on the launchpad site doesn't show much other than it looks massive on the desktop.  can anybody provide a decent screenshot?

---

### Post by subzero1266 on 2007-09-29
> **n3tfury said:**
> how configurable size-wise is this?  the measly screenshot on the launchpad site doesn't show much other than it looks massive on the desktop.  can anybody provide a decent screenshot?

There's one here - [http://news.opensuse.org/wp-content/uploads/2007/09/evolution-attachment-notification1.png](http://news.opensuse.org/wp-content/uploads/2007/09/evolution-attachment-notification1.png)

---

### Post by Forlong on 2007-09-29
> **n3tfury said:**
> can anybody provide a decent screenshot?
[http://ubuntuforums.org/showthread.php?p=3428731#post3428731](http://ubuntuforums.org/showthread.php?p=3428731#post3428731)

---

### Post by n3tfury on 2007-09-29
thanks guys!  i think i'll see if there's a conky script that does the same.  that's a bit too big for me.

---

### Post by Lord Illidan on 2007-10-04
All those having trouble compiling :

before running configure, run :

```
automake --add-missing
```

Thanks to Flavio De Costa who answered my question here : [https://answers.launchpad.net/intlclock/+question/14020](https://answers.launchpad.net/intlclock/+question/14020)

---

### Post by 23meg on 2007-10-04
[According to Jorge Castro]("http://stompbox.typepad.com/blog/2007/10/jorge-castro-in.html"), the enhancements to the applet will go upstream in the next GNOME release.

---

### Post by Erunno on 2007-10-04
Stop! In the name of freedom! Don't use this extension. It has been paid for with dirty Micro$haft money by the Linux hating/user betraying/puppy hurting Novell. Quickly, somebody start a petition so that GNOME refuses this M$ tainted piece of code upstream.

---

### Post by Lord Illidan on 2007-10-04
> **Erunno said:**
> Stop! In the name of freedom! Don't use this extension. It has been paid for with dirty Micro$haft money by the Linux hating/user betraying/puppy hurting Novell. Quickly, somebody start a petition so that GNOME refuses this M$ tainted piece of code upstream.

Then, why the heck are you using OpenSuse?

---

### Post by Lord Illidan on 2007-10-04
Whew..getting all these make errors!

```
gcc -DHAVE_CONFIG_H -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/librsvg-2 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0   -DGNOMELOCALEDIR=\"/usr/local/share/locale\" -DEVOLUTION_TEXTDOMAIN=\"evolution-2.6\" -DINTLCLOCK_TEXTDOMAIN=\"gnome-panel-2.0\" -DINTLCLOCK_ICONDIR=\"/usr/local/share/intlclock\" -DINTLCLOCK_DATADIR=\"/usr/local/share/intlclock\" -DSYSTEM_ZONEINFODIR=\"/usr/share/zoneinfo\"    -g -O2 -MT intlclock-ui.o -MD -MP -MF .deps/intlclock-ui.Tpo -c -o intlclock-ui.o intlclock-ui.c
intlclock-ui.c:11:25: error: glade/glade.h: No such file or directory
intlclock-ui.c:72: error: expected specifier-qualifier-list before ‘GladeXML’
intlclock-ui.c: In function ‘intlclock_ui_is_12hr’:
intlclock-ui.c:188: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c: In function ‘intlclock_ui_reset_timeout’:
intlclock-ui.c:210: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:210: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:211: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:213: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c: In function ‘panel_button_clicked_cb’:
intlclock-ui.c:225: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:236: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:240: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:242: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c: In function ‘position_popup_window’:
intlclock-ui.c:317: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘intlclock_reposition_events_window’:
intlclock-ui.c:368: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:369: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c: In function ‘intlclock_window_expose_cb’:
intlclock-ui.c:425: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:425: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:427: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:427: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:439: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:442: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:443: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:444: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:445: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:460: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:460: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:461: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:461: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:473: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:476: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:477: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:477: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:481: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:481: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:482: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:482: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:495: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:498: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:499: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:499: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:503: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:503: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:504: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:504: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c: In function ‘intlclock_ui_tick’:
intlclock-ui.c:525: error: ‘IntlClockUIPrivate’ has no member named ‘running’
intlclock-ui.c: In function ‘intlclock_ui_locations_changed’:
intlclock-ui.c:536: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c: In function ‘update_panel_label’:
intlclock-ui.c:554: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:555: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:556: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:557: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:558: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:560: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:570: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:572: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:573: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:576: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:576: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c: In function ‘create_panel_buttons’:
intlclock-ui.c:588: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:593: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:597: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:600: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:601: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:602: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:606: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:607: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:610: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:611: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:615: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:616: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:620: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:621: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:627: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:630: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:631: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:633: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:637: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:641: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:644: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:646: error: ‘IntlClockUIPrivate’ has no member named ‘running’
intlclock-ui.c:657: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:659: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:661: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:661: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:664: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:665: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:667: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c: In function ‘intlclock_ui_change_orient’:
intlclock-ui.c:677: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:678: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c: In function ‘create_panel_button_popup’:
intlclock-ui.c:689: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:691: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:698: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:700: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘create_events_window’:
intlclock-ui.c:718: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:719: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:719: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:721: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:724: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c: In function ‘create_clock_window’:
intlclock-ui.c:734: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:735: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:736: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c: In function ‘create_main_section’:
intlclock-ui.c:748: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:749: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:751: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:753: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:754: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:757: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:762: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c: In function ‘create_cities_section’:
intlclock-ui.c:837: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:838: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:839: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:842: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:846: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:847: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:849: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:853: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:886: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:888: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:897: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:898: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:900: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c: In function ‘create_map_section’:
intlclock-ui.c:909: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:910: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:911: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:914: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:918: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:920: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:921: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:923: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:923: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:925: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:926: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:928: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:931: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:932: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c: In function ‘create_cities_store’:
intlclock-ui.c:940: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:943: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:944: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:945: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:949: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:959: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:960: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:969: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:971: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:971: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:973: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c: In function ‘intlclock_prefs_hide’:
intlclock-ui.c:983: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:985: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:985: warning: assignment makes pointer from integer without a cast
intlclock-ui.c: In function ‘intlclock_edit_clear’:
intlclock-ui.c:1004: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1004: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1006: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1006: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1007: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1007: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1009: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1009: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1010: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1010: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1011: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1011: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:1012: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1012: warning: initialization makes pointer from integer without a cast
intlclock-ui.c: In function ‘intlclock_edit_hide’:
intlclock-ui.c:1031: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1031: warning: initialization makes pointer from integer without a cast
intlclock-ui.c: In function ‘set_12hr_format_radio_cb’:
intlclock-ui.c:1060: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘set_date_check_cb’:
intlclock-ui.c:1069: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘set_seconds_check_cb’:
intlclock-ui.c:1080: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘set_locations_check_cb’:
intlclock-ui.c:1091: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘set_map_check_cb’:
intlclock-ui.c:1102: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘fill_prefs_window’:
intlclock-ui.c:1118: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1118: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1122: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:1123: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1123: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1128: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1128: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1131: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:1134: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1134: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1135: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:1140: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1140: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1141: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:1146: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1146: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1147: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:1152: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1152: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1165: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c: In function ‘display_prefs_window’:
intlclock-ui.c:1194: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:1195: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:1196: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1199: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1199: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1202: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1202: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1204: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_locations’
intlclock-ui.c:1205: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1207: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:1217: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1217: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1223: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1223: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1229: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1229: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1234: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1235: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1242: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1242: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1245: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1245: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1247: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1247: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1268: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c: In function ‘intlclock_ui_change_background’:
intlclock-ui.c:1283: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1285: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1292: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1296: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1300: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘intlclock_ui_new’:
intlclock-ui.c:1316: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1319: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1320: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1322: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1324: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1337: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:1341: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:1343: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c: In function ‘intlclock_ui_init’:
intlclock-ui.c:1368: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1370: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1371: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1373: error: ‘IntlClockUIPrivate’ has no member named ‘panel_box’
intlclock-ui.c:1374: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button’
intlclock-ui.c:1375: error: ‘IntlClockUIPrivate’ has no member named ‘panel_label’
intlclock-ui.c:1377: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:1379: error: ‘IntlClockUIPrivate’ has no member named ‘panel_button_popup’
intlclock-ui.c:1381: error: ‘IntlClockUIPrivate’ has no member named ‘clock_vbox’
intlclock-ui.c:1383: error: ‘IntlClockUIPrivate’ has no member named ‘main_section’
intlclock-ui.c:1384: error: ‘IntlClockUIPrivate’ has no member named ‘clock_calendar’
intlclock-ui.c:1386: error: ‘IntlClockUIPrivate’ has no member named ‘cities_section’
intlclock-ui.c:1388: error: ‘IntlClockUIPrivate’ has no member named ‘map_section’
intlclock-ui.c:1389: error: ‘IntlClockUIPrivate’ has no member named ‘map_widget’
intlclock-ui.c:1391: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:1393: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:1395: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:1396: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:1398: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_window’
intlclock-ui.c:1400: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:1401: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:1402: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:1403: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_week’
intlclock-ui.c:1406: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c: In function ‘intlclock_ui_finalize’:
intlclock-ui.c:1418: error: ‘IntlClockUIPrivate’ has no member named ‘running’
intlclock-ui.c:1420: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1424: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1425: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1426: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1429: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1430: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1431: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1434: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1436: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1439: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:1440: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:1441: error: ‘IntlClockUIPrivate’ has no member named ‘panel_tips’
intlclock-ui.c:1444: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:1445: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:1446: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:1451: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c: In function ‘gconf_hours_changed’:
intlclock-ui.c:1481: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:1484: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c: In function ‘gconf_show_seconds_changed’:
intlclock-ui.c:1506: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:1508: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1508: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1510: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c: In function ‘gconf_show_date_changed’:
intlclock-ui.c:1532: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:1534: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1534: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1536: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c: In function ‘gconf_show_week_changed’:
intlclock-ui.c:1557: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_week’
intlclock-ui.c:1560: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_week’
intlclock-ui.c:1562: error: ‘IntlClockUIPrivate’ has no member named ‘clock_calendar’
intlclock-ui.c:1564: error: ‘IntlClockUIPrivate’ has no member named ‘clock_calendar’
intlclock-ui.c:1566: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_week’
intlclock-ui.c:1572: error: ‘IntlClockUIPrivate’ has no member named ‘clock_calendar’
intlclock-ui.c: In function ‘gconf_show_locations_changed’:
intlclock-ui.c:1592: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:1594: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1594: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1596: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c: In function ‘gconf_show_map_changed’:
intlclock-ui.c:1617: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:1619: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:1619: warning: assignment makes pointer from integer without a cast
intlclock-ui.c:1621: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c: In function ‘gconf_cities_changed’:
intlclock-ui.c:1727: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c: In function ‘intlclock_ui_save_cities_store’:
intlclock-ui.c:1758: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:1770: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘setup_gconf’:
intlclock-ui.c:1793: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1796: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1798: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1806: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1807: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1815: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1816: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1824: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1825: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1833: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1834: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1842: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1843: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c:1851: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1852: error: ‘IntlClockUIPrivate’ has no member named ‘listeners’
intlclock-ui.c: In function ‘load_gconf_settings’:
intlclock-ui.c:1873: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1884: error: ‘IntlClockUIPrivate’ has no member named ‘format_12hr’
intlclock-ui.c:1886: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_seconds’
intlclock-ui.c:1887: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1890: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_date’
intlclock-ui.c:1891: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1894: error: ‘IntlClockUIPrivate’ has no member named ‘format_show_week’
intlclock-ui.c:1895: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1898: error: ‘IntlClockUIPrivate’ has no member named ‘show_locations’
intlclock-ui.c:1899: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1902: error: ‘IntlClockUIPrivate’ has no member named ‘show_map’
intlclock-ui.c:1903: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1906: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c:1915: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c: In function ‘run_time_configuration’:
intlclock-ui.c:1967: error: ‘IntlClockUIPrivate’ has no member named ‘events_window’
intlclock-ui.c:1971: error: ‘IntlClockUIPrivate’ has no member named ‘panel_applet’
intlclock-ui.c: In function ‘remove_tree_row’:
intlclock-ui.c:2039: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:2045: error: ‘IntlClockUIPrivate’ has no member named ‘cities_store’
intlclock-ui.c:2046: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c: In function ‘zone_combo_changed’:
intlclock-ui.c:2056: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:2063: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2063: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2065: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2065: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2067: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2067: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2069: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2069: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2071: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2071: warning: initialization makes pointer from integer without a cast
intlclock-ui.c: In function ‘fill_timezone_combo_from_location’:
intlclock-ui.c:2129: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c: In function ‘edit_tree_row’:
intlclock-ui.c:2204: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2204: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2206: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2206: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2208: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2208: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2210: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2210: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2212: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2212: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2214: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2214: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2216: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2216: warning: initialization makes pointer from integer without a cast
intlclock-ui.c: In function ‘run_prefs_locations_remove’:
intlclock-ui.c:2257: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_locations’
intlclock-ui.c:2258: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_locations’
intlclock-ui.c: In function ‘run_prefs_locations_add’:
intlclock-ui.c:2268: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2268: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2269: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2269: warning: initialization makes pointer from integer without a cast
intlclock-ui.c: In function ‘run_prefs_locations_edit’:
intlclock-ui.c:2282: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_locations’
intlclock-ui.c:2283: error: ‘IntlClockUIPrivate’ has no member named ‘prefs_locations’
intlclock-ui.c: In function ‘run_prefs_edit_save’:
intlclock-ui.c:2292: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2293: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2294: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:2298: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2298: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2299: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2299: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2301: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2301: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2302: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2302: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2303: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2303: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2304: error: ‘IntlClockUIPrivate’ has no member named ‘glade_xml’
intlclock-ui.c:2304: warning: initialization makes pointer from integer without a cast
intlclock-ui.c:2337: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
intlclock-ui.c:2339: error: ‘IntlClockUIPrivate’ has no member named ‘clock’
make[3]: *** [intlclock-ui.o] Error 1
make[3]: Leaving directory `/home/jean/software/intlclock/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jean/software/intlclock/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jean/software/intlclock'
make: *** [all] Error 2

```

---

### Post by Erunno on 2007-10-04
> **Lord Illidan said:**
> Then, why the heck are you using OpenSuse?

Infiltration.

---

### Post by ButteBlues on 2007-10-06
> **Erunno said:**
> Stop! In the name of freedom! Don't use this extension. It has been paid for with dirty Micro$haft money by the Linux hating/user betraying/puppy hurting Novell. Quickly, somebody start a petition so that GNOME refuses this M$ tainted piece of code upstream.
Novell is also responsible for finally taking out SCO - a group that caused far more harm to the Linux/UNIX communities than Microsoft ever has.

If you're into conspiracy theories, go waste your time chasing big foot rather than ranting about Novell.

---

### Post by Forlong on 2007-10-06
Come on, he was obviously being sarcastic.

---

### Post by Lord Illidan on 2007-10-06
I listed a few launchpad pages which might help people wanting to compile it from scratch..

[https://answers.launchpad.net/intlclock/+question/14020](https://answers.launchpad.net/intlclock/+question/14020)
[https://answers.launchpad.net/intlclock/+question/14531](https://answers.launchpad.net/intlclock/+question/14531)

---

### Post by Forlong on 2007-10-06
Thanks for your effort! I'll give it a try later.
Although I have to say I'm pretty satisfied with the deb :)

---

### Post by Lord Illidan on 2007-10-06
> **Forlong said:**
> Thanks for your effort! I'll give it a try later.
Although I have to say I'm pretty satisfied with the deb :)

Sure, but it will soon be outdated..

---

### Post by sailor2001 on 2007-10-06
[http://www.poodwaddle.com/worldclock.swf](http://www.poodwaddle.com/worldclock.swf)

---

### Post by sunny_nwho on 2007-10-09
cool works great on my gusty..i removed the old clock applet:guitar:

---

### Post by motang on 2007-10-26
> **MetalMusicAddict said:**
> Some have asked for it so here's a proper **_Gutsy_** .deb built properly (no checkinstall) by one of the Ubuntu Studio packagers.

Used [https://launchpad.net/intlclock](https://launchpad.net/intlclock) as the source. This is great for people working on projects where people are spread out. :)

For people who want to build it yourself the build-deps are: debhelper (>= 5), autotools-dev, libedataserverui1.2-dev, libecal1.2-dev, libpanel-applet2-dev, librsvg2-dev, libxml-parser-perl

Sweet works well thanks. :-D

---

### Post by phyrewall on 2007-10-28
Works great for me. Only issue I have so far is you can't use & in the place name (the location name won't show up on the clock...?).  e.g. "Mom & Dad"

I changed the broken link on the UbuntuGuide.org wiki to this thread, I hope to OP doesn't mind.

Great applet, nice job deb'ing it. Any chance this will get repo'd/updates?

---

### Post by Youresorock on 2007-11-12
Installed fine for me, easy to add to panel, but it crashes when I try to add Asia/Tokyo.

---

### Post by skyspam on 2007-11-15
make sure you have your old clock off the panel, or it will crash when you try to add places.

---

### Post by graabein on 2008-01-08
How do I get this on Ubuntu 7.10?

---

### Post by Forlong on 2008-01-08
The deb attached in the first post is for 7.10

---

### Post by Vinno on 2008-02-03
Meh no 64bit version deb for gutsy?

---

### Post by RebounD11 on 2008-02-03
I had this in OpenSuSE and I didn't know what it's name was :D Thanx

---

### Post by Grone1985 on 2008-02-05
> **Vinno said:**
> Meh no 64bit version deb for gutsy?

On this page:
[https://edge.launchpad.net/~jorge/+archive]("https://edge.launchpad.net/~jorge/+archive")

There's one if you press that white arrow in the bottom, it will show you a list of packages and you'll see what you're looking for.

Cheers!

---

