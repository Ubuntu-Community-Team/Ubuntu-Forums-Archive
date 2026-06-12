---
title: "strange errors"
date: 2009-03-01
forum: Wine
---

### Post by uBuNNtu on 2009-03-01
Hi,

I installed the newest version of wine and I am trying now to get one windows application started in my ubuntu unfortunely without success.
I am getting the following errors during the start process :

err:module:import_dll Library LANGLIB.dll (which is needed by...) not found
err:module:import_dll Library MFC42.DLL (which is needed by ....) not found
err:module:LdrInitializeThunk Main exe initialization 

Well, now I achieved to fix these bugs and the application can be started but as far as I begin to use it, the application would closed. What can be here the problem for this?

The console is showing this output :

00000017 
	00000018    0
Backtrace:
=>1 0x7bc47040 in ntdll (+0x37040) (0x0032b2bc)
  2 0x004095aa in ed (+0x95aa) (0x00000000)
wine: Call from 0x4095aa to unimplemented function MFC42.DLL.6907, aborting


thanks in advance

uBuNNTu

---

