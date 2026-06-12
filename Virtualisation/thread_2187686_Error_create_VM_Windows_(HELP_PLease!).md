---
title: "Error create VM Windows (HELP PLease!)"
date: 2013-11-13
forum: Virtualisation
---

### Post by daemoncesar on 2013-11-13
[COLOR=#444444][FONT=Verdana]Fresh Ubuntu 13.10 server build with all the latest patches, installed Xen 4.3 and XCP-XAPI. Got Xenbr0 working properly and created an LVM storage repository and a CIFS ISO repository.[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]I can create VM's no problem at all but whenever I try to start them I get the following error from the log. Only Windows VM. The error comes up almost instantly when trying to start it. Not sure where to go to from here. Any help appreciated.[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]----------------[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana] Internal error: Xenctrl.Error [ memory 7225148 KiB free; to be scrubbed 0 KiB; total 8175 MiB]: 1: Operation not permitted[/FONT][/COLOR]

---

### Post by bashiergui on 2013-11-23
Dear Matt/ Caesar/ stomach/ smeagolll/ daemoncesar/ 


Dude..... I admire your persistence.


[http://web.archiveorange.com/archive/v/zCKz5wNrECbAIS4Icjsm](http://web.archiveorange.com/archive/v/zCKz5wNrECbAIS4Icjsm)


[http://xen.1045712.n5.nabble.com/Xen-4-2-on-Ubuntu-13-04-error-starting-VM-s-td5718439.html](http://xen.1045712.n5.nabble.com/Xen-4-2-on-Ubuntu-13-04-error-starting-VM-s-td5718439.html)


[http://www.linuxquestions.org/questions/linux-server-73/xen-start-vm-windows-%3D-problem-help-please-4175484442/](http://www.linuxquestions.org/questions/linux-server-73/xen-start-vm-windows-%3D-problem-help-please-4175484442/)


[http://irclogs.ubuntu.com/2013/11/13/%23ubuntu-server.html](http://irclogs.ubuntu.com/2013/11/13/%23ubuntu-server.html)


[http://translate.googleusercontent.com/translate_c?depth=1&nv=1&rurl=translate.google.com&sl=auto&tl=en&u=http://ubuntuforum-br.org/index.php%3Ftopic%3D109960.0&usg=ALkJrhgNuy5pTlhfIIHuBCyX5m77f9Mouw](http://translate.googleusercontent.com/translate_c?depth=1&nv=1&rurl=translate.google.com&sl=auto&tl=en&u=http://ubuntuforum-br.org/index.php%3Ftopic%3D109960.0&usg=ALkJrhgNuy5pTlhfIIHuBCyX5m77f9Mouw)

[http://ubuntuforums.org/showthread.php?t=2187585](http://ubuntuforums.org/showthread.php?t=2187585) 

[http://ubuntuforums.org/showthread.php?t=2187670](http://ubuntuforums.org/showthread.php?t=2187670)

Looks like you have root owning everything. Is root running XEN? You didn't want them all in the root group. you want the user running XEN to have permission to access the VM. And did you confirm that your vm hard disk is big enough to run? the error message seems to indicat you don't have enough space to run it. 
If you eliminated all thos possibilities then your best bet is: 

> Re: Desperate with XEN server (Create Windows machine)
«Reply # 2 on: November 17, 2013, 01:04»
So have many other users with this problem. Including in international fora. Seems to be a bug reported to the list of e-mail Xen. Verified if the xapi group is having the necessary permissions? The error has to do with the xcp-xapi.

---

