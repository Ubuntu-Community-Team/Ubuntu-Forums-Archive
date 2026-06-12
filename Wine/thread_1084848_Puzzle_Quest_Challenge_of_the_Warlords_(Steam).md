---
title: "Puzzle Quest: Challenge of the Warlords (Steam)"
date: 2009-03-02
forum: Wine
---

### Post by smcg on 2009-03-02
Hey

I've [checked the AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10277") and Google, but couldn't see any answers.

I bought PQ:CotW on Steam, and it doesn't run. It looks like it's an issue with OpenAL - if I'm reading this right, Wine thinks it's a 64-bit library? How can I get around this?

```
sean@fortaleza:~/.wine/drive_c/Program Files/Steam/steamapps/common/puzzle quest$ wine Puzzle\ Quest.exe 
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library OpenAL32.dll (which is needed by L"C:\\Program Files\\Steam\\steamapps\\common\\puzzle quest\\alut.dll") failed (error c000007b).
err:module:import_dll Library alut.dll (which is needed by L"C:\\Program Files\\Steam\\steamapps\\common\\puzzle quest\\FreeSL.dll") not found
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library OpenAL32.dll (which is needed by L"C:\\Program Files\\Steam\\steamapps\\common\\puzzle quest\\FreeSL.dll") failed (error c000007b).
err:module:import_dll Library FreeSL.dll (which is needed by L"C:\\Program Files\\Steam\\steamapps\\common\\puzzle quest\\Puzzle Quest.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steam\\steamapps\\common\\puzzle quest\\Puzzle Quest.exe" failed, status c0000135
```

---

### Post by HoverHell on 2009-04-18
It seems to be a problem with some specific OpenAL dll (I've got the same problem with Osmos Demo). Trying some other OpenAL.dll didn't help (although game at least tried to start w/o sound).
That might also be the problem with the newer wine version, but I can't test that yet right now.

---

### Post by smcg on 2009-05-23
The problem is that the OpenAL seems to think that Wine is 64-bit:
[http://bugs.winehq.org/show_bug.cgi?id=17897](http://bugs.winehq.org/show_bug.cgi?id=17897)

I found a workaround which got PQ working for me, which is to copy the 32-bit DLLs in the below file to the system32 directory.
[http://rapidshare.com/files/98104844/NR_OpenAL_AddOn.7z.html](http://rapidshare.com/files/98104844/NR_OpenAL_AddOn.7z.html)

```
sean@fortaleza:~/.wine/drive_c/windows/system32$ winedump OpenAL32.dll | grep Machine
Machine: 014C (i386)
sean@fortaleza:~/.wine/drive_c/windows/system32$ winedump wrap_oal.dll | grep Machine
Machine: 014C (i386)
```

---

