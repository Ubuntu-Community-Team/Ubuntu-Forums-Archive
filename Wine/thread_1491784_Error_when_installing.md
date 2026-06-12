---
title: "Error when installing"
date: 2010-05-24
forum: Wine
---

### Post by aprillia99 on 2010-05-24
wine /home/kyle/Desktop/LeagueOfLegendsDownloader04_27_2010.exe
fixme:system:SetProcessDPIAware stub!
Log file is being written to C:\users\kyle\Temp\LeagueOfLegendsDownloader04_27_2010.exe.log
wine: cannot find L"C:\\windows\\system32\\c++filt.exe"


Anyone know what this means?

---

### Post by hikaricore on 2010-05-24
I would suspect that it means wine cannot find C:\windows\system32\c++filt.exe
On a less obvious note you should check the appdb to see if your program actually works
with wine before driving yourself insane trying to get something to run that may not.

---

