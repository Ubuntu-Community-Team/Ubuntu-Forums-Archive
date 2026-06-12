---
title: "How do I load Winpe 3.0 over PXE?"
date: 2010-03-15
forum: Server Platforms
---

### Post by clivebuckwheat on 2010-03-15
over pxe, on my Ubuntu pxe server. Does any know what the file structure  should be in the tftpboot folder?

---

### Post by BobVila on 2010-03-15
> **clivebuckwheat said:**
> over pxe, on my Ubuntu pxe server. Does any know what the file structure  should be in the tftpboot folder?

It's a total PITA... I got it set up with the structure below, but I'm sure there are some redundancies, but none of the files are super big. It's living on a server that pxe's a bunch of other linux distros and tools, so I can't really blow it out and find out which files are absolutely necessary.

Following is my (working) setup:
/tftpboot
   tftpd.remap
   /Boot

/tftpboot/Boot
  abortpxe.com  
  BCD.LOG
  bootmgr.exe
  hdlscom1.n12
  hdlscom2.n12
  pxeboot.n12
  startrom.0
  WdsConfig.inf
  winpe.wim
  BCD
  boot.sdi
  hdlscom1.com
  hdlscom2.com
  pxeboot.com
  pxelinux.0
  wdsnbp.com
 
/tftpboot/Boot/Fonts
   wgl4_boot.ttf

/tftpboot/Boot/Boot
   BCD
   BCD.LOG

/tftpboot/Boot/Boot/Fonts
   wgl_boot.ttf

---

### Post by clivebuckwheat on 2010-03-15
I take it some of those files are from Microsoft's WDS. I just made a Winpe 3.0 using Microsoft's WAK and now I would like to put it on my Ubuntu PXE server. 

Where can I got those files if I do not have WDS?

---

### Post by BobVila on 2010-03-16
> **clivebuckwheat said:**
> I take it some of those files are from Microsoft's WDS. I just made a Winpe 3.0 using Microsoft's WAK and now I would like to put it on my Ubuntu PXE server. 

Where can I got those files if I do not have WDS?

I didn't take any files from WDS - they're all from the Win7 WAIK. I pxe install 2003, 2008, Vista, and 7 for dev testing, which is why I used the Win7 WAIK.

---

### Post by clivebuckwheat on 2010-03-16
Thanks, after I set up my directory structure, which file do you call from you PXE menu?

---

### Post by BobVila on 2010-03-16
startrom.0

---

### Post by clivebuckwheat on 2010-03-17
Thanks.

I have a question exactly where is startrom.0, and boot.sdi located? I looked in the WAIK. Also in your directory structure above what exactly is BCD?

a folder or a file?

sorry for my ignorance new to linux pxe booting.

---

### Post by BobVila on 2010-03-18
> **clivebuckwheat said:**
> Thanks.

I have a question exactly where is startrom.0, and boot.sdi located? I looked in the WAIK. Also in your directory structure above what exactly is BCD?

a folder or a file?

sorry for my ignorance new to linux pxe booting.

This link got me through most of the process:
[http://sysadminman.net/blog/2007/pxe-boot-winpe-2-vista-using-linux-as-the-pxe-server-8](http://sysadminman.net/blog/2007/pxe-boot-winpe-2-vista-using-linux-as-the-pxe-server-8)

---

### Post by clivebuckwheat on 2010-03-21
Hi

I been trying to boot Winpe 3.0 (aka Win7PE) over pxe boot using my Ubuntu tftp/pxe server.

I have gotten pretty far but I keep getting an error. Tell me what else can I or should I try to resolve this?



[IMG]http://img265.imageshack.us/img265/4012/screenshotn.png[/IMG]

---

### Post by uofaer on 2010-10-14
I think clivebuckwheat solved his problem on another forum but I want to have this here for anybody else having issues with tftp-hpa, pxe, and WinPE from working together.  This drove me nuts for 2 days.

For reference I am using Ubuntu 10.04 Lucid Lynx and I followed this guide:
[http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/](http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/)

I know this is a little old but I wasn't able able to boot into WinPE 3 over PXE either.  I was getting the same BCD error 0xc000000f .  I found my problem was that I was missing the remap file.  I created a file in my tftp server /srv/tftp/tftpd.remap and I then entered and saved the following text into the remap file:

**gr \\ /**

Lastly I edited the file /etc/default/tftpd-hpa to include the remap file in options as follows:
[B]
[COLOR=#000080]# /etc/default/tftpd-hpa  
TFTP_USERNAME="tftp"[/COLOR][B][COLOR=#000080] 
TFTP_DIRECTORY="/srv/tftp"[/COLOR][/B][COLOR=#000080]
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure -m /srv/tftp/tftpd.remap"

[/COLOR][/B]Don't forget to restart your tftp server by issuing the "sudo service tftpd-hpa restart" command!
[B][COLOR=#000080]
[/COLOR][/B]The above settings are what worked for me.  I posted this because it might be helpful to people in the future.

---

### Post by Maikey81 on 2011-07-25
That's a shame. The solution above did not help me solve the problem.
I'm still getting error 0xc000000f

[IMG]http://i51.tinypic.com/2rr00ah.png[/IMG]

My tftpd-hpa.remap contains the following lines:

```
re ^bootmgr\.exe Boot/bootmgr.exe
re ^BCD Boot/BCD
r ^\\Boot\\ Boot/
r ^\\boot\\ Boot/
rg \\ /
```And the info from the tftpd-hpa file itself:

```
# /etc/default/tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -m /etc/default/tftpd-hpa.remap -s /var/lib/tftpboot -vvv"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure -m /etc/default/tftpd-hpa.remap"
```Does anyone see a problem in this configuration? Contents of /var/lib/tftpboot:

/var/lib/tftpboot/
-bootmgr.exe
-pxeboot.com
-wdsnbp.0

/var/lib/tftpboot/Boot/
-abortpxe.com
-BCD
-boot.sdi
-bootmgr.exe
-hdlscom1.com
-hdlscom1.n12
-hdlscom2.com
-hdlscom2.n12
-pxeboot.com
-pxeboot.n12
-WdsConfig.inf
-wdsmgfw.efi
-wdsnbp.com
-winpe.wim

/var/lib/tftpboot/sources/
-boot.wim

Aditional info:

Using Wireshark I 've looked if the server sent information back to the client. Here's the result.
```
828    16.469297    192.168.100.100    192.168.100.254    TFTP    Read Request, File: \Boot\Fonts\wgl4_boot.ttf\000, Transfer type: octet\000, tsize\000=0\000
829    16.470242    192.168.100.254    192.168.100.100    TFTP    Error Code, Code: File not found, Message: File not found\000
830    16.476578    192.168.100.100    192.168.100.254    TFTP    Read Request, File: \boot\bcd\000, Transfer type: octet\000, tsize\000=0\000
831    16.477253    192.168.100.254    192.168.100.100    TFTP    Error Code, Code: File not found, Message: File not found\000
832    16.480127    192.168.100.100    192.168.100.254    TFTP    Read Request, File: \Boot\Fonts\wgl4_boot.ttf\000, Transfer type: octet\000, tsize\000=0\000
833    16.485938    192.168.100.254    192.168.100.100    TFTP    Error Code, Code: File not found, Message: File not found\000
```

---

### Post by Maikey81 on 2011-07-27
Nobody?

---

### Post by bogus_83 on 2011-07-29
It appears your BCD file was not created correctly. 
I was getting the same error 0xc0000001 and 0xc000000f and 0xc0000034. 
 
After much googling around I was able to find a very helpful site.
 
Go here [http://diddy.boot-land.net/pxe/index.htm](http://diddy.boot-land.net/pxe/index.htm) tons of info.
 
Download the guide and scripts / batchfiles to automate all the commands instead of copying and pasting by clicking on this link 
[http://diddy.boot-land.net/ccount12/click.php?id=3](http://diddy.boot-land.net/ccount12/click.php?id=3)
 
1. Once you download the guide, extract the contents to C:\PXE.
 
2. Install WAIK for Windows 7 
[http://www.microsoft.com/download/en/details.aspx?id=5753](http://www.microsoft.com/download/en/details.aspx?id=5753)
 
3. Install tftpd32
[http://tftpd32.jounin.net/](http://tftpd32.jounin.net/)
 
4. Browse to C:\PXE\Scripts and execute the 1_create_folders.cmd
 
5. Execute the 4a_WinPE.cmd script
 
6. This step creates the BCD file. Based on the WinPE architecture you are creating x86 or x64 you'll need to edit the 4b_WinPE.cmd script. Right-click; Edit.
[INDENT]The 5th line should read
```
 
SET bcdedit=%TOOLSDIR%\bcdedit%PROCESSOR_ARCHITECTURE%.exe

```
Change the %PROCESSOR_ARCHITECTURE% to the architecture of the WinPE image you are creating. Example if creating a x86 boot image the line should read 
```
SET bcdedit=%TOOLSDIR%\bcdeditx86.exe
```; if creating a x64 boot image the line should read ```
SET bcdedit=%TOOLSDIR%\bcdeditamd64.exe
``` Save and execute the script.
[/INDENT]7. Copy the pxeboot.n12 file from C:\PXE\tftpboot\Boot to C:\PXE\tftpboot
 
8. Once the file is copied rename it to pxelinux.0
 
9. Set your TFTP server working directory to C:\PXE\ftfpboot
 
10. Start PXE server and TFTP Server. Attempt PXE boot.

---

### Post by bogus_83 on 2011-07-29
My tftpboot directory contents
 
PS C:\pxe\tftpboot> ls

    Directory: C:\pxe\tftpboot

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/29/2011   2:36 PM            2008
d----         7/29/2011   3:38 PM            Boot
d----         7/29/2011   2:36 PM            disks
d----         7/29/2011   2:36 PM            menu.lst
d----         7/29/2011   2:36 PM            pe
d----         7/29/2011   2:48 PM            pxelinux.cfg
d----         7/29/2011   2:36 PM            seven
d----         7/29/2011   2:36 PM            vista
d----         7/29/2011   2:36 PM            win2k
d----         7/29/2011   2:36 PM            win2k3
d----         7/29/2011   2:36 PM            winxp
-a---         7/13/2009   8:26 PM     523328 bootmgr.exe
-a---         6/10/2009   4:15 PM      25772 pxelinux.0

PS C:\pxe\tftpboot> cd boot
PS C:\pxe\tftpboot\boot> ls

    Directory: C:\pxe\tftpboot\boot

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         6/10/2009   4:44 PM         79 abortpxe.com
-a---         7/29/2011   3:04 PM      12288 BCD
-a---         6/10/2009   2:44 PM    3170304 boot.sdi
-a---         7/13/2009   8:26 PM     523328 bootmgr.exe
-a---         6/10/2009   4:15 PM      26076 hdlscom1.com
-a---         6/10/2009   4:15 PM      26060 hdlscom1.n12
-a---         6/10/2009   4:15 PM      26076 hdlscom2.com
-a---         6/10/2009   4:15 PM      26060 hdlscom2.n12
-a---         6/10/2009   4:15 PM      25772 pxeboot.com
-a---         6/10/2009   4:15 PM      25772 pxelinux.0
-a---         6/10/2009   4:44 PM       1347 WdsConfig.inf
-a---         6/10/2009   4:44 PM      31124 wdsnbp.com
-a---         7/29/2011   3:36 PM  117382144 x86.wim
-a---         7/29/2011   2:48 PM  114851861 x86.wim.old

---

### Post by bogus_83 on 2011-08-17
Also, I found the BCD error is/can be caused by invalid TFTP settings or options. 
 
See the attached picture and set your TFTP server accordingly. ;)

---

### Post by mdshann on 2011-09-20
That's all well and good, but how did we go from using Ubuntu as the server to using windows as the server? I'm stuck with the same issue but your steps show how to use Windows as the server so they don't really help.

---

### Post by arbrandes on 2011-10-16
I followed this to get pxelinux working on Ubuntu 10.04:

[http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/](http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/)

And then this to make a WinPE image:

[http://xlshadow.livejournal.com/158711.html](http://xlshadow.livejournal.com/158711.html)

With these (and nothing else) I have successfully loaded WinPE 3.0 as served from Ubuntu.  Now, to try and install Windows! :)

---

