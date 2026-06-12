---
title: "Gecko doesn't install correctly"
date: 2010-01-13
forum: Wine
---

### Post by tiatlon on 2010-01-13
I've downloaded latest wine 1.1.36 and it seems that gecko is not installed correctly

when I try:
wine iexplore [http://www.winehq.org](http://www.winehq.org)
I get:

===================================
Warning: could not find DOS drive for current working directory '/home/tiatlon', starting in the Windows directory.
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
err:mshtml:check_version Could not open VERSION file
err:mshtml:check_version Could not open VERSION file
Could not load wine-gecko. HTML rendering will be disabled.
err:mshtml:HTMLDocument_Create Failed to init Gecko, returning CLASS_E_CLASSNOTAVAILABLE
fixme:ole:CoCreateInstance no instance created for interface {00000000-0000-0000-c000-000000000046} of class {25336920-03f9-11cf-8fd0-00aa00686f13}, hres is 0x80040111
===================================

I've tried manual install from here: [http://ubuntuforums.org/archive/index.php/t-634464.html](http://ubuntuforums.org/archive/index.php/t-634464.html) but it did not help.

---

### Post by Soulcage on 2010-01-14
Did you install wine1.2-gecko on karmic? Or wine-gecko pre-karmic?
sudo apt-get install wine1.2-gecko
Thats how I install not sure if its a dependency now in karmic.

---

### Post by wolpertinger on 2010-06-30
Hello, 

I am exploring the forums to find a solution to this issue, but not really found the good trick.
I have wine1.2 but get a similar message while, installing a game(wow), the acceptance EULA  pop (with a error message).


Exactly for the corresponding part:

boxfixme:shdocvw:PersistStorage_InitNew (0x17a1d8)->(0x597d98)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
err:module:import_dll Loading library xul.dll (which is needed by L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\xpcom.dll") failed (error c0000017).
err:module:import_dll Loading library xul.dll (which is needed by L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\xpcom.dll") failed (error c0000017).
Could not load wine-gecko. HTML rendering will be disabled.
err:mshtml:HTMLDocument_Create Failed to init Gecko, returning CLASS_E_CLASSNOTAVAILABLE
fixme:ole:CoCreateInstance no instance created for interface {00000000-0000-0000-c000-000000000046} of class {25336920-03f9-11cf-8fd0-00aa00686f13}, hres is 0x80040111

Any suggestion is welcome
Thx

---

### Post by dino99 on 2010-06-30
wine1.2-gecko 1.0.0.-0ubuntu4 work without issue here

sometimes .wine folder need to be removed, use synaptic to remove/purge then reinstall the packages (can use winetricks too in case)

---

