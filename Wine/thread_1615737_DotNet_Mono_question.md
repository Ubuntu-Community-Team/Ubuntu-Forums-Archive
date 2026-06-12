---
title: "DotNet Mono question"
date: 2010-11-07
forum: Wine
---

### Post by duke.tim on 2010-11-07
I have some windows programs that require .net . They didn't seem to work when I used winetricks to install mono-2.6 so I installed dotnet20. Which required me adding these registry values before I used winetricks
```
wine reg add "HKLM\Software\Microsoft\.NETFramework\policy\v2.0"
wine reg add "HKLM\Software\Microsoft\.NETFramework" /v InstallRoot
```
 It now works, my question is if I add mono will it be useful for any future programs or will DotNet20 be sufficent (at least for all of my dotnet2 requiring programs)
and will mono help or conflict with DotNet20 if I install both?(if I get time i'll test it)

Lastly it seems like wine is set as heading towards the use of mono, does it seem like that to anyone else?

---

