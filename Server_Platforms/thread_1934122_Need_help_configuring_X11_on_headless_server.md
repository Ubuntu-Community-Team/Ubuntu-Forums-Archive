---
title: "Need help configuring X11 on headless server"
date: 2012-03-01
forum: Server Platforms
---

### Post by MuleHeadJoe on 2012-03-01
Server hosted in "the cloud", Ubuntu 11.04, headless (no monitor).
 
Want to run gui-based software (SoapUI) on it and export the display to my workstation (workstation is Ubuntu 11.10). SoapUI requires java and x11. I installed openjdk and xorg (installs succeeded with no error messages) but I can't get xserver to run.
 
Ran 'sudo xinit' to start xserver, got this:
 
Fatal server error:
no screens found
Please consult the The X.Org Foundation support 
at [http://wiki.x.org](http://wiki.x.org)
for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
 
I read the indicated logfile 'Xorg.0.log' and nothing in there was meaningful to me. I searched wiki.x.org and found no help there either. I am not sure how to troubleshoot this ... any advice would be appreciated.

---

### Post by VanJr on 2012-03-01
Is the display set?

```

export DISPLAY=hostname:0

```

in where host name is the hostname (or IP addy) of your station?

---

