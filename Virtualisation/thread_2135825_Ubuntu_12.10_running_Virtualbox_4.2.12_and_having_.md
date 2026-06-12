---
title: "Ubuntu 12.10 running Virtualbox 4.2.12 and having problems connecting serial ports"
date: 2013-04-15
forum: Virtualisation
---

### Post by craigsn on 2013-04-15
I have 12:10 Ubuntu 64bit running with Win 7 32bit and all of the latest updates for both of them. I'm trying to run by Davis Weather Pro software in win7, and I need serial ports to connect the console to the computer. When I was running just Win 7, the ports on my card are Com4 and Com5. Now in Linux they appear to be ttyS4 and ttyS5. When I do a: 
@UbuDoo:~$ dmesg | grep ttyS
[ 0.480868] 0000:02:00.0: ttyS4 at I/O 0xdf00 (irq = 20) is a ST16650V2
[ 0.502741] 0000:02:00.1: ttyS5 at I/O 0xde00 (irq = 21) is a ST16650V2

So in my VMM serial setup I put
Port 1 - Enable Serial Port, Port Number - User-defined IRQ of 20 and I/O Port of 0xdf00, Port Mode - Host Device, Port/File Path - COM4:
Port 2 - Enable Serial Port, Port Number - User-defined IRQ of 21 and I/O Port of 0xde00, Port Mode - Host Device, Port/File Path - COM5:

In System Motherboard I have enabled the extended feature of IO APIC. 

But my VM will not start when I have these settings, I get a message dialog
Failed to open a session for the virtual machine Winch.
No error info.
Result Code: NS_ERROR_CALL_FAILED (0x800706BE)
Component: ProgressProxy
Interface: IProgress {c20238e4-3221-4d3f-8891-81ce92d9f913}

On the Virtualbox forum, it was suggested I do a different configuration, so I did this in Virtualbox


Port 1 - Enable Serial Port, Port Number - COM1 and the rest default, except for Port/File Path - /dev/ttyS4
Port 1 - Enable Serial Port, Port Number - COM2 and the rest default, except for Port/File Path - /dev/ttyS5


I save that and when I tried to run the VM, the screen blanks out and I get the following dialog and the VM doesn't start.


Failed to open a session for the virtual machine Winch.

Cannot open host device '/dev/ttyS4' for read/write access. Check the permissions of that device ('/bin/ls -l /dev/ttyS4'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user (VERR_ACCESS_DENIED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {db7ab4ca-2a3f-4183-9243-c1208da92392}

So after seeing this message, I looked for a device group, but there isn't any on my system, so that error message didn't help me. 
Did I get the setup right? Is there something else to try?

any help to get this working would be appreciated.
Craig

---

