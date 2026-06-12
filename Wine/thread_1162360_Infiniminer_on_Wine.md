---
title: "Infiniminer on Wine?"
date: 2009-05-17
forum: Wine
---

### Post by tsunamikitsune on 2009-05-17
I discovered a fun game called [_Infiniminer_]("http://www.zachtronicsindustries.com/pivot/entry.php?id=82") for Windows about a week ago that I can't seem to put down. The only problem is, I prefer to use Linux for my daily computing, so I'm not thrilled about having to boot into Windows every time I want to play this game.

So, I've been trying to get Infiniminer running under Wine in Ubuntu. The game requires the .NET 2.0 Runtime (which I installed through winetricks) and the XNA 3.0 Runtime (which I installed by downloading and running normally). Once I installed the runtimes, I installed Infiniminer and attempted to launch the client. Below is the terminal output:

```
kitsune@kitsune-desktop:~$ wine '/home/kitsune/.wine/dosdevices/c:/Program Files/Zachtronics Industries/Infiniminer/Infiniminer.exe'
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"msvcm80"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cff8,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game.resources"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game.resources"
```

It takes about 20-30 seconds for this to start showing up and once it does, I get the below message in a dialog box:

> No suitable graphics card found.

The device creation parameters contain invalid configuration options.

This program requires pixel shader 1.1 and vertex shader 1.1.

In the Graphics tab of my Wine Configuration, Vertex Shader Support is set to Hardware and the Allow Pixel Shader checkbox is checked. It might also be worth noting that both the Wine Configuration window and my other Wine applications (Notepad, for example) also take 20-30 seconds to open. This is probably unrelated to my problems running this game, but it's a little annoying nonetheless.

I'm not extremely familiar with Ubuntu or Linux in general (I've been using Ubuntu off and on very casually for the past few years), so I'm not really sure what to make of this. Any help would be deeply appreciated as this addicting game is the only reason I even have to revisit the nightmare that is my Windows partition on a regular basis.

---

### Post by asdfoo on 2009-05-17
you're starting the program incorrectly.

you have to cd to the install directory and then run

---

### Post by tsunamikitsune on 2009-05-17
> **asdfoo said:**
> you're starting the program incorrectly.

you have to cd to the install directory and then run

I'm having trouble changing to the game's directory (I think it's because there's a space in Program Files), so I don't know if that terminal information is helpful or not, but I do get the same 20-30 wait and dialog box when running the program from the Applications > Wine > Programs menu.

---

### Post by asdfoo on 2009-05-17
> **tsunamikitsune said:**
> I'm having trouble changing to the game's directory (I think it's because there's a space in Program Files), so I don't know if that terminal information is helpful or not, but I do get the same 20-30 wait and dialog box when running the program from the Applications > Wine > Programs menu.

You can tab complete the path when you type it

cd ~/.wine/drive_c/Progra<TAB>

It will insert a backslash \ before the spaces to escape them

---

### Post by tsunamikitsune on 2009-05-17
```
kitsune@kitsune-desktop:~/.wine/drive_c/Program Files/Zachtronics Industries/Infiniminer$ wine Infiniminer.exe
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"msvcm80"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cff8,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game.resources"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game.resources"
```

And this shows up after I click OK on the dialog box (I forgot to include it last time):

```
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub

```

---

### Post by asdfoo on 2009-05-17
Check that you're also using a new release of Wine, 1.1.21 is the latest release.

If it still doesn't work then it's likely that some of the .NET bugs in Wine are stopping this from working, it's still go awhile to go before .NET apps will work reliably.

I have heard that someone is working on a game very similar to infiniminer but in Java so that it will be run on Mac and Linux as well as Windows.

---

### Post by asdfoo on 2009-05-18
The developers blog is [http://notch.tumblr.com](http://notch.tumblr.com) - name of the game is minecraft

---

### Post by qwertymn on 2009-05-29
Hi, try the next coming out wine-version next week 1.1.23.
We fixed 3 bugs in wine (see [http://bugs.winehq.org/show_bug.cgi?id=18529](http://bugs.winehq.org/show_bug.cgi?id=18529), and [http://www.winehq.org/pipermail/wine-bugs/2009-May/178717.html](http://www.winehq.org/pipermail/wine-bugs/2009-May/178717.html)) and I got the game running now. Only thing is I don't hear any sound, but might be a problem on my side ( or is the game mute?)

---

