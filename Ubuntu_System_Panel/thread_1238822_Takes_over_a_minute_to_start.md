---
title: "Takes over a minute to start"
date: 2009-08-12
forum: Ubuntu System Panel
---

### Post by shuriky on 2009-08-12
First I thought that USP doesn't work. Then I found the details for how to start in a 'window' mode. Well, apparently USP works, but it takes about 80-90 seconds to start. I would say that this is unacceptable for such a vital piece of software.

I'm running 9.04 64bit and enabled Compiz (I don't run it as it interferes too much with redrawing windows and I have problems with scrollbars).

The output in terminal seems normal:

---------------------
Keybinder Loaded
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
Binding USP Menu to Hotkey: <Ctrl><Alt>U

(usp:7877): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
-----------------------

Any ideas on what is happening?

Thanks

---

### Post by Malac on 2009-08-13
Thanks for the report shuriky.
I have never heard of USP taking this long to start before.

Which version are you using, the .deb files from the "New Release" page or SVN or Synaptic launchpad repo ?

Can you check that there is no other instance of the usp process running.
You can do this in a terminal with: ```
killall usp
```Then running:```
usp -w
``` and check the output.
Also open gconf-editor and navigate to /apps/panel/applets and check that you only have one instance  of usp on the panel. There should be one applet with the bonobo_iid:GNOME_USP. This picture is how it should look.
[ATTACH]124707[/ATTACH]
I haven't a 64-bit machine so cannot check usp on this architecture myself but we have had no reports of this from other 64-bit users.
The other thing to try is to run:
```
usp -w applications
``` this just runs usp with the applications plugin but without altering your settings. If that makes a difference then change the plugin name on the command line until the problem happens again and let me know which plugin caused the problem.

Hope this helps.

---

