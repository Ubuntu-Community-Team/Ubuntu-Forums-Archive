---
title: "No puedo ver ningún tipo de video"
date: 2009-08-01
forum: Software
---

### Post by AlvaroV on 2009-08-01
Amigos tengo Ubuntu 9.04 y cuando trato der ver un video (MOD, mpeg, avi, ogv), los software de reproducción  (totem, VCL, Media Player) tratan de abrir el video y durante una decima de segundo incluso escucho el sonido pero luego se cierran.

Ejecute Totem con consola y esto me arrojo al cerrarse:

ddddd@dddddd:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

(totem:4034): GStreamer-CRITICAL **: 
Trying to dispose element test, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 93 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ddddd@dddddd-laptop:~$ 

*Mi  maquina es* un noteboocks HP 530 centrino.

---

### Post by AlvaroV on 2009-08-02
Solución: [https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html)

---

