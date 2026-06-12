---
title: "clam antivirus"
date: 2006-10-13
forum: Server Platforms
---

### Post by ckonrad on 2006-10-13
Hello

I installed clamav, i know i probably dont need it but i am just curious how it works, how do i run it and do a scan? I have tried clam and clamav, clam antivirus etc in the terminal but that doesnt do anything. I checked and it is installed on my system but when i type in whereis clam it shows that it isnt installed. What am i missing here?

Thanks

---

### Post by Rhubarb on 2006-10-13
Clamav in linux is a lot different to clamwin in windows (or any other av programme in windows).
While you can use clamav to scan individual files in the terminal, it's really designed to sit on an email server to scan emails.

There is a gui front end for clamav you can use (I haven't tried it, as I don't think you really need av for general linux use), it's called ClamTk:
[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

It's also possible to integrate clamav in nautilus by right clicking on a file and selecting scan.  It's floating around somewhere in these forums.

---

### Post by mitch.c on 2006-10-13
> **ckonrad said:**
> Hello

I installed clamav, i know i probably dont need it but i am just curious how it works, how do i run it and do a scan? I have tried clam and clamav, clam antivirus etc in the terminal but that doesnt do anything. I checked and it is installed on my system but when i type in whereis clam it shows that it isnt installed. What am i missing here?

To scan files in the current directory:
```
clamscan
```

To update definitions:
```
sudo freshclam
```

You don't need to worry about updating the definitions manually, the clamav package installs an init script that starts freshclam as a daemon, and checks several times a day.

To get command line help on either:
```
clamscan --help
freshclam --help
```

There is also a package called clamtk that will give you a nice little GUI front-end.



Good luck.

---

