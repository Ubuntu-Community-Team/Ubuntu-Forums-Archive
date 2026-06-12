---
title: "ies4linux installation error: X Window System error"
date: 2010-09-27
forum: Wine
---

### Post by bitteralmond on 2010-09-27
I get this error when installing ies4linux. I have wine1.0 installed, but it says I have an older version. When I proceed with the installation anyway, I get an X Window System error.

```
bitteralmond@ubuntubox:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 3385 error_code 1 request_code 0 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
bitteralmond@ubuntubox:~/ies4linux-2.99.0.1$ 
```How do I fix this?

I am using Lucid. I am trying to install ie6. Wine version is 1.0.1, specifically. I tried wine1.2 first, but I got a similar error and that's why I tried to downgrade to 1.0.

EDIT: Tried with wine1.2 again, and this is the error:
```
bitteralmond@ubuntubox:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 3400 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
bitteralmond@ubuntubox:~/ies4linux-2.99.0.1$ 
```EDIT2: Solved through searching through forums. I had to use:
```
./ies4linux --no-gui
```(But flash doesn't work.)

---

### Post by rvw on 2010-12-06
I'm trying to get IE running on 10.10, but IE6 crashes each time I open another page than the startpage, and IE7 starts to download something, then crashes. IE5 and IE5.5 don't even install (with --no-gui). 

Do you have it running normally?

---

### Post by rvw on 2010-12-06
I've got it fixed by installing PlayonLinux. That works a lot better, including IE7.

---

