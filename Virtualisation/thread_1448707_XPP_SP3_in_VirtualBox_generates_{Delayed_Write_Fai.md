---
title: "XPP SP3 in VirtualBox generates {Delayed Write Failed} error"
date: 2010-04-07
forum: Virtualisation
---

### Post by Simon Cropper on 2010-04-07
Hi,

After much searching I think I have uncovered a work around for the following problem.

Host: Ubuntu 9.10
Guest: WinXP Pro SP3 (bridged network)
Software: VirtualBox OSE v. 3.0.8_OSE_r53138 although appeared also with latest release v. 3.1
Problem: Pop up appears when using various packages with following message.

[INDENT]{Delayed Write Failed} Windows was unable to save all the data for the file \Device\LanmanRedirector. The data has been lost. This error may be caused by a failure of your computer hardware or network connection. Please try to save this file elsewhere.[/INDENT]

Full details of error in Event Viewer are...

[INDENT]Event Type:	Warning
Event Source:	MRxSmb
Event Category:	None
Event ID:	50
Date:		07/04/2010
Time:		10:36:30 AM
User:		N/A
Computer:	SIMONXP
Description:
{Delayed Write Failed} Windows was unable to save all the data for the file \Device\LanmanRedirector. The data has been lost. This error may be caused by a failure of your computer hardware or network connection. Please try to save this file elsewhere.

For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).
Data:
0000: 04 00 04 00 02 00 56 00   ......V.
0008: 00 00 00 00 32 00 04 80   ....2..€
0010: 00 00 00 00 0c 02 00 c0   .......À
0018: 00 00 00 00 00 00 00 00   ........
0020: 00 00 00 00 00 00 00 00   ........
0028: 0c 02 00 c0               ...À    

For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).
Data:
0000: 00040004 00560002 00000000 80040032
0010: 00000000 c000020c 00000000 00000000
0020: 00000000 00000000 **c000020c** 
[/INDENT]

Googling this error takes you to numerous sites and solutions. None worked. Note that the last 'word' is **c000020c**.

The basic setup of Ubuntu was to use the default disk format (Linux Ext4 Version 1.0) and use Nautilus to share the directory. These shared directories were then mounted in Windows XP to a drive letter.

As I could trigger the error at will, I was able to verify if a particular solution worked. After many weeks of searching, applying fixes, updating VirtualBox, fiddling with Ubuntu I read a post that mentioned that Samba was more stable than NFS and I considered whether the error was due to the inability of Windows XP to directly interact with Linux Ext4. Consequently I reconfigured the system so that all shares used Samba. 

:P So far I have been unable to trigger the error anymore.

Consequently I consider this issue fixed and thought posting the solution might save others the heartache I have gone through.

Simon

---

