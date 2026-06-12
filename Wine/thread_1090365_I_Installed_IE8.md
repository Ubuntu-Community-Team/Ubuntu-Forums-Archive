---
title: "I Installed IE8"
date: 2009-03-08
forum: Wine
---

### Post by MasterPoulos89 on 2009-03-08
I first installed winetricks in order to install the following:

code:
winetricks ie6 comctl32 comctl32.ocx corefonts gdiplus gecko msls31 msxml3 msxml4 msxml6 riched20 riched30 tahoma

Then you can easily run the IE7 installer which you can download from Microsoft. It installs and runs successfully. Run it from "wine/c:program files/internet explorer/iexplorer.exe. Its a lil glitchy ofcource but it runs.

Then I go to run the IE8 installer which you can also download from Microsoft. The installer starts up fine and runs. When it tries to install updates before install it fails and says "cannot install important update" or something like that. Then it asks if you want to manually download the file. if you click download it will open in IE7 if you installed it but you cant download it cause its not fully functional.

Here is a link to the update necessary for IE8: 

[http://mytopfiles.com/programs/file/WindowsXP-KB932823-v3-x86-ENU/246359.htm](http://mytopfiles.com/programs/file/WindowsXP-KB932823-v3-x86-ENU/246359.htm)

After installing this you can then install IE8. My problem is that after it installs I try to run it from the same location mentioned above but nothing happens. 

So I was wondering if since I got this far then maybe someone who knows a lil more then I do can copy the steps and tell me if there is anything that can be done to make IE8 run after install or if maybe I should just wait for the final release.

Any one wondering why I need IE8 at all The answer is partially just for the hell of it but also cause it helps wine sometimes like for combat arms. With this method combat arms runs and pretty good since I installed IE7 but the mouse still glitches. Maybe With IE8 combat arms as well as other programs can run with less glitches.

Thanks in advance for any help.

---

### Post by Meow27 on 2009-03-08
you might want to use the [code] code for quoting commands :/

---

### Post by MasterPoulos89 on 2009-03-08
Thanks.....I know better for next time.

Anyone have any advice for IE8

---

### Post by cogadh on 2009-03-08
My only advice is don't bother for now. No version of IE has really worked with Wine since IE 5.5, other than by using [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") and IE8 currently has a "garbage" rating on [Wine's AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11110"). That may change as Wine develops, but for now you are likely wasting your time.

---

### Post by RaiCoss on 2009-03-08
> **MasterPoulos89 said:**
> I first installed winetricks in order to install the following:

code:
winetricks ie6 comctl32 comctl32.ocx corefonts gdiplus gecko msls31 msxml3 msxml4 msxml6 riched20 riched30 tahoma

Then you can easily run the IE7 installer which you can download from Microsoft. It installs and runs successfully. Run it from "wine/c:program files/internet explorer/iexplorer.exe. Its a lil glitchy ofcource but it runs.

Then I go to run the IE8 installer which you can also download from Microsoft. The installer starts up fine and runs. When it tries to install updates before install it fails and says "cannot install important update" or something like that. Then it asks if you want to manually download the file. if you click download it will open in IE7 if you installed it but you cant download it cause its not fully functional.

Here is a link to the update necessary for IE8: 

[http://mytopfiles.com/programs/file/WindowsXP-KB932823-v3-x86-ENU/246359.htm](http://mytopfiles.com/programs/file/WindowsXP-KB932823-v3-x86-ENU/246359.htm)

After installing this you can then install IE8. My problem is that after it installs I try to run it from the same location mentioned above but nothing happens. 

So I was wondering if since I got this far then maybe someone who knows a lil more then I do can copy the steps and tell me if there is anything that can be done to make IE8 run after install or if maybe I should just wait for the final release.

Any one wondering why I need IE8 at all The answer is partially just for the hell of it but also cause it helps wine sometimes like for combat arms. With this method combat arms runs and pretty good since I installed IE7 but the mouse still glitches. Maybe With IE8 combat arms as well as other programs can run with less glitches.

Thanks in advance for any help.

It also nails the WINE defacto iexplore.exe to a cross and cremates it, i.e. its a very, very bad idea.

---

### Post by MasterPoulos89 on 2009-03-09
Thanks for the responses. I guess I'll wait for a better time.

Unless anyone else has anything else to say.

---

### Post by UbuntuNerd on 2009-03-09
> **MasterPoulos89 said:**
> Thanks for the responses. I guess I'll wait for a better time.

Unless anyone else has anything else to say.
any reason you want to use IE?

---

### Post by Meow27 on 2009-03-09
> **UbuntuNerd said:**
> any reason you want to use IE?

IE doesnt have a bad gui.......


i used to be a bg fan of ie7. but i think id rather have it for linux. id probably be faster than firefox on linux, heck firefox in Wine is faster than firefox native!

---

### Post by MasterPoulos89 on 2009-03-10
Maybe native Linux Firefox does run slow as people say, but for me it seems to run as good as anything else I've used including IE. The only think I've noticed to be a problem is the buggy Linux flash player, but I can deal with that. But that has nothing to do with why I'm trying to install IE8 on wine.

As I said before, IE helps wine for certain things. After installing IE6 Combat Arms installs Flawlessly but doesn't run. After IE7 It runs but its a bit glitchy. Im wondering if IE8 will fix it if it can install properly. And if so then IE is definitely helping wine maybe even for different programs.

I think Mac and Linux biggest problem is games because everything else pretty much has a way to be done natively. 

Microsoft Office is an other important program for any OS to have. I'm not saying Open Office Isn't just as good. But Microsoft office is pretty popular and .doc files are not fully compatible with Open Office. Microsoft Office 2000 installs pretty flawlessly and 2007 as well although 2007 crashes when I open a couple of menu files I made for my uncles restaurant. But you may not have those problems.

Also Aim is another program that is not necessary but Pidgin And Kopete Don't really compare to aim. Aim does not work with wine. Not the recent versions anyway, I think 5.9 works but your better off with Pidgin or Kopete instead of Aim 5.9.

---

### Post by PomCompot on 2009-04-08
Honestly, I'm quite interested in getting IE8 working on Linux, just to see the rendering as I am conceiving a web site. IEs4linux seems pretty dead since 02/2008 on the blog. IE7 integration still in beta in the last version, and no information on a future IE8 integration.

MasterPoulos89, considering your will to get MSOffice, AIM and IE8 working under Wine for a regular use, I think you don't get the good approach. I you want to get all Windows specific apps working on Linux, you'd better use a virtual machine with Windows inside Linux.

---

### Post by NAVOKAR on 2009-10-21
Just installed IE6 as made available through Wine-Doors which was installed yesterday.  IE6 runs so slow it is frustrating.  1st thought was that I need more memory.  I have 2GB.  After exiting IE6 everything works fast--no problems.
System is dual boot Windows Vista/Linux Mint w Firefox & Thunderbird.  Sometimes I need IE for applications not friendly w Firefox and I do not like having to reboot into Windows for IE.
Also wondering if using Crossover--Wine might provide better performance.
Any ideas would be appreciated.

---

### Post by pascat on 2009-11-18
Isn't there a VM software capable of using Hardware VM Acceleration in Linux? I'd have thought some people of the community would have done that by now, and allowed to run Actual Windows XP under Linux. (Then you install your IE8 in Windows XP, and Voilà!) ...
Who knows, since you're alreayd Dual-booting, maybe you could even load your actual Windows in the VM for IE. I've never tried VM personally.

---

### Post by mahirh on 2010-02-02
> **MasterPoulos89 said:**
> I first installed winetricks in order to install the following:

code:
winetricks ie6 comctl32 comctl32.ocx corefonts gdiplus gecko msls31 msxml3 msxml4 msxml6 riched20 riched30 tahoma

sir, the code really should be ```
sh winetricks ie6 comctl32 comctl32.ocx corefonts gdiplus gecko msls31 msxml3 msxml4 msxml6 riched20 riched30 tahoma
```
it needed a "sh"

---

### Post by Dooglus on 2010-11-09
I played around for a few hours trying to get IE8 to work in Ubuntu 10.10, but had no luck.  I had received complaints that a web page I designed wasn't rendering correctly in IE8 and wanted to see for myself.

In the end I found a website which lets me see how any page looks in IE8 (and older versions of IE too).

It's here: [http://ipinfo.info/netrenderer/](http://ipinfo.info/netrenderer/)

You give it the URL, tell it which version of IE to use, and it shows you an image of how that version of IE renders it.

That way they end up with all the malware, not me.  :)  Yay!

---

### Post by Thelinuxgeek on 2010-11-10
Um, why do you want to install IE in Ubuntu? IE is like the slowest thing ever! But anyway, thank you for the useful tip. Very Informative!        :P

---

### Post by Bar2D2 on 2011-01-23
Unfortunately, some website (tools) still need IE :(
Garmin is an example, The registration page does not work with Firefox or Chrome [https://my.garmin.com/mygarmin/customers/myGarminHome.faces](https://my.garmin.com/mygarmin/customers/myGarminHome.faces)

---

### Post by trinitydan on 2011-01-23
> **Bar2D2 said:**
> Unfortunately, some website (tools) still need IE :(
Garmin is an example, The registration page does not work with Firefox or Chrome [https://my.garmin.com/mygarmin/customers/myGarminHome.faces](https://my.garmin.com/mygarmin/customers/myGarminHome.faces)

While I hate to admit any weakness in open source alternative software, unfortunately it is true that you just can't operate some websites using Firefox.  It really is a shame.  Being that I don't have a Windows computer at all, I have no way of using these sites currently.  Is there a browser we can install that will have a better chance of working with sites that don't work with Firefox?

---

### Post by I@1n on 2011-03-01
Just started a uni grad dip course - the online lab only supports IE7 or 8... no firefox or linux support...if anyone knows any fixes...?

---

### Post by Tweak42 on 2011-03-01
> **I@1n said:**
> Just started a uni grad dip course - the online lab only supports IE7 or 8... no firefox or linux support...if anyone knows any fixes...?

Windows XP in a VirtualBox VM?  My school has an Academic agreement for MS software so enrolled students can requisition use of most MS software.  Using a VM probably is the only sure fire you won't run into any compatibly/plugin problems running IE.

---

