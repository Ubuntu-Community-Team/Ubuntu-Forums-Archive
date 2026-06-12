---
title: "Wine Anarchy Online Issue"
date: 2008-12-17
forum: Wine
---

### Post by sayonora on 2008-12-17
Greetings,

I've been playing Anarchy Online for a while now, on a windows version. About 6 months ago, we decided that we'd had enough of the Microsoft incompetence, and changed to Linux Ubuntu. For as far as I've seen, I'd say its only slightly better (but that is me being a complete dummy in computers).

Now, to get back to the point :)
I wanted to continue playing Anarchy Online, so I layed my hands on a brandnew Wine. at first I copied my old Anarchy Online folder completely into the Wine c:// directory, but that didn't quite work...
So I decided I would do it the more catholic way, and ran the Install.exe trough wine.

The installation went fine, and as I was enjoying an ingame party in a vision, I tried to run Anarchy online, and well, it basicly just shut down.

heres what happens: I open anarchy.exe, trough wine, and I get the EULA.
I hit accept, and the "checking Integrity" window appears, but vanishes even faster than it appeared, and boom, no more anarchy online.

It keeps going this way, every time I try to start it up.
I have the latest Ubuntu, and the latest Wine version. I'm using the 17.9 Anarchy Online client version.

here's my anarchy.err:

```

[21:00:59] Checking integrity of files:

[21:00:59] Checksum for file 'AnarchyPatcher.exe' failed

[21:00:59] The file C:\Program Files\Funcom\Anarchy Online\AnarchyPatcher.exe is missing. Trying to copy from PatchesUndo.

[21:01:00] C:\Program Files\Funcom\Anarchy Online\AnarchyPatcher.exe was copied from PatchesUndo.

[21:01:00] Abort() was called

[21:01:00] Abort() was called


```
(I hope that helped)

I've browsed trough whole of google, looking for solutions, of wich none succeeded. I have allso browsed trough this very forum, and found a number of threads (both with cerega and wine), about people who have the same issue. None had an answer though.

Could anyone help me/us out please?

thanks on forehand.

---

### Post by djn808 on 2009-02-28
I know it's a dead thread. But I have the EXACT same dilemma.

I got AO running for awhile, but then the 18.0 Legacy of the Xan patch came out.

Tried re-downloading, patching and installing etc. multiple times, but in the end I always get the same outcome. 

I'm very sad, anyone else have the same problem now that 18.0 is out?
:(:confused:

---

### Post by loudog23 on 2009-03-29
Easy Setup, No script, all legal, no crash, Newbie proof, Not even a Terminal window! 15-20 Min + Patch and you play

'file&link' are sigle quoted
[Button] are bracketed
"select&Inputbox" are double quoted

1.Get Files
1.1 Get PlayOnLinux 'http://www.playonlinux.com/en/download.html'
1.2 Get 'AdvancedWineConfiguration_3.5.1.pol' (bottom of download page)

2.Install and run PlayOnLinux
2.1 Install PlayOnLinux
2.2 (On Ubuntu) [application] -> "Games" -> "playonlinux"

3.Install Advanaced Wine Config (To enable -Opengl)
3.1 CLick [Install]
3.2 (Bottom left) click "Install a .pol package or an unsuppoerted application"
3.3 Select "Install a .pol package"
3.4 Browse to find 'AdvancedWineConfiguration_3.5.1.pol' you just downloaded
3.5 Click [Next] and complete instalation wizard

4.Install Ie4Linux (To Fix Patching Issue)
4.1 Click [Install]
4.2 Select "Internet" in the left Menu
4.3 Select "Internet Explorer 6" From the list on the right
4.4 Click [Apply] and Complete Installation Wizard

5.Install Anarchy Online
5.1 Click [Install]
5.2 (Bottom left) click "Install a .pol package or an unsuppoerted application"
5.3 Select Manual Installation -> [Next] -> [Forward]
5.4 Select "Edit an application already installed" -> [Forward]
5.5 Select "ie6" -> [Forward] -> [No]
5.6 Browse to find the Anarchy Installer.exe ('AnarchyOnline_17.9.1_EP1_EP2_EP3.exe') -> [Open] -> [Forward]
5.7 Complete Anarchy Instalation Wizard -> [Forward]
5.8 At the "Do you want to create a shortcut ..." click [Yes]
5.9 Browse to find 'Anarchy.exe' -> [Open] -> [Forward]
5.10 Type a Name for your shortcut
5.11 Select Desktop and/or Menu (or none if you only want it in the Playonlinux window)
5.12 Second time you get the "Do you want to create a shortcut ..." click [No]

6.Tweaks (Enable Sound and Open GL)
6.1 Select your AnarchyOnline shortcut (Inside playOnLinux)
6.2 Click [Configure this Application]
6.3 [Forward] -> Select "Configure wine" -> [Forward]
6.4 Tab[Audio] -> Set your sound (default works of me) -> [Apply] -> [Ok]
6.5 Select "Use advanced wine configuraiton plugin" -> [Forward]
6.6 [Forward] -> Select your AnarchyOnline Shorcut -> [Forward]
6.7 select "DirectDrawRender" -> [Forward]
6.8 select "OpenGl" -> [Forward] -> ...Wait... -> [Forward]
6.9 [Cancel] to exit config menu

7.Play
7.1 Select your anarchyonline shortcut -> [run]

THEORY

In order to get the patcher to work you need Internet explorer from windows. I found a thread where it make you intal ie4linux and run the Anarchyonline in the ei4linux Wineprefix. Since Playonlinux makes separate Prefix for each game and allow you to insert more than one application in the same prefix, you can by default get you AO running inside Ie4linux prefix.

Other Benifit
PlayOnLinux also provide you with nice plug in and tools totweak your game, if you know your way around i suggest you take a peak at the advance wine config.

Enjoy, Lou

---

