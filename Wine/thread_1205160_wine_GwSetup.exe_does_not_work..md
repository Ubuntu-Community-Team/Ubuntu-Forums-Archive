---
title: "wine GwSetup.exe does not work."
date: 2009-07-05
forum: Wine
---

### Post by bmtlol on 2009-07-05
Whenever I try to install Guild wars via wine by typing    
wine GwSetup.exe
it says wine: could not load L"C:\\windows\\system32\\GwSetup.exe": Module not found

I followed everything the tutorial said on the guild wars page.
though, if I double-click the setup icon, it will start downloading GW, but it closes after a few seconds.


D:

---

### Post by ackanao on 2009-07-05
You have to type full path to your Setup.exe, something like this:

```
wine /home/your_name/Desktop/Setup.exe
```

---

### Post by bmtlol on 2009-07-05
[LEFT]Yeah it worked that time, thanks, but.. When it starts to download it stops and closes out
heres the terminal line


> brandon@brandon-desktop:~$ wine /home/brandon/Desktop/GwSetup.exe
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com" 0x13afe0 0x32f5cc
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com/support/support.html" 0x145418 0x32f5cc
fixme:shellllCanUnloadNow stub
brandon@brandon-desktop:~$ fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e63c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e030,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e0c0,0x00000000), stub!
fixme:devenumEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenumEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e228,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33dc1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33dcac,0x00000000), stub!
fixme:devenumEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenumEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.



the : D were removed since they come up as smileys
[/LEFT]

---

### Post by ackanao on 2009-07-05
Take a look at this page:

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=9194](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=9194)

Install some Wine version that yields "Platinum" results and follow the Howto's described there.

Click on "Show All Tests" button to see all tests

---

### Post by bmtlol on 2009-07-05
huh?
Im very new, can I please have a little more detail

---

### Post by bmtlol on 2009-07-05
if you meant install a lower version of wine, I dont know how to remove the version I have

---

### Post by ackanao on 2009-07-05
Well, I just tried it on my system and it installs without problems. I have Wine 1.0.1 installed. Sorry but I really can't help you that much - I didn't know what the Guild Wars is untill now...

---

### Post by bmtlol on 2009-07-05
Can you please tell me how to downgrade from my current version to the one you have

---

