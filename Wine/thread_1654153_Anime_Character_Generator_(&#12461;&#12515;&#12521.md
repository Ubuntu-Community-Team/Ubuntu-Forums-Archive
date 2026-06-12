---
title: "Anime Character Generator (&#12461;&#12515;&#12521;&#12463;&#12479;&#12540;&#12394;&#12435;&#12392;&#12363;&#27231;)"
date: 2010-12-27
forum: Wine
---

### Post by Joseph Schwenker on 2010-12-27
After discovering Ren'Py, I discovered a Windows program called [&#12461;&#12515;&#12521;&#12463;&#12479;&#12540;&#12394;&#12435;&#12392;&#12363;&#27231;]("http://khmix.sakura.ne.jp/download.shtml") (commonly referred to as the Anime Character Generator) that allows you to create a character that you can use for a visual novel.  I tried running the program in Wine, but I got this mojibake error message:

> #Error 39
-->“à•”ƒGƒ‰[‚ª”*¶‚µ‚Ü‚µ‚½(39)

This is mojibake, or incorrectly rendered Asian text.  I searched around, and found [this thread]("http://ubuntuforums.org/showthread.php?t=383628").  After following all of step one except the part with Vera Sans YuanTi (it didn't work) and all of step 3, I was able to get the error message rendering correctly.  Using sysxp, I got these errors:

> &#25351;&#23450;&#12373;&#12428;&#12383;&#12487;&#12540;&#12479;&#12364;&#35211;&#12388;&#12363;&#12425;&#12394;&#12363;&#12387;&#12383;&#12398;&#12391;default&#12434;&#35501;&#12415;&#36796;&#12415;&#12414;&#12377;&#12290;

> #Error 39
-->&#20869;&#37096;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383;(39)

When I machine translated these, the errors seemed pretty generic, so I'm now at a dead end.  I do, however, have wineloc's output:

```
joseph@joseph:~$ wineloc -l ja_JP /home/joseph/Downloads/character_02.08/character.exe 
WineLocale 0.41 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
fixme:msvcrt:_setmbcp trail bytes data not available for DBCS codepage 0 - assuming all bytes
Executing application ...
fixme:atl:AtlAxWinInit semi-stub
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x5
Restoring old Wine locale settings
fixme:msvcrt:_setmbcp trail bytes data not available for DBCS codepage 0 - assuming all bytes
joseph@joseph:~$ 
```

Does anyone have any advice on how to get this working?

---

### Post by Joseph Schwenker on 2011-01-06
I'm not sure, but while I was experimenting with some different Wine settings, I managed to get this program working.  I'm not sure which of the things I did actually affected Wine, but when I tried to run the program from Wineloc (which you really should get, as it fixes all the mojibake), I got this error message when the program crashed.

```
fixme:msvcrt:_setmbcp trail bytes data not available for DBCS codepage 0 - assuming all bytes
```

After some searching, I found someone mentioning wsh56vb, which you have to install through Winetricks.  I did this, and when I changed my Windows version in Wine to Windows 2.0, the program worked, but none of its options did anything.  Again, I am not sure which options really impacted the program.  If anyone would like to test this further, then please do so.  I also found that changing the Windows version to under Windows NT 3.5 helps some other Japanese applications run.  What's more is that some Japanese applications will run only with Wine and not Wineloc.  So be sure to test your applications with both Wine and Wineloc.

In case anyone is interested, a screenshot of AnimeGen on Linux is attached.

---

### Post by Animiexoxo on 2011-12-11
> **Joseph Schwenker said:**
> After discovering Ren'Py, I discovered a Windows program called [&#12461;&#12515;&#12521;&#12463;&#12479;&#12540;&#12394;&#12435;&#12392;&#12363;&#27231;]("http://khmix.sakura.ne.jp/download.shtml") (commonly referred to as the Anime Character Generator) that allows you to create a character that you can use for a visual novel.  I tried running the program in Wine, but I got this mojibake error message:



This is mojibake, or incorrectly rendered Asian text.  I searched around, and found [this thread]("http://ubuntuforums.org/showthread.php?t=383628").  After following all of step one except the part with Vera Sans YuanTi (it didn't work) and all of step 3, I was able to get the error message rendering correctly.  Using sysxp, I got these errors:





When I machine translated these, the errors seemed pretty generic, so I'm now at a dead end.  I do, however, have wineloc's output:

```
joseph@joseph:~$ wineloc -l ja_JP /home/joseph/Downloads/character_02.08/character.exe 
WineLocale 0.41 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
fixme:msvcrt:_setmbcp trail bytes data not available for DBCS codepage 0 - assuming all bytes
Executing application ...
fixme:atl:AtlAxWinInit semi-stub
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x5
Restoring old Wine locale settings
fixme:msvcrt:_setmbcp trail bytes data not available for DBCS codepage 0 - assuming all bytes
joseph@joseph:~$ 
```Does anyone have any advice on how to get this working?



[SIZE=4]did you extract all files? [/SIZE]

---

### Post by Joseph Schwenker on 2011-12-11
> **Animiexoxo said:**
> [SIZE=4]did you extract all files? [/SIZE]

I'm not sure - this was nearly a year ago, and I no longer have wineloc nor Anime Character Generator.

---

