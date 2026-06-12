---
title: "Shalsum Mismatch?"
date: 2009-03-08
forum: Wine
---

### Post by Mashuteichou on 2009-03-08
Basically, I get this error when I try to load Framework 2.0

I type in "sh winetricks dotnet20".  Heres what happens...

----------------------------------
Setting Windows Version to Win2K

Executing wine regedit /home/phantom/.wine/drive_c/winetrickstmp/set-winver.reg

Executing cp -f /home/phantom/.winetrickscache/dotnet20/l.intl.nle /home/phantom/.wine/drive_c/windows/syystem32/

shalsum mismatch! Rename /home/phantom/.winetrickscache/dotnet20/dotnetfx.exe and try again
----------------------------------

Then it stops and asks for a command again.  

What do I change in the cache file?  Assuming thats what I do?  I found the "Load Dotnet20" part of it, and it has 3 "dotnetfx.exe" parts to it.  Do I rename these, delete the section, or what?

Heres that section of the cache...

-----------------------

load_dotnet20() {
    # Recipe from [http://bugs.winehq.org/show_bug.cgi?id=10467#c57](http://bugs.winehq.org/show_bug.cgi?id=10467#c57)
    test -d "$WINDIR/gecko" || load_gecko
    set_winver win2k
    # See [http://kegel.com/wine/l_intl-sh.txt](http://kegel.com/wine/l_intl-sh.txt) for how l_intl.nls was generated
    download dotnet20 [http://kegel.com/wine/l_intl.nls](http://kegel.com/wine/l_intl.nls)
    try cp -f "$WINETRICKS_CACHE"/dotnet20/l_intl.nls "$WINDIR/system32/"

    # [http://www.microsoft.com/downloads/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5](http://www.microsoft.com/downloads/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5)
    download dotnet20 [http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe](http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe) a3625c59d7a2995fb60877b5f5324892a1693b2a
    if [ "$WINETRICKS_QUIET"x = ""x ]
    then
       try $WINE "$WINETRICKS_CACHE"/dotnet20/dotnetfx.exe 
    else
       try $WINE "$WINETRICKS_CACHE"/dotnet20/dotnetfx.exe /q /c:"install.exe /q"
    fi
    unset_winver
} 

--------------------------------

---

### Post by cogadh on 2009-03-08
Why did you post a new thread with this? I just posted some steps that may address this issue in your initial thread on the problem:
[http://ubuntuforums.org/showthread.php?t=1089906](http://ubuntuforums.org/showthread.php?t=1089906)

---

### Post by Mashuteichou on 2009-03-08
> **cogadh said:**
> Why did you post a new thread with this? I just posted some steps that may address this issue in your initial thread on the problem:
[http://ubuntuforums.org/showthread.php?t=1089906](http://ubuntuforums.org/showthread.php?t=1089906)

Sorry, I posted it before you posted on the other one.  I thought I would post this question because I looked on google, "Shalsum Mismatch Ubuntu" and 1 page came up, and it was in Polish.   ^_^

---

