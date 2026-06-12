---
title: "How to use wine on ubuntu9.04"
date: 2010-04-29
forum: Wine
---

### Post by amirmku on 2010-04-29
Hi frends I m newbie and want to run some windows application using** WINE **I have it installed from synaptic package manager. but I dont know wht to do next and how to even use it. can anyone help me giving me detail explanation as to how to runany application on it.

Thanks in advance:confused:

---

### Post by Grenage on 2010-04-29
Have a look [here]("https://help.ubuntu.com/community/Wine").

---

### Post by amirmku on 2010-04-29
> **Grenage said:**
> Have a look [here]("https://help.ubuntu.com/community/Wine").

I tried running Firefox.exe present in wine C drive by command line
***wine firefox.exe***
But I got following error
err:module:import_dll Library xul.dll (which is needed by L"C:\\windows\\firefox.exe") not found
err:module:import_dll Library xpcom.dll (which is needed by L"C:\\windows\\firefox.exe") not found
err:module:import_dll Library nspr4.dll (which is needed by L"C:\\windows\\firefox.exe") not found
err:module:import_dll Library plc4.dll (which is needed by L"C:\\windows\\firefox.exe") not found
err:module:import_dll Library MOZCRT19.dll (which is needed by L"C:\\windows\\firefox.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\firefox.exe" failed, status c0000135

:confused:

---

### Post by cogadh on 2010-04-29
Did you install Firefox with Wine first? If so, then you didn't specify the application path correctly. If Firefox is installed with Wine correctly, then it should have added a shortcut to the Applications menu that you can use to launch it without have to worry about the application paths. More importantly, why would you install Firefox in Wine, Firefox does have a native Linux version installed by default in Ubuntu.

---

### Post by tyrod27 on 2010-04-29
Just to make sure that wine is running properly, try [here]("http://www.youtube.com/watch?v=hZgjgeDQVo4")

---

### Post by MelissaNBarkley on 2011-08-09
Hi amirmku,


Here is the mozcrt19.dll : [http://dllcentral.com/mozcrt19.dll/8.00.0000/]("http://dllcentral.com/mozcrt19.dll/8.00.0000/")&#8230;download it and then extract the downloaded zip file to the system32 folder which is located in windows folder (that is located in your main drive which contains the installed windows)

---

### Post by amirmku on 2011-08-10
solved, Thanks guys:)

---

