---
title: "Unable to Shut Down and/or Reboot 13.10!"
date: 2013-04-28
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-04-28
Not sure what the problem is. All 13.10 is letting me do right now is either Log Out and/or Lock the Computer!

---

### Post by rrnbtter on 2013-04-28
Greetings,
Try shutdown -h, Raring did this for a couple of days until they fixed it.

---

### Post by serdotlinecho on 2013-04-28
Same for me. I think it's maybe something to do with systemd-logind :-k

---

### Post by Harry33 on 2013-04-29
The poweroff issue was fixed a while ago.
And it was indeed due to the new systemd upgrade which brought in logind (instead of old consolekit).
Now this upgrade never made it into raring, so you could not have experienced it there.
Unless, you had enabled Gnome3 Staging PPA.

I think the systemd upgrade in SS yesterday should not have had the poweroff issue.
However, after updating you need to reboot your setup.
Do that in terminal commanding:
```

sudo reboot

```

---

### Post by kevpan815 on 2013-04-30
> **Harry33 said:**
> The poweroff issue was fixed a while ago.
And it was indeed due to the new systemd upgrade which brought in logind (instead of old consolekit).
Now this upgrade never made it into raring, so you could not have experienced it there.
Unless, you had enabled Gnome3 Staging PPA.

I think the systemd upgrade in SS yesterday should not have had the poweroff issue.
However, after updating you need to reboot your setup.
Do that in terminal commanding:
```

sudo reboot

```

Yes, the issue is now fixed, it might have also had something to do with the fact that I had Saucy-Proposed Enabled. I have since Re-installed Saucy from a 13.04 USB Flash Drive Installer, and this time I left Saucy-Proposed Disabled. By the way, due to the fact that I have UEFI Firmware on 1 of my 3 Computers, I always use X64 Unity Ubuntu, NOT Gnome-PPA Ubuntu, just to let you know. :-)

---

### Post by NBPX on 2013-04-30
It was happening also in Ubuntu 13.04. I and some guys in Brazil had the [same problem]("http://ubuntuforum-br.org/index.php/topic,105265.msg580192.html#msg580192"), sometimes.

---

### Post by kevpan815 on 2013-05-01
For me it did not happen until I put in Ventrical's 3 command's, and then started receiving the Saucy Updates from the Saucy Repos. For me it does still occur right after a Clean 13.04 install, followed by Ventrical's 3 commands, but before I Reboot 13.10 for the first time right after the 3 commands. To fix the issue I do a Control + Alt + F1, I then wait for the Login Screen to change from the 13.04 Login Screen (which is Broken at the momment) to the 13.10 Login Screen (takes about 30-60 seconds after Loading Up the TTY1 Screen, assuming that you did the 13.04 to 13.10 Conversion Correctly), then I Login using my Computer Name and Password and then I type in: "sudo shutdown now -h" which forces the computer to turn itself off. :-)

---

### Post by nikhilbhalwankar on 2013-08-16
> **kevpan815 said:**
> For me it did not happen until I put in Ventrical's 3 command's, and then started receiving the Saucy Updates from the Saucy Repos. For me it does still occur right after a Clean 13.04 install, followed by Ventrical's 3 commands, but before I Reboot 13.10 for the first time right after the 3 commands. To fix the issue I do a Control + Alt + F1, I then wait for the Login Screen to change from the 13.04 Login Screen (which is Broken at the momment) to the 13.10 Login Screen (takes about 30-60 seconds after Loading Up the TTY1 Screen, assuming that you did the 13.04 to 13.10 Conversion Correctly), then I Login using my Computer Name and Password and then I type in: "sudo shutdown now -h" which forces the computer to turn itself off. :-)


Me too facing the same issue. I manually type the shutdown command from command prompt. How to fix this? Any solution?

---

### Post by Cavsfan on 2013-08-21
It has been this way for me for a long time. I have cairo dock installed and use the logout button there to restart. It also notifies me when there is a need to restart after updating files.
Logout and Suspend are the only things that work from the top right button in flashback.

There's a bug for it I believe but I'm not sure where it is.

---

### Post by 02rashid.khan on 2013-11-10
Hello All I was also facing same issues few days back , it was observed by me this was the bug which was occurred after upgrading to Ubuntu 13.XX
from 12.XX

if you did installed cairo dock same thing will work ,
to trouble shoot this issue 
I googled 
software essentails for ubuntu 13.XX

one ubuntu professional updated all code to install software from CLI 
interestingly i found software such as reduce battery consumption
this is surprisingly I got more than my expectation now mys system runs like rolling on smooth butter   

[http://www.unixmen.com/top-things-installing-ubuntu-13-10/#](http://www.unixmen.com/top-things-installing-ubuntu-13-10/#)
this is the link

LINUX is the best thing happen in my life :) , Ubuntu is the gateway for this special world where dominance by windows doesnt hold anymore

---

### Post by Elfy on 2013-11-10
Closed.

We're discussing Trusty Tahr in here now.

---

