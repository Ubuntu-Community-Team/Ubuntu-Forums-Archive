---
title: "Gnome-shell --replace error"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by floydsp on 2012-02-02
Gdk-ERROR **: The program 'gnome-shell' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 141 error_code 1 request_code 139 minor_code 66)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

I get this on my Precise when trying to run gnome-shell. started couple weeks ago any help appreciated

floydsp

---

### Post by Harry33 on 2012-02-02
> **floydsp said:**
> Gdk-ERROR **: The program 'gnome-shell' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 141 error_code 1 request_code 139 minor_code 66)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

I get this on my Precise when trying to run gnome-shell. started couple weeks ago any help appreciated

floydsp

Haven't seen that one on my setups.
Do you have any PPA's enabled or is it a clean Precise alfa installation?
Do you have a fully updated setup?

---

### Post by floydsp on 2012-02-02
I have Ricotz Testing PPA and its update from oneiric but like I said was working fine. I have another install to test with but wanted to find out the error here if I could.

Have unistalled gnome-shell and reinstalled but did not do any good

floydsp

---

### Post by ronacc on 2012-02-02
I am running an up to date 12.04 (64bit) with an Nvidia 7600 and Nvidia-current driver from the regular repos , no PPA and I am not seeing this with GS .

---

### Post by Harry33 on 2012-02-02
> **ronacc said:**
> I am running an up to date 12.04 (64bit) with an Nvidia 7600 and Nvidia-current driver from the regular repos , no PPA and I am not seeing this with GS .

Rigth,
I also have two clean installations of 12.04 (32-bit and 64-bit) with no PPA's enabled.
Then I have one 64-bit Precise installation with Gnome-shell testing PPA, Gnome3 PPA and Xorg-edgers PPA enabled.
All these are working fine here.

---

