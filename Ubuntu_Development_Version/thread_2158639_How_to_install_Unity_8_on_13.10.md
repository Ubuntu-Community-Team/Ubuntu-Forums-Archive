---
title: "How to install Unity 8 on 13.10"
date: 2013-06-29
forum: Ubuntu Development Version
---

### Post by MaZaMo on 2013-06-29
How do I do this? Unity 8 looks really really cool. I've tried this: [http://unity.ubuntu.com/getinvolved/development/unity8/](http://unity.ubuntu.com/getinvolved/development/unity8/) but it isn't working for me :(

---

### Post by MaZaMo on 2013-06-29
Isn't it supposed to be supported in the software center by the time of the 13.10 release? I wonder when it will be added to the software center...

---

### Post by QIII on 2013-06-29
Moved to Ubuntu + 1

---

### Post by rrnbtter on 2013-06-29
Greetings,
The release date should be OCT 31, 2013. So it will probably be there before then.

---

### Post by MaZaMo on 2013-06-29
Ok but I saw a video of someone using it on his macbook. How is that done?

---

### Post by cariboo on 2013-06-30
> **MaZaMo said:**
> Ok but I saw a video of someone using it on his macbook. How is that done?

It was probably a developer using a pre-release version. A ppa for mir just became available, it seems to me that mir needs to be released before we get Unity 8.

---

### Post by MaZaMo on 2013-06-30
(Deleted Post)

---

### Post by MaZaMo on 2013-06-30
Well I just found I can still run unity next in ubuntu ([http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop](http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop)). Even that isn't working for me, though! On step 3, when I try to run ./build I get this error in terminal:

**CMake Error at CMakeLists.txt:1 (message):**
**  THIS BRANCH IS NO LONGER USED.  Development continues on lp:unity/8.0**


**-- Configuring incomplete, errors occurred!**
**make: *** No targets specified and no makefile found.  Stop.**

---

### Post by MaZaMo on 2013-06-30
Deleted

---

### Post by Bucky Ball on 2013-06-30
What release are you using? 12.10 here:

[http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop](http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop)

... if any help.

---

### Post by MaZaMo on 2013-06-30
It says development continues to lp:unity/8.0 so I tried this: [http://unity.ubuntu.com/getinvolved/development/unity8/](http://unity.ubuntu.com/getinvolved/development/unity8/)
Now on the build dependencies step, when I run [COLOR=#000000]./build -s I get this error: 
[/COLOR]
**./build: 55: ./build: Syntax error: "||" unexpected**

---

### Post by MaZaMo on 2013-06-30
[SIZE=2][I][COLOR=#000000]What release are you using? 12.10 here:[/COLOR]
[http://www.omgubuntu.co.uk/2013/04/h...n-your-desktop]("http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop")
[COLOR=#000000]... if any help.[/COLOR][/I][/SIZE]

I'm using 13.10 right now. Is that the problem?

---

### Post by MaZaMo on 2013-06-30
Anyway forget about Unity next... I want to run that unity 8 if possible, which needs ubuntu 13.10.

**./build: 55: ./build: Syntax error: "||" unexpected**

---

### Post by cariboo on 2013-06-30
What happens when you change this line:

```
 bzr branch lp:unity/phablet ~/unity/unity-next
```

to this?

```
 bzr branch lp:unity/8.0 ~/unity/unity-next
```

---

### Post by MaZaMo on 2013-06-30
now on the **./build -s** I get this error:

**./build: 55: ./build: Syntax error: "||" unexpected**

---

### Post by cariboo on 2013-06-30
> **MaZaMo said:**
> now on the **./build -s** I get this error:

**./build: 55: ./build: Syntax error: "||" unexpected**

You'll probably have to go through the scripts to see what ppas it is trying to pull in, and see if they are still valid.

The instructions you are trying to follow, are from April of this year, and as you can see, much has changed since then.

---

### Post by MaZaMo on 2013-06-30
This is newer: [http://unity.ubuntu.com/getinvolved/development/unity8/](http://unity.ubuntu.com/getinvolved/development/unity8/)
But I get the same error. How do I go through the scripts like you said?

---

### Post by mc4man on 2013-06-30
If it doesn't like the || then get rid of.
Overall currently none too useful on the Desktop, hardly worth the effort. (give it a month or so at best

---

### Post by cariboo on 2013-06-30
Please don't create multiple threads on the same subject. I've merged your two threads.

---

### Post by MaZaMo on 2013-06-30
> **mc4man said:**
> If it doesn't like the || then get rid of.
Overall currently none too useful on the Desktop, hardly worth the effort. (give it a month or so at best
How do I get rid of it? Sorry for all the questions I'm not that good with this kind of stuff.

---

### Post by mc4man on 2013-06-30
> **MaZaMo said:**
> How do I get rid of it? Sorry for all the questions I'm not that good with this kind of stuff.

While it wouldn't really matter if you remove the || may as well fix the mistake.

Open up /unity/unity8/build in a text editor.
scroll down to line 55, put your cursor to the immediate left  of the first | and backspace till it is **on a line right below** "unity-lens-applications \"
Where on that line doesn't particularly  matter, far left is ok, see screen (point is that there can't be an empty line between line # 53 & || exit 5
Then ./build -s will run

---

### Post by MaZaMo on 2013-06-30
Thank you so much! But now there's another problem. :( The **./build -s** works, but then when I do the next command which is **./build** it comes up with this error:

```
./build: 57: ./build: mk-build-deps: not found
-- Could NOT find Lcov (missing:  LCOV_EXECUTABLE GENHTML_EXECUTABLE) 
-- Could NOT find gcovr (missing:  GCOVR_EXECUTABLE) 
-- checking for one of the modules 'hud-client-2'
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:363 (message):
  None of the required 'hud-client-2' found
Call Stack (most recent call first):
  tests/qmltests/plugins/HudClient/CMakeLists.txt:8 (pkg_search_module)


-- checking for module 'unity-core-6.0'
--   package 'unity-core-6.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:279 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:333 (_pkg_check_modules_internal)
  plugins/Unity/CMakeLists.txt:4 (pkg_check_modules)


-- checking for one of the modules 'hud-client-2'
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:363 (message):
  None of the required 'hud-client-2' found
Call Stack (most recent call first):
  plugins/HudClient/CMakeLists.txt:5 (pkg_search_module)


-- Configuring incomplete, errors occurred!
```

---

### Post by MaZaMo on 2013-06-30
You know... never mind about this whole thing. I wish I could do it, but it just messed up my system and now the unity dash looks really weird. Take a look at the screenshot:

[IMG]http://ubuntuone.com/2DXjWU6VlsK2h3senV2UYP[/IMG]

---

### Post by mc4man on 2013-07-01
Didn't see anything wrong with your screen of Dash.
Anyway as mentioned - there really isn't much to do with the unity8 build atm for users, so no big loss.

---

### Post by grahammechanical on 2013-07-01
> [COLOR=#000000]it just messed up my system [/COLOR]

That is why I experiment with an installation on another partition. Well, actually, several installations of several partitions. If things go badly wrong I can always re-install. Besides, I always have a Ubuntu that I do not mess with as standby. Then I can take a break from messing around and do some proper work (stretching the definition of both "proper" and "work" quite a bit).

Regards.

---

### Post by zika on 2013-07-02
> **MaZaMo said:**
> Thank you so much! But now there's another problem. :( The **./build -s** works, but then when I do the next command which is **./build** it comes up with this error:

**./build: 57: ./build: mk-build-deps: not found**
**-- Could NOT find Lcov (missing:  LCOV_EXECUTABLE GENHTML_EXECUTABLE) **
**-- Could NOT find gcovr (missing:  GCOVR_EXECUTABLE) **
**-- checking for one of the modules 'hud-client-2'**
**CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:363 (message):**
**  None of the required 'hud-client-2' found**
**Call Stack (most recent call first):**
**  tests/qmltests/plugins/HudClient/CMakeLists.txt:8 (pkg_search_module)**


**-- checking for module 'unity-core-6.0'**
**--   package 'unity-core-6.0' not found**
**CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:279 (message):**
**  A required package was not found**
**Call Stack (most recent call first):**
**  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:333 (_pkg_check_modules_internal)**
**  plugins/Unity/CMakeLists.txt:4 (pkg_check_modules)**


**-- checking for one of the modules 'hud-client-2'**
**CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:363 (message):**
**  None of the required 'hud-client-2' found**
**Call Stack (most recent call first):**
**  plugins/HudClient/CMakeLists.txt:5 (pkg_search_module)**


**-- Configuring incomplete, errors occurred!**
„Code“ tags would be easier to read than this bold... In my humble opinion...

---

### Post by wojox on 2013-07-02
> **MaZaMo said:**
>  but it just messed up my system and now the unity dash looks really weird.

Welcome to testing. :)

Edit: Used your linked and built it. Pretty cool. [unity 8]("http://ubuntuone.com/4zvMaUL1pGZDWW76TCD7FX")

---

### Post by Bucky Ball on 2013-07-02
> **zika said:**
> &#8222;Code&#8220; tags would be easier to read than this bold...

+1. A heads up: use code tags, please, not bold text. Bold is considered shouting and bad forum etiquette when used on large chunks of text. ;)

---

### Post by wojox on 2013-07-02
> **MaZaMo said:**
> Thank you so much! But now there's another problem. :( The **./build -s** works, but then when I do the next command which is **./build** it comes up with this error:

Got this and fixed with -c for clean, which just deletes the build directory. ```
./build -c
```

---

### Post by jerrylamos on 2013-07-05
Did a zsync of 13.10.0-2 today, fresh install.

Started down the instructions for unity8 in this thread.

It wanted to install bzr (bazaar) whatever that is.

bazaar wanted a launchpad id.  What for?  I gave it one.

bazaar wanted a shell id so the internet could shell into my pc.  That's a security exposure of the first order.

Followed all the instructions didn't work.

No idea how launchpad could shell into my pc anyway, since it is on a hidden network.

Bisarre result - no unity desktop.  No applets.  No network icon.  Nothing.

All I've got is wallpaper and a cursor, and I can open a terminal session and start firefox.  

Ctrl-Alt-Del logs out, there is a vestige of some fait applets so I could get the hidden network connected.  As a matter of policy, saucy does not automatically connect to a hidden network even though it is the only network and saucy has the key already.  Manual intervention required to tell it to connect using the info it has already.  On every boot.  That's a bear with just wallpaper and a cursor, and a terminal session with no way I know of to start system settings.  Yes there's a launchpad bug #.  Network developers not interested, it's working the way they want it to.  Automatically disconnect on boot, that is.

Could not find any way to get unity desktop back.

If unity8 pre-req is bazaar, and bazaar wants to open my pc so the internet can shell into my personal pc, I don't want any.  As far as I can tell (I hope) it won't work, I'd better re-install to wipe out all vestiges of bazaar (I hope).

---

### Post by castrojo on 2013-07-05
> **jerrylamos said:**
> If unity8 pre-req is bazaar, and bazaar wants to open my pc so the internet can shell into my personal pc, I don't want any.  As far as I can tell (I hope) it won't work, I'd better re-install to wipe out all vestiges of bazaar (I hope).

bzr doesn't open your PC to the internet, it's a version control system to check out code from launchpad.

---

### Post by mc4man on 2013-07-05
> **jerrylamos said:**
> 
It wanted to install bzr (bazaar) whatever that is.

bazaar wanted a launchpad id.  What for?  I gave it one.

If unity8 pre-req is bazaar, and bazaar wants to open my pc so the internet can shell into my personal pc, I don't want any.  As far as I can tell (I hope) it won't work, I'd better re-install to wipe out all vestiges of bazaar (I hope).

You should read, pay a little closer attention, using bzr to checkout a branch does not require a launchpad id or anything else

>  bzr branch lp:unity/8.0 ~/unity/unity8
You have not informed bzr of your Launchpad ID, and [B]you must do this [COLOR="#FF0000"]to
write[/COLOR] to Launchpad or[COLOR="#FF0000"] access private data[/COLOR][/B].  See "bzr help launchpad-login".

For what you were doing you need to do neither..

---

### Post by jerrylamos on 2013-07-05
> For what you were doing you need to do neither.. 
Thanks for the info.  I was trying to follow the directions.  Maybe there's another set of directions somewhere.

---

### Post by wojox on 2013-07-05
This the error:
> You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 68 revisions. 

---

### Post by jerrylamos on 2013-07-06
> You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data. See "bzr help launchpad-login".
Branched 68 revisions.I tried that.  Gave bzr my launchpad ID.  bzr then insisted I give it some sort of launchpad shell ID, taking the defaults, followed all the instructions to do that, and still didn't work.

Why does bzr require launchpad just to install unity8?  The bzr scripts absolutely to me refuse to install unity8 without all that launchpad stuff.  I use launchpad for bugs.  

Anyone know of the site for unity8 that would just use ppa like (x)mir does?  I tried making /unity and /unity8 directories, and put the ppa's in sources.list, but apt didn't know where to find them.

---

### Post by wojox on 2013-07-06
Post back this command:
```
bzr branch lp:unity/8.0 ~/unity/unity8
```

---

### Post by jerrylamos on 2013-07-06
> **wojox said:**
> Post back this command:
```
bzr branch lp:unity/8.0 ~/unity/unity8
```Here goes: ```
jerry@Aspire1:~$ bzr branch lp:unity/8.0 ~/unity/unity8
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Parent of "/home/jerry/unity/unity8" does not exist.  
```
Stupid question on my part, why does bzr want to "write to Launchpad or access private data." just to install unity8?

Thanks.

---

### Post by mc4man on 2013-07-06
> **jerrylamos said:**
> Here goes: ```
jerry@Aspire1:~$ bzr branch lp:unity/8.0 ~/unity/unity8
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Parent of "/home/jerry/unity/unity8" does not exist.  
```
Stupid question on my part, why does bzr want to "write to Launchpad or access private data." just to install unity8?

Thanks.
It is Not required to checkout the bzr branch, (**or Any bzr branch**) & doesn't want to, it's just 'generic' info from the bzr command

Currently your issue is you're not actually following the instructions fully, otherwise you would have created ~/unity first before running the above command

Here - I'm on 13.04 atm & obviously don't want this but still can checkout, - screen shows during the checkout

---

### Post by cariboo on 2013-07-07
@jerrylamos, you aren't reading the error message properly, you need to enter your launchpad id in order to:

> write to Launchpad or **access private data** 

I hope the part in bold makes some sense to you.

---

### Post by jerrylamos on 2013-07-07
What I get out of your comments is to ignore the bzr messages.

```
here goes:

(if this reply is too big someone who knows how to do such things can delete it)

jerry@Compaq:~$ mkdir ~/unity

jerry@Compaq:~$ sudo apt-get install bzr

jerry@Compaq:~$  bzr branch lp:unity/8.0 ~/unity/unity8

You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 68 revisions. 

jerry@Compaq:~$ cd ~/unity/unity8
jerry@Compaq:~/unity/unity8$ 

jerry@Compaq:~/unity/unity8$ ./build -s

You are about to add the following PPA to your system:
many many lines of text
0 upgraded, 72 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.8 MB of archives.
After this operation, 51.2 MB of additional disk space will be used.

Do you want to continue [Y/n]? y

many many lines of text
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
jerry@Compaq:~/unity/unity8$

./build

many lines of text
0 upgraded, 102 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 35.3 MB of archives.
After this operation, 218 MB of additional disk space will be used.

Do you want to continue [Y/n]? y

many many many lines of text
Linking CXX executable qsortfilterproxymodeltestExec
[100%] Built target qsortfilterproxymodeltestExec

jerry@Compaq:~/unity/unity8$ ./run

QML debugging is enabled. Only use this in a safe environment.
Module 'HudClient' does not contain a module identifier directive - it cannot be protected from external registrations.
file:///home/jerry/unity/unity8/Shell.qml:620:5: QML Binding: Binding loop detected for property "target"
file:///home/jerry/unity/unity8/Hud/HudParametrizedActionsPage.qml:138:5: QML Item: Binding loop detected for property "width"
__showHeader is deprecated. Do not use it.
Fail to load themed icon for: "text-plain" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/text-plain
Fail to load themed icon for: "drive-harddisk" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/drive-harddisk
many many screens of Failed....
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/help-browser
Fail to load themed icon for: "firefox" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/firefox
Fail to load themed icon for: "applications-system" 
Fail to load themed icon for: "preferences-desktop-remote-desktop" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/applications-system
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/preferences-desktop-remote-desktop
Fail to load themed icon for: "x-office-address-book" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/x-office-address-book
Fail to load themed icon for: "system-lock-screen" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/system-lock-screen
Fail to load themed icon for: "preferences-desktop-wallpaper" 
file:///home/jerry/unity/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://gicon/preferences-desktop-wallpaper 
```
Now have a "Qml Phone Shell" with 69 minutes of talk time.
Little vertical window looks a bit silly on this 1440x900 monitor.
And I don't have any apps such as firefox, terminal, office, ....  I think I saw something somewhere about how to install apps on unity8 but I forget where.

So something is running....

---

