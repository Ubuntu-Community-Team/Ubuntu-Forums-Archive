---
title: "Trojan, Worm Question"
date: 2022-01-15
forum: Windows
---

### Post by tuser001 on 2022-01-15
Hello, I suspect i have a trojan or worm in a hidden partition or mrb/gpt(had win7 show up on my pc). So I downloaded ubuntu terminal and looked at my partitions. And i have a bunch of partitions i dont think should be there. Could anyone have a look and tell me if those 8 items under filesystem are partitions in the picture are okay and how i could delete those partitions Ir if i need to dual boot with windows 10 to see partitions?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289803&stc=1[/IMG]

Thanks.

---

### Post by HermanAB on 2022-01-15
If you find a Linux worm, please email it to me.  I’d like to look at it, since Linux critters are very unusual. The last time, more than a decade ago, Linus had to modify the kernel to make a virus work: [https://www.linux.com/news/torvalds-creates-patch-cross-platform-virus/](https://www.linux.com/news/torvalds-creates-patch-cross-platform-virus/)

Note that messing with partitions is a pretty good way to lose all your data, but the tool for that is gparted.

---

### Post by tuser001 on 2022-01-15
Sorry for misunderstanding, there is no lunix virus. I had virus, either from a bad browser download, or a usb port virus that i think dug itself into boot parpartitions. AT one point I notice i had 11 drive volumes and and my boot order was changed to ivp6 network, had seen bunch of d/ling i didnt do, searched suspicious logs entries, silent install of apps where log was destroyed after install,100 svchost service etc. SO i just did a factory reset, passworded everything and It came back the next day, lead me to believe it in boot, or d/ling from server somewhere. The way i noticed is my google search was altered, then i noticed alot of pages where a little off, like my bank page. So when i used my bookmarks it took me to fake pages, but my saved login in if would not come up on their fakesites. Only when i manually changed the address to correct site would my saved info popup.


Anyways, I seen people say the were able to find and remove the virus with ubuntu, just not exactly how they did it....

---

### Post by Holger_Gehrke on 2022-01-15
Do you mean you're running Windows as your OS and have Ubuntu on Windows inside the **W**indows **S**ubsystem for **L**inux ?

That would explain why your 'df' output is slightly weird: everything except the entry with '/' in the last column and the one with '/mnt/c' has the wrong kind of file system ('/dev/' should be a udev filesystem (a pseudo filesystem that automatically creates files to represent devices connected to the system), the others should be tmpfs (RAM-disk that automatically grows as needed up to an upper boundary given when mounting the file system)). Also the size (2nd column), used and free space are identical. If this is WSL, that's understandable (it's only Windows play-acting at being a Linux-Kernel, it will get things like that wrong).

The right way to use Ubuntu (or any other Linux) to clean up the aftermath of a malware incident is to boot a live system prepared on a different, known to be clean computer and use that to backup any data (**and only data**; programs can and should be reinstalled from clean sources, since you can't tell what's o.k. and what isn't) that has not been backed up and then nuke the disk from orbit ... Re-install Windows from clean install media (not from a recovery partition on the system, the malware might have spread to that), re-install your programs and restore data from backups.

Holger

---

### Post by tuser001 on 2022-01-16
Yeah went out, came home and it is back... My event log has like 200 entries in a couple hours of me being gone...all suspicious. and now im having to click twice on everything, when i should only have to click once....

I would erase everything, but then im afraid i wont be able to use windows if i dont have the serial verification code that they want/need to reload.... since before Pentium 1, i had cpus. I think i could tell when im hacked, surprisingly this is first time that wasnt something that a scanner didnt find...
And if i search for trojans, it brings up fake hacked sites from like 5,10 years ago, that pretend they helping you but just trying to get you to download their virus removal apps, that are viruses.... And it got in my phone, DLed android folder and bluestacks, turned on my bluetooth, and linked to my phone. Took me few hours to just factory reset my phone, cause everything was blocked or gone in settings(tried to only restart phone if i had wifi, when i did a reset day before no problem)...... Nasty thing it is......

"333"pic is when i left home and there is like 100+ more events after that, special login, security account, user account, etc......and now my searches are like before when  hacked...

I'm ready to get new computer, new modem, new router, etc......
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289807&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289808&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289809&stc=1[/IMG]

---

### Post by tuser001 on 2022-01-16
Oh yeah, the other place i see suspicious activity is in the credentials..... CA roots from 10+ years ago, duplicates, property info blanked out and not able to access, errors when try to take control via permissions, 20-50+ new user accounts/permission accounts etc..... SO annoying cause i know it not like a hacker prolly trying to hack account to steal money, but hacking account to use, gather all my info and sell it on the dark web bundled with 100s of other peoples....for like 0.10 cents a person. smh.....

---

### Post by howefield on 2022-01-16
Moved to the "*Windows*" sub forum for a better fit.

---

### Post by tuser001 on 2022-01-16
Thanks....... sadly, it hard to tell what sites are real or not.... They have fake bleepingcomputers site.....

Anyways.......
I did a farbar, looking like their was some suspicious files to me, if Im asking here cause at BC, they just tell you if you have malware and adware.... I just did factory reset and have at least harddisk Volume 1-6......

Anyways thanks for whatever advice info ppl can give. Thanks again for your time.

```
Firmware Application (101fffff)
-------------------------------
identifier              {af5ad3f5-1fe1-11eb-85e1-806e6f6e6963}
description             Onboard NIC(IPV4)


Firmware Application (101fffff)
-------------------------------
identifier              {af5ad3f6-1fe1-11eb-85e1-806e6f6e6963}
description             Onboard NIC(IPV6)


Windows Boot Loader
-------------------
identifier              {09c405cc-9ec4-11e5-9b46-5ce0c5654d7a}
device                  ramdisk=[\Device\HarddiskVolume6]\sources\sos.wim,{492933ee-cd0d-11e1-9b66-d4bed91b7fc5}
path                    \windows\system32\winload.efi
description             Dell SupportAssist
locale                  en-US
inherit                 {bootloadersettings}
osdevice                ramdisk=[\Device\HarddiskVolume6]\sources\sos.wim,{492933ee-cd0d-11e1-9b66-d4bed91b7fc5}
systemroot              \Windows
nx                      OptIn
bootmenupolicy          Standard
winpe                   Yes


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 10
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {dcd5eb6a-1fe7-11eb-be53-70b5e83648cd}
displaymessageoverride  Recovery
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {16dcf3b2-1fdf-11eb-913c-70b5e83648cd}
nx                      OptOut
bootmenupolicy          Standard
bootstatuspolicy        DisplayAllFailures


Windows Boot Loader
-------------------
identifier              {dcd5eb6a-1fe7-11eb-be53-70b5e83648cd}
device                  ramdisk=[\Device\HarddiskVolume4]\Recovery\WindowsRE\Winre.wim,{dcd5eb6b-1fe7-11eb-be53-70b5e83648cd}
path                    \windows\system32\winload.efi
description             Windows Recovery Environment
locale                  en-US
inherit                 {bootloadersettings}
displaymessage          Recovery
osdevice                ramdisk=[\Device\HarddiskVolume4]\Recovery\WindowsRE\Winre.wim,{dcd5eb6b-1fe7-11eb-be53-70b5e83648cd}
systemroot              \windows
nx                      OptIn
bootmenupolicy          Standard
winpe                   Yes


 Registry (Whitelisted) ===================


(If an entry is included in the fixlist, the registry item will be restored to default or removed. The file will not be moved.)


HKLM\...\Run: [RtkAudUService] => C:\Windows\System32\RtkAudUService64.exe [953120 2019-12-26] (Realtek Semiconductor Corp. -> Realtek Semiconductor)
HKLM\...\Run: [WavesSvc] => C:\Windows\System32\DriverStore\FileRepository\wavesapo9de.inf_amd64_0dc1f198e733bf19\WavesSvc64.exe [1594664 2019-12-06] (Waves Inc -> Waves Audio Ltd.)
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\Run: [NordVPN] => C:\Program Files\NordVPN\NordVPN.exe [280440 2021-06-05] (nordvpn s.a. -> TEFINCOM S.A.)
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Delete Cached Update Binary] => C:\Windows\system32\cmd.exe /q /c del /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\Update\OneDriveSetup.exe"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Delete Cached Standalone Update Binary] => C:\Windows\system32\cmd.exe /q /c del /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\StandaloneUpdater\OneDriveSetup.exe"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Uninstall 21.220.1024.0005\amd64] => C:\Windows\system32\cmd.exe /q /c rmdir /s /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\21.220.1024.0005\amd64"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Uninstall 21.220.1024.0005] => C:\Windows\system32\cmd.exe /q /c rmdir /s /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\21.220.1024.0005"
HKLM\Software\Microsoft\Active Setup\Installed Components: [{8A69D345-D564-463c-AFF1-A69D9E530F96}] -> C:\Program Files\Google\Chrome\Application\97.0.4692.71\Installer\chrmstp.exe [2022-01-14] (Google LLC -> Google LLC)




Scan result of Farbar Recovery Scan Tool (FRST) (x64) Version: 15-01-2022
Ran by StopHacking (administrator) on DESKTOP-E28L7AL (Dell Inc. Inspiron 3880) (16-01-2022 05:59:39)
Running from C:\Users\StopHacking\Downloads
Loaded Profiles: StopHacking
Platform: Microsoft Windows 10 Home Version 2004 19041.450 (X64) Language: English (United States)
Default browser: Chrome
Boot Mode: Normal


==================== Processes (Whitelisted) =================


(If an entry is included in the fixlist, the process will be closed. The file will not be moved.)


(Dell Inc -> ) C:\Program Files (x86)\Dell Digital Delivery Services\Dell.D3.WinSvc.exe
(Dell Inc -> Dell INC.) C:\Program Files\Dell\SARemediation\agent\DellSupportAssistRemedationService.exe
(Dell Inc -> Dell Inc.) C:\Program Files\Dell\SupportAssistAgent\bin\SupportAssistAgent.exe
(Dell Technologies Inc. -> Dell Technologies Inc.) C:\Program Files\Dell\DellDataVault\DDVCollectorSvcApi.exe
(Dell Technologies Inc. -> Dell Technologies Inc.) C:\Program Files\Dell\DellDataVault\DDVDataCollector.exe
(Dell Technologies Inc. -> Dell Technologies Inc.) C:\Program Files\Dell\DellDataVault\DDVRulesProcessor.exe
(Google LLC -> Google LLC) C:\Program Files (x86)\Google\Update\1.3.36.112\GoogleCrashHandler.exe
(Google LLC -> Google LLC) C:\Program Files (x86)\Google\Update\1.3.36.112\GoogleCrashHandler64.exe
(Google LLC -> Google LLC) C:\Program Files\Google\Chrome\Application\chrome.exe <89>
(Intel(R) Embedded Subsystems and IP Blocks Group -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\dal.inf_amd64_31a8dbbf39dcdc3b\jhi_service.exe
(Intel(R) Embedded Subsystems and IP Blocks Group -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\lms.inf_amd64_8a00302ff60aed46\LMS.exe
(Intel(R) pGFX 2020 -> ) C:\Windows\System32\DriverStore\FileRepository\igcc_dch.inf_amd64_5b19dfe7970a7139\OneApp.IGCC.WinService.exe
(Intel(R) pGFX 2020 -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\cui_dch.inf_amd64_cb5b3ac4d6a4f65a\igfxCUIService.exe
(Intel(R) pGFX 2020 -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\cui_dch.inf_amd64_cb5b3ac4d6a4f65a\igfxEM.exe
(Intel(R) pGFX 2020 -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_91dc746bbfc507e6\IntelCpHDCPSvc.exe
(Intel(R) pGFX 2020 -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_91dc746bbfc507e6\IntelCpHeciSvc.exe
(Intel(R) Rapid Storage Technology -> Intel Corporation) C:\Windows\System32\DriverStore\FileRepository\iastorac.inf_amd64_99239023b47c777a\RstMwService.exe
(McAfee, Inc. -> McAfee LLC.) C:\Program Files\Common Files\McAfee\AMCore\mcshield.exe
(McAfee, Inc. -> McAfee, LLC) C:\Program Files\Common Files\McAfee\SystemCore\mfemms.exe
(McAfee, Inc. -> McAfee, LLC) C:\Windows\System32\mfevtps.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\CSP\4.9.104.0\McCSPServiceHost.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\MMSSHost\MMSSHOST.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\ModuleCore\ModuleCoreService.exe <3>
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\ModuleCore\ProtectedModuleHost.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\PEF\CORE\PEFService.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\Platform\McUICnt.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\Common Files\McAfee\VSCore_21_9\mcapexe.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\MfeAV\MfeAVSvc.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\MQS\QcShm.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\VUL\McVulAlert.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\VUL\McVulCtr.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\WebAdvisor\servicehost.exe
(McAfee, LLC -> McAfee, LLC) C:\Program Files\McAfee\WebAdvisor\uihost.exe
(McAfee, LLC. -> McAfee, LLC.) C:\Program Files\Common Files\McAfee\Platform\MSM\McSmtFwk.exe
(Microsoft Windows -> Microsoft Corporation) C:\Windows\HelpPane.exe
(Microsoft Windows -> Microsoft Corporation) C:\Windows\ImmersiveControlPanel\SystemSettings.exe
(Microsoft Windows -> Microsoft Corporation) C:\Windows\System32\dllhost.exe <2>
(Microsoft Windows -> Microsoft Corporation) C:\Windows\System32\MoUsoCoreWorker.exe
(Microsoft Windows -> Microsoft Corporation) C:\Windows\System32\smartscreen.exe
(nordvpn s.a. -> TEFINCOM S.A.) C:\Program Files\NordVPN\NordVPN.exe
(nordvpn s.a. -> TEFINCOM S.A.) C:\Program Files\NordVPN\nordvpn-service.exe
(PC-Doctor, Inc. -> PC-Doctor, Inc.) C:\Program Files\Dell\SupportAssistAgent\PCD\SupportAssist\Dsapi.exe
(Realtek Semiconductor Corp. -> Realtek Semiconductor) C:\Windows\System32\RtkAudUService64.exe <2>
(Rivet Networks LLC -> DELL) C:\Config.Msi\4578dd9.rbf
(Rivet Networks LLC -> Rivet Networks) C:\Program Files\Rivet Networks\SmartByte\SmartByteAnalyticsService.exe
(Rivet Networks LLC -> Rivet Networks) C:\Program Files\Rivet Networks\SmartByte\SmartByteNetworkService.exe
(Scott Brogden) C:\Program Files\WindowsApps\60145ScottBrogden.ditto-cp_3.24.214.0_x86__n6b029mg40na2\Ditto.exe
(Skype) C:\Program Files\WindowsApps\Microsoft.SkypeApp_14.53.77.0_x64__kzf8qxf38zg5c\SkypeApp.exe
(Waves Inc -> Waves Audio Ltd.) C:\Windows\System32\DriverStore\FileRepository\wavesapo9de.inf_amd64_0dc1f198e733bf19\WavesSysSvc64.exe


==================== Registry (Whitelisted) ===================


(If an entry is included in the fixlist, the registry item will be restored to default or removed. The file will not be moved.)


HKLM\...\Run: [RtkAudUService] => C:\Windows\System32\RtkAudUService64.exe [953120 2019-12-26] (Realtek Semiconductor Corp. -> Realtek Semiconductor)
HKLM\...\Run: [WavesSvc] => C:\Windows\System32\DriverStore\FileRepository\wavesapo9de.inf_amd64_0dc1f198e733bf19\WavesSvc64.exe [1594664 2019-12-06] (Waves Inc -> Waves Audio Ltd.)
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\Run: [NordVPN] => C:\Program Files\NordVPN\NordVPN.exe [280440 2021-06-05] (nordvpn s.a. -> TEFINCOM S.A.)
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Delete Cached Update Binary] => C:\Windows\system32\cmd.exe /q /c del /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\Update\OneDriveSetup.exe"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Delete Cached Standalone Update Binary] => C:\Windows\system32\cmd.exe /q /c del /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\StandaloneUpdater\OneDriveSetup.exe"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Uninstall 21.220.1024.0005\amd64] => C:\Windows\system32\cmd.exe /q /c rmdir /s /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\21.220.1024.0005\amd64"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\RunOnce: [Uninstall 21.220.1024.0005] => C:\Windows\system32\cmd.exe /q /c rmdir /s /q "C:\Users\StopHacking\AppData\Local\Microsoft\OneDrive\21.220.1024.0005"
HKLM\Software\Microsoft\Active Setup\Installed Components: [{8A69D345-D564-463c-AFF1-A69D9E530F96}] -> C:\Program Files\Google\Chrome\Application\97.0.4692.71\Installer\chrmstp.exe [2022-01-14] (Google LLC -> Google LLC)


==================== Scheduled Tasks (Whitelisted) ============


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)


Task: {03BB1C4A-0D9F-4981-8389-61AC85EDE803} - System32\Tasks\SmartByte Telemetry => C:\Program Files\Rivet Networks\SmartByte\SmartByteTelemetry.exe [96520 2021-08-13] (Rivet Networks LLC -> DELL)
Task: {04F0DC85-7D2B-4C35-AB0C-3BD59926BB6A} - System32\Tasks\Microsoft\Office\Office Automatic Updates 2.0 => C:\Program Files\Common Files\Microsoft Shared\ClickToRun\OfficeC2RClient.exe [24610408 2020-04-09] (Microsoft Corporation -> Microsoft Corporation)
Task: {1ECCE3C0-B8E4-43EC-AD59-8D51E3080A2D} - System32\Tasks\GoogleUpdateTaskMachineUA => C:\Program Files (x86)\Google\Update\GoogleUpdate.exe [156232 2022-01-14] (Google LLC -> Google LLC)
Task: {3BD18D02-2D5F-41E1-9D00-C6D745063E13} - System32\Tasks\Microsoft\Office\Office Feature Updates Logon => C:\Program Files\Microsoft Office\root\Office16\sdxhelper.exe [158544 2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Task: {3D99C8A9-A734-40A7-9D80-EE73D49FE9B4} - System32\Tasks\McAfee\DAD.Execute.Updates => C:\Program Files\Common Files\McAfee\DynamicAppDownloader\DADUpdater.exe [4119992 2021-10-07] (McAfee, LLC -> McAfee, LLC)
Task: {568E2D11-C694-4E57-B46D-545420E4CA0C} - System32\Tasks\McAfee\McAfee DAT Built in test => C:\Program Files\Common Files\McAfee\AMContent\scanners\x86_64\datrep\1.0.12.663\mcdatrep.exe [1889696 2022-01-14] (McAfee, Inc. -> McAfee, LLC.)
Task: {766DFD69-1728-48E1-9540-CC59BCF2FE96} - System32\Tasks\Microsoft\Office\Office Feature Updates => C:\Program Files\Microsoft Office\root\Office16\sdxhelper.exe [158544 2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Task: {7771F430-362C-4770-8688-03D9A14ACD63} - System32\Tasks\McAfee Remediation (Prepare) => C:\Program Files\Common Files\AV\McAfee VirusScan\upgrade.exe [4696128 2021-11-18] (McAfee, LLC -> McAfee, LLC)
Task: {B14EA03F-1E71-4310-8360-E53E029C87CC} - System32\Tasks\McAfee\McAfee Auto Maintenance Task Agent => {ABCECA3B-EA5A-496B-A021-5C6BAB365E5C} C:\Program Files\Common Files\McAfee\TaskScheduler\McAMTaskAgent.exe [1032448 2021-08-02] (McAfee, LLC -> McAfee, LLC)
"C:\Windows\System32\Tasks\McAfee\McAfee Idle Detection Task" was unlocked. <==== ATTENTION
Task: {BF871146-F20A-401C-A14F-61A07FE268AC} - System32\Tasks\McAfee\McAfee Idle Detection Task => {ABCDCA3B-DE6B-5A7C-B132-6D7CBA63E5C5} C:\Program Files\Common Files\McAfee\TaskScheduler\McAMTaskAgent.exe [1032448 2021-08-02] (McAfee, LLC -> McAfee, LLC)
Task: {C2E8058A-E267-4E51-8183-8A827C21E3E2} - System32\Tasks\GoogleUpdateTaskMachineCore => C:\Program Files (x86)\Google\Update\GoogleUpdate.exe [156232 2022-01-14] (Google LLC -> Google LLC)
Task: {D226B63A-28F4-4B19-BA40-3BFF0E226C70} - System32\Tasks\McAfeeLogon => C:\Program Files\Common Files\McAfee\Platform\McUICnt.exe [757944 2021-05-06] (McAfee, LLC -> McAfee, LLC)
Task: {D7A3AC5C-909A-45A4-A715-7B06DE2F237D} - System32\Tasks\Microsoft\Office\Office ClickToRun Service Monitor => C:\Program Files\Common Files\Microsoft Shared\ClickToRun\OfficeC2RClient.exe [24610408 2020-04-09] (Microsoft Corporation -> Microsoft Corporation)
Task: {E258AD12-0FE4-4974-AE6C-53D754BCBFA8} - System32\Tasks\Dell SupportAssistAgent AutoUpdate => C:\Program Files\Dell\SupportAssistAgent\bin\SupportAssistInstaller.exe [1060384 2021-11-15] (Dell Inc -> Dell Inc.)


(If an entry is included in the fixlist, the task (.job) file will be moved. The file which is running by the task will not be moved.)




==================== Internet (Whitelisted) ====================


(If an item is included in the fixlist, if it is a registry item it will be removed or restored to default.)


Tcpip\Parameters: [DhcpNameServer] 192.168.1.1
Tcpip\..\Interfaces\{663293cb-c45c-46c6-bf86-b6c4f76378fb}: [NameServer] 103.86.96.100,103.86.99.100
Tcpip\..\Interfaces\{9193966c-a501-459c-bc0a-30253c059440}: [DhcpNameServer] 192.168.1.1


Edge: 
=======
Edge Profile: C:\Users\StopHacking\AppData\Local\Microsoft\Edge\User Data\Default [2022-01-16]


FireFox:
========
FF HKLM\...\Thunderbird\Extensions: [msktbird@mcafee.com] - C:\Program Files\McAfee\MSKHKLM => not found
FF Plugin: @mcafee.com/MSC,version=10 -> C:\Program Files\McAfee\MSC\npMcSnFFPl64.dll [2021-12-11] (McAfee, LLC -> )
FF Plugin: @microsoft.com/SharePoint,version=14.0 -> C:\Program Files\Microsoft Office\root\Office16\NPSPWRAP.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
FF Plugin-x32: @mcafee.com/MSC,version=10 -> C:\Program Files (x86)\McAfee\MSC\npMcSnFFPl.dll [2021-12-11] (McAfee, LLC -> )
FF Plugin-x32: @microsoft.com/SharePoint,version=14.0 -> C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\NPSPWRAP.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)


Chrome: 
=======
CHR Profile: C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default [2022-01-16]
CHR Extension: (Slides) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\aapocclcgogkmnckokdopfmhonfmgoek [2022-01-14]
CHR Extension: (Docs) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\aohghmighlieiainnegkcijnfilokake [2022-01-14]
CHR Extension: (Google Drive) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\apdfllckaahabafndbhieahigkjlhalf [2022-01-14]
CHR Extension: (YouTube) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\blpcfgokakmgnkcojhhkbfbldkacnbeo [2022-01-14]
CHR Extension: (Sheets) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\felcaaldnbdncclmgdcncolpebgiejap [2022-01-14]
CHR Extension: (Google Docs Offline) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\ghbmnnjooekpmoecnnnilnnbdlolhkhi [2022-01-14]
CHR Extension: (AdBlock &#8212; best ad blocker) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\gighmmpiobklfepjocnamgkkbiglidom [2022-01-14]
CHR Extension: (Chrome Web Store Payments) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\nmmhkkegccagdldgiimedpiccmgmieda [2022-01-14]
CHR Extension: (Gmail) - C:\Users\StopHacking\AppData\Local\Google\Chrome\User Data\Default\Extensions\pjkljhegncpnkpknbcohdijeoejaedia [2022-01-14]
CHR HKLM\...\Chrome\Extension: [fheoggkfdfchfphceeifdbepaooicaho]
CHR HKLM-x32\...\Chrome\Extension: [fheoggkfdfchfphceeifdbepaooicaho]


==================== Services (Whitelisted) ===================


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)


S2 0221201642290449mcinstcleanup; C:\ProgramData\McInstTemp0221201642290449\McInst.exe [873408 2021-12-07] (McAfee, LLC -> McAfee, LLC)
S2 ClickToRunSvc; C:\Program Files\Common Files\Microsoft Shared\ClickToRun\OfficeClickToRun.exe [11109232 2020-04-09] (Microsoft Corporation -> Microsoft Corporation)
R2 DDVCollectorSvcApi; C:\Program Files\Dell\DellDataVault\DDVCollectorSvcApi.exe [436256 2021-09-29] (Dell Technologies Inc. -> Dell Technologies Inc.)
R2 DDVDataCollector; C:\Program Files\Dell\DellDataVault\DDVDataCollector.exe [3847712 2021-09-29] (Dell Technologies Inc. -> Dell Technologies Inc.)
R2 DDVRulesProcessor; C:\Program Files\Dell\DellDataVault\DDVRulesProcessor.exe [462880 2021-09-29] (Dell Technologies Inc. -> Dell Technologies Inc.)
R2 Dell Digital Delivery Services; c:\Program Files (x86)\Dell Digital Delivery Services\Dell.D3.WinSvc.exe [40656 2020-04-09] (Dell Inc -> )
R2 Dell Hardware Support; C:\Program Files\Dell\SupportAssistAgent\PCD\SupportAssist\Dsapi.exe [1024680 2021-09-01] (PC-Doctor, Inc. -> PC-Doctor, Inc.)
R2 Dell SupportAssist Remediation; C:\Program Files\Dell\SARemediation\agent\DellSupportAssistRemedationService.exe [17608 2020-08-10] (Dell Inc -> Dell INC.)
S2 DellClientManagementService; C:\Program Files (x86)\Dell\UpdateService\ServiceShell.exe [38600 2021-11-11] (Dell Inc -> )
R2 McAfee WebAdvisor; C:\Program Files\McAfee\WebAdvisor\ServiceHost.exe [971504 2022-01-14] (McAfee, LLC -> McAfee, LLC)
R2 McAPExe; C:\Program Files\Common Files\McAfee\VSCore_21_9\McApExe.exe [797576 2021-12-07] (McAfee, LLC -> McAfee, LLC)
S3 McAWFwk; C:\Program Files\Common Files\McAfee\ActWiz\McAWFwk.exe [584296 2020-02-06] (McAfee, LLC. -> McAfee, LLC.)
R2 mccspsvc; C:\Program Files\Common Files\McAfee\CSP\4.9.104.0\\McCSPServiceHost.exe [2671064 2021-11-26] (McAfee, LLC -> McAfee, LLC)
S3 mfefire; C:\Program Files\Common Files\McAfee\SystemCore\mfemms.exe [1242112 2021-09-24] (McAfee, Inc. -> McAfee, LLC)
R2 mfemms; C:\Program Files\Common Files\McAfee\SystemCore\mfemms.exe [1242112 2021-09-24] (McAfee, Inc. -> McAfee, LLC)
R3 mfevtp; C:\Program Files\Common Files\McAfee\SystemCore\mfemms.exe [1242112 2021-09-24] (McAfee, Inc. -> McAfee, LLC)
R2 ModuleCoreService; C:\Program Files\Common Files\McAfee\ModuleCore\ModuleCoreService.exe [1681704 2021-12-10] (McAfee, LLC -> McAfee, LLC)
R2 nordvpn-service; C:\Program Files\NordVPN\nordvpn-service.exe [280440 2021-06-05] (nordvpn s.a. -> TEFINCOM S.A.)
R2 PEFService; C:\Program Files\Common Files\McAfee\PEF\CORE\PEFService.exe [4288832 2021-08-31] (McAfee, LLC -> McAfee, LLC)
S2 RAPSService; C:\Program Files\Rivet Networks\SmartByte\RAPSService.exe [66296 2021-08-13] (Rivet Networks LLC -> Rivet Networks, LLC.)
S3 RNDBWM; C:\Program Files\Rivet Networks\SmartByte\RNDBWMService.exe [66296 2021-08-13] (Rivet Networks LLC -> Rivet Networks, LLC.)
R2 SmartByte Analytics Service; C:\Program Files\Rivet Networks\SmartByte\SmartByteAnalyticsService.exe [1633040 2021-08-13] (Rivet Networks LLC -> Rivet Networks)
R2 SmartByte Network Service x64; C:\Program Files\Rivet Networks\SmartByte\SmartByteNetworkService.exe [2390800 2021-08-13] (Rivet Networks LLC -> Rivet Networks)
R2 SupportAssistAgent; C:\Program Files\Dell\SupportAssistAgent\bin\SupportAssistAgent.exe [39968 2021-11-15] (Dell Inc -> Dell Inc.)
S3 WdNisSvc; C:\Program Files\Windows Defender\NisSrv.exe [3004048 2019-12-07] (Microsoft Windows Publisher -> Microsoft Corporation)
S3 WinDefend; C:\Program Files\Windows Defender\MsMpEng.exe [103384 2019-12-07] (Microsoft Windows Publisher -> Microsoft Corporation)


===================== Drivers (Whitelisted) ===================


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)


R3 cfwids; C:\Windows\System32\drivers\cfwids.sys [74752 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
R3 DDDriver; C:\Windows\System32\drivers\dddriver64Dcsa.sys [43400 2021-09-09] (Microsoft Windows Hardware Compatibility Publisher -> Dell Technologies)
S3 mfeaack; C:\Windows\System32\drivers\mfeaack.sys [574464 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
U3 mfeaack01; no ImagePath
R3 mfeavfk; C:\Windows\System32\drivers\mfeavfk.sys [390656 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
U3 mfeavfk01; no ImagePath
S0 mfeelamk; C:\Windows\System32\drivers\mfeelamk.sys [90048 2021-09-28] (Microsoft Windows Early Launch Anti-malware Publisher -> McAfee, LLC)
R3 mfefirek; C:\Windows\System32\drivers\mfefirek.sys [526336 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
R0 mfehidk; C:\Windows\System32\drivers\mfehidk.sys [1088512 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
U3 mfehidk01; no ImagePath
R3 mfencbdc; C:\Windows\System32\DRIVERS\mfencbdc.sys [638464 2021-09-16] (McAfee, Inc. -> McAfee LLC.)
U3 mfencbdc01; no ImagePath
U3 mfencbdc02; no ImagePath
S3 mfencrk; C:\Windows\System32\DRIVERS\mfencrk.sys [110080 2021-09-16] (McAfee, Inc. -> McAfee LLC.)
R3 mfeplk; C:\Windows\System32\drivers\mfeplk.sys [118784 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
R0 mfewfpk; C:\Windows\System32\drivers\mfewfpk.sys [256512 2021-09-28] (McAfee, Inc. -> McAfee, LLC)
R2 NDivert; C:\Program Files\NordVPN\Drivers\NDivert.sys [128856 2021-06-09] (nordvpn s.a. -> Nordvpn S.A.)
R1 nordlwf; C:\Windows\system32\DRIVERS\nordlwf.sys [42576 2021-06-13] (nordvpn s.a. -> TEFINCOM S.A.)
R3 SmbCoSvc; C:\Windows\system32\DRIVERS\SmbCo10X64.sys [166032 2021-08-13] (Intel Corporation -> Rivet Networks, LLC.)
R3 tapnordvpn; C:\Windows\System32\drivers\tapnordvpn.sys [49744 2021-06-13] (nordvpn s.a. -> The OpenVPN Project)
S3 WdBoot; C:\Windows\system32\drivers\WdBoot.sys [46688 2019-12-07] (Microsoft Windows Early Launch Anti-malware Publisher -> Microsoft Corporation)
S3 WdFilter; C:\Windows\system32\drivers\WdFilter.sys [350136 2019-12-07] (Microsoft Windows -> Microsoft Corporation)
S3 WdNisDrv; C:\Windows\System32\Drivers\WdNisDrv.sys [54200 2019-12-07] (Microsoft Windows -> Microsoft Corporation)
R3 wintun; C:\Windows\system32\DRIVERS\wintun.sys [29680 2022-01-14] (Microsoft Windows Hardware Compatibility Publisher -> WireGuard LLC)
S4 DBUtilDrv2; \SystemRoot\System32\drivers\DBUtilDrv2.sys [X]


==================== NetSvcs (Whitelisted) ===================


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)




==================== Three months (created) (Whitelisted) =========


(If an entry is included in the fixlist, the file/folder will be moved.)


2022-01-16 05:59 - 2022-01-16 06:00 - 000020573 _____ C:\Users\StopHacking\Downloads\FRST.txt
2022-01-16 05:59 - 2022-01-16 05:59 - 000000000 ____D C:\FRST
2022-01-16 05:57 - 2022-01-16 05:57 - 002311680 _____ (Farbar) C:\Users\StopHacking\Downloads\FRST64 (1).exe
2022-01-16 05:47 - 2022-01-16 05:47 - 002311680 _____ (Farbar) C:\Users\StopHacking\Downloads\FRST64.exe
2022-01-15 18:44 - 2022-01-15 18:45 - 000000000 ____D C:\ProgramData\Temp
2022-01-15 18:44 - 2022-01-15 18:44 - 000000000 ____D C:\Windows\{2F366A08-5179-4948-A3AD-CB3F835A5AD5}
2022-01-15 18:43 - 2022-01-15 18:43 - 000000000 ____D C:\Program Files\Rivet Networks
2022-01-15 18:42 - 2022-01-15 18:42 - 000000000 _____ C:\Windows\invcol.tmp
2022-01-15 18:39 - 2022-01-15 18:39 - 000000000 ____D C:\ProgramData\Microsoft\Windows\Start Menu\Programs\McAfee
2022-01-15 17:47 - 2022-01-15 17:47 - 000000000 ____D C:\ProgramData\McInstTemp0221201642290449
2022-01-15 17:46 - 2022-01-15 17:47 - 000000000 ____D C:\ProgramData\McInstTemp0218651642290371
2022-01-14 22:29 - 2022-01-14 22:29 - 000000000 ___SD C:\Windows\SysWOW64\lxss
2022-01-14 22:29 - 2022-01-14 22:29 - 000000000 ___SD C:\Windows\system32\lxss
2022-01-14 22:11 - 2022-01-14 22:15 - 000000000 ____D C:\Users\StopHacking\AppData\Roaming\balena-etcher
2022-01-14 22:11 - 2022-01-14 22:11 - 000002492 _____ C:\Users\StopHacking\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\balenaEtcher.lnk
2022-01-14 22:11 - 2022-01-14 22:11 - 000002484 _____ C:\Users\StopHacking\Desktop\balenaEtcher.lnk
2022-01-14 22:11 - 2022-01-14 22:11 - 000000000 ____D C:\Users\StopHacking\AppData\Local\balena-etcher-updater
2022-01-14 21:41 - 2022-01-14 21:42 - 145457016 _____ (Balena Inc.) C:\Users\StopHacking\Downloads\balenaEtcher-Setup-1.7.3.exe
2022-01-14 21:39 - 2022-01-14 21:50 - 3071934464 _____ C:\Users\StopHacking\Downloads\ubuntu-20.04.3-desktop-amd64.iso
2022-01-14 20:58 - 2022-01-14 20:58 - 000000000 ___HD C:\$WinREAgent
2022-01-14 19:43 - 2022-01-16 04:30 - 000000000 ____D C:\Users\StopHacking\AppData\Local\D3DSCache
2022-01-14 19:41 - 2022-01-14 19:41 - 000002325 _____ C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Google Chrome.lnk
2022-01-14 19:41 - 2022-01-14 19:41 - 000002284 _____ C:\Users\Public\Desktop\Google Chrome.lnk
2022-01-14 19:41 - 2022-01-14 19:41 - 000000000 ____D C:\Program Files\Google
2022-01-14 19:40 - 2022-01-16 05:45 - 000000000 ____D C:\Program Files (x86)\Google
2022-01-14 19:40 - 2022-01-14 19:45 - 000000000 ____D C:\Users\StopHacking\AppData\Local\Google
2022-01-14 19:40 - 2022-01-14 19:40 - 001341272 _____ (Google LLC) C:\Users\StopHacking\Downloads\ChromeSetup.exe
2022-01-14 19:40 - 2022-01-14 19:40 - 000003420 _____ C:\Windows\system32\Tasks\GoogleUpdateTaskMachineUA
2022-01-14 19:40 - 2022-01-14 19:40 - 000003296 _____ C:\Windows\system32\Tasks\GoogleUpdateTaskMachineCore
2022-01-14 19:16 - 2022-01-14 19:16 - 000029680 _____ (WireGuard LLC) C:\Windows\system32\Drivers\wintun.sys
2022-01-14 18:54 - 2022-01-14 18:54 - 000000000 ____D C:\Users\StopHacking\AppData\Local\IsolatedStorage
2022-01-14 18:53 - 2022-01-15 20:07 - 000003592 _____ C:\Windows\system32\Tasks\OneDrive Reporting Task-S-1-5-21-3883862340-2037335681-1545001466-1001
2022-01-14 18:51 - 2022-01-14 23:57 - 000001778 _____ C:\Users\StopHacking\Desktop\NordVPN.lnk
2022-01-14 18:51 - 2022-01-14 23:57 - 000000000 ____D C:\Users\StopHacking\AppData\Local\NordVPN
2022-01-14 18:51 - 2022-01-14 23:57 - 000000000 ____D C:\ProgramData\NordVPN
2022-01-14 18:51 - 2022-01-14 23:57 - 000000000 ____D C:\Program Files\NordVPN
2022-01-14 18:51 - 2021-06-13 11:02 - 000042576 _____ (TEFINCOM S.A.) C:\Windows\system32\Drivers\nordlwf.sys
2022-01-14 18:50 - 2022-01-14 18:50 - 000000000 ____D C:\Program Files\NordVPN network TUN
2022-01-14 18:50 - 2022-01-14 18:50 - 000000000 ____D C:\Program Files (x86)\NordVPN network TAP
2022-01-14 18:48 - 2022-01-14 18:48 - 067191480 _____ (TEFINCOM S.A. ) C:\Users\StopHacking\Downloads\NordVPNSetup.exe
2022-01-14 18:48 - 2022-01-14 16:57 - 000000000 ____D C:\Users\StopHacking\AppData\Local\DELL
2022-01-14 18:45 - 2022-01-15 20:07 - 000003392 _____ C:\Windows\system32\Tasks\OneDrive Standalone Update Task-S-1-5-21-3883862340-2037335681-1545001466-1001
2022-01-14 18:45 - 2022-01-14 18:45 - 000001820 _____ C:\Users\StopHacking\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\MaxxAudio Pro by Waves &#8211; Speaker and Microphone Audio Control and Nx 3D Sound.lnk
2022-01-14 18:45 - 2022-01-14 18:45 - 000000000 ___RD C:\Users\StopHacking\OneDrive
2022-01-14 18:43 - 2022-01-15 05:41 - 000000000 ____D C:\Users\StopHacking\AppData\Local\Packages
2022-01-14 18:43 - 2022-01-14 22:35 - 000000000 __SHD C:\Users\StopHacking\IntelGraphicsProfiles
2022-01-14 18:43 - 2022-01-14 18:45 - 000002354 _____ C:\Users\StopHacking\Desktop\Microsoft Edge.lnk
2022-01-14 18:43 - 2022-01-14 18:44 - 000000000 ____D C:\Users\StopHacking\AppData\Local\Intel
2022-01-14 18:43 - 2022-01-14 18:43 - 000000000 ___RD C:\Users\StopHacking\3D Objects
2022-01-14 18:43 - 2022-01-14 18:43 - 000000000 ____D C:\Users\StopHacking\AppData\Roaming\Adobe
2022-01-14 18:43 - 2022-01-14 18:43 - 000000000 ____D C:\Users\StopHacking\AppData\LocalLow\Intel
2022-01-14 18:43 - 2022-01-14 18:43 - 000000000 ____D C:\Users\StopHacking\AppData\Local\VirtualStore
2022-01-14 18:43 - 2022-01-14 18:43 - 000000000 ____D C:\Users\StopHacking\AppData\Local\ConnectedDevicesPlatform
2022-01-14 18:43 - 2022-01-14 16:58 - 000000000 ____D C:\Users\StopHacking\AppData\Local\Publishers
2022-01-14 18:42 - 2022-01-15 20:07 - 000002403 _____ C:\Users\StopHacking\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.lnk
2022-01-14 18:42 - 2022-01-14 18:45 - 000000000 ____D C:\Users\StopHacking
2022-01-14 18:42 - 2022-01-14 18:42 - 000000020 ___SH C:\Users\StopHacking\ntuser.ini
2022-01-14 18:39 - 2022-01-14 18:39 - 000000000 _SHDL C:\Documents and Settings
2022-01-14 18:39 - 2022-01-14 18:39 - 000000000 ____H C:\Windows\system32\Drivers\Msft_User_WpdFs_01_11_00.Wdf
2022-01-14 16:57 - 2022-01-14 16:57 - 000000000 ____D C:\Users\StopHacking\AppData\Local\Comms
2022-01-14 16:51 - 2022-01-14 22:24 - 000000000 ____D C:\Users\StopHacking\AppData\Local\PlaceholderTileLogoFolder
2022-01-14 16:35 - 2022-01-14 16:37 - 000000000 ____D C:\tmp


==================== Three months (modified) ==================


(If an entry is included in the fixlist, the file/folder will be moved.)


2022-01-16 00:27 - 2020-10-12 08:25 - 000000000 ____D C:\Windows\system32\SleepStudy
2022-01-15 22:46 - 2020-11-05 21:44 - 000000000 ____D C:\Program Files (x86)\Dell Digital Delivery Services
2022-01-15 18:51 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\AppReadiness
2022-01-15 18:45 - 2020-11-05 21:42 - 000000000 ____D C:\Program Files\Dell
2022-01-15 18:45 - 2019-12-07 03:14 - 000000000 ___HD C:\Program Files\WindowsApps
2022-01-15 18:44 - 2019-12-07 03:14 - 000000000 ____D C:\ProgramData\regid.1991-06.com.microsoft
2022-01-15 18:44 - 2019-12-07 03:13 - 000000000 ____D C:\Windows\INF
2022-01-15 18:43 - 2020-11-05 21:51 - 000003068 _____ C:\Windows\system32\Tasks\SmartByte Telemetry
2022-01-15 18:43 - 2020-11-05 21:50 - 000000000 ____D C:\ProgramData\Dell
2022-01-15 18:43 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\Registration
2022-01-15 17:48 - 2020-11-05 21:47 - 000003316 _____ C:\Windows\system32\Tasks\McAfeeLogon
2022-01-15 17:48 - 2020-11-05 21:46 - 000000000 ____D C:\Program Files\Common Files\McAfee
2022-01-15 17:47 - 2020-11-05 21:46 - 000000000 ____D C:\Windows\system32\Tasks\McAfee
2022-01-15 17:47 - 2019-12-07 03:14 - 000000000 ___HD C:\Windows\ELAMBKUP
2022-01-15 17:46 - 2020-11-05 21:46 - 000000000 ____D C:\Program Files (x86)\McAfee
2022-01-15 17:45 - 2020-11-05 21:46 - 000000000 ____D C:\ProgramData\McAfee
2022-01-15 05:41 - 2020-10-12 08:28 - 000002440 _____ C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Microsoft Edge.lnk
2022-01-15 05:34 - 2020-10-12 08:28 - 000003480 _____ C:\Windows\system32\Tasks\MicrosoftEdgeUpdateTaskMachineUA
2022-01-15 05:34 - 2020-10-12 08:28 - 000003356 _____ C:\Windows\system32\Tasks\MicrosoftEdgeUpdateTaskMachineCore
2022-01-15 04:03 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\appcompat
2022-01-14 22:33 - 2020-10-12 08:33 - 000795738 _____ C:\Windows\system32\PerfStringBackup.INI
2022-01-14 22:29 - 2020-11-05 21:39 - 000000000 ____D C:\Intel
2022-01-14 22:29 - 2020-10-12 08:25 - 000008192 ___SH C:\DumpStack.log.tmp
2022-01-14 22:29 - 2020-10-12 08:25 - 000000006 ____H C:\Windows\Tasks\SA.DAT
2022-01-14 22:29 - 2019-12-07 03:03 - 000524288 _____ C:\Windows\system32\config\BBI
2022-01-14 22:29 - 2019-12-07 03:03 - 000000000 ____D C:\Windows\CbsTemp
2022-01-14 22:28 - 2020-10-12 09:18 - 002486584 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\vmswitch.sys
2022-01-14 22:28 - 2020-10-12 09:18 - 000291640 _____ (Microsoft Corporation) C:\Windows\system32\nvspinfo.exe
2022-01-14 22:28 - 2020-10-12 09:18 - 000286008 _____ (Microsoft Corporation) C:\Windows\system32\vmsif.dll
2022-01-14 22:28 - 2020-10-12 09:18 - 000199168 _____ (Microsoft Corporation) C:\Windows\system32\wsl.exe
2022-01-14 22:28 - 2020-10-12 09:18 - 000078848 _____ (Microsoft Corporation) C:\Windows\system32\wslconfig.exe
2022-01-14 22:28 - 2020-10-12 09:18 - 000064512 _____ (Microsoft Corporation) C:\Windows\system32\bash.exe
2022-01-14 22:28 - 2020-10-12 09:18 - 000051000 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\VmsProxy.sys
2022-01-14 22:28 - 2020-10-12 09:18 - 000039224 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\VmsProxyHNic.sys
2022-01-14 22:28 - 2019-12-07 03:09 - 001115664 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\lxcore.sys
2022-01-14 22:28 - 2019-12-07 03:09 - 000222008 _____ (Microsoft Corporation) C:\Windows\system32\NetMgmtIF.dll
2022-01-14 22:28 - 2019-12-07 03:09 - 000151352 _____ C:\Windows\system32\nmscrub.exe
2022-01-14 22:28 - 2019-12-07 03:09 - 000142648 _____ (Microsoft Corporation) C:\Windows\system32\nmbind.exe
2022-01-14 22:28 - 2019-12-07 03:09 - 000123704 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\vmbkmclr.sys
2022-01-14 22:28 - 2019-12-07 03:09 - 000122168 _____ (Microsoft Corporation) C:\Windows\system32\vmsifcore.dll
2022-01-14 22:28 - 2019-12-07 03:09 - 000107048 _____ (Microsoft Corporation) C:\Windows\system32\p9np.dll
2022-01-14 22:28 - 2019-12-07 03:09 - 000091152 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\p9rdr.sys
2022-01-14 22:28 - 2019-12-07 03:09 - 000081208 _____ (Microsoft Corporation) C:\Windows\SysWOW64\p9np.dll
2022-01-14 22:28 - 2019-12-07 03:09 - 000027960 _____ (Microsoft Corporation) C:\Windows\system32\vmsifproxystub.dll
2022-01-14 22:28 - 2019-12-07 03:09 - 000015880 _____ (Microsoft Corporation) C:\Windows\system32\Drivers\lxss.sys
2022-01-14 22:24 - 2020-11-05 21:57 - 000000000 ____D C:\ProgramData\Packages
2022-01-14 18:51 - 2020-11-05 21:50 - 000000000 ____D C:\ProgramData\Package Cache
2022-01-14 18:43 - 2020-10-12 08:43 - 000000000 ___RD C:\Users\Public\AccountPictures
2022-01-14 18:42 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\system32\WinBioDatabase
2022-01-14 18:41 - 2019-12-07 03:50 - 000000000 ____D C:\Windows\system32\FxsTmp
2022-01-14 18:41 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\system32\spool
2022-01-14 18:14 - 2020-11-05 21:46 - 000003710 _____ C:\Windows\system32\Tasks\McAfee Remediation (Prepare)
2022-01-14 17:30 - 2020-11-05 21:42 - 000000000 ____D C:\ProgramData\PCDr
2022-01-14 17:30 - 2020-11-05 21:42 - 000000000 ____D C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Dell
2022-01-14 17:29 - 2020-11-05 21:57 - 000003914 _____ C:\Windows\system32\Tasks\Dell SupportAssistAgent AutoUpdate
2022-01-14 17:16 - 2020-11-05 21:46 - 000000000 ____D C:\Program Files\McAfee
2022-01-14 16:57 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\ServiceState
2022-01-14 16:56 - 2019-12-07 03:03 - 000032768 _____ C:\Windows\system32\config\ELAM
2022-01-14 16:55 - 2019-12-07 03:14 - 000000000 ____D C:\Windows\system32\NDF


==================== SigCheckExt =========================


2022-01-16 05:57 - 2022-01-16 05:57 - 002311680 _____ (Farbar) C:\Users\StopHacking\Downloads\FRST64 (1).exe
2022-01-16 05:47 - 2022-01-16 05:47 - 002311680 _____ (Farbar) C:\Users\StopHacking\Downloads\FRST64.exe


==================== SigCheck ============================


(There is no automatic fix for files that do not pass verification.)




==================== BCD ================================


Firmware Boot Manager
---------------------
identifier              {fwbootmgr}
displayorder            {bootmgr}
                        {72da8d8b-6f82-11ec-85f6-806e6f6e6963}
                        {72da8d8c-6f82-11ec-85f6-806e6f6e6963}
                        {af5ad3f5-1fe1-11eb-85e1-806e6f6e6963}
                        {af5ad3f6-1fe1-11eb-85e1-806e6f6e6963}
timeout                 0


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {16dcf3b2-1fdf-11eb-913c-70b5e83648cd}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 300


Firmware Application (101fffff)
-------------------------------
identifier              {72da8d8b-6f82-11ec-85f6-806e6f6e6963}
device                  unknown
path                    \EFI\Boot\BootX64.efi
description             UEFI: ST1000DM003-1ER162


Firmware Application (101fffff)
-------------------------------
identifier              {72da8d8c-6f82-11ec-85f6-806e6f6e6963}
device                  unknown
path                    \EFI\Boot\BootX64.efi
description             UEFI: Samsung SSD 850 EVO 250GB




Resume from Hibernate
---------------------
identifier              {16dcf3b2-1fdf-11eb-913c-70b5e83648cd}
device                  partition=C:
path                    \Windows\system32\winresume.efi
description             Windows Resume Application
locale                  en-US
inherit                 {resumeloadersettings}
recoverysequence        {dcd5eb6a-1fe7-11eb-be53-70b5e83648cd}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
filedevice              partition=C:
filepath                \hiberfil.sys
bootmenupolicy          Standard
debugoptionenabled      No


Windows Memory Tester
---------------------
identifier              {memdiag}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Microsoft\Boot\memtest.efi
description             Windows Memory Diagnostic
locale                  en-US
inherit                 {globalsettings}
badmemoryaccess         Yes


EMS Settings
------------
identifier              {emssettings}
bootems                 No


Debugger Settings
-----------------
identifier              {dbgsettings}
debugtype               Local


RAM Defects
-----------
identifier              {badmemory}


Global Settings
---------------
identifier              {globalsettings}
inherit                 {dbgsettings}
                        {emssettings}
                        {badmemory}


Boot Loader Settings
--------------------
identifier              {bootloadersettings}
inherit                 {globalsettings}
                        {hypervisorsettings}


Hypervisor Settings
-------------------
identifier              {hypervisorsettings}
hypervisordebugtype     Serial
hypervisordebugport     1
hypervisorbaudrate      115200


Resume Loader Settings
----------------------
identifier              {resumeloadersettings}
inherit                 {globalsettings}


Device options
--------------
identifier              {492933ee-cd0d-11e1-9b66-d4bed91b7fc5}
ramdisksdidevice        partition=\Device\HarddiskVolume6
ramdisksdipath          \sources\boot.sdi


Setup Ramdisk Options
---------------------
identifier              {ramdiskoptions}
ramdisksdidevice        partition=\Device\HarddiskVolume6
ramdisksdipath          \sources\boot.sdi


Device options
--------------
identifier              {dcd5eb6b-1fe7-11eb-be53-70b5e83648cd}
description             Windows Recovery
ramdisksdidevice        partition=\Device\HarddiskVolume4
ramdisksdipath          \Recovery\WindowsRE\boot.sdi


==================== End of FRST.txt ========================


Additional scan result of Farbar Recovery Scan Tool (x64) Version: 15-01-2022
Ran by StopHacking (16-01-2022 06:00:59)
Running from C:\Users\StopHacking\Downloads
Microsoft Windows 10 Home Version 2004 19041.450 (X64) (2022-01-15 00:39:20)
Boot Mode: Normal
==========================================================




==================== Accounts: =============================




(If an entry is included in the fixlist, it will be removed.)


Administrator (S-1-5-21-3883862340-2037335681-1545001466-500 - Administrator - Disabled)
DefaultAccount (S-1-5-21-3883862340-2037335681-1545001466-503 - Limited - Disabled)
Guest (S-1-5-21-3883862340-2037335681-1545001466-501 - Limited - Disabled)
StopHacking (S-1-5-21-3883862340-2037335681-1545001466-1001 - Administrator - Enabled) => C:\Users\StopHacking
WDAGUtilityAccount (S-1-5-21-3883862340-2037335681-1545001466-504 - Limited - Disabled)


==================== Security Center ========================


(If an entry is included in the fixlist, it will be removed.)


AV: Windows Defender (Disabled - Up to date) {D68DDC3A-831F-4fae-9E44-DA132C1ACF46}
AV: McAfee VirusScan (Enabled - Up to date) {9D4501E6-72F6-2877-C789-89AF6F535B2C}
FW: McAfee Firewall (Enabled) {A57E80C3-3899-292F-ECD6-209A91801C57}


==================== Installed Programs ======================


(Only the adware programs with "Hidden" flag could be added to the fixlist to unhide them. The adware programs should be uninstalled manually.)


balenaEtcher 1.7.3 (HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\d2f3b6c7-6f49-59e2-b8a5-f72e33900c2b) (Version: 1.7.3 - Balena Inc.)
Dell Digital Delivery Services (HKLM-x32\...\{CC5730C7-C867-43BD-94DA-00BB3836906F}) (Version: 4.0.52.0 - Dell Inc.)
Dell Mobile Connect Drivers (HKLM\...\{2D27B76E-8FB1-495B-A61D-FB76349E7E36}) (Version: 3.1.9518 - Screenovate Technologies Ltd.)
Dell SupportAssist (HKLM\...\{E0659C89-D276-4B77-A5EC-A8F2F042E78F}) (Version: 3.10.4.18 - Dell Inc.)
Dell SupportAssist Remediation (HKLM\...\{28CCD076-0839-4837-9B2D-EF35E7BF2488}) (Version: 5.2.0.12833 - Dell Inc.) Hidden
Dell SupportAssist Remediation (HKLM-x32\...\{3c7a4bc1-7c12-40a9-be55-a4a2c1b415bd}) (Version: 5.2.0.12833 - Dell Inc.)
Dell Update - SupportAssist Update Plugin (HKLM-x32\...\{819b927b-a8d8-46a9-9512-0326900f80e3}) (Version: 5.2.0.12833 - Dell Inc.)
Dell Update for Windows Universal (HKLM\...\{41D2D254-D869-4CD8-B440-5DF49083C4BA}) (Version: 4.4.0 - Dell Inc.)
Dynamic Application Loader Host Interface Service (HKLM\...\{044CFD6C-2031-4589-B764-308FB8DDE6EF}) (Version: 1.0.0.0 - Intel Corporation) Hidden
Google Chrome (HKLM-x32\...\Google Chrome) (Version: 97.0.4692.71 - Google LLC)
Intel(R) Management Engine Components (HKLM\...\{1CEAC85D-2590-4760-800F-8DE5E91F3700}) (Version: 2009.14.0.1496 - Intel Corporation)
Intel(R) Processor Graphics (HKLM-x32\...\{F0E3AD40-2BBD-4360-9C76-B9AC9A5886EA}) (Version: 26.20.100.8141 - Intel Corporation)
McAfee LiveSafe (HKLM-x32\...\MSC) (Version: 16.0 R42 - McAfee, LLC)
Microsoft Edge (HKLM-x32\...\Microsoft Edge) (Version: 97.0.1072.62 - Microsoft Corporation)
Microsoft Office 365 - en-us (HKLM\...\O365HomePremRetail - en-us) (Version: 16.0.12527.20482 - Microsoft Corporation)
Microsoft OneDrive (HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\OneDriveSetup.exe) (Version: 21.245.1128.0002 - Microsoft Corporation)
Microsoft Visual C++ 2015-2019 Redistributable (x64) - 14.29.30139 (HKLM-x32\...\{2c673fb6-3e65-4751-965d-33d30b68a8a6}) (Version: 14.29.30139.0 - Microsoft Corporation)
NordVPN (HKLM\...\{19465C24-3D5D-4327-B99F-3CC0A1D38151}_is1) (Version: 6.41.11.0 - TEFINCOM S.A.)
NordVPN network TAP (HKLM-x32\...\{97DEC5D6-2BE9-45BB-BFC5-274B851B486B}) (Version: 1.0.1 - NordVPN)
NordVPN network TUN (HKLM\...\{BD0E4F38-D3F6-452D-A32E-B14D721839AC}) (Version: 1.0.1 - NordVPN)
Office 16 Click-to-Run Extensibility Component (HKLM\...\{90160000-008C-0000-1000-0000000FF1CE}) (Version: 16.0.12527.20482 - Microsoft Corporation) Hidden
Office 16 Click-to-Run Licensing Component (HKLM\...\{90160000-007E-0000-1000-0000000FF1CE}) (Version: 16.0.12527.20482 - Microsoft Corporation) Hidden
Office 16 Click-to-Run Localization Component (HKLM\...\{90160000-008C-0409-1000-0000000FF1CE}) (Version: 16.0.12527.20482 - Microsoft Corporation) Hidden
Realtek High Definition Audio Driver (HKLM-x32\...\{F132AF7F-7BCA-4EDE-8A7C-958108FE7DBC}) (Version: 6.0.8865.1 - Realtek Semiconductor Corp.)
SmartByte Drivers and Services (HKLM\...\{A0CDAD3D-0329-4E3E-8DC1-30E333D6564D}) (Version: 3.1.995 - Rivet Networks)
WebAdvisor by McAfee (HKLM-x32\...\{35ED3F83-4BDC-4c44-8EC6-6A8301C7413A}) (Version: 4.1.1.663 - McAfee, LLC)


Packages:
=========
Cortana -> C:\Program Files\WindowsApps\Microsoft.549981C3F5F10_1.1911.21713.0_x64__8wekyb3d8bbwe [2019-12-07] (Microsoft Corporation)
Dell Customer Connect -> C:\Program Files\WindowsApps\DellInc.DellCustomerConnect_5.2.45.0_x64__htrsf667h5kn2 [2020-11-05] (Dell Inc)
Dell SupportAssist for Home PCs -> C:\Program Files\WindowsApps\DellInc.DellSupportAssistforPCs_3.10.7.0_x64__htrsf667h5kn2 [2022-01-14] (Dell Inc)
Dell Update -> C:\Program Files\WindowsApps\DellInc.DellUpdate_4.4.18.0_x86__htrsf667h5kn2 [2022-01-15] (Dell Inc)
Disney+ -> C:\Program Files\WindowsApps\Disney.37853FC22B2CE_1.22.3.0_x64__6rarf9sa4v8jt [2022-01-14] (Disney)
Ditto Clipboard -> C:\Program Files\WindowsApps\60145ScottBrogden.ditto-cp_3.24.214.0_x86__n6b029mg40na2 [2022-01-14] (Scott Brogden) [Startup Task]
Dropbox promotion -> C:\Program Files\WindowsApps\C27EB4BA.DropboxOEM_16.4.9.0_x64__xbfy0k16fey96 [2020-11-05] (Dropbox Inc.)
Intel® Graphics Command Center -> C:\Program Files\WindowsApps\AppUp.IntelGraphicsExperience_1.100.3407.0_x64__8j3eq9eme6ctt [2022-01-14] (INTEL CORP) [Startup Task]
Intel® Optane&#8482; Memory and Storage Management -> C:\Program Files\WindowsApps\AppUp.IntelOptaneMemoryandStorageManagement_17.8.1007.0_x64__8j3eq9eme6ctt [2020-11-05] (INTEL CORP)
Mail and Calendar -> C:\Program Files\WindowsApps\microsoft.windowscommunicationsapps_16005.11629.20316.0_x64__8wekyb3d8bbwe [2019-12-07] (Microsoft Corporation) [MS Ad]
McAfee® Personal Security -> C:\Program Files\WindowsApps\5A894077.McAfeeSecurity_2.1.38.0_x64__wafk5atnkzcwy [2020-11-05] (McAfee LLC.)
Media Suite Essentials for Dell -> C:\Program Files\WindowsApps\DB6EA5DB.MediaSuiteEssentialsforDell_2.6.4028.0_x86__mcezb6ze687jp [2020-11-05] (CYBERLINK CORPORATION.)
Microsoft Advertising SDK for XAML -> C:\Program Files\WindowsApps\Microsoft.Advertising.Xaml_10.1808.3.0_x64__8wekyb3d8bbwe [2019-12-07] (Microsoft Corporation) [MS Ad]
Microsoft Solitaire Collection -> C:\Program Files\WindowsApps\Microsoft.MicrosoftSolitaireCollection_4.4.8204.0_x64__8wekyb3d8bbwe [2019-12-07] (Microsoft Studios) [MS Ad]
MPEG-2 Video Extension -> C:\Program Files\WindowsApps\Microsoft.MPEG2VideoExtension_1.0.22661.0_x64__8wekyb3d8bbwe [2020-05-05] (Microsoft Corporation)
MSN Weather -> C:\Program Files\WindowsApps\Microsoft.BingWeather_4.25.20211.0_x64__8wekyb3d8bbwe [2019-12-07] (Microsoft Corporation) [MS Ad]
My Dell -> C:\Program Files\WindowsApps\DellInc.MyDell_1.5.26.0_x64__htrsf667h5kn2 [2020-11-05] (Dell Inc)
Netflix -> C:\Program Files\WindowsApps\4DF9E0F8.Netflix_6.93.375.0_x64__mcm4njqhnhss8 [2020-11-05] (Netflix, Inc.)
Partner Promo -> C:\Program Files\WindowsApps\DellInc.PartnerPromo_1.0.21.0_x64__htrsf667h5kn2 [2020-11-05] (Dell Inc)
Power Media Player for Dell -> C:\Program Files\WindowsApps\DB6EA5DB.PowerMediaPlayerforDell_14.1.8708.0_x86__mcezb6ze687jp [2020-11-05] (CYBERLINK CORPORATION.)
Power2Go for Dell -> C:\Program Files\WindowsApps\DB6EA5DB.Power2GoforDell_11.0.3920.0_x86__mcezb6ze687jp [2020-11-05] (CYBERLINK CORPORATION.) [Startup Task]
PowerDirector for Dell -> C:\Program Files\WindowsApps\DB6EA5DB.PowerDirectorforDell_15.0.3826.0_x64__mcezb6ze687jp [2020-11-05] (CYBERLINK CORPORATION.)
Skype -> C:\Program Files\WindowsApps\Microsoft.SkypeApp_14.53.77.0_x64__kzf8qxf38zg5c [2019-12-07] (Skype)
SmartByte -> C:\Program Files\WindowsApps\RivetNetworks.SmartByte_3.1.937.0_x64__rh07ty8m5nkag [2020-11-05] (Rivet Networks LLC)
Spotify Music -> C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0 [2022-01-14] (Spotify AB) [Startup Task]
Ubuntu -> C:\Program Files\WindowsApps\CanonicalGroupLimited.UbuntuonWindows_2004.2021.825.0_x64__79rhkp1fndgsc [2022-01-14] (Canonical Group Limited)
Waves MaxxAudio Pro for Dell 2020 -> C:\Program Files\WindowsApps\WavesAudio.MaxxAudioProforDell2020_3.0.98.0_x64__fh4rh281wavaa [2022-01-14] (Waves Audio)


==================== Custom CLSID (Whitelisted): ==============


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)


CustomCLSID: HKU\S-1-5-21-3883862340-2037335681-1545001466-1001_Classes\CLSID\{0BAD39CB-DD3E-4F21-9156-649B0156C28E}\localserver32 -> C:\Windows\System32\DriverStore\FileRepository\wavesapo9de.inf_amd64_0dc1f198e733bf19\WavesSvc64.exe (Waves Inc -> Waves Audio Ltd.)
ContextMenuHandlers1: [McCtxMenuFrmWrk] -> {CCA9EFD3-29ED-430A-BA6D-E6BBFF0A60C2} => C:\Program Files\McAfee\MSC\McCtxMenuFrmWrk.dll [2021-12-11] (McAfee, LLC -> McAfee, LLC)
ContextMenuHandlers6: [McCtxMenuFrmWrk] -> {CCA9EFD3-29ED-430A-BA6D-E6BBFF0A60C2} => C:\Program Files\McAfee\MSC\McCtxMenuFrmWrk.dll [2021-12-11] (McAfee, LLC -> McAfee, LLC)


==================== Codecs (Whitelisted) ====================


==================== Shortcuts & WMI ========================


==================== Loaded Modules (Whitelisted) =============


2020-04-09 22:11 - 2020-04-09 22:11 - 000019456 _____ () [File not signed] c:\Program Files (x86)\Dell Digital Delivery Services\Dell.D3.HSA.Server.dll
2022-01-14 21:23 - 2022-01-14 21:23 - 000017408 _____ () [File not signed] C:\Program Files\WindowsApps\60145ScottBrogden.ditto-cp_3.24.214.0_x86__n6b029mg40na2\ICU_Loader.dll
2022-01-14 21:23 - 2022-01-14 21:23 - 000043008 _____ (Ditto Utility Addin) [File not signed] C:\Program Files\WindowsApps\60145ScottBrogden.ditto-cp_3.24.214.0_x86__n6b029mg40na2\Addins\DittoUtil.dll
2021-08-13 16:57 - 2021-08-13 16:57 - 000122880 _____ (Rivet Networks) [File not signed] C:\Program Files\Rivet Networks\SmartByte\KillerNetworkServicePS.dll
2021-11-12 04:56 - 2021-11-12 04:56 - 001638912 _____ (Robert Simpson, et al.) [File not signed] C:\Program Files\Dell\SupportAssistAgent\bin\x64\SQLite.Interop.dll


==================== Alternate Data Streams (Whitelisted) ========


==================== Safe Mode (Whitelisted) ==================


(If an entry is included in the fixlist, it will be removed from the registry. The "AlternateShell" will be restored.)


HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Minimal\MCODS => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Minimal\mcpltsvc => ""=""
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Minimal\ModuleCoreService => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mcapexe => ""=""
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\McMPFSvc => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\MCODS => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mcpltsvc => ""=""
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeaack => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeaack.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeavfk => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeavfk.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfefire => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfefirek => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfefirek.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfehidk => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfehidk.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfemms => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeplk => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfeplk.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfetdi2k => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfetdi2k.sys => ""="Driver"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\mfevtp => ""="Service"
HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network\ModuleCoreService => ""="Service"


==================== Association (Whitelisted) =================


==================== Internet Explorer (Whitelisted) ==========


BHO: McAfee WebAdvisor -> {B164E929-A1B6-4A06-B104-2CD0E90A88FF} -> C:\Program Files\McAfee\WebAdvisor\x64\IEPlugin.dll [2022-01-14] (McAfee, LLC -> McAfee, LLC)
BHO-x32: Skype for Business Browser Helper -> {31D09BA0-12F5-4CCE-BE8A-2923E76605DA} -> C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\OCHelper.dll [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
BHO-x32: McAfee WebAdvisor -> {B164E929-A1B6-4A06-B104-2CD0E90A88FF} -> C:\Program Files\McAfee\WebAdvisor\win32\IEPlugin.dll [2022-01-14] (McAfee, LLC -> McAfee, LLC)
Handler: mso-minsb-roaming.16 - {83C25742-A9F7-49FB-9138-434302C88D07} - C:\Program Files\Microsoft Office\root\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler-x32: mso-minsb-roaming.16 - {83C25742-A9F7-49FB-9138-434302C88D07} - C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler: mso-minsb.16 - {42089D2D-912D-4018-9087-2B87803E93FB} - C:\Program Files\Microsoft Office\root\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler-x32: mso-minsb.16 - {42089D2D-912D-4018-9087-2B87803E93FB} - C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler: osf-roaming.16 - {42089D2D-912D-4018-9087-2B87803E93FB} - C:\Program Files\Microsoft Office\root\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler-x32: osf-roaming.16 - {42089D2D-912D-4018-9087-2B87803E93FB} - C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler: osf.16 - {5504BE45-A83B-4808-900A-3A5C36E7F77A} - C:\Program Files\Microsoft Office\root\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Handler-x32: osf.16 - {5504BE45-A83B-4808-900A-3A5C36E7F77A} - C:\Program Files\Microsoft Office\root\VFS\ProgramFilesX86\Microsoft Office\Office16\MSOSB.DLL [2020-10-12] (Microsoft Corporation -> Microsoft Corporation)
Filter: application/x-mfe-ipt - {3EF5086B-5478-4598-A054-786C45D75692} - C:\Program Files\McAfee\MSC\McSnIePl64.dll [2021-12-11] (McAfee, LLC -> McAfee, LLC)
Filter-x32: application/x-mfe-ipt - {3EF5086B-5478-4598-A054-786C45D75692} - C:\Program Files (x86)\McAfee\MSC\McSnIePl.dll [2021-12-11] (McAfee, LLC -> McAfee, LLC)


==================== Hosts content: =========================


(If needed Hosts: directive could be included in the fixlist to reset Hosts.)


2019-12-07 03:14 - 2019-12-07 03:12 - 000000824 _____ C:\Windows\system32\drivers\etc\hosts


==================== Other Areas ===========================


(Currently there is no automatic fix for this section.)


HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\Control Panel\Desktop\\Wallpaper -> C:\Windows\web\wallpaper\Dell\Win LTBLUE 1920x1200.jpg
DNS Servers: 103.86.96.100 - 103.86.99.100
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System => (ConsentPromptBehaviorAdmin: 5) (ConsentPromptBehaviorUser: 3) (EnableLUA: 1)
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer => (SmartScreenEnabled: )
Windows Firewall is enabled.


Network Binding:
=============
Ethernet: NordVPN LightWeight Firewall -> NordLwf (enabled) 
Ethernet 2: NordVPN LightWeight Firewall -> NordLwf (enabled) 


==================== MSCONFIG/TASK MANAGER disabled items ==


(If an entry is included in the fixlist, it will be removed.)


HKLM\...\StartupApproved\Run: => "WavesSvc"
HKLM\...\StartupApproved\Run: => "RtkAudUService"
HKU\S-1-5-21-3883862340-2037335681-1545001466-1001\...\StartupApproved\Run: => "OneDrive"


==================== FirewallRules (Whitelisted) ================


(If an entry is included in the fixlist, it will be removed from the registry. The file will not be moved unless listed separately.)


FirewallRules: [{0EF674A8-4284-4A89-A19B-C664053841AD}] => (Allow) C:\Program Files\Microsoft Office\root\Office16\outlook.exe (Microsoft Corporation -> Microsoft Corporation)
FirewallRules: [{A34FCD76-7C2F-4205-B2F2-7C9FC11C2155}] => (Allow) C:\Program Files (x86)\Common Files\McAfee\MMSSHost\MMSSHost.exe (McAfee, LLC -> McAfee, LLC)
FirewallRules: [{EBCB52E0-98F0-4681-BB75-043B583ED4FF}] => (Allow) C:\Program Files\Common Files\McAfee\MMSSHost\MMSSHost.exe (McAfee, LLC -> McAfee, LLC)
FirewallRules: [{F7B56FDC-1539-4207-97DB-E8F56328F3DA}] => (Allow) C:\Program Files\Common Files\McAfee\Platform\McSvcHost\McSvHost.exe (McAfee, LLC. -> McAfee, LLC.)
FirewallRules: [{C91D0076-E389-4A1F-B984-7270B0A33242}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{CEE7B2A3-B6FF-48DF-B639-90B190F939BB}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{0FD5EDBA-66D0-438A-A2AF-4F1751AA2C3F}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{18493320-7746-48A5-AFC9-119DB8B9FD47}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{219997BC-DEE3-4D2E-B9DA-16407097AA9D}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{701A36E0-0797-4A0F-9AA0-F36749B8BB80}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{92E03EF0-4D64-4D82-A199-64E3A2F7FDC7}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{1FA982FC-0A1E-4E21-B82A-1703F07ED8D7}] => (Allow) C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.176.447.0_x86__zpdnekdrzrea0\Spotify.exe (Spotify AB -> Spotify Ltd)
FirewallRules: [{33CDDE71-1DEF-4D3B-9257-A48EC1CF6E33}] => (Allow) C:\Program Files\Google\Chrome\Application\chrome.exe (Google LLC -> Google LLC)
FirewallRules: [{4C47C0E9-993D-4728-9A32-FE661CE6205C}] => (Allow) C:\Program Files\WindowsApps\ScreenovateTechnologies.DellMobileConnect_3.3.9809.0_x64__0vhbc3ng4wbp0\app\DellMobileConnectClient.exe (SCREENOVATE TECHNOLOGIES LTD. -> Screenovate Technologies Ltd.) [File not signed]
FirewallRules: [{B591B6D7-956F-49D1-8568-7349C1FDDF24}] => (Allow) C:\Program Files\WindowsApps\ScreenovateTechnologies.DellMobileConnect_3.3.9809.0_x64__0vhbc3ng4wbp0\app\DellMobileConnectClient.exe (SCREENOVATE TECHNOLOGIES LTD. -> Screenovate Technologies Ltd.) [File not signed]


==================== Restore Points =========================


14-01-2022 17:30:30 Dell SupportAssist OS Recovery Plugin for Dell Update
15-01-2022 18:43:25 Dell Client Management Service
15-01-2022 18:44:16 Dell Client Management Service


==================== Faulty Device Manager Devices ============




==================== Event log errors: ========================


Application errors:
==================
Error: (01/15/2022 05:50:05 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/15/2022 05:50:04 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/15/2022 05:50:03 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/15/2022 05:50:02 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/15/2022 05:50:01 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/15/2022 05:50:00 PM) (Source: SecurityCenter) (EventID: 16) (User: )
Description: Error while updating  status to SECURITY_PRODUCT_STATE_ON.


Error: (01/14/2022 07:59:26 PM) (Source: VSS) (EventID: 8194) (User: )
Description: Volume Shadow Copy Service error: Unexpected error querying for the IVssWriterCallback interface.  hr = 0x80070005, Access is denied.
.
This is often caused by incorrect security settings in either the writer or requestor process.




Operation:
   Gathering Writer Data


Context:
   Writer Class Id: {e8132975-6f93-4464-a53e-1050253ae220}
   Writer Name: System Writer
   Writer Instance ID: {88b2d21c-df81-4f79-a241-e669561c531c}


Error: (01/14/2022 07:58:20 PM) (Source: VSS) (EventID: 8194) (User: )
Description: Volume Shadow Copy Service error: Unexpected error querying for the IVssWriterCallback interface.  hr = 0x80070005, Access is denied.
.
This is often caused by incorrect security settings in either the writer or requestor process.




Operation:
   Gathering Writer Data


Context:
   Writer Class Id: {e8132975-6f93-4464-a53e-1050253ae220}
   Writer Name: System Writer
   Writer Instance ID: {88b2d21c-df81-4f79-a241-e669561c531c}




System errors:
=============
Error: (01/16/2022 04:37:05 AM) (Source: Service Control Manager) (EventID: 7031) (User: )
Description: The AppX Deployment Service (AppXSVC) service terminated unexpectedly.  It has done this 1 time(s).  The following corrective action will be taken in 120000 milliseconds: Restart the service.


Error: (01/16/2022 04:35:47 AM) (Source: Service Control Manager) (EventID: 7034) (User: )
Description: The Rivet AP Selector Service service terminated unexpectedly.  It has done this 1 time(s).


Error: (01/15/2022 06:43:36 PM) (Source: Service Control Manager) (EventID: 7034) (User: )
Description: The Rivet AP Selector Service service terminated unexpectedly.  It has done this 1 time(s).


Error: (01/14/2022 10:29:32 PM) (Source: Service Control Manager) (EventID: 7000) (User: )
Description: The VMSP service failed to start due to the following error: 
Insufficient system resources exist to complete the requested service.


Error: (01/14/2022 10:29:12 PM) (Source: DCOM) (EventID: 10005) (User: NT AUTHORITY)
Description: DCOM got error "1115" attempting to start the service wuauserv with arguments "Unavailable" in order to run the server:
{E60687F7-01A1-40AA-86AC-DB1CBF673334}


Error: (01/14/2022 10:29:12 PM) (Source: DCOM) (EventID: 10005) (User: NT AUTHORITY)
Description: DCOM got error "1115" attempting to start the service wuauserv with arguments "Unavailable" in order to run the server:
{E60687F7-01A1-40AA-86AC-DB1CBF673334}


Error: (01/14/2022 10:11:35 PM) (Source: VDS Basic Provider) (EventID: 5) (User: )
Description: Cannot zero sectors on disk \\?\PhysicalDrive1. Error code: 5@0101000F


Error: (01/14/2022 09:36:27 PM) (Source: VDS Basic Provider) (EventID: 5) (User: )
Description: Cannot zero sectors on disk \\?\PhysicalDrive1. Error code: 1B1@0101000F




CodeIntegrity:
===============
Date: 2022-01-15 17:53:11
Description: 
Code Integrity determined that a process (\Device\HarddiskVolume3\Program Files\Common Files\McAfee\ModuleCore\ProtectedModuleHost.exe) attempted to load \Device\HarddiskVolume3\Program Files\McAfee.com\Agent\WSCLLCGlobalSign.exe that did not meet the Custom 3 / Antimalware signing level requirements.


Date: 2022-01-15 17:53:11
Description: 
Code Integrity determined that a process (\Device\HarddiskVolume3\Program Files\Common Files\McAfee\ModuleCore\ProtectedModuleHost.exe) attempted to load \Device\HarddiskVolume3\Program Files\Common Files\McAfee\Platform\Core\vtploader.dll that did not meet the Custom 3 / Antimalware signing level requirements.


Date: 2022-01-15 17:53:11
Description: 
Code Integrity determined that a process (\Device\HarddiskVolume3\Windows\System32\svchost.exe) attempted to load \Device\HarddiskVolume3\Program Files\McAfee\MfeAV\AMSIExt.dll that did not meet the Windows signing level requirements.




==================== Memory info =========================== 


BIOS: Dell Inc. 1.5.1 08/20/2021
Motherboard: Dell Inc. 05GD68
Processor: Intel(R) Core(TM) i3-10100 CPU @ 3.60GHz
Percentage of memory in use: 88%
Total physical RAM: 7939.7 MB
Available physical RAM: 877.98 MB
Total Virtual: 17445.65 MB
Available Virtual: 3180.59 MB


==================== Drives ================================


Drive c: (OS) (Fixed) (Total:220.15 GB) (Free:155.68 GB) NTFS


\\?\Volume{c1c04e18-3f27-423a-a673-f6438e28fbe2}\ (WINRETOOLS) (Fixed) (Total:0.97 GB) (Free:0.48 GB) NTFS
\\?\Volume{dc09e84e-b306-4db4-a4a3-892eb7424655}\ (Image) (Fixed) (Total:15.74 GB) (Free:0.14 GB) NTFS
\\?\Volume{d5ff3066-be6c-4dd7-9c7a-d7ac281de88d}\ (DELLSUPPORT) (Fixed) (Total:1.33 GB) (Free:0.48 GB) NTFS
\\?\Volume{f1aa288b-2592-4d1d-86a9-88c09545a8ee}\ (ESP) (Fixed) (Total:0.14 GB) (Free:0.08 GB) FAT32


==================== MBR & Partition Table ====================


==========================================================
Disk: 0 (Size: 238.5 GB) (Disk ID: AEAF30DB)


Partition: GPT.


==================== End of Addition.txt =======================
```

---

### Post by TheFu on 2022-01-16
Please don't post images of text. Copy/paste them when posting here.  500 bytes of text is better than 10 KB images.

If you care about security, maybe don't run Windows and allow it to connect to the internet.  Just a though.  They are the biggest target for malware, so why tempt the bad guys?

Use both an external firewall and an on-host firewall. Block all inbound and all outbound traffic, then open the outbound for only the needs you have.  This isn't any guarantee, since more and more bad-guy traffic hides inside HTTPS protocol requests.  Maybe use a pi-hole or some other DNS filter to block lookups to bad locations on the internet?  My little list of bad locations is almost 400K locations.

Ok, going back to the first image at the top of this thread.  There is nothing odd in there.  It is clear this isn't a real install of Linux. It appears to be running inside a container, so anything it sees will only be stuff that the hostOS allows it to see. That will be lies or, at best, fake devices.
Linux uses pseudo-file systems as a way to provide an interface into the OS settings and to provide a view of what the OS is doing.  In Unix/Linux everything is either a file or a process.  Those are the only 2 choices. Ain't nothing else.  So ... a process is something that is actively running or in the process table.  It has a real-userid, effective user-id and effective groupid. It accesses files for everything. Input/output of every sort.  Files are files. Directories are files. Devices are files. Network ports are files.  Keyboard, mice, monitor, speakers, microphones, joysticks, printers, scanners, disks, partitions, USB ports, USB devices ... _**everything that isn't a process ... is "a file."**_  
To see how much RAM we have in a system, look at /proc/meminfo. That's a "file" full of what the running OS knows about the RAM in the system.  There's a /proc/cpuinfo "file" too.  They are constantly modified as the situation on the system changes.  So see the changes every 2 seconds, run:
```
$ watch cat  /proc/meminfo
```
The cpuinfo file won't change as often, but if the CPU speed changes, it will show up in there.  There are lots of other files like this.  /sys/ is where we can modify settings - perhaps reduce or increase the network buffer size?  Usually, users don't interace directly with these locations and they are setup so that only root:root can modify them.  The programs that allow changing system-wide configurations are allowed to modify those values.  

If you have issues with Windows, might be best to ask on Windows specific forums.

BTW, fdisk and cfdisk commands work when used with the correct options and are run with root privilege. Using them improperly can destroy a system. Beware.

If you are looking for a trojan or rootkit on a running system, you'll never see it. Those programs usually replace the system calls other programs use to find symptoms or files left over.  You'll need to boot from a different OS to perform the scanning to avoid the hidden files.

---

