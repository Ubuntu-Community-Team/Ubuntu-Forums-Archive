---
title: "I installed VirtualBox...do i need virus protection for windows?"
date: 2007-12-17
forum: Virtualisation
---

### Post by hopelessone on 2007-12-17
Hi,

im installing windows in VirtualBox...

do i need to install anti virus? for the virtual windows?

thanks

---

### Post by gfg on 2007-12-17
It wouldn't hurt, but if you download all the updates, it really isn't necessary. If you stay away from dangerous websites, and don't download suspicous stuff, you should be okay. And if you happen to get a virus, it will only hurt your virtual windows install, and not your Ubuntu system. I myself have been running windows without anti-virus and so far I've had no problems at all.

---

### Post by anaconda on 2007-12-17
yes you do.  Windows in a virtual box is just as vulnerable as a "real" windows. Actually virtual windows machines are often used for testing windows viruses..

Unless you do the same than I.. my virtual windows doesn't have a network connection (by default)! So it is pretty safe.

Another solution is to use restore points, so that even if you get a virus you can restore your virtual machine to a previous state..  preferably a virus free state.

---

### Post by bvanaerde on 2007-12-17
For example: if a keylogger gets installed on your "virtual Windows installation", it's still possible that your passwords and other protected data will be revealed.
So you can't just think you're safe when using VirtualBox...

---

### Post by LarryJ2 on 2007-12-17
I've been listening to the podcast Security Now with Steve Gibson.  Based on that, it seems to me that you would want to do a snap shot of your updated WinXP SP2+ with Anti Spam and Anti Virus programs installed.   Get this snapshot before you troll the internet and by all means install firefox with the NoScript extension so it's included in your snapshot.

Then each time you fire up WinXP in your virtual machine using VirtualBox, start from the "virgin" snapshot.   That should give you an uncontaminated machine for a little while. :-}

---

### Post by nowshining on 2007-12-17
it depends, if u just want to have fun and don't input any personal info in thru the virtualbox, then no, if other then yes. :)

---

### Post by viking777 on 2007-12-17
Do you really need to connect to the internet with windows?

I *never* let windows connect to the internet nowadays I just do everything online in Linux. If I am ever unfortunate enough to have to boot windows for real I unplug the phone line from the router beforehand and my virtualbox copy is configured to not have internet access. 

You probably have a good reason for wanting to do this, but I would make absolutely sure that whatever it is cant be done with Linux first. Connecting to the internet with Windows is too dangerous without a battery of anti-this,that and everything else tools even in a virtual machine.

---

### Post by rickycodie on 2007-12-17
i don't have any anti virus and haven't had any problems, but i don't use the internet except for gspace.

---

### Post by bodhi.zazen on 2007-12-17
Unless you disable internet access to the virtual machine, which is what I would advise, you need to take the same precautions with virtual machines as you would with physical machines.

---

### Post by derby007 on 2007-12-18
Myself & a co-worker had an argument/discussion about how SAFE are these virtual OS's. He was convinced that the host could get infected (via MEMORY, ie. both OS's are using same physical memory) by a virus thru the guest OS. 
Is this possible, do ye think ?

---

### Post by bodhi.zazen on 2007-12-18
> **derby007 said:**
> Myself & a co-worker had an argument/discussion about how SAFE are these virtual OS's. He was convinced that the host could get infected (via MEMORY, ie. both OS's are using same physical memory) by a virus thru the guest OS. 
Is this possible, do ye think ?

Well, anything is possible. What you are asking would be highly unlikely.

---

### Post by hopelessone on 2007-12-19
On all your advice i installed:

AVG Anti-Spyware and Anti-Virus protection...

Many thanks..

---

### Post by matrixfox on 2008-02-13
what is impossible?
away for a virus to infect linux is through the root account correct??
so how could a windows virus corrupt the linux user account through visualbox? if your not running it in a root account? how could it bypass the keyring admin password?

---

### Post by hopelessone on 2008-02-13
you misunderstood...i was talking about the windows part only ...linux will be safe for the better part..Virtualbox only has user access set..

---

### Post by Sockerdrickan on 2008-02-14
[http://free.grisoft.com](http://free.grisoft.com)

---

