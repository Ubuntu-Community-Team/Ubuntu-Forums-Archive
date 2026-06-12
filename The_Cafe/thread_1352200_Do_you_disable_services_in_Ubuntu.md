---
title: "Do you disable services in Ubuntu?"
date: 2009-12-11
forum: The Cafe
---

### Post by Rytron on 2009-12-11
Do you disable services in Ubuntu?

---

### Post by Marlonsm on 2009-12-11
Just some of them
My computer is running fast enough so digging around for which services I can disable and which I can't just isn't worth it.

---

### Post by bodhi.zazen on 2009-12-11
Moved to the cafe. I disable all services I do not use.

---

### Post by jomiolto on 2009-12-11
I don't use a default installation, so I don't really need to disable services :)

---

### Post by pwnst*r on 2009-12-11
nah, i'm not concerned with RAM or CPU processes.

---

### Post by joeknoodle on 2009-12-11
Don't use bluetooth at all right now - no bt devices

Don't use print services - enable them on the few occasions I do print

Slow system, so every little bit helps.

---

### Post by MooPi on 2009-12-11
I concur with jomiolto
> I don't use a default installation, so I don't really need to disable services
If I'm turning things off then It's a malware thats leaked in from :twisted: gnome-look

---

### Post by Uncle Spellbinder on 2009-12-11
> **pwnst*r said:**
> nah, i'm not concerned with RAM or CPU processes.

Ditto

---

### Post by NoaHall on 2009-12-11
I have plenty of RAM, and CPU power, but I do turn them off - because they aren't needed. Same reason why I use Arch.

---

### Post by Psumi on 2009-12-11
I usually disable bluetooth, and that's about it.

---

### Post by RabbitWho on 2009-12-11
I disabled bluetooth.. That's it, because everything else I don't know what it is so I'm afraid to.

---

### Post by MaxIBoy on 2009-12-11
I disable Bluetooth, VPN, cron/anacron, saned, and a few more.

---

### Post by falconindy on 2009-12-11
> **MaxIBoy said:**
> I disable Bluetooth, VPN, **cron/anacron**, saned, and a few more.
You should understand what cron does and who uses it before you choose to disable it.

---

### Post by Dragonbite on 2009-12-11
I disable Bluetooth because I don't have any devices.

Other than that, I can never tell what to turn off or not.  Like do I need 3 cron-like services and 3 logging services or can I get by with one?

---

### Post by chessnerd on 2009-12-11
I disable some stuff I don't need (for example, neither of my systems has bluetooth, so I remove those programs and disable their services) but I don't go and cut down everything I can. In fact, I even add some extra stuff. On my laptop, because I have the RAM, I load KDE libraries at the startup. It makes running KDE applications much quicker.

---

### Post by ratcheer on 2009-12-11
I use bum (bootup manager) and turn off everything I don't use.

Tim

---

### Post by MaxIBoy on 2009-12-11
> **falconindy said:**
> You should understand what cron does and who uses it before you choose to disable it.
By default, neither Debian nor Ubuntu actually have any cron jobs. They are not used for anything by default, they slow your boot time, and I haven't needed them so far. Been running without them for about four or five months.

---

### Post by falconindy on 2009-12-11
> **MaxIBoy said:**
> By default, neither Debian nor Ubuntu actually have any cron jobs. They are not used for anything by default, they slow your boot time, and I haven't needed them so far. Been running without them for about four or five months.
False. You're probably looking in /etc/cron.d/ when you should be looking in /etc/cron.{hourly,daily,weekly,monthly}/.

The below results are from a vanilla Karmic install on my VM:
```
$ ls /etc/cron.*
cron.d:
anacron

cron.daily:
0anacron  apt       bsdmainutils  logrotate  mlocate             standard
apport    aptitude  dpkg          man-db     popularity-contest

cron.hourly:

cron.monthly:
0anacron  sreadahead  standard

cron.weekly:
0anacron  apt-xapian-index  man-d
```
Looks like there's plenty of update jobs in there.

---

### Post by nothingspecial on 2009-12-11
yep

---

### Post by wojox on 2009-12-11
Yes, I have the need, the need for speed.

---

### Post by Nerd King on 2009-12-11
I get rid of things I don't need, and because I'm a tweak-a-holic.

---

### Post by Yvan300 on 2009-12-11
Only a few such as the blue tooth and assistive tools.

---

