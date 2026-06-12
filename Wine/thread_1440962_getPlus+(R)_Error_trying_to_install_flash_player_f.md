---
title: "getPlus+(R): Error trying to install flash player for firefox"
date: 2010-03-28
forum: Wine
---

### Post by welshsteve on 2010-03-28
Hi everyone.  Complete newbie to ubuntu

I have installed Firefox in Wine (downloaded installer, right clicked and told it to open with "Wine Windows program loader).  I'm now trying to install flash player for firefox, as it's required to run ondemand tv programs at [www.five.tv](www.five.tv) and [www.itv.com](www.itv.com) etc.  but i keep getting the following error

[B]getPlus+(R): Error
Operating system error! (16263.201.355 - 42772312.80040152.FFFFFFFF.00000000)[/B]

Is anybody able to assist?  I've tried searching for an answer but not had any luck.  I'm stumped.  I'm running Ubuntu 8.10

Many thanks in advance

---

### Post by itagomo on 2010-03-28
huh? why are you using wine just to browse with firefox? I know firefox is a built-in app in ubuntu(i'm using 9.10). Just download the adobe flash player for linux, and extract it(i know it's in a tar.gz file) to the 'plugin' folder of firefox.

to download firefox:
Open the terminal(Applications > Accessories > Terminal)
then type this:
sudo apt-get install firefox-3.6

that should download and install firefox.

---

### Post by welshsteve on 2010-03-29
> **itagomo said:**
> huh? why are you using wine just to browse with firefox? I know firefox is a built-in app in ubuntu(i'm using 9.10). Just download the adobe flash player for linux, and extract it(i know it's in a tar.gz file) to the 'plugin' folder of firefox.

to download firefox:
Open the terminal(Applications > Accessories > Terminal)
then type this:
sudo apt-get install firefox-3.6

that should download and install firefox.

The reason I'm doing this is because the tv on demand services at [www.five.tv]("http://www.five.tv"), [www.itv.com]("http://www.itv.com") and the BBC iPlayer ([www.bbc.co.uk/iplayer]("http://www.bbc.co.uk/iplayer")) do not work with Linux, or at least don't work with the version of Ubuntu I am using.  To get around the problem I thought running Firefox through wine would solve the problem.

---

### Post by itagomo on 2010-03-29
so you want to watch those episodes/shows with the use of adobe flash player in firefox, right?
then you must have the firefox version for linux and have the flash player installed.

---

### Post by welshsteve on 2010-03-29
I do have Firefox installed, and the latest version of Flash, but I still get the problem, which is why I'm trying the wine route (it was suggested to me by somebody)

---

### Post by DoktorSeven on 2010-03-29
Don't download Flash from Windows Firefox (under Wine).  The weird installer just doesn't work.

Open normal Firefox (Linux version) or whatever browser you normally use, go to Adobe's Flash download site and click the "different operating system or browser" link.  Choose Windows XP/7/etc and "flash 10 for other browsers", you'll get an EXE to download.

Run that with Wine.

You should now have Flash installed for the Windows version of Firefox under Wine.

---

### Post by ottosykora on 2010-03-30
Try following:

go to a windows machine where latest version of flash is installed and search for file 

NPSWF32.dll

this will be let say on xp in c:\windows\system32\macromed\flash

simply copy this file with an usb stick or so to \firefox\plugin where ever this is on your wine installation. Restart your wine ff and you have the latest flash ready.

This way you can bypass all that nonsense of get-plus introduced by adobe. This getplus tries to install itslef to specific windows folders which are  not existing on your wine install, thus it fails and can not install the flash itself later.

---

### Post by welshsteve on 2010-03-31
Thanks guys I'll try these options

---

### Post by donkyhotay on 2010-03-31
You can also try using the user agent switcher and changing it to windows. A lot of websites query the browser for what OS is running and if detecting something besides windows report "not compatible". In reality it's because they just don't want to do any testing for other OS's while it can often work just fine. The user agent switcher simply reports your computer as a different OS to get past those checks. Doesn't always work (some sites really are incompatible) but it does work more often then not and it's pretty much the first thing I try whenever I go to a site that says "windows only" or "IE only".

---

### Post by bikerelc on 2010-07-22
I have been futzing with this error for a while now, I think I have it figured out although the solution kind of stinks.  
Go to adobe's site and when you click other operating systems choose Windows 98/ME, and try installing that .exe file instead.  It worked or appears to have worked for me.  I have some rendering issues in anything but fullscreen but my graphics card is glitchy even running flash natively.

---

### Post by asdfoo on 2010-07-22
> **welshsteve said:**
> Hi everyone.  Complete newbie to ubuntu

I have installed Firefox in Wine (downloaded installer, right clicked and told it to open with "Wine Windows program loader).  I'm now trying to install flash player for firefox, as it's required to run ondemand tv programs at [www.five.tv](www.five.tv) and [www.itv.com](www.itv.com) etc.  but i keep getting the following error

[B]getPlus+(R): Error
Operating system error! (16263.201.355 - 42772312.80040152.FFFFFFFF.00000000)[/B]

Is anybody able to assist?  I've tried searching for an answer but not had any luck.  I'm stumped.  I'm running Ubuntu 8.10

Many thanks in advance

If you're still trying, make sure you have the latest version of Wine (1.2).  

Post the terminal output here if it still fails

---

