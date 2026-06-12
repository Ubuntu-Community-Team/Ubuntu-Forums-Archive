---
title: "world of warcraft, crashing at launch"
date: 2009-06-21
forum: Wine
---

### Post by Julakk on 2009-06-21
sorry for this another wow issue post (i might be in the wrong section of the forum, sorry !)
i've been trying to find a solution either in french or in english, on both forums and guide.
i tried by myself for a week and nothing seems to work >.<
when i launch wow i get error 132 

i got last wine version (1.1.24)( i had the last stable version yesterday and it wasnt working either)
Ubuntu 8.10
carte ati radeon x1600

my error message, on the terminal:

    > ge@ge-desktop:~$ wine /home/ge/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -OpenGL
    fixme:advapi:SetSecurityInfo stub
    archive Data\enUS\patch-enUS.MPQ opened
    archive Data\patch.MPQ opened
    archive Data\enUS\patch-enUS-2.MPQ opened
    archive Data\patch-2.MPQ opened
    archive Data\expansion.MPQ opened
    archive Data\lichking.MPQ opened
    archive Data\common.MPQ opened
    archive Data\common-2.MPQ opened
    archive Data\enUS\locale-enUS.MPQ opened
    archive Data\enUS\speech-enUS.MPQ opened
    archive Data\enUS\expansion-locale-enUS.MPQ opened
    archive Data\enUS\lichking-locale-enUS.MPQ opened
    archive Data\enUS\expansion-speech-enUS.MPQ opened
    archive Data\enUS\lichking-speech-enUS.MPQ opened
  **  fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub**!

my wow error message :

>     this application has encountered a critical error:

    ERROR #132 (0x85100084) Fatal Exception
    Program:    C:\Program Files\World of Warcraft\Wow.exe
    Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:7CA0C2E7

    The instruction at "0x7CA0C2E7" referenced memory at "0x00000018".
    The memory could not be "read".


    WoWBuild: 9947
    Settings:
    SET locale "enUS"
    SET realmList "us.logon.worldofwarcraft.com"
    SET patchlist "us.version.worldofwarcraft.com"
    SET coresDetected "1"
    ------------------------------------------------------------------------------

    ----------------------------------------
        x86 Registers
    ----------------------------------------

    EAX=00000000  EBX=00000000  ECX=7CB2D9A0  EDX=6ACED9D0  ESI=00000001
    EDI=7BAFFA88  EBP=003AE9BC  ESP=003AE940  EIP=7CA0C2E7  FLG=00010246
    CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


    ----------------------------------------
        Stack Trace (Manual)
    ----------------------------------------

    Address  Frame    Logical addr  Module

    Showing 2/2 threads...

    --- Thread ID: 41 ---
    7B88F972 01CCE9A0 0001:0006E972 C:\windows\system32\KERNEL32.dll
    7B88F9B5 01CCE9C0 0001:0006E9B5 C:\windows\system32\KERNEL32.dll
    004245E4 01CCE9E8 0001:000235E4 C:\Program Files\World of Warcraft\Wow.exe
    008D967F 01CCEA20 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe
    008D9724 01CCEA38 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe
    7BC75382 01CCEAD8 0001:00064382 C:\windows\system32\ntdll.dll
    7BC75550 01CCF3C8 0001:00064550 C:\windows\system32\ntdll.dll
    B7F7450F 01CCF4C8 0000:00000000 <unknown>

    --- Thread ID: 40 [Current Thread] ---
    7CA0C2E7 003AE9BC 0000:00000000 <unknown>
    7C56B20A 003AE9FC 0000:00000000 <unknown>
    7C7866F0 003AEA3C 0000:00000000 <unknown>
    7E8AAF39 003AEABC 0001:000D9F39 C:\windows\system32\wined3d.dll
    7E82B046 003AF09C 0001:0005A046 C:\windows\system32\wined3d.dll
    7E8AF593 003AF0CC 0001:000DE593 C:\windows\system32\wined3d.dll
    7E8FA9A0 003AF0FC 0001:000099A0 C:\windows\system32\d3d9.dll
    00628C0A 003AF110 0001:00227C0A C:\Program Files\World of Warcraft\Wow.exe
    00623867 003AF728 0001:00222867 C:\Program Files\World of Warcraft\Wow.exe
    00553E62 003AFB54 0001:00152E62 C:\Program Files\World of Warcraft\Wow.exe
    00551450 003AFC10 0001:00150450 C:\Program Files\World of Warcraft\Wow.exe
    00406A1E 003AFE5C 0001:00005A1E C:\Program Files\World of Warcraft\Wow.exe
    00406BF9 003AFE6C 0001:00005BF9 C:\Program Files\World of Warcraft\Wow.exe
    00406C7D 003AFF08 0001:00005C7D C:\Program Files\World of Warcraft\Wow.exe
    7B877ED0 003AFFE8 0001:00056ED0 C:\windows\system32\KERNEL32.dll

    ----------------------------------------
        Stack Trace (Using DBGHELP.DLL)
    ----------------------------------------

    Showing 2/2 threads...

    --- Thread ID: 41 ---
    7B88F972 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x01CCE9C0,0x7B8549D7)
    7B88F9B5 KERNEL32.dll Sleep+37 (0x00000064,0x7B88F990,0x7BC93FF4,0x01AEA8D8)
    004245E4 Wow.exe      <unknown symbol>+0 (0x01AEA8D8,0x7FB1BB6E,0x008D96A5,0x01AEA938)
    008D967F Wow.exe      <unknown symbol>+0 (0x01AEA938,0x7BC7354E,0x01AEA938,0x01AEA938)
    008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x01AEA938,0x7BCAF8A0,0xB7F790C1)
    7BC75382 ntdll.dll    <unknown symbol>+0 (0x01CCEB0C,0x00000000,0x00000000,0x00000000)
    7BC75550 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01CCFB90,0x01CCFB90,0x01CCFB90)
    B7F7450F              start_thread+191 (0x01CCFB90,0x00000000,0x00000000,0x00000000)
    B7EF17EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

    --- Thread ID: 40 [Current Thread] ---
    7CA0C2E7              <unknown symbol>+0 (0x7BBE5490,0x00000000,0x00000000,0x00000001)
    7C56B20A              <unknown symbol>+0 (0x7BBE2D98,0x00008D40,0x00008CE0,0x00000DE1)
    7C7866F0              <unknown symbol>+0 (0x00008D40,0x00008CE0,0x00000DE1,0x00000001)
    7E8AAF39 wined3d.dll  initPixelFormats+1849 (0x0013F61C,0x7E121242,0x00000021,0x00000100)
    7E82B046 wined3d.dll  InitAdapters+52678 (0x0013F5F8,0x00000008,0x00000924,0x7BC34ED1)
    7E8AF593 wined3d.dll  WineDirect3DCreate+99 (0x00000009,0x0013F5E0,0x00000010,0x7B86851D)
    7E8FA9A0 d3d9.dll     Direct3DCreate9+112 (0x00000020,0x00000000,0x00000000,0x003AF728)
    00628C0A Wow.exe      <unknown symbol>+0 (0x003AF720,0x003AF724,0x01113F10,0x01113F12)
    00623867 Wow.exe      <unknown symbol>+0 (0x01113F10,0x01113F12,0x01113F14,0x01113F18)
    00553E62 Wow.exe      <unknown symbol>+0 (0x01113F10,0x01114095,0x0099E6E8,0x0099E6F4)
    00551450 Wow.exe      <unknown symbol>+0 (0x003AFC24,0x00000001,0x00000001,0x6C726F57)
    00406A1E Wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x003AFF08,0x00406C7D)
    00406BF9 Wow.exe      <unknown symbol>+0 (0x0040AFD9,0x00400000,0x00000000,0x00114EB4)
    00406C7D Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
    7B877ED0 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
    B7F9EDA7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


    ----------------------------------------
        Loaded Modules
    ----------------------------------------

    0x00400000 - 0x01758000  C:\Program Files\World of Warcraft\Wow.exe
    0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
    0x7B820000 - 0x7B954000  C:\windows\system32\KERNEL32.dll
    0x7BC10000 - 0x7BCB0000  C:\windows\system32\ntdll.dll
    0x7BF40000 - 0x7BF7F000  C:\windows\system32\dbghelp.dll
    0x7C160000 - 0x7C189000  C:\windows\system32\uxtheme.dll
    0x7C350000 - 0x7C363000  C:\windows\system32\psapi.dll
    0x7DEC0000 - 0x7DEC9000  C:\windows\system32\midimap.dll
    0x7DED0000 - 0x7DEE1000  C:\windows\system32\msacm32.drv
    0x7E020000 - 0x7E050000  C:\windows\system32\winealsa.drv
    0x7E0A0000 - 0x7E125000  C:\windows\system32\winex11.drv
    0x7E230000 - 0x7E235000  C:\windows\system32\lz32.dll
    0x7E240000 - 0x7E250000  C:\windows\system32\version.dll
    0x7E260000 - 0x7E2BD000  C:\windows\system32\rpcrt4.dll
    0x7E2E0000 - 0x7E3B7000  C:\windows\system32\ole32.dll
    0x7E3C0000 - 0x7E3F0000  C:\windows\system32\dinput.dll
    0x7E400000 - 0x7E40A000  C:\windows\system32\dinput8.dll
    0x7E410000 - 0x7E438000  C:\windows\system32\ws2_32.dll
    0x7E440000 - 0x7E45E000  C:\windows\system32\msacm32.dll
    0x7E470000 - 0x7E526000  C:\windows\system32\comctl32.dll
    0x7E540000 - 0x7E6B0000  C:\windows\system32\shell32.dll
    0x7E6C0000 - 0x7E70E000  C:\windows\system32\shlwapi.dll
    0x7E710000 - 0x7E731000  C:\windows\system32\mpr.dll
    0x7E750000 - 0x7E79A000  C:\windows\system32\wininet.dll
    0x7E7A0000 - 0x7E7BB000  C:\windows\system32\imm32.dll
    0x7E7D0000 - 0x7E8E6000  C:\windows\system32\wined3d.dll
    0x7E8F0000 - 0x7E917000  C:\windows\system32\d3d9.dll
    0x7EAF0000 - 0x7EB71000  C:\windows\system32\opengl32.dll
    0x7EB80000 - 0x7EBC7000  C:\windows\system32\advapi32.dll
    0x7EBE0000 - 0x7EC68000  C:\windows\system32\gdi32.dll
    0x7EC80000 - 0x7EDB3000  C:\windows\system32\user32.dll
    0x7EDC0000 - 0x7EE4A000  C:\windows\system32\winmm.dll


    ----------------------------------------
        Memory Dump
    ----------------------------------------

    Code: 16 bytes starting at (EIP = 7CA0C2E7)

    7CA0C2E7: 8B 40 18 C3  90 8D 74 26  00 55 89 E5  5D C3 90 8D  .@....t&.U..]...


    Stack: 1024 bytes starting at (ESP = 003AE940)

    * = addr  **                                                  *               
    003AE940: 59 B4 9F 7C  00 00 00 00  18 3E 1D 7C  8C E9 3A 00  Y..|.....>.|..:.
    003AE950: 00 00 00 00  80 E9 3A 00  00 00 00 00  00 00 00 00  ......:.........
    003AE960: 01 00 00 00  01 00 00 00  00 10 00 00  18 3E 1D 7C  .............>.|
    003AE970: 00 00 00 00  00 00 00 00  40 01 43 7D  00 00 00 00  ........@.C}....
    003AE980: 80 ED CE 6A  88 FA AF 7B  80 ED CE 6A  00 00 00 00  ...j...{...j....
    003AE990: 00 00 00 00  90 54 BE 7B  88 FA AF 7B  D0 D9 CE 6A  .....T.{...{...j
    003AE9A0: 00 00 00 00  D0 D9 CE 6A  00 00 00 00  80 ED CE 6A  .......j.......j
    003AE9B0: 98 2D BE 7B  01 00 00 00  00 00 00 00  FC E9 3A 00  .-.{..........:.
    003AE9C0: 0A B2 56 7C  90 54 BE 7B  00 00 00 00  00 00 00 00  ..V|.T.{........
    003AE9D0: 01 00 00 00  01 00 00 00  00 00 00 00  00 00 00 00  ................
    003AE9E0: 1A 04 00 00  01 00 00 00  01 00 00 00  00 00 00 00  ................
    003AE9F0: 00 00 00 00  01 00 00 00  E1 0D 00 00  3C EA 3A 00  ............<.:.
    003AEA00: F0 66 78 7C  98 2D BE 7B  40 8D 00 00  E0 8C 00 00  .fx|.-.{@.......
    003AEA10: E1 0D 00 00  01 00 00 00  00 00 00 00  3C EA 3A 00  ............<.:.
    003AEA20: A1 6A 78 7C  98 2D BE 7B  E0 8C 00 00  40 8D 00 00  .jx|.-.{....@...
    003AEA30: F4 3F 8E 7E  A8 EA 3A 00  F0 2F 14 00  BC EA 3A 00  .?.~..:../....:.
    003AEA40: 39 AF 8A 7E  40 8D 00 00  E0 8C 00 00  E1 0D 00 00  9..~@...........
    003AEA50: 01 00 00 00  00 00 00 00  00 00 00 00  08 19 00 00  ................
    003AEA60: 01 14 00 00  00 00 00 00  74 EB DA 6A  1C 98 8D 7E  ........t..j...~
    003AEA70: F4 9F F6 B7  C0 84 8D 7E  C0 84 8D 7E  9C EA 3A 00  .......~...~..:.
    003AEA80: 56 14 E8 B7  F4 EF C4 7E  F8 F5 13 00  AC EA 3A 00  V......~......:.
    003AEA90: 08 19 00 00  01 14 00 00  D5 8C 00 00  50 01 00 00  ............P...
    003AEAA0: 3F 45 C3 7B  00 00 00 00  01 00 00 00  01 00 00 00  ?E.{............
    003AEAB0: F4 3F 8E 7E  AE EF 3A 00  1C F6 13 00  9C F0 3A 00  .?.~..:.......:.
    003AEAC0: 46 B0 82 7E  1C F6 13 00  42 12 12 7E  21 00 00 00  F..~....B..~!...
    003AEAD0: 00 01 00 00  1C F6 13 00  40 00 00 00  3F 45 C3 7B  ........@...?E.{
    003AEAE0: 10 00 00 00  00 00 C1 7B  60 C0 C3 7B  E6 57 C4 7B  .......{`..{.W.{
    003AEAF0: 88 EB 3A 00  00 00 00 00  AC EB 33 61  65 64 61 30  ..:.......3aeda0
    003AEB00: 91 B5 E3 B7  B0 00 00 00  63 12 12 7E  1C 4B 8E 7E  ........c..~.K.~
    003AEB10: 49 4E 8C 7E  04 08 8C 7E  80 E6 8D 7E  1C 4B 8E 7E  IN.~...~...~.K.~
    003AEB20: 49 4E 8C 7E  12 1D 8C 7E  DC 43 C9 7B  00 00 C1 7B  IN.~...~.C.{...{
    003AEB30: E4 D7 E7 B7  4D 00 00 00  39 02 00 49  F4 9F F6 B7  ....M...9..I....
    003AEB40: 87 F0 CA 7B  8C 45 8C 7E  68 45 8C 7E  6B 20 8C 7E  ...{.E.~hE.~k .~
    003AEB50: 5B 20 8C 7E  87 F0 CA 7B  9B F9 E4 B7  F4 9F F6 B7  [ .~...{........
    003AEB60: 87 F0 CA 7B  88 EB 3A 00  9F EC E7 B7  AC EB 3A 00  ...{..:.......:.
    003AEB70: A6 EC CA 7B  00 4E 8E 7E  8C EF 3A 00  7C EF 3A 00  ...{.N.~..:.|.:.
    003AEB80: 78 EF 3A 00  68 EF 3A 00  98 EC 3A 00  42 7F F0 B7  x.:.h.:...:.B...
    003AEB90: 64 53 8E 7E  1C F6 13 00  3C 4F 8E 7E  F8 F5 13 00  dS.~....<O.~....
    003AEBA0: 00 00 00 00  4C EC 3A 00  5C 00 00 00  00 00 00 00  ....L.:.\.......
    003AEBB0: F0 45 CE 6A  90 28 8C 7E  37 F7 13 00  A6 EC CA 7B  .E.j.(.~7......{
    003AEBC0: D4 EA 8D 7E  00 00 00 00  12 FF CE 6A  42 12 12 7E  ...~.......jB..~
    003AEBD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
    003AEBE0: 00 00 00 00  FC 23 36 7C  04 00 00 00  EE 31 C4 7B  .....#6|.....1.{
    003AEBF0: 00 00 00 00  00 00 00 00  64 00 6C 00  04 1A FA B7  ........d.l.....
    003AEC00: 64 00 6C 00  6C 00 00 00  00 00 00 00  E1 B5 F9 B7  d.l.l...........
    003AEC10: 14 00 11 00  FF FF FF FF  68 EC 3A 00  80 47 C4 7B  ........h.:..G.{
    003AEC20: 40 99 F6 B7  00 00 00 00  C8 ED 3A 00  AC EC 3A 00  @.........:...:.
    003AEC30: 91 B5 E3 B7  C8 F7 13 00  40 00 00 00  F4 3F C9 7B  ........@....?.{
    003AEC40: 40 99 F6 B7  00 00 00 00  18 ED 3A 00  B7 5D C3 7B  @.........:..].{
    003AEC50: 00 00 00 00  FF FF FF FF  AB AA C6 7B  F4 3F C9 7B  ...........{.?.{
    003AEC60: 94 EB CA 7B  F8 FE 3A 00  C0 5E C3 7B  F4 3F C9 7B  ...{..:..^.{.?.{
    003AEC70: 00 00 00 00  DA 9B D4 7E  B8 EC 3A 00  25 5B C3 7B  .......~..:.%[.{
    003AEC80: 60 DD 05 B8  60 CC 05 B8  44 00 00 00  88 EC CA 7B  `...`...D......{
    003AEC90: D8 EC 3A 00  94 B0 F7 B7  26 00 00 00  0C 5C C3 7B  ..:.....&....\.{
    003AECA0: 88 EC CA 7B  CC EC CA 7B  00 00 00 00  FF FF FF FF  ...{...{........
    003AECB0: DA 9B D4 7E  50 ED 3A 00  D8 EC 3A 00  88 EC CA 7B  ...~P.:...:....{
    003AECC0: 80 E8 CA 7B  00 00 00 00  A6 EC CA 7B  F4 3F C9 7B  ...{.......{.?.{
    003AECD0: 1E 00 00 00  DA 9B D4 7E  08 ED 3A 00  A0 5C C3 7B  .......~..:..\.{
    003AECE0: DA 9B D4 7E  50 ED 3A 00  C1 7D D7 7E  EA 9E D4 7E  ...~P.:..}.~...~
    003AECF0: 05 00 00 00  C8 F7 13 00  01 00 00 00  F4 DF 0B B8  ................
    003AED00: C0 7D D7 7E  00 00 00 00  38 ED 3A 00  49 C2 F9 B7  .}.~....8.:.I...
    003AED10: 00 00 00 00  C0 7D D7 7E  EA 9E D4 7E  F4 7F 8B 7B  .....}.~...~...{
    003AED20: 01 00 00 00  A0 F6 3A 00  78 ED 3A 00  59 09 86 7B  ......:.x.:.Y..{
    003AED30: 80 D9 0B B8  00 00 00 00  F4 EF 3A 00  01 00 00 00  ..........:.....


    ------------------------------------------------------------------------------

    ======================================================================
    Hardware/Driver Information:
    Processor:              0x0
    Page Size:              4096
    Min App Address:        0x10000
    Max App Address:        0x7ffeffff
    Processor Mask:         0x1
    Number of Processors:   1
    Processor Type:         586
    Allocation Granularity: 65536
    Processor Level:        6
    Processor Revision:     2049
    Os Version:             5.1
    Os Service Pack:        4.0

    Percent memory used:    35
    Total physical memory:  1324453888
    Free Memory:            852004864
    Page file:              5198520320
    Total virtual memory:   2147352575

i tried this script (my ubuntu is in french) i pick that solution on french ubuntu tutorial :

  >   #!/bin/sh

    export WOW_PATH=~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/ # Chemin d'installation

    gksudo true || ( exit 1 ) # Valider le mot de passe
    sudo X :3 -ac -terminate &   # Lance sur un nouveau serveur X affichage 3
    cd "${WOW_PATH}"        # Cible le répertoire de WoW
    sleep 2           # Attend 2 secondes que le serveur soit prêt
    DISPLAY=:3 `which wine` WoW.exe -opengl # Lance WoW avec Wine et le paramètre OpenGL

i end up with black screen  =/

i tried that :
   
> 
    *       Entrez la commande regedit dans une console, une fenêtre hideuse apparaît avec une liste de dossiers qui commencent tous par HKEY.
        *      Allez dans HKEY_CURRENT_USER &#8594; Software &#8594; Wine.
        *      Cliquez-droit sur le dossier Wine &#8594; Nouvelle &#8594; Clé
        *      Nommez-le dossier (la clé) OpenGL
        *      Cliquez-droit sur le dossier OpenGL &#8594; Nouvelle &#8594; Valeur Chaîne
        *      Nommez cette chaîne DisabledExtensions puis double-cliquez dessus
        *      Remplissez le champs "Données de la valeur" avec GL_ARB_vertex_buffer_object

no result 

i never been able to make wow run so i dont have a config.wtf folder i only have those 2 folder :

> runonce.wtf

    SET readTOS "-1"

    SET readEULA "-1"

    SET readScanning "-1"

    SET readContest "-1"

    SET readTerminationWithoutNotice "-1"

    SET checkAddonVersion "1"

    SET installType "Retail"
    [B]SET gxApi "opengl"
    SET ffxDeath "0"
    SET ffxGlow "0"
    SET M2UsePixelShaders "1"
    SET M2UseShaders "0"
    SET UIFaster "2"[/B]

runonce_wlk.wtf

   >  SET readTOS "-1"

    SET readEULA "-1"

    SET readTerminationWithoutNotice "-1"

    SET readScanning "-1"

    SET readContest "-1"

    SET checkAddonVersion "1"

    SET locale "enUS"

    SET expansionMovie "1"

    SET movie "1"

    SET showToolsUI "1"
  [B]  SET gxApi "opengl"
    SET ffxDeath "0"
    SET ffxGlow "0"
    SET M2UsePixelShaders "1"
    SET M2UseShaders "0"
    SET UIFaster "2"[/B]

 for the ati drivers, i got envyng install, hoping it would get the best drivers (it wasnt working with default ubuntu drivers)

I'm new in the linux univers and i feel like i tried everything i could with what i know
thanks for the help ! 

oh yeah, i also set wine in virtual desktop and tried that command line :


    > WINEDEBUG="fixme-all" wine "C:\Program Files\World of Warcraft\WoW.exe"

---

### Post by NightMKoder on 2009-06-21
I smell ATI. [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) set offscreenrenderingmode to backbuffer.

---

