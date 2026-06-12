---
title: "newbie wants help with wine"
date: 2009-01-20
forum: Wine
---

### Post by okeyletsdothis on 2009-01-20
First time ubuntu user here, damn windows crashed after installed service pack. Have download wine now and want the game warcraft 3 to work. have tried this:

> erik@ubuntu:~$ sudo wine \war3.exe --opengl
[sudo] password for jazz:
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\system32\\Storm.dll") not found
err:module:import_dll Library Storm.dll (which is needed by L"C:\\windows\\system32\\war3.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\system32\\war3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\war3.exe" failed, status c0000135
erik@ubuntu:~$ 

Now I no ide how to continue ^___^

---

### Post by mempman on 2009-01-20
You need to get winetricks.sh.  This is basically a script program that will allow you to download and install other "tools" that wine needs.  
The tool that I think you need is C++ assembler or something...you'll see when you get winetricks.  Do a quick search with msvcr80.dll and wine on google and you will find exactly what I'm talking bout.

---

### Post by donkyhotay on 2009-01-20
do *not* run commands with sudo unless you absolutely have to, it's a security risk and if you do the wrong thing or there's a really bad glitch (which often happens with wine) you can @#$% up your system. Just for your information wine *never EVER* needs to be run with sudo. In regards to the question about running war3 you do want to use winetricks. Here's a link to the site
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

//edit: Oh and this also should have been posted in the wine forum, you are more likely to recieve useful posts on wine there.

---

