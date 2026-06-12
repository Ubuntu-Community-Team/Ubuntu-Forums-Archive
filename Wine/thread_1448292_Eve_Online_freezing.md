---
title: "Eve Online freezing"
date: 2010-04-06
forum: Wine
---

### Post by sprinj76 on 2010-04-06
Hi all, I've been working on this problem for more than a week now and can't seem to fix the problem. Eve is suppose to run well with wine, but I'm having all kinds of issues.

I'm relatively new to Linux so bare with me (maybe two weeks experience).

I'm running Ubuntu 9.10 x86
Nvidia drivers 185 installed through Administration>Hardware Drivers
hardware is typical except I'm running two 8800 GT's in SLI
AMD X2 5000, 4gb ddr2 ram, 160gb linux hdd, etc...

When I run eve it goes fine until I'm in the game roughly 10-15 seconds then it freezes. I ran the game through the terminal and these are the things which were displayed:

[email]jason@jason:~/.wine[/email]$ wine start "C:\Program Files\CCP\Eve\eve.exe"
fixme:exec:SHELL_execute flags ignored: 0x00000100
[email]jason@jason:~/.wine[/email]$ err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x7c9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20080 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x21da98,0x1053fb60): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20080, 0x145aa8): stub
fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #20:
fixme:d3d_shader:print_glsl_info_log     Vertex info
fixme:d3d_shader:print_glsl_info_log     -----------
fixme:d3d_shader:print_glsl_info_log     warning: no vertex attribute is explicitly assigned to vertex attribute zero
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:NotifyIME NI_CLOSECANDIDATE

After this it is completely frozen, no dialog boxes pop up and I have to kill the winesever to get eve to stop.

Can anyone give me some guidance?

---

### Post by sprinj76 on 2010-04-06
Well I did more reading. I guess this is a ubuntu specific problem with a potential fix.

I was refferenced this link [http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1226117&page=3#66](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1226117&page=3#66)

Which goes to another link, that I can't find any instructions on how to fix the problem, just what the problem is.

Can anyone help me decode what needs to be changed/fixed and how?

---

### Post by sprinj76 on 2010-04-06
Took some advice from my brother who said I should try turning off effects in the game until I find out what is not working correctly.

I turned off the audio, which let me play the game for 20-25 minutes before a wine window popped up telling me there was a serious error (that's a first). 

Some progress made at the very least.

---

### Post by sprinj76 on 2010-04-07
Well I've made some headway on my issues. The audio problem is apparently directly related to pulseaudio. I will be switching to OSS: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

As a side note for anyone that may find this in the future. The launching problem with Eve online in Ubuntu 9.10 is related to NEW_FAIR_SLEEPERS, which ubuntu has disabled by default. re-enabling this will launch Eve every time without having to modify the prefs.ini file. See this link for more details: [http://ubuntuforums.org/showpost.php?p=8050178&postcount=4](http://ubuntuforums.org/showpost.php?p=8050178&postcount=4)

---

### Post by sarasfox on 2010-06-06
i have the same issue it sounds like
** Sun Jun  6 10:32:22 2010
Starting '/opt/cxgames/bin/wineloader' 'winewrapper.exe' '--start' '--'
'/home/kevin/.cxgames/EVE' 'Online/dosdevices/c:/Program' 'Files/CCP/EVE/eve.exe'

fixme:exec:SHELL_execute flags ignored: 0x00000100
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x6a7000 0 0x33fc90 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338fa4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x2007c 0x00000000
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x857ddf8,0x857e378): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x2007c, 0x168420): stub
fixme:reg:GetNativeSystemInfo (0x33b7d0) using GetSystemInfo()
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ntdll:RtlpWaitForCriticalSection section 0x7e6066c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0030, blocked by 001c, retrying (60 sec)
wine: Critical section 7e6066c0 wait failed at address 0x7bc3314b (thread 0030), starting debugger...

[http://www.system76.com/product_info.php?cPath=28&products_id=101](http://www.system76.com/product_info.php?cPath=28&products_id=101) with 4 gigs of ram

---

