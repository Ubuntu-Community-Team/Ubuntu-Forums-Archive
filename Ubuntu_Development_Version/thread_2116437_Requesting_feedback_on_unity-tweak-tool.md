---
title: "Requesting feedback on unity-tweak-tool"
date: 2013-02-15
forum: Ubuntu Development Version
---

### Post by jokerdino on 2013-02-15
I am part of the development team of unity-tweak-tool. Our team is working on ensuring our configuration tool gets into the repository of 13.04 and I would like the feedback of several of the power users in this sub forum on that regard.

If you haven't tried the tool yet, consider helping us with installing the PPA:

```
sudo add-apt-repository ppa:freyja-dev/unity-tweak-tool-daily
sudo apt-get update
sudo apt-get install unity-tweak-tool 
```

The package has apport support. So, feel free to submit any automatic crash reports and any other feedback that you would like to share with us. Specifically, if there is any setting that doesn't work right or doesn't work at all, we would be interested in working with the users in fixing that.

The feature freeze of 13.04 is pretty close (March 7). So, we are requesting your help in testing the most of the app to benefit the users. 

Thanks!

---

### Post by mcellius on 2013-02-15
I can't test it beyond trying to open it; it crashes on the attempt.  I was able to add myself to an existing bug report on Launchpad.

I'm running Raring, fully updated for now.

EDIT:

I tried to open it from the command line, and it never opened, but I did get the following:

> mdk@savina:~$ unity-tweak-tool
Initialising...

(unity-tweak-tool:7656): GLib-GIO-ERROR **: Settings schema 'com.canonical.indicator.bluetooth' is not installed

Trace/breakpoint trap (core dumped)

---

### Post by tdockery97 on 2013-02-15
I installed the unity-tweak-tool today, and made all of the changes I wanted to make.  I experienced no crashes or glitches whatsoever.  I am running the Ubuntu 13.04 2/15/13 daily build.

---

### Post by PJs Ronin on 2013-02-16
I installed unity-tweak-tool today on 13.04 32 bit... system was updated prior to the tweak update.   The tweak tool ran well, I made a few changes and everything seemed fine and beaut.   Didn't do serious testing as my system crashed for another reason (operator stupidity methinks).

---

### Post by zika on 2013-02-16
> **mcellius said:**
> I can't test it beyond trying to open it; it crashes on the attempt.  I was able to add myself to an existing bug report on Launchpad.

I'm running Raring, fully updated for now.

EDIT:

I tried to open it from the command line, and it never opened, but I did get the following:Same here but without „core dumped“... ;)

---

### Post by P-I H on 2013-02-16
Installed 3 days back when gnome-tweak-tool crashed.
Before I installed unity-tweak-tool I uninstalled gnome-tweak-tool by use of Software Center.
Changed theme, icons and curser style to what I wanted. Missing the feature to change icon size below 32.

Also istalled on 12.10 and it worked OK. However it crashed on the 12.10 system today after updates.

---

### Post by jokerdino on 2013-02-16
> **mcellius said:**
> I can't test it beyond trying to open it; it crashes on the attempt.  I was able to add myself to an existing bug report on Launchpad.

I'm running Raring, fully updated for now.

EDIT:

I tried to open it from the command line, and it never opened, but I did get the following:

That seems like a weird issue. Can you try installing indicator-bluetooth package and see if that helps? If that solves the issue, I can figure out a solution for this problem.

---

### Post by jokerdino on 2013-02-16
> **zika said:**
> Same here but without „core dumped“... ;)

Can you open unity-tweak-tool and see what error message you get? That would be useful in fixing the issue.

Thanks!

---

### Post by mc4man on 2013-02-16
You have to have indicator-bluetooth installed or the tool will not open

---

### Post by jokerdino on 2013-02-16
> **P-I H said:**
> Installed 3 days back when gnome-tweak-tool crashed.
Before I installed unity-tweak-tool I uninstalled gnome-tweak-tool by use of Software Center.
Changed theme, icons and curser style to what I wanted. Missing the feature to change icon size below 32.

Also istalled on 12.10 and it worked OK. However it crashed on the 12.10 system today after updates.

I'll look into the launcher icon size issue. I am not sure if it possible to set it below 32 but if it is, I'll fix that for you.

Also, can you run unity-tweak-tool from terminal and see what error message you get? That would be quite useful. Thanks!

---

### Post by jokerdino on 2013-02-16
> **mc4man said:**
> You have to have indicator-bluetooth installed or the tool will not open

That is a useful piece of info. I'll work around the issue then. Thanks.

---

### Post by mc4man on 2013-02-16
A minor issue that is also seen  elsewhere is there is no checking against bindings already set, be it compiz against unity against gnome, ect.

So just in regards to just the tool maybe nothing to be done though a little surprised it allows the same binding for different actions in the same settings window (Ex. spread

---

### Post by zika on 2013-02-16
> **jokerdino said:**
> Can you open unity-tweak-tool and see what error message you get? That would be useful in fixing the issue.

Thanks!As I wrote, the same as @mcellius```
:~$ unity-tweak-tool
Initialising...

(unity-tweak-tool:4833): GLib-GIO-ERROR **: Settings schema 'com.canonical.indicator.bluetooth' is not installed

Trace/breakpoint trap
```minus &#8222;core dumped&#8220;...
After installing indicator-bluetooth```
:~$ unity-tweak-tool 
Initialising...
Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 56, in <module>
    UnityTweakTool.init()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 118, in init
    connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 55, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 117, in <module>
    Unity.add_page(DashIcons)
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 46, in add_page
    page.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 67, in refresh
    element.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/elements/switch.py", line 70, in refresh
    type  =self.type
KeyError: 2
```

Update&#8321;: After upgrade a minute ago it works... Now I have to see why Unity is refusing to work properly... ;) It worked nice several days ago. But since there are Unity and Compiz PPAs turned on, something has changed...

---

### Post by mc4man on 2013-02-16
> **P-I H said:**
> .
Changed theme, icons and curser style to what I wanted. Missing the feature to change icon size below 32.

Going down to 8 is certainly allowed, seems the tweak tool can do this also with small edit. (in addition to ccsm, unity appearances panel hasn't been fixed here yet or ever

To test - 

```
gksudo gedit /usr/share/unity-tweak-tool/unity.ui
```

line 5, ("lower"),  change value to 8, save.

---

### Post by jokerdino on 2013-02-16
> **mc4man said:**
> A minor issue that is also seen  elsewhere is there is no checking against bindings already set, be it compiz against unity against gnome, ect.

So just in regards to just the tool maybe nothing to be done though a little surprised it allows the same binding for different actions in the same settings window (Ex. spread

That is a nifty feature. I'll see what I can do and check if a particular binding is already in use. Can't promise but I'll definitely take a look.

---

### Post by Jaybowee on 2013-02-16
It worked fine until last night I did a software update and now it wont even start when I click on the icon.

---

### Post by jokerdino on 2013-02-16
> **mc4man said:**
> Going down to 8 is certainly allowed, seems the tweak tool can do this also with small edit. (in addition to ccsm, unity appearances panel hasn't been fixed here yet or ever

To test - 

```
gksudo gedit /usr/share/unity-tweak-tool/unity.ui
```

line 5, ("lower"),  change value to 8, save.

I realize 8 pixel launcher icons are only available on 13.04. I would either have to maintain two different versions for both 12.10 and 13.04 or be lazy and stick with 32 across both the versions.

I'll talk with the rest of my team and get to this. :)

---

### Post by P-I H on 2013-02-16
This is what I get from the terminal, when launching on **12.10**.

```
p-i@pi-GA-990FXA-UD3-1210:~$ unity-tweak-tool
Initialising...
Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 56, in <module>
    UnityTweakTool.init()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 118, in init
    connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 55, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 117, in <module>
    Unity.add_page(DashIcons)
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 46, in add_page
    page.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 67, in refresh
    element.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/elements/switch.py", line 70, in refresh
    type  =self.type
KeyError: 2
p-i@pi-GA-990FXA-UD3-1210:~$ 
```

---

### Post by jokerdino on 2013-02-16
> **Jaybowee said:**
> It worked fine until last night I did a software update and now it wont even start when I click on the icon.
Can you start unity-tweak-tool and provide me any error message that you may get?

---

### Post by jokerdino on 2013-02-16
> **P-I H said:**
> This is what I get from the terminal, when launching on **12.10**.

```
p-i@pi-GA-990FXA-UD3-1210:~$ unity-tweak-tool
Initialising...
Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 56, in <module>
    UnityTweakTool.init()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 118, in init
    connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 55, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 117, in <module>
    Unity.add_page(DashIcons)
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 46, in add_page
    page.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 67, in refresh
    element.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/elements/switch.py", line 70, in refresh
    type  =self.type
KeyError: 2
p-i@pi-GA-990FXA-UD3-1210:~$ 
```
I did fix that bug earlier today. But unity-tweak-tool won't work at the moment due to another bug. 

I have fixed both the issue and the package is currently building. 

If your issue is not fixed in the package unity-tweak-tool - 0.0.3-0~68, let me know.

---

### Post by mc4man on 2013-02-16
> **jokerdino said:**
> I realize 8 pixel launcher icons are only available on 13.04. I would either have to maintain two different versions for both 12.10 and 13.04 or be lazy and stick with 32 across both the versions.

I'll talk with the rest of my team and get to this. :)

If only maintaing one source then wouldn't bother with < 32, users who desire can get in ccsm & there really isn't any reason the Appearances panel can't do also (other than no one has done so, simple 2 char source edit
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1101816](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1101816)

In 12.10 if a lower than usable value is set while initially not an issue, will just stop @ 32,  upon a restart/re-login then unity will use the default (48) in leiu of the set < 32 value.

---

### Post by mc4man on 2013-02-16
69 version starts up in absence of indicator-bluetooth & also starts in 12.10 without previous values module error.
(quick work, - also nice to see a ppa with apport hooks

---

### Post by scradock on 2013-02-16
Starting unity-tweak-tool from a terminal, with or without "sudo" leads to the following crash:

```
~$ sudo unity-tweak-tool
Initialising...
Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 56, in <module>
    UnityTweakTool.init()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 118, in init
    connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 55, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 36, in <module>
    from UnityTweakTool.section.sphagetti.unity import Unitysettings as SphagettiUnitySettings
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/sphagetti/unity.py", line 38, in <module>
    from .values import values
ImportError: No module named 'UnityTweakTool.section.sphagetti.values'
```

The latest version available through Synaptic is ~67 - no sign of ~68 or ~69 even after reloading package information.

Any ideas?

PS launchpad bug # 1127309

---

### Post by jokerdino on 2013-02-16
> **scradock said:**
> Starting unity-tweak-tool from a terminal, with or without "sudo" leads to the following crash:

```
~$ sudo unity-tweak-tool
Initialising...
Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 56, in <module>
    UnityTweakTool.init()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 118, in init
    connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 55, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 36, in <module>
    from UnityTweakTool.section.sphagetti.unity import Unitysettings as SphagettiUnitySettings
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/sphagetti/unity.py", line 38, in <module>
    from .values import values
ImportError: No module named 'UnityTweakTool.section.sphagetti.values'
```

The latest version available through Synaptic is ~67 - no sign of ~68 or ~69 even after reloading package information.

Any ideas?
The package including the bug fix just finished building. Give it a couple of minutes and then update your system.

---

### Post by P-I H on 2013-02-16
The 69 version is working now on my **12.10**

---

### Post by scradock on 2013-02-16
OK, version ~69 fixes that and is now installed. Thanks for the fast work...

---

### Post by Jaybowee on 2013-02-16
> **jokerdino said:**
> Can you start unity-tweak-tool and provide me any error message that you may get?

It wont even start for me at all. I will try to reinstall.

---

### Post by jokerdino on 2013-02-16
> **Jaybowee said:**
> It wont even start for me at all. I will try to reinstall.
I fixed a couple of bugs today. Try updating your system and see if that helps. If there is no difference, try starting unity-tweak-tool in terminal and file a bug report with that error message.

---

### Post by mcellius on 2013-02-16
> 69 version starts up in absence of indicator-bluetooth & also starts in 12.10 without previous values module error.

Same here.  Nice quick fix!

---

