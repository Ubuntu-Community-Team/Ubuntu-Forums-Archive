---
title: "RoM (Runes of Magic) help"
date: 2009-08-11
forum: Wine
---

### Post by nixIT on 2009-08-11
Hello all,

I've read many of the posts on Runes of Magic, and even got as far as getting it to run very choppy on my POS work laptop, and also managed to get sound with a black screen on my home system (AMD X2 5400+ Radeon 3870).  However now I just get the following when I issue the following command:

wine client.exe

Here is what I get:

```

err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\mnt\\data\\games\\rom\\xerces-c_2_8.dll") not found
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"Z:\\mnt\\data\\games\\rom\\client.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\mnt\\data\\games\\rom\\client.exe" failed, status c0000135

```

I installed winetricks and had that install allfonts and d3dx9.  Not sure if I was supposed to, but it was mentioned in a thread.  I also saw a post somewhere, cannot find it anywhere, where it mentions to install vcrun something, but in winetricks there is more than one vcrun file, and I'm not sure which one to install since I cannot find the post anywhere.

any help... I would be happy to write a howto if we can all put our heads together and troubleshoot this.  

help.. please..

--nixIT

---

### Post by nixIT on 2009-08-12
On my work machine, where I can see the login screen, after I enter in my user name and password, the system appears to just sit there on the "Obtaining server list" dialong.

Any way to get past this?

--nixIT

---

