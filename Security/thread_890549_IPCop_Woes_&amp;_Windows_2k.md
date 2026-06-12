---
title: "IPCop Woes &amp; Windows 2k"
date: 2008-08-15
forum: Security
---

### Post by Squizz on 2008-08-15
Hi there,

We've had some problems where IPCop has been complaining and shutting down services.

We've discovered that it's because one of the users on the network has been trying to access thousands of websites, and getting denied access each time, which fills up the log and thus IPCop starts shutting down services to deal with the memory load.  These websites are [http://www.sdfjkhsdf.com](http://www.sdfjkhsdf.com) and similar randomness.

I would normally just wipe the OS and start afresh, or replace the guys computer - but there's business critical software on there that would be too time consuming and awkward to re-deploy as the company will soon be ceasing trading.

Is there a way to check and see what is trying to connect to all these websites?  I've run various antivirus and spyware programs  (the only problem being "insecure cookies" which I deleted) but the problems persist.

Any suggestions would be gladly received.

Regards

---

### Post by hyper_ch on 2008-08-15
how about you block that user?

---

### Post by Squizz on 2008-08-15
It's not technically that user, just their PC.

There seems to be something that has gotten hold of the proxy address and port and is trying to connect.  The overload is happening from denied requests.

I've looked through a hijackthis log as well, but couldn't see anything that I thought looked dodgy - but I'm no expert.

> 
Logfile of HijackThis v1.99.1
Scan saved at 12:29:56, on 15/08/2008
Platform: Windows 2000 SP4 (WinNT 5.00.2195)
MSIE: Internet Explorer v6.00 SP1 (6.00.2800.1106)

Running processes:
C:\WINNT\System32\smss.exe
C:\WINNT\system32\winlogon.exe
C:\WINNT\system32\services.exe
C:\WINNT\system32\lsass.exe
C:\WINNT\system32\svchost.exe
C:\WINNT\system32\spoolsv.exe
C:\Program Files\Lavasoft\Ad-Aware 2007\aawservice.exe
C:\WINNT\System32\svchost.exe
C:\WINNT\system32\hidserv.exe
C:\WINNT\System32\nslsvice.exe
C:\ePOAgent\FrameworkService.exe
C:\Program Files\McAfee\VirusScan Enterprise\Mcshield.exe
C:\Program Files\McAfee\VirusScan Enterprise\VsTskMgr.exe
C:\Program Files\Common Files\Microsoft Shared\VS7Debug\mdm.exe
C:\Program Files\Microsoft SQL Server\MSSQL\Binn\sqlservr.exe
C:\Lotus\Notes\ntmulti.exe
C:\WINNT\system32\regsvc.exe
C:\WINNT\system32\MSTask.exe
C:\WINNT\system32\stisvc.exe
C:\WINNT\System32\WBEM\WinMgmt.exe
C:\WINNT\system32\mspmspsv.exe
C:\WINNT\Explorer.EXE
C:\Program Files\Internet Explorer\iexplore.exe
C:\ePOAgent\UdaterUI.exe
C:\Program Files\Picasa2\PicasaMediaDetector.exe
C:\ePOAgent\McTray.exe
C:\Program Files\Java\jre1.5.0_13\bin\jusched.exe
C:\WINNT\system32\ctfmon.exe
C:\Program Files\Toshiba\Bluetooth Toshiba Stack\TosBtMng.exe
C:\Program Files\Hewlett-Packard\LaserJet 33xx\hppdirector.exe
C:\Program Files\Toshiba\Bluetooth Toshiba Stack\TosA2dp.exe
C:\Program Files\Toshiba\Bluetooth Toshiba Stack\TosBtHsp.exe
C:\Program Files\Internet Explorer\IEXPLORE.EXE
C:\WINNT\System32\svchost.exe
C:\WINNT\system32\notepad.exe
C:\WINNT\system32\svchost.exe
C:\Program Files\Java\jre1.5.0_13\bin\jucheck.exe
C:\Program Files\HijackThis\HijackThis.exe

R0 - HKCU\Software\Microsoft\Internet Explorer\Main,Start Page = [http://www.nec-online.co.uk/](http://www.nec-online.co.uk/)
R1 - HKLM\Software\Microsoft\Internet Explorer\Main,Default_Page_URL = [http://intranet](http://intranet)
R1 - HKCU\Software\Microsoft\Internet Explorer\Main,Window Title = Microsoft Internet Explorer provided by 
R1 - HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings,ProxyServer = 172.16.4.3:3128
O1 - Hosts: 172.16.6.1 company.co.uk #PRE
O1 - Hosts: 172.16.6.28 c1 #PRE
O1 - Hosts: 172.16.6.1 server1 #PRE
O1 - Hosts: 172.16.6.10 intranet #PRE
O1 - Hosts: 172.16.6.16 printserver #PRE
O1 - Hosts: 172.16.6.9 wayserver #PRE
O1 - Hosts: 172.16.6.13 server2 #PRE
O1 - Hosts: 172.16.6.15 server3 #PRE
O1 - Hosts: 172.16.6.26 server4 #PRE
O1 - Hosts: 172.16.6.3 AS400 #PRE
O1 - Hosts: 172.16.6.3 AUTO1 #PRE
O1 - Hosts: 172.16.6.19 ARCHIVESERVER #PRE
O2 - BHO: AcroIEHlprObj Class - {06849E9F-C8D7-4D59-B87D-784B7D6BE0B3} - C:\Program Files\Adobe\Acrobat 6.0\Reader\ActiveX\AcroIEHelper.dll
O2 - BHO: Skype add-on (mastermind) - {22BF413B-C6D2-4d91-82A9-A0F997BA588C} - C:\Program Files\Skype\Toolbars\Internet Explorer\SkypeIEPlugin.dll
O2 - BHO: SSVHelper Class - {761497BB-D6F0-462C-B6EB-D4DAF1D92D43} - C:\Program Files\Java\jre1.5.0_13\bin\ssv.dll
O2 - BHO: scriptproxy - {7DB2D5A0-7241-4E79-B68D-6309F01C5231} - C:\Program Files\McAfee\VirusScan Enterprise\scriptcl.dll
O2 - BHO: Google Toolbar Helper - {AA58ED58-01DD-4d91-8333-CF10577473F7} - c:\program files\google\googletoolbar1.dll
O3 - Toolbar: &Radio - {8E718888-423F-11D2-876E-00A0C9082467} - C:\WINNT\system32\msdxm.ocx
O3 - Toolbar: &Google - {2318C2B1-4965-11d4-9B18-009027A5CD4F} - c:\program files\google\googletoolbar1.dll
O4 - HKLM\..\Run: [NvCplDaemon] RUNDLL32.EXE NvQTwk,NvCplDaemon initialize
O4 - HKLM\..\Run: [Synchronization Manager] mobsync.exe /logon
O4 - HKLM\..\Run: [EM_EXEC] C:\PROGRA~1\MOUSEW~1\SYSTEM\EM_EXEC.EXE
O4 - HKLM\..\Run: [HPDJ Taskbar Utility] C:\WINNT\System32\spool\drivers\w32x86\3\hpztsb04.exe
O4 - HKLM\..\Run: [McAfeeUpdaterUI] "C:\ePOAgent\UdaterUI.exe" /StartedFromRunKey
O4 - HKLM\..\Run: [Picasa Media Detector] C:\Program Files\Picasa2\PicasaMediaDetector.exe
O4 - HKLM\..\Run: [HP SchedIndexer] C:\Program Files\Hewlett-Packard\LaserJet 33xx\hppschedindexer.exe
O4 - HKLM\..\Run: [HP AutoIndexer] C:\Program Files\Hewlett-Packard\LaserJet 33xx\hppautoindexer.exe
O4 - HKLM\..\Run: [ShStatEXE] "C:\Program Files\McAfee\VirusScan Enterprise\SHSTAT.EXE" /STANDALONE
O4 - HKLM\..\Run: [SunJavaUpdateSched] "C:\Program Files\Java\jre1.5.0_13\bin\jusched.exe"
O4 - HKLM\..\Run: [Winpooch] C:\Program Files\Winpooch\Winpooch.exe
O4 - HKCU\..\Run: [ctfmon.exe] ctfmon.exe
O4 - Global Startup: Bluetooth Manager.lnk = C:\Program Files\Toshiba\Bluetooth Toshiba Stack\TosBtMng.exe
O4 - Global Startup: HP LaserJet Director.lnk = C:\Program Files\Hewlett-Packard\LaserJet 33xx\hppdirector.exe
O9 - Extra button: (no name) - {08B0E5C0-4FCB-11CF-AAA5-00401C608501} - C:\Program Files\Java\jre1.5.0_13\bin\ssv.dll
O9 - Extra 'Tools' menuitem: Sun Java Console - {08B0E5C0-4FCB-11CF-AAA5-00401C608501} - C:\Program Files\Java\jre1.5.0_13\bin\ssv.dll
O9 - Extra button: Skype - {77BF5300-1474-4EC7-9980-D32B190E9B07} - C:\Program Files\Skype\Toolbars\Internet Explorer\SkypeIEPlugin.dll
O9 - Extra button: Related - {c95fe080-8f5d-11d2-a20b-00aa003c157a} - C:\WINNT\web\related.htm
O9 - Extra 'Tools' menuitem: Show &Related Links - {c95fe080-8f5d-11d2-a20b-00aa003c157a} - C:\WINNT\web\related.htm
O14 - IERESET.INF: START_PAGE_URL=http://intranet
O16 - DPF: {6414512B-B978-451D-A0D8-FCFDF33E833C} (WUWebControl Class) - [http://www.update.microsoft.com/windowsupdate/v6/V5Controls/en/x86/client/wuweb_site.cab?1218799318045](http://www.update.microsoft.com/windowsupdate/v6/V5Controls/en/x86/client/wuweb_site.cab?1218799318045)
O16 - DPF: {CAFEEFAC-0013-0001-0002-ABCDEFFEDCBA} (Java Runtime Environment 1.3.1_02) - [http://abff07/WFC/plugins/j2re-1_3_1_02-win-i.exe](http://abff07/WFC/plugins/j2re-1_3_1_02-win-i.exe)
O17 - HKLM\System\CCS\Services\Tcpip\Parameters: Domain = abautomotive.co.uk
O17 - HKLM\System\CS1\Services\Tcpip\Parameters: Domain = abautomotive.co.uk
O17 - HKLM\System\CS2\Services\Tcpip\Parameters: Domain = abautomotive.co.uk
O18 - Protocol: skype4com - {FFC8B962-9B40-4DFF-9458-1830C7DD7F5D} - C:\PROGRA~1\COMMON~1\Skype\SKYPE4~1.DLL
O23 - Service: Ad-Aware 2007 Service (aawservice) - Lavasoft AB - C:\Program Files\Lavasoft\Ad-Aware 2007\aawservice.exe
O23 - Service: Logical Disk Manager Administrative Service (dmadmin) - VERITAS Software Corp. - C:\WINNT\System32\dmadmin.exe
O23 - Service: Google Updater Service (gusvc) - Google - C:\Program Files\Google\Common\Google Updater\GoogleUpdaterService.exe
O23 - Service: Lotus Notes Single Logon - Unknown owner - C:\WINNT\System32\\nslsvice.exe
O23 - Service: McAfee Framework Service (McAfeeFramework) - Unknown owner - C:\ePOAgent\FrameworkService.exe" /ServiceStart (file missing)
O23 - Service: McAfee McShield (McShield) - McAfee, Inc. - C:\Program Files\McAfee\VirusScan Enterprise\Mcshield.exe
O23 - Service: McAfee Task Manager (McTaskManager) - McAfee, Inc. - C:\Program Files\McAfee\VirusScan Enterprise\VsTskMgr.exe
O23 - Service: Multi-user Cleanup Service - IBM Corp - C:\Lotus\Notes\ntmulti.exe


---

### Post by Mister.Vash on 2008-08-16
I don't have XP with me right now so I don't have the exact command handy, but on the machine that is doing it, do a netstat /help - they have options to show the process that owns the connection.

For your IPCOP logs, I don't what the best way is to handle them - you might want to see if you can get that taken care of first - they have a forum setup and might have some suggestions on dealing with high volume logs, [http://www.ipcops.com/phpbb3/](http://www.ipcops.com/phpbb3/)  You don't want your firewall going down because of it this time or the next time it happens

---

### Post by EnGorDiaz on 2008-08-27
> **Squizz said:**
> Hi there,

We've had some problems where IPCop has been complaining and shutting down services.

We've discovered that it's because one of the users on the network has been trying to access thousands of websites, and getting denied access each time, which fills up the log and thus IPCop starts shutting down services to deal with the memory load.  These websites are [http://www.sdfjkhsdf.com](http://www.sdfjkhsdf.com) and similar randomness.

I would normally just wipe the OS and start afresh, or replace the guys computer - but there's business critical software on there that would be too time consuming and awkward to re-deploy as the company will soon be ceasing trading.

Is there a way to check and see what is trying to connect to all these websites?  I've run various antivirus and spyware programs  (the only problem being "insecure cookies" which I deleted) but the problems persist.

Any suggestions would be gladly received.

Regards

3 things

reactos + ipcop + your corporate software = epic win!!! (well for you)

---

