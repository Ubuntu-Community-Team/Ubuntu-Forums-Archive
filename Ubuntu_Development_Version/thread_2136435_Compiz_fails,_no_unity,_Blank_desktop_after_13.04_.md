---
title: "Compiz fails, no unity, Blank desktop after 13.04 update"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by bogan on 2013-04-17
**Hi!,**
On my second day with Raring Ringtail I booted normally and ran the updates, which I think included some for Compiz, and a reboot was requested.
 
It rebooted to an normal GUI Desktop with chosen background, top panel and greeter login window. Logging in to Ubuntu gave a Blank screen with no panel or launcher; after a pause a window announced the Network was connected.

'Ctrl+Alt+t' gave a terminal and echo $DESKTOP_SESSION gave: "ubuntu".
 
In the course of many reboots I had several 'System failures' for Compiz and unity-greeter, amongst others. ```
setsid unity # did nothing
sudo apt-get install -f # also did nothing
dpkg-reconfigure -a # gave an interactive display
```ending with a list of what appeared to be Compiz failures or errors.

Rebooting from 'Recovery>Resume Normal Boot' gave the same result, as did 'Ctrl+Alt+F1 startx',  or ' lightdm stop'  and  'restart'.
 
Right Clicking on the Desktop gave access to  Additional Drivers but the window had no buttons, or menus, nor size function, so I could not tell which version was which, and as I have not installed any video drivers it is running Nouveau on my GT 520 Nvidia card.```
apt-cache policy unity # returns:"Installed: 7.0.0daily13.04.15..." So it is not due to that reported Bug.
```In my notes I have a command to reset Compiz, but it is not complete:```
dconf reset -f /org/compiz/
# Edited typo 'reset was omitted here, not in original
```This I got from:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)
But it requires a PATH, either a Key or a Dir, Edit: presumably error was because /org/compiz/ does not exist ??

 Would someone please tell me what 'PATH' to add? I have a separate /Home partition.

Or what else to try?

 After rebooting and logging in to Gnome Classic(no effects) a normal Desktop resulted, so it is not a video driver problem.Edit: But see later Post.
 
 Chao!,** bogan**.

---

### Post by ventrical on 2013-04-17
> **bogan said:**
> **Hi!,**
On my second day with Raring Ringtail I booted normally and ran the updates, which I think included some for Compiz, and a reboot was requested.
 
It rebooted to an normal GUI Desktop with chosen background, top panel and greeter login window. Logging in to Ubuntu gave a Blank screen with no panel or launcher; after a pause a window announced the Network was connected.

'Ctrl+Alt+t' gave a terminal and echo $DESKTOP_SESSION gave: "ubuntu".
 
In the course of many reboots I had several 'System failures' for Compiz and unity-greeter, amongst others. ```
setsid unity # did nothing
sudo apt-get install -f # also did nothing
dpkg-reconfigure -a # gave an interactive display
```ending with a list of what appeared to be Compiz failures or errors.

Rebooting from 'Recovery>Resume Normal Boot' gave the same result, as did 'Ctrl+Alt+F1 startx',  or ' lightdm stop'  and  'restart'.
 
Right Clicking on the Desktop gave access to  Additional Drivers but the window had no buttons, or menus, nor size function, so I could not tell which version was which, and as I have not installed any video drivers it is running Nouveau on my GT 520 Nvidia card.```
apt-cache policy unity # returns:"Installed: 7.0.0daily13.04.15..." So it is not due to that reported Bug.
```In my notes I have a command to reset Compiz, but it is not complete:```
dconf -f /org/compiz/ 
```This I got from:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)
But it requires a PATH, either a Key or a Dir,

 Would someone please tell me what 'PATH' to add? I have a separate /Home partition.

Or what else to try?

 After rebooting and logging in to Gnome Classic(no effects) a normal Desktop resulted, so it is not a video driver problem.Edit: But see later Post.
 
 Chao!,** bogan**.



[B]sudo  -i dpkg  --configure -a

may help and  it's

sudo apt-get -f install

not 

sudo apt-get install -f

You can also visit this link-

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)


regards,
ventrical

[/B]

---

### Post by bogan on 2013-04-17
Hi!, All,

I also tried:```
display:0 compiz --replace # gave "Fatal: couldnt open display2
gconftool-2 --recursive-unset /apps/compiz-1 # gave: Warning Client unable toconnect to D-bus daemon, unable to autolaunch D-Bus daemon -
gconftool-2 --recursive-unset /apps/compizconfig-1 # - withoutdisplay for X11
dpkg-reconfigure compiz-gnome compiz gnome-control-center
```None of these affected the problem. the only change I noted was that the Software & Udates icon was misssing from System Settings.

Both 'dpkg' and 'apt-get install --reinstall compiz-gnome compiz  gnome-control-center' gave errors similar to those with gconftool.

Also 'startx' gave the Desktop screen but hung on "Loading extension GLX' , However:```
glxinfo | grep -i opengl # gave normal output for Nouveau.
```

In view of these error messages I installed the 313-updates driver from Additional Drivers, rebooted, and - touch wood - things seem back to normal. 'apt-get install --reinstall compiz-gnome compiz  gnome-control-center' no longer gives error messages.

But I would still like an answer to my previous question: What PATH should I add to this command?:```
dconf -f /org/compiz/ PATH
```

Chao!, bogan. I will give it a few days before marking Solved.

---

### Post by mc4man on 2013-04-17
You're not missing the path but the command
```
 dconf reset -f /org/compiz/
```

---

### Post by serdotlinecho on 2013-04-17
You can also restart Unity from unity dash. Press Alt+F2 and type unity, Enter. Same with compiz, Alt+F2 and type compiz --replace, or from terminal:

```
setsid compiz --replace
```

---

### Post by bogan on 2013-04-18
> **mc4man said:**
> You're not missing the path but the command
```
 dconf reset -f /org/compiz/
```Sorry, my typo copying from tty, the 'reset' was in the original, I have edited the Post.

Actual output was :```
dconf reset -f /org/compiz/
 error: Error spawning command line 'dbus-launch &#8211;autolaunch=b76ca......3fb &#8211;binary-syntax &#8211;close-stderr' : Child process exited with code 1
 Usage: dconf reset [-f] PATH
 Reset a key or dir. -f is required for dirs.
 Arguments:
 PATH         Either a KEY or Dir
 KEY           A key path (starting, but not ending with '/')
 DIR            A directory path  (starting, but and ending with '/')
```**But /org/ does not appear to exist in 13.04**, so what path should I use  ??

Chao!, **bogan.**

---

### Post by bogan on 2013-04-18
Hi!,** ventrical,**

You Posted:> **it's sudo apt-get -f install, not sudo apt-get install -f**Where did you get this from?

In 'man apt-get', " -f" is shown as equal to "--fix-broken", and I see nothing to suggest the option should, or must be before the command.

There seem to be an endless series of commands all claimed to be to reset Compiz and/or Unity.

Chao!,** bogan.**

---

### Post by ventrical on 2013-04-18
> **bogan said:**
> Hi!,** ventrical,**

You Posted:Where did you get this from?

In 'man apt-get', " -f" is shown as equal to "--fix-broken", and I see nothing to suggest the option should, or must be before the command.

There seem to be an endless series of commands all claimed to be to reset Compiz and/or Unity.

Chao!,** bogan.**

It appears to work both ways.

I usually load :

sudo  apt-get install fvwm-crystal

which is a windows manager that you can log on to from lightdm. I can run ccsm from there and manually setup Unity Plugin. It has always been a good failsafe when Unity or ccsm are in conflict with each other or terminal does not produce the required results.

In development cycle there have always been anomolies with Unity , ccsm and certain video drivers.  When all else fails, fvwm-crystal has always been of a great help.


regards,

ventrical

---

### Post by Chris62 on 2013-04-18
Hi,

I have exactly the same problem as bogan after updating Ubuntu 13.04 yesterday; after the required re-boot I was logged in but without a desktop. I have tried the suggestions made by ventrical but they don't help. Doing 
```
dpkg -i --configure -a
``` 
produces an error message 
> dpkg: error: conflicting actions (--configure) and -i (--install)

Has anyone any further suggestions?

At one point I got an error message saying that my hardware may not be supported, but it is relatively new (an Intel i7 processor in an Asus P8P67 Pro motherboard with an Nvidia GE Force 9500 Graphics  card and 8 GB RAM. It works perfectly with Ubuntu 12.10 and has worked well (so far) apart from a couple of minor hiccups, Ubuntu 13.04 so I am not convinced that my hardware is at fault

---

### Post by ventrical on 2013-04-18
> **Chris62 said:**
> Hi,

I have exactly the same problem as bogan after updating Ubuntu 13.04 yesterday; after the required re-boot I was logged in but without a desktop. I have tried the suggestions made by ventrical but they don't help. Doing 
```
dpkg -i --configure -a
``` 
produces an error message 


Has anyone any further suggestions?

At one point I got an error message saying that my hardware may not be supported, but it is relatively new (an Intel i7 processor in an Asus P8P67 Pro motherboard with an Nvidia GE Force 9500 Graphics  card and 8 GB RAM. It works perfectly with Ubuntu 12.10 and has worked well (so far) apart from a couple of minor hiccups, Ubuntu 13.04 so I am not convinced that my hardware is at fault

  I just retried that command and I got the same error.  the 'sudo dpkg  -i --configure -a' is used when there has been a broken package during  an update or install. Worked great for me during previous installs  unless this has been changed also.

---

### Post by ventrical on 2013-04-18
> **Chris62 said:**
> Hi,

I have exactly the same problem as bogan after updating Ubuntu 13.04 yesterday; after the required re-boot I was logged in but without a desktop. I have tried the suggestions made by ventrical but they don't help. Doing 
```
dpkg -i --configure -a
``` 
produces an error message 


Has anyone any further suggestions?

At one point I got an error message saying that my hardware may not be supported, but it is relatively new (an Intel i7 processor in an Asus P8P67 Pro motherboard with an Nvidia GE Force 9500 Graphics  card and 8 GB RAM. It works perfectly with Ubuntu 12.10 and has worked well (so far) apart from a couple of minor hiccups, Ubuntu 13.04 so I am not convinced that my hardware is at fault

'sudo -i dpkg --configure -a' is a valid command:


[http://www.ossdoc.com/2012/10/how-to-repair-broken-software-package.html](http://www.ossdoc.com/2012/10/how-to-repair-broken-software-package.html)

 Why it is not working is beyond me. I can only assume that you actually have to have some broken packages for it to work.

---

### Post by ventrical on 2013-04-18
> **Chris62 said:**
> Hi,

I have exactly the same problem as bogan after updating Ubuntu 13.04 yesterday; after the required re-boot I was logged in but without a desktop. I have tried the suggestions made by ventrical but they don't help. Doing 
```
dpkg -i --configure -a
``` 
produces an error message 


Has anyone any further suggestions?

At one point I got an error message saying that my hardware may not be supported, but it is relatively new (an Intel i7 processor in an Asus P8P67 Pro motherboard with an Nvidia GE Force 9500 Graphics  card and 8 GB RAM. It works perfectly with Ubuntu 12.10 and has worked well (so far) apart from a couple of minor hiccups, Ubuntu 13.04 so I am not convinced that my hardware is at fault


 My bad ..

it's :

sudo -i dpkg --configure -a

and it is best to run it from {alt+F1} terminal. Not GUI terminal.

---

### Post by grahammechanical on 2013-04-18
> [COLOR=#000000]After rebooting and logging in to Gnome Classic(no effects) a normal Desktop resulted, so it is not a video driver problem.Edit: But see later Post.[/COLOR]

Does Gnome classic use Compiz as the compositing manager?

Here is my tuppenny worth (2 cents worth) to solving this.

Right click the desktop and select Change Desktop Background. When System Settings opens click Software & Updates and at the Additional Drivers tab de-activate the Nvidia driver and activate the Nouveau driver. Then run
```
dconf reset -f /org/compiz/
``` and reboot.

It works for me. The error message about an incorrect path is due to not having a forward slash at the front and at the end. Try it with ```
deconf dump /org/compiz
``` and ```
deconf dump /org/compiz/
``` which one gives the error message?

During the Raring development cycle I have only been able to use the Nvidia drivers for about 4 weeks without them breaking something. I tried three of the available Nvidia drivers and I got the same problem but with Nouveau things work just fine.

Oh, by the way, the changes (improvements?) to Unity since 12.04 mean that reset options that work in 12.04 do not work in 12.10 and now it seems that different reset options are needed for 13.04. I just hope that if the development branch does eventually become the replacement of interim releases that someone thinks of informing us development branch users of these changes to the code.

Regards.

---

### Post by Dark_Horizon on 2013-04-18
Yesterday all my troubles seemed so far away then they came to stay... in the form of an update that broke unity, and compiz and did a lot of no good to Open GL I've tried every fix I could think of a lot of them detailed here. yesterday there was an update that took a fairly well working 13.04 B2 to a completely broken one, its absolutely shocking that this sort of thing is going on at this stage of development. I reinstalled the B2 and its a bit buggy still but works more or less; the kind of thing you'd expect from a A1 or 2 build. However, I did just downed and burned the latest daily build to test out; and unity and compiz don't work even running it from DVD. Here's this afternoons error report...really its a problem ..I don't think so it works unlike the updated version.  

 

 The problem cannot be reported: ...you don’t say!
  
 You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 
  
 update-notifier, apport, apport-gtk, apt, apt-utils, at-spi2-core, binutils, gdb, gir1.2-atk-1.0, gir1.2-gtk-3.0, glib-networking, glib-networking-common, glib-networking-services, libappindicator3-1, libapt-inst1.5, libapt-pkg4.12, libatk-bridge2.0-0, libatk1.0-0, libatk1.0-data, libatspi2.0-0, libcups2, libgail-3-0, libgl1-mesa-dri, libglib2.0-0, libglib2.0-data, libgstreamer-plugins-base1.0-0, libgstreamer1.0-0, libgtk-3-0, libgtk-3-bin, libgtk-3-common, libgudev-1.0-0, libindicator3-7, libpci3, libpython-stdlib, libpython2.7, libpython2.7-minimal, libpython2.7-stdlib, libpython3-stdlib, libpython3.3-minimal, libpython3.3-stdlib, libudev1, passwd, pciutils, perl, perl-base, perl-modules, python, python-gi, python-minimal, python2.7, python2.7-minimal, python3, python3-apport, python3-distupgrade, python3-gi, python3-minimal, python3-problem-report, python3-update-manager, python3.3, python3.3-minimal, shared-mime-info, tar, ubuntu-release-upgrader-core, ubuntu-release-upgrader-gtk, udev, update-manager, update-manager-core, update-notifier, update-notifier-common
 

 Have the guys writing this ever considered working for Microsoft, what have you guys been smoking.  Its up for final release in 7 days and the desktop environment is broken! Coding by the Fabulous furry freak brothers!

---

### Post by ventrical on 2013-04-18
> **Dark_Horizon said:**
> Yesterday all my troubles seemed so far away then they came to stay... in the form of an update that broke unity, and compiz and did a lot of no good to Open GL I've tried every fix I could think of a lot of them detailed here. yesterday there was an update that took a fairly well working 13.04 B2 to a completely broken one, its absolutely shocking that this sort of thing is going on at this stage of development. I reinstalled the B2 and its a bit buggy still but works more or less; the kind of thing you'd expect from a A1 or 2 build. However, I did just downed and burned the latest daily build to test out; and unity and compiz don't work even running it from DVD. Here's this afternoons error report...really its a problem ..I don't think so it works unlike the updated version.  

 

 The problem cannot be reported: ...you don’t say!
  
 You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 
  
 update-notifier, apport, apport-gtk, apt, apt-utils, at-spi2-core, binutils, gdb, gir1.2-atk-1.0, gir1.2-gtk-3.0, glib-networking, glib-networking-common, glib-networking-services, libappindicator3-1, libapt-inst1.5, libapt-pkg4.12, libatk-bridge2.0-0, libatk1.0-0, libatk1.0-data, libatspi2.0-0, libcups2, libgail-3-0, libgl1-mesa-dri, libglib2.0-0, libglib2.0-data, libgstreamer-plugins-base1.0-0, libgstreamer1.0-0, libgtk-3-0, libgtk-3-bin, libgtk-3-common, libgudev-1.0-0, libindicator3-7, libpci3, libpython-stdlib, libpython2.7, libpython2.7-minimal, libpython2.7-stdlib, libpython3-stdlib, libpython3.3-minimal, libpython3.3-stdlib, libudev1, passwd, pciutils, perl, perl-base, perl-modules, python, python-gi, python-minimal, python2.7, python2.7-minimal, python3, python3-apport, python3-distupgrade, python3-gi, python3-minimal, python3-problem-report, python3-update-manager, python3.3, python3.3-minimal, shared-mime-info, tar, ubuntu-release-upgrader-core, ubuntu-release-upgrader-gtk, udev, update-manager, update-manager-core, update-notifier, update-notifier-common
 

 Have the guys writing this ever considered working for Microsoft, what have you guys been smoking.  Its up for final release in 7 days and the desktop environment is broken! Coding by the Fabulous furry freak brothers!

Thanks for the heads up. :)   There were a few times I was the canary in the cage :)

---

### Post by bogan on 2013-04-18
Hi!, **grahammechanical**,

Thanks for the insight, but I already knew that the PATH had to have forward slashes fore & aft. The original code did have both slashes.

The same code:```
dconf rest -f /org/compiz/
``` no longer gives an error, but the assumed expected output.

What I do not understand is the "/org/" bit. Nautilus does not show it as folder, but somehow 'dconf' finds it.

'man dconf>dump' shows only "DIR" as an Argument, not "PATH", though confusingly it desribes it as : " A directory path (starting and ending with '/')"

Of couse, both your "deconf dump" test codes give errors, but that is from the 'deconf" typo. Presumably, without the '/' suffix it would be a "KEY", whatever that means.

Chao!, **bogan**.

---

### Post by swftech on 2013-04-18
Just chiming in to let you know I have the same problem. I have been running Ubuntu 13.04 daily build for over a month without issues at all. Yesterday I ran software updater, it required a reboot when finished so I rebooted and it would stop right before the login screen. I entered tty logged in and ran command "startx" which brought me to the desktop but nothing was there other than my wallpaper. No launcher, panels or anything. Nothing worked at all.

I messed with it for about an hour before deciding to re-install. After re-install everything was fine until I updated, then ran into the same exact problem. I decided to wait until today to download a newer daily build. Threw it on a flash drive and booted it...same thing. Once I log in nothing is there just the wallpaper. No commands work, nothing will run. I'm not sure what got screwed up, but something in this latest update has broken Ubuntu 13.04. I triple boot Ubuntu, Mint 14 Xfce and Debian sid so I'll wait til later or tomorrow to try the next daily build to see if the problem is fixed. Hopefully it will be since the final release is a week away. Funny how it doesn't screw up until right before release...lol.

---

### Post by ventrical on 2013-04-18
I just updated (compiz settings and all) and there have been no adverse effects.

---

### Post by Dark_Horizon on 2013-04-18
If you revert your version of Compiz and OpenGL to an older version it works, well it appears to work since I'm talking on it right now, I have just reinstalled the B2 for the 3rd time today. Before reinstall I ran the dreaded update, however, I de selected compiz config centre and unity worked but anything using OpenGl like cairo dock and screenlets just didn't start then I rebooted and it crashed on login so I reinstalled and used an older Compiz seems to be working fine for the moment. just notice some graphics corruption  problems on drop down menus. no error messages coming up though.

---

### Post by philinux on 2013-04-18
> **ventrical said:**
> I just updated (compiz settings and all) and there have been no adverse effects.

Same here. Must be hardware specific. Mind you this is a clean install from alpha. So clean home. No odd configs left over.

---

### Post by ventrical on 2013-04-18
> **philinux said:**
> Same here. Must be hardware specific. Mind you this is a clean install from alpha. So clean home. No odd configs left over.

  I have ccsm running in raring across most platforms, ATi , Nvidia, Intel and AMD, 32bit and 64bit. ATi graphics has been tough though. Unity dash gets really distorted, especially on the most recent . dailys.

---

### Post by whyisdaskyblue on 2013-04-18
Same thing happened to me, fine until yesterdays update. Just see the wallpaper, no unity and no amount of fiddling would fix it.  Downloaded the latest daily build to usb and on bootup .. same thing.
This is on a Lenovo T61p laptop with nvidia video (using open source drivers).

---

### Post by cecilpierce on 2013-04-18
I did 'compiz --replace' in a terminal and desktop came back but crapy, after reboot seems to be working ok but slow booting.

---

### Post by Chris62 on 2013-04-19
Please ignore this post. I have solved the problem

---

### Post by whyisdaskyblue on 2013-04-19
in a terminal window did a apt-get update and todays update that I just did now included something that now brings up the unity interface.  problem now solved for me.

---

### Post by ultracarl on 2013-04-20
I had the same problem. Fiddled for a long time before I found a solution, and it turned out to be quite simple. Here's how I solved it:

1. Installed dconf-tools (didn't actually have to install this, because I already had it installed)
2. Reset workspaces, launcher size etc....
```
dconf reset -f /org/compiz/
```
3. Reset Unity with default icons:
```
unity --reset-icons
```

After this, the screen flickered a few times, and voila, everything was back to normal. Hope this can help someone having the same problem :)

I got the idea for the solution from OMGUbuntu: [http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)

---

### Post by bogan on 2013-04-23
Hi!, **All**,

One more day, one more update - including a kernal  upgrade from 3.5 to 3.8.0-19 #29 - and one more foul-up!

Back to a Blank Desktop background less than full screen size, without Launchers or Panels when logged-in to Ubuntu - though Gnome Classic Fallback still works. I can access that by 'Ctrl+Alt+Del' to logout to the greeter Log-in screen, which is normal and complete with top panel - and now the correct screen display size.

Nothing I tried cured the problem which this time it seems to be not  Compiz but Plymouth which failed, 'Ctrl+Alt_F1' gives a hung TTY saying: "mountall: disconnected from Plymouth" and the opengl seems not to be active.

Further, reinstalling the nvidia driver, both from Additional Drivers and with NVIDIA.com Downloads failed, as both were trying to create modules for 3.5 not 3.8.

Only three days to go to the Release date, and I thought the Schedule called for a freeze 7 days from release, except for .iso finalisation.

I think I will wait till Thursday before re-installing 13.04.

Chao!, **bogan**.

---

### Post by TRPrecht on 2013-04-23
> **serdotlinecho said:**
> You can also restart Unity from unity dash. Press Alt+F2 and type unity, Enter. Same with compiz, Alt+F2 and type compiz --replace, or from terminal:

```
setsid compiz --replace
```

I had a similar issue and this work for me on my parents computer. But on reboot, the issue popped back up. Luckily, I had another user account on the machine, logged in to it, deleted the other account leaving files, recreated account with same name. After that Bob's Your Uncle; every thing worked fine and after reboots and on top of that my mom got to keep all of her other settings.

---

### Post by Thee on 2013-04-25
> **grahammechanical said:**
> Does Gnome classic use Compiz as the compositing manager?

Here is my tuppenny worth (2 cents worth) to solving this.

Right click the desktop and select Change Desktop Background. When System Settings opens click Software & Updates and at the Additional Drivers tab de-activate the Nvidia driver and activate the Nouveau driver. Then run
```
dconf reset -f /org/compiz/
``` and reboot.

It works for me. The error message about an incorrect path is due to not having a forward slash at the front and at the end. Try it with ```
deconf dump /org/compiz
``` and ```
deconf dump /org/compiz/
``` which one gives the error message?

During the Raring development cycle I have only been able to use the Nvidia drivers for about 4 weeks without them breaking something. I tried three of the available Nvidia drivers and I got the same problem but with Nouveau things work just fine.

Oh, by the way, the changes (improvements?) to Unity since 12.04 mean that reset options that work in 12.04 do not work in 12.10 and now it seems that different reset options are needed for 13.04. I just hope that if the development branch does eventually become the replacement of interim releases that someone thinks of informing us development branch users of these changes to the code.

Regards.

Thanks a lot! This worked for me :)

---

### Post by joseph8th on 2013-04-25
> **Thee said:**
> Thanks a lot! This worked for me :)

This also worked for me. Thanks to everyone for saving hours or even days figuring this out.

---

### Post by bogan on 2013-04-26
Hi! All,

Well! Things have gone from bewildering to to totally mind-boggling.

Three new installations of the released 13.04 and all three are the same, as soon as I install an Nvidia driver of any sort, when logged in to Ubuntu I get the same Blank Desktop with my chosen backgrund, but no Panels or Launchers. Both 'Ctrl+Alt+t' & 'Ctrl+Alt+F1-7' work correctly, and  'Ctrl+Alt+Del' allows me to logout.

Previously everything was OK with Nouveau, but after removing the nvidia driver and the Nouveau blacklist the display remained blank.

I do not have Gnome-shell but Gnome-session-fallback, both classic & no_effects run as expected with their Panels and Launcher. As does logging in to a Guest account.

Which, it seems clear to me, means the problem is one of configuration and/or Compiz; yet I have tried every way I can find or imagine to remove and reinstall, or clear & reset all the compiz and unity settings, to no avail.

In one case I thought I had found the cause, as the Unity Plugin had not been activated in CCSM. However, ticking it and rebooting had no effect.

The only other clue I have found is that several Compiz resets give fatal errors involving D-bus Daemon and a lack of a display, regardless of what mode was set-up, or whether the desktop manager was running or not: 'starx' opens the same login screen or blank desktop.

THE CLEAEST MESSAGE I GOT WAS FROM RE-INSTALLING COMPIZ ETC:> ERROR : unity.session.gnome GnomeSessionManager.cpp:297 Gnome Session call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown:

Any fresh ideas welcome.

Edit: Creating a new administration account allows unity to work correctly even with an Nvidia driver installed.
Chao!, **bogan.**

---

### Post by junctionIV on 2013-04-26
Bogan, I had the exact same problem listed here and tried follwing everything listed in this forum to fix it to no sucess, utnil I tried using
> sudo dconf reset -f /org/compiz
gnome-session-quit

When I Logged back in, UINTY was correcly installed and running but I had to reconfig the display settings.
Also I am using an Nvidia GTX660TI and have the nvidia drivers

---

### Post by bogan on 2013-04-27
Hi!,** junctionIV,**

Thanks for the response, 'gnome-session-quit' is one thing I had not tried; 			 		'sudo dconf reset -f /org/compiz' does nothing when Unity is working, but gives an error when there is a blank Desktop, so still does nothing.

I have settled to using a fresh Admin account, from which I will not install any nvidia drivers.

Which nvidia version are you using ?  The Video card in my new computer is an MSI GTX 660, and nvidia recommend the 310.44 driver, and for some reason not the later 313 versions.

Chao!,** bogan**.

---

### Post by Giantmundo on 2013-04-29
This problem was giving me alot grief as well.  I came across a suggestion to get up a terminal (ctrl alt t) and display ccsm and disable the Unity Plugin.  Then re-enable the plugin and resolve cthe conflicts that were displayed and all was OK.  That was my only upgrade problem and now everything is good.  The issues that nvidia cards have with upgrades is frustrating.

---

### Post by bogan on 2013-04-29
Hi!, **All**,

I am marking this thread as Solved, as all my Raring installations are working correctly, though just what cured them I have little idea.

One, at least, seems to have cured itself without even an update, or any attempt to alter anything.

In principle, it seems that all the various ways I tried to correct the apparent Compiz failures, returned error messages and failed to reset things, as there was no  display available, or GLX was not activated. ie no plugin.

When I created, and logged into a second Administration account, Ubuntu/Unity ran correctly and the compix reset commands then succeeded and put right the original account.

The strangest thing of all is that in this new account, which is running AOK, when I checked in CCSM I found the Unity Plug-in was shown as not activated, though there was an empty check box against the Icon - which was missing in the faulty accounts - when I activated it I got messages that dependencies were required including: OpenGL, Composite, Compiz-toolbox, Scale, and Expc.
After they were all were activated, the Plugin was too, but it made no difference to the already correct display. [To do this you need to be in root, ie 'gksudo ccsm' from a terminal.]

I recommend to anyone still with this Blank Desktop problem unsolved, to try logging in to another account and checking both Unity and GLX plugins are activated. IE 'opengl' & 'unityshell' .
Use the following command with the 'get' option, instead of 'reset,' to list them.```
gsettings reset org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins
```
But no guarantees!

Chao!, **bogan.**

---

### Post by bogan on 2013-05-03
Hi!, **All,**

Latest is that the 'Solved' was a bit premature: The three 13.04 installations in my new computer, are still working correctly - I have not tried re-installing, or updating, any of the nvidia drivers used - but in the older Win7 machine my original 13.04 installation was still in its Blank Desktop state and neither any of the Compiz or Unity resets, nor using a Guest or second Admin account, got Unity back. [ Though Fallback still works. ]

Further, running 'startx' went directly to the Blank Desktop, not to the Greeter Log-in screen.

Included in the things I tried are those in the following list: If anyone has any further suggestions please Post them.

Edit: I have not included **MAFoElffen'**s latest suggestion, I only just now stumbled on it. [Edit 2: but it did not work, anyway.] **EDIT3: But see later Post #39, it worked when re-arranged.**

Chao!,** bogan.**

**To Check & reset Compiz/Unity:**

dconf reset -f /org/compiz/
unity --reset-icons

sudo dconf reset -f /org/compiz # should have a end '/' ??
gnome-session-quit 

dpkg-reconfigure compiz-gnome compiz gnome-control-center
dpkg-reconfigure -a 

setsid compiz --replace # or compiz>Enter or Unity>Enter
setsid unity

display=:0 compiz --replace # [Edit: '=' was omitted.]

glxinfo | grep -i opengl 

gconftool-2 --recursive-unset /apps/compiz-1 
gconftool-2 --recursive-unset /apps/compizconfig-1

**To check plugins:** [use 'reset' in place of 'get' which just lists them]
 {should include: 'opengl' & 'unityshell'}
gsettings get org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins

 (ctrl+alt+t) 'gksudo ccsm' and disable the Unity Plugin. Then re-enable the plugin and resolve the conflicts that were displayed and all was OK.

**Plus: **sudo apt-get install --reinstall & dpkg --reconfigure all the related CMD's.

---

### Post by matt_symes on 2013-05-03
Hi

```
display:0 compiz --replace
```

Doesn't this throw an error; *display:0 command not found* ? Are you sure you're not trying to type

```
DISPLAY=:0 compiz --replace
```

Setting the DISPLAY environmental variable so that compiz knows which display to use/reset ?

Kind regards

---

### Post by bogan on 2013-05-04
> **matt_symes said:**
> Hi

```
display:0 compiz --replace
```

Doesn't this throw an error; *display:0 command not found* ? Are you sure you're not trying to type

```
DISPLAY=:0 compiz --replace
```

Setting the DISPLAY environmental variable so that compiz knows which display to use/reset ?

Kind regardsThanks for that, You are quite right. There was a typo in the post I copy/pasted it from.

Unfortunately, even corrected, I still got a 'can not open display', D-Bus error.

Chao!,** bogan.**

---

### Post by bogan on 2013-05-04
Hi!,** All,**

My problem with 13.04 has been cured by using a terminal in Fallback mode to enter the reset unity command included in Unity-Tweak-Tool:```
sudo apt-get install unity-tweak-tool
echo $DESKTOP_SESSION 
fallback-compiz 

gksudo unity-tweak-tool --reset-unity
Warning: You are about to reset unity to its default configuration.  
It is normal for your desktop to flicker during the process.  
Type yes to continue, anything else to exit.   
Do You wish to continue? _
```On rebooting all the log-in options were correct and with intact Launchers and Panels.

Running the same command when logged into the faulty Ubuntu/Unity Blank Desktop gave a 'Can not open display' message and did nothing.

It is probable - though I have not tried it - that the other compix/unity reset commands would also work if run in the same way.

Chao!, **bogan**.

---

### Post by cuyabro on 2013-05-07
I had this same issue.  After hours of resetting Compiz and re-downloading ATI drivers, removing them, reinstalling old generic drivers nothing would work.  I decided to create a new account and login just for kicks and the menu bar came up along with the systray.  However, as soon as I logged in with my regular admin account it would go back to the same empty desktop.  

I deleted ~/cache and ~/gconf and ~/config and I got my bars back on my desktop using my main admin account.  

This link below was very useful.  I hope it helps you too.

[http://askubuntu.com/questions/286088/menu-bar-and-launcher-missing-in-ubuntu-13-04](http://askubuntu.com/questions/286088/menu-bar-and-launcher-missing-in-ubuntu-13-04)

-Elverth

---

### Post by schtinky on 2013-05-18
> **Dark_Horizon said:**
> its absolutely shocking that this sort of thing is going on at this stage of development.

I couldn't agree more. Linux has been my primary OS since 1999 (mostly RH/Fedora, more recently Ubuntu) and fighting these sorts of battles has gotten tiresome. Yesterday, on another machine with Fedora, upgraded my packages, rebooted and the XFCE login screen wouldn't come up. Today, I sit down to write some Java on this Ubuntu machine and Unity crashes, killing the launcher and window frames. I'm always switching back and forth between distros in an overly-optimistic, but ill-advised search for a distro where everything (or at least the basic stuff) just works. It doesn't exist.

Every time one of these "wrinkles" pops up, that's a few hours of productivity down the drain -- if you can fix it at all (which usually requires insane understanding of obscure text config files or whatever) -- and that's why desktop linux has never gained any significant market share. Enterprise software developers, whether web applications, native software, embedded systems, etc don't allow this sort of thing to happen outside of 99.99999999% certainty because they know it's entirely unacceptable. The company would cease being able to sell products, especially to companies, and the coder/team responsible would be reprimanded and/or fired. 

Obviously Linux is a collaboration of free labor and the comparison isn't quite fair. However, this is the reality of why desktop Linux is and apparently will remain a hobbyist OS. No corporate IT department in its right mind would take on the burden of trying to make linux work across their enterprise. It's an expensive and frustrating battle that saps productivity at the macro and micro levels. No one is more passionate about Linux than I am, and I would seriously hesitate to green-light desktop linux across my employees' machines.

So what am I supposed to do? Go buy Windows 8? Hell no. Pay inflated prices for Mac hardware just to get a well-polished linux-based OS from Apple? I'd rather not do that, either. Chrome OS? 

I'm sure it's been said a thousand times before, but all this energy exerted in disparate directions (gnome, kde, unity, xfce, just to name the window managers) is detrimental to the overall success of desktop Linux. We need something we can count on to be stable across as much hardware as possible, whose governing team is focused and well funded so they can test out distro changes before putting it out there and crashing a bunch of machines. 

People like to talk about open source software in evolutionary terms: "The best software will gain the most developers and emerge as the leader." But the analogy is wrong. In evolution, THINGS MUST DIE so the better individuals can supercede and consume the resource pool. Gnome 3, for instance, was such a complete joke that it shouldn't be around anymore. The programmers (resources) should now be available for -- oh, I don't know, Unity, maybe? Instead, it's still there, sucking up programmer cycles and gumming up the works for better window managers.

The pillars of the open source community need to stand up and talk about the benefits of focusing efforts on 1 or 2 window managers, 1 or 2 compositing managers... even 1 or 2 GUI distros. This hodge-podge nonsense has to stop.

Yes, this is my first post. Feel free to trash me. I don't care.

---

### Post by cariboo on 2013-05-18
Thanks, for posting and welcome to the forum. This sub-forum is meant to be a place where those of us, that enjoy taking part in testing development versions of Ubuntu can get help solving problems we run into. Currently we are using and discussing problems we are running into with Saucy (13.10).

@schtinky, your comments would be better posted in [Ubuntu, Linux and OS Chat]("http://ubuntuforums.org/forumdisplay.php?f=434"), but be warned, that your thread will probably be moved to Recurring Discussions, as this topic has been discussed so many times, that it is bound to be reported as recurring.

Thread closed.

---

