---
title: "Xp in Ubuntu 7.04"
date: 2008-01-12
forum: Virtualisation
---

### Post by jakobtritten on 2008-01-12
This will be straightforward and to-the-point.  

(1)  For all intents and purposes, i'm a newb to Linux; but i love it and would like to eventually ditch Windows completely, if possible.  For now, i'm running a dual boot Ubuntu 7.04/XP Pro machine.  

(2)  As for virtualization, i'm just running into dead-ends.  For instance:  I spent about 20 minutes today following Raja's instructions on [http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html](http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html).  However, i only got to the part where you create a virtual machine.  When i try to START the machine, it opens a blank window with a little dialog box that says something like "Starting virtual machine."  And it just sits there for an indefinite amount of time, accessing my HDD like there's no tomorrow.  I let it sit for about 20 minutes and was only able to stop it with a hard reset of my computer.  I even tried following the process on my root account, but to no avail.  Same problem.  

(3)  Why is it that so many people talk about virtualization like it's such an easy task?  I suppose it would be easy for some of my LInux guru friends; but they're busy making money using their knowledge.  Is someone out there able and willing to help out someone who's an aspiring Linux user with very little Linux know-how?  

Thank you in advance for your assistance.

---

### Post by logos34 on 2008-01-12
I used VMWare Server to run XP on Feisty.  I found the official doc on the vmware site the most helpful.  

[http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

I didn't have all the much trouble setting it up.  Maybe I got lucky.


Here are the other links I relied on (although you've probably seen them already):

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)
[http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631)
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
[http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)
[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)
[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)
[http://ubuntuforums.org/showthread.php?p=2863026#post2863026](http://ubuntuforums.org/showthread.php?p=2863026#post2863026)
[http://www.vmware.com/support/player2/doc/releasenotes_player2.html](http://www.vmware.com/support/player2/doc/releasenotes_player2.html)

---

### Post by wolfvorkian1 on 2008-01-14
> **jakobtritten said:**
> This will be straightforward 
(3)  Why is it that so many people talk about virtualization like it's such an easy task?  I suppose it would be easy for some of my LInux guru friends; but they're busy making money using their knowledge.  Is someone out there able and willing to help out someone who's an aspiring Linux user with very little Linux know-how?  

Thank you in advance for your assistance.

Perhaps you started off wrong like I did. I tried with 'VmPlayer' first and had absolutely no luck. I chose it because it had more 'stars'  in Add-Remove than did VmWare Server.;-)  This turned out to be a fatal error for me. 

I did a bit of reading and tried again with VmServer and after a few hours of fiddling around I had a virtual machine with XP as the guest. It wasn't that hard, just like Logos34 said. 

I don't know much about computers and if I can do it, you can. I'm still wondering why I bothered though. The  one program that there is simply no Linux substitute for and I do need works reasonably well with Wine. I guess it was the challenge.

---

### Post by jakobtritten on 2008-01-14
Thanks to both of you for your help.  I have indeed spent hours upon hours of blood, sweat, and tears trying to figure out VMWare and make it work.  Not sure what i'm doing wrong.  I guess one thing i've found about Linux in general is that some things work for some people right away, while others have to do a lot to make the very same things happen.  I suppose it depends or your machine.  

I would appreciate any more advice.

Thanks again!

---

### Post by spur on 2008-01-14
I found it a lot easier to use Virtualbox.

---

