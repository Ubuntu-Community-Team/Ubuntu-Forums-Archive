---
title: "windows equiv of 'sudo killall'"
date: 2006-12-28
forum: Windows
---

### Post by dbbolton on 2006-12-28
my brother installed ITUNES+QUICKTIME package on his windows box. here's what burns my biscuits- these programs automatically install and run qttask.exe, ituneshelper.exe, and ipodservice.exe upon boot.

i took care of the first two, but i can't kill the third one. in taskmgr, i can't kill it because its listed user is SYSTEM, and if i simply click 'end process', i get error message "access denied."

thoughts ?

---

### Post by Ex-XP on 2006-12-28
Go in via the Control Panel and open the Services (or open an MSC to get at them).  You should be able to find the evil Service in the list and shut it down.

---

### Post by Ex-XP on 2006-12-28
I'm trying to forget such things.....loving my Debian box, post-XP-ectomy.

---

### Post by Ex-XP on 2006-12-28
> **dbbolton said:**
> my brother installed ITUNES+QUICKTIME package on his windows box. here's what burns my biscuits- these programs automatically install and run qttask.exe, ituneshelper.exe, and ipodservice.exe upon boot.

i took care of the first two, but i can't kill the third one. in taskmgr, i can't kill it because its listed user is SYSTEM, and if i simply click 'end process', i get error message "access denied."

thoughts ?

To help you go and kill that Mofo:  [http://www.theeldergeek.com/services_guide.htm](http://www.theeldergeek.com/services_guide.htm)

Best of luck.

---

### Post by dbbolton on 2006-12-28
thanks, 

worked perfectly :)

---

### Post by smoker on 2006-12-29
a quick way to stop all the crap thats starts with windows is to click, start, run, and type 'msconfig' without the quotes, enter, and when the config box comes up on screen, select the startup tab.

there should be a list, with a column of boxes on the left, every ticked box is something that starts at windows boot, and the more ticked boxes, the slower the boot.

untick everything but antivirus, firewall appz, and apply. the system will need a restart for changes to take effect, let this happen, and when the msconfig has changed box appears, click the box so it will not appear again.

these changes do not uninstall, or delete anything, they only stop windows starting them at boot time, and can be unchanged simply by reversing the process.

hope this helps

---

### Post by psycosmyth on 2006-12-29
My problem with that is a pop-up is activated telling me I did that, it won't go away and I thought I killed those too. I have had apps reactivate startup status and I had to go into services mgmnt to kill them.
I just put said apps on my xp side but I have'nt noticed anything wrong, like it would bother me:rolleyes:

---

### Post by d3v1ant_0n3 on 2006-12-29
See it's stuff like that that convinces me that Windows isn't ready for the desktop ;) *JOKE*

Have you tried using Crapcleaner?

It features a section for stopping startup programs that seems somewhat more aggressive than the default windows one.

---

### Post by smoker on 2006-12-30
> **psycosmyth said:**
> My problem with that is a pop-up is activated telling me I did that, it won't go away and I thought I killed those too. I have had apps reactivate startup status and I had to go into services mgmnt to kill them.
:rolleyes:

yes, many windows programmes seem to think they have a god given right to be started with windows, and also phone home whenever they desire, pester you with popups of upgrades, etc. when i ran windows i checked the msconfig regularly, and also disabled as many services as possible. disabling services can be dodgy though, if you are not sure what programmes use what service, many can use the same service, and some can use several services. it can be a long trial and error process. often it is better to get rid of a programme and find something else that does the same, without ingratiating itself into your windows start up.

> by. d3v1ant_0n3 "Have you tried using Crapcleaner?"

i find this app indispensible for sorting out a lot of pc's with windows problems that come my way. it's also free:D

---

### Post by dbbolton on 2006-12-30
i have to clean out the Run/RunOnce entries of my registry every couple of weeks.

---

