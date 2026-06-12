---
title: "Internet explorer doesn't display properly."
date: 2009-02-11
forum: Wine
---

### Post by AllRadioisDead on 2009-02-11
Hi, I've installed IE via winetricks, (Tried 6, 7 as well with playonlinux)but I only get a blank box titled [Wine Internet Explorer] with no GUI functions, or home page. How can I fix this?

---

### Post by rocky5051 on 2009-02-11
Assuming ies4linux hasn't changed in functionality since the last time I used it, try the link it makes on your desktop again. If that doesn't work, open up Winecfg like this:

```
winecfg
```

Then go to the overrides section and add iexplore.exe to the list and set it to "native".

I believe the problem is that Wine's implementation of IE overrides the execution of the actual IE in case it's installed.

Really though, unless you need it for web developing purposes it's a pretty big waste of time. It's not really all that stable or functional. Not even with CrossOver.

Hope that helps.

---

### Post by AllRadioisDead on 2009-02-11
> **rocky5051 said:**
> Assuming ies4linux hasn't changed in functionality since the last time I used it, try the link it makes on your desktop again. If that doesn't work, open up Winecfg like this:

```
winecfg
```Then go to the overrides section and add iexplore.exe to the list and set it to "native".

I believe the problem is that Wine's implementation of IE overrides the execution of the actual IE in case it's installed.

Really though, unless you need it for web developing purposes it's a pretty big waste of time. It's not really all that stable or functional. Not even with CrossOver.

Hope that helps.
That's set already.

---

### Post by rocky5051 on 2009-02-12
Try this command:

```
WINEPREFIX="$HOME/.ies4linux" wine iexplore.exe
```

I believe that's the wineprefix that ies4linux sets.

Can't think of anything else to get it going since I never encountered that problem with ies before.

---

### Post by AllRadioisDead on 2009-02-12
Alright, thanks that seemed to get us somewhere.
It opened up a window and complained about not having gecko, so it downloaded that for me and shot all this out:
```
wine: created the configuration directory '/home/james/.ies4linux'
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/james/.ies4linux' has been updated.
fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:urlmon:ObtainUserAgentString (0, 0x7df52507, 0x7df52500): stub
fixme:urlmon:ObtainUserAgentString (0, 0x155000, 0x7df52500): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cc739f8, overlapped 0x7cc739dc): stub
fixme:msimtf:ActiveIMMApp_Activate Stub
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 24 0 32eb98)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 81 0 32ea34)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 83 0 32ee5c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 1 0 32ea34)
fixme:msimtf:ActiveIMMApp_FilterClientWindows Stub
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 81 0 32f124)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 83 0 32f0d4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 1 0 32f124)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 5 0 640064)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 3 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 1f 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 a 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 81 0 32ecf4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 83 0 32eca4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 1 0 32ecf4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 5 0 640064)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 3 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 210 1 20032)
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14d0bc)->((null) 1 0x32f19c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 25 2 0x32f1b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 26 2 0x32f1b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14d0bc)->(0x32f1ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32f2c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f350)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 81 0 32e368)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 83 0 32e318)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 1 0 32e368)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 5 0 640064)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 3 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 210 1 10040)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 81 0 32e884)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 0 32e834)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 1 0 32e884)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 3 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 210 1 10042)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32e8b8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32e918)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 22 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32e918)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32ea6c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 1 32e988)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32ea6c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 640054)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 80 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 80 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 210 2 20032)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20032 82 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32ea70)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 22 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 47 0 32ea70)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14d0bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32fbb8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32fbb8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 26 2 0x32fc80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 29 2 0x32fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 28 2 0x32fbb8 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14d0bc)->(0x32fb2c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 46 0 32edd8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 83 1 32ecf4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 47 0 32edd8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 5 0 28d03b4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32eda4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 83 1 32ecc0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32f928)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 22 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 46 0 32f988)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 22 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 47 0 32f988)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 a 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 7 1002a 0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14d0bc)->(0xb7ea8d31)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 26 2 0x32fa60 (nil))
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32f5c4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 1 32f4e0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32f5c4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 28d03a4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14d0bc)->((null) 21 2 (nil) (nil))
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 10302e6)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 d102de)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 f902f4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 c702ec)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 f50300)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 c302f8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 ed0306)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 bb02fe)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 e50310)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 b30308)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 e40311)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 b20309)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 e30311)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 b10309)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 df0317)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 ad030f)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 d90319)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 a70311)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 d9031a)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 a70312)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 d10320)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 9f0318)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 c50324)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 93031c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 bb0326)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 89031e)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 ad032a)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 7b0322)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 a1032c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 6f0324)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 930332)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 61032a)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 870334)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 55032c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 790336)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 47032e)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 6b0338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 390330)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 5f033a)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 2d0332)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 510340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 1f0338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 490340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 170338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 460340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 140338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 380340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 380340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 60338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 350340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 20 10042 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 200 0 30338)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 84 0 350340)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 1c 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 8 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 46 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 83 1 32dc14)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 47 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 5 0 1c001c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32dcc4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 83 1 32dbe0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 1 32d1e4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 1c001c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 1c 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 46 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 83 1 32dc14)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 47 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 5 0 28d03b4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32dcc4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 83 1 32dbe0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 1 32d1e4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 28d03a4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 85 1 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20038 1c 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 46 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 83 1 32dc14)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 47 0 32dcf8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x20034 5 0 1c001c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 46 0 32dcc4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10040 83 1 32dbe0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 46 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 83 1 32d1e4)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 47 0 32d2c8)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10042 5 0 1c001c)



```

---

### Post by rocky5051 on 2009-02-12
```
wine: created the configuration directory '/home/james/.ies4linux'
```

I must have given you the wrong wineprefix in the command because if it were the ies wineprefix, wine would not have needed to create it.

EDIT: Yep...actually, this is what you should have run...

```
$HOME/bin/ie6
```

---

### Post by AllRadioisDead on 2009-02-12
Thanks for the help, I've reinstalled wine and it's working great!

---

