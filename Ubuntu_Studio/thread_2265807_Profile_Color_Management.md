---
title: "Profile Color Management"
date: 2015-02-17
forum: Ubuntu Studio
---

### Post by francesco23 on 2015-02-17
Hi, How do I manage color profiles in ubuntu studio?
 GNOME Color Manager in Ubuntu Studio does not seem like a  "manager"... It's just color profiles viewer ...
 After installing DispcalGUI to create a color profile of my monitor I can not find or import it into gnome color manager.
 What should I do to manage color profiles? Should I change distro?
 Up to this time Ubuntu Studio does not seem the right choice for professional graphics.

---

### Post by tgalati4 on 2015-02-18
A few links to consider:

[http://askubuntu.com/questions/571423/import-icm-color-profile-from-windows](http://askubuntu.com/questions/571423/import-icm-color-profile-from-windows)

[http://askubuntu.com/questions/8755/modify-monitor-color-profiles-settings](http://askubuntu.com/questions/8755/modify-monitor-color-profiles-settings)

[https://help.ubuntu.com/stable/ubuntu-help/color-howtoimport.html](https://help.ubuntu.com/stable/ubuntu-help/color-howtoimport.html)

[https://help.ubuntu.com/stable/ubuntu-help/color.html](https://help.ubuntu.com/stable/ubuntu-help/color.html)

Chances are your display came with a Windows utility to "calibrate" your device and save the color profile for future use.  You can then import the ICC or ICM file into linux to achieve the same color match.  Unfortunately, the tools to modify color profiles are quite limited in Linux, so one needs to rely on the Windows utilities (via dual-boot or a Windows virtual machine).  Once the profiles are generated for a given workflow, they won't change until the monitor ages out or the lighting conditions change or the printer or other output device changes.  

Yes, Ubuntu Studio may not be the right choice, but if you understand its capabilities, it might work well for a specific graphic workflow.

---

