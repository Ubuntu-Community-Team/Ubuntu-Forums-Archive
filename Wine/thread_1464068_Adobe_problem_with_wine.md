---
title: "Adobe problem with wine"
date: 2010-04-27
forum: Wine
---

### Post by xxwckdxx on 2010-04-27
I have done some searching and can't come up with a answer. I installed wine and iam trying to install Adobe Cs4 master Collection or Adobe Photoshop Cs4. Both of them when I open the install I get a "program error" and i have to close.

Any suggestions?


<===Ubuntu noob sorry
Robert

---

### Post by Jon Monreal on 2010-04-27
Hello,

Take a look at the [page on CS4 at the Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318") and see if the HOWTO section there will solve your problem.

If that doesn't work, we can look at other possibilities.

---

### Post by xxwckdxx on 2010-04-27
> **Jon Monreal said:**
> Hello,

Take a look at the [page on CS4 at the Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318") and see if the HOWTO section there will solve your problem.

If that doesn't work, we can look at other possibilities.
Thanks i actually just found that and followed it, my problem is now that it says to install "LANG=C wine Setup.exe" but where or how do i point it to the set.exe file? Where should the setup files be placed? i can't figure that part out so far everything else in the tutorial worked.

---

### Post by xxwckdxx on 2010-04-27
when i paste that command to the terminal i get this

```
xxwckdxx@xxwckdxx-laptop:~$ LANG=C wine Setup.exe
wine: could not load L"C:\\windows\\system32\\Setup.exe": Module not found
xxwckdxx@xxwckdxx-laptop:~$ err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r

```

---

### Post by Jon Monreal on 2010-04-27
Where are you installing from, the CD?

---

### Post by xxwckdxx on 2010-04-27
No, I gave it straight on the computer on a seperate partition. I moved it to "home"

---

### Post by Jon Monreal on 2010-04-27
So Setup.exe itself is in your home? If it's in a folder, you'll need to specify /folder/Setup.exe

---

### Post by xxwckdxx on 2010-04-27
> **Jon Monreal said:**
> So Setup.exe itself is in your home? If it's in a folder, you'll need to specify /folder/Setup.exe
i did 

LANG=C wine /Adobe/Setup.exe

but came back no such file or directory ill try again when i get back to the laptop iam not near it now

---

### Post by kmsalex on 2010-04-27
if your willing to pay crawsover has a preponderated installer for photo shop.

---

### Post by xxwckdxx on 2010-04-27
> **kmsalex said:**
> if your willing to pay crawsover has a preponderated installer for photo shop.

I tried crossover also i keep getting "adobe program recieved a error contact adobe customer support"

---

### Post by Jon Monreal on 2010-04-28
> **xxwckdxx said:**
> I tried crossover also i keep getting "adobe program recieved a error contact adobe customer support"

So, are you trying to install the master collection or just Photoshop (or have you tried both)?

Also, what version of Crossover are you using?

Thanks.

---

### Post by xxwckdxx on 2010-04-28
Tried both...and crossover 9.0.1, also in that tutorial for photoshop it says to use 1.1.7 ver of wine and it wasn't on the page that was listed so i used 1.1.8 i don't know if that would make a difference

---

### Post by Jon Monreal on 2010-04-28
> **xxwckdxx said:**
> Tried both...and crossover 9.0.1, also in that tutorial for photoshop it says to use 1.1.7 ver of wine and it wasn't on the page that was listed so i used 1.1.8 i don't know if that would make a difference

see

> It requires removing the current version of Wine and installing version 1.1.17.  Later versions will not work with Photoshop's installer.  Upgrading to the latest version of Wine after installation is possible and does not hinder performance.

---

### Post by xxwckdxx on 2010-04-28
ok so i uninstalled wine then went and downloaded wine 1.1.1.7 for Ubuntu 8.xxx and installed it...when i go to the terminal and type LANG=C wine /home/xxwckdxx/PS/Setup.exe

i get

```
xxwckdxx@xxwckdxx-laptop:~$ LANG=C wine /home/xxwckdxx/PS/Setup.exe
fixme:console:AttachConsole stub ffffffff
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svg" 4 4 (nil) (nil) 0x12e030 (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svgz" 4 4 (nil) (nil) 0x12e030 (nil)
Begin Adobe Setup
UI mode: Full GUI
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0032f8e0 EBP:0032fb0c EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:0032f908 EDX:00000079
 ESI:00000006 EDI:00000000
Stack dump:
0x0032f8e0:  00434e15 00000006 00000000 00000000
0x0032f8f0:  00000000 0032f908 7097e9ef 00698338
0x0032f900:  0032fd58 00000000 2059f016 00000000
0x0032f910:  00000007 0012dfe8 00000030 0012dfd8
0x0032f920:  0012df60 00110014 00000000 0000011c
0x0032f930:  00000006 00000000 00001770 00000002
Backtrace:
=>1 0x00000000 (0x0032fb0c)
  2 0x0045c064 in setup (+0x5c064) (0x0032fb50)
  3 0x0042b114 in setup (+0x2b114) (0x0032fbc8)
  4 0x536e6957 (0x02020002)
  5 0x00000000 (0x00000000)
0x00000000: addb    %al,0x0(%eax)
Modules:
Module    Address            Debug info    Name (93 modules)
PE      400000-  6fc000    Export          setup
ELF    60000000-6001d000    Deferred        ld-linux.so.2
ELF    6001d000-60036000    Deferred        libpthread.so.0
ELF    60036000-6017b000    Deferred        libc.so.6
ELF    6017b000-6017f000    Deferred        libdl.so.2
ELF    6017f000-601a5000    Deferred        libm.so.6
ELF    601a5000-601ad000    Deferred        libnss_compat.so.2
ELF    601ad000-601c4000    Deferred        libnsl.so.1
ELF    601c4000-601cf000    Deferred        libnss_nis.so.2
ELF    601cf000-601db000    Deferred        libnss_files.so.2
ELF    601db000-60238000    Deferred        shlwapi<elf>
  \-PE    601f0000-60238000    \               shlwapi
ELF    60238000-60385000    Deferred        user32<elf>
  \-PE    60250000-60385000    \               user32
ELF    60385000-60425000    Deferred        gdi32<elf>
  \-PE    603a0000-60425000    \               gdi32
ELF    60425000-6047a000    Deferred        advapi32<elf>
  \-PE    60430000-6047a000    \               advapi32
ELF    6047a000-604a7000    Deferred        ws2_32<elf>
  \-PE    60480000-604a7000    \               ws2_32
ELF    604a7000-604c7000    Deferred        iphlpapi<elf>
  \-PE    604b0000-604c7000    \               iphlpapi
ELF    604c7000-60575000    Deferred        comdlg32<elf>
  \-PE    604d0000-60575000    \               comdlg32
ELF    60575000-6063c000    Deferred        comctl32<elf>
  \-PE    60580000-6063c000    \               comctl32
ELF    6063c000-60673000    Deferred        winspool<elf>
  \-PE    60640000-60673000    \               winspool
ELF    60673000-6069c000    Deferred        oledlg<elf>
  \-PE    60680000-6069c000    \               oledlg
ELF    6069c000-607af000    Deferred        ole32<elf>
  \-PE    606c0000-607af000    \               ole32
ELF    607af000-60816000    Deferred        rpcrt4<elf>
  \-PE    607c0000-60816000    \               rpcrt4
ELF    60816000-60903000    Deferred        oleaut32<elf>
  \-PE    60830000-60903000    \               oleaut32
ELF    60903000-6091e000    Deferred        version<elf>
  \-PE    60910000-6091e000    \               version
ELF    6091e000-60933000    Deferred        lz32<elf>
  \-PE    60920000-60933000    \               lz32
ELF    60933000-60949000    Deferred        psapi<elf>
  \-PE    60940000-60949000    \               psapi
ELF    60949000-6095f000    Deferred        libz.so.1
ELF    6095f000-6098c000    Deferred        libfontconfig.so.1
ELF    6098c000-609b3000    Deferred        libexpat.so.1
ELF    609b3000-609bc000    Deferred        libsm.so.6
ELF    609bc000-609d7000    Deferred        libice.so.6
ELF    609d7000-609e7000    Deferred        libxext.so.6
ELF    609e7000-60b16000    Deferred        libx11.so.6
ELF    60b16000-60b1b000    Deferred        libuuid.so.1
ELF    60b1b000-60b1f000    Deferred        libxau.so.6
ELF    60b1f000-60b3d000    Deferred        libxcb.so.1
ELF    60b3d000-60b5e000    Deferred        imm32<elf>
  \-PE    60b40000-60b5e000    \               imm32
ELF    60b5e000-60b61000    Deferred        libxinerama.so.1
ELF    60b61000-60b67000    Deferred        libxxf86vm.so.1
ELF    60b67000-60b71000    Deferred        libxrender.so.1
ELF    60b71000-60b7a000    Deferred        libxrandr.so.2
ELF    60b7a000-60b7e000    Deferred        libxcomposite.so.1
ELF    60b7e000-60b84000    Deferred        libxfixes.so.3
ELF    60b84000-60b8f000    Deferred        libxcursor.so.1
ELF    60b8f000-60bd5000    Deferred        libcups.so.2
ELF    60bd5000-60bff000    Deferred        libgssapi_krb5.so.2
ELF    60bff000-60ca7000    Deferred        libgnutls.so.26
ELF    60ca7000-60cb3000    Deferred        libavahi-common.so.3
ELF    60cb3000-60cc4000    Deferred        libavahi-client.so.3
ELF    60cc4000-60d6a000    Deferred        libkrb5.so.3
ELF    60d6a000-60d93000    Deferred        libk5crypto.so.3
ELF    60d93000-60d97000    Deferred        libcom_err.so.2
ELF    60d97000-60d9f000    Deferred        libkrb5support.so.0
ELF    60d9f000-60da3000    Deferred        libkeyutils.so.1
ELF    60da3000-60e1f000    Deferred        libgcrypt.so.11
ELF    60e1f000-60e28000    Deferred        librt.so.1
ELF    60e28000-60e2d000    Deferred        libgpg-error.so.0
ELF    62c5f000-62c71000    Deferred        libtasn1.so.3
ELF    64311000-64316000    Deferred        libxdmcp.so.6
ELF    64d58000-64d73000    Deferred        wsock32<elf>
  \-PE    64d60000-64d73000    \               wsock32
ELF    695c5000-695d9000    Deferred        libresolv.so.2
ELF    6a00c000-6a08b000    Deferred        libfreetype.so.6
ELF    6be9c000-6bf38000    Deferred        winex11<elf>
  \-PE    6beb0000-6bf38000    \               winex11
ELF    6e4ee000-6e60a000    Deferred        shell32<elf>
  \-PE    6e500000-6e60a000    \               shell32
ELF    7258e000-725c7000    Deferred        libdbus-1.so.3
ELF    76244000-76277000    Deferred        uxtheme<elf>
  \-PE    76250000-76277000    \               uxtheme
ELF    799ae000-79ae5000    Deferred        libwine.so.1
ELF    7b800000-7b941000    Deferred        kernel32<elf>
  \-PE    7b820000-7b941000    \               kernel32
ELF    7bc00000-7bca9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\xxwckdxx\PS\Setup.exe
    00000009    0 <==
0000000c 
    00000016    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000017 
    00000018    0
Backtrace:
=>1 0x00000000 (0x0032fb0c)
  2 0x0045c064 in setup (+0x5c064) (0x0032fb50)
  3 0x0042b114 in setup (+0x2b114) (0x0032fbc8)
  4 0x536e6957 (0x02020002)
  5 0x00000000 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
xxwckdxx@xxwckdxx-laptop:~$ 

```

---

### Post by xxwckdxx on 2010-04-28
If i try to open the setup.exe directly crossover gives me ....
```

FATAL ERROR
Unable to find the 'default' bottle:
bottle 'default' not found in '/home/xxwckdxx/.cxoffice'
bottle 'default' not found in '/opt/cxoffice/support'

```

---

### Post by Jon Monreal on 2010-04-28
> **xxwckdxx said:**
> If i try to open the setup.exe directly crossover gives me ....
```

FATAL ERROR
Unable to find the 'default' bottle:
bottle 'default' not found in '/home/xxwckdxx/.cxoffice'
bottle 'default' not found in '/opt/cxoffice/support'

```

You're using Crossover Office?

---

### Post by xxwckdxx on 2010-04-28
I downloaded the trial of crossover from their website...shouldn't be office

---

### Post by xxwckdxx on 2010-04-28
Says Crossover Linux on the website..

---

### Post by lavinog on 2010-04-28
> **xxwckdxx said:**
> i did 

LANG=C wine /Adobe/Setup.exe

but came back no such file or directory ill try again when i get back to the laptop iam not near it now

Do you know where the Adobe folder is located?
If you use a leading '/' you are telling it that the folder is located in the root folder...which is most likely not correct.

---

### Post by xxwckdxx on 2010-04-28
yeah i realized it after and renamed the folder to PS
xxwckdxx@xxwckdxx-laptop:~$ LANG=C wine /home/xxwckdxx/PS/Setup.exe

doing this method it starts to install then gets a program error

---

### Post by varunendra on 2010-04-28
Just checked crossover's website & found it officially supports only CS2.

Also, I think the Master Collection's setup structure is a bit different from that of standalone Photoshop CS4 installer.

Anyway, can't give conclusions yet. See if u can get it solved, else I'll try it (CS4- PS & Master Coll.) tonight & post the results by tomorrow.

Hope u get it working.

---

### Post by xxwckdxx on 2010-04-28
I also realized that i get a error of Cs4 requires xp service 2 pack to be installed and if i  try the incompatable vista bottle doesn't work either...

---

### Post by Jon Monreal on 2010-04-28
> **varunendra said:**
> Just checked crossover's website & found it officially supports only CS2.

Also, I think the Master Collection's setup structure is a bit different from that of standalone Photoshop CS4 installer.

Yeah, before more recent versions of Wine CS4 wouldn't run at all.

There is a [page on CS4 support]("http://www.codeweavers.com/compatibility/browse/name?app_id=4854") at the CodeWeavers website that says it will run with a specific version. Not sure about trials at any rate.

A Google search on the Wine website shows that many have had problems even when CS4 does work like parts of windows turning black. If you really need CS4 and need it to work, I would recommend a virtual machine running Windows (or dual-booting if you need native speed).

---

### Post by xxwckdxx on 2010-04-28
any tutorials on how to install a virtual machine?  I found a different tutorial for photoshop which got me way further then before but after it asked for the serial and all, it started to install and it came back with a fatal error installing photoshop so i had to cancel the install.

---

### Post by Jon Monreal on 2010-04-28
I'll write one up for you if you want. Been meaning to do so, anyways.

---

### Post by donkyhotay on 2010-04-28
I'm surprised this thread has so many posts without getting shifted over to the [wine subforum](http://ubuntuforums.org/forumdisplay.php?f=313) here at ubuntuforums.

---

### Post by xxwckdxx on 2010-04-28
> **Jon Monreal said:**
> I'll write one up for you if you want. Been meaning to do so, anyways.

I'd appreciate it.

---

### Post by xxwckdxx on 2010-04-28
> **donkyhotay said:**
> I'm surprised this thread has so many posts without getting shifted over to the [wine subforum]("http://ubuntuforums.org/forumdisplay.php?f=313") here at ubuntuforums.

I just realized there was a wine forum today hopefully a mod will move it for me.

---

### Post by Jon Monreal on 2010-04-28
Here's the tutorial.

If you need any additional help or notice any mistakes, please feel free to ask.

---

### Post by Iowan on 2010-04-28
Moved ot Wine forum.

---

### Post by xxwckdxx on 2010-04-29
Thanks for the tutorial iam installing cs4 master suite now so far so good

---

### Post by varunendra on 2010-04-30
Please tell us if it worked so as to help others save their time.

---

