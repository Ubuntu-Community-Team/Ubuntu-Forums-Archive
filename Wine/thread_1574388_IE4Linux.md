---
title: "IE4Linux"
date: 2010-09-14
forum: Wine
---

### Post by mahsom on 2010-09-14
Hello
I have problem with install IE4Linux.
recive this error :


```
The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 6668 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by 3rdalbum on 2010-09-14
If you are using RGBA transparency, add the script to your blacklist. (ies4linux-gta.py)

If you have no idea what RGBA is, then you are not using it.

---

### Post by philinux on 2010-09-14
Moved to Wine forum.

---

### Post by RavanH on 2010-10-30
> **3rdalbum said:**
> If you are using RGBA transparency, add the script to your blacklist. (ies4linux-gta.py)

If you have no idea what RGBA is, then you are not using it.

I ran into the exact same error today but I have absolutely NO idea what the "RGBA transparency script" is... 

Any other known cause/solution around?

Thanks :)

---

