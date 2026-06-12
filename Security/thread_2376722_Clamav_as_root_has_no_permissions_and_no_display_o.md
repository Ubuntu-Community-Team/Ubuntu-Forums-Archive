---
title: "Clamav as root has no permissions and no display of infected files"
date: 2017-11-05
forum: Security
---

### Post by smith73 on 2017-11-05
While running clamscan as root ~80 files can't be accesses by ClamAv due to lack of permissions (these are mainly in ~sys/drivers directory). I checked the permissions of some of them, and they are root:root.

Also after setting option -i in clamscan to display infected files, -enable-stats and detect PUAs, only the number of infected files (~80) is shown in final report, not an infected filename in a directory. While running clamtk, ~50 PUAs related to LibreOfficeMacro-2 are shown. I googled all of them and they are written about to be false positives, but clamscan via terminal doesn't display them (these probably are among the 80 infected).

Freshclam as root also can't be launched, displaying error messages regarding the lack of permissions to ~freshclam.log file (which has permissions root:root).

I didn't install Wine on Ubuntu Mate 16.04 and run Win8 twice only on Virtual Machine (and XP once). But I copied to hard disk several files for WIndows 8 (Win8.iso, some Win8 image for usbstick I never used which I was unable to delete from Desktop (it somehow disappeared), Win8 antivirus, Office and some utils) and don't know if clamav actually checked them, because it doesn't display infected files in the report.

Can anything be done?
(Ubuntu Mate 16.04 in dual boot with Win8)

---

### Post by ajgreeny on 2017-11-05
When you speak of permissions you are showing ownership only, not the full permissions.

I am also confused by your **/sys/drivers** folder, which I do not have and have never seen before, but if you really have such a folder please run command ls -l /sys/drivers which may show more useful info.

Perhaps you meant /sys/modules?

---

### Post by smith73 on 2017-11-06
Yep, I see, I was writing this from Windows so did not have access to the details. The directory may have had another name, but one of its sudirectories was related to drivers. Changing permissions to ~80 files for Clamav to access them would be a bit cumbersome, but maybe it's sort of ok for clamav? I heard from one Linux user that the mere necessity for Clamav to access files may make them sort of vulnerable.

I'd suppose the content of options after clamscan does not affect one another except for pipes, I ran clamscan with several runnable options and the option -i never displayed infected filenames in a directory if these had been spotted. If no infected files had been found but some error, it did not display the errors.

Also the option --leave-temps[=yes] displayed error and did not launch (similar to all options with [=yes/no] or [=0/1/2] syntax).

---

