---
title: "starcraft on wine"
date: 2010-08-06
forum: Wine
---

### Post by kr651129 on 2010-08-06
I'll try and post as many specifics as I can remember but I am at work so I don't have all the info and will get the rest out when I get home.

I tried to run starcraft (the first not starcradt 2 beta) on wine.

Note:  The wine I installed was the wine in ubuntus repos

I mounted the ISO, added the mount path to winecfg and installed the software.

After installing the software I tried to run the application and I recieved an error that said

```
ERROR: NOT ENOUGH MEMORY
```

I have 4GB of memory and 10GB of open swap, my conky shows no other large daemons or programs running at the time that would eat up my memory.

I then uninstalled wine via

```
#> aptitude pruge wine
```

After it removed itself I then downloaded the wine source and compilied it, after I ran the config I noticed a few warnings that I fixed ldap, cups, opengl, etc etc and I installed all of thoes from apt-get or source

After I resolved all the warnings I then installed wine sucessfully and got the same error.

I then ran across a thread from someone who had the same problem only with a diffrent application and they got it working by

```
#> apt-get install wine-2.1
``` (Note: I can't remember the version off hand)

So I uninstalled wine and reinstalled via the command above and still I had no sucess.

I'm running a dell with an intel 4gb of ram, 250GB HDD, and all drivers installed are linux native from the repos.

Any ideas?

---

### Post by asdfoo on 2010-08-06
your commands have typos in them, it's "purge" and "wine-1.2"

which video card do you have?

post the output of `wine --version`

Also post the terminal output when running starcraft: [http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by kr651129 on 2010-08-07
yeah it was 1.2 sorry I was at work when I posted this.


so when I got home I removed 1.2 and upgraded from source to 1.3 and I thought that may help.  I made a little progress, before the install screen for starcraft had no audio now it does.  But I'm still getting the same error


Here's the data you asked for

```

$> wine --version
wine-1.3.0

```

```

kclark@krisbox:~$ env WINEPREFIX="/home/kclark/.wine" wine C:\\windows\\command\\start.exe /Unix /home/kclark/.wine/dosdevices/c:/users/kclark/Start\ Menu/Programs/Starcraft/Starcraft\ -\ Brood\ War.lnk
fixme:exec:SHELL_execute flags ignored: 0x00000100
err:exec:shellex_load_object_and_run failed to get data object

```

```

$> lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

and log.txt is empty

my video card is Intel Integrated Graphics Media Accelerator 4500MHD

---

### Post by kr651129 on 2010-08-07
bump

---

### Post by kr651129 on 2010-08-07
I opened a bug for this, you can view it [here]("http://bugs.winehq.org/show_bug.cgi?id=23938")

---

### Post by kr651129 on 2010-08-07
and here is the error log


```


------------------------------------------------------
PROGRAM VERSION: 1.0.0.0
COMPUTER NAME: kclark
TIME: 08/07/10 16:55:03
INFO: 

Exception code: 80000003 BREAKPOINT
Fault address:	1500E1DF 01:0000D1DF C:\Program Files\Starcraft\storm.dll

Registers:
EAX:00000000
EBX:01270040
ECX:1502E23C
EDX:00000000
ESI:00052011
EDI:00000002
CS:EIP:0073:1500E1DF
SS:ESP:007B:0125E03C EBP:0125E990
DS:007B ES:007B FS:0033 GS:003B
Flags:00000246
Call stack:
Address  Frame    Logical addr  Module
1500E1DF 0125E990 0001:0000D1DF C:\Program Files\Starcraft\storm.dll

Stack bytes:
0x0125e03c: 62 ed e3 8c  00 00 27 01  9c b3 02 15  54 68 69 73  b.....'.....This
0x0125e04c: 20 61 70 70  6c 69 63 61  74 69 6f 6e  20 68 61 73   application has
0x0125e05c: 20 65 6e 63  6f 75 6e 74  65 72 65 64  20 61 20 63   encountered a c
0x0125e06c: 72 69 74 69  63 61 6c 20  65 72 72 6f  72 3a 0a 0a  ritical error:..
0x0125e07c: 4e 6f 74 20  65 6e 6f 75  67 68 20 6d  65 6d 6f 72  Not enough memor
0x0125e08c: 79 0d 0a 0a  50 72 6f 67  72 61 6d 3a  09 43 3a 5c  y...Program:.C:\
0x0125e09c: 50 72 6f 67  72 61 6d 20  46 69 6c 65  73 5c 53 74  Program Files\St
0x0125e0ac: 61 72 63 72  61 66 74 5c  53 74 61 72  43 72 61 66  arcraft\StarCraf
0x0125e0bc: 74 2e 65 78  65 0a 46 69  6c 65 3a 09  53 46 49 4c  t.exe.File:.SFIL
0x0125e0cc: 45 2e 43 50  50 0a 4c 69  6e 65 3a 09  34 32 31 0a  E.CPP.Line:.421.
0x0125e0dc: 0a 0a 0a 50  72 65 73 73  20 4f 4b 20  74 6f 20 74  ...Press OK to t
0x0125e0ec: 65 72 6d 69  6e 61 74 65  20 74 68 65  20 61 70 70  erminate the app
0x0125e0fc: 6c 69 63 61  74 69 6f 6e  2e 00 00 00  00 00 00 00  lication........
0x0125e10c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e11c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e12c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e13c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e14c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e15c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e16c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e17c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e18c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e19c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e20c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e21c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e22c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e23c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e24c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e25c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e26c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e27c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e28c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e29c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e30c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e31c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e32c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

Code bytes:
0x1500e1df: cc 6a 01 e8  69 03 00 00  ff 15 58 25  03 15 8b 35  .j..i.....X%...5



------------------------------------------------------
PROGRAM VERSION: 1.0.0.0
COMPUTER NAME: kclark
TIME: 08/07/10 16:55:34
INFO: 

Exception code: 80000003 BREAKPOINT
Fault address:	1500E1DF 01:0000D1DF C:\Program Files\Starcraft\storm.dll

Registers:
EAX:00000000
EBX:01270040
ECX:1502E23C
EDX:00000000
ESI:00052011
EDI:00000002
CS:EIP:0073:1500E1DF
SS:ESP:007B:0125E03C EBP:0125E990
DS:007B ES:007B FS:0033 GS:003B
Flags:00000246
Call stack:
Address  Frame    Logical addr  Module
1500E1DF 0125E990 0001:0000D1DF C:\Program Files\Starcraft\storm.dll

Stack bytes:
0x0125e03c: 62 ed e3 8c  00 00 27 01  9c b3 02 15  54 68 69 73  b.....'.....This
0x0125e04c: 20 61 70 70  6c 69 63 61  74 69 6f 6e  20 68 61 73   application has
0x0125e05c: 20 65 6e 63  6f 75 6e 74  65 72 65 64  20 61 20 63   encountered a c
0x0125e06c: 72 69 74 69  63 61 6c 20  65 72 72 6f  72 3a 0a 0a  ritical error:..
0x0125e07c: 4e 6f 74 20  65 6e 6f 75  67 68 20 6d  65 6d 6f 72  Not enough memor
0x0125e08c: 79 0d 0a 0a  50 72 6f 67  72 61 6d 3a  09 43 3a 5c  y...Program:.C:\
0x0125e09c: 50 72 6f 67  72 61 6d 20  46 69 6c 65  73 5c 53 74  Program Files\St
0x0125e0ac: 61 72 63 72  61 66 74 5c  53 74 61 72  43 72 61 66  arcraft\StarCraf
0x0125e0bc: 74 2e 65 78  65 0a 46 69  6c 65 3a 09  53 46 49 4c  t.exe.File:.SFIL
0x0125e0cc: 45 2e 43 50  50 0a 4c 69  6e 65 3a 09  34 32 31 0a  E.CPP.Line:.421.
0x0125e0dc: 0a 0a 0a 50  72 65 73 73  20 4f 4b 20  74 6f 20 74  ...Press OK to t
0x0125e0ec: 65 72 6d 69  6e 61 74 65  20 74 68 65  20 61 70 70  erminate the app
0x0125e0fc: 6c 69 63 61  74 69 6f 6e  2e 00 00 00  00 00 00 00  lication........
0x0125e10c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e11c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e12c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e13c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e14c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e15c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e16c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e17c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e18c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e19c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e1fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e20c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e21c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e22c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e23c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e24c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e25c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e26c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e27c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e28c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e29c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e2fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e30c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e31c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0125e32c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

Code bytes:
0x1500e1df: cc 6a 01 e8  69 03 00 00  ff 15 58 25  03 15 8b 35  .j..i.....X%...5



------------------------------------------------------
PROGRAM VERSION: 1.0.0.0
COMPUTER NAME: kclark
TIME: 08/07/10 21:59:58
INFO: 

Exception code: 80000003 BREAKPOINT
Fault address:	1500E1DF 01:0000D1DF C:\Program Files\Starcraft\storm.dll

Registers:
EAX:00000000
EBX:01250040
ECX:1502E23C
EDX:00000000
ESI:00052011
EDI:00000002
CS:EIP:0073:1500E1DF
SS:ESP:007B:0123E03C EBP:0123E990
DS:007B ES:007B FS:0033 GS:003B
Flags:00000246
Call stack:
Address  Frame    Logical addr  Module
1500E1DF 0123E990 0001:0000D1DF C:\Program Files\Starcraft\storm.dll

Stack bytes:
0x0123e03c: 62 ed e3 8c  00 00 25 01  9c b3 02 15  54 68 69 73  b.....%.....This
0x0123e04c: 20 61 70 70  6c 69 63 61  74 69 6f 6e  20 68 61 73   application has
0x0123e05c: 20 65 6e 63  6f 75 6e 74  65 72 65 64  20 61 20 63   encountered a c
0x0123e06c: 72 69 74 69  63 61 6c 20  65 72 72 6f  72 3a 0a 0a  ritical error:..
0x0123e07c: 4e 6f 74 20  65 6e 6f 75  67 68 20 6d  65 6d 6f 72  Not enough memor
0x0123e08c: 79 0d 0a 0a  50 72 6f 67  72 61 6d 3a  09 43 3a 5c  y...Program:.C:\
0x0123e09c: 50 72 6f 67  72 61 6d 20  46 69 6c 65  73 5c 53 74  Program Files\St
0x0123e0ac: 61 72 63 72  61 66 74 5c  53 74 61 72  43 72 61 66  arcraft\StarCraf
0x0123e0bc: 74 2e 65 78  65 0a 46 69  6c 65 3a 09  53 46 49 4c  t.exe.File:.SFIL
0x0123e0cc: 45 2e 43 50  50 0a 4c 69  6e 65 3a 09  34 32 31 0a  E.CPP.Line:.421.
0x0123e0dc: 0a 0a 0a 50  72 65 73 73  20 4f 4b 20  74 6f 20 74  ...Press OK to t
0x0123e0ec: 65 72 6d 69  6e 61 74 65  20 74 68 65  20 61 70 70  erminate the app
0x0123e0fc: 6c 69 63 61  74 69 6f 6e  2e 00 00 00  00 00 00 00  lication........
0x0123e10c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e11c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e12c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e13c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e14c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e15c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e16c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e17c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e18c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e19c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e20c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e21c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e22c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e23c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e24c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e25c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e26c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e27c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e28c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e29c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e30c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e31c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e32c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

Code bytes:
0x1500e1df: cc 6a 01 e8  69 03 00 00  ff 15 58 25  03 15 8b 35  .j..i.....X%...5



------------------------------------------------------
PROGRAM VERSION: 1.0.0.0
COMPUTER NAME: kclark
TIME: 08/07/10 22:14:40
INFO: 

Exception code: 80000003 BREAKPOINT
Fault address:	1500E1DF 01:0000D1DF C:\Program Files\Starcraft\storm.dll

Registers:
EAX:00000000
EBX:01250040
ECX:1502E23C
EDX:00000000
ESI:00052011
EDI:00000002
CS:EIP:0073:1500E1DF
SS:ESP:007B:0123E03C EBP:0123E990
DS:007B ES:007B FS:0033 GS:003B
Flags:00000246
Call stack:
Address  Frame    Logical addr  Module
1500E1DF 0123E990 0001:0000D1DF C:\Program Files\Starcraft\storm.dll

Stack bytes:
0x0123e03c: 62 ed e3 8c  00 00 25 01  9c b3 02 15  54 68 69 73  b.....%.....This
0x0123e04c: 20 61 70 70  6c 69 63 61  74 69 6f 6e  20 68 61 73   application has
0x0123e05c: 20 65 6e 63  6f 75 6e 74  65 72 65 64  20 61 20 63   encountered a c
0x0123e06c: 72 69 74 69  63 61 6c 20  65 72 72 6f  72 3a 0a 0a  ritical error:..
0x0123e07c: 4e 6f 74 20  65 6e 6f 75  67 68 20 6d  65 6d 6f 72  Not enough memor
0x0123e08c: 79 0d 0a 0a  50 72 6f 67  72 61 6d 3a  09 43 3a 5c  y...Program:.C:\
0x0123e09c: 50 72 6f 67  72 61 6d 20  46 69 6c 65  73 5c 53 74  Program Files\St
0x0123e0ac: 61 72 63 72  61 66 74 5c  53 74 61 72  43 72 61 66  arcraft\StarCraf
0x0123e0bc: 74 2e 65 78  65 0a 46 69  6c 65 3a 09  53 46 49 4c  t.exe.File:.SFIL
0x0123e0cc: 45 2e 43 50  50 0a 4c 69  6e 65 3a 09  34 32 31 0a  E.CPP.Line:.421.
0x0123e0dc: 0a 0a 0a 50  72 65 73 73  20 4f 4b 20  74 6f 20 74  ...Press OK to t
0x0123e0ec: 65 72 6d 69  6e 61 74 65  20 74 68 65  20 61 70 70  erminate the app
0x0123e0fc: 6c 69 63 61  74 69 6f 6e  2e 00 00 00  00 00 00 00  lication........
0x0123e10c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e11c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e12c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e13c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e14c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e15c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e16c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e17c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e18c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e19c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e20c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e21c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e22c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e23c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e24c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e25c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e26c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e27c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e28c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e29c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e30c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e31c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e32c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

Code bytes:
0x1500e1df: cc 6a 01 e8  69 03 00 00  ff 15 58 25  03 15 8b 35  .j..i.....X%...5



------------------------------------------------------
PROGRAM VERSION: 1.0.0.0
COMPUTER NAME: kclark
TIME: 08/07/10 22:14:42
INFO: 

Exception code: 80000003 BREAKPOINT
Fault address:	1500E1DF 01:0000D1DF C:\Program Files\Starcraft\storm.dll

Registers:
EAX:00000000
EBX:01250040
ECX:1502E23C
EDX:00000000
ESI:00052011
EDI:00000002
CS:EIP:0073:1500E1DF
SS:ESP:007B:0123E03C EBP:0123E990
DS:007B ES:007B FS:0033 GS:003B
Flags:00000246
Call stack:
Address  Frame    Logical addr  Module
1500E1DF 0123E990 0001:0000D1DF C:\Program Files\Starcraft\storm.dll

Stack bytes:
0x0123e03c: 62 ed e3 8c  00 00 25 01  9c b3 02 15  54 68 69 73  b.....%.....This
0x0123e04c: 20 61 70 70  6c 69 63 61  74 69 6f 6e  20 68 61 73   application has
0x0123e05c: 20 65 6e 63  6f 75 6e 74  65 72 65 64  20 61 20 63   encountered a c
0x0123e06c: 72 69 74 69  63 61 6c 20  65 72 72 6f  72 3a 0a 0a  ritical error:..
0x0123e07c: 4e 6f 74 20  65 6e 6f 75  67 68 20 6d  65 6d 6f 72  Not enough memor
0x0123e08c: 79 0d 0a 0a  50 72 6f 67  72 61 6d 3a  09 43 3a 5c  y...Program:.C:\
0x0123e09c: 50 72 6f 67  72 61 6d 20  46 69 6c 65  73 5c 53 74  Program Files\St
0x0123e0ac: 61 72 63 72  61 66 74 5c  53 74 61 72  43 72 61 66  arcraft\StarCraf
0x0123e0bc: 74 2e 65 78  65 0a 46 69  6c 65 3a 09  53 46 49 4c  t.exe.File:.SFIL
0x0123e0cc: 45 2e 43 50  50 0a 4c 69  6e 65 3a 09  34 32 31 0a  E.CPP.Line:.421.
0x0123e0dc: 0a 0a 0a 50  72 65 73 73  20 4f 4b 20  74 6f 20 74  ...Press OK to t
0x0123e0ec: 65 72 6d 69  6e 61 74 65  20 74 68 65  20 61 70 70  erminate the app
0x0123e0fc: 6c 69 63 61  74 69 6f 6e  2e 00 00 00  00 00 00 00  lication........
0x0123e10c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e11c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e12c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e13c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e14c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e15c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e16c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e17c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e18c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e19c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e1fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e20c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e21c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e22c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e23c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e24c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e25c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e26c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e27c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e28c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e29c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ac: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2bc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2cc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2dc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2ec: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e2fc: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e30c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e31c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0x0123e32c: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

Code bytes:
0x1500e1df: cc 6a 01 e8  69 03 00 00  ff 15 58 25  03 15 8b 35  .j..i.....X%...5



```

---

### Post by kr651129 on 2010-08-08
Well I gave up on wine and figured I would try out cedega and that errors out on me to so it sounds like I have a courrupt libray somewhere here is the dialog I get when trying to install

```

"The following file could not be installed on your current access privileges:

comctl32.dll

If you continue, the Starcraft Map Editor will not function properly until a recent version of this file is installed."

```

and here is the terminal output

```
kclark@krisbox:~$ cedega
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
wine: Unhandled exception, starting debugger...
WineDbg starting on pid 11
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x7000e550
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libntdll.so' (0x7001f000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwine.so' (0x701a3000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwine_unicode.so' (0x701bc000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwine_port.so' (0x702b9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x702d2000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x702f8000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x70452000)
No debug information in ELF '/lib/tls/i686/cmov/librt.so.1' (0x7046c000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x70475000)
No debug information in ELF '/lib/ld-linux.so.2' (0x70000000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libcrtdll.so' (0x704b9000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libuser32.so' (0x704ce000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libgdi32.so' (0x7061c000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libpsapi.so' (0x702c6000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libadvapi32.so' (0x706a3000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libtggraphics.so' (0x706d4000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libcomdlg32.so' (0x70726000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwine_uuid.so' (0x70782000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libshell32.so' (0x70797000)
No debug information in ELF '/lib/libpng12.so.0' (0x7081a000)
No debug information in ELF '/lib/libz.so.1' (0x7083f000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libole32.so' (0x70854000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/librpcrt4.so' (0x708b9000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libshlwapi.so' (0x708fb000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libcomctl32.so' (0x70934000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwinspool.drv.so' (0x709cc000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libversion.so' (0x70805000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/liblz32.so' (0x70811000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwineserver.so' (0x709e7000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0x70a54000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libx11drv.so' (0x70b68000)
No debug information in ELF '/home/kclark/.cedega/.winex_ver/winex-2010071/winex/lib/libwine_tsx11.so' (0x70aca000)
No debug information in ELF '/usr/lib/libSM.so.6' (0x70aea000)
No debug information in ELF '/usr/lib/libICE.so.6' (0x70af3000)
No debug information in ELF '/usr/lib/libXxf86vm.so.1' (0x70b0c000)
No debug information in ELF '/usr/lib/mesa/libGL.so.1' (0x70be4000)
No debug information in ELF '/usr/lib/libGLU.so.1' (0x70c49000)
No debug information in ELF '/usr/lib/libXext.so.6' (0x70cba000)
No debug information in ELF '/usr/lib/libX11.so.6' (0x70cca000)
No debug information in ELF '/lib/libuuid.so.1' (0x70b12000)
No debug information in ELF '/usr/lib/libXdamage.so.1' (0x70b17000)
No debug information in ELF '/usr/lib/libXfixes.so.3' (0x70b1b000)
No debug information in ELF '/lib/libdrm.so.2' (0x70de7000)
No debug information in ELF '/lib/libgcc_s.so.1' (0x70ee8000)
No debug information in ELF '/usr/lib/libxcb.so.1' (0x70f07000)
No debug information in ELF '/usr/lib/libXau.so.6' (0x70f21000)
No debug information in ELF '/usr/lib/libXdmcp.so.6' (0x70f25000)
No debug information in ELF '/usr/lib/dri/i965_dri.so' (0x71008000)
No debug information in ELF '/lib/libexpat.so.1' (0x70f2b000)
No debug information in ELF '/lib/libdrm_intel.so.1' (0x70f52000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0x70f5c000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0x70f66000)
No debug information in ELF '/lib/tls/i686/cmov/libnss_compat.so.2' (0x70fb4000)
No debug information in ELF '/lib/tls/i686/cmov/libnsl.so.1' (0x70fbc000)
No debug information in ELF '/lib/tls/i686/cmov/libnss_nis.so.2' (0x70fd3000)
No debug information in ELF '/lib/tls/i686/cmov/libnss_files.so.2' (0x70fdd000)
No debug information in 32bit DLL 'C:\Program Files\Starcraft\StarCraft.exe' (0x00400000)
No debug information in 32bit DLL 'C' (0x70064000)
No debug information in 32bit DLL 'C' (0x77038000)
No debug information in 32bit DLL 'C' (0x78000000)
No debug information in 32bit DLL 'C' (0x704c4000)
No debug information in 32bit DLL 'C' (0x702c9000)
No debug information in 32bit DLL 'C' (0x706b6000)
No debug information in 32bit DLL 'C' (0x706d9000)
No debug information in 32bit DLL 'C' (0x7063b000)
No debug information in 32bit DLL 'C' (0x70502000)
No debug information in 32bit DLL 'C' (0x708d3000)
No debug information in 32bit DLL 'C' (0x7086a000)
No debug information in 32bit DLL 'C' (0x7090e000)
No debug information in 32bit DLL 'C' (0x70941000)
No debug information in 32bit DLL 'C' (0x707b1000)
No debug information in 32bit DLL 'C' (0x709d5000)
No debug information in 32bit DLL 'C' (0x7072e000)
No debug information in 32bit DLL 'C' (0x70814000)
No debug information in 32bit DLL 'C' (0x70808000)
No debug information in 32bit DLL 'C' (0x15000000)
No debug information in 32bit DLL 'C' (0x70b7d000)
No debug information in 32bit DLL 'C' (0x02000000)
In 32-bit mode.
Modules:
Address			Module	Name
0x00400000-0069c400	(PE)	C:\Program Files\Starcraft\StarCraft.exe
0x02000000-02010600	(PE)	C
0x15000000-1503a400	(PE)	C
0x70064000-701a3000	(PE)	C
0x702c9000-702cf000	(PE)	C
0x704c4000-704ce000	(PE)	C
0x70502000-7061c000	(PE)	C
0x7063b000-706a3000	(PE)	C
0x706b6000-706d4000	(PE)	C
0x706d9000-70726000	(PE)	C
0x7072e000-70782000	(PE)	C
0x707b1000-70805000	(PE)	C
0x70808000-70811000	(PE)	C
0x70814000-70819000	(PE)	C
0x7086a000-708b9000	(PE)	C
0x708d3000-708fb000	(PE)	C
0x7090e000-70934000	(PE)	C
0x70941000-709cc000	(PE)	C
0x709d5000-709e7000	(PE)	C
0x70b7d000-70be4000	(PE)	C
0x77038000-770b9000	(PE)	C
0x78000000-78046000	(PE)	C
Threads:
process  tid      prio
00000011 (D) C:\Program Files\Starcraft\StarCraft.exe
	00000010    1 <==
	00000015    0
	00000014    0
	00000012    0
WineDbg terminated on pid 11


```

and I get the same errors if I run as sudo, any thoughts?

---

### Post by kr651129 on 2010-08-09
I was thinking after reading a post that said switching the /etc/fstab from auth to vfat helped the preformance but still gave errors.  But that was on an 8.04 ubuntu.  So my thought is....could I be getting these errors because I selected an encrypted drive on the ubuntu install?  Can anyone confirm this idea or does it even make sence?

---

### Post by kr651129 on 2010-08-09
bump

---

### Post by kr651129 on 2010-08-10
So I replaced the comctl32.dll in ~/.wine/drive_c/windows/system32 with a downgraded older version of the dll and now I don't get that error message in wine anymore now the command line output to shows this

```
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
```

and instead of erroring out on comctl32.dll in cedega it just stops at the point of install for that dll and waits


I also don't know if wine looks like it wants it install because I adjusted some compiz settings or not...

---

### Post by kr651129 on 2010-08-10
I also get this now

```
kclark@krisbox:~/.wine/drive_c/Program Files/Starcraft$ ./StarCraft.exe
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\comctl32.dll" (error=80)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:iphlpapi:NotifyAddrChange (Handle 0x62de8d8, overlapped 0x62de8e0): stub
wine: configuration in '/home/kclark/.wine' has been updated.

```

---

### Post by kr651129 on 2010-08-13
So i reinstalled my system to start clean from an older version of wine.  I'm getting the same errors in 1.0, 1.2, and 1.3.  Do you think that the installation source could be corrupt?

---

### Post by kr651129 on 2010-08-14
So I got another source copy of starcraft and I no longer have that error.  It installs on cedega and wine...and runs.  Then wine crashes and I have some graphics problems.  Will update soon

---

### Post by kr651129 on 2010-08-14
Runs in wine fine now after updates but I don't care for the resolution.  Cedega is running it perfect you just need to make sure to select windows 98 or lower.  As far as I can tell it was just a bad iso.

---

