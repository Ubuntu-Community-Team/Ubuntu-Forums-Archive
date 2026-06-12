---
title: "foobar2000"
date: 2010-03-05
forum: Wine
---

### Post by evanct on 2010-03-05
When I launch foobar2000 I get a blank window. Well, not exactly blank - it's like the window displays a screenshot of whatever was directly beneath it when it opened. like so:

[IMG]http://img221.imageshack.us/img221/9752/screenshothb.png[/IMG]

output is this, repeated more times than I care to count:
```
fixme:shell:DllGetClassObject failed for CLSID={a07034fd-6caa-4954-ac3f-97a27216f98a} (Query file associations)
err:ole:CoCreateInstance apartment not initialised
err:shell:SHCoCreateInstance failed (0x800401f0) to create CLSID:{a07034fd-6caa-4954-ac3f-97a27216f98a} (Query file associations) IID:{c46ca590-3c3f-11d2-bee6-0000f805ca57} (unknown)
err:shell:SHCoCreateInstance class not found in registry
```

followed by:

```
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:win:RegisterShellHookWindow (0x10034): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1e8,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1004a 0x00000000
err:ole:CoGetClassObject class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
err:ole:CoGetClassObject class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
err:ole:create_server class {1968106d-f3b5-44cf-890e-116fcb9ecef1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {1968106d-f3b5-44cf-890e-116fcb9ecef1} could be created for context 0x17

```

it just stays like this until i close it. any ideas?

---

### Post by Bwathke on 2010-03-05
1. Run with -opengl

2. Run in a "virtual desktop" In the graphics settings in WINE

3. Look [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18689](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18689) <<< For answers

---

