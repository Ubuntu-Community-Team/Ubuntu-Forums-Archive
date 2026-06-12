---
title: "ssh -X errors"
date: 2010-10-11
forum: Server Platforms
---

### Post by tad1073 on 2010-10-11
Ok, here is the error I get trying to open nautilus when I ssh-X into my server.

```
thomas@servthom:~$ nautilus
Initializing nautilus-gdu extension

(nautilus:1506): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 200 error_code 2 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by arrrghhh on 2010-10-11
Hrm... Well without more info are you forwarding it to another Linux box or a Windows box?

---

### Post by tad1073 on 2010-10-11
linux...10.10 server and 10.10 desktop

---

### Post by arrrghhh on 2010-10-11
Do you have problems with other X apps or just nautilus?

---

### Post by tad1073 on 2010-10-11
Its working now, go figure.

---

