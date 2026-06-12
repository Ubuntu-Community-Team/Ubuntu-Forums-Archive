---
title: "installing patchs on wine 1.2 ?"
date: 2010-07-19
forum: Wine
---

### Post by gufide on 2010-07-19
Hi, I want to know how to install patch on wine1.2. I know that you have to compile it with the patch, but I have no idea how to do. I want to install acceptEx patch and desktop switching patch. I have these files:
[ATTACH]163968[/ATTACH]
[ATTACH]163969[/ATTACH]
I know that is txt files, but just rename to a .patch file.

---

### Post by mc4man on 2010-07-20
Whether advisable to do so for several reasons can't say, and one part of one patch fails so you'd need to manually investigate.

For the acceptex I'd open in a text editor and remove the heading, may not matter but I would.
Ex. top of file should be 
> diff --git a/dlls/ws2_32/socket.c b/dlls/ws2_32/socket.c
index 2eb5837..1693583 100644
--- a/dlls/ws2_32/socket.c
+++ b/dlls/ws2_32/socket.c
<rest of patch>

Then rename acceptex.diff and desktop_switching.diff and  place them in the wine1.2 source folder
cd to to source folder in a terminal and run at the prompt
```
patch -p1 < ./acceptex.diff
```
```
patch -p1 < ./desktop_switching.diff
```

The 2nd patch in the desktop patch will fail - you'll need to see why...

> doug@doug-desktop1:~/Desktop/winep/wine1.2-1.1.42$ patch -p1 < ./acceptex.diff
patching file dlls/mswsock/mswsock.spec
patching file dlls/ws2_32/socket.c
Hunk #1 succeeded at 248 (offset 45 lines).
Hunk #2 succeeded at 307 (offset 53 lines).
Hunk #3 succeeded at 1386 (offset 301 lines).
Hunk #4 succeeded at 2999 (offset 387 lines).
patching file dlls/ws2_32/tests/sock.c
Hunk #1 succeeded at 2967 (offset 230 lines).
Hunk #2 succeeded at 2984 (offset 230 lines).
patching file dlls/ws2_32/ws2_32.spec

doug@doug-desktop1:~/Desktop/winep/wine1.2-1.1.42$ patch -p1 < ./desktop_switching.diff
patching file dlls/winex11.drv/event.c
Hunk #1 succeeded at 306 with fuzz 2.
Hunk #2 FAILED at 433.
Hunk #3 succeeded at 710 (offset 54 lines).
1 out of 3 hunks FAILED -- saving rejects to file dlls/winex11.drv/event.c.rej

What you'll be left with at this point is a partially patched dlls/winex11.drv/event.c, the orig event.c and the reject 
(you could delete the partial and rename the event.c.orig to event.c and forget this patch or ...


Taking a look in event.c you'll see the area to be patched has moved to line 460, the line to be replaced to line 467
You'll also notice that section has changed a bit, 2 if's have been added - see screen 1

So, **you could forget this**, or rewrite the patch or because it's just one line do the failed patch manually in event.c

If so then copy the line from the patch, careful to only copy the text
 see screen 2

And carefully highlight line 467 in event.c (screen 1) and replace with the coped text, should look like this  - screen 3


At the end of the day, because these patches seem a bit old, you may end up with a borked wine or it may not even build 

**also note these examples are from the maverick 10.10 source - the latest may yet again be different**

---

### Post by gufide on 2010-07-20
thank you! but I get another error in acceptex.diff:

```
guillaume@comput1:~/Downloads/wine-1.2$ patch -p1 <acceptex.dif
guillaume@comput1:~/Downloads/wine-1.2$ patch -p1 <acceptex.diff
patching file dlls/mswsock/mswsock.spec
patching file dlls/ws2_32/socket.c
Hunk #1 succeeded at 248 (offset 45 lines).
Hunk #2 succeeded at 294 (offset 53 lines).
Hunk #3 succeeded at 1372 (offset 302 lines).
Hunk #4 FAILED at 2319.
1 out of 4 hunks FAILED -- saving rejects to file dlls/ws2_32/socket.c.rej
patching file dlls/ws2_32/tests/sock.c
Hunk #1 succeeded at 3607 (offset 870 lines).
Hunk #2 succeeded at 3624 (offset 870 lines).
patching file dlls/ws2_32/ws2_32.spec
```
you know how to solve it?

---

### Post by gufide on 2010-07-20
ho! I forget, thats the reject:
```
--- dlls/ws2_32/socket.c
+++ dlls/ws2_32/socket.c
@@ -2319,27 +2026,9 @@
     break;
 
    case WS_SIO_GET_EXTENSION_FUNCTION_POINTER:
-   {
-        GUID acceptex_guid = WSAID_ACCEPTEX;
-        GUID acceptexsockaddrs_guid = WSAID_GETACCEPTEXSOCKADDRS;
-        if( IsEqualGUID(&acceptex_guid,lpvInBuffer) )
-        {
-            LPFN_ACCEPTEX *lpfvDummy = (LPFN_ACCEPTEX*)lpbOutBuffer;
-            *lpfvDummy = AcceptEx;
-            WSASetLastError(STATUS_SUCCESS);
-            return STATUS_SUCCESS;
-        }
-        if( IsEqualGUID(&acceptexsockaddrs_guid,lpvInBuffer) )
-        {
-            LPFN_GETACCEPTEXSOCKADDRS *lpfvDummy = (LPFN_GETACCEPTEXSOCKADDRS*)lpbOutBuffer;
-            *lpfvDummy = GetAcceptExSockaddrs;
-            WSASetLastError(STATUS_SUCCESS);
-            return STATUS_SUCCESS;
-        }
-        FIXME("SIO_GET_EXTENSION_FUNCTION_POINTER %s: stub\n", debugstr_guid(lpvInBuffer));
-        WSASetLastError(WSAEOPNOTSUPP);
-        return SOCKET_ERROR;
-   } 
+       FIXME("SIO_GET_EXTENSION_FUNCTION_POINTER %s: stub\n", debugstr_guid(lpvInBuffer));
+       WSASetLastError(WSAEOPNOTSUPP);
+       return SOCKET_ERROR;
 
    case WS_SIO_KEEPALIVE_VALS:
    {
```
That will help you I guess...

---

