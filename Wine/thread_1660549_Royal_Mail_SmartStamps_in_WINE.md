---
title: "Royal Mail SmartStamps in WINE?"
date: 2011-01-05
forum: Wine
---

### Post by Subtlelegance on 2011-01-05
Hello everyone, 

I am completely new to Ubuntu, having installed 10.10 earlier today. First impressions are: it's brilliant. 

I'm hoping to be able to run Royal Mail's Smartstamps program, unfortunately only available as Windows software, in WINE but am having no luck thus far. The .exe installer will start to run, but upon install almost immediately gives the error message 'The program IDriver.exe has encountered a serious problem and needs to close.' Has anybody been able to get Smartstamps up and running? Or perhaps someone can suggest an approach to try? Any help would be greatly appreciated! (particularly because I'm in the unfortunate position of the functionality this software possibly being a deal-breaker as to whether I can use Ubuntu)

Thank you,
Ray :-)

---

### Post by matt_symes on 2011-01-05
Hi

> The SmartStamp® system requirements for your PC are:
A CPU of 200 MHz minimum
64 MB RAM
20 MB free hard-drive space.
Your computer should be running one of the following operating systems:
Windows® 2000 (Server & Professional, SP2 & SP3) 
Windows® NT (4.0 Server & 4.0 Workstation, SP6 & SP6a) 
Windows® XP (Home & Professional) SP1
 Windows® Vista

SmartStamp® requires Microsoft Internet Explorer 5.01 or above. 

I have never used this service, but i am wondering about its dependencies on internet explorer. Maybe try to install IE under wine?

I might have a go at installing the trial version under wine tomorrow (along with IE). If i do and i can get it working i will post back. In the meantime hopefully someone from the UK will have tried this. A perfunctory search turned up no leads. 

Kind regards

---

### Post by Subtlelegance on 2011-01-06
That's brilliant thank you, I will try installing IE as you suggest later today.

Ray :-)

---

### Post by Subtlelegance on 2011-01-08
I installed Internet Explorer 7 in WINE as suggested in case of dependencies and that program works fine, but installation of Smartstamp still fails. 
The .exe installer runs but gives four error messages during installation:

1: 1904 2: C:\Program Files\Royal Mail\SmartStamp\BINARY\SASEBAY.OCX 3: -2147220473

1: 1904 2: C:\Program Files\Royal Mail\SmartStamp\BINARY\SSTOOLS.OCX 3: -2147220473

1: 1904 2: C:\Program Files\Royal Mail\SmartStamp\BINARY\SASADCTL.OCX 3: -2147220473

1: 1904 2: C:\Program Files\Royal Mail\SmartStamp\BINARY\ICWIZARD.OCX 3: -2147220473

After hitting 'OK' through these messages, the installer finishes but when the program is launched Smartstamp fails to start. ('Starting SmartStamp' appears for a few seconds then vanishes)

If anybody has any further suggestions they would be hugely appreciated. I have a (very) small business and was hoping to migrate from Windows to Ubuntu. I have found native programs that do absolutely everything else I need, but Smartstamp is critical because unfortunately it is the only way to print Royal Mail stamps and they don't provide a Linux version (I've pestered them about that to no avail) The alternative is waiting in the Post Office every day.

I don't want to have to stick with Windows because of one crappy but necessary program and lack of forward thinking from Royal Mail - help!

Thanks a lot :-)

---

### Post by cascade9 on 2011-01-08
Seems like SmartStamps doesnt like WINE much- 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4122](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4122)

You might be able to get it going, but that doesnt look hopeful.

If worst comes to the worst, you can run Windows in a virtual machine.

---

### Post by Subtlelegance on 2011-01-08
Thinking about it, because I was struggling to install Internet Explorer, I installed both it and Smartstamp using PlayOnLinux, which runs all applications in different prefixes of WINE. So Smartstamp probably isn't actually benefiting from any of the potentially useful bits of Internet Explorer.

I scrapped PlayOnLinux and installed Internet Explorer 7 using these instructions [http://yokozar.org/blog/archives/236](http://yokozar.org/blog/archives/236) found through a google search, but when installing Smartstamp I get exactly the same errors and results as before.

---

### Post by Subtlelegance on 2011-01-08
Yeah, looks like I'm stuffed. Thank you for looking anyway :-)


> Seems like SmartStamps doesnt like WINE much- 

[http://appdb.winehq.org/objectManage...ation&iId=4122](http://appdb.winehq.org/objectManage...ation&iId=4122)

You might eb abel to get it going, but that doesnt look hopeful.

---

### Post by cascade9 on 2011-01-08
Sorry I couldnt help.

---

