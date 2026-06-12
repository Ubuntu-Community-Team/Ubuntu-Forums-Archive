---
title: "Everest Dictionary and libborqt"
date: 2011-02-01
forum: Ubuntu Studio
---

### Post by Regele IONESCU on 2011-02-01
Hello!

**I am having a miserable day trying to run Everest Dictionary.** One could download it from [http://www.vetrinait.com/modules/mydownloads/singlefile.php?lid=16](http://www.vetrinait.com/modules/mydownloads/singlefile.php?lid=16) .

Apparently the problem is caused by libborqt-6.9-qt2.3.so file. The program comes packed with that file. I copied it to /usr/lib but no success as instructed by program's author. I keep getting the following error:

```
symbol lookup error: /home/admiral/Everest/Everest: undefined symbol: initPAnsiStrings
```

If I run ldd ./ Everest from the application folder I get:

	```
linux-gate.so.1 =>  (0xf7782000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7646000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf762d000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7628000)
	libc.so.6 => /lib32/libc.so.6 (0xf74cd000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf74b3000)
	/lib/ld-linux.so.2 (0xf7783000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf74af000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf74a9000)

```

Please help me to make this application work.

---

### Post by ForrestUUID on 2011-02-01
Possibly

sudo ldconfig

at the command line will help.

Although if I copy it into /usr/lib32 instead of /usr/lib, it works without that step.

---

### Post by Regele IONESCU on 2011-02-02
> **ForrestUUID said:**
> Possibly

sudo ldconfig

at the command line will help.

Although if I copy it into /usr/lib32 instead of /usr/lib, it works without that step.

Now it works!!! Being on a 64 bit system I should have thought of moving that library into the 32 bit folder.

Thank you a thousand billion times!

---

