---
title: "ubuntu-bug send failure"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-07-28
ubuntu-bug firefox selected "send" shortly thereafter ubuntu-bug disappeared.  Did not send.  

All up to date to today, 28 July:  
3.5.0-6-generic #6-Ubuntu SMP Mon Jul 23 19:53:07 UTC 2012 i686 i686 i686 GNU/Linux
Firefox 15.0

Firefox running O.K. then "unresponsive".  Not responding to mouse or keyboard.  Opera running O.K. so it is not hardware or network.  Re-booted, same scenario.

What do I do when ubuntu-bug gathers all the data, I select "send", seconds later ubuntu-bug disappears?

Thanks for any ideas,

Jerry

---

### Post by jerrylamos on 2012-07-28
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

How do I close firefox when it is not responding?  Selecting ghe "x" on the top left corner does nothing.  "File" does not open a drop down, Alt-F4 does nothing.  Is there some way to find a "process" number and close the process?

Maybe Firefox is not waking up from suspend? - edit - suspend has nothing to do with it.  Occurs spontaneously.

Thanks, Jerry

p.s.  This is from Opera which has no such problem.

---

### Post by mc4man on 2012-07-28
Try again
If it was from a crash then use what's in /var/crash
If not, (ubuntu-bug <app>), then you could also try 
apport-cli <app>
and use appropriate options

Edit - didn't see your subsequent post where issue is FF, not apport...

---

### Post by effenberg0x0 on 2012-07-28
> **jerrylamos said:**
> Is there some way to find a "process" number and close the process?


You can get the pid and then kill it using ps and kill commands. This will kill all instances of firefox:

```
sudo kill -s KILL $(ps ax | grep -i firefox |  awk 'BEGIN {FS=" "} {print $1}' | tr "\n" " ")
```

I have it as a shell script named /usr/bin/superkill.sh. It will search/kill whatever is provided as the first command argument (it uses "$1" instead of firefox in the command line above). One can also use it in ~/.bash_aliases for simplicity.

Regards,
Effenberg

---

### Post by philinux on 2012-07-28
> **jerrylamos said:**
> "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

How do I close firefox when it is not responding?  Selecting ghe "x" on the top left corner does nothing.  "File" does not open a drop down, Alt-F4 does nothing.  Is there some way to find a "process" number and close the process?

Maybe Firefox is not waking up from suspend?

Thanks, Jerry

p.s.  This is from Opera which has no such problem.
 
Easy way.

[http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher)

---

### Post by jerrylamos on 2012-07-28
> **mc4man said:**
> Try again
If it was from a crash then use what's in /var/crash
If not, (ubuntu-bug <app>), then you could also try 
apport-cli <app>
and use appropriate options

Edit - didn't see your subsequent post where issue is FF, not apport...
Send is prime issue.  The reason I was trying to send was the FF which I think is failure to begin again after "turn screen off after 10 min".  I'll try the apport-cli.  

What's in /var/crash is
_usr_lib_indicator-datetime_indicator-datetime-service.1000.crash
doesn't seem to be the FF or the send problems.

Thanks for ideas.

Jerry

---

### Post by ronacc on 2012-07-28
I saw a post in the last couple of days about the current FF being seriously borked but I can't find it again , philinux gave good advice about using Opera , that has been my default browser forever .

---

### Post by ventrical on 2012-07-28
The 3.5.0-6 kernel is being held back here it appears.

The following packages have been kept back:
  cups-filters linux-headers-generic linux-image-generic

---

### Post by effenberg0x0 on 2012-07-28
> **ventrical said:**
> The 3.5.0-6 kernel is being held back here it appears.

The following packages have been kept back:
  cups-filters linux-headers-generic linux-image-generic

Same here until sudo apt-get dist-upgrade

Regards,
Effenberg

---

### Post by jerrylamos on 2012-07-28
send fails because it automatically tries to reach launchpad through firefox which is dead of course.

apport-cli firefox worked because it allows choice of browser so I used Opera.  

It's bug #1030363 written about the firefox will not respond to anything except "Force Quit".

Thanks for the suggestions.

Jerry

---

### Post by ventrical on 2012-07-28
> **effenberg0x0 said:**
> Same here until sudo apt-get dist-upgrade

Regards,
Effenberg

ThnX ! :)

---

### Post by ventrical on 2012-07-28
> **jerrylamos said:**
> ubuntu-bug firefox selected "send" shortly thereafter ubuntu-bug disappeared.  Did not send.  

All up to date to today, 28 July:  
3.5.0-6-generic #6-Ubuntu SMP Mon Jul 23 19:53:07 UTC 2012 i686 i686 i686 GNU/Linux
Firefox 15.0

Firefox running O.K. then "unresponsive".  Not responding to mouse or keyboard.  Opera running O.K. so it is not hardware or network.  Re-booted, same scenario.

What do I do when ubuntu-bug gathers all the data, I select "send", seconds later ubuntu-bug disappears?

Thanks for any ideas,

Jerry

 Ok .. that works ok here jerry on my Intel MoBo, 2.6GHz Dual Core

---

### Post by jerrylamos on 2012-07-29
Alpha 2 updated daily Firefox would hang.  Opera running fine.  With Firefox hung, did ubuntu-bug firefox.  Ubuntu-bug being dumb tried to access launchpad thru Firefox which by definition was dead.  Never occurred to ubuntu-bug it was started because Firefox wasn't working.

So nice hint from the thread here, apport-cli firefox allows selection of browser so I selected Opera which was working.

Gave up on Alpha 2 updated and did an install of Alpha 3 in another partition.  Firefox running fine.  So much for updates being as good as new installs.

Jerry

---

### Post by ventrical on 2012-07-29
> **jerrylamos said:**
> Alpha 2 updated daily Firefox would hang.  Opera running fine.  With Firefox hung, did ubuntu-bug firefox.  Ubuntu-bug being dumb tried to access launchpad thru Firefox which by definition was dead.  Never occurred to ubuntu-bug it was started because Firefox wasn't working.

So nice hint from the thread here, apport-cli firefox allows selection of browser so I selected Opera which was working.

Gave up on Alpha 2 updated and did an install of Alpha 3 in another partition.  Firefox running fine.  So much for updates being as good as new installs.

Jerry

Ahhh... interesting. Never thought of that. Firefox hung. ubuntu-bug being dumb. Apport was doing something similar a while back. I would bring me to launch pad with a non-bug - or a bug that was already filed (dupiclate). So then , if bug is already reported, why call Firefox/launchpad?

---

### Post by jerrylamos on 2012-07-29
> **ventrical said:**
> Ahhh... interesting. Never thought of that. Firefox hung. ubuntu-bug being dumb. Apport was doing something similar a while back. I would bring me to launch pad with a non-bug - or a bug that was already filed (dupiclate). So then , if bug is already reported, why call Firefox/launchpad?
Is there a bug reported already about Firefox hanging with 12.10 Alpha3 level?  Really, it is Alpha 2 updated every day.  So what I did was a new install yesterday which does not hang.  So much for updates being sufficient.

Jerry

---

