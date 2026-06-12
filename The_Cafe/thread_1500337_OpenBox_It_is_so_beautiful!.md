---
title: "OpenBox: It is so beautiful!"
date: 2010-06-03
forum: The Cafe
---

### Post by TironN on 2010-06-03
Ok guys, time for a bit of a rant.

I recently have been trying out OpenBox on my netbook as Gnome was just that bit too slow for me. I tried KDE (which was slower) and XFCE (which was ugly) and settled on OpenBox. It's fast, customisable and simple.

It's insanely fast compared to anything else I've used and for a netbook this is the main reason I chose it.

It's customisable to the best level: straight code. Using Obmenu and Obconf I can change almost anything I need or even drop into the hard XML! Also with Tint2 and Conky I have an even further level of choice!

The best feature is it's simplicity. It looks good as its not over the top!


tl;dr: Use OpenBox

---

### Post by dzon65 on 2010-06-03
Started with ubuntu (full),quickly changed nautilus to thunar,replaced the wm with openbox.Change was great.Nowadays only minimal and openbox and all leightweight stuff.Never went back.Solid and fast.Since this is minimal,I use the gnome panel (it's there so why not use it),no need to add any other.
Don't know if you have the shutdownbox,if not,let me know,usefull app.

---

### Post by mexicanseaf00d on 2010-06-03
> **dzon65 said:**
> Started with ubuntu (full),quickly changed nautilus to thunar,replaced the wm with openbox.Change was great.Nowadays only minimal and openbox and all leightweight stuff.Never went back.Solid and fast.Since this is minimal,I use the gnome panel (it's there so why not use it),no need to add any other.
Don't know if you have the shutdownbox,if not,let me know,usefull app.


thunar looks great, especially that media-tags plugin

if i switch from nautilus to it, are there any risks involved (like destroying EVERYTHING)? currently running ubuntu/gnome

---

### Post by wojox on 2010-06-03
> **mexicanseaf00d said:**
> thunar looks great, especially that media-tags plugin

if i switch from nautilus to it, are there any risks involved (like destroying EVERYTHING)? currently running ubuntu/gnome

It shouldn't. Just download it and run it.

---

### Post by dzon65 on 2010-06-03
No,no worries.Here you go:
To cause Thunar to open whenever you click an entry in the Places menu, you&#8217;ll need to edit a configuration file: open a terminal window, and type the following:
gksu gedit /usr/share/applications/nautilus-folder-handler.desktop

Scroll to the bottom of the file, and look for the line that reads Exec=nautilus --no-desktop %U. Change it so it reads Exec=thunar %U. Then save the file, log out and back in again, and test the changes by selecting Places --> Home.

And there you go,thunar as default.It won't handle the computer file though,that's handled by nautilus.But in a way that could be handy if you want to open a file as owner (with nautilus-gksu for example).Keep in mind that thunar doesn't handle desktop.

If you want openbox as wm,it's sufficiant to open system/prefs/sessions and add this "openbox --replace".Logout/in and voila.
Changing those two will speed up things seriously.
Kind regards,J.

---

### Post by mexicanseaf00d on 2010-06-03
wow, thanks for the tip! will check it out :D

---

### Post by Simian Man on 2010-06-03
> **TironN said:**
> XFCE (which was ugly) and settled on OpenBox. It's fast, customisable and simple.

You know Xfce is extremely customizable as well right?  I'm not arguing with your choice, but I don't think you gave Xfce as much of a chance as OpenBox (which I've always found overrated).

---

### Post by dzon65 on 2010-06-03
That openbox replace thing:it's openbox (space)-- replace

---

### Post by Shazzam6999 on 2010-06-03
> **TironN said:**
> Ok guys, time for a bit of a rant.

I recently have been trying out OpenBox on my netbook as Gnome was just that bit too slow for me. I tried KDE (which was slower) and XFCE (which was ugly) and settled on OpenBox. It's fast, customisable and simple.

It's insanely fast compared to anything else I've used and for a netbook this is the main reason I chose it.

It's customisable to the best level: straight code. Using Obmenu and Obconf I can change almost anything I need or even drop into the hard XML! Also with Tint2 and Conky I have an even further level of choice!

The best feature is it's simplicity. It looks good as its not over the top!


tl;dr: Use OpenBox

I think you just copy and pasted my thoughts :). I can never get XFCE to a point where I think it actually looks good, whereas Openbox takes me like 5 minutes tops to configure. It's so simple to configure, looks so good, and works so well. In fact, it works too well, because now I just get annoyed by other WMs. I love tint2 as well, I think it's one of the best looking panels out there and it's also really simple to configure and super lightweight.

---

### Post by cascade9 on 2010-06-03
> **Simian Man said:**
> You know Xfce is extremely customizable as well right?  I'm not arguing with your choice, but I don't think you gave Xfce as much of a chance as OpenBox (which I've always found overrated).

Exactly what I was thinking ;)

---

### Post by Shazzam6999 on 2010-06-03
> **cascade9 said:**
> Exactly what I was thinking ;)
I guess I would say that while XFCE is probably just as customizable, and I've seen some gorgeous XFCE desktops, that he just found everything he wanted in Openbox and it was easier for him. That's how it was for me, it just simpler for me to get Openbox the way I want than it is to get XFCE the way I want. We all have our preferences :).

---

### Post by disabledaccount on 2010-06-03
Enlightment - much faster than xfce, extremely fast desktop effects (even without hw acceleration), fully customizable, reasonable memory footprint - for me it is the best joice in lightweight interfaces.
Openbox, LXDE ... are ok - but only if you have very old, slow machine with insufficient amount of RAM.
I think, that many openbox-like fans are not understanding the basic fact, that those interfaces are getting extremely fat if one have to launch any normal/bigger applcation QT or GTK-based. The Fact is, that simple window managers save resources only if you use simple apps, like conky or terminal.

...and GNOME? KDE? - yes, they are slow and heavy - but also easiest to manage by unexperienced users, very well supported on programmer side (IDE), feature-rich by default -> without messing with scripts, compilations or config files by hand.

...at least we have choice, unlike some others... ;)

---

### Post by dzon65 on 2010-06-03
Never tried enlightment.But openbox/lxde ONLY for old machines?They are one of the best choices for old rigs,that's a fact.Don't think you'll get enlightment running well on,say,something with 256mb ram.Ubuntu/enlightment that is.Might be wrong though.As for the "others".Back in my windows days,did a hell of a lot of tweaking.Just today came across blackbox for windows.
Don't get me wrong,that's waaaaaaaaaayy in the past and ain't never going back.

---

### Post by disabledaccount on 2010-06-03
> **dzon65 said:**
> Never tried enlightment.But openbox/lxde ONLY for old machines?They are one of the best choices for old rigs,that's a fact.Don't think you'll get enlightment running well on,say,something with 256mb ram.
Well, you can of course setup openbox on 4-core machine with 8GB RAM, SLI/CrossFire gfx subsystem that boots from 6xSSD connected to hardware RAID6 controller - but I can assure You will not see any difference in speed, comparing to GNOME or KDE ;)

---

### Post by dzon65 on 2010-06-03
Lol,nuclear pc's.

---

### Post by TironN on 2010-06-04
Sorry XFCE lovers but I just found OpenBox and fell in love.

---

### Post by halovivek on 2010-06-04
How to install in ubuntu 10.04...
Help please

---

### Post by Shazzam6999 on 2010-06-04
Here's the wiki page on it, tells you everything you need to know:
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

---

### Post by T-rock007 on 2010-06-04
It does look pretty good.

---

### Post by RiceMonster on 2010-06-04
I used it for a while. It's ok. Takes a little to much time to configure, I think.

---

### Post by medic2000 on 2010-06-04
> **RiceMonster said:**
> I used it for a while. It's ok. Takes a little to much time to configure, I think.

I concur with that.

---

### Post by dragos240 on 2010-06-04
lSN'T IT BEAUTIFUL?
[IMG]http://www.quebecgamers.com/impressions/cdi/faces_of_evil/animation_fin10.jpg[/IMG]

---

### Post by alexan on 2010-06-04
If you need resource, try this:

**sudo apt-get install jwm menu pcmanfm**


(joe windows manager is the one of puppylinux)

Let pcmanfm manage the desktop.. and you'll really see how fast can run the Lucid Lynx.

---

### Post by mobilediesel on 2010-06-04
> **dzon65 said:**
> Don't know if you have the shutdownbox,if not,let me know,usefull app.
I like the look of that shutdownbox.

I currently use this:
[ATTACH]159345[/ATTACH]

Which is a bit ugly even if it's functional.

---

### Post by dzon65 on 2010-06-05
Here you go.
[http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/](http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/)

As we "speak".Laptop is in for cleaning and I'm on this medieval compaq 5000 (1997 or something),256 mb ram,1,9 Gb hd and an old nvanta card.A minimal/openbox/thunar install.(pcmanfm is hardly usuable,something wrong with it when used in minimal 9.10).Anyway,wouldn't say it flies,but works pretty good.

---

### Post by ibuclaw on 2010-06-05
> **tomazzi said:**
> Enlightment - much faster than xfce, extremely fast desktop effects (even without hw acceleration), fully customizable, reasonable memory footprint - for me it is the best joice in lightweight interfaces.


I tried to like enlightenment (honest) but it's simply too visual for me. :)

I've used Openbox alot, and it's the base of what I've done for Zenix (a distro myself, bodhi and paultag have got in the flux).

My netbook current uses the Unity Shell desktop, and Mutter, while nice, is CPU intensive, sometimes persistently for no obvious reason. And because I care about heat production, wasted process, and the freedom to have smooth rendering videos (Currently my only option is to temporarily switch to Metacity to watch streams) it's gonna have to go soon... Only thing preventing me currently is that I'd like other people to freely use my netbook, if and when needed.

I have a machine with XFCE, it runs well looks nice too, however, not preventing me from making the change some day. ;)

Openbox ftw!

---

### Post by mobilediesel on 2010-06-05
> **dzon65 said:**
> Here you go.
[http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/](http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/)

As we "speak".Laptop is in for cleaning and I'm on this medieval compaq 5000 (1997 or something),256 mb ram,1,9 Gb hd and an old nvanta card.A minimal/openbox/thunar install.(pcmanfm is hardly usuable,something wrong with it when used in minimal 9.10).Anyway,wouldn't say it flies,but works pretty good.

Thank you! That'll look way better than using gmessage from a bash script.

---

### Post by ibuclaw on 2010-06-05
> **dzon65 said:**
> Here you go.
[http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/](http://celettu.wordpress.com/2008/06/01/howto-graphical-logoutshutdownreboot-in-any-window-manager/)

As we "speak".Laptop is in for cleaning and I'm on this medieval compaq 5000 (1997 or something),256 mb ram,1,9 Gb hd and an old nvanta card.A minimal/openbox/thunar install.(pcmanfm is hardly usuable,something wrong with it when used in minimal 9.10).Anyway,wouldn't say it flies,but works pretty good.

BTW, you don't need to use 'sudo shutdown' to shutdown the workstation. You can do it using dbus-send without the need for elevating privileges. :)

---

### Post by dzon65 on 2010-06-05
Be carefull with it though!(sudoers file)
In terminal:sudo visudo
With the down arrow to the bottom and add:

your-name ALL=NOPASSWD: /sbin/shutdown
press enter to leave a empty line under it.
press-> ctrl+x
then-> y
then-> enter

Let's say you want it in your menu.
Obmenu,new item,path to the shutdownbox' py.Save,done.

---

### Post by dzon65 on 2010-06-05
Talking about enlightenment.Downloaded elive/compiz yesterday to give it a spin.695 mb for a demo ?!?! Isn't that distro free?

---

### Post by dzon65 on 2010-06-05
> **RiceMonster said:**
> I used it for a while. It's ok. Takes a little to much time to configure, I think.

Well,not when you use it in gnome.Only thing to do is choose your style.As a standalone,that's another story.But once you get the hang with obmenu,nitrogen (or feh).....it's pretty easy.

---

### Post by bigseb on 2010-06-05
> **dzon65 said:**
> Started with ubuntu (full),quickly changed nautilus to thunar,replaced the wm with openbox.Change was great.Nowadays only minimal and openbox and all leightweight stuff.Never went back.Solid and fast.Since this is minimal,I use the gnome panel (it's there so why not use it),no need to add any other.
Don't know if you have the shutdownbox,if not,let me know,usefull app.
  Tell me, what is that on the right hand side. Looks awesome!

---

### Post by dzon65 on 2010-06-05
Conky?You mean the white/blue/orange thing?That's conky.

---

### Post by bigseb on 2010-06-05
> **dzon65 said:**
> Conky?You mean the white/blue/orange thing?That's conky.

*drools* ... must get Conky...

---

### Post by dzon65 on 2010-06-05
Synaptic>conky
You can get conkyscripts on gnome look.If you want this one,let me know.The scripts,you save as .conkyrc in,say,your home folder.
One easy thing is a conkyswitch.That way you can turn it on/out.
It's very easy to do.Save this as .conkyswitch (or whatever) in your home map (or whereever).
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky

fi

Make it executable (easiest way:rightclick on it>properties>use as a program)(sorry for my english  but you'll figure it out)
Add a new launcher to your panel with a path to where you saved it.

---

### Post by ibuclaw on 2010-06-05
> **ibuclaw said:**
> BTW, you don't need to use 'sudo shutdown' to shutdown the workstation. You can do it using dbus-send without the need for elevating privileges. :)
Took me a while to find...

Suspend:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:1

```
Hibernate:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate

```
Shutdown:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

```
Reboot:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot

```

Regards.

:)

---

### Post by dzon65 on 2010-06-05
Ibuclaw.Posted this once,no replies.Why is it that the ram in conky doesn't show the exact ram being used (shows far more).Someone said it's due to the cache.

Edit:quickly installed one on my old rig.

---

### Post by ibuclaw on 2010-06-05
> **dzon65 said:**
> Ibuclaw.Posted this once,no replies.Why is it that the ram in conky doesn't show the exact ram being used (shows far more).Someone said it's due to the cache.

Edit:quickly installed one on my old rig.

You are correct. Conky includes the shared, buffered and cached memory too.


type in:
```
free -m
```

And you'll see something like:
```

            total       used       free     shared    buffers     cached
Mem:          2004       1905         99          0        263        903
-/+ buffers/cache:        738       1266
Swap:         3624          1       3622

```

On my system, 1905MB of RAM is being used. However, 1166MB are buffered/cached memory. The difference of that comes to 738MB.

Which is correct to what gnome-system-monitor reports (see attachment).

---

### Post by ibuclaw on 2010-06-05
> **ibuclaw said:**
> You are correct. Conky includes the shared, buffered and cached memory too.


What you do is use the following in your .conkyrc
```
no_buffers yes
```
Which should subtract file system buffers from used memory.

---

### Post by bigseb on 2010-06-05
> **dzon65 said:**
> If you want this one,let me know.
I will let you know. First gotta fix my PC though :(

---

### Post by dzon65 on 2010-06-05
> **ibuclaw said:**
> What you do is use the following in your .conkyrc
```
no_buffers yes
```
Which should subtract file system buffers from used memory.

Aha!Thanks man.
kind regards,J.

---

### Post by Shining Arcanine on 2010-06-05
> **TironN said:**
> Ok guys, time for a bit of a rant.

I recently have been trying out OpenBox on my netbook as Gnome was just that bit too slow for me. I tried KDE (which was slower) and XFCE (which was ugly) and settled on OpenBox. It's fast, customisable and simple.

It's insanely fast compared to anything else I've used and for a netbook this is the main reason I chose it.

It's customisable to the best level: straight code. Using Obmenu and Obconf I can change almost anything I need or even drop into the hard XML! Also with Tint2 and Conky I have an even further level of choice!

The best feature is it's simplicity. It looks good as its not over the top!


tl;dr: Use OpenBox

You should try Gentoo Linux on your netbook. All software usually runs faster on Gentoo Linux because it strips bloat out of the binaries that other distributions leave in them.

---

### Post by ibuclaw on 2010-06-05
> **Shining Arcanine said:**
> You should try Gentoo Linux on your netbook. All software usually runs faster on Gentoo Linux because it strips bloat out of the binaries that other distributions leave in them.

Oh dear ... probably best not to go down the -funroll-loops route. ;)

There is absolutely nothing to suggest that Gentoo (or Archlinux) run faster than Ubuntu.

Phoronix [proved this to be the case]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_arch_faster&num=1") with their benchmark testsuite, although Archlinux ever so slightly outperformed in some areas, they concluded it was mostly down to Arch using the much improved GCC-4.5 compiler.

---

### Post by dzon65 on 2010-06-05
Haven't tried arch yet but most say it's quite fast.I always dominimal installs/openbox and the speed is quite impressive.
Fastest I've used is slitaz though.

---

### Post by RiceMonster on 2010-06-05
> **dzon65 said:**
> Well,not when you use it in gnome.Only thing to do is choose your style.As a standalone,that's another story.But once you get the hang with obmenu,nitrogen (or feh).....it's pretty easy.

I used it for 6 months, I know all about it. Even with those tools, I still spent an unnecessary amount of time configuring it. Furthermore, I don't really see what the point in using it with Gnome would be.

---

### Post by Linuxforall on 2010-06-05
> **ibuclaw said:**
> Oh dear ... probably best not to go down the -funroll-loops route. ;)

There is absolutely nothing to suggest that Gentoo (or Archlinux) run faster than Ubuntu.

Phoronix [proved this to be the case]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_arch_faster&num=1") with their benchmark testsuite, although Archlinux ever so slightly outperformed in some areas, they concluded it was mostly down to Arch using the much improved GCC-4.5 compiler.

Fully agreed having run both, I found them to be no faster than Ubuntu. The only place Arch outperformed Ubuntu was in graphics and that was due to Compiz being disabled by default on Arch and enabled by default on Ubuntu.

---

### Post by dzon65 on 2010-06-05
Why not?A minimal install comes with gnome,might as well use it.There's hardly any difference in resources between gnomepanel compared to say lxpanel.I've got the panels autohidden,why would I add another panel to it.Question of taste.

---

### Post by Shining Arcanine on 2010-06-05
> **ibuclaw said:**
> Oh dear ... probably best not to go down the -funroll-loops route. ;)

There is absolutely nothing to suggest that Gentoo (or Archlinux) run faster than Ubuntu.

Phoronix [proved this to be the case]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_arch_faster&num=1") with their benchmark testsuite, although Archlinux ever so slightly outperformed in some areas, they concluded it was mostly down to Arch using the much improved GCC-4.5 compiler.

Various programs and libraries have optional features that you can select when you compile them. On Gentoo Linux, these features are exposed through high level use flags, allowing you to turn them on and off at will. For instance, With certain versions of Chromium, you can turn off support for certain audio/video codecs by specifying the appropriate USE flags. Other things like debug code can also be disabled in many packages with USE flags. USE flags also allow you to trim entire branches of dependencies from software, such as semantic desktop support when building KDE, which has a significant impact on system memory usage. In addition, Gentoo's package manager runs GNU strip on generated binaries, which removes unnecessary code from them.

How could Phoronix have proven that these things have no effect with their test suite when they have not done any benchmarks? Also, why is it that when someone suggests that people use Gentoo Linux for better performance, people such as yourself automatically suggest that doing so involves employing some of the stupidest techniques to employ performance that are possible? My system runs Gentoo Linux and lacks -funroll-loops, which can be beneficial when used in the right places. At the moment, my system CFLAGS are [COLOR="Green"]CFLAGS="-O2 -march=prescott --param l1-cache-size=32 --param l1-cache-line-size=64 --param l2-cache-size=2048 -pipe -fomit-frame-pointer"[/COLOR], which is a long-hand notation for [COLOR="Green"]CFLAGS="-O2 -march=native -pipe -fomit-frame-pointer"[/COLOR] on my system. Since GCC needs to translate -march=native into alternative flags upon every invocation, it introduces a little overhead before things compile and specifying those flags in place of -march=native eliminates that overhead.

---

### Post by Linuxforall on 2010-06-05
> **Shining Arcanine said:**
> Various programs and libraries have optional features that you can select when you compile them. On Gentoo Linux, these features are exposed through high level use flags, allowing you to turn them on and off at will. For instance, With certain versions of Chromium, you can turn off support for certain audio/video codecs by specifying the appropriate USE flags. Other things like debug code can also be disabled in many packages with USE flags. USE flags also allow you to trim entire branches of dependencies from software, such as semantic desktop support when building KDE, which has a significant impact on system memory usage. In addition, Gentoo's package manager runs GNU strip on generated binaries, which removes unnecessary code from them.

How could Phoronix have proven that these things have no effect with their test suite when they have not done any benchmarks?

Phoronix did a test against a fully optimised Gentoo Linux against Ubuntu in past, lets say Gentoo didn't set the benchmarks on fire against Ubuntu, it did have edge on certain tests but thats it, edge, nothing conclusive.

---

### Post by RiceMonster on 2010-06-05
Shining Arcanine, we get it, you like Gentoo.

---

### Post by Shining Arcanine on 2010-06-05
> **Linuxforall said:**
> Phoronix did a test against a fully optimised Gentoo Linux against Ubuntu in past, lets say Gentoo didn't set the benchmarks on fire against Ubuntu, it did have edge on certain tests but thats it, edge, nothing conclusive.

Do you have a link? As far as I know, the only time Phoronix did testing with Gentoo was when they tested Sabayon, which is the equivalent of doing tests on Debian by benchmarking Ubuntu.

There was a site called Linux magazine that did do some tests on Gentoo Linux, but the entire Gentoo Linux community seemed to agree that the system was not properly optimized in the first place.

---

### Post by Shazzam6999 on 2010-06-05
> **Linuxforall said:**
> Phoronix did a test against a fully optimised Gentoo Linux against Ubuntu in past, lets say Gentoo didn't set the benchmarks on fire against Ubuntu, it did have edge on certain tests but thats it, edge, nothing conclusive.

I don't use either Gentoo or Ubuntu so I'm not really concerned with which distro won, but would you happen to have a link? I don't really trust Phoronix and it would be nice to see the actual data.

Someone beat me to the question :p

---

### Post by Linuxforall on 2010-06-05
Sorry it was Linux mag and not Phoronix and here is the benchmark.

[http://www.linux-mag.com/id/7574/1/](http://www.linux-mag.com/id/7574/1/)

---

### Post by Linuxforall on 2010-06-05
> **Shining Arcanine said:**
> Do you have a link? As far as I know, the only time Phoronix did testing with Gentoo was when they tested Sabayon, which is the equivalent of doing tests on Debian by benchmarking Ubuntu.

There was a site called Linux magazine that did do some tests on Gentoo Linux, but the entire Gentoo Linux community seemed to agree that the system was not properly optimized in the first place.

As you can see in this test, optimizations were done regardless of what Gentoo community thinks. I ran a x64 optimized Gentoo distro for a while as a teaching project at my univ, never found it blazingly fast over Ubuntu.

---

### Post by sdennie on 2010-06-05
> **Shining Arcanine said:**
> USE flags also allow you to trim entire branches of dependencies from software, such as semantic desktop support when building KDE, which has a significant impact on system memory usage.


The only thing this is likely to do in real world usage is use less disk space.  Linux already has a low level mechanism in place to take unused pieces of software and data out of memory.  It's called swappiness.  If memory pressure is so high that you'd notice the difference in what you are describing, the kernel would have swapped it to disk if you have a sane swappiness setting.

> 
In addition, Gentoo's package manager runs GNU strip on generated binaries, which removes unnecessary code from them.


```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
$ file `which ls`
/bin/ls: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, **stripped**

```

> 
My system runs Gentoo Linux and lacks -funroll-loops, which can be beneficial when used in the right places. At the moment, my system CFLAGS are [COLOR="Green"]CFLAGS="-O2 -march=prescott --param l1-cache-size=32 --param l1-cache-line-size=64 --param l2-cache-size=2048 -pipe -fomit-frame-pointer"[/COLOR], which is a long-hand notation for [COLOR="Green"]CFLAGS="-O2 -march=native -pipe -fomit-frame-pointer"[/COLOR] on my system. Since GCC needs to translate -march=native into alternative flags upon every invocation, it introduces a little overhead before things compile and specifying those flags in place of -march=native eliminates that overhead.

I will admit, this is a first for me.  You are actually suggesting that you are optimizing your compilation phase by explicitly stating the characteristics of your machine instead of letting it deduce them -march=native?  Can you show me the benchmarks on how much of a difference that makes?

---

### Post by Shining Arcanine on 2010-06-05
> **Linuxforall said:**
> Sorry it was Linux mag and not Phoronix and here is the benchmark.

[http://www.linux-mag.com/id/7574/1/](http://www.linux-mag.com/id/7574/1/)

The testing methodology of those benchmarks was flawed and all Gentoo users appear to be in agreement on this matter:

[http://forums.gentoo.org/viewtopic-t-817950-highlight-.html](http://forums.gentoo.org/viewtopic-t-817950-highlight-.html)

The benchmarks conducted by Linux magazine are more benchmarks of different GCC compiler optimization levels that they happened to run on top of Gentoo Linux than benchmarks of Gentoo Linux.

Any value that the comparison could have had was invalidated by the lack of proper kernel optimizations and the use of different major kernel versions, x servers and nvidia drivers and a different desktop environment.

Distributions tend to be defined by their package managers and repositories, but Gentoo Linux is somewhat unique in that its customizability allows it to match any configuration a static distribution like Ubuntu assumes, allowing for a true comparison of the distribution differences between itself and other distributions. If you do not want something quite that rigorous and only want to benchmarks on the out of box experience, then you still still need to do proper kernel optimization and you would also need to provide the kernel's .config file with the system configuration. Simply saying "I used x kernel version" when doing Gentoo Linux benchmarks is not good enough because the kernel is just as configurable as the rest of the system, but unlike other distributions, Gentoo Linux exposes that to you.

Lastly, while it is not an additional reason to invalidate their results, Linux Magazine claims that they compiled the system toolchain twice and then the rest of the system was compiled twice, between different benchmark runs. This demonstrates a lack of understanding of how Gentoo Linux works, because they should only need to run a recompilation of the entire system one time and the result should be the same as if you had recompiled it a thousand times. The toolchain will generate the same code regardless of the CFLAGS with which it was compiled and if there was a situation in which it did not, the chances are better of a million people being struck by lightning simultaneously than the chances of GCC successfully compiling itself on Gentoo. In every circumstance worth considering, the triple compilation of GCC  will detect any issues with the toolchain not compiling code properly.

---

### Post by ibuclaw on 2010-06-05
Shining Arcade, I will say this again, as you didn't seem to hear the first time.

Please do **not** throw the discussion off-topic.

Now, back to the topic of Openbox, anyone?

---

### Post by Shining Arcanine on 2010-06-05
> **sdennie said:**
> The only thing this is likely to do in real world usage is use less disk space.  Linux already has a low level mechanism in place to take unused pieces of software and data out of memory.  It's called swappiness.  If memory pressure is so high that you'd notice the difference in what you are describing, the kernel would have swapped it to disk if you have a sane swappiness setting.



```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
$ file `which ls`
/bin/ls: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, **stripped**

```



I will admit, this is a first for me.  You are actually suggesting that you are optimizing your compilation phase by explicitly stating the characteristics of your machine instead of letting it deduce them -march=native?  Can you show me the benchmarks on how much of a difference that makes?

Well, I have three things to say here.

The first is that I forgot to mention in my other post that Gentoo Linux is a minimal distribution, so it will only run essential background services in the background by default. Gentoo Linux does not run things like an apparmor firewall in the background by default like Ubuntu does. A fresh Gentoo Linux installation on an x86 system only uses about 25MB of RAM before optional software and services are installed by the user. On average, the sum of these software and services is less than they would be on distribution like Ubuntu that adopts a one glove fits all policy. This leads to a lower system memory footprit, which provides the kernel with more memory to use as a disk cache, which does impact performance.

The second is that the leaner binaries also affect load times (because there is less code to load, especially when dynamic links involving large dependency branches have been eliminated) and the system memory footprint. The lower system memory footprint from having lean binaries also has the same effect on performance that having fewer software and services running does, which is that it provides the kernel with more memory to use as a disk cache, which also improves performance.

The third is that there are no benchmarks comparing use of explicit CFLAGS versus the use of -march=native when doing large compilations. The only information I have regarding it is that there is a small delay incurred by -march=native and that delay is incurred tens  of thousands if not hundreds of thousands of times (ccache statistics show this). Trying to benchmark this effect would likely take more time than it would save, so people just tend to use it because the system CFLAGS are one of those set it and forget it settings. After all, how often is it that people change their systems' CPUs?

---

### Post by Shining Arcanine on 2010-06-05
> **ibuclaw said:**
> Shining Arcade, I will say this again, as you didn't seem to hear the first time.

Please do **not** throw the discussion off-topic.

Now, back to the topic of Openbox, anyone?

You have only said this once and you are the one who mentioned -funroll-loops. I was on topic by suggesting that running Open Box on Gentoo Linux would improve whatever software it is that he wanted to run on it and I have enumerated why.

Also, my handle is Shining Arcanine, not Shining Arcade.

As for Open Box, it is possible that a minimalist distribution like Gentoo Linux would have a smaller memory footprint with a full-blown desktop environment like GNOME than Ubuntu has with Open Box, assuming he is running Open Box on Ubuntu. Using Open Box with a minimalist distribution like Gentoo Linux will only lower the memory footprint further.

---

### Post by Linuxforall on 2010-06-05
Of course the test would always be flawed for Gentoo users when its being compared to Ubuntu ;) now back to Open Box if we can. :)

---

### Post by Sporkman on 2010-06-05
Shining Arcanine is worse about promoting Gentoo than I am about Ubuntu Server! :lol:

As for Openbox, I've tried it before - it's pretty slick, though xfce seems to meet my low-resource needs.

BTW, if anybody needs a fast and rock-solid server distro, I recommend Ubuntu Server. :)

---

### Post by ibuclaw on 2010-06-05
> **Sporkman said:**
> BTW, if anybody needs a fast and rock-solid server distro, I recommend Ubuntu Server. :)

I've always preferred Debian IMO. ;)
Better OpenVZ support, it has.


Anyways ... Woot! Distro coming along nicely:

[[IMG]http://iainbuclaw.files.wordpress.com/2010/05/2010-05-30-002118_1024x600_scrot.png?w=150[/IMG]]("http://iainbuclaw.files.wordpress.com/2010/05/2010-05-30-002118_1024x600_scrot.png")

[[IMG]http://iainbuclaw.files.wordpress.com/2010/05/2010-05-30-200439_1024x600_scrot.png?w=150[/IMG]]("http://iainbuclaw.files.wordpress.com/2010/05/2010-05-30-200439_1024x600_scrot.png")

Uses Openbox for the session and gdm window manager. :)

---

### Post by Shining Arcanine on 2010-06-05
I thought that openbox was a window manager. How do you use it as a session manager?

---

### Post by sdennie on 2010-06-06
> **Shining Arcanine said:**
> Well, I have three things to say here.

The first is that I forgot to mention in my other post that Gentoo Linux is a minimal distribution, so it will only run essential background services in the background by default. Gentoo Linux does not run things like an apparmor firewall in the background by default like Ubuntu does. A fresh Gentoo Linux installation on an x86 system only uses about 25MB of RAM before optional software and services are installed by the user. On average, the sum of these software and services is less than they would be on distribution like Ubuntu that adopts a one glove fits all policy. This leads to a lower system memory footprit, which provides the kernel with more memory to use as a disk cache, which does impact performance.

The second is that the leaner binaries also affect load times (because there is less code to load, especially when dynamic links involving large dependency branches have been eliminated) and the system memory footprint. The lower system memory footprint from having lean binaries also has the same effect on performance that having fewer software and services running does, which is that it provides the kernel with more memory to use as a disk cache, which also improves performance.

The third is that there are no benchmarks comparing use of explicit CFLAGS versus the use of -march=native when doing large compilations. The only information I have regarding it is that there is a small delay incurred by -march=native and that delay is incurred tens  of thousands if not hundreds of thousands of times (ccache statistics show this). Trying to benchmark this effect would likely take more time than it would save, so people just tend to use it because the system CFLAGS are one of those set it and forget it settings. After all, how often is it that people change their systems' CPUs?

Giving high regard to the disk cache is warranted.  However, if you give it such high regard that you'd be willing to compile your entire machine from scratch, if you are compiling everything -O2 and not -Os, you haven't thought it through.  I've built and used LFS machines compiled with -Os and if you are using a spinning disk, yes, it does make a difference.

I think a lot of people have problems with gentoo users because you get a huge amount of automation to get your perceived performance benefits.  You don't have to think about them.  They magically "happen".  Build a machine using one of the LFS guides and you will have a much better understanding of what makes things fast and what makes them slow.

---

### Post by ibuclaw on 2010-06-06
> **Shining Arcanine said:**
> I thought that openbox was a window manager. How do you use it as a session manager?
The details probably aren't exact, but this is how I see it.
The GDM package in Ubuntu is split off into 2, gdm-session and gdm-binary. gdm-binary are just the binaries for gdm, and gdm-session is the "Look and feel" data. gdm-binary recommends gdm-session, gdm-session depends on metacity.

Knowing that, we can:
1) Install gdm-binary **without** gdm-session
2) Create a desktop file for loading Openbox in /usr/share/gdm/autostart/LoginWindow
3) Create an Openbox rc.xml in /var/lib/gdm, as we want to remove some unneeded features (ie: right-click menu, multiple workspaces).
4) Create a .gtkrc-2.0 file for theming gdm, as gdm-session isn't there to do it for us.

The configuration is hosted on Launchpad, you can see it [here]("http://bazaar.launchpad.net/~zenix-shravaka/zenix/zenix-artwork/files/head:/"). Or to point you to the specific files:
[usr/share/gdm/autostart/LoginWindow/zenix.desktop]("http://bazaar.launchpad.net/~zenix-shravaka/zenix/zenix-artwork/annotate/head:/usr/share/gdm/autostart/LoginWindow/zenix.desktop"),
[/usr/share/zenix/gdm.sh]("http://bazaar.launchpad.net/~zenix-shravaka/zenix/zenix-artwork/annotate/head:/usr/share/zenix/gdm.sh"),
[/var/lib/gdm/.gtkrc-2.0]("http://bazaar.launchpad.net/~zenix-shravaka/zenix/zenix-artwork/annotate/head:/var/lib/gdm/.gtkrc-2.0"), and
[/var/lib/gdm/.config/openbox/rc.xml]("http://bazaar.launchpad.net/~zenix-shravaka/zenix/zenix-artwork/annotate/head:/var/lib/gdm/.config/openbox/rc.xml"). :)

> **sdennie said:**
> Giving high regard to the disk cache is warranted.  However, if you give it such high regard that you'd be willing to compile your entire machine from scratch, if you are compiling everything -O2 and not -Os, you haven't thought it through.  I've built and used LFS machines compiled with -Os and if you are using a spinning disk, yes, it does make a difference.

I think a lot of people have problems with gentoo users because you get a huge amount of automation to get your perceived performance benefits.  You don't have to think about them.  They magically "happen".  Build a machine using one of the LFS guides and you will have a much better understanding of what makes things fast and what makes them slow.

Actually, (we have discussed this before, remember? :)) Kernels optimised for space (cache usage, essentially) is no longer true with modern processors and that one can improve performance by as much as 8% by using GCC -O2 performance optimisation flags and allowing the CPU to deal with cache pre-fetching itself.

---

### Post by dzon65 on 2010-06-06
Guys.Regardless all thread spin-offs.For those "newbies"(like myself).Is openbox worth the try?It is.

---

### Post by Shining Arcanine on 2010-06-06
> **ibuclaw said:**
> Actually, (we have discussed this before, remember? :)) Kernels optimised for space (cache usage, essentially) is no longer true with modern processors and that one can improve performance by as much as 8% by using GCC -O2 performance optimisation flags and allowing the CPU to deal with cache pre-fetching itself.

I would like to add that it depends on the CPU. Recent CPUs like the Core 2 and its successors benefit more from -O2 than they do from -Os. Older processors are the reverse. While it is not a kernel option and I have not explicitly benchmarked the effect, I suspect that on systems with large amounts of cache (e.g. Core 2 Quad Q9550, which is what I use), -O3 is actually faster than -O2. I say this because of two Gentoo Linux virtual machines I used to keep alongside one another. One was a 32-bit x86 virtual machine compiled with -O2 and the other was a 64-bit x86 virtual machine compiled with -O3. The 64-bit machine ran circles around the 32-bit machine when doing system compilations and the only differences were the instruction set and CFLAGS. It has not been worth my time to try two different 64-bit machines with -O2 being the only difference, but I suspect that if I do, I will find having -O3 brings a significant speed-up, which I believe is caused by the incredibly large cache present on my system's processor.

> **dzon65 said:**
> Guys.Regardless all thread spin-offs.For those "newbies"(like myself).Is openbox worth the try?It is.

This is one of those things where if you need to ask, the answer is  probably no, so probably not. Most people here are not as interested in tinkering with their systems and assuming you run Ubuntu, doing this would likely go outside of an officially supported configuration, which most people here would likely want to avoid doing.

---

### Post by aeiah on 2010-06-06
i was gonna go with openbox when i installed 10.04 minimal, but decided on gnome in the end. i really wanted openbox, but i wanted a file manager that had ssh, custom actions and tabs, so i ended up settling for nautilus. if i have nautilus, i might as well use gnome...

how i wish pcmanfm had custom actions :(

---

### Post by dzon65 on 2010-06-06
> **Shining Arcanine said:**
> I would like to add that it depends on the CPU. Recent CPUs like the Core 2 and its successors benefit more from -O2 than they do from -Os. Older processors are the reverse. While it is not a kernel option and I have not explicitly benchmarked the effect, I suspect that on systems with large amounts of cache (e.g. Core 2 Quad Q9550, which is what I use), -O3 is actually faster than -O2. I say this because of two Gentoo Linux virtual machines I used to keep alongside one another. One was a 32-bit x86 virtual machine compiled with -O2 and the other was a 64-bit x86 virtual machine compiled with -O3. The 64-bit machine ran circles around the 32-bit machine when doing system compilations and the only differences were the instruction set and CFLAGS. It has not been worth my time to try two different 64-bit machines with -O2 being the only difference, but I suspect that if I do, I will find having -O3 brings a significant speed-up, which I believe is caused by the incredibly large cache present on my system's processor.



This is one of those things where if you need to ask, the answer is  probably no, so probably not. Most people here are not as interested in tinkering with their systems and assuming you run Ubuntu, doing this would likely go outside of an officially supported configuration, which most people here would likely want to avoid doing.

That's up to them to decide.The thread was about someone being happy with openbox in the first place,so he/she already tinkered his/her system.

---

### Post by Linuxforall on 2010-06-06
The i7 extreme Gentoo PC at our univ boots slower than my slower dual xeon PC at home, I also don't find it any snappier than the plain vanilla Ubuntu PC here, it does compile a bit faster but then thats expected from a PC with that CPU. 

Anyways, lets talk about Open Box here, not Gentoo.

---

### Post by Shining Arcanine on 2010-06-06
ibuclaw was talking about the effects that -Os and -O2 have on performance. Although my experience in the area is based on stuff done on Gentoo Linux, it is not specific to Gentoo Linux.

Anyway, I agree about talking about Open Box instead of compiler optimizations. A certain someone here should know that I have been maintaining a long running private message conversation with him on a related topic to avoid bringing this thread offtopic. :/

---

### Post by Linuxforall on 2010-06-06
Defintely so lets stick to the topic and stop peddling Gentoo here, this is Ubuntu forum, if we wanted Gentoo, we would be there, obviously most of us don't find the need for it and are happy with what Ubuntu offers here.

---

