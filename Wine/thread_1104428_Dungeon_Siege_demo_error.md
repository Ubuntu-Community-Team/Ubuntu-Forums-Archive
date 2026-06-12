---
title: "Dungeon Siege demo error"
date: 2009-03-23
forum: Wine
---

### Post by wolfyking2 on 2009-03-23
Well, I found this game called 'dungeon siege' and it was diablo like, so i had to try it :)  the decided to install the demo, install went flawless, creating character was fine (i put texture detial too lowest, my computer graphics card is...undesirable) the loading took like 5 minutes (but that's some bug that can't be fixed, i'm not complaining) the intro movie works fine...but when the game actually starts, I get this error box saying 'exception found' or something like that.  Then it comes up the the windows box saying 'dungeon siege has encountered a problem and needs to close, etc'  I do not know why it is doing this, and I really want to play.  Can someone help me?

EDIT:  I clicked on the multiplayer button and the same error popped up as soon as I  clicked it.

---

### Post by hikaricore on 2009-03-23
I know I ask you this EVERY single time, but did you check the AppDB for info on this game and follow any hints found there?

---

### Post by wolfyking2 on 2009-03-23
yes, I checked the howto thing there, installed corefonts, directx9, and vcrun6 using winetricks and added the strings to the H_KEY_CURRENT_USER thing.  It's still not working.

---

### Post by wolfyking2 on 2009-03-24
bump

---

### Post by wolfyking2 on 2009-03-25
well, I think I found the error (had to open it with text  editor, wouldn't let me do anything else) this what was in the crash report thing-a-ma-jig.

-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-

-== App          : Dungeon Siege Demo (C:\Program Files\Microsoft Games\Dungeon Siege Demo\DungeonSiegeDemo.exe - DEMO: Retail)

-== Log category : Fatal Exception

-== Session      : 3/25/2009 07:00:43 AM

-== Build        : Win2k (00.[05].02.10.2301)

-== Failures     : 0 warnings, 0 errors, 0 SEH's

-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-



Siege Loader Thread



*** Report for process 0x00000032



    Process command line    : C:\PROG~FBU\MICR~SC1\DUNG~R1M\DUNG~5JV.EXE

    Process priority class  : 32

    Process priority boosted: no

    

*** Report for thread RapiMouse ***



    Exception code: access violation (continuable) - attempted to read data at 0xFF584728

    Occurred at IP: 0xFF584728

    

    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (Success)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:00:46.71

        Thread kernel mode time: 14:11:0.000

        Thread user mode time  : 366:25:40.000

    

    CPU registers:

    

        eax=FF725D33 cs=0073 eip=FF584728 eflags=00010286

        ebx=7E25A0D0 ss=007B esp=010CE254 ebp   =010CE2C0

        ecx=783407F0 ds=007B esi=7C55A8F8 fs    =0033

        edx=03801000 es=007B edi=FF1D2A30 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0C7F

        st1=  0.000000 st5=  0.000000 stat=0120

        st2=  0.000000 st6=  0.000000 tags=FFFF

        st3=  0.000000 st7=  0.000000

    

    Stack trace:

    

        0xFF584728 <unknown module>: <unknown symbol/offset>

        0x7E2166E3 <unknown module>: <unknown symbol/offset>

        0x7E8E5F4A winex11.drv: 0001:00044F4A

        0x7EDE3367 gdi32.dll: 0001:00052367

        0x7DD5BB71 wined3d.dll: 0001:0002AB71

        0x7DDF40F7 wined3d.dll: 0001:000C30F7

        0x7DD59CF4 wined3d.dll: 0001:00028CF4

        0x7DD5D5D2 wined3d.dll: 0001:0002C5D2

        0x7DD5D9EC wined3d.dll: 0001:0002C9EC

        0x7DDE5F5F wined3d.dll: 0001:000B4F5F

        0x7DDF1A80 wined3d.dll: 0001:000C0A80

        0x7DDE987B wined3d.dll: 0001:000B887B

        0x7EA7C297 ddraw.dll: 0001:0002B297

        0x0063563F DungeonSiegeDemo.exe: 0001:0023463F

        0x0063510C DungeonSiegeDemo.exe: 0001:0023410C

        0x006348CA DungeonSiegeDemo.exe: 0001:002338CA

        0x004263F4 DungeonSiegeDemo.exe: 0001:000253F4

        0x00612254 DungeonSiegeDemo.exe: 0001:00211254

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7E444FB <unknown module>: <unknown symbol/offset>

    

*** Report for thread Main ***



    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:00:40.836

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=00000001 cs=0073 eip=7BC34551 eflags=00000202

        ebx=7EA9A57C ss=007B esp=0033F720 ebp   =0033F758

        ecx=00000001 ds=007B esi=00000001 fs    =0033

        edx=00000001 es=007B edi=7BC914C8 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1= -0.000156 st5=74992520900051101000000000000.000000 stat=CAAC

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C818

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0x7BC34551 ntdll.dll: 0001:00023551

        0x7BC34657 ntdll.dll: 0001:00023657

        0x7EA65CEE ddraw.dll: 0001:00014CEE

        0x7EA65F86 ddraw.dll: 0001:00014F86

        0x00632655 DungeonSiegeDemo.exe: 0001:00231655

        0x006713C6 DungeonSiegeDemo.exe: 0001:002703C6

        0x0067100F DungeonSiegeDemo.exe: 0001:0027000F

        0x006491A8 DungeonSiegeDemo.exe: 0001:002481A8

        0x00471DED DungeonSiegeDemo.exe: 0001:00070DED

        0x00471655 DungeonSiegeDemo.exe: 0001:00070655

        0x004332D0 DungeonSiegeDemo.exe: 0001:000322D0

        0x00E85000 <unknown module>: <unknown symbol/offset>

        0x0046DF18 DungeonSiegeDemo.exe: 0001:0006CF18

    

*** Report for thread SiegeLoad ***



    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:00:48.248

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=FFFFFFFC cs=0073 eip=B7FC1410 eflags=00000246

        ebx=00000000 ss=007B esp=01EFE8D8 ebp   =01EFE944

        ecx=00000000 ds=007B esi=00000000 fs    =0033

        edx=00000000 es=007B edi=01EFE924 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1= -0.000156 st5=74992520900051101000000000000.000000 stat=CAAC

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C818

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0xB7FC1410 <unknown module>: <unknown symbol/offset>

        0x7B88D044 kernel32.dll: 0001:0006C044

        0x7B88D095 kernel32.dll: 0001:0006C095

        0x0065007A DungeonSiegeDemo.exe: 0001:0024F07A

        0x004263F4 DungeonSiegeDemo.exe: 0001:000253F4

        0x00612254 DungeonSiegeDemo.exe: 0001:00211254

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7E444FB <unknown module>: <unknown symbol/offset>

    







-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-

-== App          : Dungeon Siege Demo (C:\Program Files\Microsoft Games\Dungeon Siege Demo\DungeonSiegeDemo.exe - DEMO: Retail)

-== Log category : Fatal Exception

-== Session      : 3/25/2009 07:00:43 AM

-== Build        : Win2k (00.[05].02.10.2301)

-== Failures     : 0 warnings, 0 errors, 0 SEH's

-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-



Siege Loader Thread



*** Report for process 0x00000032



    Process command line    : C:\PROG~FBU\MICR~SC1\DUNG~R1M\DUNG~5JV.EXE

    Process priority class  : 32

    Process priority boosted: no

    

*** Report for thread RapiMouse ***



    Exception code: breakpoint (continuable)

    Occurred at IP: 0x004154C0

    

    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (Success)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:00:46.71

        Thread kernel mode time: 14:12:30.000

        Thread user mode time  : 366:26:20.000

    

    CPU registers:

    

        eax=00000001 cs=0073 eip=004154C0 eflags=00000202

        ebx=010CE901 ss=007B esp=010CDA40 ebp   =010CDD84

        ecx=010CDDD8 ds=007B esi=010CDDB8 fs    =0033

        edx=00000002 es=007B edi=006FB4C0 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0C7F

        st1=  0.000000 st5=  0.000000 stat=0122

        st2=  0.000000 st6=  0.000000 tags=FFFF

        st3=  0.000000 st7=  0.000000

    

    Stack trace:

    

        0x004154C0 DungeonSiegeDemo.exe: 0001:000144C0

        0x00634918 DungeonSiegeDemo.exe: 0001:00233918

        0x004263F4 DungeonSiegeDemo.exe: 0001:000253F4

        0x00612254 DungeonSiegeDemo.exe: 0001:00211254

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7E444FB <unknown module>: <unknown symbol/offset>

    

*** Report for thread Main ***



    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:00:40.836

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=FFFFFFFC cs=0073 eip=7BC346EF eflags=00000297

        ebx=7EA9A57C ss=007B esp=0033F8C0 ebp   =0033F968

        ecx=00000000 ds=007B esi=0033F948 fs    =0033

        edx=00000000 es=007B edi=7BC914C8 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1= -0.000156 st5=74992520900051101000000000000.000000 stat=C298

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C004

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0x7BC346EF ntdll.dll: 0001:000236EF

        0x7BC34CA0 ntdll.dll: 0001:00023CA0

        0x7EA6370F ddraw.dll: 0001:0001270F

        0x7EA637C4 ddraw.dll: 0001:000127C4

        0x00632234 DungeonSiegeDemo.exe: 0001:00231234

        0x00649193 DungeonSiegeDemo.exe: 0001:00248193

        0x00471DED DungeonSiegeDemo.exe: 0001:00070DED

        0x00471655 DungeonSiegeDemo.exe: 0001:00070655

        0x004332D0 DungeonSiegeDemo.exe: 0001:000322D0

        0x00E85000 <unknown module>: <unknown symbol/offset>

        0x0046DF18 DungeonSiegeDemo.exe: 0001:0006CF18

    







-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-

-== App          : Dungeon Siege Demo (C:\Program Files\Microsoft Games\Dungeon Siege Demo\DungeonSiegeDemo.exe - DEMO: Retail)

-== Log category : Fatal Exception

-== Session      : 3/25/2009 07:25:01 AM

-== Build        : Win2k (00.[05].02.10.2301)

-== Failures     : 0 warnings, 0 errors, 0 SEH's

-==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==--==-



Siege Loader Thread



*** Report for process 0x0000002B



    Process command line    : "C:\Program Files\Microsoft Games\Dungeon Siege Demo\DungeonSiegeDemo.Exe"

    Process priority class  : 32

    Process priority boosted: no

    

*** Report for thread RapiMouse ***



    Exception code: access violation (continuable) - attempted to read data at 0x000004D0

    Occurred at IP: 0x7E78DFD7

    

    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (Success)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:25:02.378

        Thread kernel mode time: 02:49:40.000

        Thread user mode time  : 65:42:50.000

    

    CPU registers:

    

        eax=7E24314D cs=0073 eip=7E78DFD7 eflags=00010202

        ebx=7E84484C ss=007B esp=010CDF78 ebp   =010CDFC0

        ecx=7BA79ED8 ds=007B esi=7E2521FC fs    =0033

        edx=00000000 es=007B edi=00000000 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0C7F

        st1=  0.000000 st5=  0.000000 stat=0120

        st2=  0.000000 st6=  0.000000 tags=FFFF

        st3=  0.000000 st7=  0.000000

    

    Stack trace:

    

        0x7E78DFD7 <unknown module>: <unknown symbol/offset>

        0x7E782D4B <unknown module>: <unknown symbol/offset>

        0x7E853443 <unknown module>: <unknown symbol/offset>

        0x7E20B61D <unknown module>: <unknown symbol/offset>

        0x7E20C0CF <unknown module>: <unknown symbol/offset>

        0x7E20D22D <unknown module>: <unknown symbol/offset>

        0x7E20D33D <unknown module>: <unknown symbol/offset>

        0x7E20D6E3 <unknown module>: <unknown symbol/offset>

        0x7E8DAF4A winex11.drv: 0001:00049F4A

        0x7EDE8367 gdi32.dll: 0001:00057367

        0x7DD52B71 wined3d.dll: 0001:00021B71

        0x7DDEB0F7 wined3d.dll: 0001:000BA0F7

        0x7DD50CF4 wined3d.dll: 0001:0001FCF4

        0x7DD545D2 wined3d.dll: 0001:000235D2

        0x7DD549EC wined3d.dll: 0001:000239EC

        0x7DDDCF5F wined3d.dll: 0001:000ABF5F

        0x7DDE8A80 wined3d.dll: 0001:000B7A80

        0x7DDE087B wined3d.dll: 0001:000AF87B

        0x7EA70297 ddraw.dll: 0001:0002F297

        0x0063563F DungeonSiegeDemo.exe: 0001:0023463F

        0x0063510C DungeonSiegeDemo.exe: 0001:0023410C

        0x006348CA DungeonSiegeDemo.exe: 0001:002338CA

        0x004263F4 DungeonSiegeDemo.exe: 0001:000253F4

        0x00612254 DungeonSiegeDemo.exe: 0001:00211254

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7D9B4FB <unknown module>: <unknown symbol/offset>

    

*** Report for thread Main ***



    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:25:01.85

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=006F80F8 cs=0073 eip=00431D5C eflags=00000206

        ebx=7EEB2D00 ss=007B esp=0032FB58 ebp   =0032FB70

        ecx=00EB00AC ds=007B esi=0032FBFC fs    =0033

        edx=7EF2D364 es=007B edi=00000000 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1=  0.000000 st5=74992520900051101000000000000.000000 stat=C7D0

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C53C

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0x00431D5C DungeonSiegeDemo.exe: 0001:00030D5C

        0x004332D0 DungeonSiegeDemo.exe: 0001:000322D0

        0x00E95000 <unknown module>: <unknown symbol/offset>

        0x0046DF18 DungeonSiegeDemo.exe: 0001:0006CF18

    

*** Report for thread SiegeLoad ***



    Thread traits:

    

        Thread priority        : 0

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:25:02.789

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=FFFFFFFC cs=0073 eip=B7F18410 eflags=00000246

        ebx=00000000 ss=007B esp=01EFE8D8 ebp   =01EFE944

        ecx=00000000 ds=007B esi=00000000 fs    =0033

        edx=00000000 es=007B edi=01EFE924 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1=  0.000000 st5=74992520900051101000000000000.000000 stat=C7D0

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C53C

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0xB7F18410 <unknown module>: <unknown symbol/offset>

        0x7B88D044 kernel32.dll: 0001:0006C044

        0x7B88D095 kernel32.dll: 0001:0006C095

        0x0065007A DungeonSiegeDemo.exe: 0001:0024F07A

        0x004263F4 DungeonSiegeDemo.exe: 0001:000253F4

        0x00612254 DungeonSiegeDemo.exe: 0001:00211254

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7D9B4FB <unknown module>: <unknown symbol/offset>

    

*** Report for thread #0x35 ***



    Thread traits:

    

        Thread priority        : 15

        Last error             : 0x00000000 (<unknown>)

        Thread priority boosted: <unknown>

        Thread creation time   : 03/25/2009,07:25:04.588

        Thread kernel mode time: 00:00:0.000

        Thread user mode time  : 00:00:0.000

    

    CPU registers:

    

        eax=FFFFFFFC cs=0073 eip=B7F18410 eflags=00000246

        ebx=04D2EA10 ss=007B esp=04D2E9A4 ebp   =04D2E9C8

        ecx=00000001 ds=007B esi=7ED01200 fs    =0033

        edx=FFFFFFFF es=007B edi=B7D90FF4 gs    =003B

    

    FPU registers:

    

        st0=  0.000000 st4=  0.000000 ctrl=0048

        st1=  0.000000 st5=74992520900051101000000000000.000000 stat=C7D0

        st2=2036349328973201900000000000000000000.000000 st6=18176800534038298000000000000000.000000 tags=C53C

        st3=  0.000000 st7=73027876963360891000000000000000.000000

    

    Stack trace:

    

        0xB7F18410 <unknown module>: <unknown symbol/offset>

        0x7ECA6885 winmm.dll: 0001:00025885

        0x7BC7172E ntdll.dll: 0001:0006072E

        0x7BC71A02 ntdll.dll: 0001:00060A02

        0x7BC72A85 ntdll.dll: 0001:00061A85

        0xB7D9B4FB <unknown module>: <unknown symbol/offset>

---

