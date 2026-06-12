---
title: "[SOLVED] Using SeamlessRDP with VirtualBox?"
date: 2008-01-31
forum: Virtualisation
---

### Post by jjsonp on 2008-01-31
I just found [this article]("http://www.linux.com/feature/124908") describing using SeamlessRDP to access Windows apps in a virtual machine running on Linux. However the instructions are for VM-Ware, and I'm using VirtualBox (with an XP Pro guest under Ubuntu 7.10 - works great!).

I followed the basic instructions, but when I run the rdesktop command from xterm i just get a message saying the keyboard is EN-US or something; no Windows apps appear.

I enabled remote access on the Windows VM. I ran ipconfig to get the IP number. The VirtualBox is running as root, and I've tried using both a terminal and an xterm as root and my normal user. But whatever I try, when I run this:
rdesktop -A -s "c:\seamless\seamlessrdpshell.exe notepad" 10.0.2.15 -u [My Win Username] -p [My Win Password]

I get this in the terminal, and nothing else happens:
"Autoselected keyboard map en-us"

Okay, very weird...as I was typing this, Notepad appeared! It worked! But after literally several minutes. The xterm says: ERROR: connect: Connection timed out
$
$ notepad

So I guess it's *sort of* working...but if apps take 3-4 minutes to launch I don't know how useful that is.

If anyone has gotten SeamlessRDP working with VirtualBox I'd be most appreciative of an outline of the steps.

---

### Post by Rompalle on 2008-02-01
lots of people have this setup. See the thread below

[http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP]("http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessRDP")

---

### Post by jjsonp on 2008-02-02
I found a [site]("http://www.itvidya.com/how_to_run_windows_and_linux_at_one_place") that explains it very simply and I was able to get it working with no difficulty. I've summarized the steps below; amazing easy!

    *  Install [VirtualBox]("http://virtualbox.org/wiki/Downloads") and create a Windows XP virtual machine.
    * In the WinXP VM, open the registry editor (Start &#8594; Run &#8594; regedit) and press enter. Navigate to HKEY_CURRENT_ USER &#8594; Software &#8594; Microsoft &#8594; Windows &#8594; Current Version &#8594; Policies &#8594; Explorer. Right-click in the whitespace on the right panel, create a new DWORD entry and name it 'NoDesktop'; set its value to 1.
    * Inside the VM, select the top Devices menu and select Install Guest Additions. After the installation is complete, reboot the VM.
    * Log back into the VM, select the top Machine menu and select 'Seamless Mode'. To toggle seamless mode via keyboard, press (right) Ctrl+L.

---

