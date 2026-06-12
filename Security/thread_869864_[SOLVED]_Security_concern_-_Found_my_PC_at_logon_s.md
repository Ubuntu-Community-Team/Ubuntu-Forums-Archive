---
title: "[SOLVED] Security concern - Found my PC at logon screen third day in row!"
date: 2008-07-25
forum: Security
---

### Post by bmwman on 2008-07-25
Hello guys,
I have a desktop machine which i use at work with Ubuntu 8.04. I never turn it off when I go home but today is the third day I come to work and find the machine rebooted and at the logon screen. Nobody else has access to my office. I had 3D Cube screensafer enabled before and that caused it crash occasionally but it wouldn't reboot for that. That was awhile back. Now I just have a regular screen saver, no 3D stuff and before I leave everyday i Lock the screen. 

How can I find out what happened? I know it should be in the logs somewhere, but which ones?

Thanks

---

### Post by bmwman on 2008-07-25
No ideas? I though most people here know more than me about security and at least know which log and where to look!

43 views and nobody, that's hard to believe. 
:)

---

### Post by moonpup on 2008-07-25
Well, there could be a couple of reasons why this is happening.

1) Could be faulty hardware in the computer causing it to spontaneoulsy reboot.

2) Maybe there are power problems in your office with the power going off or maybe the building is doing maintenance and shutting of the power to the building temporarily. Have you asked them if they turned off the power recently?

3) Take a look in /var/log/messages

Let us know what you find out :)

---

### Post by thefunnyman on 2008-07-25
I've had issues with X randomly restarting before.  If u restart X ( Ctrl+Alt+Backspace ) u are taken to ur login screen.  That is also a possibility for what could have happened.  Check in /var/log/Xorg.log.0

Think that path is right.....

Hope this helps.

---

### Post by k_grdn on 2008-07-25
Hi,


To eliminate possible reboots as the cause check uptime, to see how long the systems been up.


Also the Logs are you friend!!

Regards,

k_grdn

---

### Post by bmwman on 2008-07-26
Thanks to all :)
/var/log folder has all the information that i needed. I didnt find anything out of the ordinary in /var/log/messages so it could have been a power outtage. 3 days in a row is a little weird but it's a possibility, since one of those days we had a storm. Let's see what happens on Monday.

BTW I set up a intrusion detection system using this how to :[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10)

It seems pretty good. I had some incomming UDP packets giving me ICMP alerts or something like that. Then I added that originating IP to the blocked in iptables so all packets comming from it are being dropped.

---

### Post by 3rdalbum on 2008-07-27
There's a possibility that the Compiz screensaver crashed X, delivering you back to the login screen.

---

### Post by ovidiub on 2008-07-28
maybe there was some power cut :)

---

### Post by bmwman on 2008-07-28
Well i come in on Monday and find the same thing. The computer is at login screen. I don't think they have a power outtages everyday. That's not possible. My 3D screensaver is disabled also. I just set he screen to go blank so no screensaver -period. This is so weird.

---

### Post by Shazaam on 2008-07-28
Perhaps a janitor or security guard? Or mice chewing on the wires?

---

### Post by tdmoore on 2008-07-28
bmwman,

Are you running dual boot?  Although not very well versed on how to solve issues, I run dual boot and find that if using Windows and shut down, sometimes the computer reboots and after grub sits for the obligatory few seconds, it then boots to the login screen.

If running Windows, suggest you shut down and wait to see if it boots up.

If it's from Ubuntu, sorry but this is as far as I can go.

Just curious....

---

### Post by bmwman on 2008-07-29
> **tdmoore said:**
> bmwman,

Are you running dual boot?  Although not very well versed on how to solve issues, I run dual boot and find that if using Windows and shut down, sometimes the computer reboots and after grub sits for the obligatory few seconds, it then boots to the login screen.

If running Windows, suggest you shut down and wait to see if it boots up.

If it's from Ubuntu, sorry but this is as far as I can go.

Just curious....

Its only Ubuntu, no dual boot.

---

### Post by forger on 2008-07-29
1) Did you by any chance change anything in System > preferences > screensaver lately?
2) Maybe someone is trying to log in with your account?
check out system > administration > system log > auth.log
[https://help.ubuntu.com/community/LinuxLogFiles#Authorization%20Log](https://help.ubuntu.com/community/LinuxLogFiles#Authorization%20Log)
3) Maybe someone is trying to log in with your account by clicking "Switch user" in lock screen? :)

---

### Post by forger on 2008-07-29
Also try:
```
sudo last -n 10 $USER
sudo last -n 20
```

Will show you the last logins with your username, and generally all usernames

---

### Post by daleus on 2008-07-29
Chances are this is not a security issue, What time 'every night' does the machine go off? if its a static time, then there will be a reason for it, maybe something is misconfigured, or the power in the building shuts off at that time to make sure everything is switched off, then your computer comes back on when the power comes back on.

Just thoughts.

---

### Post by forger on 2008-07-29
I think I know a way we can solve this.
bmwman, when you're about to leave, open Applications > Accessories > Text editor, type something in ("This is a test"), don't save it and leave it like that, lock your screen and go back again the next day to see what happens.

If you login and the window is still open and the text "This is a test" is in it, then your system wasn't shut down nor gnome was restarted.
If the gedit window is open without that text, then it the desktop manager was restarted or rebooted/shut down.

It could be a crash, as it was mentioned earlier. You could install a keylogger to check out the activity, you have a bunch of them in the repositories: lkl, deskscribe ..
[http://packages.ubuntu.com/search?keywords=key+log&searchon=all&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=key+log&searchon=all&suite=hardy&section=all)
[http://pykeylogger.wiki.sourceforge.net/](http://pykeylogger.wiki.sourceforge.net/)

---

### Post by bmwman on 2008-08-05
I've been really busy lately and I haven't had a chance to look into the log files. The PC hasn't rebooted in the last few days so I guess it's fine now. I'll look into it when I get a chance.

Thanks to everybody for all tips and suggestions. I hope this is being helpfull to others too.

;)

---

### Post by pedja_portugalac on 2008-08-06
> **bmwman said:**
> I've been really busy lately and I haven't had a chance to look into the log files. The PC hasn't rebooted in the last few days so I guess it's fine now. I'll look into it when I get a chance.

Thanks to everybody for all tips and suggestions. I hope this is being helpfull to others too.

;)

Maybe, someone have the keys of your office (or other tools) and restart your computer to boot in a live distribution of choice to watch content of your hard drive? But then, why letting login screen on? Maybe someone else remotely control your computer over night and to accomplish some installs need reboot? What services are you running at night? Lot of questions, Lot of questions?

---

### Post by bmwman on 2008-08-07
It's not running anything special. It's just the main Ubuntu 8.04.1 with all the updates and I'm running VMware Workstation 6.04. Everything else is standard, no SSH enabled, no Remote Desktop, etc. It had to be a power outtage or the system crashed, but it just didn't seem right to happen 4-5 days in a row. This week I haven't had the problem.

---

### Post by k3lt01 on 2008-08-09
I don't think a power outage was the problem. To my way of thinking power goes out PC shuts off and cant reboot itself cause its off. Makes sense to me, lol. You may be experiencing a "brown out" where power doesn't cut totally but does reduce dramatically. I have had that happen with PCs before and they reboot or burn out, obviously the burn out is not a good thing.

If it isn't a brown out I think it is either a settings problem or a hardware problem. For settings check your logs as already advised, for hardware..... well.... get your PC checked.

---

