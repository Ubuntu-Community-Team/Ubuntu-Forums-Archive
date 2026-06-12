---
title: "Problems with running BADA OS Emulator"
date: 2010-05-22
forum: Wine
---

### Post by _BPS_ on 2010-05-22
Hi

i would like to write application for BADA operating system (its os for samsung mobile phones). I've downloaded SDK, IDE works perfectly fine (its only eclipse :) ) but i have problem with "Bada Simulator" - mobile phone emulator for testing apps.

to run Bada Simulator i type:
```

env WINEPREFIX="/home/bps/.wine" wine "C:\bada\1.0.0b2\Model\Wave\Simulator\Simulator.exe" -s c:\bada\1.0.0b2\Model\Wave\Simulator\PhoneShell.dll -d Generic.dbi

```and that gives me this output
```

...
MANY MORE SIMILAR LINES
....
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library ShpCommProtocol.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpDrm.dll") not found
err:module:import_dll Library ShpDrm.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpGWESME.dll") not found
err:module:import_dll Library ShpGWESME.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpGWESWinSet.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\wpcap.dll") not found
err:module:import_dll Library wpcap.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library ShpCommProtocol.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpAVMS.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\wpcap.dll") not found
err:module:import_dll Library wpcap.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library ShpCommProtocol.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpDrm.dll") not found
err:module:import_dll Library ShpDrm.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpAVMS.dll") not found
err:module:import_dll Library ShpAVMS.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpAppFrmwk.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\wpcap.dll") not found
err:module:import_dll Library wpcap.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library ShpCommProtocol.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpDrm.dll") not found
err:module:import_dll Library ShpDrm.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpAppFrmwk.dll") not found
err:module:import_dll Library ShpAppFrmwk.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpSettingSvc.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\wpcap.dll") not found
err:module:import_dll Library wpcap.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\NPPTools.dll") not found
err:module:import_dll Library NPPTools.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\WanPacket.dll") not found
err:module:import_dll Library WanPacket.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\packet.dll") not found
err:module:import_dll Library packet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpCommProtocol.dll") not found
err:module:import_dll Library ShpCommProtocol.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpSettingSvc.dll") not found
err:module:import_dll Library ShpSettingSvc.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\ShpGWESWinSet.dll") not found
err:module:import_dll Library ShpGWESWinSet.dll (which is needed by L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\Simulator.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\bada\\1.0.0b2\\Model\\Wave\\Simulator\\Simulator.exe" failed, status c0000135

```whats going on, why wine can't find those dlls?

All libraries from this list are in same directory with executable file, so they are not missing, this must be configuration problem :rolleyes:

---

### Post by cogadh on 2010-05-22
Change directories to the app's install directory before running it from the terminal, that will sometimes make it "see" the local DLL files.

---

### Post by _BPS_ on 2010-05-22
> **cogadh said:**
> Change directories to the app's install directory before running it from the terminal, that will sometimes make it "see" the local DLL files.


i've tried already

```

cd /home/bps/.wine/drive_c/bada/1.0.0b2/Model/Wave/Simulator
env WINEPREFIX="/home/bps/.wine" wine "C:\bada\1.0.0b2\Model\Wave\Simulator\Simulator.exe" -s c:\bada\1.0.0b2\Model\Wave\Simulator\PhoneShell.dll -d Generic.dbi

```

and

```

cd /home/bps/.wine/drive_c/bada/1.0.0b2/Model/Wave/Simulator
wine ./Simulator.exe

```

it gives same errors :(

---

### Post by cogadh on 2010-05-22
Just curious, why did you add the "./" in front of the executable name? That really shouldn't be necessary.

---

### Post by _BPS_ on 2010-05-23
> **cogadh said:**
> Just curious, why did you add the "./" in front of the executable name? That really shouldn't be necessary.

its just my habit 

```

cd /home/bps/.wine/drive_c/bada/1.0.0b2/Model/Wave/Simulator
wine Simulator.exe

```

changes nothing :(

---

### Post by _BPS_ on 2010-05-23
I found solution :KS

it was simple dependency hell, i was missing MFC42u.dll 

:guitar:

---

### Post by moljac024 on 2011-02-21
And the sdk works fine?
The sdk was one of the reasons why I finally took the plunge and infested my laptop with windows ](*,)

---

