---
title: "SEAlert Error after installing SELinux"
date: 2011-05-26
forum: Security
---

### Post by DAB4970 on 2011-05-26
Installation: Ubuntu 10.04 Lucid Lynx 64 bit

Hello.  I just installed SELinux pkg, rebooted when prompted, and it returned an SEAlert notification "AVC Denial".

This is what the error says:

Opps, sealert hit an error!

Traceback (most recent call last):
  File "/usr/bin/sealert", line 972, in <module>
    run_as_dbus_service(username)
  File "/usr/bin/sealert", line 97, in run_as_dbus_service
    app = SEAlert(user, dbus_service.presentation_manager, watch_setroubleshootd=True)
  File "/usr/bin/sealert", line 597, in __init__
    from setroubleshoot.browser import BrowserApplet
  File "/usr/lib/pymodules/python2.6/setroubleshoot/browser.py", line 11, in <module>
    import gtkhtml2
ImportError: No module named gtkhtml2

I opened up Synaptic and searched for gtkhtml2 pkg and noticed "libgtkhtml3.14-19" pkg already installed.  What would this error mean?

---

### Post by spynappels on 2011-05-26
Sorry to rain on your parade, but SELinux on Ubuntu is just more pain than a mere mortal can cope with. It may eventually work, but it will never work easily or exactly as you expect, and lots of other things will stop working.

AppArmor is the program of choice on Ubuntu and Bodhi.Zazen has a great info page here: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by tgalati4 on 2011-05-26
If you want to play with SELinux, then use Fedora's implementation.  It works well enough, even though it's the first thing most folks turn off when installing Fedora.

---

### Post by bodhi.zazen on 2011-05-26
> **tgalati4 said:**
> If you want to play with SELinux, then use Fedora's implementation.  It works well enough, even though it's the first thing most folks turn off when installing Fedora.

+1, selinux is difficult tor impossible to configure on Debian or Ubuntu.

Selinux is much much better on Fedora, and there is both documentation on the Fedora wiki and graphical tools to help you manage selinux alerts and policy.

Also selinux has come a long way, and turning selinux off is no longer the first thing people do. The default (selinux) policies are very reasonable and many people never notice it is there, with the exception of a few alerts which are mostly harmless.

---

### Post by DAB4970 on 2011-06-27
Thanks for the suggestion in using AppArmor.  So I installed that.  Can someone lead me to managing it?  (if any configuring is needed after the installation)

Thanks.

---

### Post by nevius on 2011-06-27
> **DAB4970 said:**
> Thanks for the suggestion in using AppArmor.  So I installed that.  Can someone lead me to managing it?  (if any configuring is needed after the installation)

Thanks.

Follow the link in Post #2 above.

---

