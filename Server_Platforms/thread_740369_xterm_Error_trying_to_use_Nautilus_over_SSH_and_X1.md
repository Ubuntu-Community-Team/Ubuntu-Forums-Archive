---
title: "xterm: Error trying to use Nautilus over SSH and X11 from OS X"
date: 2008-03-30
forum: Server Platforms
---

### Post by vsiege on 2008-03-30
Im trying to use xterm that I installed on OS X (10.4.11) to SSH into my Ubuntu server (7.10), then use nautilus. I seem to be able to SSH with no problem. When I try to get nautilus working I get the below message> me@server:~$ gksudo nautilus

(gksudo:5991): Gdk-WARNING **: Connection to display localhost:10.0 appears to b
e untrusted. Pointer and keyboard grabs and inter-client communication may not w
ork as expected.
The program 'gksudo' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 130 error_code 3 request_code 25 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.) At this point I'm not sure what to do.

---

### Post by pseudo-random on 2008-03-30
So you're attempting to start an X session over SSH?
That's not the right way to go about it.
You can Tunnel X over SSH but it involves setting up local port forwarding etc on the remote server.
[http://www.ubuntu-unleashed.com/2008/03/howto-create-ssh-tunnel-for-firefox-to.html](http://www.ubuntu-unleashed.com/2008/03/howto-create-ssh-tunnel-for-firefox-to.html)

---

### Post by vsiege on 2008-03-30
> So you're attempting to start an X session over SSH?Yes.

Im not looking to use firefox to start using nautilus. I was told to install the X11 server on my mac to achieve this. Otherwise what else is xterm good for?

---

