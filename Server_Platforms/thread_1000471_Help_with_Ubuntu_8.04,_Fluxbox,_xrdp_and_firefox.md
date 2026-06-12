---
title: "Help with Ubuntu 8.04, Fluxbox, xrdp and firefox"
date: 2008-12-02
forum: Server Platforms
---

### Post by battletux on 2008-12-02
Hi,

As per the title I have a VPS which is running ubuntu 8.04 server with fluxbox and xrdp.

The problem I am having is that when I run firefox I keep getting the following error:

The program 'firefox' recieved an X window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
 (Details: serial 79 error_code 1 request_code 146 minor_code 2)

I installed fluxbox with a simple apt-get install fluxbox and likewise for xrdp.  Both worked instantly with no tweaking.

Becuase it is just a bog standard fluxbox install (a wm I'm not too familier with) I want a webbrowser, firefox. It can be installed with apt without issue, but it just wont run.

Does anyone have any pointers on what I need to do to get this up and running?

The whole point in the setup is to have a remote 'desktop' that I can rdp to from anywhere, but mainly from work :P.

Thanks in advance.

---

### Post by kerry_s on 2008-12-03
did you install X? **sudo apt-get install xorg**
then> startx
to start fluxbox

---

### Post by battletux on 2008-12-03
> **kerry_s said:**
> did you install X? **sudo apt-get install xorg**
then> startx
to start fluxbox

Yes X is installed and started. Fluxbox works as I can RDP onto the server and am presented with the fluxbox desktop.

The problem is that firefox (or almost any GUI web browser it seems, except Dillo) wont start and gives me the error posted above.

---

### Post by battletux on 2008-12-08
bump....

---

### Post by alienConcept on 2010-03-12
Hi

The problem is with vnc server not xrdp.

You need to pass Xvnc the following parameter: -extension XFIXES

You can put this in your sesman.ini file - it should look something like:

```
[Xvnc]
param1=-bs
param2=-ac
param3=-nolisten
param4=tcp
param5=-extension
param6=XFIXES

```

The relevant bug in vnc is [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263)

---

### Post by kerry_s on 2010-03-12
a 2008 resurrection. ;)

---

### Post by alienConcept on 2010-03-12
Well its solved now for everybody :-)

---

