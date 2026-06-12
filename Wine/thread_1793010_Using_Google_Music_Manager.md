---
title: "Using Google Music Manager"
date: 2011-06-28
forum: Wine
---

### Post by hellz99 on 2011-06-28
I'm getting this error:

```
err:module:import_dll Loading library ODBC32.dll (which is needed by L"Z:\\home\\bob\\Downloads\\MusicManager\\log4cxx.dll") failed (error c000007b).
err:module:import_dll Library log4cxx.dll (which is needed by L"Z:\\home\\bob\\Downloads\\MusicManager\\MusicManager.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\bob\\Downloads\\MusicManager\\MusicManager.exe" failed, status c0000135
```

Running ubuntu 10.04 32bit, wine 1.3.21 

I'm guessing the dlls are not being found although they are in the same dir as my exe where I'm executing the wine command. Also copied them to the system32 just for the heck of it. Still no dice.

Anyone have any ideas? I've seen people talk about getting this working, but sure if they're running a newer ubuntu version or wine or what.

---

### Post by haqking on 2011-06-28
> **hellz99 said:**
> I'm getting this error:

```
err:module:import_dll Loading library ODBC32.dll (which is needed by L"Z:\\home\\bob\\Downloads\\MusicManager\\log4cxx.dll") failed (error c000007b).
err:module:import_dll Library log4cxx.dll (which is needed by L"Z:\\home\\bob\\Downloads\\MusicManager\\MusicManager.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\bob\\Downloads\\MusicManager\\MusicManager.exe" failed, status c0000135
```Running ubuntu 10.04 32bit, wine 1.3.21 

I'm guessing the dlls are not being found although they are in the same dir as my exe where I'm executing the wine command. Also copied them to the system32 just for the heck of it. Still no dice.

Anyone have any ideas? I've seen people talk about getting this working, but sure if they're running a newer ubuntu version or wine or what.


I dont know your answer.

However i posted to this thread earlier today see if there is any information of use

[http://ubuntuforums.org/showthread.php?t=1792776](http://ubuntuforums.org/showthread.php?t=1792776)

---

