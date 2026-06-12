---
title: "New Linux/Wine User Needs Help!"
date: 2010-05-21
forum: Wine
---

### Post by tf4545 on 2010-05-21
I am running Wine within Ubuntu 10.04 on a Toshiba Laptop.  I installed Wine using the Ubuntu Software Center and am using 1.1.42.  I have 'installed' Adobe Reader, Firefox, IE 8 and Business Plan Pro from Palo Alto Software.  

Firefox will start and run, IE 8 will not fully execute and freeze, Adobe Reader gives an error stating 'Wine C++ Runtime Error' and Biz Plan Pro gives an Active X error '429 Can't create object.

Prior to upgrading from Ubuntu 9.10 to 10.04 I had the same software configuration listed above and had no problems with any of the Windows applications running in Wine...I know this is a long list but I'm stuck and could really use some help.  I have looked through the forums both here and with Wine and am getting more confused with the more I read.

Thanks in advance for any and all help!

---

### Post by cogadh on 2010-05-21
I find it hard to believe you had IE 8 running in Wine at all on any version of Wine or Ubuntu. To quote the Wine FAQ "The Wine project does not support installing the real Internet Explorer, as it requires a huge number of native DLLs, which is hard to configure." and, according to the Wine Application Database, [IE8 only gets as high as a bronze rating]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16041"), which is not really functional. It is possible to get some of the earlier versions of IE running using the [winetricks]("http://wiki.winehq.org/winetricks") script or [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). If one of those helps you, not only will it fix your IE problem, but it should also eliminate Biz Plan Pro's ActiveX error.

Now, Adobe Reader... we need to know what version you are trying to run, each one has its own set of problems.

---

### Post by tf4545 on 2010-05-23
After spending the better part of an entire day I was unable to get the Biz Plan application to work with Wine.  I was able to get IE6 to run and not freeze like IE8 and also got an older version of Reader to run as well but Business Plan Pro was not able to run.  I went an alternative route and am using Virtual Box to run a copy of Windows 7 that was originally shipped with my laptop.  With that came success!  Everything works great!

Thanks for the help!

---

