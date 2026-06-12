---
title: "Telechart from  Wordem Brothers in Wine"
date: 2008-12-11
forum: Wine
---

### Post by gallo2000sv on 2008-12-11
Hello everybody, i have been trying to install this software in my ubuntu 8.04 using wine 1.0 and finally i did it after search in google and everywhere and have some unofficial support from Wordem but now i have a problem and i can't solve it.

When im working in telechart suddenly closes without any messages or something.

Sometimes Telechart freezes and have to kill the process because is not responding.

If anyone want to help me.

Thanks

NOTE:  I'm using Telechart Gold Version this is a free charts software, and only have a $29.99 monthly charge for the update.

---

### Post by gallo2000sv on 2008-12-13
Please Anyone can help me with this? I really need it.
I know that is a little stupid using windows software in ubuntu but this is for my work, and is the only one windows software that i can't sustitute for other ubuntu software.

I'll be trying to find another stock charts software for ubuntu, but for my needs this other softwares are not enought. 

This is what i have tested:
LinuxTrade 
QtStalker
aiotrader
SMTM
Grism

If any one can give another choices. If is necessary, i will pay for the data updating, as i'm paying for telechart data.

But i really want to run Telechart in ubuntu.

Thanks.

---

### Post by rwk2095 on 2008-12-25
Have you made any progress with this?  I am just starting to investigate migrating to Linux, and Telechart is a must-have app for me.

[Richard]

---

### Post by gallo2000sv on 2008-12-27
I have finally Telechart working in ubuntu 8.04
This is what i did, i hope this help you:
1. Install Wine 1.0
2.Install Telechart and you maybe get some error message like:
SFserver: TrendLine error invalid property value

3.You can fix it installing this: [ftp://nero.worden.com/Font-Arial.exe](ftp://nero.worden.com/Font-Arial.exe)

With this you  will have telechart working fine, but still is some errors:  

1. The button Shift - or Shift + for changind scale does not work.
2. When you make the updates after that telechart will show some error messages like:

SFServer Error Bad Create, or WebPro3 Error Bad create.
see this image:
[http://www.motivacionfinanciera.com/imagenes/Telechar-Error.png](http://www.motivacionfinanciera.com/imagenes/Telechar-Error.png)

When you get this message you have to kill (close) Telechart (right click and close) and open again, and you will have telechart running, without any error until your next update, then you have to do the same.

I tried to fix it installing Visual basic runtime libraries from wine-doors. But still have this problem.

Anyone knows how to solve this?  
thanks.

---

### Post by rwk2095 on 2008-12-28
I installed Telechart using CrossOver, and it looks OK, but it is too slow and too unstable to be usable.  If the problem was a missing DLL or font, I think I could fix it, but this situation has me stumped.  At this point, I doubt that I will get it working satisfactorily.

---

### Post by rwk2095 on 2008-12-30
I just got feedback from Codeweavers.  It's their guess that Telechart is using .NET architecture, and they doubt that it can ever be made to run satisfactorily under CrossOver (and by implication, Wine).  I will probably give up on trying to get it to run.

---

### Post by mohe88888 on 2009-01-18
I want to use ubuntu/Linex. But I also need to use TC2000 or CSIDATA.com (Unfair Advatage) or any other stock EOD data service.

I am currently use TC2000 with XP. if I switch to Ubuntu, I need to make ste TC2000 will work in Ubuntu or to try other data service which will work in Ubuntu.


If you are using Ubuntu, what stock data service you us with Ubuntu?

I prefer not to install Window or to install WINE.
I just want to find data service which can support Ubuntu.

Any suggestion?


Thanks for advise.

---

