---
title: "Unable to play movies on Thinclient with LTSP on Ubuntu Edgy"
date: 2006-11-16
forum: Server Platforms
---

### Post by pointfre on 2006-11-16
Hi,

I have installed LTSP on a fresh Ubuntu Edgy (server version) with this how-to : [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

All works except VLC/Totem/Xine.
I have en error for the rendering with same error for all :

"received X error event: BadAccess (attempt to access private resource denied)"

and/or :

"The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 588 error_code 11 request_code 140 minor_code 18)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

My server is a Core2Duo with P5LD2-VM SE (Chipset Intel 945G Express).

I have same error with 2 Thin client :
1/ e-Box with SIS 550
2/ An old Celeron computer with an ATI Rage (with this I have try XSERVER = ati with no effect)

VLC/Totem/Xine works well on the server.

The problem seems to be that rendering used by VLC/Totem/Xine is not possible on deported X session.
But with VLC par example I have no result when I deactivated Xvideo renderer and replace by X11 renderer or other.

Two year ago i have worked with LTSP version 4 and Debian without this problem for read video on thin client.

If someone have the same problem or an idea ?

Thanks,
Emmanuel Chevallier

---

### Post by pointfre on 2006-11-16
With Kmplayer and Video Output selected with X11Shm that's work !

But it's very very slow how optimize it ?

Thanks,
Emmanuel Chevallier

---

