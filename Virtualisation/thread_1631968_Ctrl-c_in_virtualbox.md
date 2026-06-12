---
title: "Ctrl-c in virtualbox?"
date: 2010-11-27
forum: Virtualisation
---

### Post by GhostC10 on 2010-11-27
I've changed my host key to not be control and I still can't get it to pass a ctrl-c to virtualbox. I searched and looked through some threads for answers, but came up with nothing. Surely I'm missing something simple?

---

### Post by CharlesA on 2010-11-27
What host are you using?

I've been able to use Ctrl + C in VirtualBox for a while now (right ctrl key, as left ctrl is host key)

---

### Post by GhostC10 on 2010-11-27
I'm hosting an install of 10.10 server with 10.10 desktop. It simply puts a 'c' on the screen whenever I try to press ctrl-c.

---

### Post by CharlesA on 2010-11-27
Does it do that with either ctrl key?

---

### Post by GhostC10 on 2010-11-27
Yes, with either ctrl key. Quite vexing, and a little annoying to have to reboot every time a put to my crappy ftp server locks up.

---

### Post by CharlesA on 2010-11-27
Does anything using the Ctrl key work? Ctrl + Z?

---

### Post by davidjsmith67 on 2011-03-13
SOLUTION FOUND

I had the same issue with Ctrl C key etc.

I'm running Ubuntu host (10.4 / 32bit) and Virtual Box with Ubuntu OS for quick testing and the Ctrl-C wouldn't abort - all Ctrl keys were not being recognised.

I found the solution is to disable the Ctrl-key "mouse" function on the Ubuntu host (10.4) 

System -> Preferences -> Mouse -> Show position of pointer when Ctrl key is pressed in the host 

Turn this off and the Terminal Ctrl-C returns! :D

---

### Post by CharlesA on 2011-03-13
Interesting. Thanks for posting a solution. :)

---

### Post by atz6975 on 2011-10-12
This helped me solve the Ctrl-C/V within Virtual box not working.
My guest is XP and my host is 11.04.
I'm surprised that the Mouse settings "superseeds" the VirtualBox keyboard management.
This doesn't happen with VMware Workstation 7.1x (never seen it even before 71x).

Thank you.

---

### Post by pxyco on 2012-02-09
it works!!!!!!
Thank you davidjsmith67, i've been looking for a solution so long ago

Ubuntu 11.04 with Windows XP virtual box

---

### Post by 3L33T on 2013-01-04
> **davidjsmith67 said:**
> SOLUTION FOUND

I had the same issue with Ctrl C key etc.

I'm running Ubuntu host (10.4 / 32bit) and Virtual Box with Ubuntu OS for quick testing and the Ctrl-C wouldn't abort - all Ctrl keys were not being recognised.

I found the solution is to disable the Ctrl-key "mouse" function on the Ubuntu host (10.4) 

System -> Preferences -> Mouse -> Show position of pointer when Ctrl key is pressed in the host 

Turn this off and the Terminal Ctrl-C returns! :D

Bravoooo Bravoooo!!!

Thanks David!  This fixed the annoying problem I've been having on my ubuntu 10.04LTS host with Virtualbox and RHEL vm!!!

Thank you!!!

---

### Post by bala150985 on 2013-07-11
> **davidjsmith67 said:**
> SOLUTION FOUND

I had the same issue with Ctrl C key etc.

I'm running Ubuntu host (10.4 / 32bit) and Virtual Box with Ubuntu OS for quick testing and the Ctrl-C wouldn't abort - all Ctrl keys were not being recognised.

I found the solution is to disable the Ctrl-key "mouse" function on the Ubuntu host (10.4) 

System -> Preferences -> Mouse -> Show position of pointer when Ctrl key is pressed in the host 

Turn this off and the Terminal Ctrl-C returns! :D


Thanks a million this fixed my problem of copying and pasting on New Gmail Compose. This is how you fix it in newer version of ubuntu.

[ATTACH=CONFIG]244599[/ATTACH]

---

### Post by olivier-roulet on 2013-08-05
It seems the option has disapeard in 13.10 so if you had it enabled before upgrade you will need to use dconf-editor and search for "locate-pointer" option and set it off. (org.gnome.setting-daemon.peripherals.mouse)
Now it works! thanks.

---

### Post by GoRien on 2013-10-22
Thank you very much guys!! I've spent days to solve this problem, and this solution solved my ctrl+c problem in my windows guest. As sysadmin in putty window the lack of ctrl+c was a really painful lack. Thanks again guys!! :)

---

### Post by djk44883 on 2014-07-01
ubuntu 14.04 / linux mint 17 and I still need to do this... thanks for figuring this out years ago for us!

---

### Post by machiel-4 on 2014-09-12
> **davidjsmith67 said:**
> SOLUTION FOUND

I had the same issue with Ctrl C key etc.

I'm running Ubuntu host (10.4 / 32bit) and Virtual Box with Ubuntu OS for quick testing and the Ctrl-C wouldn't abort - all Ctrl keys were not being recognised.

I found the solution is to disable the Ctrl-key "mouse" function on the Ubuntu host (10.4) 

System -> Preferences -> Mouse -> Show position of pointer when Ctrl key is pressed in the host 

Turn this off and the Terminal Ctrl-C returns! :D


Hi Guys, I know this is an old post, but it just helped me out with this same issue after 2 days of searching for an answer. 

Thank you for this one.

---

### Post by jweber53 on 2014-09-20
Thanks, the dconf-editor answer is the one I needed!

---

