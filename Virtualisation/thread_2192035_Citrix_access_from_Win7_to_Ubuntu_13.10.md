---
title: "Citrix access from Win7 to Ubuntu 13.10"
date: 2013-12-05
forum: Virtualisation
---

### Post by bernhard-schreiner on 2013-12-05
Hello Everyone,

i am new to virtualization and i would like to get help in this forum here

What i want to do:
connect on a Win7 pc remotely to a Ubuntu 13.10(desktop version) pc working then with the Desktop of Ubuntu

searching through the internet i found NX (nomachine) or TightVnc - also Citrix Xenapp looks very good - but i am not sure if there is a free version

but to be honest it does not look like it is easy to setup (i have no experience with this tools - also i am not 100% if they would work for me)

So - does anyone have a suggestion to make this happen ? 

thx in advance

---

### Post by nikolapetkovic on 2013-12-05
You could try Teamviewer, it's available for Ubuntu and Windows.
Link: [http://www.teamviewer.com/en/download/windows.aspx](http://www.teamviewer.com/en/download/windows.aspx)
Chosse Linux from above of they're website.

---

### Post by codenine75a on 2013-12-06
> **bernhard-schreiner said:**
> Hello Everyone,

i am new to virtualization and i would like to get help in this forum here

What i want to do:
connect on a Win7 pc remotely to a Ubuntu 13.10(desktop version) pc working then with the Desktop of Ubuntu

searching through the internet i found NX (nomachine) or TightVnc - also Citrix Xenapp looks very good - but i am not sure if there is a free version

but to be honest it does not look like it is easy to setup (i have no experience with this tools - also i am not 100% if they would work for me)

So - does anyone have a suggestion to make this happen ? 

thx in advance

ah! Citrix.  I loved setting up cirtrix on winterm devices.  It is NOT citrix that you need.  You are trying to remote to a another computer.  Yeah, you can try tightvnc. VNC has been around for quite a while.  The problem with using VNC is it is like using a hack or controlling the remote computer using viewing pane.  It is not actually an actual remote terminal application.  What happens is if the ubuntu machine has a user on it then you are viewing their session.  It is a little security thing.

---

### Post by bernhard-schreiner on 2013-12-08
Hi,

thanks for the hints - i will try teamviewer first.

thx again
B

---

