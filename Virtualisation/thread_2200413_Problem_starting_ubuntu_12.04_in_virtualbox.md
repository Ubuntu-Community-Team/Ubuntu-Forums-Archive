---
title: "Problem starting ubuntu 12.04 in virtualbox"
date: 2014-01-19
forum: Virtualisation
---

### Post by Jose_Carlos on 2014-01-19
Hi guys,

Last night, do not install in ubuntu, that today to start ubuntu 12.04 in virtualbox do not start in visual mode, it stays frozen. I have entered the console mode "Control + alt + f1" and click "startx" and throws me an error. 


Links of screenshots with the errors: 

[LIST]
[*]1º to start in console mode. [http://imgur.com/i37fyts](http://imgur.com/i37fyts)
[*]2º typing startx. [http://imgur.com/Mlb4y2e](http://imgur.com/Mlb4y2e)
[*]3º the cat / var/log/Xorg.0.log. [http://imgur.com/hFK5xWL](http://imgur.com/hFK5xWL)
[/LIST]

I hope you can help me, thanks.

---

### Post by Jose_Carlos on 2014-01-19
Finally resolved. 
Uninstall the Nvidia packages and install them again. 
Delete authority file $ HOME / .Xauthority 
Update virtualbox guest additions and also virtuabox ready.

---

