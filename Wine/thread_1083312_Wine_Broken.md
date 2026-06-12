---
title: "Wine Broken"
date: 2009-02-28
forum: Wine
---

### Post by unplugged23 on 2009-02-28
Hey there,

Whenever I install Wine and go to winecfg, i get the configuration window, but all of the words are gone. I've uninstalled and re-installed many times and the problem still persists. How should i fix this? I'll attach a screen shot.

[IMG]http://img10.imageshack.us/img10/2582/screenshotwineconfigura.png[/IMG]

---

### Post by albinootje on 2009-02-28
> **unplugged23 said:**
> I've uninstalled and re-installed many times and the problem still persists. 

Did you move/rename your ~/.wine/ directory ?
And can you post the output of the following :
```

dpkg -l|grep -i fonts

```

---

### Post by unplugged23 on 2009-02-28
I did not move or rename any wine files, and here is the output of hte code you gave me:

```
ii  console-terminus                           4.26-1                                  Fixed-width fonts for fast reading on the Linux console
ii  gsfonts                                    1:8.11+urwcyr1.0.7~pre43-2              Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                                0.20ubuntu1                             Make Ghostscript fonts available to X11
ii  ttf-arabeyes                               2.0-2                                   Arabeyes GPL TrueType Arabic fonts
ii  ttf-bengali-fonts                          1:0.5.4ubuntu2                          Free TrueType fonts for the Bengali language
ii  ttf-bitstream-vera                         1.10-7                                  The Bitstream Vera family of free TrueType fonts
ii  ttf-freefont                               20080323-3                              Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                       1:0.5.4ubuntu2                          Core collection of free Indian language fonts
ii  ttf-kannada-fonts                          1:0.5.4ubuntu2                          Free TrueType fonts for the Kannada language
ii  ttf-liberation                             1.04~beta2-2                            Free fonts with the same metrics as Times, Arial and Cou
ii  ttf-oriya-fonts                            1:0.5.4ubuntu2                          Free TrueType fonts for the Oriya language
ii  ttf-telugu-fonts                           1:0.5.4ubuntu2                          Free TrueType fonts for the Telugu language
ii  ttf-thai-tlwg                              1:0.4.10-2                              Thai fonts in TrueType format
ii  ttf-unfonts-core                           1.0.1-7ubuntu1                          Un series Korean TrueType fonts
ii  x-ttcidfont-conf                           29                                      TrueType and CID fonts configuration for X
ii  xfonts-100dpi                              1:1.0.0-4                               100 dpi fonts for X
ii  xfonts-75dpi                               1:1.0.0-4                               75 dpi fonts for X
ii  xfonts-base                                1:1.0.0-5                               standard fonts for X
ii  xfonts-encodings                           1:1.0.2-3                               Encodings for X.Org fonts
ii  xfonts-scalable                            1:1.0.0-6                               scalable fonts for X
ii  xfonts-utils                               1:7.4+1ubuntu1                          X Window System font utility programs

```

Thanks for the help! :P

---

### Post by albinootje on 2009-02-28
> **unplugged23 said:**
> I did not move or rename any wine files

Here's two different posts :
[http://www.winehq.org/pipermail/wine-users/2006-July/022985.html](http://www.winehq.org/pipermail/wine-users/2006-July/022985.html)
[http://www.usenet-forums.com/linux-general/98340-winecfg-lettering-missing-no-fonts.html](http://www.usenet-forums.com/linux-general/98340-winecfg-lettering-missing-no-fonts.html)
suggesting that installing the msttcorefonts package would help.
You have however the ttf-liberation package installed already.
But feel free to try this suggestion though.

---

### Post by unplugged23 on 2009-02-28
> **albinootje said:**
> Here's two different posts :
[http://www.winehq.org/pipermail/wine-users/2006-July/022985.html](http://www.winehq.org/pipermail/wine-users/2006-July/022985.html)
[http://www.usenet-forums.com/linux-general/98340-winecfg-lettering-missing-no-fonts.html](http://www.usenet-forums.com/linux-general/98340-winecfg-lettering-missing-no-fonts.html)
suggesting that installing the msttcorefonts package would help.
You have however the ttf-liberation package installed already.
But feel free to try this suggestion though.

I installed the msttcorefonts package (after tracking down the dependencies) then proceeded to un and re install wine. Unfortunately I'm still having the same problem. Thanks for the reply though!

---

### Post by unplugged23 on 2009-03-01
Bump :(

---

### Post by DREMA on 2009-03-02
Which version of wine are you using? And where did you get it?

You could try deleting the wine config folder.

```
rm -R ~/.wine
```

and then, running again the winecfg command and post the output here.

---

### Post by cogadh on 2009-03-03
If you have a GeForce 2 through 6 video card, then it is actually a problem with the legacy Nvidia drivers. It can be fixed by altering a reg entry in Wine:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17)

---

### Post by unplugged23 on 2009-03-03
> **cogadh said:**
> If you have a GeForce 2 through 6 video card, then it is actually a problem with the legacy Nvidia drivers. It can be fixed by altering a reg entry in Wine:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17)

I know I'm using an old nvidia card, however this did not work for me. There is a chance that my card might be older than that though... How should I check? And thanks a lot for the post! :D


> **DREMA said:**
> Which version of wine are you using? And where did you get it?

You could try deleting the wine config folder.

```
rm -R ~/.wine
```and then, running again the winecfg command and post the output here.

Well, I ran your command, then winecfg to no avail :( Here's the output

```
izzy@izzy:~$ rm -R ~/.wine
izzy@izzy:~$ winecfg
wine: created the configuration directory '/home/izzy/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ce489f8, overlapped 0x7ce489dc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/izzy/.wine' has been updated.
X connection to :0.0 broken (explicit kill or server shutdown).
izzy@izzy:~$ 

```
When it had finished it popped open a blank wine cfg window just like I've been dealing with all this time.
I'm assuming the last line "*X connection to :0.0 broken (explicit kill or server shutdown).*" has to do with me using force quit on the window, as it wasn't very responsive. Thanks a lot for the help! :D Any more ideas? :?:

---

### Post by cogadh on 2009-03-03
Are you certain you did the registry change correctly? By all rights, it shouldn't matter how old your Nvidia card is (as long as it is older than a GeForce 6) that reg change should have corrected the issue.

---

### Post by unplugged23 on 2009-03-03
> **cogadh said:**
> Are you certain you did the registry change correctly? By all rights, it shouldn't matter how old your Nvidia card is (as long as it is older than a GeForce 6) that reg change should have corrected the issue.

Ah, well my card is older than geforce six; let me try and walk you through what I did.

1. I typed [I][HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"[/I] and saved it as settings.txt in wine's virtual C drive. 

2. I ran ```
env WINEPREFIX="/home/izzy/.wine” regedit settings.txt
``` in terminal

3. And that's pretty much it.

Did I do something wrong (probably) or leave out a step?

---

### Post by cogadh on 2009-03-03
Nope, that should have worked. You can confirm that it did by just running regedit to check for the presence of the correct registry entry.

---

### Post by unplugged23 on 2009-03-03
Ermmm, The registry editor is blank as was WINE :(
[IMG]http://img9.imageshack.us/img9/1981/screenshotregistryedito.png[/IMG]

---

### Post by cogadh on 2009-03-03
](*,)
ROFLMAO! I'm an idiot, sorry about that. In that case, open the user.reg file (found in the .wine directory) with a text editor and check for it.

---

### Post by unplugged23 on 2009-03-03
Ok, in the WINE registry I'm assuming I'm looking for 
```
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N" and saved it as settings.tx
```
I don't see it, should I place it in the file manually? If so how? Ill paste the registry in a code wrap so it doesn't take up as much space :D

```
WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\Colors] 1236119746

[Control Panel\\Desktop] 1236119752
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

[Control Panel\\Desktop\\WindowMetrics] 1236119752
"BorderWidth"="1"
"CaptionHeight"="18"
"CaptionWidth"="18"
"MenuHeight"="18"
"MenuWidth"="18"
"ScrollHeight"="16"
"ScrollWidth"="16"
"Shell Icon Size"="32"
"SmCaptionHeight"="15"
"SmCaptionWidth"="13"

[Control Panel\\International] 1236119746
"iCalendarType"="1"
"iCountry"="1"
"iCurrDigits"="2"
"iCurrency"="0"
"iDate"="0"
"iDigits"="2"
"iFirstDayOfWeek"="6"
"iFirstWeekOfYear"="0"
"iLDate"="0"
"iLZero"="1"
"iMeasure"="1"
"iNegCurr"="0"
"iNegNumber"="1"
"iPaperSize"="1"
"iTime"="0"
"iTimePrefix"="0"
"iTLZero"="0"
"LC_CTYPE"="00000409"
"LC_MEASUREMENT"="00000409"
"LC_MONETARY"="00000409"
"LC_NUMERIC"="00000409"
"LC_PAPER"="00000409"
"LC_TELEPHONE"="00000409"
"LC_TIME"="00000409"
"Locale"="00000409"
"Numshape"="1"
"s1159"="AM"
"s2359"="PM"
"sCountry"="United States"
"sCurrency"="$"
"sDate"="/"
"sDecimal"="."
"sGrouping"="3;0"
"sLanguage"="English (United States)"
"sList"=","
"sLongDate"="dddd, MMMM dd, yyyy"
"sMonDecimalSep"="."
"sMonGrouping"="3;0"
"sMonThousandSep"=","
"sNativeDigits"="0123456789"
"sNegativeSign"="-"
"sPositiveSign"=""
"sShortDate"="M/d/yyyy"
"sThousand"=","
"sTime"=":"
"sTimeFormat"="h:mm:ss tt"
"sYearMonth"="MMMM, yyyy"

[Software\\Microsoft\\Internet Explorer\\Main] 1236119747
"Search Page"="http://www.google.com"
"Start Page"="http://www.winehq.org"

[Software\\Microsoft\\Protected Storage System Provider] 1236119752
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Shell Folders] 1236119746
"AppData"="C:\\windows\\profiles\\izzy\\Application Data"
"Cache"="C:\\windows\\profiles\\izzy\\Local Settings\\Temporary Internet Files"
"Cookies"="C:\\windows\\profiles\\izzy\\Cookies"
"Desktop"="C:\\windows\\profiles\\izzy\\Desktop"
"Favorites"="C:\\windows\\profiles\\izzy\\Favorites"
"Fonts"="C:\\windows\\Fonts"
"History"="C:\\windows\\profiles\\izzy\\Local Settings\\History"
"Local AppData"="C:\\windows\\profiles\\izzy\\Local Settings\\Application Data"
"My Music"="C:\\windows\\profiles\\izzy\\My Music"
"My Pictures"="C:\\windows\\profiles\\izzy\\My Pictures"
"My Videos"="C:\\windows\\profiles\\izzy\\My Videos"
"NetHood"="C:\\windows\\profiles\\izzy\\NetHood"
"Personal"="C:\\windows\\profiles\\izzy\\My Documents"
"PrintHood"="C:\\windows\\profiles\\izzy\\PrintHood"
"Programs"="C:\\windows\\profiles\\izzy\\Start Menu\\Programs"
"Recent"="C:\\windows\\profiles\\izzy\\Recent"
"SendTo"="C:\\windows\\profiles\\izzy\\SendTo"
"Start Menu"="C:\\windows\\profiles\\izzy\\Start Menu"
"StartUp"="C:\\windows\\profiles\\izzy\\Start Menu\\Programs\\StartUp"
"Templates"="C:\\windows\\profiles\\izzy\\Templates"

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\User Shell Folders] 1236119746
"AppData"=str(2):"%USERPROFILE%\\Application Data"
"Cache"=str(2):"%USERPROFILE%\\Local Settings\\Temporary Internet Files"
"Cookies"=str(2):"%USERPROFILE%\\Cookies"
"Desktop"=str(2):"%USERPROFILE%\\Desktop"
"Favorites"=str(2):"%USERPROFILE%\\Favorites"
"Fonts"=str(2):"C:\\windows\\Fonts"
"History"=str(2):"%USERPROFILE%\\Local Settings\\History"
"Local AppData"=str(2):"%USERPROFILE%\\Local Settings\\Application Data"
"My Music"=str(2):"%USERPROFILE%\\My Music"
"My Pictures"=str(2):"%USERPROFILE%\\My Pictures"
"My Videos"=str(2):"%USERPROFILE%\\My Videos"
"NetHood"=str(2):"%USERPROFILE%\\NetHood"
"Personal"=str(2):"%USERPROFILE%\\My Documents"
"PrintHood"=str(2):"%USERPROFILE%\\PrintHood"
"Programs"=str(2):"%USERPROFILE%\\Start Menu\\Programs"
"Recent"=str(2):"%USERPROFILE%\\Recent"
"SendTo"=str(2):"%USERPROFILE%\\SendTo"
"Start Menu"=str(2):"%USERPROFILE%\\Start Menu"
"StartUp"=str(2):"%USERPROFILE%\\Start Menu\\Programs\\StartUp"
"Templates"=str(2):"%USERPROFILE%\\Templates"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings] 1236119752
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap] 1236119752
@=""
"IntranetName"=dword:00000001
"ProxyByPass"=dword:00000001
"UNCAsIntranet"=dword:00000001

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\Domains] 1236119752
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\ProtocolDefaults] 1236119752
@=""
"@ivt"=dword:00000001
"file"=dword:00000003
"ftp"=dword:00000003
"http"=dword:00000003
"https"=dword:00000003

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\Ranges] 1236119752
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones] 1236119752
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\0] 1236119752
@=""
"1001"=dword:00000000
"1004"=dword:00000000
"1200"=dword:00000000
"1201"=dword:00000001
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000000
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000000
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000000
"1805"=dword:00000000
"1A00"=dword:00000000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00020000
"1E05"=dword:00030000
"CurrentLevel"=dword:00000000
"Description"="Your computer"
"DisplayName"="My Computer"
"Flags"=dword:00000021
"Icon"="explorer.exe#0100"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\1] 1236119752
@=""
"1001"=dword:00000001
"1004"=dword:00000003
"1200"=dword:00000000
"1201"=dword:00000003
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000001
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000001
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000001
"1805"=dword:00000000
"1A00"=dword:00020000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00020000
"1E05"=dword:00020000
"CurrentLevel"=dword:00010500
"Description"="This zone contains all Web sites that are on your organization's intranet."
"DisplayName"="Local intranet"
"Flags"=dword:000000db
"Icon"="shell32.dll#0018"
"MinLevel"=dword:00010000
"RecommendedLevel"=dword:00010500

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\2] 1236119752
@=""
"1001"=dword:00000000
"1004"=dword:00000001
"1200"=dword:00000000
"1201"=dword:00000001
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000000
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000000
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000000
"1805"=dword:00000000
"1A00"=dword:00000000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00030000
"1E05"=dword:00030000
"CurrentLevel"=dword:00010000
"Description"="This zone contains Web sites that you trust not to damage your computer or data."
"DisplayName"="Trusted sites"
"Flags"=dword:00000047
"Icon"="inetcpl.cpl#00004480"
"MinLevel"=dword:00010000
"RecommendedLevel"=dword:00010000

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\3] 1236119752
@=""
"1001"=dword:00000001
"1004"=dword:00000003
"1200"=dword:00000000
"1201"=dword:00000003
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000003
"1407"=dword:00000000
"1601"=dword:00000001
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000001
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000001
"1805"=dword:00000001
"1A00"=dword:00020000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000003
"1A05"=dword:00000001
"1A06"=dword:00000000
"1A10"=dword:00000001
"1C00"=dword:00010000
"1E05"=dword:00020000
"CurrentLevel"=dword:00011000
"Description"="This zone contains all Web sites you haven't placed in other zones"
"DisplayName"="Internet"
"Flags"=dword:00000001
"Icon"="inetcpl.cpl#001313"
"MinLevel"=dword:00011000
"RecommendedLevel"=dword:00011000

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\4] 1236119752
@=""
"1001"=dword:00000003
"1004"=dword:00000003
"1200"=dword:00000003
"1201"=dword:00000003
"1400"=dword:00000003
"1402"=dword:00000003
"1405"=dword:00000003
"1406"=dword:00000003
"1407"=dword:00000003
"1601"=dword:00000001
"1604"=dword:00000001
"1605"=dword:00000000
"1606"=dword:00000003
"1607"=dword:00000003
"1608"=dword:00000003
"1609"=dword:00000001
"1800"=dword:00000003
"1802"=dword:00000001
"1803"=dword:00000003
"1804"=dword:00000003
"1805"=dword:00000001
"1A00"=dword:00010000
"1A02"=dword:00000003
"1A03"=dword:00000003
"1A04"=dword:00000003
"1A05"=dword:00000003
"1A06"=dword:00000003
"1A10"=dword:00000003
"1C00"=dword:00000000
"1E05"=dword:00010000
"CurrentLevel"=dword:00012000
"Description"="This zone contains Web sites that could potentially damage your computer or data."
"DisplayName"="Restricted sites"
"Flags"=dword:00000003
"Icon"="inetcpl.cpl#00004481"
"MinLevel"=dword:00012000
"RecommendedLevel"=dword:00012000

[Software\\Wine\\Debug] 1236119752
"RelayExclude"="ntdll.RtlEnterCriticalSection;ntdll.RtlLeaveCriticalSection;kernel32.94;kernel32.95;kernel32.96;kernel32.97;kernel32.98"
"RelayFromExclude"="winex11.drv;user32;gdi32;advapi32;kernel32"

[Software\\Wine\\Fonts] 1236133128
"Codepages"="1252,437"

[Software\\Wine\\Fonts\\External Fonts] 1236133128
"AlArabiya (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlArabiya.ttf"
"AlBattar (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlBattar.ttf"
"AlHor (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlHor.ttf"
"AlManzomah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlManzomah.ttf"
"AlMateen-Bold Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMateen-Bold.ttf"
"AlMohanad (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMohanad.ttf"
"AlMothnna-Bold Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMothnna-Bold.ttf"
"AlYarmook (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlYarmook.ttf"
"Andale Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\andalemo.ttf"
"Ani (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bengali-fonts\\ani.ttf"
"AR PL UMing CN Light (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing HK Light (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing TW Light (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing TW MBE Light (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"Arab (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Arab.ttf"
"Arial (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial.ttf"
"Arial Black (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial_Black.ttf"
"Arial Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial_Bold.ttf"
"Arial Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\arialbi.ttf"
"Arial Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\ariali.ttf"
"Bitstream Vera Sans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraBd.ttf"
"Bitstream Vera Sans Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraBI.ttf"
"Bitstream Vera Sans Mono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoBd.ttf"
"Bitstream Vera Sans Mono Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoBI.ttf"
"Bitstream Vera Sans Mono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoIt.ttf"
"Bitstream Vera Sans Mono Roman (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMono.ttf"
"Bitstream Vera Sans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraIt.ttf"
"Bitstream Vera Sans Roman (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\Vera.ttf"
"Bitstream Vera Serif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraSeBd.ttf"
"Bitstream Vera Serif Roman (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraSe.ttf"
"Comic Sans MS (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Comic_Sans_MS.ttf"
"Comic Sans MS Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\comicbd.ttf"
"Cortoba (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Cortoba.ttf"
"Courier New (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New.ttf"
"Courier New Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\courbd.ttf"
"Courier New Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New_Bold_Italic.ttf"
"Courier New Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New_Italic.ttf"
"DejaVu Sans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-Bold.ttf"
"DejaVu Sans Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-BoldOblique.ttf"
"DejaVu Sans Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans.ttf"
"DejaVu Sans Condensed Condensed (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed.ttf"
"DejaVu Sans Condensed Condensed Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-Bold.ttf"
"DejaVu Sans Condensed Condensed Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-BoldOblique.ttf"
"DejaVu Sans Condensed Condensed Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-Oblique.ttf"
"DejaVu Sans Light ExtraLight (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-ExtraLight.ttf"
"DejaVu Sans Mono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-Bold.ttf"
"DejaVu Sans Mono Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-BoldOblique.ttf"
"DejaVu Sans Mono Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono.ttf"
"DejaVu Sans Mono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-Oblique.ttf"
"DejaVu Sans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-Oblique.ttf"
"DejaVu Serif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-Bold.ttf"
"DejaVu Serif Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-BoldItalic.ttf"
"DejaVu Serif Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif.ttf"
"DejaVu Serif Condensed Condensed (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerifCondensed.ttf"
"DejaVu Serif Condensed Condensed Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerifCondensed-Bold.ttf"
"DejaVu Serif Condensed Condensed Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerifCondensed-BoldItalic.ttf"
"DejaVu Serif Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-Italic.ttf"
"Dimnah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Dimnah.ttf"
"Electron (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Electron.ttf"
"FreeMono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoBold.ttf"
"FreeMono BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoBoldOblique.ttf"
"FreeMono Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMono.ttf"
"FreeMono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoOblique.ttf"
"FreeSans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansBold.ttf"
"FreeSans BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansBoldOblique.ttf"
"FreeSans Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSans.ttf"
"FreeSans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansOblique.ttf"
"FreeSerif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifBold.ttf"
"FreeSerif BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifBoldItalic.ttf"
"FreeSerif Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifItalic.ttf"
"FreeSerif Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerif.ttf"
"Furat (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Furat.ttf"
"Garuda Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-Bold.ttf"
"Garuda BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-BoldOblique.ttf"
"Garuda Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda.ttf"
"Garuda Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-Oblique.ttf"
"Georgia (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia.ttf"
"Georgia Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia_Bold.ttf"
"Georgia Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\georgiaz.ttf"
"Georgia Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia_Italic.ttf"
"Granada (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Granada.ttf"
"Graph (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Graph.ttf"
"Hani (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Hani.ttf"
"Haramain (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Haramain.ttf"
"Hor (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Hor.ttf"
"Impact (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Impact.ttf"
"Jamrul Normal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bengali-fonts\\JamrulNormal.ttf"
"Japan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Japan.ttf"
"Jet (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Jet.ttf"
"Kayrawan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Kayrawan.ttf"
"Kedage Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Kedage-b.ttf"
"Kedage BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Kedage-t.ttf"
"Kedage Normal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Kedage-n.ttf"
"Kedage NormalItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Kedage-i.ttf"
"Khalid (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Khalid.ttf"
"Kinnari Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari-Bold.ttf"
"Kinnari BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari-BoldItalic.ttf"
"Kinnari BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari-BoldOblique.ttf"
"Kinnari Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari-Italic.ttf"
"Kinnari Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari.ttf"
"Kinnari Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Kinnari-Oblique.ttf"
"Kochi Gothic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\kochi\\kochi-gothic-subst.ttf"
"Kochi Mincho (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\kochi\\kochi-mincho-subst.ttf"
"Liberation Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationMono-Regular.ttf"
"Liberation Mono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationMono-Bold.ttf"
"Liberation Mono Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationMono-BoldItalic.ttf"
"Liberation Mono Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationMono-Italic.ttf"
"Liberation Sans (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSans-Regular.ttf"
"Liberation Sans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSans-Bold.ttf"
"Liberation Sans Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSans-BoldItalic.ttf"
"Liberation Sans Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSans-Italic.ttf"
"Liberation Serif (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSerif-Regular.ttf"
"Liberation Serif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSerif-Bold.ttf"
"Liberation Serif Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSerif-BoldItalic.ttf"
"Liberation Serif Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-liberation\\LiberationSerif-Italic.ttf"
"Likhan Normal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bengali-fonts\\LikhanNormal.ttf"
"Lohit Bengali (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bengali-fonts\\lohit_bn.ttf"
"Lohit Gujarati (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_gu.ttf"
"Lohit Hindi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_hi.ttf"
"Lohit Kannada (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\lohit_kn.ttf"
"Lohit Oriya (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-oriya-fonts\\lohit_or.ttf"
"Lohit Punjabi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_pa.ttf"
"Lohit Tamil (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_ta.ttf"
"Lohit Telugu (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-telugu-fonts\\lohit_te.ttf"
"Loma Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-Bold.ttf"
"Loma BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-BoldOblique.ttf"
"Loma Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma.ttf"
"Loma Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-Oblique.ttf"
"Mallige Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Malige-b.ttf"
"Mallige BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Malige-t.ttf"
"Mallige Normal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Malige-n.ttf"
"Mallige NormalItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-kannada-fonts\\Malige-i.ttf"
"Marlett (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\marlett.ttf"
"Mashq (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Mashq.ttf"
"Mashq-Bold Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Mashq-Bold.ttf"
"Metal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Metal.ttf"
"Mitra Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bengali-fonts\\mitra.ttf"
"Mukti Narrow (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\MuktiNarrow.ttf"
"Nada (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nada.ttf"
"Nagham (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nagham.ttf"
"Nice (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nice.ttf"
"Norasi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi.ttf"
"Norasi Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Bold.ttf"
"Norasi BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-BoldItalic.ttf"
"Norasi BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-BoldOblique.ttf"
"Norasi Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Italic.ttf"
"Norasi Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Oblique.ttf"
"OpenSymbol (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\openoffice\\opens___.ttf"
"Ostorah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Ostorah.ttf"
"Ouhod-Bold Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Ouhod-Bold.ttf"
"Petra (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Petra.ttf"
"Phetsarath OT (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-lao\\Phetsarath_OT.ttf"
"Pothana2000 Pothana2000 (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-telugu-fonts\\Pothana2000.ttf"
"Purisa Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Purisa.ttf"
"Rachana (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Rachana_04.ttf"
"Rasheeq-Bold Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Rasheeq-Bold.ttf"
"Rehan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Rehan.ttf"
"Salem (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Salem.ttf"
"Samyak Oriya (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-oriya-fonts\\Samyak-Oriya.ttf"
"Sawasdee (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Sawasdee.ttf"
"Sawasdee Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeBold.ttf"
"Sawasdee BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeBoldOblique.ttf"
"Sawasdee Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeOblique.ttf"
"Shado (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Shado.ttf"
"Sharjah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Sharjah.ttf"
"Sindbad (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Sindbad.ttf"
"Tahoma (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\tahoma.ttf"
"Tahoma Bold (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\tahomabd.ttf"
"Tarablus (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Tarablus.ttf"
"Tholoth (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Tholoth.ttf"
"Times New Roman (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\times.ttf"
"Times New Roman Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Bold.ttf"
"Times New Roman Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Bold_Italic.ttf"
"Times New Roman Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Italic.ttf"
"Tlwg Typist Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-Bold.ttf"
"Tlwg Typist BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-BoldOblique.ttf"
"Tlwg Typist Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist.ttf"
"Tlwg Typist Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-Oblique.ttf"
"Tlwg Typo Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypo-Bold.ttf"
"Tlwg Typo BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypo-BoldOblique.ttf"
"Tlwg Typo Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypo.ttf"
"Tlwg Typo Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypo-Oblique.ttf"
"TlwgMono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-Bold.ttf"
"TlwgMono BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-BoldOblique.ttf"
"TlwgMono Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono.ttf"
"TlwgMono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-Oblique.ttf"
"TlwgTypewriter Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-Bold.ttf"
"TlwgTypewriter BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-BoldOblique.ttf"
"TlwgTypewriter Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter.ttf"
"TlwgTypewriter Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-Oblique.ttf"
"Trebuchet MS (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebuc.ttf"
"Trebuchet MS Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebucbd.ttf"
"Trebuchet MS Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebucbi.ttf"
"Trebuchet MS Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Trebuchet_MS_Italic.ttf"
"Umpush Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush-Bold.ttf"
"Umpush BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush-BoldOblique.ttf"
"Umpush Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush.ttf"
"Umpush Light (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush-Light.ttf"
"Umpush LightOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush-LightOblique.ttf"
"Umpush Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Umpush-Oblique.ttf"
"UnBatang (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnBatang.ttf"
"UnBatang Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnBatangBold.ttf"
"UnDotum (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnDotum.ttf"
"UnDotum Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnDotumBold.ttf"
"utkal Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\utkal.ttf"
"Vemana2000 Pothana2000 (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Vemana.ttf"
"Verdana (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana.ttf"
"Verdana Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\verdanab.ttf"
"Verdana Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana_Bold_Italic.ttf"
"Verdana Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana_Italic.ttf"
"Waree Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-Bold.ttf"
"Waree BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-BoldOblique.ttf"
"Waree Book (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree.ttf"
"Waree Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-Oblique.ttf"
"Webdings (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Webdings.ttf"
"WenQuanYi Zen Hei Medium (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\wqy\\wqy-zenhei.ttf"

[Software\\Wine\\MSHTML] 1236119752
"GeckoUrl"="http://source.winehq.org/winegecko.php"

[Software\\Wine\\MSHTML\\0.1.0] 1236119748
"GeckoPath"="C:\\windows\\gecko\\0.1.0\\wine_gecko"
```

Thanks a lot for all of your help! :biggrin:

---

### Post by cogadh on 2009-03-03
Try adding it to the end of the file like this:
```
[Software\\Wine\\X11 Driver]
"ClientSideWithRender"="N"
```

---

### Post by unplugged23 on 2009-03-04
SUCCESS!!! 

[IMG]http://img209.imageshack.us/img209/2582/screenshotwineconfigura.png[/IMG]

Thanks A LOT for your help! :D Keep up the great work!

---

