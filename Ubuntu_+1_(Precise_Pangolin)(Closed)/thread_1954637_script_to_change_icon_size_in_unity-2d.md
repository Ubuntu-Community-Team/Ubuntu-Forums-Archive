---
title: "script to change icon size in unity-2d"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ppd on 2012-04-08
**Update: This script only works on current beta "Precise Pangolin". The changes will persist until some unity update overwrites those qml files again. Re-running the script will help then.**

As we all know unity 2D currently lacks an option to configure the size of those launcher icons.

It is possible though to achieve this by manually editing some qml files. This is quite annoying, so I put a script together that takes care of it. It doesn't rely on line numbers but has some very simple "logic" to be able to handle possible line shifts in the future.

Coding style is of course horrible, and not many possible fail cases (e.g unity 2d is not even installed...) are taken care of. 
Only thing it really does is backup those qml files before overwriting them.
Maybe somebody considers this useful...

Usage:

1) Save script somewhere you like
2) make it executable (chmod +x script.py)
3) run as: script.py iconSize (e.g. script.py 32)

Don't forget to restart your launcher. Killing it might be sufficient, logging out and in again works for sure.

I don't have any clue whether such a script already exists, but here is mine ;-)

Having such a script polished and then integrated into one of those fancy unity configuration programs may be an interesting option as long as Unity 2D lacks this feature.

Greetings 
ppd

---

### Post by fjgaude on 2012-04-08
Wow, very effective!

Thank you, ppd, for solving an issue with Unity 2D. I've not seen this issue fixed before.

---

### Post by mc4man on 2012-04-08
Seems to work well here - 
There was a commit proposed last year to allow a per user configuration of the launcher size in unity-2d. It worked well but was rejected I believe because of some minor 'not right's' when it wasn't used, ie. at the default size. 

I believe there is some hope to have a user config option available in 2d in 12.10

---

### Post by berthiggins on 2012-04-08
Thanks it works a treat for me as well :-))

---

### Post by ppd on 2012-04-08
Glad you find it useful. There are some minor problems with this method as far as I can see: The spread and the workspace switcher still think the launcher is as big as before. So one would need to find these settings in the qml and fix this.

---

### Post by ShareBuntu on 2012-04-09
I'm running 11.10. I don't have /usr/share/unity-2d/shell/Shell.qml. In fact, I don't have the entire /usr/share/unity-2d/shell directory. Any thoughts?

---

### Post by Phyllinux on 2012-04-10
I have exactly the same problem, using also Oneiric on my netbook.
In unity-2D directory, I have only these directories :
Launcher
Places
Spread
No Shell directory.

So, I got this error message :
[HTML]Traceback (most recent call last):
  File "./script.py", line 49, in <module>
    content = load_file (shell_qml)
  File "./script.py", line 23, in load_file
    file = open (filename, "r")
IOError: [Errno 2] No such file or directory: '/usr/share/unity-2d/shell/Shell.qml'
[/HTML]

---

### Post by ShareBuntu on 2012-04-10
> **Phyllinux said:**
> I have exactly the same problem, using also Oneiric on my netbook.
In unity-2D directory, I have only these directories :
Launcher
Places
Spread
No Shell directory.

So, I got this error message :
[HTML]Traceback (most recent call last):
  File "./script.py", line 49, in <module>
    content = load_file (shell_qml)
  File "./script.py", line 23, in load_file
    file = open (filename, "r")
IOError: [Errno 2] No such file or directory: '/usr/share/unity-2d/shell/Shell.qml'
[/HTML]
I thought it's worth adding that unity-2d runs just fine, albeit without the Shell.qml file, but that makes the script inoperable.

---

### Post by arune on 2012-04-10
I have the same issue. Ubuntu 11.10 and no shell folder under unity-2d. Is this only for 12.04 then please update first post with this useful information.

---

### Post by jerrylamos on 2012-04-10
Thanks!  Worked fine!  Do I have to run it on every boot?

Jerry

---

### Post by ppd on 2012-04-10
The script doesn't have to be run on every boot. Only if some update overwrites those qml files.

The script will not run on oneiric. I did not test this. I thought posting this in the Ubuntu+1 part of the forum would be sufficient to make this clear.

---

### Post by Phyllinux on 2012-04-11
> **ppd said:**
> The script doesn't have to be run on every boot. Only if some update overwrites those qml files.

The script will not run on oneiric. I did not test this. I thought posting this in the Ubuntu+1 part of the forum would be sufficient to make this clear.

Yes, of course, but some other forums have a link to this post, without warning that the script is only dedicated to Precise. But it does not matter. Only few days before the official delivery of 12.04 :lolflag:

---

### Post by rjrich on 2012-04-12
Thank you so much! I have been testing many different linux distros and DEs. I had avoided Ubuntu and Unity, mainly because it did not seem possible to configure the Launcher, and the large icons destroyed the symmetry and aesthetics of the screen. Thanks to your script, my desktop now looks balanced and elegant. I am going to give Ubuntu Unity another try. Your script ought to be incorporated into Ubuntu's mainstream product as part of the System Settings.

---

### Post by mihoo on 2012-04-13
For do some changes in oneric look here [http://www.ubunturoot.com/2011/10/customize-unity-2d-in-1110.html](http://www.ubunturoot.com/2011/10/customize-unity-2d-in-1110.html)

In precise You can also delete background and remove unused icons simply run in terminal:
```
sudo nautilus
```
go to and edit /usr/share/unity-2d/shell/launcher/Launcher.qml
and make simple change code in lines 224, 225 for example:
```
items.appendModel(workspaces);
items.appendModel(devices);
```
to
```
/*items.appendModel(workspaces);*/
 /*items.appendModel(devices);*/
```
this hide devices and workspaces ;)

You can also edit: /usr/share/unity-2d/shell/common/IconTile.qml
and change line 60 from:
```
.arg(actualColor.toString().replace("#", ""))
```
to
```
/*.arg(actualColor.toString().replace("#", ""))*/
```
this will remove background color from launcher icons.

If You have Precise and yours Unity 3d crashes as hell You can change Unity 2d and forget about it. ;)
cheers :)

PS: for scrollbars look here -> [http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)
for "Show Desktop" make some file with simple script:
```
#!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
```
And make some launcher/icon to run after that You can drag launcher to Unity 2d

---

### Post by nachordez on 2012-04-14
Thanks a lot! That's something really needed. I can't understand why is not yet in main development for unity... Works like a charm!

---

### Post by mikewhatever on 2012-04-15
> **nachordez said:**
> Thanks a lot! That's something really needed. I can't understand why is not yet in main development for unity... Works like a charm!

Resizing the Launcher was supposed to be a feature of Unity2d in Precise, but it wasn't ready. Hopefully it will get into Precise +1, and perhaps even get backported.

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by ShareBuntu on 2012-04-15
> **MarkieB said:**
> A question, is the effect of the script different to the effect of changing the size in compiz settings -> unity plugin ?
I believe that setting affects Unity (3D), as opposed to Unity (2D).

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by kolinab on 2012-04-15
MarkieB,

If you're in session 'ubuntu' then that will be the default 3D session. At the login screen, you can click on the settings 'gear' to select the unity2d session if you want. 

To adjust the launcher icon size in the default unity session, see this thread:

[http://ubuntuforums.org/showthread.php?t=1859670](http://ubuntuforums.org/showthread.php?t=1859670)

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

