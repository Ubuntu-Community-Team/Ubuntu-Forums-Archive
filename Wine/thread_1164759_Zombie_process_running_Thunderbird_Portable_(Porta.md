---
title: "Zombie process running Thunderbird Portable (PortableApps.com) in Wine"
date: 2009-05-20
forum: Wine
---

### Post by 7F0C147C on 2009-05-20
**Overview:**[LIST]
[*]Ubuntu 9.04
[*]Wine 1.0.1
[*]Default Wine settings used
[*]No applications installed in Wine
[*]Important Terminal Output
```
wine: Unhandled page fault on write access to 0x0000002c at address 0x5221af (thread 0037), starting debugger...
Unhandled exception: page fault on write access to 0x0000002c in 32-bit code (0x005221af)
```
[/LIST]

I started a thread at [PortableApps.com]("http://portableapps.com/node/19331"), and was recommended to post it here. I installed Ubuntu (9.04) onto my laptop, HP nw8440. Wine (1.0.1) was able to run some of my portable applications on my flash drive from PortableApps.com. The important programs, Thunderbird Portable and Keepass, worked.

I run TBP this morning and it freezes at the program start. In the System Monitor, it labels thunderbird.exe (a called process of ThunderbirdPortable.exe) as "Zombie" with waiting channel "do_exit". It ceases to function after moving through the menus five items, no matter how slow. Five clicks and it is done.

Addon in TB is Adblock. I have two email accounts, both Gmail, and RSS feeds. 

Full terminal output:
```
augi@compy:/media/CRUZER4GB/PortableApps/ThunderbirdPortable$ ls
App Data help.html Other ThunderbirdPortable.exe
augi@compy:/media/CRUZER4GB/PortableApps/ThunderbirdPortable$ wine ThunderbirdPortable.exe
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:CheckTokenMembership ((nil) 0x2550860 0x32fb40) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x2550860 0x32fb40) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x2550860 0x32fb40) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x2550860 0x32fb40) stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d26b9e8, overlapped 0x7d26b9cc): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xc186a4)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SetProcessDPIAware stub!
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:imm:ImmReleaseContext (0x20204, 0x13d8a0): stub
fixme:imm:ImmGetOpenStatus (0x13d8a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13d8a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13d8a0): semi-stub
wine: Unhandled page fault on write access to 0x0000002c at address 0x5221af (thread 0037), starting debugger...
Unhandled exception: page fault on write access to 0x0000002c in 32-bit code (0x005221af).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:005221af ESP:0033488c EBP:003348a0 EFLAGS:00210246( - 00 -RIZP1)
EAX:0000002c EBX:00110000 ECX:00000000 EDX:00000001
ESI:0033aa54 EDI:0033e920
Stack dump:
0x0033488c: 000001ca 0033a994 0033a8d8 0000000f
0x0033489c: 00110000 0033e93c 005219ee 0000000e
0x003348ac: 000001ca 0033e8dc 0033e8e0 00000000
0x003348bc: 00000040 025249e0 00000000 00000000
0x003348cc: 003348d0 01010100 00000001 00000000
0x003348dc: 00000000 00000000 00000000 00000000
Backtrace:
=>1 0x005221af in thunderbird (+0x1221af) (0x003348a0)
2 0x005219ee in thunderbird (+0x1219ee) (0x0033e93c)
3 0x00522560 in thunderbird (+0x122560) (0x0033e978)
4 0x0052376e in thunderbird (+0x12376e) (0x0033e9c0)
5 0x005249bc in thunderbird (+0x1249bc) (0x0033e9f4)
6 0x0052570d in thunderbird (+0x12570d) (0x0033ea28)
7 0x0051adf6 in thunderbird (+0x11adf6) (0x0033ea58)
8 0x00a15f0a in thunderbird (+0x615f0a) (0x0033ea80)
9 0x00519774 in thunderbird (+0x119774) (0x0033ea9c)
10 0x00a15de0 in thunderbird (+0x615de0) (0x0033ed34)
11 0x006da0ac in thunderbird (+0x2da0ac) (0x0033ee00)
12 0x006d9b2f in thunderbird (+0x2d9b2f) (0x0033eec4)
13 0x006d965f in thunderbird (+0x2d965f) (0x0033ef58)
14 0x00562055 in thunderbird (+0x162055) (0x0033ef88)
15 0x0063afb4 in thunderbird (+0x23afb4) (0x0033efa4)
16 0x005c9be4 in thunderbird (+0x1c9be4) (0x0033efec)
17 0x005c9932 in thunderbird (+0x1c9932) (0x0033f0a0)
18 0x005c9391 in thunderbird (+0x1c9391) (0x0033f1a4)
19 0x005ca74b in thunderbird (+0x1ca74b) (0x0033f210)
20 0x0063b62e in thunderbird (+0x23b62e) (0x0033f22c)
21 0x00534fe3 in thunderbird (+0x134fe3) (0x0033f31c)
22 0x00537e4d in thunderbird (+0x137e4d) (0x0033f5a0)
23 0x0053538d in thunderbird (+0x13538d) (0x0033f5d4)
24 0x7ec7e29a WINPROC_wrapper+0x1a() in user32 (0x0033f604)
25 0x7ec7e6ea WINPROC_wrapper+0x46a() in user32 (0x0033f644)
26 0x7ec839fd in user32 (+0xb39fd) (0x0033f684)
27 0x7ec43f97 in user32 (+0x73f97) (0x0033f6e4)
28 0x7ec48ec5 in user32 (+0x78ec5) (0x0033f744)
29 0x7ec493dc SendMessageW+0x4c() in user32 (0x0033f784)
30 0x7ec5563e RedrawWindow+0x20e() in user32 (0x0033f7e4)
31 0x7ec56ba5 UpdateWindow+0x35() in user32 (0x0033f804)
32 0x00537b01 in thunderbird (+0x137b01) (0x0033f840)
33 0x7ec73099 in user32 (+0xa3099) (0x0033f870)
34 0x7ec730e4 EnumChildWindows+0x34() in user32 (0x0033f890)
35 0x00537b79 in thunderbird (+0x137b79) (0x0033f8b8)
36 0x005388c1 in thunderbird (+0x1388c1) (0x0033fb38)
37 0x0053538d in thunderbird (+0x13538d) (0x0033fb6c)
38 0x7ec7e29a WINPROC_wrapper+0x1a() in user32 (0x0033fb9c)
39 0x7ec7e6ea WINPROC_wrapper+0x46a() in user32 (0x0033fbdc)
40 0x7ec839fd in user32 (+0xb39fd) (0x0033fc1c)
41 0x7ec440b6 DispatchMessageW+0x96() in user32 (0x0033fc5c)
42 0x0054136f in thunderbird (+0x14136f) (0x0033fcb0)
43 0x007e2b04 in thunderbird (+0x3e2b04) (0x0033fe4c)
44 0x00401012 in thunderbird (+0x1012) (0x0033ff08)
45 0x7b878828 in kernel32 (+0x58828) (0x0033ffe8)
46 0xb7f12d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x005221af: orl %edx,0x0(%eax)
Modules:
Module Address Debug info Name (128 modules)
PE 400000- c31000 Export thunderbird
PE 10000000-10022000 Deferred calbscmp
PE 60010000-60022000 Deferred jar50
PE 60040000-6004a000 Deferred myspell
PE 60050000-6005e000 Deferred spellchk
PE 60090000-600c1000 Deferred freebl3
PE 600d0000-60142000 Deferred js3250
PE 60170000-60193000 Deferred nsldap32v50
PE 601a0000-601a6000 Deferred nsldappr32v50
PE 601b0000-601d7000 Deferred nspr4
PE 601e0000-6023b000 Deferred nss3
PE 60240000-60288000 Deferred nssckbi
PE 60290000-60297000 Deferred plc4
PE 602a0000-602a6000 Deferred plds4
PE 602b0000-602ca000 Deferred smime3
PE 602d0000-6030f000 Deferred softokn3
PE 60310000-60331000 Deferred ssl3
PE 60350000-60364000 Deferred xpcom_compat
PE 60370000-603d9000 Deferred xpcom_core
ELF 7b800000-7b93d000 Export kernel32<elf>
\-PE 7b820000-7b93d000 \ kernel32
ELF 7bc00000-7bca7000 Deferred ntdll<elf>
\-PE 7bc10000-7bca7000 \ ntdll
ELF 7bf00000-7bf04000 Deferred <wine-loader>
ELF 7c688000-7c68b000 Deferred libnss_mdns4_minimal.so.2
ELF 7cac3000-7cad7000 Deferred msimg32<elf>
\-PE 7cad0000-7cad7000 \ msimg32
ELF 7d573000-7d58a000 Deferred msimtf<elf>
\-PE 7d580000-7d58a000 \ msimtf
ELF 7d58a000-7d58e000 Deferred libgpg-error.so.0
ELF 7d58e000-7d5f7000 Deferred libgcrypt.so.11
ELF 7d5f7000-7d609000 Deferred libtasn1.so.3
ELF 7d609000-7d60d000 Deferred libkeyutils.so.1
ELF 7d60d000-7d616000 Deferred libkrb5support.so.0
ELF 7d616000-7d63a000 Deferred libk5crypto.so.3
ELF 7d63a000-7d6cc000 Deferred libkrb5.so.3
ELF 7d6cc000-7d769000 Deferred libgnutls.so.26
ELF 7d769000-7d794000 Deferred libgssapi_krb5.so.2
ELF 7d794000-7d7cb000 Deferred libcups.so.2
ELF 7d7d4000-7d7db000 Deferred libnss_dns.so.2
ELF 7d827000-7d85a000 Deferred uxtheme<elf>
\-PE 7d830000-7d85a000 \ uxtheme
ELF 7d85a000-7d86f000 Deferred midimap<elf>
\-PE 7d860000-7d86f000 \ midimap
ELF 7d86f000-7d897000 Deferred msacm32<elf>
\-PE 7d880000-7d897000 \ msacm32
ELF 7d897000-7d8b0000 Deferred msacm32<elf>
\-PE 7d8a0000-7d8b0000 \ msacm32
ELF 7e0b1000-7e0b7000 Deferred libattr.so.1
ELF 7e0b7000-7e116000 Deferred libpulse.so.0
ELF 7e122000-7e126000 Deferred libcom_err.so.2
ELF 7e126000-7e1ee000 Deferred libasound.so.2
ELF 7e1f0000-7e1f7000 Deferred libgdbm.so.3
ELF 7e1f7000-7e1fe000 Deferred libasound_module_pcm_pulse.so
ELF 7e1fe000-7e235000 Deferred winealsa<elf>
\-PE 7e210000-7e235000 \ winealsa
ELF 7e235000-7e23e000 Deferred libxcursor.so.1
ELF 7e23e000-7e243000 Deferred libxfixes.so.3
ELF 7e243000-7e247000 Deferred libxcomposite.so.1
ELF 7e247000-7e24f000 Deferred libxrandr.so.2
ELF 7e24f000-7e259000 Deferred libxrender.so.1
ELF 7e259000-7e25c000 Deferred libxinerama.so.1
ELF 7e25c000-7e27d000 Deferred imm32<elf>
\-PE 7e260000-7e27d000 \ imm32
ELF 7e27d000-7e282000 Deferred libxdmcp.so.6
ELF 7e282000-7e29c000 Deferred libxcb.so.1
ELF 7e29c000-7e2a0000 Deferred libxau.so.6
ELF 7e2a0000-7e38f000 Deferred libx11.so.6
ELF 7e38f000-7e39f000 Deferred libxext.so.6
ELF 7e39f000-7e3a5000 Deferred libxxf86vm.so.1
ELF 7e3a5000-7e3bd000 Deferred libice.so.6
ELF 7e3bd000-7e3c6000 Deferred libsm.so.6
ELF 7e3c6000-7e3cb000 Deferred libcap.so.2
ELF 7e3cb000-7e3d4000 Deferred librt.so.1
ELF 7e3d6000-7e471000 Deferred winex11<elf>
\-PE 7e3e0000-7e471000 \ winex11
ELF 7e4bd000-7e4e4000 Deferred libexpat.so.1
ELF 7e4e4000-7e511000 Deferred libfontconfig.so.1
ELF 7e521000-7e537000 Deferred libz.so.1
ELF 7e537000-7e5ae000 Deferred libfreetype.so.6
ELF 7e5ae000-7e654000 Deferred oleaut32<elf>
\-PE 7e5c0000-7e654000 \ oleaut32
ELF 7e654000-7e68b000 Deferred winspool<elf>
\-PE 7e660000-7e68b000 \ winspool
ELF 7e68b000-7e739000 Deferred comdlg32<elf>
\-PE 7e690000-7e739000 \ comdlg32
ELF 7e739000-7e74e000 Deferred lz32<elf>
\-PE 7e740000-7e74e000 \ lz32
ELF 7e74e000-7e769000 Deferred version<elf>
\-PE 7e750000-7e769000 \ version
ELF 7e769000-7e7cc000 Deferred rpcrt4<elf>
\-PE 7e780000-7e7cc000 \ rpcrt4
ELF 7e7cc000-7e872000 Deferred ole32<elf>
\-PE 7e7e0000-7e872000 \ ole32
ELF 7e872000-7e937000 Deferred comctl32<elf>
\-PE 7e880000-7e937000 \ comctl32
ELF 7e937000-7e992000 Deferred shlwapi<elf>
\-PE 7e940000-7e992000 \ shlwapi
ELF 7e992000-7eaa6000 Deferred shell32<elf>
\-PE 7e9a0000-7eaa6000 \ shell32
ELF 7eaa6000-7eb12000 Deferred msvcrt<elf>
\-PE 7eac0000-7eb12000 \ msvcrt
ELF 7eb12000-7ebb2000 Deferred gdi32<elf>
\-PE 7eb20000-7ebb2000 \ gdi32
ELF 7ebb2000-7ecfe000 Export user32<elf>
\-PE 7ebd0000-7ecfe000 \ user32
ELF 7ecfe000-7ed92000 Deferred winmm<elf>
\-PE 7ed10000-7ed92000 \ winmm
ELF 7ed92000-7eda8000 Deferred libresolv.so.2
ELF 7eda8000-7edc7000 Deferred iphlpapi<elf>
\-PE 7edb0000-7edc7000 \ iphlpapi
ELF 7edc7000-7edf4000 Deferred ws2_32<elf>
\-PE 7edd0000-7edf4000 \ ws2_32
ELF 7edf4000-7ee0f000 Deferred wsock32<elf>
\-PE 7ee00000-7ee0f000 \ wsock32
ELF 7ee0f000-7ee62000 Deferred advapi32<elf>
\-PE 7ee20000-7ee62000 \ advapi32
ELF 7ee62000-7ee6e000 Deferred libnss_files.so.2
ELF 7ee6e000-7ee87000 Deferred libnsl.so.1
ELF 7ee87000-7ee90000 Deferred libnss_compat.so.2
ELF 7ee90000-7ee95000 Deferred libuuid.so.1
ELF 7efca000-7eff0000 Deferred libm.so.6
ELF 7eff5000-7f000000 Deferred libnss_nis.so.2
ELF b7d7a000-b7d7e000 Deferred libdl.so.2
ELF b7d7e000-b7ee1000 Deferred libc.so.6
ELF b7ee2000-b7efb000 Deferred libpthread.so.0
ELF b7f0b000-b8042000 Export libwine.so.1
ELF b8044000-b8062000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000c
00000012 0
0000000e 0
0000000d 0
0000000f
00000016 0
00000014 0
00000011 0
00000010 0
00000019
0000001a 0
0000001b
0000001c 0
00000031
00000032 0
00000036
00000033 0
0000002a
00000035 0
00000038 (D) D:\PortableApps\ThunderbirdPortable\App\Thunderbird\thunderbird.exe
00000044 0
00000043 0
00000042 0
00000041 0
00000040 0
00000022 0
00000027 0
0000001d 0
0000001e 0
00000029 0
0000001f 0
00000039 0
00000037 0 <==
Backtrace:
=>1 0x005221af in thunderbird (+0x1221af) (0x003348a0)
2 0x005219ee in thunderbird (+0x1219ee) (0x0033e93c)
3 0x00522560 in thunderbird (+0x122560) (0x0033e978)
4 0x0052376e in thunderbird (+0x12376e) (0x0033e9c0)
5 0x005249bc in thunderbird (+0x1249bc) (0x0033e9f4)
6 0x0052570d in thunderbird (+0x12570d) (0x0033ea28)
7 0x0051adf6 in thunderbird (+0x11adf6) (0x0033ea58)
8 0x00a15f0a in thunderbird (+0x615f0a) (0x0033ea80)
9 0x00519774 in thunderbird (+0x119774) (0x0033ea9c)
10 0x00a15de0 in thunderbird (+0x615de0) (0x0033ed34)
11 0x006da0ac in thunderbird (+0x2da0ac) (0x0033ee00)
12 0x006d9b2f in thunderbird (+0x2d9b2f) (0x0033eec4)
13 0x006d965f in thunderbird (+0x2d965f) (0x0033ef58)
14 0x00562055 in thunderbird (+0x162055) (0x0033ef88)
15 0x0063afb4 in thunderbird (+0x23afb4) (0x0033efa4)
16 0x005c9be4 in thunderbird (+0x1c9be4) (0x0033efec)
17 0x005c9932 in thunderbird (+0x1c9932) (0x0033f0a0)
18 0x005c9391 in thunderbird (+0x1c9391) (0x0033f1a4)
19 0x005ca74b in thunderbird (+0x1ca74b) (0x0033f210)
20 0x0063b62e in thunderbird (+0x23b62e) (0x0033f22c)
21 0x00534fe3 in thunderbird (+0x134fe3) (0x0033f31c)
22 0x00537e4d in thunderbird (+0x137e4d) (0x0033f5a0)
23 0x0053538d in thunderbird (+0x13538d) (0x0033f5d4)
24 0x7ec7e29a WINPROC_wrapper+0x1a() in user32 (0x0033f604)
25 0x7ec7e6ea WINPROC_wrapper+0x46a() in user32 (0x0033f644)
26 0x7ec839fd in user32 (+0xb39fd) (0x0033f684)
27 0x7ec43f97 in user32 (+0x73f97) (0x0033f6e4)
28 0x7ec48ec5 in user32 (+0x78ec5) (0x0033f744)
29 0x7ec493dc SendMessageW+0x4c() in user32 (0x0033f784)
30 0x7ec5563e RedrawWindow+0x20e() in user32 (0x0033f7e4)
31 0x7ec56ba5 UpdateWindow+0x35() in user32 (0x0033f804)
32 0x00537b01 in thunderbird (+0x137b01) (0x0033f840)
33 0x7ec73099 in user32 (+0xa3099) (0x0033f870)
34 0x7ec730e4 EnumChildWindows+0x34() in user32 (0x0033f890)
35 0x00537b79 in thunderbird (+0x137b79) (0x0033f8b8)
36 0x005388c1 in thunderbird (+0x1388c1) (0x0033fb38)
37 0x0053538d in thunderbird (+0x13538d) (0x0033fb6c)
38 0x7ec7e29a WINPROC_wrapper+0x1a() in user32 (0x0033fb9c)
39 0x7ec7e6ea WINPROC_wrapper+0x46a() in user32 (0x0033fbdc)
40 0x7ec839fd in user32 (+0xb39fd) (0x0033fc1c)
41 0x7ec440b6 DispatchMessageW+0x96() in user32 (0x0033fc5c)
42 0x0054136f in thunderbird (+0x14136f) (0x0033fcb0)
43 0x007e2b04 in thunderbird (+0x3e2b04) (0x0033fe4c)
44 0x00401012 in thunderbird (+0x1012) (0x0033ff08)
45 0x7b878828 in kernel32 (+0x58828) (0x0033ffe8)
46 0xb7f12d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
augi@compy:/media/CRUZER4GB/PortableApps/ThunderbirdPortable$
```


Any help is greatly appreciated. Other threads do not seem to address "zombie" processes unless referring to World of Warcraft.

---

### Post by GreatAshGoblin on 2009-11-08
I realise this is a pretty old thread, but I was having the same problem and may have found the reason for the issue, or three possible reasons anyways, so I figured I'd make a forum account and share the information for anyone who encountered this issue. I'm using Karmic (9.10).

It seems that the Zombie ThunderbirdPortable.exe issue might stem from having winetricks, playonlinux or gecko installed, I'm not sure which since I installed them all before noticing TB stopped working and I uninstalled them all at the same time. Thunderbird Portable was working fine for me before I installed them while trying to install Steam. In order to fix the issue, I purged Wine from my system using:

```
sudo apt-get remove --purge wine
sudo aptitude purge wine
```And then reinstalled wine using:
```
sudo apt-get install wine
```Sorry I can't give any more precise information on the subject, but this method worked for me, TB Portable is now working correctly.

---

