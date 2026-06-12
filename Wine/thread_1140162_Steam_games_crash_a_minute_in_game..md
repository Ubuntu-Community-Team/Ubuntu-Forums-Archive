---
title: "Steam games crash a minute in game."
date: 2009-04-27
forum: Wine
---

### Post by CodyK46 on 2009-04-27
a[HTML]<meta name="robots" content="noindex">
[/HTML]

---

### Post by Kareeser on 2009-04-27
Copy and Paste error messages

---

### Post by Cody the Linux Guru on 2009-04-27
You have to remember they just released 9.04 and there still might be some bugs to work out.
And steam games like Counter Strike are for me crashing to!

---

### Post by asdfoo on 2009-04-27
use wine 1.1.20 + 180.44 and report back.

---

### Post by CodyK46 on 2009-04-27
a

---

### Post by vitamind1 on 2009-04-28
I'm having a similar problem. I have Counter-Strike: Source installed with Crossover Games 7.2.0 which worked under 8.10, right after I upgraded to 9.04 I can open the game like usual, select a server and connect, right when it connects the game just crashes and I return to my desktop.

I'm using 64-bit ubuntu with the 180.44 driver.

Specs:
Asus G1S
2.4Ghz Core 2 Duo
4GB Ram
Nvidia 8600M GT

---

### Post by Kareeser on 2009-04-28
Add hl.exe to the compatability mode list. Select "Windows 98" for it.

---

### Post by andy71600 on 2009-04-30
> **Kareeser said:**
> Add hl.exe to the compatability mode list. Select "Windows 98" for it.
tried that... i'm getting crashes too.

---

### Post by andy71600 on 2009-04-30
Well, I have found out that CS only crashes on certain maps... Any custom maps work just fine, but I always get a crash after 1-2 minutes when playing de_dust2

---

### Post by 8Kuula on 2009-05-03
Same problem here, using 9.04 (64bit), wine 1.1.20, nvidia 180.44.

CSS and L4D crashes randomly, on L4D its good money to bet on mapchange where crash hapends, do not hapend everytime thou.

Allso did play L4D No Mercy Campaign up to chapter 4 start as single player, no crashes.
This left me feeling its something to do with how client talks to server, since single player game don't talk to server, or I was realy realy lucky :D

So did start CSS from console (wine hl2.exe -game cstrike), Did end with this:
```

...
fixme:d3d:fixed_get_input Unsupported input stream [usage=WINED3DDECLUSAGE_POSITION, usage_idx=1]
fixme:d3d:fixed_get_input Unsupported input stream [usage=WINED3DDECLUSAGE_NORMAL, usage_idx=1]
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x14e3f8) : stub
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x14e3f8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x14e3f8) : stub
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10385348)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10385348)
fixme:shdocvw:OleObject_Close (0x10385348)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x102e1f78)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x102e1f78)
fixme:shdocvw:OleObject_Close (0x102e1f78)->(1)
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on read access to 0x00000024 at address 0xd49b423 (thread 0037), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d49b423).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0d49b423 ESP:0032e5e8 EBP:00000002 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000020 EBX:00000000 ECX:40730188 EDX:07365780
 ESI:0d4aea18 EDI:00000090
Stack dump:
0x0032e5e8:  0d4aea18 0066364c 0d49b452 40730002
0x0032e5f8:  0d4aea18 0066364c 0d4aea18 40730006
0x0032e608:  0d49b7d5 40730006 0d4aea18 40730006
0x0032e618:  0d4aea3c 00000020 0d4aea18 0d4998da
0x0032e628:  40730001 ffffffff 00000000 00000009
0x0032e638:  0032ff08 0032e67c 1000753b 00000003
Backtrace:
=>0 0x0d49b423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)
0x0d49b423: movl    0x24(%ebx),%eax
Modules:
Module    Address            Debug info    Name (163 modules)
PE      330000-  366000    Deferred        tier0
PE      370000-  38e000    Deferred        vstdlib
PE      390000-  3e4000    Deferred        filesystem_steam
PE      3f0000-  3ff000    Deferred        unicode
PE      400000-  41c000    Deferred        hl2
PE     d240000- d33e000    Deferred        datamodel
PE     d450000- d48d000    Deferred        dmserializers
PE     d490000- d4b5000    Export          datacache
PE     d4c0000- d4d4000    Deferred        inputsystem
PE     d5f0000- d6a5000    Deferred        materialsystem
PE     d6b0000- d6c6000    Deferred        valve_avi
PE     d6d0000- d7a0000    Deferred        vguimatsurface
PE     d7a0000- d815000    Deferred        vgui2
PE     d820000- d834000    Deferred        steam_api
PE     d950000- d979000    Deferred        stdshader_dbg
PE     d980000- d9b5000    Deferred        stdshader_dx6
PE     d9c0000- d9e8000    Deferred        stdshader_dx7
PE     d9f0000- da33000    Deferred        stdshader_dx8
PE     da40000- da91000    Deferred        stdshader_dx9
PE     daa0000- dad6000    Deferred        soundemittersystem
PE     dae0000- dafb000    Deferred        scenefilecache
PE     e1c0000- e1e7000    Deferred        vaudio_speex
PE     f0f0000- f2d3000    Deferred        gameui
PE     f700000- fa07000    Deferred        steamclient
PE     fa10000- fa7b000    Deferred        vstdlib_s
PE     fa80000- fb26000    Deferred        tier0_s
PE     fc40000- fd6d000    Deferred        p2pvoice
PE    10000000-10030000    Deferred        launcher
PE    11210000-112db000    Deferred        serverbrowser
PE    11490000-114a0000    Deferred        vaudio_miles
PE    114a0000-11504000    Deferred        mss32
PE    20000000-205ef000    Deferred        engine
PE    21100000-211ad000    Deferred        mss32_s
PE    22000000-22642000    Deferred        server
PE    24000000-24476000    Deferred        client
PE    26000000-26138000    Deferred        vphysics
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2e000    Deferred        mssmp3.asi
PE    2a000000-2a0a8000    Deferred        shaderapidx9
PE    2c000000-2c3e3000    Deferred        studiorender
PE    30000000-302c1000    Deferred        steam
PE    60000000-60021000    Deferred        cserhelper
PE    628c0000-628d9000    Deferred        parsifal
ELF    7b800000-7b948000    Deferred        kernel32<elf>
  \-PE    7b820000-7b948000    \               kernel32
ELF    7bb9e000-7bbde000    Deferred        shdocvw<elf>
  \-PE    7bbb0000-7bbde000    \               shdocvw
ELF    7bbee000-7bbfd000    Deferred        libgcc_s.so.1
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c4a0000-7c4a7000    Deferred        libnss_dns.so.2
ELF    7c4a7000-7c4ab000    Deferred        libgpg-error.so.0
ELF    7c4ab000-7c514000    Deferred        libgcrypt.so.11
ELF    7c514000-7c526000    Deferred        libtasn1.so.3
ELF    7c526000-7c5c3000    Deferred        libgnutls.so.26
ELF    7c5e0000-7c607000    Deferred        netapi32<elf>
  \-PE    7c5f0000-7c607000    \               netapi32
ELF    7c607000-7c632000    Deferred        secur32<elf>
  \-PE    7c610000-7c632000    \               secur32
ELF    7c632000-7c6b5000    Deferred        crypt32<elf>
  \-PE    7c640000-7c6b5000    \               crypt32
ELF    7c6b5000-7c702000    Deferred        dsound<elf>
  \-PE    7c6c0000-7c702000    \               dsound
ELF    7cce1000-7dbf9000    Deferred        libglcore.so.1
ELF    7dbf9000-7dcb3000    Deferred        libgl.so.1
ELF    7dd83000-7dd87000    Deferred        iso8859-15.so
ELF    7ddb0000-7ddc6000    Deferred        winejoystick<elf>
  \-PE    7ddc0000-7ddc6000    \               winejoystick
ELF    7ddc6000-7dddc000    Deferred        psapi<elf>
  \-PE    7ddd0000-7dddc000    \               psapi
ELF    7dddc000-7de2b000    Deferred        dbghelp<elf>
  \-PE    7dde0000-7de2b000    \               dbghelp
ELF    7de2b000-7df50000    Deferred        wined3d<elf>
  \-PE    7de40000-7df50000    \               wined3d
ELF    7df50000-7df81000    Deferred        d3d9<elf>
  \-PE    7df60000-7df81000    \               d3d9
ELF    7df81000-7dfa4000    Deferred        mpr<elf>
  \-PE    7df90000-7dfa4000    \               mpr
ELF    7dfa4000-7dff6000    Deferred        wininet<elf>
  \-PE    7dfb0000-7dff6000    \               wininet
ELF    7dff6000-7e0dd000    Deferred        oleaut32<elf>
  \-PE    7e010000-7e0dd000    \               oleaut32
ELF    7e0dd000-7e107000    Deferred        msvfw32<elf>
  \-PE    7e0e0000-7e107000    \               msvfw32
ELF    7e107000-7e143000    Deferred        avifil32<elf>
  \-PE    7e110000-7e143000    \               avifil32
ELF    7e143000-7e158000    Deferred        midimap<elf>
  \-PE    7e150000-7e158000    \               midimap
ELF    7e158000-7e17e000    Deferred        msacm32<elf>
  \-PE    7e160000-7e17e000    \               msacm32
ELF    7e17e000-7e187000    Deferred        librt.so.1
ELF    7e187000-7e24f000    Deferred        libasound.so.2
ELF    7e24f000-7e252000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e254000-7e26c000    Deferred        msacm32<elf>
  \-PE    7e260000-7e26c000    \               msacm32
ELF    7e26c000-7e2a3000    Deferred        winealsa<elf>
  \-PE    7e280000-7e2a3000    \               winealsa
ELF    7e2a3000-7e336000    Deferred        winmm<elf>
  \-PE    7e2b0000-7e336000    \               winmm
ELF    7e3cc000-7e400000    Deferred        uxtheme<elf>
  \-PE    7e3d0000-7e400000    \               uxtheme
ELF    7e400000-7e414000    Deferred        lz32<elf>
  \-PE    7e410000-7e414000    \               lz32
ELF    7e414000-7e4dd000    Deferred        comctl32<elf>
  \-PE    7e420000-7e4dd000    \               comctl32
ELF    7e4dd000-7e53b000    Deferred        shlwapi<elf>
  \-PE    7e4f0000-7e53b000    \               shlwapi
ELF    7e53b000-7e6c5000    Deferred        shell32<elf>
  \-PE    7e550000-7e6c5000    \               shell32
ELF    7e6c5000-7e732000    Deferred        rpcrt4<elf>
  \-PE    7e6d0000-7e732000    \               rpcrt4
ELF    7e732000-7e82b000    Deferred        ole32<elf>
  \-PE    7e750000-7e82b000    \               ole32
ELF    7e82b000-7e841000    Deferred        libresolv.so.2
ELF    7e841000-7e843000    Deferred        libnvidia-tls.so.1
ELF    7e843000-7e85e000    Deferred        version<elf>
  \-PE    7e850000-7e85e000    \               version
ELF    7e85e000-7e87d000    Deferred        iphlpapi<elf>
  \-PE    7e860000-7e87d000    \               iphlpapi
ELF    7e87d000-7e8aa000    Deferred        ws2_32<elf>
  \-PE    7e890000-7e8aa000    \               ws2_32
ELF    7e8aa000-7e8b3000    Deferred        libxcursor.so.1
ELF    7e8b3000-7e8b8000    Deferred        libxfixes.so.3
ELF    7e8b8000-7e8bc000    Deferred        libxcomposite.so.1
ELF    7e8bc000-7e8c4000    Deferred        libxrandr.so.2
ELF    7e8c4000-7e8ce000    Deferred        libxrender.so.1
ELF    7e8ce000-7e8d4000    Deferred        libxxf86vm.so.1
ELF    7e8d4000-7e8d7000    Deferred        libxinerama.so.1
ELF    7e8d7000-7e8f8000    Deferred        imm32<elf>
  \-PE    7e8e0000-7e8f8000    \               imm32
ELF    7e8f8000-7e8fd000    Deferred        libxdmcp.so.6
ELF    7e8fd000-7e917000    Deferred        libxcb.so.1
ELF    7e917000-7e91b000    Deferred        libxau.so.6
ELF    7e91b000-7ea0a000    Deferred        libx11.so.6
ELF    7ea0a000-7ea1a000    Deferred        libxext.so.6
ELF    7ea1a000-7ea32000    Deferred        libice.so.6
ELF    7ea32000-7ea3b000    Deferred        libsm.so.6
ELF    7ea3b000-7ead7000    Deferred        winex11<elf>
  \-PE    7ea50000-7ead7000    \               winex11
ELF    7eb2e000-7eb55000    Deferred        libexpat.so.1
ELF    7eb55000-7eb82000    Deferred        libfontconfig.so.1
ELF    7eb82000-7eb9d000    Deferred        wsock32<elf>
  \-PE    7eb90000-7eb9d000    \               wsock32
ELF    7eb9f000-7ec16000    Deferred        libfreetype.so.6
ELF    7ec17000-7ec1c000    Deferred        libuuid.so.1
ELF    7ec33000-7ec89000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec89000    \               advapi32
ELF    7ec89000-7ed2a000    Deferred        gdi32<elf>
  \-PE    7eca0000-7ed2a000    \               gdi32
ELF    7ed2a000-7ee76000    Deferred        user32<elf>
  \-PE    7ed40000-7ee76000    \               user32
ELF    7ef98000-7efa4000    Deferred        libnss_files.so.2
ELF    7efa4000-7efbd000    Deferred        libnsl.so.1
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe7000-7effd000    Deferred        libz.so.1
ELF    f7c23000-f7c2e000    Deferred        libnss_nis.so.2
ELF    f7c2f000-f7c33000    Deferred        libdl.so.2
ELF    f7c33000-f7d96000    Deferred        libc.so.6
ELF    f7d97000-f7db0000    Deferred        libpthread.so.0
ELF    f7dc4000-f7dcd000    Deferred        libnss_compat.so.2
ELF    f7dcd000-f7f08000    Deferred        libwine.so.1
ELF    f7f0a000-f7f2b000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    0000000b    1
    00000043    1
    00000042    1
    00000041    1
    00000040    1
    0000003f    1
    0000003e    1
    0000003d    1
    0000003c    1
    0000003b    1
    00000033    0
    00000030    0
    0000002f    0
    0000002d    1
    0000002b    0
    00000029   15
    00000027    0
    00000026    0
    00000023    0
    00000021    0
    00000020    1
    0000001f    0
    0000001e    0
    0000001d    0
    0000001c    0
    0000001b    0
    0000001a    0
    00000019    0
    00000018    0
    00000009    0
0000000c 
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000016 
    00000017    0
00000036 (D) D:\Games\Steam\steamapps\[sensored my account name]\counter-strike source\hl2.exe
    0000002e    0
    00000022    0
    00000047    0
    00000046   15
    00000045    2
    00000044    0
    0000003a    0
    00000039    0
    00000038    2
    00000037    0 <==
Backtrace:
=>0 0x0d49b423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```In hope that helps some geek :P

Did try on both L4D and CSS:
 - did uninstall whole pulseaudio (apt-get purge pulseaudio) -> still crash
 - without sound (started with -nosound option) -> crash (CSS only tested).
 - diffirent video settings -> crashing, no use.

hope this helps even little :)

---

### Post by asdfoo on 2009-05-03
I only play css on cs_office (24/7 servers), 180.44 gf8, probably only experience a crash once a week.

---

### Post by dino7 on 2009-07-31
[SIZE=1]Any news with this issue?

I am new in both this forum and in the Linux world. I just found this post while looking trough google and I have the same problem. Wathever steam game I play, it crashes after just 1 or 2 minute in game. It just bring me back to the desktop without any error message. I thought I would post the log from the console after it has crashed.

```
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
[/SIZE]   [SIZE=1][COLOR=Red]E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory[/COLOR][/SIZE][SIZE=1]
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
E: memblock.c: [/SIZE][SIZE=1][COLOR=Red]Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.[/COLOR][/SIZE][SIZE=1]
wine: Assertion failed at address 0xf7f6e430 (thread 00c5), starting debugger...
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x13d10bb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
Unhandled exception: assertion failed in 32-bit code (0xf7f6e430).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f7f6e430 ESP:751ed688 EBP:751ed6a0 EFLAGS:00000296(   - 00      -ISAP1)
 EAX:00000000 EBX:00001eee ECX:00001f0e EDX:00000006
 ESI:74cb4948 EDI:f7ddeff4
Stack dump:
0x751ed688:  751ed6a0 00000006 00001f0e f7cab9a0
0x751ed698:  f7ddeff4 751ed7c0 751ed7c8 f7cad368
0x751ed6a8:  00000006 751ed740 00000000 7e17f790
0x751ed6b8:  751ed6f8 7e187fb4 7e19a3c8 751ed7b8
0x751ed6c8:  7ffb0000 7e187da1 00000000 751ed810
0x751ed6d8:  751ed7b8 00000053 006c10a4 626d656d
Backtrace:
=>1 0xf7f6e430 (0x751ed6a0)
  2 0xf7cad368 abort+0x188() in libc.so.6 (0x751ed7c8)
  3 0x7e1736e0 in libpulse.so.0 (+0x376e0) (0x751ed7f8)
  4 0x7e15b3f2 pa_stream_peek+0xe2() in libpulse.so.0 (0x751ed838)
  5 0x7e294fd8 _init+0x9e0() in libasound_module_pcm_pulse.so (0x751ed888)
  6 0x7e24baa1 in libasound.so.2 (+0x90aa1) (0x751ed8b8)
  7 0x7e206cd8 in libasound.so.2 (+0x4bcd8) (0x751ed8e8)
  8 0x7e24bd05 in libasound.so.2 (+0x90d05) (0x751ed948)
  9 0x7e201104 snd_pcm_readi+0x54() in libasound.so.2 (0x751ed978)
  10 0x7e2c26d8 in winealsa (+0x226d8) (0x751eda18)
  11 0x7bc6d46e call_thread_entry_point+0xe() in ntdll (0x751eda28)
  12 0x7bc6ea92 in ntdll (+0x5ea92) (0x751edac8)
  13 0x7bc6ec8d in ntdll (+0x5ec8d) (0x751ee3b8)
  14 0xf7dea4ff start_thread+0xbf() in libpthread.so.0 (0x751ee4b8)
  15 0xf7d66b9e __clone+0x5e() in libc.so.6 (0x00000000)
0xf7f6e430: popl    %ebp
Modules:
Module    Address            Debug info    Name (230 modules)
PE      330000-  366000    Deferred        tier0
PE      370000-  38e000    Deferred        vstdlib
PE      390000-  3e4000    Deferred        filesystem_steam
PE      3f0000-  3ff000    Deferred        unicode
PE      400000-  41c000    Deferred        hl2
PE     d0b0000- d1ae000    Deferred        datamodel
PE     d2c0000- d2fd000    Deferred        dmserializers
PE     d300000- d325000    Deferred        datacache
PE     d330000- d345000    Deferred        inphttp://ubuntuforums.org/showthread.php?t=1167746&page=2utsystem
PE     d460000- d515000    Deferred        materialsystem
PE     d520000- d536000    Deferred        valve_avi
PE     d540000- d610000    Deferred        vguimatsurface
PE     d610000- d685000    Deferred        vgui2
PE     d690000- d6a4000    Deferred        steam_api
PE     d8d0000- d8f9000    Deferred        stdshader_dbg
PE     d900000- d935000    Deferred        stdshader_dx6
PE     d940000- d968000    Deferred        stdshader_dx7
PE     d970000- d9b3000    Deferred        stdshader_dx8
PE     d9c0000- da11000    Deferred        stdshader_dx9
PE     da20000- da56000    Deferred        soundemittersystem
PE     da60000- da7b000    Deferred        scenefilecache
PE     e920000- ec79000    Deferred        steamclient
PE     ec80000- ecf0000    Deferred        vstdlib_s
PE     ecf0000- ed99000    Deferred        tier0_s
PE     efc0000- f1a7000    Deferred        gameui
PE     ffb0000- ffc0000    Deferred        vaudio_miles
PE    10000000-10030000    Deferred        launcher
PE    10f90000-1105b000    Deferred        serverbrowser
PE    114c0000-114e7000    Deferred        vaudio_speex
PE    114f0000-114f6000    Deferred        xpcom
PE    11500000-11569000    Deferred        xpcom_core
PE    11570000-11597000    Deferred        nspr4
PE    115a0000-115a7000    Deferred        plc4
PE    11ae0000-11ae6000    Deferred        plds4
PE    11af0000-11aff000    Deferred        jsd3250
PE    11b00000-11b11000    Deferred        mozz
PE    11b20000-11b26000    Deferred        xpistub
PE    13720000-13791000    Deferred        js3250
PE    137a0000-137d5000    Deferred        xpc3250
PE    137e0000-13800000    Deferred        ssl3
PE    13800000-13813000    Deferred        jsj3250
PE    1fc60000-1fcbb000    Deferred        nss3
PE    1fcc0000-1fcff000    Deferred        softokn3
PE    1fd00000-1fd1a000    Deferred        smime3
PE    1fd20000-1fd26000    Deferred        mozctlx
PE    1fd30000-1fd6e000    Deferred        nssckbi
PE    1fd70000-1fda1000    Deferred        freebl3
PE    1fdb0000-1fdc6000    Deferred        gkgfx
PE    1fdd0000-1fde4000    Deferred        xpcom_compat
PE    1fdf0000-1fe6d000    Deferred        necko
PE    1fe70000-1fe7c000    Deferred        xppref32
PE    1ff90000-1ffbe000    Deferred        i18n
PE    1ffc0000-1ffdf000    Deferred        embedcomponents
PE    1ffe0000-1ffef000    Deferred        caps
PE    1fff0000-1fffc000    Deferred        typeaheadfind
PE    20000000-205ef000    Deferred        engine
PE    205f0000-20889000    Deferred        gklayout
PE    20890000-208b7000    Deferred        imglib2
PE    208c0000-208db000    Deferred        rdf
PE    208e0000-20918000    Deferred        appcomps
PE    20920000-20930000    Deferred        appshell
PE    20930000-2093f000    Deferred        profile
PE    20940000-20947000    Deferred        xpcom_compat_c
PE    20950000-2095e000    Deferred        webbrwsr
PE    20960000-20985000    Deferred        gkwidget
PE    20990000-209b4000    Deferred        gkgfxwin
PE    209c0000-209ec000    Deferred        docshell
PE    209f0000-209f8000    Deferred        pipboot
PE    20a00000-20a0c000    Deferred        oji
PE    20a10000-20ace000    Deferred        uconv
PE    20ad0000-20ae0000    Deferred        chrome
PE    20ae0000-20b19000    Deferred        gkparser
PE    20c30000-20c3d000    Deferred        jar50
PE    20c40000-20c47000    Deferred        txmgr
PE    21100000-21164000    Deferred        mss32
PE    22000000-22642000    Deferred        server
PE    24000000-24476000    Deferred        client
PE    26000000-26138000    Deferred        vphysics
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2e000    Deferred        mssmp3.asi
PE    2a000000-2a0a8000    Deferred        shaderapidx9
PE    2c000000-2c3e3000    Deferred        studiorender
PE    30000000-302c2000    Deferred        steam
PE    60000000-60021000    Deferred        cserhelper
PE    628c0000-628d9000    Deferred        parsifal
ELF    6c1d9000-6c27a000    Deferred        mshtml<elf>
  \-PE    6c1e0000-6c27a000    \               mshtml
ELF    6c27a000-6c2b9000    Deferred        urlmon<elf>
  \-PE    6c280000-6c2b9000    \               urlmon
ELF    6fc02000-6fc06000    Deferred        libgpg-error.so.0
ELF    6fc06000-6fc6f000    Deferred        libgcrypt.so.11
ELF    6fc6f000-6fc81000    Deferred        libtasn1.so.3
ELF    6fc81000-6fca5000    Deferred        libk5crypto.so.3
ELF    6fca5000-6fd37000    Deferred        libkrb5.so.3
ELF    6fd37000-6fdd4000    Deferred        libgnutls.so.26
ELF    6fdd4000-6fdff000    Deferred        libgssapi_krb5.so.2
ELF    6fdff000-6fe36000    Deferred        libcups.so.2
ELF    6fe36000-6fee4000    Deferred        comdlg32<elf>
  \-PE    6fe40000-6fee4000    \               comdlg32
ELF    6fee4000-6ff1b000    Deferred        winspool<elf>
  \-PE    6fef0000-6ff1b000    \               winspool
ELF    7024e000-702ba000    Deferred        msvcrt<elf>
  \-PE    70260000-702ba000    \               msvcrt
ELF    75703000-75707000    Deferred        libkeyutils.so.1
ELF    75707000-75710000    Deferred        libkrb5support.so.0
ELF    75710000-75714000    Deferred        libcom_err.so.2
ELF    75714000-7572b000    Deferred        msimtf<elf>
  \-PE    75720000-7572b000    \               msimtf
ELF    757bd000-757cc000    Deferred        libgcc_s.so.1
ELF    799ef000-79a3b000    Deferred        dsound<elf>
  \-PE    79a00000-79a3b000    \               dsound
ELF    79e3e000-79e7a000    Deferred        shdocvw<elf>
  \-PE    79e50000-79e7a000    \               shdocvw
ELF    7af8c000-7aff5000    Deferred        crypt32<elf>
  \-PE    7afa0000-7aff5000    \               crypt32
ELF    7b800000-7b93c000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bc00000-7bca7000    Export          ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c04e000-7c055000    Deferred        libnss_dns.so.2
ELF    7c055000-7c07c000    Deferred        netapi32<elf>
  \-PE    7c060000-7c07c000    \               netapi32
ELF    7c10a000-7c132000    Deferred        secur32<elf>
  \-PE    7c110000-7c132000    \               secur32
ELF    7c17c000-7c194000    Deferred        mcicda<elf>
  \-PE    7c180000-7c194000    \               mcicda
ELF    7c1b5000-7d0cd000    Deferred        libglcore.so.1
ELF    7d0cd000-7d187000    Deferred        libgl.so.1
ELF    7d2af000-7d2fb000    Deferred        dbghelp<elf>
  \-PE    7d2c0000-7d2fb000    \               dbghelp
ELF    7d40c000-7d522000    Deferred        wined3d<elf>
  \-PE    7d420000-7d522000    \               wined3d
ELF    7d70f000-7d712000    Deferred        libnss_mdns4_minimal.so.2
ELF    7d71a000-7d72f000    Deferred        winejoystick<elf>
  \-PE    7d720000-7d72f000    \               winejoystick
ELF    7d72f000-7d745000    Deferred        psapi<elf>
  \-PE    7d730000-7d745000    \               psapi
ELF    7d745000-7d776000    Deferred        d3d9<elf>
  \-PE    7d750000-7d776000    \               d3d9
ELF    7d776000-7d799000    Deferred        mpr<elf>
  \-PE    7d780000-7d799000    \               mpr
ELF    7d799000-7d7e9000    Deferred        wininet<elf>
  \-PE    7d7a0000-7d7e9000    \               wininet
ELF    7d7e9000-7d88f000    Deferred        oleaut32<elf>
  \-PE    7d800000-7d88f000    \               oleaut32
ELF    7d88f000-7d8b8000    Deferred        msvfw32<elf>
  \-PE    7d8a0000-7d8b8000    \               msvfw32
ELF    7d8b8000-7d8f4000    Deferred        avifil32<elf>
  \-PE    7d8c0000-7d8f4000    \               avifil32
ELF    7d8f4000-7d91c000    Deferred        msacm32<elf>
  \-PE    7d900000-7d91c000    \               msacm32
ELF    7d91c000-7d935000    Deferred        msacm32<elf>
  \-PE    7d920000-7d935000    \               msacm32
ELF    7e136000-7e13c000    Deferred        libattr.so.1
ELF    7e13c000-7e19b000    Export          libpulse.so.0
ELF    7e19d000-7e1b2000    Deferred        midimap<elf>
  \-PE    7e1a0000-7e1b2000    \               midimap
ELF    7e1b2000-7e1bb000    Deferred        librt.so.1
ELF    7e1bb000-7e283000    Export          libasound.so.2
ELF    7e287000-7e28e000    Deferred        libgdbm.so.3
ELF    7e28e000-7e293000    Deferred        libcap.so.2
ELF    7e293000-7e29a000    Export          libasound_module_pcm_pulse.so
ELF    7e29a000-7e2d1000    Export          winealsa<elf>
  \-PE    7e2a0000-7e2d1000    \               winealsa
ELF    7e2d1000-7e365000    Deferred        winmm<elf>
  \-PE    7e2e0000-7e365000    \               winmm
ELF    7e4ba000-7e4ed000    Deferred        uxtheme<elf>
  \-PE    7e4c0000-7e4ed000    \               uxtheme
ELF    7e4ed000-7e508000    Deferred        version<elf>
  \-PE    7e4f0000-7e508000    \               version
ELF    7e508000-7e5cd000    Deferred        comctl32<elf>
  \-PE    7e510000-7e5cd000    \               comctl32
ELF    7e5cd000-7e628000    Deferred        shlwapi<elf>
  \-PE    7e5e0000-7e628000    \               shlwapi
ELF    7e628000-7e73d000    Deferred        shell32<elf>
  \-PE    7e640000-7e73d000    \               shell32
ELF    7e73d000-7e7a0000    Deferred        rpcrt4<elf>
  \-PE    7e750000-7e7a0000    \               rpcrt4
ELF    7e7a0000-7e846000    Deferred        ole32<elf>
  \-PE    7e7b0000-7e846000    \               ole32
ELF    7e846000-7e85c000    Deferred        libresolv.so.2
ELF    7e85c000-7e85e000    Deferred        libnvidia-tls.so.1
ELF    7e873000-7e892000    Deferred        iphlpapi<elf>
  \-PE    7e880000-7e892000    \               iphlpapi
ELF    7e892000-7e8bf000    Deferred        ws2_32<elf>
  \-PE    7e8a0000-7e8bf000    \               ws2_32
ELF    7e8bf000-7e8da000    Deferred        wsock32<elf>
  \-PE    7e8c0000-7e8da000    \               wsock32
ELF    7e8da000-7e8e3000    Deferred        libxcursor.so.1
ELF    7e8e3000-7e8e8000    Deferred        libxfixes.so.3
ELF    7e8e8000-7e8ec000    Deferred        libxcomposite.so.1
ELF    7e8ec000-7e8f4000    Deferred        libxrandr.so.2
ELF    7e8f4000-7e8fe000    Deferred        libxrender.so.1
ELF    7e8fe000-7e91f000    Deferred        imm32<elf>
  \-PE    7e900000-7e91f000    \               imm32
ELF    7e91f000-7e924000    Deferred        libxdmcp.so.6
ELF    7e924000-7e93e000    Deferred        libxcb.so.1
ELF    7e93e000-7e942000    Deferred        libxau.so.6
ELF    7e942000-7e947000    Deferred        libuuid.so.1
ELF    7e947000-7ea36000    Deferred        libx11.so.6
ELF    7ea36000-7ea46000    Deferred        libxext.so.6
ELF    7ea46000-7ea4c000    Deferred        libxxf86vm.so.1
ELF    7ea4c000-7ea64000    Deferred        libice.so.6
ELF    7ea64000-7ea6d000    Deferred        libsm.so.6
ELF    7ea6d000-7ea82000    Deferred        lz32<elf>
  \-PE    7ea70000-7ea82000    \               lz32
ELF    7ea84000-7eb1f000    Deferred        winex11<elf>
  \-PE    7ea90000-7eb1f000    \               winex11
ELF    7eb48000-7eb6f000    Deferred        libexpat.so.1
ELF    7eb6f000-7eb9c000    Deferred        libfontconfig.so.1
ELF    7eb9c000-7ec13000    Deferred        libfreetype.so.6
ELF    7ec13000-7ec16000    Deferred        libxinerama.so.1
ELF    7ec2a000-7ec7d000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec7d000    \               advapi32
ELF    7ec7d000-7ed1d000    Deferred        gdi32<elf>
  \-PE    7ec90000-7ed1d000    \               gdi32
ELF    7ed1d000-7ee69000    Deferred        user32<elf>
  \-PE    7ed40000-7ee69000    \               user32
ELF    7ef93000-7ef9f000    Deferred        libnss_files.so.2
ELF    7ef9f000-7efaa000    Deferred        libnss_nis.so.2
ELF    7efaa000-7efc3000    Deferred        libnsl.so.1
ELF    7efc3000-7efe9000    Deferred        libm.so.6
ELF    7efe9000-7efff000    Deferred        libz.so.1
ELF    f7c72000-f7c7b000    Deferred        libnss_compat.so.2
ELF    f7c7c000-f7c80000    Deferred        libdl.so.2
ELF    f7c80000-f7de3000    Export          libc.so.6
ELF    f7de4000-f7dfd000    Export          libpthread.so.0
ELF    f7e14000-f7f4b000    Deferred        libwine.so.1
ELF    f7f4d000-f7f6e000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000016    0
    00000015    0
    00000011    0
    00000010    0
0000004b 
    000000bf    1
    000000b5    1
    00000083    0
    0000000b    0
    00000028    1
    00000045    1
    00000043    1
    00000044    1
    0000002b    1
    0000002e    1
    00000051    1
    00000022    1
    0000004d    0
    00000037    0
    0000005d    0
    0000002f    0
    0000003b    0
    00000039    0
    00000063    1
    00000014    0
    00000023   15
    0000002a    0
    0000004f    0
    0000005c    0
    00000030    0
    00000013    0
    00000056    0
    0000002c    0
    0000005b    0
    0000003a    0
    00000020    0
    0000004a    0
0000005e 
    00000061    0
000000b0 (D) C:\Program Files\Steam\steamapps\*****r@msn.com\counter-strike source\hl2.exe
    000000cb    0
    000000ca    0
    000000c9    0
    000000c8    0
    000000c7    0
    000000c6    0
    000000c5   15 <==
    000000c0    0
    000000bb    0
    000000ba   15
    000000b9   15
    000000b7    2
    000000b6    0
    000000b4    0
    000000b3    0
    000000b2    2
    000000b1    0
Backtrace:
=>1 0xf7f6e430 (0x751ed6a0)
  2 0xf7cad368 abort+0x188() in libc.so.6 (0x751ed7c8)
  3 0x7e1736e0 in libpulse.so.0 (+0x376e0) (0x751ed7f8)
  4 0x7e15b3f2 pa_stream_peek+0xe2() in libpulse.so.0 (0x751ed838)
  5 0x7e294fd8 _init+0x9e0() in libasound_module_pcm_pulse.so (0x751ed888)
  6 0x7e24baa1 in libasound.so.2 (+0x90aa1) (0x751ed8b8)
  7 0x7e206cd8 in libasound.so.2 (+0x4bcd8) (0x751ed8e8)
  8 0x7e24bd05 in libasound.so.2 (+0x90d05) (0x751ed948)
  9 0x7e201104 snd_pcm_readi+0x54() in libasound.so.2 (0x751ed978)
  10 0x7e2c26d8 in winealsa (+0x226d8) (0x751eda18)
  11 0x7bc6d46e call_thread_entry_point+0xe() in ntdll (0x751eda28)
  12 0x7bc6ea92 in ntdll (+0x5ea92) (0x751edac8)
  13 0x7bc6ec8d in ntdll (+0x5ec8d) (0x751ee3b8)
  14 0xf7dea4ff start_thread+0xbf() in libpthread.so.0 (0x751ee4b8)
  15 0xf7d66b9e __clone+0x5e() in libc.so.6 (0x00000000)
Aborted

```I am on a HP Pavillion dv6600 laptop. It has a NVIDIA GeForce 8400M GS.

I run the latest Ubuntu version (I've install it 3 days ago...) and the latest version of Wine aswell. 

A friend told me I would be able to run steam games without a problem on Linux... I am a bit disapointed ^^ But it seemed to work fine with the older version of Ubuntu... so there got to be a solution. Hope you will be able to convince me staying with linux by solving this problem.

Sorry for my bad english.

Thanks in advance. 

Cheers.

[SIZE=3]
Edit : Never mind I found the solution. For those who are interested here is the link : [http://ubuntuforums.org/showthread.php?t=1167746&page=2](http://ubuntuforums.org/showthread.php?t=1167746&page=2)[/SIZE]
[/SIZE]

---

