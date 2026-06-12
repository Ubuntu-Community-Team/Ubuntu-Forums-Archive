---
title: "chrome says your time is ahead on windows xp"
date: 2021-08-04
forum: Virtualisation
---

### Post by snype9lives on 2021-08-04
alright so, im having major issues when it comes to chrome on a windows xp vm and I wanna know if there is some sort of bypass to this (god please do) cause this is a huge pain.

---

### Post by MAFoElffen on 2021-08-04
Please explain the problem. Seems a bit vague so far...

LOL! (Saw the reason for the Edit!!!)

EDIT: Are you meaning that Chrome is warning you that it is ending support for XP? It alread has ended support for XP. So has Opera and Firefox. Just as have all ended support for Vista.

If it is already installed and warning you that it's time is near... There is this article, but do not follow this advice at all... I'm just posting it as aan example of bad advice: [https://www.askvg.com/tip-disable-windows-xp-and-vista-will-no-longer-be-supported-yellow-infobar-in-google-chrome/](https://www.askvg.com/tip-disable-windows-xp-and-vista-will-no-longer-be-supported-yellow-infobar-in-google-chrome/) 

it will disable all pop-up advice in chrome and cripple it. What you want todo is just turn off the resident google-update and it's own notifier... So that it doesn't check for updates, install it automatically behind your back, and all of a sudden not be working at all. That is only a temporary fix, Eventually, without browser updates, the website certs will be outdated.

If that is what you are describing, and if you need instructions to do that, I will deal with that in a followup post...

---

### Post by Skaperen on 2021-08-04
> **snype9lives said:**
> alright so, im having major issues when it comes to chrome on a windows xp vm and I wanna know if there is some sort of bypass to this (god please do) cause this is a huge pain.

ask each system what time it is and let us know.

Windows normally works with the hardware clock set to local time.  Linux works with the hardware clock set to UTC time.  if Windows starts up with the hardware clock on UTC and your local time is west of UTC then Windows time will be ahead some number of hours.  i don't know how to set Windows to do UTC but if you can find out how, that might be the best solution for you.  another might be to configure the VM engine to always start the clock X hours back (local time).  but then Linux would have trouble in that VM.  if you dedicate a VM to each system you run, that could solve that issue.

a good VM would detect the time offset the guest OS sets and save the difference so the next time it starts up, the guest OS sees the time the way it set it.

---

### Post by MAFoElffen on 2021-08-04
See this IS why I need more info... We are talking about a browser that was not supporting any updates for Windows XP since April 2016...

Maybe it is time to install another browser that still supports Windows XP, such a K-Meleon? Is a fork of FireFox.

If it is just time, this is not a Chrome Browser thing. But rather a Windows system thing. If you go to Windows Control Panel > Time and Date > There is a setting to set by network time... Even then, even with Windows 10... Sometimes you have to set this off and on every once in a while for it to reset, to work right.

---

### Post by snype9lives on 2021-08-05
I found out a fix. but thanks ig

---

### Post by QIII on 2021-08-05
Would you care to share the solution you found so that the next poor user who runs into this issue doesn't have to thrash through the thorn patches alone?

---

### Post by snype9lives on 2021-08-07
Go to propertys of chrome and put  --ignore-certificate-errors  in shortcut bar.

---

### Post by CharlesA on 2021-08-08
> **snype9lives said:**
> Go to propertys of chrome and put  --ignore-certificate-errors  in shortcut bar.



That is never a good idea. Setting that property will cause Chrome to accept all certificates, even if they are invalid or expired. It might "work" for your issue, but its not something you should be if you care about security.

With that said, you shouldn't be getting certificate errors if your time is off unless you are close to the time the certificate expires. Without more information (which you did not provide), it's hard to tell why you were having the problem in the first place.

---

### Post by MAFoElffen on 2021-08-08
See Post #4. He's getting certicate erors ebcause the certs have not been updated since April 2016, along with any other updates... 

He would be better off going to a Browser that support outdated Windows versions. At least then it would have current security updates, including trusted sites (certificates).

---

### Post by CharlesA on 2021-08-08
> **MAFoElffen said:**
> See Post #4. He's getting certicate erors ebcause the certs have not been updated since April 2016, along with any other updates... 

He would be better off going to a Browser that support outdated Windows versions. At least then it would have current security updates, including trusted sites (certificates).

Thanks! That would definitely explain it because Chrome uses the Windows certificate store and any changes to that are pushed out via Windows update.

I don't think Firefox does by default, but like you mentioned, finding an update-to-date browser that supports XP is going to be difficult.

Now, with all that said, I just downloaded and installed Chrome on one of my XP VMs - I see the time is correct in Windows and Chrome isn't complaining about the time being wrong, even if I change the time. However, when the installer downloaded Google Chrome, it grabbed version 49.0.02623.112, which is ancient.

I did get a message when I first launched Chrome that said "This computer will no longer receive Google Chrome updates because Windows XP and Windows Vista are no longer supported", but that's to be expected with a browser release that was out in 2016 and an OS that ended support in 2016.

FWIW, I wasn't getting certificate errors, even when accessing sites like microsoft, amazon, bing, etc. The last time updates were installed on that box was back in 2014 - with the exception of [KB4012598]("https://www.microsoft.com/en-us/download/details.aspx?id=55245"), which was installed 5/25/2017. It's very possible the root certificates were updated after that, but it's hard to tell since it isn't listed in the list of Windows Updates for me.

Without more info from the OP about what specific error they were getting, it's unlikely we'd be able to guess as to what it wrong with their certificates.

---

### Post by MAFoElffen on 2021-08-09
Yes... He needs to know that that is going to happen with Windows Explorer, Chrome, Firefox, and Opera. All those stopped support (and any updates) for XP and Vista years ago.

The best alternative  that I have found for running old Windows VM's is K-Meleon. It supports Windows NT through Vista... and is based on Gecko/Mozilla.
> [h=3]System Requirements[/h]    
[LIST]
[*] Windows 95, 98, 98SE, ME, Windows NT 4.0, Windows 2000 or Windows XP
[*] 32 MB RAM minimum
[*] 4 MB of free hard disk space for download. 11.0 MB of free hard disk space for installation.
[*] Users running Windows95 and/or versions of Internet Explorer  older than 5.0 need to download and install the Common Control Library  from Microsoft: [http://www.microsoft.com/msdownload/ieplatform/ie/comctrlx86.asp](http://www.microsoft.com/msdownload/ieplatform/ie/comctrlx86.asp): 50comupd.exe (x86)
[/LIST]


---

