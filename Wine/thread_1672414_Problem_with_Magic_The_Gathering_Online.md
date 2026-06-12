---
title: "Problem with Magic The Gathering Online"
date: 2011-01-20
forum: Wine
---

### Post by magic_user on 2011-01-20
I'm trying to find a way to run MTGO without having to actually purchase Windows, and I figured WINE would be my best bet, but so far I'm not really getting anywhere. 

I'm running Lucid Lynx ( Ubuntu 10.04 LTS ) and I have WINE version 1.3.11 (installed with synaptic package manager)

I downloaded the MTGO installer, MTGOIII_Helper.exe, which downloaded and installed the game just fine. However, when I attempted to actually run the application through the created desktop icon, the system appears to be working "Starting Magic Online" but then stops abruptly. Upon further investigation, I tried launching the icon's target (Renamer.exe) from the command line and was told the following: 
wine: Install the Windows version of Mono to run .NET executables

Naturally, I installed the latest version of Mono (2.6.7) but I continue to get the same error message. What am I missing?

---

### Post by directhex on 2011-01-20
> **magic_user said:**
> I'm trying to find a way to run MTGO without having to actually purchase Windows, and I figured WINE would be my best bet, but so far I'm not really getting anywhere. 

I'm running Lucid Lynx ( Ubuntu 10.04 LTS ) and I have WINE version 1.3.11 (installed with synaptic package manager)

I downloaded the MTGO installer, MTGOIII_Helper.exe, which downloaded and installed the game just fine. However, when I attempted to actually run the application through the created desktop icon, the system appears to be working "Starting Magic Online" but then stops abruptly. Upon further investigation, I tried launching the icon's target (Renamer.exe) from the command line and was told the following: 
wine: Install the Windows version of Mono to run .NET executables

Naturally, I installed the latest version of Mono (2.6.7) but I continue to get the same error message. What am I missing?

The Windows version of Mono, inside wine, i.e. "wine ~/Downloads/mono-2.6.7-gtksharp-2.12.10-win32-2.exe" ?

---

### Post by magic_user on 2011-01-21
> **directhex said:**
> The Windows version of Mono, inside wine, i.e. "wine ~/Downloads/mono-2.6.7-gtksharp-2.12.10-win32-2.exe" ?


Umm... no. I used synaptic package manager to get Mono. How do I update the version of mono inside wine?

---

### Post by directhex on 2011-01-21
> **magic_user said:**
> Umm... no. I used synaptic package manager to get Mono. How do I update the version of mono inside wine?

Install it. There's no version of Mono inside Wine as standard. That's the point. Wine has its own, isolated virtual Windows environment, and to run apps in it, those need to be Windows apps (hence the Windows version of Mono, not the Linux version outside Wine)

---

### Post by magic_user on 2011-01-21
Ok, I've made some progress. I downloaded the following files from the mono project website:
[INDENT]mono-2.6.7-gtksharp-2.12.10-win32-2.exe
gtk-sharp-2.12.10.win32.msi[/INDENT]

Then, I was no longer getting the "you need mono" message. I got the following:

[INDENT]wine: Call from 0x7bc4bbc0 to unimplemented function libglib-2.0-0.dll.g_malloc_n, aborting
err:seh:setup_exception_record stack overflow 1804 bytes in thread 0009 eip 7bc5[/INDENT]

I tried installing some more packages from the Glib library, and now I get a similar error.
[INDENT]wine: Call from 0x7bc4bbc0 to unimplemented function libglib-2.0-0.dll.g_malloc_n, aborting
err:seh:setup_exception_record stack overflow 1804 bytes in thread 0009 eip 7bc53556 esp 00230c24 stack 0x230000-0x330000[/INDENT]

---

### Post by directhex on 2011-01-21
> **magic_user said:**
> Ok, I've made some progress. I downloaded the following files from the mono project website:
[INDENT]mono-2.6.7-gtksharp-2.12.10-win32-2.exe
gtk-sharp-2.12.10.win32.msi[/INDENT]

Then, I was no longer getting the "you need mono" message. I got the following:

[INDENT]wine: Call from 0x7bc4bbc0 to unimplemented function libglib-2.0-0.dll.g_malloc_n, aborting
err:seh:setup_exception_record stack overflow 1804 bytes in thread 0009 eip 7bc5[/INDENT]

I tried installing some more packages from the Glib library, and now I get a similar error.
[INDENT]wine: Call from 0x7bc4bbc0 to unimplemented function libglib-2.0-0.dll.g_malloc_n, aborting
err:seh:setup_exception_record stack overflow 1804 bytes in thread 0009 eip 7bc53556 esp 00230c24 stack 0x230000-0x330000[/INDENT]

Doesn't look like it'll work. You may get some mileage using winetricks to install Microsoft.NET

---

### Post by silverslyph on 2011-02-05
From what I've learned magic will not run in wine, but you should be able to run it through a virtual machine... I have been currently working on this process. Running ubuntu 10.04 for 64, using virtualbox prog, created xp machine and have installed magic, currently getting to launch screen, just installed all .NET framework, kinda stuck at this point but thought you might be able to run with it.

---

