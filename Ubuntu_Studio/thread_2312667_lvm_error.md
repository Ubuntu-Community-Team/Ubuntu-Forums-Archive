---
title: "lvm error"
date: 2016-02-06
forum: Ubuntu Studio
---

### Post by dj-d424 on 2016-02-06
i have an error
beheer@beheer-PDSBM:~$   system-config-lvm - GUI 
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::display after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  gnome.program_init (PROGNAME, VERSION)
The program 'system-config-lvm.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3028 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


how can fix this

---

### Post by steeldriver on 2016-02-06
Hello and welcome to the forums

AFAIK system-config-lvm doesn't have a "- GUI" option (if that's what you're trying to do)

Are you trying to run it on a desktop version of Ubuntu or a server version?

---

