---
title: "virtualbox folder sharing error"
date: 2008-05-28
forum: Virtualisation
---

### Post by alonips on 2008-05-28
i'm getting this error, when i write this in the terminal:
VBoxManage sharedfolder add "windowsxp" -name "Music" 
                   -hostpath "/home/bernardo/Music"

where (windowsxp) is my virtualmachine, (Music) the name of the folder i want to share, and (/home/bernardo/Music) the path to the folder.

what appears in the terminal is :
Syntax error: Not enough parameters
bernardo@bernardo-desktop:~$                    -hostpath "/home/bernardo/Music"
bash: -hostpath: command not found
bernardo@bernardo-desktop:~$ VBoxManage sharedfolder add "windowsxp" -name "Music" 
VirtualBox Command Line Management Interface Version 1.6.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Usage:

VBoxManage sharedfolder     add <vmname>|<uuid>
                            -name <name> -hostpath <hostpath>
                            [-transient] [-readonly]


Syntax error: Not enough parameters
bernardo@bernardo-desktop:~$                    -hostpath "/home/bernardo/Music"


help me please!!!

---

### Post by barnex on 2008-05-28
> **alonips said:**
> 
bash: -hostpath: command not found


It appears that you may have entered your code in two lines in the terminal, make sure there is no line break before '-hostpah'. 

Hope this helps.

PS: also check out: [http://ubuntuforums.org/showthread.php?t=810287](http://ubuntuforums.org/showthread.php?t=810287), virtualbox may have problems after the last kernel upgrade.

---

### Post by alonips on 2008-05-28
Can you please write me how you think it shoul be i have tried what you say but i am still not managing to find the folder in xp and error continues.
I reallu need a folder that's in a disk that belongs to ubuntu. because i would like to work with daemontools in windows to mount images. 
i want to understand first with the folder music how to share, files folder i don't know if it's possible to share disks or partition disks.
help me with that lines tu put in the terminal and in the run in windows.
regards

---

