---
title: "spyware, trojan, changed configuration, what happend to my mouse?"
date: 2008-02-15
forum: Security Discussions
---

### Post by jaime77 on 2008-02-15
hi, im from windows paranoia to ubuntu like many... when i search about virus, spyware, etc. almost everybody say you dont need antivirus, antispyware or firewall in ubuntu, so for almost 2 years i have been using ubuntu without any, but...

last week i was surfing the web, and after i visit X site (dont remember it since i visited many) my mouse become making weird things, not all the time, more like random.

like click left button of the mouse, was like it got pressed... for example if i was trying to open a file, after the doble leftclick, it dont open, but when moving the mouse it was dragging the file, same with scrolls bars, or buttons... in any window or program

very random sometimes 1 of 10 times, sometimes more often.

i run my ubuntu with an admin user, almost never use, and a few users all unprivileged, all start happening after that day when visit many sites from a unpriviliged user, i remember the problems begin after one site pop up a dialog asking to download something, i hit no and close the tab, but i think the problem start after that.

what bothered me the most is the problem spread to all the other users, so annoying, i start thinking my mouse was dying, because the problem appear more and more often, i notice it got worse if i not "define" my clicks (not click too fast or click and move the mouse)

well it get worse and was making my way to buy a new mouse, when try to remember if i dropped it or something, and remember the web site pop up (i dont give it much importance at the time since it happened me before) and remembering my windows days i format and reinstall.

i dont think what i was hoping more, that the problem was my mouse or ubuntu, now with a fresh install and without the mouse problems, i think i would like instead my mouse die.

just if you are asking, not installed software that day, i use almost an out of the box ubuntu, just install like 4 debs from ubuntu when installed fresh 7.1 last month, i used those debs in 7.04 and 6.1 all 2007 without problems, even havent used the admin user for weeks before the problems start.

WHAT HAPPEND?

i think the days that my pc got infected, misconfigurated, etc. just by visiting a site were over when i stop using windows.

can one site autoinstall trojans, keyloggers, mouseloggers (that will be my first guess, since its like some clicks events were missing) change configurations, etc?

i think what happened in vegas stay in vegas, or what happened in one user stay with that user, why all users were affected?

ohh, i used firefox from ubuntu installation, have firefox some bug or flaw that allow this?


:mad: how many time before i get logged out... i have to retype every word again

---

### Post by ajgreeny on 2008-02-15
Do you mean you run as root or just as the first user who has admin rights with his user password?  If you run as root, which I must admit, I doubt, please be aware that it is not truly safe and certainly not advised.  All administration can and should be done using "sudo" not by logging in as root.

Have you checked the mouse on another machine, or did you double check the mouse settings after the problems started?  If not it would have been useful to do so to eliminate that as a problem, but now there is little that we can do to help as you have reinstalled.  I doubt if it was any trojan or keylogger that cused the problem, however.  Ubuntu simply doesn't suffer in that way.

---

### Post by thegnuguru on 2008-02-15
Sounds like your X11 configuration got messed up somehow or other i  doubt its malware. As most linux based malware is designed to infect servers.

---

### Post by SunnyRabbiera on 2008-02-15
This is probably not some sort of malware issue...
it might be an update issue of some type or you messed up something by accident.

---

### Post by jaime77 on 2008-02-15
thx all for taking the time to read and respond...

> it might be an update issue of some type or you messed up something by accident
i really doubt it, i really dont mess up with configuration at all, and only hit the update with the admin user twice without any new update, so never updated anything.

> Sounds like your X11 configuration got messed up somehow
my second guess, but can be messed up from an user unpriviliged? 

> Do you mean you run as root or just as the first user who has admin rights with his user password?
i never have logged as root in ubuntu, the only user that can use "sudo" is the admin (well, has other name) and only use it when installed ubuntu to add flash, brasero a few more apps from ubuntu  the day of installation, everyday only log in with an unprivileg user.

> Have you checked the mouse on another machine, or did you double check the mouse settings after the problems started? 
as i say im using it in the moment with a fresh install without problems, so the mouse its ok, but never check the mouse settings after the problems started, i really dont know how, dont mess with configuration at all and use ubuntu with the configuration that came out of the box (a burned iso md5 checked), and the problems were random, not like a changed configuration from right to left click or something like this, more like every once in a while the mouse click release event were not detected, or left and right click press event were not detected. 

> but now there is little that we can do to help as you have reinstalled
I may try to visit every site i could to try to found the problem again, and then check whats wrong, but will be in a few weeks, since right now i have a lot of work

THX TO ALL AGAIN

---

### Post by jaime77 on 2008-02-25
well it start to happend again

i havent reinstalled ubuntu, i have the problem at the moment, so if anyone could help me how to check the configuration, mouse, etc would help me a lot.

maybe its a configuration issue, this time i visit many sites, since i having trouble to see a DVDs friend, i installed many things (codecs, libcss, vcl, plugins, one bundle from add/remove) several times since nothing worked, until i installed one that change my region or quit compiz, dont remember what make it work to play the DVD. it was my first time trying to see a DVD in ubuntu.

but at half movie my power supply fail, hard shutdown, when restarted the problem i describe with the mouse start to happend.

any TIP or should i just reinstall ubuntu?

---

### Post by jaime77 on 2008-02-26
any help? 
also xorg in system monitor always taking a lot of cpu? and 0 bytes memory

---

### Post by RedRat on 2008-02-26
you say that you had a power failure and a hard shut down. Sometimes this can damage the hard drive ever so slightly depending on what and where the read/write head was at the time of the failure. While most R/W heads retract very quickly, it might have touched the surface and it could be that something might have happened. Also another thing, it could be that your machine was writing something to disk when the failure occurred and the write was not done correctly. In any event, you may have a damaged system. Also, when you have a power failure, you might have damaged something in hardware (eg. the motherboard or one of its components), I have had this happen to one of my computers.

that brings up a question: Does Linux have the equivalent of chkdsk in Windows? Can it do a repair of the files, seems to me that it should. What is the command?

At worst, re-format and reload Linux. If the problem persists after that, then you might have a hardware issue.

---

