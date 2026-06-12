---
title: "Is it legal to use dll files with wine?"
date: 2009-12-02
forum: Wine
---

### Post by Karisma on 2009-12-02
Hi, all
i downloaded a MMORPG named Destiny Online. This game requires a file called msvcp60.dll files to run (under wine) and i've found it on internet. My question is, is it legal if i use this dll file, including for commercial purpose (i'd like to provide the game in my internet cafe)?
Should i have a copy of Microsoft Windows to use this file?
Where can i find information about this dll file?:confused:

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by sloggerkhan on 2009-12-02
Probably varies depending on country, licensing agreements, etc.

---

### Post by Karisma on 2009-12-02
@all:
Thank you very much for your fast responds :D.
About the license agreement, unfortunately i didn't find any other file along with the dll file. 
anyway, i found information about this file on this page:
[http://support.microsoft.com/kb/259403](http://support.microsoft.com/kb/259403)
and it said that a file named vcredist.exe can be distributed freely with one's application. Vcredist.exe is a file which installs several files including msvcp60.dll. (The dll file i downloaded was not from either this site or this file).
I'm still confused if it also means that i can use the file freely without having a copy of Microsoft Windows. Currently, i've deleted the dll file and won't use any copies of it until i really sure that i can use it legally.

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by Karisma on 2009-12-02
> **PariahVayne said:**
> Which country do you live in?

Indonesia

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by Karisma on 2009-12-02
> **PariahVayne said:**
> Hmmm, ok. Do you own a copy of Windows 98/2000/XP/Vista/7?

No, i don't have it...

---

### Post by sloggerkhan on 2009-12-02
> **Karisma said:**
> @all:
Thank you very much for your fast responds :D.
About the license agreement, unfortunately i didn't find any other file along with the dll file. 
anyway, i found information about this file on this page:
[http://support.microsoft.com/kb/259403](http://support.microsoft.com/kb/259403)
and it said that a file named vcredist.exe can be distributed freely with one's application. Vcredist.exe is a file which installs several files including msvcp60.dll. (The dll file i downloaded was not from either this site or this file).
I'm still confused if it also means that i can use the file freely without having a copy of Microsoft Windows. Currently, i've deleted the dll file and won't use any copies of it until i really sure that i can use it legally.

If MS allows free distribution, then you are probably fine.

---

### Post by lightstream on 2009-12-02
I would say that DLL is the Visual C++ 6.0 runtime library, that will be (freely) distributed with software that was created using that language.

I would tend to agree with sloggerkhan that the licence for installing the DLL would not explicitly require a copy of MS Windows, although I don't know that for sure!

The link you posted says "VC6RedistSetup.exe will present you with an End User License Agreement." You'd need to read that agreement I reckon in order to know for sure.

---

### Post by Karisma on 2009-12-03
> **lightstream said:**
> I would say that DLL is the Visual C++ 6.0 runtime library, that will be (freely) distributed with software that was created using that language.

I would tend to agree with sloggerkhan that the licence for installing the DLL would not explicitly require a copy of MS Windows, although I don't know that for sure!

The link you posted says "VC6RedistSetup.exe will present you with an End User License Agreement." You'd need to read that agreement I reckon in order to know for sure.

When i tried to execute the file vc6redistsetup_enu.exe, i was prompted with a this license agreement: 

The Visual C++ 6.0 VCREDIST.EXE Pack contains updated versions 
of one or more of the software products listed below. This document 
shall serve as an addendum ("Addendum") to the Microsoft End User 
License Agreement ("EULA") you acquired with version 6.0 or later of 
any of the Microsoft products listed below.  Except as provided in this
Addendum, the VCREDIST.EXE Pack is licensed under the same 
terms and conditions contained in the EULA.  

Visual Studio
Visual C++

1.If you do not agree to be bound by the terms of the EULA and this 
Addendum, you are not authorized to use the VCREDIST.EXE Pack.
 
2.The VCREDIST.EXE Pack and all of its contents are redistributable.
Your use of any such files is subject to all terms and conditions of the 
EULA that relate to "Redistributables" (as defined in the EULA). 

3.Microsoft also grants you the nonexclusive right to copy and 
distribute the VCREDIST.EXE Pack itself and all of its contents to any 
validly licensed end user of any of the products listed above.

----------------------------------------------------------

I'm sorry i can't really understand this. Does the EULA mentioned in the agreement refer to the EULA of the Visual Studio?
And i don't really understand abut the point number 3. Does it mean that only the validly licensed users of the softwares above may copy and redistribute the file? What is the meaning of nonexclusive right? 

I found a file named vcredist.exe after extracting the .exe file. Unfortunately it seems that i can't successfully execute this file under wine. Does the license agreement above apply to the same dll files from another sources as well?

---

### Post by rocky5051 on 2009-12-03
> **Karisma said:**
> When i tried to execute the file vc6redistsetup_enu.exe, i was prompted with a this license agreement: 

The Visual C++ 6.0 VCREDIST.EXE Pack contains updated versions 
of one or more of the software products listed below. This document 
shall serve as an addendum ("Addendum") to the Microsoft End User 
License Agreement ("EULA") you acquired with version 6.0 or later of 
any of the Microsoft products listed below.  Except as provided in this
Addendum, the VCREDIST.EXE Pack is licensed under the same 
terms and conditions contained in the EULA.  

Visual Studio
Visual C++

1.If you do not agree to be bound by the terms of the EULA and this 
Addendum, you are not authorized to use the VCREDIST.EXE Pack.
 
2.The VCREDIST.EXE Pack and all of its contents are redistributable.
Your use of any such files is subject to all terms and conditions of the 
EULA that relate to "Redistributables" (as defined in the EULA). 

3.Microsoft also grants you the nonexclusive right to copy and 
distribute the VCREDIST.EXE Pack itself and all of its contents to any 
validly licensed end user of any of the products listed above.

----------------------------------------------------------

I'm sorry i can't really understand this. Does the EULA mentioned in the agreement refer to the EULA of the Visual Studio?
And i don't really understand abut the point number 3. Does it mean that only the validly licensed users of the softwares above may copy and redistribute the file? What is the meaning of nonexclusive right? 

I found a file named vcredist.exe after extracting the .exe file. Unfortunately it seems that i can't successfully execute this file under wine. Does the license agreement above apply to the same dll files from another sources as well?

It means if you own a license to use either of those products, you are allowed to distribute the redistributable any way you want. The license agreement you see there is an addition to the EULA of Visual Studio and Visual C++.

MEANING, that if it's not specified whether or not you can use the dll outside a Windows OS, then you ought to check if it's legal to do so on the Visual Studio EULA. If that product is disallowed to be used outside Windows, then that applies to the redistributable too.

---

