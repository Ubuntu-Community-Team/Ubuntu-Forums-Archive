---
title: "Teamviewer 7 installation - Ubuntu 12.04 Precise Pangolin"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by volkerbradley on 2012-03-05
Has anyone managed to get Teamviewer 7 running on 64-bit Pangolin Beta 1?
Teamviewer 7 seems to install but the following error message appears when I try to run the application:
"Could not load the GNU/Linux extension shared library tvwine.dll.so"
Any suggestions?

---

### Post by orngreen on 2012-03-05
Have the same problem. some threads suggest that its missing wine, but I had wine - even re-installed it (wine) and then re-installed Teamviewer 7...

But the problem is still there.

I'm on 64bit Pangolin and used 64bit version of Teamviewer aswell.

---

### Post by volkerbradley on 2012-03-05
> **orngreen said:**
> Have the same problem. some threads suggest that its missing wine, but I had wine - even re-installed it (wine) and then re-installed Teamviewer 7...

But the problem is still there.

I'm on 64bit Pangolin and used 64bit version of Teamviewer aswell.

Tried all those things too.  As you know, Teamviewer installs its own version of WINE.  That's where the trouble lies.
Here are my winelog contents:
Release:        12.04
Codename:       precise
 
err:dc:CreateDCW no driver found for L"WINEPS.DRV"
fixme:winspool:AddPrinterW DocumentPropertiesW on printer L"EPSON Artisan 837" fails
err:dc:CreateDCW no driver found for L"WINEPS.DRV"
err:dc:CreateDCW no driver found for L"WINEPS.DRV"
fixme:winspool:AddPrinterW DocumentPropertiesW on printer L"EPSON EPSON Artisan 837" fails
err:dc:CreateDCW no driver found for L"WINEPS.DRV"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\windows\\system32\\stdole2.tlb" failed with error 2
err:module:import_dll Library ddraw.dll (which is needed by L"C:\\windows\\system32\\dxdiagn.dll") not found
err:ole:TLB_ReadTypeLib Loading of typelib L"mshtml.tlb" failed with error 2
err:mshtml:register_server typelib registration failed: 80029c4a
err:module:import_dll Library msi.dll (which is needed by L"C:\\windows\\system32\\msiexec.exe") not found
err:winedevice:ServiceMain driver L"MountMgr" failed to load
wine: configuration in '/home/volker/Downloads/teamviewer7/profile' has been updated.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:secur32:SECUR32_initSchannelSP libgnutls not found, SSL connections will fail
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
If someone has suggestions, I sure would be grateful for your help.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-06
Am having the same problem. Anyone got it working yet?

---

### Post by pnunn on 2012-03-06
Hate the "me too's" but I've just tried installing it on Kubuntu 12.04 from both source and deb package (after going through the dependency hell) and have the same issue in both cases.

Peter.

---

### Post by Hreinsi on 2012-03-06
> **volkerbradley said:**
> Has anyone managed to get Teamviewer 7 running on 64-bit Pangolin Beta 1?
Teamviewer 7 seems to install but the following error message appears when I try to run the application:
"Could not load the GNU/Linux extension shared library tvwine.dll.so"
Any suggestions?

Have not install wine but using temviewer 7 see pic

[http://imageshack.us/f/201/screenshotat20120306084.png/](http://imageshack.us/f/201/screenshotat20120306084.png/)

---

### Post by Hreinsi on 2012-03-06
oh sorry you talking about presice not tryed that

---

### Post by apos on 2012-03-11
Anyone solved the problem?
This drives me crazy ... runs flawlessly under 11.10 

Axel

---

### Post by volkerbradley on 2012-03-11
Surely this is an issue that a knowlegeable WINE programmer could fix.  
I have submitted a ticket to TeamViewer, GmbH.  Hopefully, they will respond.

---

### Post by Leu8 on 2012-03-12
Hi!
Maybe this link could help us out?
[http://silviumc.wordpress.com/2012/03/05/installing-teamviewer-7-on-opensuse-12-1/](http://silviumc.wordpress.com/2012/03/05/installing-teamviewer-7-on-opensuse-12-1/)

It says:"Even if you got the 64 bit package, it appears it&#8217;s not all-64, still has some 32 bit parts, that&#8217;s why it needs those libraries"
-> libfreetype6-32bit libXrender1-32bit libXfixes3-32bit

Also wine has to be installed manually. "Without it, you will get this error when launching TeamViewer: Could not load the GNU/Linux extension shared library tvwine.dll.so."

I didn´t find the time to check it yet.

---

### Post by volkerbradley on 2012-03-12
I read that message too.  Apparently these files are installed with the ia32-libs package.
On my 64-bit Pangolin system I have the ia32-libs and WINE installed.
Still can't start Teamviewer.

---

### Post by ndioses on 2012-03-12
I did install wine apart from installing teamviewer, but i did it after installing teamviewer.

Maybe it'll work to uninstall everything and install wine first and teamviewer the second... 

I'll try later when i get home, and tell you how it went.

---

### Post by cariboo on 2012-03-12
I'd suggest that anyone trying to install the 64-bit package, purge it, and install the i386 package, with multiarch support in Precise, that will pull in the needed dependencies. Especially seeing as the 64-bit package is just a kludge, that still depends on 32-bit libraries.

---

### Post by Neil Huang on 2012-03-14
Tried that but didn't work for me. 

To be fair, there is a flash-version of teamviewer available, but the keyboard mapping is incorrect. If you want to use just mouse clicks then try it but anything with keystrokes is no luck.

Link is [https://login.teamviewer.com/](https://login.teamviewer.com/)

I still would like to see the actual version working under wine though...

---

### Post by volkerbradley on 2012-03-14
Tried the flash-version and found that the keyboard functioned correctly for me.  Thanks for reminding us of this link.

---

### Post by sgrzy01 on 2012-03-14
Man.. 

This is the only thing keeping me from using 12.04 on a daily basis... I live in TV, and need it to work or I'm stuck in 11.10

I've had no luck either with above suggestions...

---

### Post by gosteen on 2012-03-14
If you list the dynamic library dependencies on the file 'tvwine.dll.so', you should notice some missing links.  Those can be resolved with the following command and then TeamViewer appears to work normally.

```

$ sudo apt-get install libxtst6:i386 wine

```

Installing wine here might actually not be necessary.  Feel free to try without it.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-14
Lovely! Thanks for this :thumbsup:

---

### Post by Leu8 on 2012-03-14
For me, this is sufficient:
```
sudo apt-get install libxtst6:i386
```
Works fine. Thanks a lot!

By the way: I got the same error-report using ubuntu 12.04 and teamviewer 6!

---

### Post by ndioses on 2012-03-14
thankssssss!!

this
```
sudo apt-get install libxtst6:i386
```
worked  just fine! :p

---

### Post by heavyt on 2012-03-14
> **gosteen said:**
> If you list the dynamic library dependencies on the file 'tvwine.dll.so', you should notice some missing links.  Those can be resolved with the following command and then TeamViewer appears to work normally.

```

$ sudo apt-get install libxtst6:i386 wine

```

Installing wine here might actually not be necessary.  Feel free to try without it.
Thanks, it fix the error.

---

### Post by Fixxxer_K12 on 2012-03-15
> **gosteen said:**
> If you list the dynamic library dependencies on the file 'tvwine.dll.so', you should notice some missing links.  Those can be resolved with the following command and then TeamViewer appears to work normally.

```

$ sudo apt-get install libxtst6:i386 wine

```

Installing wine here might actually not be necessary.  Feel free to try without it.

Thank you!!! That fixed it for me! You rock !!:guitar:

---

### Post by sgrzy01 on 2012-03-15
You da man!

worked w/o having to add wine...

---

### Post by korg91 on 2012-03-18
PLEASE add "ubuntu 12.04 (precise pangolin)" to the topic title...it makes the topic much easier to find on google

---

### Post by volkerbradley on 2012-03-18
> **gosteen said:**
> If you list the dynamic library dependencies on the file 'tvwine.dll.so', you should notice some missing links.  Those can be resolved with the following command and then TeamViewer appears to work normally.

```

$ sudo apt-get install libxtst6:i386 wine

```

Installing wine here might actually not be necessary.  Feel free to try without it.
Worked for me as well.
Thanks for the solution.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-18
> **korg91 said:**
> PLEASE add "ubuntu 12.04 (precise pangolin)" to the topic title...it makes the topic much easier to find on google

Agreed.

---

### Post by howefield on 2012-03-18
> **korg91 said:**
> PLEASE add "ubuntu 12.04 (precise pangolin)" to the topic title...it makes the topic much easier to find on google

Done. 

Thank you.

---

### Post by Leu08 on 2012-03-19
Wrote to teamviewer, reported the bug and this solutions. Suggested to implement the needed 32bit-libraries into the download.
Got the answer that this "feature request" was sent to the development division.

---

### Post by Leu08 on 2012-03-21
Got the answer today from the teamviewer technical support. The bug is related to the beta-stadium of ubuntu 12.04. They already wrote a fix for the next version of teamviewer. Now it seems obsolete.

If we update ubuntu 12.04 now, libxtst6 depends now on ia32-libs which depends teamviewer on. So libxtst6 will be automatically installed by installing teamviewer7.

The technical support of teamviewer is aware of this situation. By the way: Thanks to the teamviewer support for their fast and professional answers!

---

### Post by IndyGunFreak on 2012-03-28
This did not work for me, I still get the same error.

---

### Post by volkerbradley on 2012-03-29
> **IndyGunFreak said:**
> This did not work for me, I still get the same error.

What are your referring to when you mention "This"?

---

### Post by IndyGunFreak on 2012-03-29
> **volkerbradley said:**
> What are your referring to when you mention "This"?

The fixes listed in this thread?  Specifically post #25

---

### Post by kalkems on 2012-04-25
I tried to install Teamviewer 32bit on an upgraded 12.04 32bit install but it wants to remove bash and dash replacing it with bash:i386 and dash:i386 which creates problems with the system. I managed to backtrack and fix the system.

Does anyone have a solution for this?

---

