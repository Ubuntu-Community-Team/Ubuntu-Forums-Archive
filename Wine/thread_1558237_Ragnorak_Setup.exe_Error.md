---
title: "Ragnorak Setup.exe Error"
date: 2010-08-21
forum: Wine
---

### Post by Bwathke on 2010-08-21
Ok so I found out ragnorak was rated platinum if you do a few things with winetricks so I installed it and patched it fine but if I start the game I get a wine error screen saying Were sorry setup.exe has encountered a serious issue and needs to close etc. So I looked everywhere and I cannot see anyone who has posted that problem... Im on wine 1.3. If it helps Im trying to run the valkrye server or "the free one:. Thanks

---

### Post by Corey4666 on 2010-08-21
You have more information on the error? or a screen shot?
I've run a lot of different RO clients on wine + ubuntu and It usually is very hard to play due to FPS being low. I can help you get it up and running though.


EDIT:

You know what, tell me what you've done so far with setting it up. Did you emulate virtual desktop? I could never get the setup.exe and ro.exe to run without it. Anyways, I will try to help out but I need more info. :P

---

### Post by Bwathke on 2010-08-22
I did everything listed on [http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928) And no I am only using WINE because well my Win XP disc wont work in virtualbox for some reason =/ Also you need 3D support to play it dont you? I didnt think you could get that in a virtual desktop. Oh and just to clarify I am using the official client not a private server.

---

### Post by Corey4666 on 2010-08-22
So when you try to launch the game... you get a error with setup.exe not opening? or is it a gravity error? 

If not a gravity error, did you try running the setup.exe w/ emulated desktop? btw wine has compatibility for windows 98/xp/2000 etc don't it? *been a while since I used wine* 

TBH simple things like that helped me with RO problems before.
I never had to use *winetricks* either. Btw since setup wont open aren't you able to define the settings a .cfg file? 

lol I suppose I am not much help, It's been a while since I used wine or even played Ragnarok in the last year or so. I also never tried setting up a official server. I only played the P-servers. 

I hope someone comes along to help you out.

EDIT:
No, I dont believe you need 3d support for RO everything's 2D.

---

### Post by shini-kire on 2010-08-22
visit link here 

[http://ubuntuforums.org/showthread.php?t=1556938&highlight=ragnarok](http://ubuntuforums.org/showthread.php?t=1556938&highlight=ragnarok)

---

### Post by Bwathke on 2010-08-22
No its a wine error not gravity and I have tried running in an emulated desktop and not. Ill test out that .cfg thing right now and see if that will let me skip opening the setup.exe. I dont see any .cfg files in the folder at all =/ I just tried running the setup in Windows 7, Vista, 2008, XP, 98, 95 and ME. Still nothing but thanks for the ideas!

---

### Post by Corey4666 on 2010-08-22
> **shini-kire said:**
> visit link here 

[http://ubuntuforums.org/showthread.php?t=1556938&highlight=ragnarok](http://ubuntuforums.org/showthread.php?t=1556938&highlight=ragnarok)

That's a great way to advert a private server! :lolflag:

Too bad It dont help with setup.exe 

The last thing I could probably recommend to fixing your problem is to use a setup.exe from a private servers patch. I think these days a small few of the top rated servers have custom setup.exe's now.

If you don't mind me asking.. Why would you wanna play valkyrie anyways? My friend said its filled with bot's because the GM's don't care to ban them or even look for them. Almost every lowrate RO p-server has very strong anti-botting systems implemented. They do in fact work, if you check openkore they do have a big list of private servers that are impossible to bot. 

If you never played a p-server I could always help ya install it. Its quite simple to do, There are official rate like servers now on ratemyserver.net.

---

### Post by Bwathke on 2010-08-22
I used to play one called aeRO I could never find a lowrate and valkrye is the only free non monthly payment official server =P But non official servers work on ubuntu? If they do could you PM me on how to do it? I dont want to get in trouble talking about private servers in the public forums ahaha

---

### Post by Corey4666 on 2010-08-22
Ah, I could PM you if you'd like. Though private ragnarok servers are not illegal. If they were they would all be shut down by gravity. 

The reason there not illegal is because there using a open source emulator "eAthena" and using sakray test client and not the official RO client. 

The only RO servers that get shut down are the ones that charged money. That's why all servers have the "donation" system now. 
In fact 1 of the popular low rate servers I forget which one. The head GM is friends with a staff member of gravity afaik ;)

Anyways it's not so hard to setup a private server on ubuntu. Tell me which server you wanna try in a PM or on this thread and I can tell ya some steps you need to take to get it going. 

I'd suggest using ragray client google it, and install the patch from the private server then I can guide you through the rest of it. The ragray client comes with the renewal client to update which I believe works with wine pretty well just like Valkyries updater does. If the server you have comes with a full client. Just get that to avoid any unnecessary problems, You might not even need to patch a majority of the time with a full client. 

I'd probably recommend EuphRO since its 3/3/2 rates and they don't wipe unless something bad goes down. *like 3 years ago i think? was last wipe* The server has had some bad times, but it has new management and GM's.

1 last thing, Do you have a nvidia graphics card or a ATI? I heard that ATI cards run slow on RO + Wine. Maybe that's why I always had FPS problems. 

Anyways get back to me, PM me or post here whichever you like. ):P

---

### Post by Bwathke on 2010-08-23
My nvidia broke last month so Im just using the old card in my system but it can run RO for sure =P Im getting the ragray thing now. EuphRO was the server I was looking at on ratemyserver also =) ATI Videocards arent supported by ATI for very long I think so you cant get the newest drivers or something like that =/ Otherwise I would have one ahaha

EDIT:

I went to 1.1.42 and it works fine now but wine still wont open it... I click the play button and it says its loading then it poofs and nothing happens.

---

### Post by Corey4666 on 2010-08-23
It closes when your entering the game after the character selection / creation login server? So what happens is you get the 0-100% bar loading right? then it closes you say? 

You don't have winetricks installed do you? I'd uninstall it. Also try using emulated desktop if you have not *I am sure you have*

These are not the problems I have ever ran into running a p-server on ubuntu using wine. Uhh.. I really not sure what to say, So your using a ati card? did you trying using the proprietary drivers? 

When it comes to patching and updates, connection errors, gravity error I got your back lol but I still kind of lost on whats going on with your game client right now. Hit the post up later and give me a bit more detail. 

If your game just randomly closes while loading your first screen before you enter the game, I'd say try messing with different drivers and re-test. Also if you have not just a reminder try switching compatibility to windows 2000 or xp. 

You could try getting GRF Tool from google, It's hosted on a source forge website extract the EuphRO.grf file and put all the contents into a folder named "data" inside the base directory of RO. That could maybe help rule out any possible problems with loading screens or anything. take a shot in the dark lol.

Sorry for such late replies my internet has been acting up horribly, It won't even let me stay online for more than a few minutes today.

---

### Post by Bwathke on 2010-08-24
I got one to work finally but I guess it has some 3D cus whenever I run a program with 3D my comp crashes because Im using a video card that is not supported anymore =/ Guess Ill have to wait till I get the new Nvidia =P Thanks for all your help!

---

### Post by Corey4666 on 2010-08-24
No problem! please pm me anytime you'd like If you run into anymore problems in the future. 

I am thinking about installing ubuntu on my PC again. I have not been using it lately because I have had dial up for quite some time. Now that I have high speed I think I will try out RO + wine and we can join the same server.

---

### Post by 1XYDavidYX1 on 2010-10-03
I have the same problem when I try to execute ragnarok and others 3D games the games crash if any one can help me with this little problem or if any one can tell me where can I find information about it 
waiting for answer thanks

attached information of the error 


wine: Unhandled page fault on write access to 0x018810e6 at address 0x880818 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x018810e6 in 32-bit code (0x00880818).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 00000000 in module L"aroexe"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00880818 ESP:0032fddc EBP:0032fe14 EFLAGS:00210207(  R- --  I   - -P-C)
 EAX:00000000 EBX:015e8470 ECX:018810e6 EDX:00e80000
 ESI:015e85ac EDI:016f5960
Stack dump:
0x0032fddc:  0000a81e 017f0004 00000005 444affaa
0x0032fdec:  6360a4a8 a8a98b1e 6f5c926f fd16ffd4
0x0032fdfc:  0032fe10 00088000 0000eea1 00000003
0x0032fe0c:  00000024 01880000 0032fe34 00880af5
0x0032fe1c:  017f0004 00000000 00000004 7bc10000
0x0032fe2c:  00000000 7b8b8ff4 0032fe58 00880b5b
Backtrace:
=>0 0x00880818 in aroexe (+0x480818) (0x0032fe14)
  1 0x00880af5 in aroexe (+0x480af5) (0x0032fe34)
  2 0x00880b5b in aroexe (+0x480b5b) (0x0032fe58)
  3 0x0087fe13 in aroexe (+0x47fe13) (0x0032fe7c)
  4 0x007136ad in aroexe (+0x3136ad) (0x0032ff08)
  5 0x7b878500 in kernel32 (+0x58500) (0x0032ffe8)
  6 0xb767ae1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x00880818: addl    %edx,0x0(%ecx)
Modules:
Module    Address            Debug info    Name (95 modules)
PE      330000-  38d000    Deferred        granny2
PE      400000-  8d2000    Export          aroexe
PE    10000000-10015000    Deferred        cps
PE    21100000-2115d000    Deferred        mss32
PE    30000000-3006d000    Deferred        binkw32
PE    60000000-6005d000    Deferred        ijl15
PE    78000000-78044000    Deferred        msvcrt
ELF    7b800000-7b96e000    Export          kernel32<elf>
  \-PE    7b820000-7b96e000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d831000-7d847000    Deferred        psapi<elf>
  \-PE    7d840000-7d847000    \               psapi
ELF    7d847000-7d85b000    Deferred        sxs<elf>
  \-PE    7d850000-7d85b000    \               sxs
ELF    7d8a9000-7d8dc000    Deferred        uxtheme<elf>
  \-PE    7d8b0000-7d8dc000    \               uxtheme
ELF    7d8dc000-7d8f1000    Deferred        midimap<elf>
  \-PE    7d8e0000-7d8f1000    \               midimap
ELF    7d8f1000-7d917000    Deferred        msacm32<elf>
  \-PE    7d900000-7d917000    \               msacm32
ELF    7d917000-7d92f000    Deferred        msacm32<elf>
  \-PE    7d920000-7d92f000    \               msacm32
ELF    7e130000-7e136000    Deferred        libattr.so.1
ELF    7e136000-7e13d000    Deferred        libgdbm.so.3
ELF    7e13d000-7e19c000    Deferred        libpulse.so.0
ELF    7e1aa000-7e272000    Deferred        libasound.so.2
ELF    7e274000-7e279000    Deferred        libcap.so.2
ELF    7e279000-7e280000    Deferred        libasound_module_pcm_pulse.so
ELF    7e280000-7e2b7000    Deferred        winealsa<elf>
  \-PE    7e290000-7e2b7000    \               winealsa
ELF    7e2b7000-7e2c0000    Deferred        libxcursor.so.1
ELF    7e2c0000-7e2c5000    Deferred        libxfixes.so.3
ELF    7e2c5000-7e2c9000    Deferred        libxcomposite.so.1
ELF    7e2c9000-7e2d1000    Deferred        libxrandr.so.2
ELF    7e2d1000-7e2db000    Deferred        libxrender.so.1
ELF    7e2db000-7e2e1000    Deferred        libxxf86vm.so.1
ELF    7e2e1000-7e2e4000    Deferred        libxinerama.so.1
ELF    7e2e4000-7e2e9000    Deferred        libxdmcp.so.6
ELF    7e2e9000-7e303000    Deferred        libxcb.so.1
ELF    7e303000-7e307000    Deferred        libxau.so.6
ELF    7e307000-7e30c000    Deferred        libuuid.so.1
ELF    7e30c000-7e3fb000    Deferred        libx11.so.6
ELF    7e3fb000-7e40b000    Deferred        libxext.so.6
ELF    7e40b000-7e423000    Deferred        libice.so.6
ELF    7e423000-7e42c000    Deferred        libsm.so.6
ELF    7e42f000-7e438000    Deferred        librt.so.1
ELF    7e43a000-7e4d9000    Deferred        winex11<elf>
  \-PE    7e450000-7e4d9000    \               winex11
ELF    7e518000-7e53f000    Deferred        libexpat.so.1
ELF    7e53f000-7e56c000    Deferred        libfontconfig.so.1
ELF    7e57a000-7e590000    Deferred        libz.so.1
ELF    7e590000-7e607000    Deferred        libfreetype.so.6
ELF    7e607000-7e61d000    Deferred        libresolv.so.2
ELF    7e62b000-7e64b000    Deferred        iphlpapi<elf>
  \-PE    7e630000-7e64b000    \               iphlpapi
ELF    7e64b000-7e672000    Deferred        netapi32<elf>
  \-PE    7e650000-7e672000    \               netapi32
ELF    7e672000-7e693000    Deferred        imm32<elf>
  \-PE    7e680000-7e693000    \               imm32
ELF    7e693000-7e6c1000    Deferred        ws2_32<elf>
  \-PE    7e6a0000-7e6c1000    \               ws2_32
ELF    7e6c1000-7e719000    Deferred        ddraw<elf>
  \-PE    7e6d0000-7e719000    \               ddraw
ELF    7e719000-7e7e1000    Deferred        comctl32<elf>
  \-PE    7e720000-7e7e1000    \               comctl32
ELF    7e7e1000-7e83f000    Deferred        shlwapi<elf>
  \-PE    7e7f0000-7e83f000    \               shlwapi
ELF    7e83f000-7e9cd000    Deferred        shell32<elf>
  \-PE    7e850000-7e9cd000    \               shell32
ELF    7e9cd000-7ea69000    Deferred        winmm<elf>
  \-PE    7e9e0000-7ea69000    \               winmm
ELF    7ea69000-7ead7000    Deferred        rpcrt4<elf>
  \-PE    7ea80000-7ead7000    \               rpcrt4
ELF    7ead7000-7eb79000    Deferred        gdi32<elf>
  \-PE    7eaf0000-7eb79000    \               gdi32
ELF    7eb79000-7ecc5000    Deferred        user32<elf>
  \-PE    7eb90000-7ecc5000    \               user32
ELF    7ecc5000-7ed1c000    Deferred        advapi32<elf>
  \-PE    7ecd0000-7ed1c000    \               advapi32
ELF    7ed1c000-7ee18000    Deferred        ole32<elf>
  \-PE    7ed30000-7ee18000    \               ole32
ELF    7ee18000-7ee51000    Deferred        dinput<elf>
  \-PE    7ee20000-7ee51000    \               dinput
ELF    7ef9c000-7efa8000    Deferred        libnss_files.so.2
ELF    7efa8000-7efb3000    Deferred        libnss_nis.so.2
ELF    7efb3000-7efcc000    Deferred        libnsl.so.1
ELF    7efcc000-7eff2000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b74e4000-b74e8000    Deferred        libdl.so.2
ELF    b74e8000-b764b000    Deferred        libc.so.6
ELF    b764c000-b7665000    Deferred        libpthread.so.0
ELF    b7673000-b77af000    Export          libwine.so.1
ELF    b77b1000-b77cf000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Gravity\RO\aroexe.exe
    00000009    0 <==
0000000e 
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
0000001a 
    0000001b    0
Backtrace:
=>0 0x00880818 in aroexe (+0x480818) (0x0032fe14)
  1 0x00880af5 in aroexe (+0x480af5) (0x0032fe34)
  2 0x00880b5b in aroexe (+0x480b5b) (0x0032fe58)
  3 0x0087fe13 in aroexe (+0x47fe13) (0x0032fe7c)
  4 0x007136ad in aroexe (+0x3136ad) (0x0032ff08)
  5 0x7b878500 in kernel32 (+0x58500) (0x0032ffe8)
  6 0xb767ae1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)

image

[[IMG]http://www.uploadfilesystem.com/thumbs/10/10/04/tn_HV157372.jpg[/IMG]]("http://www.uploadfilesystem.com//viewimage.php?file=/imagenes/10/10/04/HV157372.png")

image

http://www.uploadfilesystem.com//viewimage.php?file=/imagenes/10/10/04/HV157372.png" /><img src="http://www.uploadfilesystem.com/thumbs/10/10/04/tn_HV157372.jpg" alt="Powered by UploadFileSystem.COM

---

