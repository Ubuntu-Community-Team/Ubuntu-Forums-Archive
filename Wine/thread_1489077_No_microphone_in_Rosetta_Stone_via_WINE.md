---
title: "No microphone in Rosetta Stone via WINE"
date: 2010-05-20
forum: Wine
---

### Post by tango_ninja on 2010-05-20
Any WINE experts out there?

I can't seem to get my microphone to work with Rosetta Stone v3 via WINE.  This is an onboard mic on my Dell Vostro 1000 laptop... no bluetooth, no usb, just using the mic jack.  Both speakers and microphone work fine in ubuntu applications.

Here's the weird part: the mic works fine in WINE in [GoldWave]("http://www.goldwave.com/").  Goldwave is an audio editor that allows me to record from my mic.  Just tested it and I can record and hear my voice no problem!

See attached screenshot0 for error I get in Rosetta Stone. 

I know that this is a common problem so here's what I've tried so far:

**1 - **Setting the WINE audio configuration to ALSA drivers (using 'default' like Goldwave).  See atached screenshot-1

**2 - **Manually creating an .asoundrc file [using these instructions]("http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19342002.html").  When I do this, substituting my audio device and card positions I get no speaker and no mic.  Commenting out the code makes the speaker work again but leaves the mic inoperable.

**3 - **Using killall pulseaudio.  This seems to be a popular method but it didn't work for me. The idea is to run: 
[LIST]
[*]killall pulseaudio
[*]aoss wine program.exe
[/LIST]
But I can't launch RosettaStone via the terminal that way. I get the following errors
```
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
wine: cannot find L"C:\\windows\\system32\\taskkill.exe"
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x27e3260 (nil)
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:wbemprox:wbem_locator_ConnectServer 0x14d9e0, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x90ce9a4)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:wbemprox:wbem_locator_ConnectServer 0x14d9f8, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x93ce974)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10

```

And lastly, a visual check on Rosetta Stone reveals a blank mic pulldown menu.  See last attached screenshot.

Any advice?

---

### Post by SlidingHorn on 2010-05-20
From what I can see, this tends to be a pretty common issue with Rosetta Stone.  I was only able to find one person who claimed to have it fixed (but I only looked for a couple minutes).  

Take a look here & see if it helps: [http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19365868.html]("http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19365868.html")

---

### Post by tango_ninja on 2010-05-20
> **SlidingHorn said:**
> From what I can see, this tends to be a pretty common issue with Rosetta Stone.  I was only able to find one person who claimed to have it fixed (but I only looked for a couple minutes).  

Take a look here & see if it helps: [http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19365868.html]("http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19365868.html")

hey - thanks for the link but that was step #2 in my tested fixes :-)

Forgot also to mention that I tried this with WINE 1.1.42 and just now after upgrading to v1.1.44 without luck.

---

### Post by TPWT on 2010-05-21
Yep same problem, but different symptoms:

I get the same 'No mic found'.

But when I check my ALSA driver I don't get the options that tango_ninja gets (see screenshot)

I tried the .asoundrc route, but I can't see if anything changed (see above).

And killall pulseaudio does nothing.

I also tried caltering the gain manually (as per [http://ubuntuforums.org/showthread.php?t=1250674](http://ubuntuforums.org/showthread.php?t=1250674)), but either I'm unlucky or he fluked it.


Just as a Check I tried running the Windows Version of Audacity and it worked fine. It seems to be specific to how Rosetta handles the audio

---

### Post by tango_ninja on 2010-05-21
TWPT, what version of wine are you using?  My screenshot is from 1.1.42 but those options disappeared once i upgraded to 1.1.44

Also, did your killall pulse audio test produce terminal errors like mine? Or did rosetta stone launch fine as per normal (no mic)?

---

### Post by philinux on 2010-05-21
Thread moved to Wine forum.

---

### Post by TPWT on 2010-05-21
Wine 1.0.0-0ubuntu4 (part of wine1.2-geko)

rosetta stone 3.2.11

killall Puleaudio gives no errors, but gives no mic either

:(


Upgraded wine to 1.1.44

Then got a Rosetta stone FATAL APPLICATION ERROR #2120 with the terminal displaying:

```

robert@robEEE:~$ killall pulseaudio
robert@robEEE:~$ aoss wine '/home/robert/.wine/drive_c/Program Files/Rosetta Stone/Rosetta Stone V3/RosettaStoneVersion3.exe' 
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x8f76218 (nil)


```


If I don't try the aoss wine.... trick, it logs in, but alas no alsa

---

### Post by TPWT on 2010-05-29
Fixed the problem

Installed VirtualBox
Ran Rosetta stone inside an XP virtual machine
Used external mic with Puleaudio emulated to an intel audio driver

If the microphone seems to lag- check the gain isn't too high/ You can change this in Ubuntu under the volume settings..

Hope wine sorts this problem out, while it works, running a VM fr one piece of software is a hassle. and wine would give a more practical solution!

---

### Post by lindude on 2010-05-31
I have a similar problem no mic input, either through the internal or usb mic's.
Both the mic's work with Skype and you can see them registering in the sounds settings.

Rosetta Stone sees that there are mic's there if I choose OSS Driver as my audio driver in the Wine settings, (see the first attached pic), but it still doesn't work. This was the same with Wine and Winepulse.
I can see both of the mic's in the wine settings under PluseAudio Driver but they don't show up in the Rosetta Stone settings.


So far I've tried these steps,(latest first), using Wine 1.142 and Winepulse, Rosetta Stone Version 3.3.5 and 3.4.5;

Upgraded Alsa to 1.0.23

Installed winepulse

Manually creating an .asoundrc file using these [instructions]("http://old.nabble.com/Re:-Rosetta-Stone-Microphone-Detection-p19342002.html"). 

Using killall pulseaudio. 

    * killall pulseaudio
    * aoss wine program.exe

beefcake@beefcake:~$ killall pulseaudio
beefcake@beefcake:~$ aoss wine program.exe
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
wine: cannot find L"C:\\windows\\system32\\program.exe"
beefcake@beefcake:~$

I'm using a Dell XPS M1210
Ubuntu 10.04 (64 bit) fresh install.

Any help would be greatly appreciated.
Thanks

---

### Post by zaphod777 on 2010-08-19
Has anyone found a solution for this yet? While I don't really need the mic input it would be nice.

---

### Post by whochismo on 2011-03-15
I'm having the same problem. I use firefox 3.6.15 in wine 1.3 and the microphone is not listed in the microphone selection screen in rosetta stone (the online version).

Has there been any progress regarding this issue?

---

### Post by tango_ninja on 2011-03-15
I gave up, installed WinXP via Oracle virtualbox 4.0 and ran Rosetta Stone there.  Works fine with ASLA audio.

---

### Post by allCuExpMa on 2012-01-05
Had the same problem. Ubuntu 11.10-64 - Rosetta Stone 3.4.7 - Wine 1.3.36.... no micro detected... search the whole flippin Internet for a solution, found one which works for me... I downgraded Wine to 1.2.3 now it works like a sharm....hope it helps someone here......... T[m]

---

### Post by tekkisan on 2012-03-03
I tried Wine 1.2.3 with Rosetta Stone 3.4.5. with Ubuntu 11.10. I could load RS, the language levels and make a user, but that was as far as I got. The RS hung. I tried a few times, each time deleting the .wine directory as RS would not properly uninstall. So I am back to Wine 1.3.28 with no microphone.

---

### Post by wilsonB on 2012-04-01
Using Wine 1.4 and Rosetta Stone Ver. 3

Still not able to get microphone detected in Rosetta... 


Using a VM or downgrading Wine doesn't make sense. This should be able to be worked out...

ANYONE?

---

### Post by chmegr on 2012-05-06
Sigh....same problem, and I have not found a solution. I am using RS v3.2.11a and Wine 1.4. Everything works....except the microphone. The program simply will not recognize it, even though the system will.....:(

---

### Post by whochismo on 2012-05-10
I just upgraded wine to 1.5 using this repository in ubuntu 12.04:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

And now it recognises the microphone and works flawlessly. I hope it helps.

PS: btw, I'm using Rosetta Stone 3.4.7

---

### Post by Docmero on 2012-05-12
I have the same problem but I'm afraid of installing wine 1.55 which is still a developmental version . I guess I have to wait for the next stable release :(

---

### Post by vedovatti on 2012-05-28
I just installed through PPA wine 1.55 not luck. No microphone detected. I am using vmware.

---

### Post by epimachos on 2012-05-31
I just upgraded wine to version 1.5.5 and now everything works perfectly. 
At first nothing worked but after a couple of restarts, all work! 

Ubuntu 12.04 + Rosetta Stone 3.4.5

\\:D/

---

### Post by MMagoo1 on 2012-07-01
Best Solution is here: [http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only)

Just change Wine to Alsa and everything works fine.

---

### Post by electricmaster on 2012-08-15
Hi everyone.
So I've gotten my microphone to detect in Rosetta Stone, but the mic still won't work. It can't hear my voice at all, but it works just fine in the Gnome sound recorder. Anyone know what the cause may be?

Wine 1.5.10
Ubuntu 12.04
Rosetta Stone 3.4.5
Acer Aspire One with integrated webcam/mic
I do have the audio driver set to ALSA at MMagoo1's suggestion, which is how I can see my mic to begin with.

I've already tried killall pulseaudio, but it didn't really change anything.
If I run it from ALSA, I get a fatal 2173 error in Rosetta Stone and this output from the terminal:
```
**maclm01@maclm01-AO532h:~$** killall pulseaudio
**maclm01@maclm01-AO532h:~$** aoss wine '/home/maclm01/.wine/dosdevices/c:/Program Files/Rosetta Stone/Rosetta Stone Version 3/RosettaStoneVersion3.exe' 
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x548024
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:win:EnumDisplayDevicesW ((null),0,0x32f70c,0x00000000), stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x2fe46b0 (nil)
fixme:file:K32EnumDeviceDrivers ((nil), 0, 0x32c2c4): stub
fixme:file:K32EnumDeviceDrivers (0xaa4fd38, 0, 0x32c2c4): stub
fixme:file:K32EnumDeviceDrivers ((nil), 0, 0x32c068): stub
fixme:file:K32EnumDeviceDrivers (0xaa4fe48, 0, 0x32c068): stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 74080 (device=7 access=1 func=20 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4100c (device=4 access=0 func=403 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 41018 (device=4 access=0 func=406 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c10 (device=2d access=0 func=304 method=0)
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0x7bbc1c00, 0x1de2d0, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7bbc1c00
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:client_security_SetBlanket 0x7bbc1c00, 0x1dd670, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7bbc1c00
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030

```Any ideas would be great, thanks :)

---

### Post by caka on 2012-08-20
Hi electricmaster,

I've same configuration with you and I've solved this problem about a couple of minutes ago. (After several fails with the methods in here) What I have done is

1) Click on sound applet on the right up corner> sound settings>input>Settings for microphone
Be sure that the bar is away from "Unamplified"
2) Alt+F2>winetricks>select the default prefix> Change Settings > tick the box "sound=alsa" > OK > OK

With this way Ubuntu will continue to use pulseaudio but wine will use alsa. You don't need to kill or remove any of them.

I hope it works for you.

---

### Post by electricmaster on 2012-08-20
Thanks so much for the reply!

I took the steps you mentioned: switched Wine to ALSA, put my microphone away from Unamplified (set on 100%), and started Rosetta Stone without killing pulseaudio, but it still didn't detect my voice :/ Any ideas?

---

### Post by carranty on 2012-09-15
> **whochismo said:**
> I just upgraded wine to 1.5 using this repository in ubuntu 12.04:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

And now it recognises the microphone and works flawlessly. I hope it helps.

PS: btw, I'm using Rosetta Stone 3.4.7

I can also confirm wine 1.5 + Rosetta Stone 3.4.7 + Ubuntu 12.04 works great.


I also used MMagoo1's link, not sure if that contributed or not........

---

### Post by electricmaster on 2012-09-15
> **carranty said:**
> I can also confirm wine 1.5 + Rosetta Stone 3.4.7 + Ubuntu 12.04 works great.


I also used MMagoo1's link, not sure if that contributed or not........

Still not working for me. WINE 1.5, Ubuntu 12.04, Rosetta Stone 3.4.5. You think it will work if I update to 3.4.7?

---

### Post by carranty on 2012-09-15
> **electricmaster said:**
> Still not working for me. WINE 1.5, Ubuntu 12.04, Rosetta Stone 3.4.5. You think it will work if I update to 3.4.7?

I guess it can't hurt.  I've only installed 12.04 3 days ago, so its still a pretty fresh install, I don't think I've installed any other packages that could be influencing it.   I'm using the 64 bit version of Ubuntu, I suppose that could make a difference.......

---

### Post by electricmaster on 2012-09-15
> **carranty said:**
> I guess it can't hurt.  I've only installed 12.04 3 days ago, so its still a pretty fresh install, I don't think I've installed any other packages that could be influencing it.   I'm using the 64 bit version of Ubuntu, I suppose that could make a difference.......

Yeah. I have 32 bit. I can't think of any packages that could influence it, really. I only installed the basics. I'll try updating it, maybe it's a 3.4.5 specific problem.

---

### Post by JoeDaddy on 2012-09-25
I have studied this issue for days, searched and tried lots of ideas.  The problem seems to be in Rosetta Stone-Wine because other apps in Wine pick up the microphone with no problem.  Nevertheless, I have found an ap that works.  It's called CrossOver by CodeWeavers.  It costs a few dollars but no more headaches!  I'd still like to have a solution before I buy.  I have a 14 day free trial and so far it works just fine.
Wish there was a way to FORCE the microphone on Rosetta Stone.  Something in the registry or a command line option??

---

### Post by ph1ash on 2013-03-05
This worked for me [http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only). Hope this helps!

---

### Post by CharlesA on 2013-03-06
Back to sleep you go...

---

