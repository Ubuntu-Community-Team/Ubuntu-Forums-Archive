---
title: "So I've installed winetricks and have a gui..."
date: 2010-11-24
forum: Wine
---

### Post by egkeat on 2010-11-24
So what packages do I need for Office 2007 to work in Ubuntu 10.04?

---

### Post by kroq-gar78 on 2010-11-24
[http://mediakey.dk/~cc/howto-office-2007-on-linux-with-wine/]("http://mediakey.dk/%7Ecc/howto-office-2007-on-linux-with-wine/")

this should help

---

### Post by egkeat on 2010-11-24
...not ready for all that yet....
I'll stick with the current word processor.  Was just wanting to get Office 2007 Vista to work with Ubuntu 10.04.  KOffice doesn't save .doc format, Openoffice...yuck... and AbiWord seems to send my processor spiraling out of control. I dunno...My version of Home and Student can only be installed 3 times. I've already done that twice on mine (after a Windows crash) and once on my son's pc.  Could that have anything to do with it?

---

### Post by marl30 on 2010-11-24
These are what I usually install:
1. corefonts
2. font fix
3. fontsmooth rgb
4. wsh56js
5. allfonts

Then install Office 2007

After the installation has completed, go to Wine Configuration> Libraries > New overrides for library. Then type each of the following along with setting the appropriate fields:

  Riched20 - Press enter. While riched20 is highlighted, click on edit and set the field to: Native (Windows)

 usp10 - press enter.

Office 2007, Word, Excel, and PowerPoint should now be working perfectly.

---

### Post by egkeat on 2010-11-24
> **marl30 said:**
> These are what I usually install:
1. corefonts
2. font fix
3. fontsmooth rgb
4. wsh56js
5. allfonts

Then install Office 2007

After the installation has completed, go to Wine Configuration> Libraries > New overrides for library. Then type each of the following along with setting the appropriate fields:

  Riched20 - Press enter. While riched20 is highlighted, click on edit and set the field to: Native (Windows)

 usp10 - press enter.

Office 2007, Word, Excel, and PowerPoint should now be working perfectly.


SUCCESS!!!
but now when I try using Word, it's graying in and out.  Unusable.  What'd I do wrong this time?

---

### Post by egkeat on 2010-11-25
Ok...
So Excel works perfectly.  Word, Powerpoint, and OneNote go gray every ten seconds and the office startup screen blinks in ever so often.

---

### Post by marl30 on 2010-11-25
> **egkeat said:**
> Ok...
So Excel works perfectly.  Word, Powerpoint, and OneNote go gray every ten seconds and the office startup screen blinks in ever so often.

try this in terminal and see if it helps: wineboot --update

It works for me, both under Wine 1.2.1, and version 1.3.7

I hope you didn't install riched20 and usp10, they were only to be edited from Libraries not installed from Winetricks.

---

### Post by marl30 on 2010-11-25
You could also take a look at this video of how Office 2007 is configured in Wine.[http://www.youtube.com/watch?v=Pew3v-CA0xI&feature=related](http://www.youtube.com/watch?v=Pew3v-CA0xI&feature=related)

The person in the video also installed vc2005sp1 from Winetricks. The newer tutorials for newer Wine versions don't have this, but you could install it as well to see if it improves performance. Install Tahoma too. This will Wine prove the visual fonts. 

If you can't get it to work, I'll take you through a step-by-step instruction on setting up Windows in VirtualBox.

---

### Post by egkeat on 2010-11-25
This is what happened:

~$ wineboot --update
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:iphlpapi:NotifyAddrChange (Handle 0xa5de8d8, overlapped 0xa5de8e0): stub
wine: configuration in '/home/curve/.wine' has been updated.
fixme:exec:SHELL_execute flags ignored: 0x00004000
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
:~$ fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 19660) semi-stub
fixme:keyboard:RegisterHotKey (0x40244,78,0x00000008,4E): stub
fixme:heap:RtlCompactHeap (0x110000, 0x0) stub

Word, Powerpoint, and Onenote fades gray and the startup blinks in for a  second...  I did check the green update button when installing, and  yes, I did install riched20 and usp10 from winetricks 
(I've had to typeover some of the colons because it keeps displaying as smileys in the message...sorry, I'm really knew to this)

---

### Post by marl30 on 2010-11-26
> **egkeat said:**
> This is what happened:

~$ wineboot --update
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
errole:CoCreateInstance apartment not initialised
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:iphlpapi:NotifyAddrChange (Handle 0xa5de8d8, overlapped 0xa5de8e0): stub
wine: configuration in '/home/curve/.wine' has been updated.
fixme:exec:SHELL_execute flags ignored: 0x00004000
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
:~$ fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 19660) semi-stub
fixme:keyboard:RegisterHotKey (0x40244,78,0x00000008,4E): stub
fixme:heap:RtlCompactHeap (0x110000, 0x0) stub

Word, Powerpoint, and Onenote fades gray and the startup blinks in for a  second...  I did check the green update button when installing, and  yes, I did install riched20 and usp10 from winetricks 
(I've had to typeover some of the colons because it keeps displaying as smileys in the message...sorry, I'm really knew to this)

That is why it is unstable, you should never have installed those, you were only to add them in Libraries like you saw the guy did in the video. On the Wine site they said that installing them will make Office unstable because Wine has already installed them by default. They only required library entries to serve as overrides so Word, Excel, and PowerPoint can work properly. Don't worry, I understand. :) I'm still fairly new too. I've messed up Wine a whole lot before I finally got it right through following the Wine site. I'll be patient with you. If Office was the only thing you had installed in Wine, you may need to reset the Wine folder and start over again. Don't worry, I'll try to help you through until you get it. :) just let me know if you want to try it again.

---

### Post by egkeat on 2010-11-26
> **marl30 said:**
> That is why it is unstable, you should never have installed those, you were only to add them in Libraries like you saw the guy did in the video. On the Wine site they said that installing them will make Office unstable because Wine has already installed them by default. They only required library entries to serve as overrides so Word, Excel, and PowerPoint can work properly. Don't worry, I understand. :) I'm still fairly new too. I've messed up Wine a whole lot before I finally got it right through following the Wine site. I'll be patient with you. If Office was the only thing you had installed in Wine, you may need to reset the Wine folder and start over again. Don't worry, I'll try to help you through until you get it. :) just let me know if you want to try it again.


Yes...  Looks like I will need your help on this.  I've installed my other word processor but as long as I can get it reinstalled, I'll willing.  Thanks for being patient with me.:)

---

### Post by Elfy on 2010-11-26
moved to wine

---

### Post by marl30 on 2010-11-26
> **egkeat said:**
> Yes...  Looks like I will need your help on this.  I've installed my other word processor but as long as I can get it reinstalled, I'll willing.  Thanks for being patient with me.:)

Hey, sorry for taking so long to reply. Ok lets get started with setting up Wine so you can install Office 2007. First, we are going to reset the Wine directory back to default to get rid of the bad configuration.

Run this command to reset Wine:```
rm -rf ~/.wine
```

After resetting Wine, run this command to boot and update Wine:```
wineboot --update
```

Now time to configure Wine so that it will run Office 2007, and also that the fonts in Wine will look a lot better. You'll need Winetricks for this. 

Enter winetricks in terminal. You are going to check the following Windows packages for installing into wine:

1. corefonts
2. dotnet2
3. fontfix
4. fontsmooth-rgd
5. msxml3
6. msxml4
7. msxml6
8. tahoma
9. wenquanyi
10. wsh56js
11. allfonts

Only install those that I have in this list. You'll notice that I have more listed here than what I gave initially. This is because I added some to make the font in Wine look a lot smoother, plus I've also added a few packages that I had seen Crossover and PlayonLinux install when I was testing Office 2007 on them both. 

After the packages have finished installing, run the wine reset update command before you start installing Office 2007: wineboot --update

After installing Office 2007, do not open any of the Office 2007 program's before entering the library overrides!

Go to Wine>  Wine Configuration > Libraries > New override for library: enter riched20. Highlight it, then click edit, and set to native (Windows), then click ok. 

Enter another new override for library: usp10, then click enter. Click apply. 

Go back to the applications menu and make sure Wine is set to Windows XP. Then click ok to close Wine configuration. 

Now you can scroll to Office 2007 and to check if Word, Excel, and PowerPoint are working properly. 

I hope this helps you. :)

---

