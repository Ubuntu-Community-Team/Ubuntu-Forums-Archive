---
title: "wlan0 RF_KILL weirdness"
date: 2015-01-28
forum: Server Platforms
---

### Post by xen3 on 2015-01-28
I just today installed Ubuntu Server (14.10) for the first time.

The installation experience was EXCELLENT. It was the best install experience I have had ever of any product.

Until I decided to check out manual package selection, this enabled Aptitude and I used it to install all of the pre-selected tasks or package groups. Subsequently, when I quit it, the process wasn't as smooth as the installer came across an error. Retrying the software installation step did fix that.

But I just redid the entire thing to see how it would have been if I hadn't used Aptitude in between ;-).

Any case, here is my question or remark of today:


While installing the system, it automatically detected and used and installed and activated my Wifi link. The weirdness is that this laptop's "kill switch icon" keeps flashing on and off, in Windows 7 it is simply a constant blue. Now it is switching blue and red constantly. But, I am speaking now of an Ubuntu Vivid live session.

But in this fresh install of Server, the kill switch doesn't respond to anything anymore. After searching the forums I learned that this behaviour is a pretty old one.

I learned that there might be solutions like (Haven't tested yet, because I'd have to reboot again, too tired..)

```
ifkill list
ifkill unblock all
```

or

```
for i in `find /sys -name "rf_kill"`; do echo 1 > $i; done
```.

I will give it a try. The weirdness is that wifi apparently worked fine during the install, but I couldn't get anything working after. The constant flashing in Vivid is disconcerting as well, however.

Basically DMESG showed the

 [FONT=monospace][COLOR=#000000]iwlwifi 0000:02:00.0: [/COLOR][COLOR=#ff5454]**RF_KILL**[/COLOR][COLOR=#000000] bit toggled to disable [/COLOR]radio.
[/FONT]

message. On every module load, as well. Perhaps we shall find out if it works now.

ALSO I need a web browser to activate the wifi outgoing link, but there is no links or lynx in the repo apparently? It seems I will need to use telnet to activate some http form submit??

I see now there might be a "w3m" installed. I'm sorry, perhaps I'm being a bit rash, but not having any internet is annoying ;-).

Seems strange not to include the most well known command line browsers, though...

---

