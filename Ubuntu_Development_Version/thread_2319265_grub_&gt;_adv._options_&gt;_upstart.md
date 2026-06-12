---
title: "grub &gt; adv. options &gt; upstart"
date: 2016-04-02
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-04-02
Why is it an option if it can't be used?

(- is there a way to use upstart that works?

---

### Post by zika on 2016-04-02
Yes.```
1 root      20   0   43920   4372   2832 S   0,0  0,1   0:01.53 upstart
```Other thing is if that is a real/pure UpStart... ;)```
:~$ dpkg -l|grep upstart
ii  lib[COLOR=#CC0000]**upstart**[/COLOR]1:amd64                                     1.13.2-0ubuntu21                                          amd64        Upstart Client Library
ii  [COLOR=#CC0000]**upstart**[/COLOR]                                               1.13.2-0ubuntu21                                          amd64        event-based init daemon - essential binaries
ii  [COLOR=#CC0000]**upstart**[/COLOR]-bin                                           1.13.2-0ubuntu21                                          all          event-based init daemon - transitional dummy package
ii  [COLOR=#CC0000]**upstart**[/COLOR]-dconf-bridge                                  1.13.2-0ubuntu21                                          amd64        DConf bridge for [COLOR=#CC0000]**upstart**[/COLOR]
```

---

### Post by mc4man on 2016-04-02
Well then it seems it could work though here never gets past 1st. screen & 1/2 (loading kernel, loading initial ramfs,  screen flashes, loading kernel, loading initial ramfs  > nothing

---

### Post by ajgreeny on 2016-04-02
I have just this last minute started Xubuntu 16.04 using the upstart option from grub ->Advanced options but it is a bit of a palaver.

Firstly it does not start lightdm automatically so you may need to login to command line and then run ```
sudo service lightdm start
``` 
Secondly I can not shutdown from the usual button as it returns to a login screen; to shutdown I need to run ```
sudo shutdown -h now
```

---

### Post by zika on 2016-04-02
That all is as expected. You have to remember that all the network is weaved so that SystemD is default. But the original question was only if UpStart works and if it is surplus in Grub menu, as I recall. Decision is made and I do not see much to regret, sometimes I venture in that old part of Grub, just for memories sake....

---

### Post by izznogooood on 2016-04-02
Short answer: Yes, there is a way. But you cannot use both Upstart and Systemd.
This link explaines alot & tells you what you need to change. For the record, systemd was confusing at start but easier  once you start using it :)

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

### Post by mc4man on 2016-04-02
Eventually got an ubuntu session to boot up /log in from upstart option, saw what I wanted to see & that's that. (wanted to see if a current bug was different with upstart.
At least here the only way the grub option worked was to pick it & before it timed out to a busybox go to a tty & start lightdm. So at least for a Ubuntu install the grub option does not work as described in the wiki. ( & generally a worthless option, probably should be removed.

---

### Post by zika on 2016-04-03
> **mc4man said:**
> before it timed out to a busybox go to a tty & start lightdmYou've just reminded me that I did change default settings in SystemD long time ago so that there is no 
delay present for network to get flowing... ;) That makes it a bit easier for this atavism of UpStart that's currently left (also)... ;)

---

### Post by mc4man on 2016-04-03
> **zika said:**
> You've just reminded me that I did change default settings in SystemD long time ago so that there is no 
delay present for network to get flowing... ;) That makes it a bit easier for this atavism of UpStart that's currently left (also)... ;)
One of the other issues here is the hardware I was using has some issue with the kernel that virtually non stop spams a tty with repeating error & warnings. Hardly gives time to do a ctrl+c to stop the spam & enter a command before it starts up. (also spams kernel.log

Resolved that by adding pci=noaer to grub
(the state of skylake & linux is wrought with possible issues, glad the last well made & thought out (almost, who ever decided usb ports should be even closer together is an ....) laptop I have, a lenovo y480 with Haswell, works fine. The skylake pos Hp laptop is more a curiosity with 16.04 than anything useful..

---

