---
title: "Crash on shutdown"
date: 2011-09-23
forum: Server Platforms
---

### Post by eggbloke on 2011-09-23
Hey, I installed Ubuntu Server Edition and everything seems to be working okay except for the fact that if I try to power off the server it crashes.

Any help would be appreciated. 

Here is the log: [http://paste.ubuntu.com/695739/](http://paste.ubuntu.com/695739/)

Thanks.

---

### Post by Entilza on 2011-09-23
What command are you using to shutdown? (example:  sudo shutdown -h now)

---

### Post by eggbloke on 2011-09-23
I have used shutdown, reboot and poweroff. Same result for all of them.

---

### Post by Entilza on 2011-09-23
The logging stops once the syslog daemon is killed so there's no logging after that.

What messages do you see on screen?

---

### Post by eggbloke on 2011-09-23
I took a picture: [http://dl.dropbox.com/u/21063251/IMG_20110923_192408.jpg](http://dl.dropbox.com/u/21063251/IMG_20110923_192408.jpg)

It seems to be fine until it gets to the very last moment and freezes.

---

### Post by Entilza on 2011-09-23
Ah.. No crash, it just didn't power off.

Check your motherboard bios if you have ACPI enabled.

---

### Post by eggbloke on 2011-09-23
Yep ACPI is enabled.

---

### Post by CharlesA on 2011-09-23
That looks like normal output, it's just not powering off, which points to an APCI problem.

Does it reboot correctly if you reboot it via the reboot command?

EDIT: Ninja'd.

---

### Post by eggbloke on 2011-09-23
No it doesn't reboot. It does the same thing but with 'will now reboot' or something.

---

### Post by Entilza on 2011-09-23
Double check your bios, maybe do a "reset to defaults" on your bios flags to be sure.

So what type of hardware is this, old/new?

---

### Post by CharlesA on 2011-09-23
It sounds like it's not sending the correct signal. Does the desktop version do the same thing?

---

### Post by eggbloke on 2011-09-23
When I booted with a live CD it did the same thing.

It's a VIA C3 'Nehemiah' on a Commell LV-667 Mini-ITX board which I now think may be the root of my problem. I have heard Ubuntu support is slightly patchy for it.

---

### Post by CharlesA on 2011-09-23
That could be. I know I've heard of other hardware having a similar problem.

Not sure what else to tell you - have you tried a different disto? Maybe Fedora or CentOS.

---

### Post by Entilza on 2011-09-23
Atleast you know it's not crashing so you'll have to power off manually.

Last suggestion from me is to try latest bios..

[http://www.commell.com.tw/Support/Product%20Technical%20Support/LV-667.htm](http://www.commell.com.tw/Support/Product%20Technical%20Support/LV-667.htm)

Good luck..

---

### Post by eggbloke on 2011-09-23
Okay I will probably try Slackware or something. Thanks guys.

---

### Post by eggbloke on 2011-09-23
Sabayon had a kernel panic while starting up.
PCLinuxOS froze while loading.
Slackware has the same problem as Ubuntu.

I guess my hardware and Linux just don't get on very well. =(

---

### Post by eggbloke on 2011-09-26
Solved!

Basically my hardware isn't reporting what year it is from so Linux didn't know if it could enable ACPI or not. I added acpi=force and reboot=acpi to my boot options and now it works fine.

Thanks guys. =)

---

