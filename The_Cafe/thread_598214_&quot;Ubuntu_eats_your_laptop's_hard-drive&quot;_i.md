---
title: "&quot;Ubuntu eats your laptop's hard-drive&quot; inquirer article"
date: 2007-10-31
forum: The Cafe
---

### Post by dougleduck on 2007-10-31
Just wondered if there's any truth to this claim

[http://www.theinquirer.net/gb/inquirer/news/2007/10/31/ubuntu-eats-lappy-hard-drive](http://www.theinquirer.net/gb/inquirer/news/2007/10/31/ubuntu-eats-lappy-hard-drive)

---

### Post by speedwell68 on 2007-10-31
I very much doubt that.

---

### Post by sapo on 2007-10-31
"He thinks"?!?!? wth?

---

### Post by msubzwari on 2007-10-31
There are already a couple of threads on this forum on that topic. You can also refer to this wiki page for more information

[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)

---

### Post by PartisanEntity on 2007-10-31
> **speedwell68 said:**
> I very much doubt that.

It's confirmed in launchpad.
[https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html)

---

### Post by RAV TUX on 2007-10-31
> **PartisanEntity said:**
> It's confirmed in launchpad.
[https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html)Wow!...thats not good.

Thanks for the link PartisanEntity.

---

### Post by stinger30au on 2007-10-31
> **RAV TUX said:**
> Wow!...thats not good.

Thanks for the link PartisanEntity.

if you have a read thru the info, there is a fix for it...

---

### Post by dougleduck on 2007-10-31
Hope this gets fixed for publicity's sake.

Fixed it but I dont use my battery as it stopped working for more than about 10 minutes a long time ago :P.

Thanks for the info.

---

### Post by helliewm on 2007-10-31
Can anyone explain in simple terms how to implement the fix? Step by step idiot instructions would help a lot of people, me included:)

Helen

---

### Post by speedwell68 on 2007-10-31
> **helliewm said:**
> Can anyone explain in simple terms how to implement the fix? Step by step idiot instructions would help a lot of people, me included:)

Helen

Open the terminal and type the following command...

sudo gedit /etc/acpi/suspend.d/99-hdd-spin-fix.sh

then paste these two lines of code into that file...

#!/bin/sh
hdparm -B 255 /dev/sda

and save it.

Then this command...

sudo gedit /etc/acpi/resume.d/99-hdd-spin-fix.sh

and paste the same two lines of code into this file and save.

Then repeat the process with this...


sudo gedit /etc/acpi/start.d/99-hdd-spin-fix.sh

When I first read this, I thought it was a load of tosh, however upon reflection and much more reading, it has some merit.

---

### Post by helliewm on 2007-10-31
Thanks on my Desktop at the moment. Will give this a go a bit later. That has made it much easier.

Many thanks,

Helen

---

### Post by fuscia on 2007-10-31
thanks, speedwell.

---

### Post by ice60 on 2007-10-31
i think it's only bad if you are in laptop mode, you can check with this -
```
grep ENABLE_LAPTOP_MODE /etc/default/acpi-support
```
mine is always false, even when i unplug it! so it's not a problem i suppose. what's laptop mode?

here's a different fix i made a note of -

```
gksudo gedit hdparm.conf
```
add this at the bottom [color=red]EDIT[/color] you may need to use hda below. i can't think what's the best why to find out :| sudo fdisk -l should do it.
```
/dev/sda {
apm 254
}
```
then start it like this -
```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```
i can't remember where i got that from, but it is different to the other fix!
i found where i got it from -
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

---

### Post by PartisanEntity on 2007-10-31
Btw everyone, there is no need to freak out about this. It may not even affect you.

First, read the entire bug report and you will notice that this is only the case if you have enabled laptop mode. Look here:

/etc/default/acpi-support

In my case: 

```
ENABLE_LAPTOP_MODE=false
```

After installing the monitoring tools mentioned in the bug report I started to monitor my load cycles while plugged into AC and while on battery. Here are my results:

31.10 - 17:20 : 5749
31.10 - 17:22 : 5753 (up to here laptop is not running on battery)
31.10 - 17:25 : 5754 (from here on laptop is running on battery)
31.10 - 17:29 : 5755
31.10 - 17:34 : 5757

Hope this helps.

---

### Post by macogw on 2007-10-31
Default in Ubuntu is for laptop mode to be disabled.  I enabled it on my computer though for the battery changes.  I haven't noticed any unusual disk access on my computer.  I can hear it spin up when it does, and that's generally when opening a file in Open Office or something like that.  I've even had my hard drive get physically knocked out while running, and obviously it wasn't doing anything with the disk at the time, because I popped it back in and it was fine.

---

### Post by PartisanEntity on 2007-10-31
I can't seem to be able to access the 'addcomment' box on launchpad, can anyone confirm?
[https://bugs.launchpad.net/ubuntu/+source/acpi-support](https://bugs.launchpad.net/ubuntu/+source/acpi-support)

---

### Post by bachibusuc on 2008-03-17
Hi,

I really like ubuntu and just started "working" around ubuntu to get independant from Windows. I've been looking all around to fix problems, find things to convert things from Windows to linux and everything even if it takes a lot of time to search for it. The thing is I've was looking for something and found a a post on a web page that ubuntu eats up the hard drive. I'm ready to spend a lot of times to look for ubuntu but if it damages the hardware then I would be more concerned.

I've read a lot of post especially this one:
[http://ubuntuforums.org/showthread.php?t=598214](http://ubuntuforums.org/showthread.php?t=598214)

First, is it the truth? or even if it's the truth, does it affect dramatically ur hard drive?
And there is a fix on that post(the first one with the files in /etc/acpi/...), does it really work??

Thank you.

---

### Post by ukripper on 2008-03-19
> **bachibusuc said:**
> Hi,

I really like ubuntu and just started "working" around ubuntu to get independant from Windows. I've been looking all around to fix problems, find things to convert things from Windows to linux and everything even if it takes a lot of time to search for it. The thing is I've was looking for something and found a a post on a web page that ubuntu eats up the hard drive. I'm ready to spend a lot of times to look for ubuntu but if it damages the hardware then I would be more concerned.

I've read a lot of post especially this one:
[http://ubuntuforums.org/showthread.php?t=598214](http://ubuntuforums.org/showthread.php?t=598214)

First, is it the truth? or even if it's the truth, does it affect dramatically ur hard drive?
And there is a fix on that post(the first one with the files in /etc/acpi/...), does it really work??

Thank you.

It is true in some cases but they have fix available for that (see above posts). Personally I have never come across this issue using ubuntu since 2 years and installed more than 20 machines including laptops.

Make sure ```
grep ENABLE_LAPTOP_MODE /etc/default/acpi-support
``` is set to false in battery mode and in laptop AC mode and you'll be fine.

---

### Post by Tomatz on 2008-03-19
Well this kinda kills that theory right or wrong :)

[http://news.bbc.co.uk/1/hi/technology/6376021.stm](http://news.bbc.co.uk/1/hi/technology/6376021.stm)

---

