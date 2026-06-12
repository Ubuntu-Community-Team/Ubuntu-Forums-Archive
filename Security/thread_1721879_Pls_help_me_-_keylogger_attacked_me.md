---
title: "Pls help me - keylogger attacked me"
date: 2011-04-05
forum: Security
---

### Post by Ayzenlawl on 2011-04-05
hey :) i got a probelm this is my 2nd post . 3 days ago i was attacked by a keylogger ;( and i tryed to fix it but i didn't :( instaled other win 7 vistas or etc but still didn't work . now i instaled ubuntu 10.10  and i scaned with klamAV and i discovered some files that can't be accesed , i never heard of them maybe is the keylogger ? can u help me get rid of him  ? pl0x  i really need help

---

### Post by Soul-Sing on 2011-04-05
> with klamAV and i discovered some files that can't be accesed

hi,
which files?

---

### Post by Ayzenlawl on 2011-04-05
[ATTACH]188133[/ATTACH] this and id if u don't see the pic its says  : Can't Scan /proc/1/fd-Access Denied

---

### Post by ajgreeny on 2011-04-05
I think that is because anything in /proc is a virtual file, and there is really nothing there to scan.  You have also chosen the floppy disk from proc, and if there is no disk in the drive there will certainly be nothing to scan.

Rest assured this is nothing to do with the key-logger you may have had in Windows, and there is probably no need to have Klamav on your system if you don't have Windows on the machine any more.

---

### Post by Ayzenlawl on 2011-04-05
Most of them are /lost+found , /root /tmp/.esd-133 /tmp/orbit-gdm  then /proc/sys/fs/binfmt_misc/cli  and i guess /proc/sys/fs/binfmt_misc/register are some  registry and on windows registry are the place where the keylogger hide :(( thx for the info anyway and i got a laptop not a pc :D

---

### Post by psusi on 2011-04-05
/proc contains information about what processes are running, and other misc information and control knobs for the running system.  You should not be scanning it.

---

### Post by Ayzenlawl on 2011-04-05
eh i scanned  home Folder and  System Folder  thats all . Ok so i won't be that fool :D thx

---

