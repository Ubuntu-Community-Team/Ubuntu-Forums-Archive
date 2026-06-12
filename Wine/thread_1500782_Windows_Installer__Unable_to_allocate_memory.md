---
title: "Windows Installer:  Unable to allocate memory?"
date: 2010-06-03
forum: Wine
---

### Post by McRat on 2010-06-03
I'm trying to get a Win program to install, but it stops shortly after starting.  The error log says Unable to Allocate Memory.

The program is a commercial product "EFILive" which is an engine tuning program available for free download:

[http://www.efilive.com/index.php?option=com_content&view=article&id=48&Itemid=133](http://www.efilive.com/index.php?option=com_content&view=article&id=48&Itemid=133)

The EFILive v7.5.6 Build 117 is what I'm trying to install.

I have 4gb Ram on a AMD64 running Ubuntu 10.04 32-bit with the latest Crossover Pro software (retail).

I tried both creating Bottles (XP/98/W2000/Vista) then running Setup.exe, and also Install Windows Software>Other Applications.

No dice.

Where do I start to debug?

```


***** Wed Jun  2 12:16:01 2010
Starting: '/home/patrick/cxoffice/bin/wine' '--no-convert' '--wl-app' 'assocscan.exe' '--scan' '--icon-dir' '/home/patrick/.cxoffice/EFILive/windata/Associations'

CXConfig->read(/home/patrick/cxoffice/etc/cxoffice.conf)
Product version=9.0.0
3370: Grabbing the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
3370: Got the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
CXConfig->read(/home/patrick/.cxoffice/EFILive/cxbottle.conf)
Mode = 'private'
Environment:
  CX_ROOT = "/home/patrick/cxoffice"
  CX_BOTTLE = "EFILive"
  WINEPREFIX = "/home/patrick/.cxoffice/EFILive"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/home/patrick/cxoffice/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/home/patrick/cxoffice/lib"
  WINEDLLPATH = "/home/patrick/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/home/patrick/cxoffice/bin/wineloader"
  WINESERVER = "/home/patrick/cxoffice/bin/wineserver"
  WINEDEBUG = "+seh,+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/patrick/.cxoffice/desktopdata/com.codeweavers.unknown.3031.log.fifo"
  CX_DEBUGMSG = "+seh,+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = <undefined>
  DISPLAY = ":0.0"
3370: Releasing the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
Command:
/home/patrick/cxoffice/bin/wineloader winewrapper.exe --no-convert --run -- /home/patrick/cxoffice/lib/wine/assocscan.exe.so --scan --icon-dir /home/patrick/.cxoffice/EFILive/windata/Associations

** Wed Jun  2 12:16:01 2010
Starting '/home/patrick/cxoffice/bin/wineloader' 'winewrapper.exe' '--no-convert' '--run' '--'
'/home/patrick/cxoffice/lib/wine/assocscan.exe.so' '--scan' '--icon-dir' '/home/patrick/.cxoffice/EFILive/windata/Associations'



***** Wed Jun  2 12:16:01 2010
Starting: '/home/patrick/cxoffice/bin/wine' '--bottle' 'EFILive' '--untrusted' '--wait-children' '--' '/home/patrick/cxoffice/bin/EFILiveV7.5.6.117_Setup.exe'

CXConfig->read(/home/patrick/cxoffice/etc/cxoffice.conf)
Product version=9.0.0
3377: Grabbing the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
3377: Got the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
CXConfig->read(/home/patrick/.cxoffice/EFILive/cxbottle.conf)
Mode = 'private'
Environment:
  CX_ROOT = "/home/patrick/cxoffice"
  CX_BOTTLE = "EFILive"
  WINEPREFIX = "/home/patrick/.cxoffice/EFILive"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/home/patrick/cxoffice/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/home/patrick/cxoffice/lib"
  WINEDLLPATH = "/home/patrick/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/home/patrick/cxoffice/bin/wineloader"
  WINESERVER = "/home/patrick/cxoffice/bin/wineserver"
  WINEDEBUG = "+seh,+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/patrick/.cxoffice/desktopdata/com.codeweavers.unknown.3031.log.fifo"
  CX_DEBUGMSG = "+seh,+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = <undefined>
  DISPLAY = ":0.0"
3377: Releasing the '/tmp/.wine-1000/bottle-801-68022e.lock' lock
Running `"/home/patrick/cxoffice/bin/cxavscan" "/home/patrick/cxoffice/bin/EFILiveV7.5.6.117_Setup.exe"`


***** Wed Jun  2 12:16:01 2010
Starting: '/home/patrick/cxoffice/bin/cxavscan' '/home/patrick/cxoffice/bin/EFILiveV7.5.6.117_Setup.exe'

CXConfig->read(/home/patrick/cxoffice/etc/cxoffice.conf)
Found no anti-virus tool
-> rc=768  (took 0.0221710205078125 seconds)
output=[]
Command:
/home/patrick/cxoffice/bin/wineloader winewrapper.exe --wait-children --run -- /home/patrick/cxoffice/bin/EFILiveV7.5.6.117_Setup.exe

** Wed Jun  2 12:16:01 2010
Starting '/home/patrick/cxoffice/bin/wineloader' 'winewrapper.exe' '--wait-children' '--run' '--'
'/home/patrick/cxoffice/bin/EFILiveV7.5.6.117_Setup.exe'

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:reg:GetNativeSystemInfo (0x33fc60) using GetSystemInfo()
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179360 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bdc0 0x33f784 0x179360 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c8ac
trace:seh:raise_exception  info[2]=0090ddec
trace:seh:raise_exception  info[3]=0090c738
trace:seh:raise_exception  info[4]=0090ffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bcfc 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090bcfc
trace:seh:raise_exception  info[2]=008e02c4
trace:seh:raise_exception  info[3]=0090c738
trace:seh:raise_exception  info[4]=008effff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90c8ac 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c8ac
trace:seh:raise_exception  info[2]=008dc7cc
trace:seh:raise_exception  info[3]=0090c738
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bcfc 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090bcfc
trace:seh:raise_exception  info[2]=008e0848
trace:seh:raise_exception  info[3]=0090c788
trace:seh:raise_exception  info[4]=008effff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bdbc 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c754
trace:seh:raise_exception  info[2]=008e490c
trace:seh:raise_exception  info[3]=0090c808
trace:seh:raise_exception  info[4]=008effff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bd24 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c754
trace:seh:raise_exception  info[2]=008ff810
trace:seh:raise_exception  info[3]=0090c820
trace:seh:raise_exception  info[4]=008fffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90c8ac 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c8ac
trace:seh:raise_exception  info[2]=008ddeec
trace:seh:raise_exception  info[3]=0090c820
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bd24 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090bd24
trace:seh:raise_exception  info[2]=008d3684
trace:seh:raise_exception  info[3]=0090f830
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90c8ac 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c8ac
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=0090f8bc
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f784 0x179760 0x33f780 0x33f778 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x90bd24 0x33f784 0x179760 0x33f780 0x33f778 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0090c8ac
trace:seh:raise_exception  info[2]=008df944
trace:seh:raise_exception  info[3]=0090f8bc
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f9ec
trace:seh:raise_exception  info[6]=0033f9b0
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f9b0 edi=0033f950
trace:seh:raise_exception  ebp=0033f97c esp=0033f918 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e8 0x16a190 0x33f7e4 0x33f7dc - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e4 0x16a190 0x33f7e0 0x33f7d8 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913950 0x33f7e0 0x16a190 0x33f7dc 0x33f7d4 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f8a8 0x1727e0 0x33f8a4 0x33f89c - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fcc 0x33f8a8 0x1727e0 0x33f8a4 0x33f89c - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f8a4 0x1727e0 0x33f8a0 0x33f898 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8ebbb4 0x33f8a4 0x1727e0 0x33f8a0 0x33f898 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f8a0 0x1727e0 0x33f89c 0x33f894 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fcc 0x33f8a0 0x1727e0 0x33f89c 0x33f894 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x1727e0 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x9133cc 0x33f7ec 0x1727e0 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x16b760 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d93e4 0x33f6cc 0x16b760 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x163808 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8ebe68 0x33f7ec 0x163808 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x169b80 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d93d0 0x33f6cc 0x169b80 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x169bc0 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8ebbb4 0x33f7ec 0x169bc0 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=00912d3c
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=0091ffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x169c10 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d93e4 0x33f6cc 0x169c10 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x169c60 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x9133cc 0x33f7ec 0x169c60 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x172db0 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d93d0 0x33f6cc 0x172db0 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x172e00 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8eb8fc 0x33f7ec 0x172e00 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x16b180 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fe4 0x33f7ec 0x16b180 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x16b1d0 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d9100 0x33f6cc 0x16b1d0 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x16b220 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fe4 0x33f7ec 0x16b220 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008df944
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x16b270 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8eb8fc 0x33f6cc 0x16b270 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x16b388 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fe4 0x33f7ec 0x16b388 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=008d0720
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x16b9e8 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x913fe4 0x33f7ec 0x16b9e8 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00913fe4
trace:seh:raise_exception  info[2]=00900790
trace:seh:raise_exception  info[3]=00913c1c
trace:seh:raise_exception  info[4]=0090ffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f6cc 0x16ba38 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8d93d0 0x33f6cc 0x16ba38 0x33f6c8 0x33f6c0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x172bc0 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x9157d8 0x33f7ec 0x1654b8 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=00915840
trace:seh:raise_exception  info[2]=00900bf4
trace:seh:raise_exception  info[3]=009157e0
trace:seh:raise_exception  info[4]=0090ffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f7ec 0x172bc0 0x33f7e8 0x33f7e0 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x916014 0x33f7ec 0x1654b8 0x33f7e8 0x33f7e0 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=0091607c
trace:seh:raise_exception  info[2]=00905c80
trace:seh:raise_exception  info[3]=0091601c
trace:seh:raise_exception  info[4]=0090ffff
trace:seh:raise_exception  info[5]=0033fa54
trace:seh:raise_exception  info[6]=0033fa18
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033fa18 edi=0033f9b8
trace:seh:raise_exception  ebp=0033f9e4 esp=0033f980 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f424 0x1655b8 0x33f420 0x33f418 - stub
fixme:advapi:LookupAccountNameW L"" L"patrick" 0x8e0d30 0x33f424 0x1655b8 0x33f420 0x33f418 - stub
trace:seh:raise_exception code=eedfade flags=1 addr=0x7b8402f9 ip=7b8402f9 tid=0024
trace:seh:raise_exception  info[0]=0041cc71
trace:seh:raise_exception  info[1]=008e0d30
trace:seh:raise_exception  info[2]=008d3950
trace:seh:raise_exception  info[3]=00916b44
trace:seh:raise_exception  info[4]=008dffff
trace:seh:raise_exception  info[5]=0033f68c
trace:seh:raise_exception  info[6]=0033f650
trace:seh:raise_exception  eax=7b82bec9 ebx=7b8ad7f4 ecx=00000000 edx=00000018 esi=0033f650 edi=0033f5f0
trace:seh:raise_exception  ebp=0033f61c esp=0033f5b8 cs=0073 ds=007b es=007b fs=0033 gs=003b flags=00200216
trace:seh:call_vectored_handlers calling handler at 0x76a3e340 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x76a3e340 returned 0
trace:seh:call_vectored_handlers calling handler at 0x7b83d100 code=eedfade flags=1
trace:seh:call_vectored_handlers handler at 0x7b83d100 returned 0
trace:seh:call_stack_handlers calling handler at 0x41ccf1 code=eedfade flags=1
trace:seh:call_stack_handlers handler at 0x41ccf1 returned 1
trace:seh:call_stack_handlers calling handler at 0x403f85 code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
trace:seh:__regs_RtlUnwind calling handler at 0x41ccf1 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x4043bc returned 1
trace:seh:call_stack_handlers handler at 0x404437 returned 1
trace:seh:call_stack_handlers calling handler at 0x4cf37c code=eedfade flags=1
trace:seh:__regs_RtlUnwind code=eedfade flags=3
trace:seh:__regs_RtlUnwind calling handler at 0x7bc6a180 code=eedfade flags=3
trace:seh:__regs_RtlUnwind handler at 0x7bc6a180 returned 1
fixme:advapi:LookupAccountNameW L"" L"patrick" (nil) 0x33f450
```

---

### Post by asdfoo on 2010-06-03
Crossover isn't supported here.  You should be posting on their forum if you want help with that product.

If you'd like assistance here you should be using vanilla Wine from winehq.org.

wine-1.2-rc2 is the most recent version.

---

### Post by McRat on 2010-06-04
Thanks.

---

### Post by McRat on 2010-06-04
Update:  Wine 1.2 rc2 worked when Crossover 9.0.0 would not.

However, this app requires FTDI-chipped USB support.  So it would not talk to the interface.  I tried the "Russian fix" but nothing changed.

While FTDI has a Linux driver, installing a driver in Linux is beyond my abilities for now.  None of the install instructions worked.

---

